---
title: "Distro Hopping and Grub"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by Dasani on 2010-03-05
I've started distro hopping as of recent between a couple of linux-es, but one issue remains for me in doing so.
Grub reinstalls over and over on the newer partition. This isn't much of a problem because, well, grub is grub in any colours, but for the safety of my original installation and peace of mind, I would always like to retain my original grub and then just manually add the new partitions to its menu.

Is there a standardized way in which I can do this during most Linux installs or some basic education I can get on the installation of grub with which I could avoid such problems?

thanks

---

### Post by Herman on 2010-03-05
I don't think there are any universal conventions on installation procedures across Linux distros. Each one has its own installation procedures, however there are similarities in the installers used by distros which are closely related to each other.
As far as I know, most Linux distros today prefer GRUB, a few might still use LiLo. 
There might be a lot of distros that still use GRUB Legacy.
All or if not almost all prefer if you install their boot loader to MBR, especially if you're using GRUB, because GRUB is an excellent boot manager.

Ubuntu does allow you to chose what hard disk of partition you would like to install GRUB to, but you need to read an installation how-to to see how to do that. It isn't obvious to the uninformed.

---

### Post by Herman on 2010-03-05
A couple of ideas you could try would be to use a 'dedicated GRUB partition', or use GAG Boot Manager.
Either of those makes the boot manager 'operating system independant', which is probably what you want if you're distro hopping. :D

---

### Post by Herman on 2010-03-05
GRUB isn't dangerous to an existing installed operating system, as in it won't delete any of your files or anything like that. If something goes wrong and your old os doesn't boot it might inconvenience you a little until you fix the booting issue.
A good idea would be to have a Super Grub Disk or a GAG or PLoP Boot Manager Disk around and make sure you install your original operating system's GRUB to the partition boot sector so you can still boot it easily from your boot CD no matter what goes wrong.

---

### Post by ttoilleb on 2010-03-05
While not exactly what you are asking, the following post shows how to set up a system with a main grub partition and then add as many other opsys as you may want

[http://ubuntuforums.org/showthread.php?p=8551352#post8551352](http://ubuntuforums.org/showthread.php?p=8551352#post8551352)

---

### Post by Dasani on 2010-03-07
cool stuff guys, thanks.

A dedicated boot partition would be the best for me I think and I'll look up how I can do that.
The GAG Boot Manager looks very interesting as well, I'm going to check it out...
thanks

---

