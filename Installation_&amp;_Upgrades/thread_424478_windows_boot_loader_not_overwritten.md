---
title: "windows boot loader not overwritten"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by greenacratic on 2007-04-26
okay, i might just be missing something huge but i'm gonna ask anyways.... i have a computer with two drives in it, one 120 gigabyte parralell, and one 80 gig serial ata..... i formatted the 120 as fat 32 so i can use it between systems.... i split the 80 gig down the middle with a partition and first installed windows xp sp2.... it worked.... then i installed ubuntu 7.04 from the live dvd.... reboot.... and it goes straight to windows.... how do i get the master boot record to be grub instead of the windows partition.... 

i know i'm going to feel so stupid when you guys tell me :lolflag:

---

### Post by raja on 2007-04-26
I have no idea why grub was not installed properly. Anyway now, one way to get to Ubuntu may be to boot from the live cd again and install grub onto the MBR. You can follow the instructions[ here]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by greenacratic on 2007-04-26
well this is a new one for me.... so in the meanwhile i booted up gparted and saw that there were no boot flags on any of the volumes.... so i added one to the ext3 partition.... reboot..... "unable to boot to operating system".... so i went back in and took it off..... reboot.... magically theres grub where xp was automatically loading before..... so it works.... i dunno what i did.... but i got my dual boot now

computer magic? hard drive fairy? :confused:

---

### Post by raja on 2007-04-26
Amazing !

---

