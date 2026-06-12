---
title: "Installation problems, mounted / unmounted partitions."
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Ashfaqur Rahman on 2013-04-04
Hello!
I was using a pirated copy of windows 8. But I have decided that i would not use any pirated soft.Why should I where there are may free soft like ubuntu.
During Installation Ubuntu 12.10 desktop It asks me " Unmount Partition That Are In Use? ".Actually I dont know what mount/unmount is.But reading details I clicked NO as want to install ubuntu in existing partition.I dont want to delete, creat or change partition.After that I Chose Replace Windows 8.Than Installation Process Starts.
But Its Giving This Error Messages one after one!!!

1. " Error Informing The Kernel About Modification To Partition /dev/sda1  - Device of Resource Busy". I clicked IGNORE.Than It gives following
2. " Error Informing The Kernel About Modification To Partition /dev/sda5  - Device of Resource Busy ". I clicked IGNORE.Than following
3. " Partition(s) 2,3,4 on /dev/sda have been written,but we have been unable to inform the kernel of the change,probably because it/they are in use.As a result the old partition(s) will remain in use.You should reboot now befor making further change.". I clicked IGNORE.then following
4. " Faild to creat a swap space ". I clicked OK.

After That Again The Page Comes " Installation Type ".
If I chose " Erase Disk And Install Ubuntu " Same things Happen Again.

What Can I Do Now?

---

### Post by darkod on 2013-04-04
Before starting the installation, did you try opening any of the windows partitions in ubuntu live mode? To look at some data or copy something maybe?

If you try to use a partition, it will mount it. And it can't repartition the disk when partitions are mounted(used).

Also, you say you want it installed in existing partition but linux doesn't install into ntfs partitions. It will need to make its own partition with its own filesystem.

Copy any data you might need from the disk, and I suggest to install ubuntu using the whole disk, there should be a similar option in the auto methods.

---

### Post by Ashfaqur Rahman on 2013-04-04
Before Installation I opened ubuntu " Try " option.From that mode opened my c: d: f: drives.And also tried to open some audio and video file.
Is That The Problem?

---

### Post by darkod on 2013-04-04
Yes it is. Opening the partitions mounts them so that ubuntu can access them. You can't start the installation process without unmounting them. You can simply reboot again with the cd and use the Install option. That will open the installer.

note that if you install replacing win8 or if you install on the whole hdd you will probably overwrite all data on the disk. So, make sure you copy the data you need first.

---

### Post by Ashfaqur Rahman on 2013-04-04
Problem Solved.
I Have Just Restart Computer And Install Again. Ubuntu 12.10 Desktop Installed Successfully.
Thanks.

But I Cant See Any HD Drives In Ubuntu Like Windows. Only Home Folder!

---

### Post by darkod on 2013-04-04
If you used the automatic method, it installs on only one partition (plus a swap partition which doesn't show). So, everything is together in one partition which you can browse in Filesystem.

And just for clarification, the "drives" windows was showing you are partitions on the disk, not separate physical disks. Using the term "drive" as windows is using it is misleading since it doesn't make a difference between a partition and physical disk drive.

---

