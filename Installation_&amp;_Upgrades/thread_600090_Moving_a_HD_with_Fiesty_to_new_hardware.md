---
title: "Moving a HD with Fiesty to new hardware"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by Revolution on 2007-11-01
I've been running Fiesty for about six months and have a large collection of files and programs installed.

I have just picked up a newer laptop with different hardware and after putting the old drive in the newer laptop I can get to the command line.

Am I better off copying all my relevant files off the old drive and doing a fresh Gutsy install or would it be better to just do a dist-upgrade?

Since the hardware is different I'm not sure if dist-upgrade will set up Xserver for the new video chip etc.

---

### Post by wieman01 on 2007-11-01
If it is new hardware, I would rather reinstall Gutsy. An upgrade might seriously bork your system, I just would not want to take the risk. Do a clean install.

---

### Post by Revolution on 2007-11-01
The dist-upgrade seemed to download files for upgrade but crashed back to the prompt.

So I've fixed the Xserver problem with
'sudo dpkg-reconfigure xserver-xorg' - ran through all the default settings and ran xstart.

Now I'll try the actual upgrade with xserver working.

---

