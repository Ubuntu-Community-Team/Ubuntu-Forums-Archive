---
title: "Ubuntu, Dual-Boot and a Newbie."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by FaresH on 2007-04-26
Hi,

I am totaly new to linux. At my college they asked us to download ubuntu and install it. I downloaded it, burned it and I am able to boot from cd. I get to the installation, the cd is fine (no errors), I choose the language, the location, the keyboard layout but then I get to the partition part. 

I have one 40 gb hard drive, 20 for c: and 20 for d: . I cleared all the data on d . I want to install the ubuntu on the d. What do I do now ?

---

### Post by eapache on 2007-04-26
Click custom, then the partition manager should open. You should have two partitions of 20GB each visible. One will have 0 used space (assuming you cleared it properly). Right click on it, and say 'delete'. Then right-click on the new 20GB of free space, and create a partition of the format linux-swap. It should be however big you want your swap to be. Now click on the remaining 19 or gigs and create a new partition using all of the remaining space. It should be of format ext3, and the mount-point should just be a /

Your disk used to look like:
hda1 20GB NTFS
hda2 20GB NTFS

Now your disk should look something like:
hda1 20GB NTFS
hda2 1GB linux-swap
hda3 19GB ext3 (mount point /)

That should work, but you should still back up any important files from Windows before installing.

---

### Post by wetland on 2007-04-26
There are many ways to set up your partitions.
This is a [link]("http://www.psychocats.net/ubuntu/partitioning") to a good site for an explanation on Partitioning. Check out FS-Drive from the other side.

---

### Post by FaresH on 2007-04-27
Hi, 

Thank you a lot. I did as you told me and the ubuntu is now on my pc.

---

