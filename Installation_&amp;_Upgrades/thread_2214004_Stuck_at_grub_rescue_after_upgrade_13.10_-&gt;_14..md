---
title: "Stuck at grub rescue after upgrade 13.10 -&gt; 14.04beta"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by lucio2 on 2014-03-29
Hi, 
I have upgraded from 13.10 to 14.04beta and could not reboot. 
I am stuck at grub rescue menu with error "could not find grub_term_highlight_color". Just before Grub flashes the message could not open /EFI/BOOT/fallback.efi.

The laptop is a Samsung series 9 with only Ubuntu installed.  Last time I have upgraded from 13.04 to 13.10 I had the same problem which was fixed running boot-repair from a live USB. I tried the same running boot-repair with default options from a live USB 13.10 but this time this did not fix the problem. 
The output is [http://paste.ubuntu.com/7174889](http://paste.ubuntu.com/7174889). 
Before I try to play reinstalling grub by hand and or re-running boot-repair has anybody any suggestion from looking to the above log ?
Thank you.

---

### Post by pureblood on 2014-04-18
I have had the same problem. My guess is that, since I have two hard drives, the system is trying to start from the wrong drive where an old version of GRUB is installed. My solution was to start Ubuntu with a USB stick (it does not matter which version). Once you start, these commands will do it:
# mkdir /tmp/drive
# sudo mount /dev/sdX1 /tmp/drive
# sudo mount --bind /dev /tmp/drive/dev
# sudo mount --bind /proc /tmp/drive/proc
# sudo mount --bind /sys /tmp/drive/sys
# sudo chroot /tmp/drive
# dpkg-reconfigure grub-pc
Where sdX1 must be the drive where your system is installed. When you run the last command you should select the sdX drive, though I guess running it multiple times will install the new version of grub on each drive and give you some piece of mind.

---

