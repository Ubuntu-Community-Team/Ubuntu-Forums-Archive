---
title: "Restoring the Grub in Ubuntu 9.10 after installing Windows 2008 (64bit)"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by kasun04 on 2009-12-22
I have a Ubuntu 9.10(64bit) installation (with Dual boot with XP) up and running and now I want to install Windows 2008 (replacing XP by 2008) on my machine. How I can restore my grub and start using Ubuntu again.

sudo fdisk -l : gives -->

---------------------------------------------------------------
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       14593    96735397+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7649    40957686   83  Linux
/dev/sda6            7650       11473    30716248+  83  Linux
/dev/sda7           11474       11983     4096543+  82  Linux swap / Solaris
/dev/sda8           11984       14593    20964793+   b  W95 FAT32
---------------------------------------------------------------




br,

Kas

---

### Post by lmarmisa on 2009-12-22
Try to make a backup of the code area (446 bytes) of the Master Boot Record of your sda drive:

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

```

sudo dd bs=446 count=1 if=/dev/sda of=sda.MBRCodeArea.grub.dd

```Move the sda.MBRCodeArea.grub.dd file to a directory of the FAT32 /dev/sda8 partition. I suppose that this partition sda8 will be not used for the new OS and therefore it's a safe place for storing your backup.

Now install Windows 2008 in /dev/sda1.

Start your system with a Ubuntu 9.10 Live CD.

Mount the /dev/sda8 partition and change directory (bash shell command cd) to the directory where the MBR backup file is stored.

Type this command for making a second backup, in this case, of the Windows 2008 MBR:

```

sudo dd bs=446 count=1 if=/dev/sda of=sda.MBRCodeArea.Windows2008.dd

```Now restore the grub backup:

```

 sudo dd if=sda.MBRCodeArea.grub.dd of=/dev/sda
 
```If your restart your system now, you shoud recover your old grub loader, but the new Windows 2008 will be not detected yet.

Finally, open a terminal and type:

```

sudo update-grub2

```Now the new OS will be detected by Grub2.

Best regards,

Luis

---

### Post by kasun04 on 2009-12-22
Thank you very much.Very good explanation. I'll try this and come up with the result.

-Kas

---

### Post by kasun04 on 2009-12-22
There is a different explanation in [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). 
Are you sure about this method, mind you 9.10 got Grub2. Don't we need to re-install grub after installing windows. 

Please let me know whether your method is compatible/already tested with 9.10 grub2 

best regards,
Kas

---

### Post by lmarmisa on 2009-12-23
This method uses a backup of the area code of the MBR.

When you install Windows Server 2008, the code area of the MBR is modified with the binary code of the loader program of Windows. But this Windows loader program is unable to boot the Ubuntu system.

So, you need to restore Grub if you wish a dual-boot system.

This method simply restore the content of the code area of the MBR to the previous bytes of the grub loader program.

If you follow the instructions you will have two backups:

[LIST=1]
[*]The MBR code area backup of the grub loader.
[*]The MBR code area backup of the Windows loader.
[/LIST]
So, you could restore both loaders if you wish.

This method works not only for grub2 but also for grub (except sudo update-grub2, of course).

BTW, you can check your grub version with the command **grub-install -v**:

```

lmarmisa@UBUNTU910:~$ **grub-install -v**
grub-install (GNU GRUB 1.97~beta4)

```GRUB 1.97 or something like that means grub2.

Best regards,

Luis

---

### Post by ysaric on 2009-12-23
Is there any place that has something of a step-by-step of installing Windows after you've installed 9.10?  I have an installation of 9.10 where I'd really rather not have to start totally from scratch but instead set aside some hard drive space for Windows (Vista 64-bit) and set it up to dual boot.

The steps described above seem one step ahead of where I am, which is to say I don't have any hard drive space yet specifically set aside for the Windows installation (having using the default file structure recommended by Ubuntu when I installed it), and since this is my first time trying something like this in Ubuntu it would be great to get a bit of newbie advice.  For example, the detailed instructions in the second post in this thread . . . mechanically I might be able to follow those steps, but it is definitely doing things I am unfamiliar with.

Thanks much in advance for any information provided.

---

