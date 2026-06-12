---
title: "adding a second hard drive with media already on it"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by dbpickering on 2010-09-09
hello all, well i just switched to ubuntu and i love it!! The installation went flawless but i had a second hard drive while i had windows vista to store all of my media, i.e. mp3 and pictures.  Am i able to access the stored information on the second hard drive in ubuntu? Will i need to delete the partition in order to use the second hard drive for future use?  The second hard drive shows up in the disk utility application, but not in the computer/file browser section.  The file system for the second hard drive is hpfs/ntfs.  Any help would be greatly appreciated as i am a complete newb  when it comes to linux.  Thanks for all your help.

---

### Post by fiyer on 2010-09-09
It sounds like you might need to mount the disk so that it is viewable.  Take a look at this tutorial and see if this is what you are looking for:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Hobgoblin on 2010-09-09
> **dbpickering said:**
> The second hard drive shows up in the disk utility application, but not in the computer/file browser section. 

Does it show up on the "places" menu?  If so just click on it.

You can write to NTFS with Ubuntu, so you can leave it as it is.  If you want to make it automount then you will have to tell the system to do so.

---

### Post by oldfred on 2010-09-10
If you want to permanent mount it, you have to add it to fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I actually do not recommend writing into other systems as that system may not work well with other systems writing into it. I read from my windows partition and will write into it if I have to do repairs, but have created a shared NTFS partition for any data I want to read & write from both systems.

---

