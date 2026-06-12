---
title: "Mythtv Totally Screwed Up After 'Upgrade' to 16.04"
date: 2017-09-03
forum: Installation &amp; Upgrades
---

### Post by bilkay on 2017-09-03
I just 'upgraded' from 14.04 to 16.04. I have a Hauppauge HVR-2255 video card which required a custom kernel supplied from Hauppauge. After the 'upgrade,' mythtv is useless. First off, when I try to play a recording, all I get is sound and mythtv disappears from the screen. The card is said to be supported in the 16.04 kernel but backendsetup -> capture cards doesn't even show any dvb devices.

So, I restarted with the old kernel. Running the backend setup started out with a lot of missing information. After deleting and adding cards and making connections, everything looks OK, but I still just get errors on all cards. When I quit, I get a message saying that card 10 (?) is set to start on a channel that doesn't exist. I have no idea where it's getting that information or why it thinks I have that many cards.

Am I wrong that the card should be supported? If I uninstall mythtv and reinstall it, how do I retain all my recording information? Is a reinstall likely to help?

Also, the frontend on my laptop running ubuntu 14.04 can't connect to the remote backend because of the 'upgraded' database. Can I upgrade the frontend on my laptop without 'upgrading' to 16.04?

---

