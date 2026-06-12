---
title: "Dual Boot on Separate Drives"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by Petce on 2013-12-19
I am a novice when it comes to Ubuntu and Linux in general, but I am hoping to change that.


I have a strong gaming rig running 2x SSD's and a 2tb RAID 0 NTFS Partiton.


My goal is to Dual Boot Ubuntu along side Windows 7 however I want to install them onto the 2 seperate SSD's that I have. I will be formatting my SSD's to have a fresh install of both operating systems however I would like my RAID to remain unchanged as well as be accessible from both OS's.


Is there a good guide that will walk me through this? Any tips or things I need to be aware of?


Is it possible to make the OS's not have access to each others drives?

---

### Post by Mark Phelps on 2013-12-19
> **Petce said:**
> My goal is to Dual Boot Ubuntu along side Windows 7 however I want to install them onto the 2 seperate SSD's that I have. I will be formatting my SSD's to have a fresh install of both operating systems however I would like my RAID to remain unchanged as well as be accessible from both OS's.
To do this, you should remove ALL the drives except the SSD for which you want to install Ubuntu, boot from Ubuntu install media, and install to the SSD.  


> Is there a good guide that will walk me through this? It's a simple, menu-driven process -- but you need unallocated space on the SSD for the installer to format for Ubuntu.

> Any tips or things I need to be aware of? Yes -- have NO OTHER drives connected when you do the install.  That eliminates the problem of accidentally installing GRUB to a Windows drive and hosing up the Windows boot in the process.

> Is it possible to make the OS's not have access to each others drives?Windows won't see the Linux filesystem, so it will not be able to access anything there.  Linux, on the other hand, ordinarily sees Windows filesystems --  but the presence of RAID might prevent this.  Don't know, don't use any RAID systems.

---

### Post by oldfred on 2013-12-19
Ubuntu's desktop installer does not add the RAID drivers (yet). They did away with the alternative installer for desktops with LVM or RAID, but have not yet added RAID to desktop installer. It is in server and can easily be added to an install.

Usually the way to hide NTFS partitions is to actually mount them with fstab but specify noauto (not mounted) and set permissions so no one has access. Otherwise the file browser Nautilus will show the NTFS partitions and let you auto mount them.

---

