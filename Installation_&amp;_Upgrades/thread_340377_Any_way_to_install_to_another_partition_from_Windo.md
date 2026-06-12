---
title: "Any way to install to another partition from Windows?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by PaterLucis on 2007-01-17
Let's say I'm in Windows, and I have a 10gb partition on the same drive.

Any way to install Ubuntu to it without rebooting? From Windows. I guess i'd need to mount that partition or something.

---

### Post by pebo on 2007-01-17
[This]("http://ubuntuforums.org/showthread.php?t=338279") may be what you are looking for - but it's still under development.
Apparently you will be able to install directly into windows without  having to create a new partition for ubuntu.
> The installer works by creating a disk image of a pre-installed ubuntu system on the hard disk (downloaded with a bittorrent downloader integrated into the installer, or a standard http download when we find mirrors), and then installing GRUB for windows, which can be chain loaded by the existing boot loader, and which then loads the linux kerner and initrd from the ntfs partition. The initrd is modified to support mounting the image file mentioned above as a root file system, and then continuing the boot process like a normal installation.


---

### Post by PaterLucis on 2007-01-17
No, it is not. I actually just wanted to install an ISO to another partition. 

Nothin' special.

---

### Post by allwin on 2007-01-17
The regular LIVE CD should be able to install UBUNTU to the "extra" partition there.  You may have to do a manual partitioning in the install procedure.  If it was me, I would just delete that last partition and let UBUNTU install itself and the swap to the free space there.  This is assuming you don't want that 10 G partition or its contents.  You might be able to shrink it to like 1G (if there's nothing in it), and use the remaining 9 for UBUNTU.  I'm not good enough at this yet to walk you through the process step by step, but I know you can do it if you slip into the manual partition option during the install.

---

### Post by PaterLucis on 2007-01-17
What I'm asking is if there's any way to do that FROM WINDOWS.

---

### Post by dcstar on 2007-01-17
> **PaterLucis said:**
> What I'm asking is if there's any way to do that FROM WINDOWS.

No, Windows is Windows, the Ubuntu install CD works from its own environment, it is not a Windows application.

---

### Post by PaterLucis on 2007-01-18
*sigh*

Are you listening to me?

I know very well what Ubuntu is. I am asking if there is any way to install Ubuntu to another, unused partition, FROM WINDOWS. Like, you know, mounting the unused partition, etc.

---

### Post by Aurdal on 2007-01-18
And the answer is toyour question is no. You can't install Ubuntu from Windows.

Windows is an operating system, Ubuntu is another operating system.

Is there any particular reason for you not wanting to reboot?

---

### Post by FXWGBill on 2007-01-19
Just to be sure the last 3 answers weren't clear....

NO

You could you use a partitioning program within windoze and set it up for it, but after that...

NO

Why would you NEED to install it from within Windoze?

There is a distro that you can run WITHIN windoze...  It's called Damn Small Linux or DSL for short; you can find it in a search.

But that's about it....

---

