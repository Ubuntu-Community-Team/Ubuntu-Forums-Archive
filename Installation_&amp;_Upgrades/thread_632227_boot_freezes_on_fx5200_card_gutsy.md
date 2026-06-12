---
title: "boot freezes on fx5200 card gutsy"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by dtdave on 2007-12-05
I have a dell dimension 2350 and I put in a pci geforce 5200 and it freezes on bootup, I got gutsy installed using the onboard graphics, that works fine, ofcourse I dont want to use the onboard, I have disabled the spash screen on bootup, no change. I even went through trying what is on this link [http://ubuntuforums.org/showthread.php?p=2278208](http://ubuntuforums.org/showthread.php?p=2278208) and did not work, course it was an earlier version of ubuntu for fixes, PLEASE HELP!! I am a linux newbie and vista is anoying me and I like what ubuntu has done and want it!! I also got in and updated ubuntu with all the updates, around 130 updates hoping that would help but no luck.  Thanks for any help!!

---

### Post by Torgas Prim on 2007-12-05
Have you used the Live CD to boot to safe mode?

Also, check to be sure your BIOS is updated.

---

### Post by pathiks on 2007-12-05
Same problem here.. It doesnt work even in the safe mode. Simply freezes after the 1st installation menu.

---

### Post by dtdave on 2007-12-05
the live cd freezes too, as I said it will only boot with the live cd or boot to ubuntu when using the integrated intel graphics card, cant disable it, only check it to auto or integrated, so when I put it on auto, then it boots off my geforce card, but freezes as ubuntu boots, every time, so I can get to ubuntu under the integrated card, I will see if there is a bios upgrade

---

### Post by dtdave on 2007-12-05
there is no bios upgrade, the one on Dells site is for back in 2003 for the last update to bios, are there some things I can do from that link I put in my first post, where that was an earlier version of ubuntu, wonder if there are different things to try in 7.10 one thing that was strange on that site was the hotplug/blacklist edit, when I did that there was no blacklist file there in the first place, so I made a new file of it, and editing the xorg.conf not sure if I got that totally right, any help again is very appreciated, thanks

---

### Post by louieb on 2007-12-05
I have the fx5200 in a couple of PCs. (no on-board video - no problem) I've seen a number of threads about problems with this card.  Most are installed in a PCI slot and the PC also has on-board video too. Haven't seen a fix for it yet. 
You can got to [Ubuntu Bugs]("https://bugs.launchpad.net/ubuntu") and do a search FX5200.

---

### Post by dtdave on 2007-12-06
I got it working! I ended up looking at the link in my first post that I had looked at previously and what I did differently with it is I went through the steps but in gutsy I found where the blacklist file is, it is in etc/modprobe.d/blacklist and that is where I put that stuff, then instead of configuring xorg.conf, I just reconfigured it instead with the setup (reconfigure xserver command at the bottom of the page on that link) rebooted and it worked!! Thank you everyone!!!

---

