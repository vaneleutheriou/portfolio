# Rich Presence FAQ

> The SDK that this documentation references, Discord-RPC, has been deprecated in favor of our new Discord GameSDK. Replacement functionality for the Rich Presence SDK can be found in the Activity Manager of that SDK. 
> 
> This documentation can be referenced for education but **does not entirely reflect the new SDK**.
>
> Below are answers to some common questions about integrating Rich Presence with your game. If your question isn't answered here, feel free to reach out to [gamedevs@discord.com](mailto:gamedevs@discord.com) for more help.


índice


## 1. I see "Playing MyGame", but no Rich Presence data.

There's a couple things that could be going on:

- If you're running two instances of the Discord client, check both.
- Double check that your `Discord_Initialize()` function is correct.

Throughout development, make sure you have your `errored()` and `disconnected()` callbacks hooked up for debugging. You can open up the console in Discord and look for errors pertaining to `SET_ACTIVITY` for more information as well.

## 2. I don't see Spectate buttons on my profile.

Make sure you applied for approval. If you want the **Spectate** button on your players' profiles, your integration must go through an approval process. If you have applied and have been approved and still don't see the buttons, check your Discord console for errors.

## 3. What happens if there is more than one game running that supports Rich Presence?

Due to recent changes in our infrastructure for support of multi-activities, the behavior of multiple connected Rich Presence apps has changed from what it was before. Previously, whichever application was focused would be the presence that was shown. With the recent changes, the application that connected _first_ is now displayed.

However, invite functionality across multiple connected applications now works no matter which app is display on a user's profile. For example, if you are hosting a Spotify listening party, playing Game A that allows you to send Join invites, and playing Game B that allows you to send Spectate invites, you'll be able to send invites to all three simultaneously.

## 4. What if someone looking at my profile or an invite doesn't own the game?

Anyone can see your profile data, whether they own the game or not. They'll only be able to interact with chat invites or profile buttons if they own the game and have launched it at least once. Otherwise, the invite/button tooltip will show "Game Not Detected".

## 5. Do join invitations allow players to select the number of open slots?

Currently, the SDK does not support this. Party slot information is determined by the party data you sent in your presence payload.

## 6. Can I send images via the payload rather than uploading them to my Developer Dashboard?

Yes. In addition to uploading an asset and specifying its name, you can also specify an external image URL for us to proxy. For more information, see Activity Asset Image.

## 7. Can I change something in the SDK for my own purposes?

Yes. The SDK is open source by design. If you need, you can change something for the purposes of your specific integration—like changing our JSON parser, or changing variable names.

## 8. How do I customize my integration?

Check out our Rich Presence Best Practices guide for a rundown on how to improve your integration.
