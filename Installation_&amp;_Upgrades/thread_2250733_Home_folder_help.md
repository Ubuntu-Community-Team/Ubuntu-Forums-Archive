---
title: "Home folder help"
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by cowboy7305 on 2014-10-30
Can some one help please 
i play around with ubuntu and some other derivatives of it like mint on Zorin but keep coming back to ubuntu
but every time i load up some other O/S i have to reinstall all my home folder which has all my FFOX Thunderbird and every thing else i want to keep, what is the easiest way to do this ,i have heard that set up a partition called Home but i dont know 
 iam dual booting with windows 7 and ubuntu 14.04lts 
any help would be great

---

### Post by ian-weisser on 2014-10-30
You used a partitioner when you created your dual-boot setup.
Use a partitioner again to carve yet out another partition.
It doesn't need to be called "Home", you can call it anything you want. It needs to be mapped to /home in /etc/fstab just like all the other partition(s) you mount at startup.

---

### Post by Impavidus on 2014-10-30
Have a look here: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

There is one problem in keeping all config files when moving distro or release &#8211; even worse when sharing a home partition between two Linux installs. They may come with different versions of the same software, using incompatible config files. Moving from an old to a new release is rarely a problem.

---

### Post by Bucky Ball on 2014-10-30
I personally stick everything on the one partition when installing, / with /home as a directory inside (the default install). I then delete all empty folder in the directory /home like Documents, Videos, Music, etc. and replace them with symlinks to directories called Documents, Videos, Music, etc. on a different data partition. I do the same with any other OS I install so all OSs are using the same data partition as their /home with symlinks BUT all settings are in the /home directory on the / partition where the each OS is installed. Installing another OS doesn't change that.

Hope that makes sense. ;)

---

