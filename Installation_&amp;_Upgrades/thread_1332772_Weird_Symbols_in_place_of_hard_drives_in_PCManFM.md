---
title: "Weird Symbols in place of hard drives in PCManFM"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by If I Get Old on 2009-11-20
I have had many issues since I upgraded to 9.10.  It has been quite disheartening because the previous 8 releases have worked just fine.  I have no sound like many other people and have yet to find the fix.  My CRON jobs started acting up and I haven't had a chance to look into what is happening.  When I launch VLC and play a file it crashes instantly.  My files have all lost their application association. 

The thing that perplexes me the most is my file explorer, PManFM should show my hard drive storage capacity in the upper left side and instead I'm seeing weird symbols in their place. See the attached picture for an example.  Any help here is greatly appreciated.

---

### Post by CrunchBuntu on 2009-11-20
I had the same problem with loss of file associations in PCManFm when I did the upgrade from CrunchBang to Karmic. I'm afraid I didn't find a solution other than switch to using Nautilus. The one feature I really liked in PCManFM was "open as root here" which I have now included into Nautilus with a script.

In your case however I suspect the trouble is that there is a folder on your computer called Glenn Beck and your machine is just throwing a fit  :-)

---

### Post by slumbergod on 2009-11-20
Thunar is a very lightweight, quick file browser. It is worth a try too.

---

### Post by If I Get Old on 2009-11-20
Just for extra proof the error appears in Dolphin as well.

---

### Post by If I Get Old on 2009-11-22
bump

---

### Post by motsteve on 2009-11-22
I had all kinds of problems, mostly with the bootloader.  Check your /boot/grub.cfg file for the partition that you are intending to use and make sure that your kernel is 2.6.31.... instead of some lower number of rev.  Trying to run Karmic with a Hardy kernel spells disaster.

Oh yeah, screw that notice about modifying the file.  Use vi and overide the write protect.  Be advised, though, the next time you do a update-grub2 you are back to ground zero.

Note: I hope you are line command savvy.  If not, come back and someone should be able to guide you.  I'm leaving soon, but will be back in a few hours.

Best of luck.

---

