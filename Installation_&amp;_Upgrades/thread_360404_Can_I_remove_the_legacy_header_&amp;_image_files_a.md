---
title: "Can I remove the legacy header &amp; image files after new kernel installed ?"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by xport on 2007-02-13
Hi...Buddies...

I had updated kernel from "2.6.17-10-generic" to "2.6.17-11-generic", but I found that some legacy files still leave in my disk.

Can I remove the old version files & images ?

here is some informations about them:
```

[xport@ubuntu /usr/src] $ ll
drwxr-xr-x 19 root root 4.0K 2007-01-18 09:58 linux-headers-2.6.17-10
drwxr-xr-x  4 root root 4.0K 2007-01-18 09:58 linux-headers-2.6.17-10-generic
drwxr-xr-x 19 root root 4.0K 2007-02-10 08:24 linux-headers-2.6.17-11
drwxr-xr-x  4 root root 4.0K 2007-02-10 08:25 linux-headers-2.6.17-11-generic

```

```

[xport@ubuntu /lib/modules] $ ll
drwxr-xr-x 2 root root 4.0K 2007-02-11 11:07 2.6.17-10-generic
drwxr-xr-x 6 root root 4.0K 2007-02-10 08:25 2.6.17-11-generic

```

```

[xport@ubuntu /] $ ls -l | grep "^l"
lrwxrwxrwx   1 root root    11 2007-01-17 01:59 cdrom -> media/cdrom
lrwxrwxrwx   1 root root    33 2007-02-10 08:25 initrd.img -> boot/initrd.img-2.6.17-11-generic
lrwxrwxrwx   1 root root    30 2007-02-10 08:25 vmlinuz -> boot/vmlinuz-2.6.17-11-generic

```

---

### Post by Jussi Kukkonen on 2007-02-13
Sure you can. Don't just delete them though, uninstall using aptitude (or whatever you use to install/uninstall stuff).

Of course, you should never uninstall a boot image before you are sure that the new one really works... I usually keep one previous version just to be sure.

---

### Post by whein on 2007-04-19
I have a problem.  I have a box with 2.6.17-11 upgraded from 2.6.17-10 (Edgy install CD) which in turn was upgraded from 2.6.15-something (Dapper install CD).  I went through Synaptic last night and removed all the images and header files and related stuff for 2.6.17-10 and 2.6.15.  Uninstall seemed to work fine, no errors in the terminal window from Synaptic.  But when I went to reboot the computer got as far as the gray splash screen with the Ubuntu logo and the little progress bar across the bottom, and then froze.  No boot, no visible errors, no nothing.  Help!!!  Is this in any way recoverable or do I need to backup all the data files and reinstall?
:(
-Will

---

### Post by whein on 2007-04-21
/bump

Any suggestions?  Using a Dapper LiveCD I was able to backup the hard drive (don't know why but the Edgy Live CD has never worked right on this computer) to a spare drive.  The machine boots fine into GRUB, shows me the 2.6.17-11 kernel option and the 2.6.17-11 recovery option as well as some options that are from a failed install on a different hard drive (haven't got around to cleaning that part up yet, was next on the list).  Both the 2.6.17-11 options will boot to a certain point and then just hang.  The normal option gets to the gray Ubuntu logo with a progress bar below it and the recovery mode gets a black screen just after mounting all the hard drives and readying the kernel for boot.  It almost seems like it's failing to start the X server.  Is there some log file I could look at or some trick someone has used in the past.  My only other plan at this point is a full reinstall :(
-Will

---

