---
title: "Kubuntu needs password to mount ntfs partitions"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-06-03
Greetings!

I have already made one thread ([http://ubuntuforums.org/showthread.php?t=1496349](http://ubuntuforums.org/showthread.php?t=1496349)) about the matter, but as i supposed the matter was solved, and i marked it as "solved", now even if i unmark it it becomes a no-perfix topic. Also the thread looks confusing as the actual question is asked in the last post, not in the first, and so i decided to make new one.

In this topic i want to ask the following questions that i hope can clarify something for me (and probably for somebody else who'd stumble upon it)

_Out of the box, Kubuntu needs password each time you mount a disk with ntfs file system. _

This behavior is said to be overridabe with changing files like /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla or /usr/share/polkit-1/actions/org.freedesktop.udisks.policy

When one asks "how to make it stop prompting me for password" a response is usually "change one of the said files".

But, it DOES NOT WORK. 
I studied the matter and it seems that the problem lies in ntfs-3g which is needing root privilleges, because its either outdated or uses external FUSE which makes it unsecure to let it be ran with root privilleges.

Question 1. What do theese files actually control. Which program/application/daemon/service uses them and how? 

Question 2. Why do people advise making changes in those files if the problem lies in a driver and cannot be externally changed? And why do others actually respond with "it worked" if it can never work from changing theese files because ediding those files for sure will not recompile the ntfs-3g drivers by itself...

Question 3. From reading the ntfs-3g output:
```
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged
```
I can conclude that:
Either outdated ntfs-3g is used in kubuntu 10.04 (sine 1.2506 it already includes Built-in FUSE support and it has went stable January 29, 2008)
OR
ntfs-3g used in kubuntu 10.04 is compiled with use external FUSE option

Why is it made so, for what reasons is this a default for Kubuntu (why not install latest or allow unprivilleged mounts?)
OR
Am i wrong and there is something else causing this?

Question 4. Am i right that to correct this behavior (to allow unprivilleged mounts of ntfs partitions) i have to install the lastest ntfs-3g on my system with compile options to use built-in FUSE and then set the correct bits (setuid/setgid) and that will do?

---

### Post by Istrebitel on 2010-06-03
And the fight goes on...

I have compiled ntfs-3g from source with the options needed to make it. I gave all the required permissions (binary setuid bit, permission to use volume, mount point) (even added my user to disk group, otherwise he couldnt have rights to the volume as required in ntfs-3g questionary). 

Now i can do:

istrebitel@dom-tux:~$ mount /dev/sda1

and it will mount the ntfs disk without sudo

BUT! FFS I AM FRUSTRATED! Because the damn dolphin STILL asks me for password! i tried. 

if i open the disk via dolphin while its unmounted, it asks for password
if i then open terminal and do  mound /dev/sda1 it mounts without password!

What the damn .... is happening? Why for god's sake is it asking for password it does not need?

PS: and for god's sake why dont i have 
/usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy 

everybody else seems to have

---

### Post by Istrebitel on 2010-06-04
I read alot around the webs about what Polkit is or how cool it is but... damn it, nothing about how to set it up. The only mention is here:

[http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/907-ubuntu804policykit](http://beginlinux.com/desktop_training/ubuntuhardyheron_cat/907-ubuntu804policykit)

But it tells me nothing? because in KDE on Kubuntu 10.04 there is nothing close in the menus (i've searched em all, no such option exists to manage policies)

Or am i supposed to edit the files myself instead of having some sort of gui or comandline editor? but then, why do they change the damn files with every version to make it harder to edit them?

---

### Post by Istrebitel on 2010-06-04
And what i dont quite understand is... am i the only one who has kdesudo popping up for password for ntfs partition? Am i the only one who it bothers? because searching the forums or the net gives nothing on people from kubuntu 10.04 having such problems... except some loose comments like "i have it and fix worked"... where the fix is not working on kubuntu 10.04 actually

---

### Post by Istrebitel on 2010-06-07
bump i still would like to solve this out please...

---

### Post by rykel on 2010-07-03
I am using Ubuntu 10.04 and facing exactly this same hair-tearing crazy problem!!


UPDATE

I solved my own problem!

Simply purge 3rd party drive managers (eg. Storage Device Manager), comment out all the NTFS lines in /etc/fstab, do a "sudo blkid", reboot, plug in the devices and let Ubuntu auto-detect/auto-setup the UUID of the devices. I hope this solves your problems too!

The problem seems to be due to the fact that Lucid does NOT use /dev to identify devices anymore, and uses UUID instead.

---

### Post by ElijahLynn on 2010-09-11
> **Istrebitel said:**
> bump i still would like to solve this out please...


I am having this issue and it is driving me crazy too!

I have two NTFS partiions and I get two password prompts everytime, I have tried adding the UUIDs to fstab but that does not solve and even throws errors sometimes. I also was hopeful that ticking them off in system settings> removable devices would work but it didn't.

From a user experience perspective this is poor and should be enabled by default. I don't know how to enable these drives but when I do I will try hard to file an official bug report and recommend a good way to solve it.

P.S. I am new to Kubuntu but have been dabbling with Ubuntu for about 2 years, finally made the big switch and am on Kubuntu full time now since last week.

---

### Post by ElijahLynn on 2010-09-11
In other news this guy is having the "opposite" problem with his Dolphin in Fedora!!!

He wants the NTFS to have a password!

[http://fedoraforum.org/forum/showthread.php?t=239320](http://fedoraforum.org/forum/showthread.php?t=239320)

---

### Post by ElijahLynn on 2010-09-11
Another similar issue talking about why is this so complicated.

[http://forum.sabayon.org/viewtopic.php?f=53&t=16118&p=91994](http://forum.sabayon.org/viewtopic.php?f=53&t=16118&p=91994)

---

### Post by ElijahLynn on 2010-09-11
Ok, this works. 

1. KPackageKit via Krunner (alt + f2) then type "package" and select it.
2. Search for ntfs-config - install it and reboot
3. Go to The KMenu (start menu for windows converts) > Applications > System > NTFS Configuration Tool
4. Tick off the read and write checkboxes and save (I am not sure if this is necessary but I did it)

---

