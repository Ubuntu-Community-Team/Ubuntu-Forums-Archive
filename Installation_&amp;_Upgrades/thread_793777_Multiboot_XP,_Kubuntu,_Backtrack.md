---
title: "Multiboot XP, Kubuntu, Backtrack"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by markvanhaze on 2008-05-14
Hi,
I have been searching through the forums here and remote exploit to find a solution to my problem but I am not good enough with bootmanagers to figure this one out.
I have a laptop (thinkpad T30 with a 150GB IDE harddisk) on which I have Kubuntu and XP installed nicely using grub. Now I want to add backtrack and grub is giving me the Error 18. I made a snapshot of my hdd setup: [http://www.computerprofessional.at/various/hdd.jpg](http://www.computerprofessional.at/various/hdd.jpg)

Basically I made a 150mb ext3 primary partition at the start of the hdd to make grub work
Then a primary NTFS for XP
Then an extended partition with 2 logical partitions of which one is reiserfs with kubuntu and the other swap
Finally I have another primary partition with ext3 for BT.

I have added BT into grub menu.lst with the following:

title BackTrack
root (hd0,3)
kernel /boot/vmlinuz ro root=/dev/sda4
boot

Its probably easy to solve but im stuck. Any help is appreciated.

---

