---
title: "Boot sector error prevents Ubuntu loading"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by AmpersUK on 2013-06-16
I had this trouble once before and for the life of me, cannot remember the solution. The problem with old age is, I can remember everything 40 years ago - anyone want some help with the Commodore Pet? ;-)

I had some malware so reloaded Ubuntu 13.04 and within a couple of seconds of turning the computer on, I get the following error message

[FONT=courier new][B]error: unknown filesystem.
grub rescue>[/B][/FONT]

Alas, the only way I can get to my data is to load up the live disk, and you all know how long that takes. I am slowly dying here of caffeine poisoning during the daytime and alcohol poising during the evening.

Any clues? I downloaded the boot repair disk, but that doesn't boot.

Ampers.

---

### Post by oldfred on 2013-06-16
If you have liveDVD or flash working you can download Boot-Repair into the Ubuntu installer.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by AmpersUK on 2013-06-18
Have tried that but get lots of error messages and just doesn't work.

---

### Post by oldfred on 2013-06-18
What errors are you getting with Boot-Repair or Ubuntu liveDVD/Flash?
You can try booting from grub rescue manually.

 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

You can also try Supergrub.
      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

---

