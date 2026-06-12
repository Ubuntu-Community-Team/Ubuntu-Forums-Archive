---
title: "[SOLVED] Grub Error 21: Primary Slave Hard Disk not being detected except on reboot"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by IbnKuldun on 2008-06-14
Hi guys, first post. So i've been lurking for a while now and have finally come across a problem with which i need help. I've searched for this but can't find a solution for my variant of the problem.

I'll describe the problem simply first and will then go into detail.

Essentially, When I switch on my PC, my BIOS does not detect my primary slave hard disk, but when I reboot it using the restart button it then does. I have to disks on my pc, the primary master is a 40GB disk with XP, and the primary slave is a 160GB disk with ubuntu 8.04. The BIOS is set to auto detect, the disks are IDE connected.

Output from **sudo fdisk -l** is as follows:

```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xda30da30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77536    39078081    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x161e30a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          62      497983+  82  Linux swap / Solaris
/dev/sdb2              63        4925    39062047+  83  Linux
/dev/sdb3            4926       10406    44026132+   b  W95 FAT32
/dev/sdb4           10407       19457    72702157+   c  W95 FAT32 (LBA)

```

Let me know what other info i can provide...i'm really tired of this rebooting business..

if your going to suggest a BIOS upgrade, it won't help. This ([http://support.packardbell.com/uk/item/index.php?i=6909650000&ppn=P660401901](http://support.packardbell.com/uk/item/index.php?i=6909650000&ppn=P660401901) ) is the only upgrade and it doesnt fix large disk detection.

---

### Post by meierfra. on 2008-06-14
Edit: Logos34 suggestions (see next post) sound much better to me than my own. 


I never encountered this problem before, so I'm not sure whether this will 
work:

Reinstall grub (click on FixGrub in my signature). But use

"setup --force-lba  (hd?)" in place or "setup (hd?)"



If this did not help, you should reinstall grub again, but this time without the "--force-lba" (to undo the changes).

Did you try different settings in the bios?

---

### Post by logos34 on 2008-06-14
sounds like the drive is really slow off the mark, and not spinning up in time to be recognized by Bios POST.  But once you press the reset button it's already running, so the problem is avoided.

Maybe check the power management and other drive settings with [hdparm]("http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance").

Or perhaps changing the jumper positions on the drives might help.  If they're set for 'master and 'slave', try setting each drive instead to 'cable select'.  Might also check to make sure you're using 80-wire ribbon cable rather than old 40. (not sure about this part, but thought i'd toss it in). 

maybe it's grub like meierfra said, but what gets me is that it works on restart, which seems to suggest a bios or hardware problem

---

### Post by IbnKuldun on 2008-06-15
I'll have a look at both suggestions and get back to you. I have reinstalled grub before but not with the lba parameters...

will keep you posted

---

### Post by IbnKuldun on 2008-06-25
I tried your suggestion meierfra, but problem didn't solve. In the end i switched the two disks, making the slave the master, and the master the slave. 

No reoccurence of the problem.

Marking this as solved. (Well Kinda). But thanks for your help ppl! :)

---

