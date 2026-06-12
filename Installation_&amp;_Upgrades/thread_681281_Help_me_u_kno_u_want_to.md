---
title: "Help me u kno u want to"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by 5starog on 2008-01-28
Yeah so i have two hard drives one windows and the other blank. I formatted the blank one deleted all partitions, and I'm trying to install Ubuntu on the blank one. So i downloaded the iso and burnt it on three different cds just incase. When i try to install it i get through everything except when the main install thing comes and gets stuck on 15% Detecting file system. EVERYTHING iS FROZEN usb keyboard ps2 keyboard usb mouse and ps2 mouse are all stuck nothing move the num lock doesn't work, its just frozen I tried this 17 times it always gets stuck at 15 and yesterday i even ;left it for five exact hours

I tried it in safe graphics mode, scanned the cds for errors and checked the memory (no errors) and still its stuck on 15% I read every single post here about that problem  SHOULD i just try the alternate installer?

I have Intel Celeron 1.80 ghz 256 DDR1 ram (old I kno) MAxtor 31536H2 (ubuntu) look here [http://www.hd4less.com/maxdiammaxvl7.html](http://www.hd4less.com/maxdiammaxvl7.html) and a Smasunf 40 gb (windows) and video card is SVG PRO SAVAGER 32 mb

AnotheR question, after i install Ubuntu can i make the windows master and ubuntu slave and use the windows MBR instead of GRUB. And I know that I can install GRub on a floppy to keep my windows mbr [http://ubuntuforums.org/showthread.p...ng+windows+mbr](http://ubuntuforums.org/showthread.p...ng+windows+mbr)
Should I do that or should i just make ubuntu master and windows slave and configure the grub menu after. I'm going to use windows 95% of the time

---

### Post by Rhubarb on 2008-01-28
It looks like you don't have much RAM there at all.
256MB of RAM might / might not work for you.

You have a few options in this case:
Download the Ubuntu alternate iso (this is a text-mode installer for ubuntu, so it doesn't gobble up much RAM while installing)
Or perhaps try out Xubuntu live cd, it consumes a little less resources and hence should install ok (but is based on Xfce, which looks very different from Ubuntu's Gnome environment).

IMHO it's best to use GRUB rather than windows' MBR, because window's mbr isn't that friendly towards non-microsoft operating systems.
It is quite easy to configure GRUB in ubuntu to make windows start by default in the GRUB menu.

---

### Post by DRPend on 2008-01-28
I agree with using GRUB, but be careful in the future about rerunning any windows installs, as windows has a nasty habit of messing with GRUB.  Make a full backup of everything before you attempt anything like this. Seems obvious, but there's a reason I know about this......

---

