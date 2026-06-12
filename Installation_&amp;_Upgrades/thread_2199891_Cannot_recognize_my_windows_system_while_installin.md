---
title: "Cannot recognize my windows system while installing ubuntu"
date: 2014-01-16
forum: Installation &amp; Upgrades
---

### Post by yuanhangliu1 on 2014-01-16
[COLOR=#000000]I want to install ubuntu 13.01 to my machine which already has windows 7 on it. While installing ubuntu, I didn't see the 'install ubuntu along side windows'. The windows system cannot be recognized. I know this is not a new issue. I tried many methods, including Boot-Repair. The problem still cannot be fixed. Cound anyone help me on this? My Boot-info summary generated from boot-repair is [/COLOR][http://paste.ubuntu.com/6759383/](http://paste.ubuntu.com/6759383/)

---

### Post by mastablasta on 2014-01-17
you need to:

1. defragment the disk (2 times just to be sure)
2. backup all files (you an use redo backup to image disk to external drive for example) 
3. use windows disk manager to resize one of the parittions and leave the newly creted space (where Ubuntu will go) unformatted.

hopefully you will then get install along side option. if not then:
- choose "something else"
- create one root (/) partition with ext4 format in empty unformatted disk space
- create one /swap partition (e.g. the size of your ram - if you have more than 4GB ram just create 4GB partition). i think this will show as swap format anyway. 
- continue with install
- when it asks where to put GRUB (linux boot loader), you put it on /dev/sda1

if oyu want to just give linux a tryout then you can use virtualbox. here is a nice howto with pics: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by slooksterpsv on 2014-01-17
All GPT partitioned computers I've had where I've tried to install Linux hasn't shown an Install Alongside Windows. But I do have to say I always resize my Windows partition to install Linux.

Now one thing I do want to mention is if it really is a GPT partition:

I installed grub on /dev/sda - screwed easily booting into Windows.
I installed grub on /dev/sda4 - this is where my root file system for Linux was for my systems (notated as / during partitioning) and that's worked best.

If /dev/sda1 is the EFI Boot partition, and that works, that'd be better.

---

### Post by oldfred on 2014-01-17
You seem to have a standard Windows 7 BIOS install with MBR(msdos) partitioning. 
But you have this:
>  GUID Partition Table detected, but does not seem to be used.



That is common if you installed Windows 7 over an UEFI system. Windows converts to MBR from gpt but leaves the backup gpt partition table. You need to remove backup gpt data. Linux sees both gpt & MBR and gets confused on what you have or want.

 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

