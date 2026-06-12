---
title: "Getting Grub up after Windows XP reinstall"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by bbqbuff on 2006-07-17
I hope this is the right forum to post this! Here's the short story:

1.) Installed Windows XP (hdb1).
2.) Installed Ubuntu - Dapper Drake (hdb2).
3.) Backed up my Windows files on Ubuntu (mounted the NTFS drive and just copied things over).
4.) Reinstalled Windows XP (Reformatted the C: and slip it in two, now it reads it as C: = hdb1 and D: = hdb5). 
5.) Windows rewrote over the mbr so grub doesn't boot up. 

Yes my hard drive is set to slave, I was too lazy to switch it to master!

I basically just want to access the files I backed up on my Ubuntu install but I can't because Grub won't boot and I can't mount the drive. Here's what I tried:
```

root@ubuntu:~# fdisk -l

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
102 heads, 51 sectors/track, 75109 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9842    25599016+   7  HPFS/NTFS
/dev/hdb2            9843       51601   108615159    f  W95 Ext'd (LBA)
/dev/hdb5            9843       51601   108615133+   7  HPFS/NTFS

root@ubuntu:~# mount /dev/hdb2 /mnt/hdb2
mount: you must specify the filesystem type

root@ubuntu:~# mount -t ext3 /dev/hdb2 /mnt/hdb2
mount: wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@ubuntu:~# grub-install /dev/hdb1
/dev/hdb1 does not have any corresponding BIOS drive.


```

Anyone have any Ideas how I can mount the old linux drive or get grub working so I can boot back in?

Thanks in advance!

---

### Post by mogelhead on 2006-07-17
I also had this problem when I first installed Ubuntu and then Windows. I used this HOWTO to solve it: [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

I also got the same error as you when I tried "grub-install /dev/hdb1": /dev/hdb1 does not have any corresponding BIOS drive.

But there are a couple of other options, I used "[Using the LiveCD and Overwriting the Windows bootloader]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")".

A side note: The output of your "fdisk -l" seems strange to me. Normally you should see your linux partition and your linux swap partition listed there.

---

### Post by bbqbuff on 2006-07-17
Thanks mogelhead, I'll try that when I get home. When I first looked at the output of fdisk -l, I was afraid that Windows did something and caused me to lose all my data that I backed up in Ubuntu.

I'll be sure to post an update of what happens.

---

### Post by atrophic on 2006-07-17
> **bbqbuff said:**
> 
```

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9842    25599016+   7  HPFS/NTFS
/dev/hdb2            9843       51601   108615159    f  W95 Ext'd (LBA)
/dev/hdb5            9843       51601   108615133+   7  HPFS/NTFS

```


Should hdb2 and hdb5 really start and end in the same place? That doesn't look very promising.

If you boot to the live cd you can use Grub's Command Line Interface to restore grub to the MBR.

---

### Post by bbqbuff on 2006-07-17
> **atrophic said:**
> Should hdb2 and hdb5 really start and end in the same place? That doesn't look very promising.

I never noticed that until you pointed that out. My hopes have been crushed and I fear I will never get my data back.

---

