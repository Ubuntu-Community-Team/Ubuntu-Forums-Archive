---
title: "grub2 karmic &amp; fedora 9 dualboot"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by medivh on 2009-09-17
I have a problem about dualbooting Karmic (Alpha 5) and Fedora Core 9 on my laptop (Acer 6935G).

I have installed Fedora first on a seperate partition and installed grub on that partition instead of MBR. Then I have installed Karmic on another partition and installed Grub2 on MBR. After booting into Ubuntu I used update-grub command to make the system find fedora kernel and add it to grub.cfg. It actually did add the Fedora 9 to the list of operating systems but when I try to boot it I get the following error.

```

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

The only way I can boot into both OS is chainloading grub from grub2 bye manually editing grub.cfg.

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00070884

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   b  W95 FAT32
/dev/sda2            2551        4462    15358140   83  Linux
/dev/sda3   *        4463        6374    15358140   83  Linux
/dev/sda4            6375       60801   437184877+   5  Extended
/dev/sda5            6375        6896     4192933+  82  Linux swap / Solaris
/dev/sda6            6897       11358    35840983+  83  Linux
/dev/sda7           11359       13270    15358108+  83  Linux
/dev/sda8           13271       60801   381792726    b  W95 FAT32

```

sda1 = reserved for future installation of Windows.
sda2 = ubuntu root
sda3 = fedora root
sda6 = ubuntu home
sda7 = fedora home
sda8 = general purpose storage

After booting into FC9 by chainloading I rebooted system to test Ubuntu. I have faced to a filesystem error telling me to manualy run a file system check due to some system time related issue. I guess it is about the keeping local time by changing the hardware clock. How can I fix this issue.

---

### Post by khughitt on 2009-09-17
Hello,

I would check your /etc/fstab file for Fedora. I've noticed that a lot of times after installing a new OS next to Fedora, the volume UUID's change, and it causes Fedora to panic and mount as read-only. You might start by commenting out everything except the ones used by Fedora directly. Then, if you are specifying partition locations using "/dev/sdxx" syntax, try using UUID's instead.

In karmic you can check a device's UUID using the command:

```
sudo blkid /dev/sda3
```

In Fedora, I think it's something like 

```
sudo /sbin/vol_id -u /dev/sda3
```

(try "locate vol_id" if that doesn't work).

Regarding the time issues with Ubuntu, I ran into that a few days earlier. The solution seemed to be just to wait it out: I tried all sorts of things initially: manually running fsck, modifying mount properties, etc. but nothing worked. When I came back the next day, everything was alright.

---

### Post by medivh on 2009-09-17
It appears like updates broke my karmic setup. Now it will take some time for me to do what you said. Or could someone tell me an easier way to multiboot these os or direct me to resource where I get find instructions.

---

### Post by VMC on 2009-09-17
Here's what I did to boot Fedora 11. I installed Fedora without it writing mbr to anything. Then I copied the "/boot" partition that Fedora thinks I needed, and put that inside /boot at "/" partition. Then I deleted that "/boot" partition and of course use karmics "/boot". Fedora11 anyway refuses to install without setting a ext3 "/boot" partition.

Then I issues update-grub from karmic. It misses the initrd so I had to add that myself. Here's what mine looks like:
```
menuentry "Fedora release 11 (Leonidas) (on /dev/sda8)" {
        insmod ext2
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3
        gfxpayload=1024x768
        linux /boot/vmlinuz-2.6.30.5-43.fc11.i686.PAE rhgb root=/dev/sda8
        initrd /boot/initrd-2.6.30.5-43.fc11.i686.PAE.img
}
```

---

