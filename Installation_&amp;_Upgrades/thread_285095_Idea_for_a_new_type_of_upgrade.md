---
title: "Idea for a new type of upgrade"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by willis on 2006-10-26
I've never bothered to create a separate partition for my home directory (I know I should but I'm never sure of the amount).  Suffice to say I always have this problem when a new version of ubuntu is out.  How do I upgrade and keep my /home usually I just back things up and reinstall off a cd, but I often lose things in the process.

What if....

The live-cd mounted your hard-drive and wiped all the directories except /home, then instead of formatting just switched to a chroot on the mounted hard-drive and installed it's packages.  Nothing would overwrite /home as no software is installed there.  In the end you'd have all the software from the new distro with the same /home...  Obviously any changes you did to /etc or custom software you installed would be gone, but not your personal data in /home.  And you couldn't change the filesystem as you're not reformatting.

The only two problems I can see would be 
--the user file in /etc but that could either be kept, or providing the user is going to use the same name the installer would just write a new one and it would still refer to the same username in /home

--the system would be very broken while the directories were being wiped... but that's the same as a normal install.

Would this work?  Why hasn't this been done before?

---

### Post by raqball on 2006-10-26
You can already do that with the custom partitioning option during install. Choose to NOT format the /home

Simple :)

---

### Post by willis on 2006-10-26
Right but /home is on the same partition... I.e. my hard-disk is one partition.

---

### Post by raqball on 2006-10-26
Ahhh, I guess I did not read the 1st post as well as I should have :)

In that case i like your idea, but I wonder how difficult that would be to achieve?

Future request maybe? :)

---

### Post by willis on 2006-10-26
No worries...

Well that's my question... Just musing about it I didn't see any big problems... I mean the installer just wipes the hard-drive and then installs the packages... this would just be wiping all directories except /home and then installing the packages.

But maybe I'm over simplifying it.

---

