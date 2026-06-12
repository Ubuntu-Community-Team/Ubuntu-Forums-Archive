---
title: "Upgrading OEM install of Edgy to Feisty"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by NeoTaoistTechnoPagan on 2007-04-19
Just to let all know - this worked fine with no problems. I had a system for a friend who wanted a Linux distro on it and I have a personal mirror of Dapper and Edgy here and I installed 6.10 on his IBM Netvista. After having some issues getting the video to be larger than 640x480 on an Intel 82845G (you have to enable 8M video memory in the BIOS) I had Edgy working perfectly with Automatix2.

So I was up late last night - matter of fact I'm STILL up, 36 hours plus at the moment and I'm freaking stressed.. .

I figured - what the hell - it's an OEM install - the worst that can happen is that I have to re-install 6.10 so I installed all of the updates and then did 
```
gksu "update-manager -c -d"
```

Now as this was around 3:30AM this morning, the servers were pretty much ok. Right about now they are slammed - good luck finding a local mirror that is not.

After that finished at around 5AM and I did the final reboot, it all looked great! Then I did the usual
```
sudo oem-config-prepare
```
and shut it down.

When my friend started it up, it worked beautifully - he went through the user set-up and was greeted by a login and then his very first GNOME Desktop.

I have to say that I wasn't sure if this would work but I am impressed that it did.

At the current time on my personal mirror, I am using Jigdo to assemble a DVD of Feisty from a mirror in my area. I'll have mine set up to mirror Feisty soon.

---

