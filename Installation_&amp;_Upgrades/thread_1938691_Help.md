---
title: "Help"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by DoctorVell on 2012-03-10
Hi there,

I am currently running Windows and WUBI with a 30gb "partition".  What I want to is have another real partition of 30gb (or so) of Ubuntu 11.10 where it is dual boot and I can go back and forth with copying files from each. Is there a way to copy my files from the "partiton" to a real hard drive.

I know I can copy files from the external hard drive to the "partition" and the "partition" to the external hard drive, but I want to keep all my settings and passwords without having to type them in all over again.

Thanks...if this is confusing, I'll try explain better.

---

### Post by darkod on 2012-03-10
The wubi should see the partitions on the hdd and be able to write to them. But I would recommend to create a common data partition because the users in wubi and the dual boot install will not be considered the same so you might run into permissions issues.

When you are into the dual boot installation, I am not sure it can see the wubi because it is inside a ntfs partition. There should be ways to mount it, but by default it doesn't get detected I think.

---

### Post by DoctorVell on 2012-03-10
What I want to do is create a common partition and then delete the WUBI installation.  I just want the contents of the WUBI installation to go into partition so I don't lose any of my settings, passwords, etc...

Also, can the Ubuntu be 64bit while Windows be a 32bit (on a 64bit machine)?

---

### Post by darkod on 2012-03-10
Yes, ubuntu can be 64bit, it doesn't depend on the windows version.

You could copy all of your home folder because most settings are there usually in hidden folders. But I'm not sure if that would work 100% for all software.

Otherwise you have to understand that it will be a new installation, unrelated to wubi. It will not be an exact copy.

By copying folders, most programs can keep the settings. For example, firefox stores everything inside the profile folder. If you copy your orofile folder to your new installation, you will have all your firefox bookmarks, browsing history, cookies, saved passwords, etc.

But I'm not sure if that can work for all programs.

---

### Post by bcbc on 2012-03-10
You can [migrate a wubi install to a partition]("http://ubuntuforums.org/showthread.php?t=1519354"). This will be an exact copy (except not running off a virtual partition).

---

