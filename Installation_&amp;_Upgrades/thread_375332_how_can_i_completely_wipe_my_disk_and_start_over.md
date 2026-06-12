---
title: "how can i completely wipe my disk and start over?"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by ufugu on 2007-03-03
Hi all,

Short version: Is there a way I can completely wipe my hard drive clean and start anew with an Ubuntu-only install?

Long version: I just got an HP Pavilion 1.6 GHz Core Duo last week.  Previously I had been running Ubuntu on an iMac G4 for about six months with good success.  I have about 20 years on Macs and almost no Windows experience.

Since I didn't have any desire to keep Windows XP or dual boot, I put in my Ubuntu x86 6.10 install disc and chose the option to erase the entire disc.  The install progress bar stuck at 6% for over 24 hours and I ended up doing a hard shut down with the power button (I know this is bad).

I tried again, this time with a custom partition install option to make /, swap, and /home, but Gparted crashed.  When I went to try again, I looked like the previous attempt had succeeded for the swap partition but the other two were of "unknown" format with a yellow warning icon. Tried again, same result.

At this point, I thought maybe I should just reinstall Windows to start fresh in case for some reason the machine needed me to keep a Windows partition on there.  Little did I know that my computer came without any sort of system or install discs. Guess I'm PC naive but I had no idea they sold computers without reinstall discs!  So that was a dead end.

I scoured the forums and found some stuff about Grub that sounded relevant.  I booted from the Ubuntu CD and went though terminal and got an error 15 that I have no Grub (also the message I get if I try to boot with no CD in the drive).  I also tried booting from a Grub repair CD I found through the forums but it wouldn't help me.

Right now, I have booted from the Ubuntu CD again.  I thought I would try erasing the disk with Gparted directly (not through the installer) and create one large ext3 disc.  It has now been  trying to apply the reformatting for over 36 hours to a 160 GB disk (I am just letting it go on for now). This seems too long.

I have NO data on the disk that I need to save.  All I want is a fresh Ubuntu install.  Is there any way I can just start over?

Thanks in advance for your advice!

---

### Post by taurus on 2007-03-03
Boot the LiveCD and use gparted (System -> Administration) to remove all the partitions, leaving your harddrive as one single partition.

---

### Post by ufugu on 2007-03-04
thanks.  i had tried this before but the key seemed to be to wipe out all partitions, and then reboot which is what i was missing.  all is well now.

---

