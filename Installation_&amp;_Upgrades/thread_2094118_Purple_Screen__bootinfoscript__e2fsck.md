---
title: "Purple Screen / bootinfoscript / e2fsck"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by andrewandrew on 2012-12-12
Hi there

I am getting a purple screen at bootup.
I have used a bootable usb stick to run bootinfoscript and I get the attached results.

Can anyone help me decode these results and suggest some actions for fixing my system.


cheers 
andy

---

### Post by oldfred on 2012-12-12
You have wubi.
 [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But often purple screen is video issues. But it looks like you may have Intel SRT?

Do you boot Windows, from Windows get Windows or Ubuntu, and then get a grub menu? Do not know if this works on wubi or not.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you have Intel SRT I am not sure wubi works. The Intel uses some sort of RAID which complicates Linux installs.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by andrewandrew on 2012-12-13
Hi there,

Just to give you a bit of back ground. I have a dual boot set up on my machine. Initially I was running windows 7 and I followed a link on the Ubuntu site which setup a dual boot loader and installed Ubuntu. 

This has worked fine for about 9 mouths. Recently, when I rebooted I got the purple screen which hangs.

I have been able to boot windows 7 from the boot laoder with no issues.

I have also been able to boot Ubuntu while holding down the shift key which allows me to enter a recovery mode.

Could any one give me a bit more help?

Cheers
Andy

---

### Post by dino99 on 2012-12-13
what you call "purple screen" is in fact "plymouth" (which is required by the system) and its "splash screen" (which can be remove/desactivated to get a verbose boot mode). If you remove "splash" from the boot line, then you can see the possible warnings/errors while booting.

```
sudo gedit /etc/default/grub
```

here erase "splash" and update grub then

```
sudo update-grub
```

that is the "permanent" change, for a single try, simply hit E for editing the selected ubuntu boot line from the grub menu, remove "splash" and hit ctrl+X to continue booting.

---

### Post by andrewandrew on 2012-12-13
Thanks Dino - I will give this a try when I get home tonight.

---

### Post by andrewandrew on 2012-12-13
I am getting the following error message.
Try (hd 0,0):NTFSS: No wubidr
Try (hd 0,1):NTFSS: error:"prefix" is not set.

Any clues?

---

### Post by andrewandrew on 2012-12-13
While booting in recovery mode the process hangs at the point shown in the attached pdf.

---

### Post by oldfred on 2012-12-13
I might try fsck on the wubi file from a liveCD or flash drive. Change example to your partition containing root.disk. sda3?

       [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by andrewandrew on 2012-12-17
I cannot thank you enough - that last suggestion fixed my system and I'm up and running again now.

Cheers
Andy

---

### Post by oldfred on 2012-12-17
Glad that worked. :)

If you find you like Ubuntu, you may want to consider a full partitioned install. Bit of work to reorganize partitions with Windows 7 as it like to use all 4 in MBR partitioning.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)> 
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    

       HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by andrewandrew on 2012-12-17
Hi there - it just failed to reboot again. So I repeated your procedure and I'm running again.

I think I need to migrate to a new partition.  I have created a new partition using Gparted.
Which option should i format it with?

---

### Post by bcbc on 2012-12-17
When you migrate, the script will reformat the target partition as ext4. As long as you have it as ext2/3/4 it will be accepted.

---

