---
title: "gnu grub version 1.99-21ubuntu3.10 problem"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by awilo on 2013-08-19
Hi!
i have a problem at startup of ubuntu 12.04 32bit.
 when i start the computer it says:

GNU GRUB VERSION 1.99-21ubuntu3.1
Minimal BASH- like line editing supported. for the first word, TAB 
lists all possible command completions. Anywhere else TAB list possible device or file completions.

if i press tab, it shows a list of some words that don't make sense to me.

when i insert a liveCD there is no response. yes i have selected CD boot in bios, but it starts from hard disc anyway.


Please help.

WOJ.

---

### Post by a-mozga-2012 on 2013-10-07
If anyone knows how to fix this, please let me know, as I am a new user experiencing the same problem.

---

### Post by oldfred on 2013-10-07
If liveCD is a good install with boot files then it should boot. If damaged you may need a new one. If BIOS does not see a bootable device in CD, then it will skip it.

If you can get LiveDVD or flash drive to boot.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

You may be able to boot from grub> or grub rescue if that is what you get.
      
 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

