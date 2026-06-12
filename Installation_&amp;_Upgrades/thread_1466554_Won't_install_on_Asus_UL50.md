---
title: "Won't install on Asus UL50"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by weaver4 on 2010-04-30
Can't get 10.04 to work on Asus UL50 (CULV) laptop.

First thing that happens is that it takes 30 minutes for the Welcome screen to come up from the install CD.  It will run the Live CD.

Takes over 2 hours for the system to install (30 min each on step 2 and 3).

Once installed I boot and I get this error:

"Gave up waiting for root device."

It also give the error "Missing modules (cat /proc/modules; ls /dev"

And Finally it says:
ALERT: /dev/disk/by-uuid/90eoad56....11d9 does not exist.  Dropping to shell!"

Ran a test and hard drive appears to be OK.

---

### Post by weaver4 on 2010-04-30
I checked and the path:
/dev/disk/by-uuid/90eoad56....11d9

does not exist.  I have a directory called /dev/disk/by-path but not a directory called /dev/disk/by-uuid

It appears that the "last second" changes to GRUB that Ubuntu did yesterday may have caused this problem.

---

### Post by weaver4 on 2010-04-30
Very confused.

How can Ubuntu be pointing to the kernel by UUID in the grub menu and not set up the directory that it points to?  Seems very basic.

---

### Post by ibm450 on 2010-06-28
all working sweet on ul50Vt, only gripe the brightness adjusting applet and FN+F5 not working? any1 have a patch or work around to adjust screen brightness on ul50vt as it chews up the battery

running 10.4 (linuxmint9)

cheers

---

