---
title: "Unable to boot Ubuntu- Boot Repair"
date: 2022-11-23
forum: Installation &amp; Upgrades
---

### Post by devulas1 on 2022-11-23
Ran boot repair after booting using USB - Try Ubuntu

[https://paste.ubuntu.com/p/ZNCCGq9mVv/](https://paste.ubuntu.com/p/ZNCCGq9mVv/)

I wanted to get some files from my Documents folder. I was able to look at the files but looks like they are not writable. Tried to move them into google drive but it says they are not readable. How do I change the permissions using Try Ubuntu ?

---

### Post by yancek on 2022-11-23
> I wanted to get some files from my Documents folder. I was able to look at the files but looks like they are not writable.  

Generally, copying files FROM a location does not require write permissions while copying TO does.

Boot  repair shows sda partitions with no OS (lines 58, 59).  If sda2 is the filesystem partition where the files you want to copy are located, first mount the partition and try to access it and then as root (using sudo) try to copy to another device.  You can check the permissions of that partition by mounting it and running the command:  ls -l on the mount point.

Reading through the boot repair output, I expect that you are unable to boot the installed Ubuntu as there appear to be a number of problems.  Line 59 shows no OS and  line 64 shows no fstab,   I don't use google drive so I don't know what the problem would be there.

---

### Post by tea for one on 2022-11-23
[COLOR="#0000FF"]Line 80[/COLOR] -sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
[COLOR="#0000FF"]Line 81[/COLOR] - 1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
[COLOR="#0000FF"]Line 82[/COLOR] - 2:538MB:1000GB:1000GB:[COLOR="#0000FF"]ext2[/COLOR]::;

This looks like your internal disk, but I'm surprised to see ext2 rather than ext4?
Can you explain which OS is installed?

---

