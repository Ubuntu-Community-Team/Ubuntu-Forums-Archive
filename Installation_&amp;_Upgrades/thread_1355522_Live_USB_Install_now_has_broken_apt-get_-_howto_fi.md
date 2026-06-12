---
title: "Live USB Install now has broken apt-get - howto fix?"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by macintard on 2009-12-15
I get this error on my liveusb system:

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': Input/output error
ubuntu@ubuntu:~$ sudo apt-get upgrade –fix-broken
Reading package lists... Error!
E: Could not open file /var/cache/apt/pkgcache.bin - open (5: Input/output error)
E: Failed to truncate file - ftruncate (9: Bad file descriptor)
E: The package lists or status file could not be parsed or opened.
ubuntu@ubuntu:~$ 


It's been working but during the install of openoffice it froze completely and so I hit reset. Now it is doing that. How can I repair the filesystem other than a resinstall when it comes to live usb? Perhaps I could edit the boot up options to enable recovery mode so I'll google that next but had to throw this out there. It's Xubuntu from pendrivelinux.com and it has persistence. Thanks!

---

### Post by unxzst on 2010-04-29
i'm having the same problem with ubuntu. anyone find a solution yet?

---

### Post by kalmdave on 2012-02-29
> **unxzst said:**
> i'm having the same problem with ubuntu. anyone find a solution yet?

Am on HP 165w 8Gb pen drive with Lucid Lynx 10.04.3. I get this error:

*E:Could not open file /var/cache/apt/pkgcache.bin - open (5: Input/output error), E:Failed to truncate file - ftruncate (9: Bad file descriptor), E:The package lists or status file could not be parsed or opened.*

Any guidelines. Should I reformat and reinstall in the drive?

---

