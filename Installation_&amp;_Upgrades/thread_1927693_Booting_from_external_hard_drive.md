---
title: "Booting from external hard drive"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by EricG1793 on 2012-02-18
I decided to try out Ubuntu for the first time. I didn't want to touch my existing Windows hard drive, so I got my external hard drive, shrunk its only partition, and added a new partition for Ubuntu. I told Ubunto to install "alongside" Windows, and it indicated that it would ask me which to boot, which sounded good to me.

I restarted after it installed, went into the boot menu, and told it to boot from the external hard drive. However, only the original FreeAgent partition showed up in the boot list; no sign of Ubuntu. If I try to boot from the FreeAgent partition, it instead goes to the Lenovo recovery partition in the internal hard drive, presumably because there is no OS in the FreeAgent partition.

I unplugged the external hard drive and tried to boot to the internal hard drive, and an error saying "no such device" came up. Then I plugged in the external hard drive and again told it to boot to the internal hard drive. This time, it gave me all the options for what to boot, and both Ubuntu and Windows run fine.

What I'm hoping to do is to disable Ubuntu taking over the internal hard drive and requiring the external hard drive to be connected to ask which OS. Right now I'm reliant on that external hard drive to boot Ubunto OR Windows. I'd rather just select the device from the boot menu.

So, what I ask of you guys is:

1. How to get Ubuntu to release control of the internal hard drive so it doesn't require the external one to be connected
2. How to get the BIOS to recognize the Linux partition in the hard drive and boot from that through the boot menu (I did choose to encrypt the user data in Ubuntu if that has has anything to do with it)

Thanks for any help you can give!

---

### Post by darkod on 2012-02-18
Plug in the ext hdd, boot ubuntu and in terminal execute:
sudo fdisk -l (small L)

Post the results here, and we'll sort it out fast.

---

### Post by EricG1793 on 2012-02-18
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f691e27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2459647     1228800    7  HPFS/NTFS/exFAT
/dev/sda2         2459648   292098047   144819200    7  HPFS/NTFS/exFAT
/dev/sda3       292098048   312578047    10240000    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   193476544    96738241    7  HPFS/NTFS/exFAT
/dev/sdb2       193476608   211345842     8934617+   c  W95 FAT32 (LBA)
/dev/sdb3       211347454   234440703    11546625    5  Extended
/dev/sdb5       211347456   228438015     8545280   83  Linux
/dev/sdb6       228440064   234440703     3000320   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 3072 MB, 3072327680 bytes
255 heads, 63 sectors/track, 373 cylinders, total 6000640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x992da6a0

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
eric@eric-ThinkPad-L412:~$ ^C
eric@eric-ThinkPad-L412:~$




The 160 GB drive is the internal, 120 GB is the external with Ubuntu.

---

### Post by darkod on 2012-02-18
OK. Boot into ubuntu and in terminal execute:
sudo grub-install /dev/sdb

That will install the grub2 bootloader to the ext hdd, where you want it.

After this you will need to install the windows bootloader on the int hdd. Do you have a windows cd/dvd you can use? If not, you can boot windows and if it's vista or 7 you can make a rescue cd that can reinstall the windows bootloader for you.

If even that is not possible, you can write a generic mbr with linux tools, don't worry. The first thing to try after the grub-install command above, is to create windows rescue cd (if you don't have any), then shutdown. Disconnect the ext hdd, boot with the rescue cd and select to Repair the computer. That will repair the windows boot on the MBR. Sometimes you need to do it 3-4 times until it works, it's how windows repairs things, one at a time.

---

### Post by EricG1793 on 2012-02-18
Thank you VERY much! All is well now. Better than I expected, actually. I have the USB hard drive set above the internal hard drive in the BIOS boot order. So, if the external (Ubuntu) one is plugged in, it boots straight into Ubuntu (well, to Grub to ask me where to go, but that's OK). If the external one is not plugged in, it goes straight into Windows. Perfect.

Thanks again! Here, have a Byte of your favorite food. ;)

---

### Post by darkod on 2012-02-19
No problem, glad you got it sorted out. Please mark the thread as Solved, you can do this in Thread Tools above the first post.

---

### Post by ran1063 on 2012-02-19
I can install ubuntu is my system..config is windows xp,1 gb ddr1 ram 120 gb hard disk..ide bus..help me to recover it

---

### Post by darkod on 2012-02-19
> **ran1063 said:**
> I can install ubuntu is my system..config is windows xp,1 gb ddr1 ram 120 gb hard disk..ide bus..help me to recover it

Please open a new thread, your problem has nothing in common with the original thread.

And explain the problem in more details, do you have ubuntu that is not working and want to recover it, etc.

---

### Post by EricG1793 on 2012-02-19
Sorry about that, I observed a "solved" tag before I posted but I couldn't find it... I even looked in the thread tools, and yes, I was logged in! ](*,) Ah well, it's officially solved now. :)

---

