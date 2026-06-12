---
title: "Installing Ubuntu and detecting NVRaid Mirror (RAID1)"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by yekim on 2007-08-19
Hi all, I've looked around at all the NVRaid stuff, but none of the posts seem to address my issue in particular.

I have 3 disks in my system.  The first one is an 80GB that I have partitioned as such:

60GB NTFS with WinXP already installed
18GB Linux Ext3 targeted for Ubuntu 7.04 Install, (in progress with your help!)
2GB Swap

My second two disks are NVRaid-ed (Software RAID?) in a mirror configuration (all my photos, etc. are on there, imperative I don't kill it!).  

***All I want to accomplish is the ability to access the RAID'ed drives from Ubuntu***

I don't want to install Ubuntu on these drives.  All the topics I've found are typically related to installation on the RAID drive, and so also include "format" instuctions (god-forbid on this drive!).  e.g.[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

So my question is, can someone please point me to an installation procedure that will just add this drive so Ubuntu can see it as a single mirrored drive?  Or do you recommend that I ignore it during installation, and try to get Ubuntu to recognize it after installation?

Thanks in advance,
Yek

---

### Post by yekim on 2007-08-20
Bump

I tried the install after running dmraid, and noticed there was another disk there I believe was created by using "sudo dmraid -ay"

I just let it mount as default, then chose "unused" for the two individual RAID drives.  I setup my partitions and isntalled.

I installed GRUB to HD2, my 80GB non raided drive.  Now when it boots, GRUB loads, but every option I click on says something like "Error 21: disk cannot be located" (or something like that.  Sorry my system is at home now).  Any ideas what may be happening?

Thanks!

---

### Post by icco on 2007-08-23
Bump, I want to do the same thing with Raid 0, any ideas anyone?

---

### Post by yekim on 2007-08-23
Bump.  I'm now in Ubuntu, and fixed my GRUB problems.

However, my RAID'ed disks are still appearing as "Disk 1" and "Disk 2."

Can anyone help me unmount these two disks and re-mound just the mirrored "FakeRaid" drive?

> root@YekBu:/# sudo dmraid -r
/dev/sda: nvidia, "nvidia_bgeihaed", mirror, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_bgeihaed", mirror, ok, 312581806 sectors, data@ 0
root@YekBu:/# 


Thanks!

---

### Post by chainsawbike on 2007-10-18
this isn't hard i done it a while ago but i can remember how
pm me if this still isnt solved and ill figure it out again

---

### Post by mk4umha on 2008-06-16
did anyone figure this out?

---

