---
title: "problems installing applications using apt-get install"
date: 2007-10-18
forum: Kenyan Team - Kenya
---

### Post by mwero001 on 2007-10-18
Hi guys. I upgraded my OS to feisty but i've been having problems whenever I try to get new applications using apt-get install. The same problem is exhibited when I use synaptic. This is the error message I get:
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing libdaemon0 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ke.archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Help!!

---

### Post by ajgreeny on 2007-10-18
>  E: Problem with MergeList /var/lib/apt/lists/ke.archive.ubuntu.com_ubuntu_di  sts_feisty_main_binary-i386_PackagesI see there is a space in this line which I wouldn't expect to be there.  I don't however, know what exactly you can do about it other than search your /etc/apt/ sources.list file and see if it is also there with a space.  If so get rid of the space,; you'll have to do this as root, so gksudo gedit /etc/apt/sources.list and edit it out.  Now try again.  If that works, great.  The question remains, however, as to how that space got there in the first place.

---

