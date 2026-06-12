---
title: "Ubuntu 10.10 and Windows 7 dual boot on two HDDs"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by Valbrozo on 2011-03-30
Hi everybody, 

I'm building a new system which will have two 640GB HDDs and I was wondering what is the best way to go. 
Should I use the first drive to install both operating systems (and of course some storage) and then the second one just for storage 
or is it better to have each operating system on its own drive?
In the second case how do I make bios to give me the option to choose which one I want to boot into?

Thanks a lot!

---

### Post by Sean Moran on 2011-03-30
> **Valbrozo said:**
> Hi everybody, 

I'm building a new system which will have two 640GB HDDs and I was wondering what is the best way to go. 
Should I use the first drive to install both operating systems (and of course some storage) and then the second one just for storage 
or is it better to have each operating system on each own drive?
In the second case how do I make bios to give me the option to choose which one I want to boot to?

Thanks a lot!
You could always install both on both, so to use the primary HDD most of the time, and still have 24GB or so on the secondary drive in case the primary fails or you want to use the secondary HDD in another machine for some reason.  The options are wide open, but my gut feeling tells me that the most reliable way would be to install Windows on /dev/sda1 and Linux on /dev/sda2 and save the second /dev/sdb drive for data, or maybe repeat the same system for that drive, just so you have a system should you ever want to run that drive as a priimary one day.

It's great to have so many choices, isn't it?

---

### Post by Valbrozo on 2011-03-30
Thanks for the quick reply Sean.
Indeed it's great having so many options to choose from but it also gives me a headache :-k
I don't thing I'm going for the both OS on both drives options simply because i just need the extra space. So it is just a matter of how to "arrange" the two OS into the given space.
I'm just wondering if there is a clear answer to this or is it just a matter of taste? I mean there must be some advantages and disadvantages to each case.

---

### Post by Sean Moran on 2011-03-30
> **Valbrozo said:**
> Thanks for the quick reply Sean.
Indeed it's great having so many options to choose from but it also gives me a headache :-k
I don't thing I'm going for the both OS on both drives options simply because i just need the extra space. So it is just a matter of how to "arrange" the two OS into the given space.
I'm just wondering if there is a clear answer to this or is it just a matter of taste? I mean there must be some advantages and disadvantages to each case.
Either way will work, because GRUB can boot to /dev/sda1 or /dev/sdb1 etc., so it is essentially a matter of taste.  Ubuntu only needs 8Gb or even less if you use a separate /home partition or keep your /home directories clean, and Windows 7 runs on 16Gb with Office and a few extras, but you could go 24 or 32 and still only be using 5% of one 640Gb drive.

I'd run both systems from the primary hdd and save the secondary drive for data, but it's really just a matter of taste.

---

### Post by Mark Phelps on 2011-03-30
Actually, I've done this a lot over the years and have found the version with the least problems is installing each OS to its own drive.  That allows each drive to then be bootable on its own, which also prevents updates from overwriting MBRs and boot loaders.

It's literally a 5-minute only process, once you have both installed, to boot from the Ubuntu drive, open a terminal and enter "sudo update-grub", autogenerate a new GRUB menu with the new entries, and then reboot to have access to both OSs.

---

### Post by Valbrozo on 2011-03-30
> **Mark Phelps said:**
> Actually, I've done this a lot over the years and have found the version with the least problems is installing each OS to its own drive.  That allows each drive to then be bootable on its own, which also prevents updates from overwriting MBRs and boot loaders.

It's literally a 5-minute only process, once you have both installed, to boot from the Ubuntu drive, open a terminal and enter "sudo update-grub", autogenerate a new GRUB menu with the new entries, and then reboot to have access to both OSs.

That sounds good, I suppose it's good to know you have an alternative OS to fall back to in case either of the two hard disks fails for whatever reason.
So, in this case I'm thinking of having two partitions on the windows drive (one for windows files, programs etc and another one for storage) but is it possible to make only the storage partition accessible from Ubuntu?
 I suppose both will be NTFS (therefore Ubuntu can access both) but how can I make the windows one not mount  in Ubuntu?

---

### Post by oldfred on 2011-03-30
You can (have to) mount the windows partition read only or mount it hidden so you do not know you have it mounted. Otherwise it will auto mount if clicked on.

The mount point in /mnt will not produce an icon on the desktop, so you do not normally see it. And setting it read only ro instead of rw still gives you permission to copy something from it without fear of accidentally moving or deleting something.

I am not as familiar with all the details but you could set permission so no one has any. Most of the instructions are to set permission more permissive not less.

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

