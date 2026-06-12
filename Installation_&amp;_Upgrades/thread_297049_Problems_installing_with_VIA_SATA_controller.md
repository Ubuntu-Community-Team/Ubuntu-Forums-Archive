---
title: "Problems installing with VIA SATA controller"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by Languid on 2006-11-10
Hello, I'm trying to install Edgy onto my desktop which uses a VIA VT8237 SATA controller for a RAID 0 setup with two 160GB HD's setup up to be one large 300GB drive.  However, after booting into the Edgy LiveCD and starting up the install process, the gparted only sees my two separate drives!  

Now, currently I have XP installed on the drive in a 20GB NTFS partition, with the rest of the 300GB unallocated (the XP installer, after inserting a driver disk, properly recognizes the controller and sees the one large 300GB partition).  I was hoping to install Ubuntu into the rest of the drive, and dual boot the two operating systems.

However, after doing some searches on Google, I attempted to use a Gentoo 2005.1 LiveCD to see if I had better luck, and, by passing the 'dodmraid' option to the Gentoo kernel on boot, my SATA controller is properly recognizes, and when I open fdisk it sees the drive properly as a 300GB drive.  As far as kernel modules go, I also noted that two important modules were loaded: 'libata' and 'sata_via'.  In the Ubuntu LiveCD, these modules are loaded as well.

So after more searches, I found this guide on the Ubuntu India Wiki: [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto]("http://www.ubuntu-in.org/wiki/SATA_RAID_Howto").  I followed this guide, modified my sources.list in the LiveCD to include the universe repositories, reloaded the packages list, and installed the 'dmraid' package.  However, when the install attempts to start up dmraid by running the init script at /etc/init.d/dmraid, the script immediately fails with a segmentation fault.   So dmraid doesn't start up at all, and so my drives are still seen as two 160GB drives.  I also attempted to do this after having passed the 'dodmraid' option to the kernel, as I did in the Gentoo LiveCD, by pressing F6 and adding it to the kernel parameters, but this didn't change anything.  So, no luck there.

So my question is, has anyone else had success getting the Edgy LiveCD to properly recognize and use a VIA SATA controller, or could anyone suggest other possible solutions?  I believe my SATA controller uses what is known as fakeRAID, if that is any help.  Currently, my only option is to install Gentoo instead of Ubuntu, but I'd really rather not.  So, anyone out there who can help me?  Thanks. :)

---

### Post by Languid on 2006-11-10
*bump* Anyone have any ideas?

---

### Post by Languid on 2006-11-11
*bump again* Does anyone have any ideas?  Am I asking in the wrong forum or have I not given enough information?  Any help at all would be appreciated.

---

### Post by agent007 on 2006-12-14
I have the same problem.
So, nobody can help us?

(Why in Windows all things are more simple?)

](*,)

---

