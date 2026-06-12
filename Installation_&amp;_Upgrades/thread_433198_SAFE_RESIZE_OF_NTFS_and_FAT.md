---
title: "SAFE RESIZE OF NTFS and FAT"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by sirio81 on 2007-05-04
Hi all, I'm going to use Ubuntu 7.04 in an installation party.
Peaple are coming with their computer to install Ubuntu.

I want to know if it's safe to resize NTFS and FAT partition with the new ubuntu tool.

I would like to hear you direct experience.

Anather question (less important):
why ubuntu prefeare to use this tool instead of gparted?

Thankyou !

---

### Post by taurus on 2007-05-04
What tool are you talking about?  As far as I know, gparted is what Ubuntu uses to resize your partition.  And before you resize it, make sure you defrag your harddrive in Windows a couple of times first.

---

### Post by chocbar31 on 2007-05-04
> **taurus said:**
> What tool are you talking about?  As far as I know, gparted is what Ubuntu uses to resize your partition.  And before you resize it, make sure you defrag your harddrive in Windows a couple of times first.

I agree...get gparted! It's easy and powerful.

---

### Post by sirio81 on 2007-05-05
The latest ubuntu (7.04) doesn't use gparted during the installation process.
I don't know the name of this tool.
 
 
As I said, I will use ubuntu in an installation party so I will not say to boot before with a live cd that use gparted and then install ubuntu.
I will use only the live cd for install ubuntu 7.04 and I would like to know if the resize of NTFS partiotion is safe. We have to take space from windows installation and I would like it will still works.
 
Bye.

---

### Post by super.rad on 2007-05-05
Im pretty sure it does use gparted. Anyway i resized mine with it and windows still works fine, just make sure you defrag a few times first

---

### Post by sirio81 on 2007-05-05
I found the name: [B]Ubiquity.
[/B]****Ubiquity looks more like the suse partitioning tool,it's not in the partition magik / gparted stile.

---

### Post by sirio81 on 2007-05-07
Up :(

---

### Post by kuzmaionitch on 2008-05-23
Sirio81,

You prolly have already figured this out by now, but here is a heads up just in case:

Ubiquity is the name of the installer tool.
The installer tool runs an instance of gparted,
so the partitioning tool you were talking about was actually just gparted.

---

