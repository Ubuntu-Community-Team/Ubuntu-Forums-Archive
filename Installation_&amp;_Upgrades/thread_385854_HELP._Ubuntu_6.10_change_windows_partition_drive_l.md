---
title: "HELP. Ubuntu 6.10 change windows partition drive letters"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by 6rzes on 2007-03-16
Before I install Ubuntu I had 2 partition ( c: with Windows XP x64, and d:). I have created a new one and install on it Ubuntu. After that my c: drive letter change to d: and d: to c: and i cannot boot Windows ;(.

---

### Post by lukew on 2007-03-16
> **6rzes said:**
> Before I install Ubuntu I had 2 partition ( c: with Windows XP x64, and d:). I have created a new one and install on it Ubuntu. After that my c: drive letter change to d: and d: to c: and i cannot boot Windows ;(.

Hi;

Try this one:

```
http://support.microsoft.com/kb/69013

```

---

### Post by 6rzes on 2007-03-16
It doesn't work. It only cause that I have to fix GRUB.

---

### Post by lukew on 2007-03-16
> **6rzes said:**
> It doesn't work. It only cause that I have to fix GRUB.
I would fix windows first. Then boot with a live cd and fix grub then.

---

### Post by 6rzes on 2007-03-16
I dont' want to install windows again. It is possible to change windows drive letters from linux?

---

### Post by 6rzes on 2007-03-16
Anybody knows?

---

### Post by 6rzes on 2007-03-17
help!

---

### Post by Herman on 2007-03-17
Hello there 6rzes,
Fortunately for you, Windows drive letters are irrelevant and meaningless. 
You boot.ini file in Windows doesn't even use partition letters, it uses numbers. :)

You can boot into your Windows install by making your own [Windows XP boot floppy disk.]("http://support.microsoft.com/kb/305595/EN-US/")
This is no ordinary Windows boot floppy, this one has its own copy of NTLDR, NTdetect.com, and boot.ini on it. This will boot Windows almost no matter what.
Since floppy disks are FAT32, it is easy to edit the floppy disk from Linux to change the partition number or (disk number) for Windows in the boot.ini in the floppy disk. Now you can boot Windows no matter what the partition number has been changed to.
You will just need a blank floppy disk and access to a friend's Windows XP computer to make the floppy disk with. You must format the floppy disk exactly the way the link tells you or it probably won't work.
Please post here your output from sudo fdisk -lu command so I can tell you how to edit the boot.ini on the floppy disk, and later your Windows XP boot.ini file, then it will be all fixed. ```
sudo fdisk -lu
```Regards, Herman :)
EDIT: I have a question, if you can not boot Windows in the fist place, then how do your know, (or what makes you think), the Windows partition numbers have changed? Did you use Partition Magic? > Before I install Ubuntu I had 2 partition ( c: with Windows XP x64, and d:smile:. I have created a new one and install on it Ubuntu. After that my c: drive letter change to d: and d: to c: and i cannot boot Windows ;(. 

---

### Post by mcduck on 2007-03-17
Linux can't change drive letters for Windows, that job is what Windows should do itself. If your drives are not partitions but actually different disks then it is possible to remap your drives in Grub which should provide the same result. Could you post output of 'sudo fdisk -l' here so I can try to give you the right entry for Grub?

---

### Post by 6rzes on 2007-03-17
I know because i chceck it in Windows recovery mode and in Windows Live Cd, 

Sudo fdsik -lu
Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390719855 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End              Blocks   Id  System
/dev/sda1              63          40965749    20482843+   f  W95 Ext'd (LBA)
/dev/sda2   *    40965750   380483459   169758855    7  HPFS/NTFS
/dev/sda3       380483460   388676609   4096575   83  Linux
/dev/sda4       388676610   390716864  1020127+  82  Linux swap / Solaris
/dev/sda5   *       15183      40965749     20475283+   7  HPFS/NTFS

Windows is installed on sda5

---

### Post by mcduck on 2007-03-17
You could try changing your /boot/grub/menu.lst so that the windows entry would be like following:

```
title		Microsoft Windows XP
map (hd0,5) (hd0,2)
map (hd0,2) (hd0,5)
root		(hd0,2)
savedefault
makeactive
chainloader	+1
```
That should swap the places of sda2 and sda5 for Windows.

---

### Post by 6rzes on 2007-03-17
After that modyfication of /boot/grub/menu.lst error apear when i try boot windows:
Error 13: Invalid or unsupported executable format

---

### Post by mahiyar on 2007-03-17
The comment * in fdisk indicates boot partition, as I can see there are two boot partitions sda2 and sda5, could that be the cause of your problem. Can you try booting after removing the bootable option from sda2?

---

### Post by Herman on 2007-03-17
Thank you for the fdisk -lu output, 6rzes, here is my analysis of the situation,```
sudo fdisk -lu
Disk /dev/sda: 200.0 GB, 200048565760 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390719855 sectors
Units = sectors of 1 * 512 = 512 bytes

Device_____Boot______Start_______End______Blocks______Id______System
/dev/sda1_______________63__40965749____20482843+___f W95_____Ext'd (LBA)
/dev/sda5_____*______15183__40965749____20475283+_____7_______HPFS/NTFS _21GB_Windows
/dev/sda2_____*___40965750_380483459___169758855______7_______HPFS/NTFS_174GB_data?
/dev/sda3________380483460_388676609_____4096575______83______Linux_______4GB_Ubuntu
/dev/sda4________388676610_390716864_____1020127+_____82______Linux swap__1GB
``` First try what [mahiyar]("http://ubuntuforums.org/member.php?u=213529") suggested and see if that helps. As far as I know, you cannot boot Windows in a logical partition unless you have the Windows boot files in another Windows partition which is a primary partition. They call it a 'boot' partition, but it is not the same as what we call a /boot partition in Linux. That is the default way for Windows to set up a dual boot. When people have had a Windows dual boot set up like that when something happens to the primary 'boot' partition they lose the use of their other Windows in the logical partition as well.
This does not look like the same problem, because of the presence of the extra boot flag. That means I believe you that something else happened and your Windows should contain its own NTLDR and other files needed to boot with, so this time we can save it.

6rzes, I presume you have a backup of all the data in that 173GB NTFS partition? :)
(I am guessing that's a data partition?). I think the only way out of this will be to delete all that data and then we'll need to delete the empty partition too. Then we'll have to copy and paste your Windows partition around a couple of times to get it back where it is, but as a primary partition, and the partition number /dev/hda1 again.

That's what I think is going to be needed, then you can make a new data partition again. If you don't already have all your data backed up, now is a good time to do so, you must have all your data backed up at all times anyway. :)
 
Regards, Herman :)

---

### Post by beingboston81 on 2008-04-03
This has happened to me too recently when installing 8.04 beta. I know beta is not for production and I was able to backup and restore all my files, but jeez this has happened to me twice now!

Steps:
I have one 250gb Sata drive i'm trying to dual boot, in the end it'll have three partitions (Ubuntu, windows, data)

1. in the windows install when you have to choose a partition I delete all three partitions (including swap) and create one 40 gb partition for windows.

I got through the windows install with no big changes (i'm using a windows xp pro sp2 corp disk)

2. I'll create the data partition in Windows Disk Manager and start copying my files over

3. once done i'll put in the Ubuntu CD and boot into it.

4. i'll go through the installation and when it comes to the partition i do it manauly
     a. I'll create a swap first (400mb)
     b. i'll use the remainder of the drive for the Ubuntu (~30gb)

Ubuntu will install just fine, but when I go into windows I get an error saying that it cannot find the HAL.DLL file.

This has happened twice now! Any ideas????? I'm not having fun rebuilding my computer's OS's every 5 hours.


Thanks, Tim

---

