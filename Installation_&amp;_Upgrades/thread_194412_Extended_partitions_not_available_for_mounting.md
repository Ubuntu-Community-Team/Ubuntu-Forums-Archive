---
title: "Extended partitions not available for mounting"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by cjb on 2006-06-11
Hi,
I've got a problem installing Kubuntu 6.06. I downloaded the amd64 LiveCD, and this boots fine.
I want to install this to the hard drive. I already have Win2k running on a partition, and don't want to delete this. I started the install process from the desktop icon. The first four steps (languages, keyboard maps &c.) are fine.
The fifth step presented me with the option of manually editing my partition table, which I took (I'm still wary of resizing partitions on the fly, and I normally like to keep /var and /home separate in case of problems on /).
The first primary partition on this disk is a boot partition, the second is 2k's NTFS partition. I created an extended partition, /dev/sda3, and six logical partitions within it. As far as I can tell, those partitions have been formatted, and the table has been committed.
Then I went on to step six, where I would match partitions to file system mount points. Unfortunately, the only things that are available in the drop-down partition lists are the primary partitions. The extended partitions cannot be selected.

What have I done wrong?

thanks for any help,
James

---

### Post by aysiu on 2006-06-11
Can you post a screenshot of the part where they cannot be selected?

---

### Post by cjb on 2006-06-11
[QUOTE=aysiu]Can you post a screenshot of the part where they cannot be selected?[/QUOTE]

This gives all four available options in the drop-downs, excluding the blank option at the top of the list.
I can't get a picture of the drop-down while open, I'm guessing that KSnapshot doesn't work when the focus is on particular kinds of control?

---

### Post by aysiu on 2006-06-11
To get a menu open, use the time delay on KSnapshot.

Set it to 5 seconds, click to get the snapshot, then open the menu until the 5 seconds is up.

So when you pull the drop-down menu on the partitions, you can't see any of the extended ones?

I'm talking about the drop-down menus on the *partitions*, not the *mount points*.

---

### Post by cjb on 2006-06-11
Thanks for the snapshot tip.
Here's a picture showing the partition dropdown.

---

### Post by cjb on 2006-06-11
And this is what cfdisk thinks when asked about /dev/sda:

```
                                  cfdisk 2.12r

                              Disk Drive: /dev/sda
                        Size: 80026361856 bytes, 80.0 GB
              Heads: 255   Sectors per Track: 63   Cylinders: 9729

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   Linux ext2                          65.81
                            Primary   Free Space                           3.88*
    sda2        Boot        Primary   NTFS             []              57665.99*
    sda5                    Logical   Linux ext3    [kubuntu-root]      4296.50*
    sda6                    Logical   Linux ext3     [kubuntu-usr]      5372.56*
    sda7                    Logical   Linux ext3     [kubuntu-var]      4296.50*
    sda8                    Logical   Linux swap / Solaris              2144.38*
    sda9                    Logical   Linux ext3     [kubuntu-tmp]      2144.38*
    sda10                   Logical   W95 FAT32                         4033.30*
                            Pri/Log   Free Space                           0.49*


     [Bootable]  [ Delete ]  [  Help  ]  [Maximize]  [ Print  ]
     [  Quit  ]  [  Type  ]  [ Units  ]  [ Write  ]

                 Toggle bootable flag of the current partition
```

So can anyone tell me what I'm doing wrong? I'd really like to get Kubuntu on to the hdd.

---

### Post by aysiu on 2006-06-11
To tell you the truth, I don't really know that much about partitions.

I have installed before on extended partitions, so I know it can be done, but maybe there's something special about your situation that precludes it.

Otherwise, if that's not the case, you might want to file a bug report: [https://launchpad.net/malone](https://launchpad.net/malone)

---

### Post by cjb on 2006-06-12
[QUOTE=aysiu]Otherwise, if that's not the case, you might want to file a bug report: [https://launchpad.net/malone](https://launchpad.net/malone)[/QUOTE]

Do you the name of the package to log the bug under? There are a lot of packages with "install" in their name, so I'm a bit confused.

---

### Post by aysiu on 2006-06-12
Well, it would either be Ubiquity (the installer) or GParted (the partitioner). I'm guessing it's Ubiquity.

---

### Post by cjb on 2006-06-13
I restarted the machine and the problem went away - I could see all partitions. How very Windows.

---

