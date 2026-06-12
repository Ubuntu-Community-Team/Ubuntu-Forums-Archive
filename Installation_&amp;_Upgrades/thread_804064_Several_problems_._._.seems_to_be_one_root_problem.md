---
title: "Several problems . . .seems to be one root problem."
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by CheshireMac on 2008-05-22
Hey folks. I'm trying to get a friend's Dell 1521 to run smoothly. I'm trying to get wireless working, I'm trying to do that through Ndiswrapper, and I'm trying to also get her sources.list to be up to par. 
Along the way, I keep getting errors that I've never discovered before now. I'm running on a 64bit which I've never done before, so that may be an issue, but I don't think it should be.
[FONT=monospace]```
Please insert the disk labeled: Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423) in drive /cdrom/
```
This error crops up all the time now, even though I have the disc ng inserted. I got it on the same machine with the 32bit disc as well . . . I searched Google for this error, as the forums turned up nothing. The one solution I was able to access (the other result was a 503 {I've been getting those a lot with either FF3 or Hardy} error and didn't look promising anyway)stated that I should try mounting the CD drive. I checked and tried, and it's mounted. It was mounted. 
I am desperate to get this working, as it's her only computer, and I really want to show off Ubuntu versus Vista for her. She loves the cube, and its convenience. 
So once I get this issue fixed, the W: errors should go away, and I should be able to get everything up and running. Til then, this is a pretty-in-pink brick that has a functional (but choppy) cube . . .HELP!?!?!? Thanks for any ideas.
[/FONT]

---

### Post by tamoneya on 2008-05-22
just tell it not to use the cd for packages:
1. open synaptic package manager
2. settings -> repositories
3. Uncheck the cdrom near the bottom

---

