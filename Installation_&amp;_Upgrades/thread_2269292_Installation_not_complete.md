---
title: "Installation not complete?"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by amrabdi on 2015-03-14
Okay, so I just bought an Intel NUC machine with the 5th gen Broadwell i3 cpu(as an HTPC). I at first installed Ubunut 14.10(read that it supported the 5500 gpu of the i3). Everything was working well(more so after I googled how to update to the newer kernel). However, at 1080p on a 32in TV I was having some issues with scaling(going from 1.8x to 2x just mucks things up) and font(plus Ubuntu thinks it's a 74" tv). So, decided that I'd rather keep my media separate and purchased a 128gb SSD(m.2) along with the 1tb hdd. I wanted to give Gnome a shot as I had some familiarity with it(had a 1st gen HP netbook that came with custom version of Ubuntu). So, googled and noticed that if I run 15.04 beta it will update to the final release. 

So, it looks like that everything installed correctly, but that doesn't seem to be the case. Sound doesn't work, shows up as dummy(?), and a lot of the settings are locked, but it won't let me unlock. Plus, when I try to do software update it fails, and I get a message regarding not enough access/privilege? The OS is also still showing the display as 72" and scaling is more the same here, but font scaling works better. I did another clean install, but the same thing. I would prefer to use Ubuntu as I like the interface more when using it on my tv. I prefer not to go to 14.04 as it doesn't offer sound or graphics drivers for intel 5th gen cpu and while 14.10 does, but requires an update to kernel and drivers to work, not to mention it's close to being EOL. Any ideas?

Edit: All the version I have tried have been 64bit builds.

---

### Post by fantab on 2015-03-15
If 15.04 beta works then Install it. It will update to stable by April end.
Does your TV support the resolutions which your gpu offers... you may have to change the resolution accordingly.

> Sound doesn't work, shows up as dummy(?), and a lot of the settings are  locked, but it won't let me unlock. Plus, when I try to do software  update it fails, and I get a message regarding not enough  access/privilege?
Some settings and Updates/upgrades only work if you elevate yourself to root, ie. use 'sudo'. However there seems to some issue with the way you are installing... You should not have permissions issue on a fresh install.

I'd say get yourself a fresh download of 15.04 daily build, do a SHA256Sum check on the .iso to verify its integrity. Burn the .iso to USB flash/pen drive.

---

### Post by amrabdi on 2015-03-15
I went with version 14.10, which from what I read can be easily updated to 15.04. Most of my issues are fixed, but I am still trying to figure out the scaling issue. My TV does support 1080p, and I was using 1080p on the beta and when I was testing out Unity, but right now I am on 720P, and that seem to be a little easier on my eyes at standard tv viewing distance.

---

