---
title: "Can installation on external HDD from one machine be used on another?"
date: 2017-01-27
forum: Installation &amp; Upgrades
---

### Post by martemarziano on 2017-01-27
Hi everyone,
I wondered if I install Ubuntu on an external hard drive using one machine, can that installation be used to boot up another machine with different hardware specs?

---

### Post by gdesilva on 2017-01-27
You might get away with other devices but if the graphics cards are different it is going to screw up your display.

---

### Post by martemarziano on 2017-01-27
Alright, it's good to know. The last thing I want is screwing things up! Thank you!

---

### Post by yancek on 2017-01-27
In that situation, the most common problems will be graphics and network and if you have proprietary drivers installed for your graphics card on the system on the external drive, it will definitely be a problem.  If you don't have any proprietary drivers, it should work.  You install the Grub bootloader to the MBR of the external drive and then on the new machine, select that drive in the BIOS, boot priority.

If you have UEFI on either machine it gets a little more complicated.

---

### Post by sudodus on 2017-01-28
- An ***installed Ubuntu system is quite portable between computers***. As described by *yancek*, you should avoid proprietary drivers.

- A ***persistent live*** system is an alternative - more portable, but not as upgradable as an installed system.

See this link and links from it for more details,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by martemarziano on 2017-01-28
Thank you yancek and sudodus for the instructions. I will try to work something out. Hope I can get back to you for more advice if I encounter any problem,

---

### Post by martemarziano on 2017-01-28
I tried to install Ubuntu on the external hard drive as you normally would do, following the installer and pointing it to some partition of the drive but the installer crashed time and again refusing to install the bootloader, I made an EFS partition for the bootloader and then the installing was successful. But I could only boot up from the external drive only once and after that it  has remained unbootable. I would be grateful for any suggestion as to how solve this problem.

---

### Post by sudodus on 2017-01-29
You find tips what to do 'from scratch' as well as shortcuts (compressed image files) to create a portable installed system that can boot in UEFI and BIOS mode at this link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

But

- Windows is able to damage 'competing' UEFI boot systems. So it is a good idea to disconnect the external drive, when you intend to boot into Windows.

- Major upgrades of Ubuntu including ***grub*** can also damage the ability to boot in both UEFI and BIOS mode. So these systems are sensitive. But it should continue to work in the mode, that you were running, when you upgraded it.

---

### Post by martemarziano on 2017-01-29
Thanks sudodus for the link! I should do some reading before I attempt anew from the scratch and hopefully with correct partitioning this time. I'll get back to you with the result.

---

### Post by sudodus on 2017-01-29
Good luck :-)

---

