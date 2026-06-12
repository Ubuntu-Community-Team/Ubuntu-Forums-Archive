---
title: "Win7 boots immediately after installing Ubuntu 12.04"
date: 2012-09-15
forum: Installation &amp; Upgrades
---

### Post by litchz on 2012-09-15
Hello. I just installed Ubutu alongside Windows 7, and I'm having trouble with it. 

Before I start, let me say I've googled the problem, but the problems I found weren't like what happened to me, so I decided to ask for help before trying something and screwing things up further. I know this may be redundant, and maybe my problem is just like everybody else's and I'm just overreacting, but I really don want to lose Windows or any of the data on that partition. 

Here's what happened:

I downloaded the .iso and the usb installer suggested by [here]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows"), and followed this tutorial step by step. However, when I tried to boot the USB to install it, I kept getting a command line screen, saying that no kernel was found. I downloaded both the .iso and the usb installer and tried again, and got nothing. Repeated 3 or 4 times, then gave up and went to google. 

Someone suggested [this usb creator]("http://www.linuxliveusb.com/"), and it worked for me. Finally, I got to the Ubuntu 12.04 Desktop installation  screen. I chose to install Ubuntu alongside Windows, on a partition, and just went ahead with the suggested partition. Ubuntu installed without problems, and after the process was finished, it asked to reboot. 

However, after the reboot, no OS selection screen was shown. Instead, Win7 started to load automatically. But already at the little dancing logo screen that says "Starting Windows", it crashed and rebooted once more. This happened 2 times, at which point I decided to go on recovery mode (since the computer had been rendered pretty much useless). 

After this process was complete, Windows booted without issue. However, I still got no OS selection screen. I can, however, select the OS if I stop the auto-boot by pressing F12 and select the USB drive, which I find odd.

I'm afraid the recovery process may have messed up with GRUB/GRUB2 (don't know which one), and I'm a bit weary to go ahead and try to fix it. 

Again, sorry for taking your time of this is an easy-to-fix issue, and thanks for helping!

---

### Post by darkod on 2012-09-15
Sometimes when you install from usb the ubuntu installer can put grub2 on the usb stick since that is what you booted from. You only need to boot once with the stick and install grub2 to the MBR of the disk.

But what is this recovery process you are talking about? The windows built-in recovery partition? If you ran that, it would usually delete everything on the disk and return it to factory state.

Are you sure you still have ubuntu, can you boot it now with the stick connected? If you can, simply post the output of:
```
sudo fdisk -l (small L)
```

and we can tell you how to install grub2 to the MBR of the HDD.

---

### Post by litchz on 2012-09-15
Hi, sorry for taking so long to reply. 

I was also afraid the "recovery" (my mistake, it was actually a repair process) process would wipe my hard drive clean,  but when it started, there was a note saying no files or data would be lost. It was very fast, despite a warning that it could take over an hour. I believe it was [this(link), ]("http://www.sevenforums.com/tutorials/681-startup-repair.html")which makes sense, since it serves to repair, along with other files, the MBR file.

I can boot Ubuntu from the USB. Here's the output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fe1b5bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2         3074048   562685833   279805893    7  HPFS/NTFS/exFAT
/dev/sda3       945999872   976773119    15386624   17  Hidden HPFS/NTFS
/dev/sda4       562685950   945999871   191656961    5  Extended
/dev/sda5       562685952   937717759   187515904   83  Linux
/dev/sda6       937719808   945999871     4140032   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1999 MB, 1999520768 bytes
32 heads, 63 sectors/track, 1937 cylinders, total 3905314 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0c2460aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     3904991     1952464+   b  W95 FAT32

```

---

### Post by darkod on 2012-09-16
So, boot ubuntu again with the stick, and in terminal execute:
```
grub-install /dev/sda
```

As you can see in the fdisk results, the /dev/sda is the hdd and /dev/sdb is the usb. With the above command you will install grub2 to the MBR of the hdd.

Reboot without the stick and it should work fine.

---

### Post by litchz on 2012-09-16
Thank you! I'll try this right now!

---

