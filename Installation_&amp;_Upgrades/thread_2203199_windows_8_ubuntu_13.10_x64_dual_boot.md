---
title: "windows 8 ubuntu 13.10 x64 dual boot"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by slenderwrist on 2014-02-02
Hi , i am trying to install ubuntu 13.10 x64 on my laptop lenovo g710 with windows8 pro. I installed windows 8 manually, boot mode is set to legacy support boot prioirty is set to uefi support. In the install screen after i select "something else" it shows my whole hdd as free.Then i created ext4 and swap partitions within windows8 with minitool partition wizard. Then i tried installing ubuntu again but it still show the  whole hdd as free space. Any help ?

---

### Post by dan-du on 2014-02-02
Windows cannot "see" ext4 and swap partitions, it knows they are there, but it cannot open them, or see if there is files in it.

---

### Post by slenderwrist on 2014-02-02
what i meant was ubuntu installer still shows the whole hdd as free ( after creating ext4 partition within windows with that wizard) , not native english speaker sorry

---

### Post by westie457 on 2014-02-02
@ slenderwrist
Welcome to UF.

Take a look at the links in this post. [http://ubuntuforums.org/showthread.php?t=2198077&p=12893829#post12893829](http://ubuntuforums.org/showthread.php?t=2198077&p=12893829#post12893829)

They explain the issues and give solutions.

Hope this helps.

---

### Post by oldfred on 2014-02-02
Is this an Ultrabook? That uses RAID which can cause installer issues.
If you manually reinstalled Windows did you install in BIOS boot or UEFI boot mode.
Windows does not correctly convert gpt partitions to MBR(msdos) so Ubuntu installer is not sure what you have.

If gpt partitioned fdisk does not work.
sudo parted -l
sudo fdisk -l

---

### Post by slenderwrist on 2014-02-02
it is a laptop. I installed manually in legacy mode. From livecd i opened terminal and typed sudo parted -l. It gives warning :

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. 
However, it does not have a valid fake msdos partition table, as it should. 
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT 
partition tables. Or perhaps you deleted the GPT table, and are now using an 
msdos partitiontable. Is this a GPT partition table? yes/no?

I dont know if its gpt or not, but like i said, i installed win8 in legacy mode.What should i try next ? thanks

---

### Post by oldfred on 2014-02-02
When you installed in Legacy/BIOS/CSM mode, Windows converted drive from gpt to MBR(msdos). Windows only boots from gpt with UEFI. Both Ubuntu & Windows only boot from MBR with BIOS.

But Windows does not convert correctly and leaves the backup gpt partition table. Linux tools see both MBR & backup gpt and are not sure what you have. Use fixparts to remove backup gpt partition table. 
And be sure to install Ubuntu in BIOS mode. How you boot install media is how it installs.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by slenderwrist on 2014-02-02
used fixparts problem solved, thanks

---

