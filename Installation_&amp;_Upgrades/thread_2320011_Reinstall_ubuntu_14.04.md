---
title: "Reinstall ubuntu 14.04"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by doug36 on 2016-04-09
Hi 

I want to reinstall ubuntu 14.04 on first partition sda1.

It was corrupted by an upgrade to 15.10.

It boots to a shell login and asks for login details, but when put in says they are wrong.  Tried editing grub config on initial screen but doent work!!

Wont boot to recovery mode, straight to shell login.

When i tried to reinstall on same partition through the installer it asks for the root /  There is no way of changing this or putting this in on the installer.

So i cant reinstall.

So is there a solution to either dilemma.

---

### Post by grahammechanical on 2016-04-09
It would help if you gave us a full description of the partition layout. The simple solution to any re-install is to use the Erase disk & install Ubuntu option. That will work great if we do not care about any other OS on the drive or any data we may have collected. What is your situation?

> When i tried to reinstall on same partition through the installer it  asks for the root /  There is no way of changing this or putting this in  on the installer.

I do not accept that conclusion. I put in an install of 16.04 development version just 2 weeks ago and it went into the partition I wanted it to go. It was sdb1 if you are interested. There was already another install of 16.04 in that partition. I used the Something Else option. We have to select the partition and then click Change. We then get a dialog box where we set

1) the installation type from a drop down menu. The usual type is Ext4.
2) tick or not tick the box labelled format the partition
3) set the mount point from a drop down menu in a panel labelled mount point. To install Ubuntu the mount point should be /

We cannot install Ubuntu in a partition unless the partition has been given a mount point of /. We can set partitions to have other mount points but if we have not set a mount point we will be told about it when we click OK.

When we install Ubuntu to a partition if we have not set a mount point of / then, when we are back at the partition screen and we click Install Now we get told that we have not set a mount point of /. And we have to start again.

Regards

---

### Post by doug36 on 2016-04-09
Hi
 I have 4 instances of linux of a hard drive.  Sda1 has ubuntu, sda3 has mint sda4 arch linux and sda6 has mageai so reformatting is not an option!

Will try again your install method.  I saw the file types but never checked/ticked ext4 so I'll  try that (should have known that!!). 

Many thanks.

---

### Post by doug36 on 2016-04-10
Hi

All sorted thanks, back in without formatting.  Just trying now to see if I can recover files etc.

---

