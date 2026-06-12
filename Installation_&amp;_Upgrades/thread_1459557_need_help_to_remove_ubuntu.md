---
title: "need help to remove ubuntu"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by ershibbu on 2010-04-21
Guys I was installed ubuntu 9.10 but now i want to remove it..
i have also windows xp. is there any way to remove ubuntu without effecting windows n all the data in hard drive???

because i think "THE WAY IS REMOVE ALL THE DATA IN HARD DISK N CREATE NEW PARTITION" Is it??
if there is any other way the tell me..

---

### Post by doas777 on 2010-04-21
well, first off, did you install ubuntu ***IN*** windows (wubi) or did you boot off a live CD?

yes, uninstalling ubuntu is a simple as formatting over it's partition. you should be able to format the ubuntu partition without altering the windows one, but be careful. 

the problem is usually the MBR and grub. 
after you have gotten rid of the ubuntu partition, try booting from the windowsXP cd and go into recovery mode. then enter the following pair of commands:
```

fixmbr
fixboot

```

then eject the disk and reboot. with luck it should load into window

---

### Post by ershibbu on 2010-04-22
did you install ubuntu ***IN*** windows (wubi)
no 
i installed ubuntu from live cd..
so what is the procedure

---

### Post by doas777 on 2010-04-22
just throw in your windows disk, boot into recovery manager, and run the commands shown above. 
after that, your boot shoudl ignore ubuntu like it's not even there.
then, within windows, you can use the disk manager to delete/format the partitions that ubuntu is currently occupying. 
a word of warning, always be very careful when working with the partitioner.

---

### Post by ershibbu on 2010-04-23
boot into recovery manager

how can i boot in recovery manager??

---

### Post by ershibbu on 2010-04-24
**To use the Windows XP Recovery Console:**

  The Windows XP Recovery Console allows you to:
 
[LIST]
[*]Use, copy, rename, or replace operating system files and folders.
[*]Enable or disable service or device startup when you next start your computer.
[*]Repair the file system boot sector or the Master Boot Record (MBR).
[*]Create and format partitions on drives.
[/LIST]
  Here's how to use the Recovery Console:
 
[LIST]
[*]Insert the Windows XP CD into your CD-ROM drive, and then restart your computer.
[*]On the menu that appears, click **Install Windows XP**.
[*]Press R to repair the selected Windows installation.
[/LIST]
  When you use the Recovery Console, you will be prompted to enter the Administrator account password. If you enter an incorrect password three times, the Recovery Console will close. If the database that contains user account information for your computer is missing or damaged, you will not be able to use the Recovery Console.
  After you enter your password and the Recovery Console starts, type **exit** to restart the computer. The Recovery Console has some other limitations. For details, see Microsoft Knowledge Base article 314058: Description of the Windows XP Recovery Console.


IS THIS METHOD I WILL FOLLOW TO REMOVE UBUNTU??

---

### Post by AntiBodies on 2010-04-24
first thing find your windows xp cd and boot from it

dont repair windows xp that will effectivly reinstall windows xp.. there is another option in that menu that takes you to the recovery console. read the instructions that the windows xp cd gives you

you will be asked for your local administrator password for your windows xp installation. if you dont know this you may need to boot into XP and change this to something you know.. if your PC didnt set one for you sometimes this is just nothing (press enter)

run the commands as above on the command line:
> 
fixmbr
fixboot

this will blow away grub (the ubuntu boot manager) and put back the windows xp boot manager. boot into windows and then you can use the disk managment tool to delete the ubuntu partition and create a new windows ntfs partition (easy) or you can try to resize your existing windows partition to fill up all the space (harder.. most probably need a gparted disk (linux live cd)).. this is a bit easier in vista/win7

cheers

---

### Post by ershibbu on 2010-04-24
thank u all.. now i found the recovery console in xp sp2 and apply the commands now xp is boot and i delete the partition of ubuntu..
many-2 thanks to helping me...

---

