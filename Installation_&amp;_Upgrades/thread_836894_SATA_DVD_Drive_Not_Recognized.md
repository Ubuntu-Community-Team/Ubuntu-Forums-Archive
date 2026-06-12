---
title: "SATA DVD Drive Not Recognized"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by amazingTrav on 2008-06-21
So I'm trying to install Ubuntu on my new rig, I've done this before many times on older hardware and had no problems, I also never had a SATA DVD Drive before, now when I get to the installation screen on the alternate install CD, I get an error that my CD drive is not recognized. I'm stumped, tried everything that I knew how to do for the past few days. I tried installing with the regular graphical installer, but it sets the incorrect refresh rate on my monitor as soon as it starts up and the screen goes black.


Also note that I am installing along side Windows XP x64 Edition as a dual boot, not that it should make a difference at this time.

Relevant System Specs
Motherboard: Asus MCP72XE-M3N-HT-Deluxe
Processor: AMD Phenom 9850 Black Edition Quad Core @ 2.5GHZ
Memory: 8192MB DDR2 1066mhz
Video Cards: Dual Nvidia GeForce 8800GT 512MB Running in SLI
Hard Disk: 500GB SATA HDD, 250GB Partition for Windows
Optical Drive: LITE-ON DVDRW LH-20A1S (SATA DVD RW)
Monitor: Hannspree HF289H 28" LCD 1920x1200@60Hz
Trying to install: ubuntu-8.04-alternate-amd64
(Or the standard desktop install, if someone knows how I can fix that refresh rate issue. )

How can the installer boot from the CD then not be able to detect it, haha :confused:

---

### Post by damphoud on 2008-06-22
Try checking this thred:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Are you able to get into tty1? ctrl+alt+f1. You can look into configuring from the live CD.

---

### Post by avtolle on 2008-06-22
A thought; on booting from the alternate install cd, press F6; at the end of the boot string, and before the -- at the end of the string, insert "all_generic_ide" (w/o the quotation marks), b for boot, and see if that helps.

---

### Post by amazingTrav on 2008-06-22
> **damphoud said:**
> Try checking this thred:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Are you able to get into tty1? ctrl+alt+f1. You can look into configuring from the live CD.

Yes I can get into TTY1 from the graphical installation CD, I have tried making changes to xorg.conf

Specifically I added
    HorizSync     60
    VertRefresh    60

to the monitor section and did "init 1" to boot back into graphics mode, screen comes up for about 5 seconds, I hear the ubuntu startup sounds, and then goes black, flickers back on and off sometimes for 1-6 seconds infinitely.

I have also tried 
  sudo dpkg-reconfigure xserver-xorg
which goes through a keyboard config then exits with no change.

> **avtolle said:**
> A thought; on booting from the alternate install cd, press F6; at the end of the boot string, and before the -- at the end of the string, insert "all_generic_ide" (w/o the quotation marks), b for boot, and see if that helps.

I am already using these installation options:
all_generic_ide floppy=off irqpoll

---

### Post by damphoud on 2008-06-22
Do you have an crt laying around to see if you are dealing with refresh rates?

---

### Post by amazingTrav on 2008-06-22
> **damphoud said:**
> Do you have an crt laying around to see if you are dealing with refresh rates?

I do, but I hoped that it wouldn't come to this. I'll grab it and respond in about 10 mins.

Edit:
Graphical Installer loaded up fine on CRT Monitor, Going through installer now to see if there is an issue with the CDROM.

---

### Post by amazingTrav on 2008-06-22
Seems to have hung at 5% formatting partition, not sure what's up.

---

### Post by damphoud on 2008-06-22
try running chkdsk /f in windows, and reboot twice. maybe there are hd error need to be fixed.

---

### Post by amazingTrav on 2008-06-22
> **damphoud said:**
> try running chkdsk /f in windows, and reboot twice. maybe there are hd error need to be fixed.

Hmm, still stuck at 5% on "Partitions formatting" maybe I'm just o impatient and I should let it do it's thing :P

It is installing on free space on the drive, not a previous partition.

Edit:
Yeah nevermind, there it goes, I feel like a loser.

---

### Post by amazingTrav on 2008-06-22
Ubuntu is now installed, I am still having the refresh rate issue, as soon as I see the login screen on my LCD monitor, black screen. I can login fine on the old CRT. My network access was also not automatically configured. But I suppose I can get to that later. I can access the console with ctrl+alt+F1. I have no Idea what to do about xorg.

Also, how can I make grub remember my startup options? 
floppy=off all_generic_ide irqpoll
I add these options to the loader each time ubuntu starts, but they are not saved.

---

### Post by damphoud on 2008-06-22
Look into having a default resloution as well... look into the thread I posted last night. I'm sure your answer lies in that thread.

---

### Post by markusr on 2008-07-13
"pci=nomsi" instead of "all_ide_generic" is a good solution too...

at least i worked for me and did solve my network problems at the same time

---