### Post by martemarziano on 2017-02-02
hi again, 
This [https://postimg.org/image/xxwbegjgh/](https://postimg.org/image/xxwbegjgh/) is an image from the partition table of an external drive onto which I have tried to install Ubuntu (/dev/sdb2-4). Unfortunately after several attempts it still remains unbootable. I took care to remove the internal drive at the time of installation and rebooting from the external drive. I must be doing something wrong since this procedure should be quite straight forward. I will be grateful for any suggestion as to how I can proceed from here to make it work.

---

### Post by sudodus on 2017-02-02
There might be a problem with the location of the EFI partition and the boot partition (where the grub files reside, in this case in the root partition, #3). They might be too far from the head end of the drive.

Maybe it works better if you create the big NTFS partition at the tail end of the drive (as partition #1), and after that create the EFI partition and the root partition near the head end of the drive. You can use ***gparted*** for this purpose. Compare how the partitions are located in persistent live drives made with mkusb: [mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by martemarziano on 2017-02-02
Sure, you are right. I actually tried to move the NTFS block to the end of the drive but since it is quite a big chunk the gparted's timer showed something like more than 9 hrs to do that. So I stopped the procedure. Can it really take so much time to move that partition?

---

### Post by sudodus on 2017-02-02
Yes. And it is risky too. It would be better to back it up to another drive, and after that copy it back to a fresh partition at the new location. The bonus is that you get a backup copy.

---

### Post by martemarziano on 2017-02-02
Well, maybe it would be a better idea to get an ssd and start everything from scratch, since I don't have another drive that can accommodate the amount of data I have on that NTFS partition. Among other things, I have a disk image from another Windows pc there which I don't want to lose.

---

### Post by sudodus on 2017-02-02
Yes that is a good idea. I suggest that you get a separate external USB 3 box for 2.5" SATA drives and an 'internal SSD'.

Check that there is a separate power supply for the external box. Otherwise, if powered only via USB, it might be shut down before finishing writing, and the file system might get damaged.

---

### Post by martemarziano on 2017-02-02
Alright, I will do that. Thank you for all the feedback and for putting me back on the right track again. I'll let you know when it's all done and hopefully this time everything will work.

cheers,
Marte

---

### Post by sudodus on 2017-02-03
Good luck :-)

---

### Post by martemarziano on 2017-02-03
Thanks, I'll need that!
Just wanted to ask another question before I go ahead with it all. If I use gparted to copy all the partitions of a source disk where I have Ubuntu installed one by one to a target disk, will that result in a bootable system?

---

### Post by sudodus on 2017-02-03
I have used ***gparted*** many times to create and to move partitions within the same disk, but I have not used it to copy or clone partitions. I hope and think someone who knows will answer.

But I know that you can use ***Clonezilla*** to create a cloned drive, that is bootable like the original drive, provided that you clone the whole drive (not separate partitions), and that the target drive is at least as big as the original drive.

If you copy the files or clone separate partitions, you must also install a ***bootloader*** (grub). But if it is 'only' a backup of the content of your Windows partition, you need not have it bootable. You can create Windows recovery disks separately.

---

### Post by martemarziano on 2017-02-03
Currently, I have a dual boot Ubuntu/Mint on my pc. I thought to just copy the Ubuntu partitions to a new disk with gparted and make it bootable. I don't exactly know how to do the latter. Can "boot repair" be used from a live system to install the grub on the new disk?

---

### Post by sudodus on 2017-02-03
Yes. You can use Boot Repair (or do it manually) from a live drive.

---

### Post by martemarziano on 2017-02-03
Or maybe make a clone of the whole disk with Clonezilla, delete the Mint partition and make it bootable? 
Better still would be a fresh installation of Ubuntu. Is there a way to "transfer" all the software i have already installed on my current Ubuntu and the configurations to the new installation?

---

### Post by martemarziano on 2017-02-03
> **sudodus said:**
> Yes. You can use Boot Repair (or do it manually) from a live drive.

Alright, it's good to know. I have to think through the options and choose one. What would you have done?

---

### Post by sudodus on 2017-02-03
It is often the best option to make a fresh installation. You can keep tweaks and personal files, if you copy the /home directory to a separate **home partition** on the new drive, and point to it when you make the installation 'Something else' at the partitioning page. But you must reinstall the software packages.

-o-

If the computer boots to Ubuntu's grub menu you can remove the mint partition and the cloned system will still be bootable. If it boots to Mint's grub menu you must fix the bootloader, but it is easy before you remove mint:

Select Ubuntu and when it is running, use this command

```
sudo grub-install /dev/sdx
```

where x is the drive letter. It makes things easier, if there is no other drive present, that might cause confusion.

You can use Boot Repair too.

---

### Post by martemarziano on 2017-02-03
I think I get the picture. So I first make a partition in the new drive to copy my current /home directory to. Then at the time of the installation  I choose "something else" to come to the partitioning page. Once there I make a partition for the / directory and mark the partition containing my " former" home-directory as the new /home. 
Sorry, I know that all this is very basic stuff for you and I really appreciate you taking your time to answer my questions. Thanks!

---

### Post by sudodus on 2017-02-04
In this case you need two partitions with the ext4 file system and one swap partition.

1. **/** (slash) alias root partiiton

2. **/home** alias home partition

3. and a small **linux swap partition**.

---

### Post by martemarziano on 2017-02-04
Thank you so much for your invaluable guidelines! I will get on with it now.
greetings,
marte

---

