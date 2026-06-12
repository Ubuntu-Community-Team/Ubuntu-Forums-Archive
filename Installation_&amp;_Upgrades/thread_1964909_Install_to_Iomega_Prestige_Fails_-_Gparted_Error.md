---
title: "Install to Iomega Prestige Fails - Gparted Error"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by cshemby on 2012-04-24
I recently purchased a 1tb Iomega Prestige external hard drive and have been trying to install Ubuntu to it. The first issue is that when running the live CD the installation partition editor only reads 125 gb. The installation continues up until it tries to write the partitions. At this point an error occurs and gparted closes. Can anyone help with this?

---

### Post by darkod on 2012-04-24
Boot into live mode, and with the external connected, in terminal post the output of these two commands:
sudo fdisk -l (small L)
sudo parted /dev/sda print all

Lets see what does it say about the partitions.

---

### Post by cshemby on 2012-04-24
Darko,

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xdaf34c6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256      499967     1998848   83  Linux
/dev/sdb2          500222   244189439   974756872    5  Extended
/dev/sdb5          500224    12499967    47998976   82  Linux swap / Solaris
/dev/sdb6        12500224    53124863   162498560   83  Linux
/dev/sdb7        53125120   244189439   764257280   83  Linux
ubuntu@ubuntu:~$ sudo/parted/dev/sdb print all
bash: sudo/parted/dev/sdb: No such file or directory

---

### Post by darkod on 2012-04-24
It shows linux partitions on it.

The only issue I can see is that the disk uses sectors of 4KB. That is a new format but usually used for disks larger than 2TB.

The older disks work with sectors of 512B. Depending how the disk is manufactured, it might now recognize it correctly.

I think the answer will be around this issue. But I have no idea what the solution would be right now.

The internal disks with 4KB are usually manufactured with emulation so to the OS they still look like 512B.

This one looks like 4KB without any emulation.
Sector size (logical/physical): 4096 bytes / 4096 bytes

---

### Post by cshemby on 2012-04-24
thanks, I'll look into that issue

---

### Post by darkod on 2012-04-24
Seems like you were unlucky to select this 4K disk.

This thread for example is full of people complaining that even MS servers can't backup to external disks with 4K sectors.
[http://social.technet.microsoft.com/Forums/en-US/windowsbackup/thread/5d9e2f23-ee70-4d41-8bfc-c9c4068ee4e2/](http://social.technet.microsoft.com/Forums/en-US/windowsbackup/thread/5d9e2f23-ee70-4d41-8bfc-c9c4068ee4e2/)

Google is full of similar complaints. Not sure if you can find a solution for this, but it's worth googling for it.

---

### Post by cshemby on 2012-04-25
Thanks for your help. I have been looking into it as well without much luck. The only suggestion that I haven't tried has been to disconnect my internal hard drive before I run the live cd and only pick up the external drive. A professor here suggested that but he is a VMWare guru so we'll see.

---

### Post by darkod on 2012-04-25
Another idea might be to wait few more days until 12.04 LTS is officially released (I believe tomorrow). It will be the latest long term supported release and it might include some 4K compatibility that is missing in current releases. Since both internal and external disks of large capacity are moving towards 4K that would make some sense.

If you are OK with using the manual install option, I would still try installing on the external once more. We already saw there are some linux partitions there, if those are from previous installs I would do:
1. Wait for the 12.04 LTS release and burn a cd with it.
2. Check it out in live mode first, if everything runs OK on your machine.
3. Start the install and use the manual way. Delete all partitions currently on the disk (if you don't have any data to save there).
4. Create the install you want, root + swap partitions, or root + swap + /home, etc.
5. Make sure grub2 bootloader is selected to go to the ext disk.
6. If the first restart doesn't show up grub2 when booting from the ext, use live mode and try to add grub2 manually (ask help if you need it for this).

That would cover the "standard" options, without going into too much complicated stuff. Just sort of as a last try before really digging into this problem.

---

