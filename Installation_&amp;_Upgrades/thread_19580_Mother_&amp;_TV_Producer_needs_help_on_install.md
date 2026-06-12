---
title: "Mother &amp; TV Producer needs help on install"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by bk452 on 2005-03-12
I've intalled Ubuntu on the kids pc (Dell GX110).  I love it.  I've tried other distros. but I want my tv team to use Ubuntu.

I need to boot to windows to use Adobe Audition.  Here is where I got confused:
I have 2 partitions: C for windows and D which has nothing on it.
----------------
This is an overview of your currently configured partitions & mount points...

IDE master (hda) - 40.0 GB Toshiba  MK 4019 GAX

#1 primary     20.9 GB   ntfs
#5 logical       19.0 GB
      pri/log        8.2  MB  FREE SPACE

----------------------

When I clicked on the 19.0 GB, I got a message about not having set a root.  What do I do?

---

### Post by az on 2005-03-12
You have to give it a label.  The default should already be /

That's what it mean about root (/)

It will not intall unless you define a /.

Delete the existing partition if it is not already free space.  Then, go with guided partitioning.  It will ask you before it does anything.

---

### Post by bk452 on 2005-03-12
Thanks for the info.  I've got Ubuntu installed but now I can't boot to windows. Now what do I do?

---

### Post by Gary Powers on 2005-03-13
Seems one of the most common problems with this is the setting on the hard drive.  Reboot, dump into SETUP (typically the delete key) and make sure the drive is set on LBA rather than AUTO.  I have experienced this on two of my machines.

Gary

---

### Post by bk452 on 2005-03-13
Thank you so much for your time.  I can dual-boot fine now.  This is one thing that has sold me on Ubuntu.  It's a great OS but when you run into trouble, people take the time to help out.

SuSE only speaks geek and Fedora Core doesn't have the time to respond.

So thanks a million and take pride in the fact that you got a tv crew going!

---

### Post by az on 2005-03-13
[QUOTE=bk452]people take the time to help out.

SuSE only speaks geek and Fedora Core doesn't have the time to respond.
[/QUOTE]


Now, lets get Adobe Audition working under wine.  (or cedega)

BTW: Suse is german, actually.

---

### Post by bk452 on 2005-03-14
I just looked up cedega.  I'm going to be following it closely.  Not just because I think Adobe Audition would fit better in it, but my kids want video games.  Thanks.

---

### Post by gungaden on 2005-03-14
Your kids are blessed.... Go, Mom.

---

