---
title: "Installation seems impossible on my acer"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by ellipsic on 2010-06-05
I have tried to install Ubuntu i386 on an Acer Aspire 5810TZ, but have been unsuccessful... I have tried

 - installation by CD and DVD of all releases from 8.04 up to 10.04
 - installation via bootable USB
 - installation via bootable USB onto another USB stick acting as the hard drive

all of these fail.  Basically, the install goes well until copying files, then fails with an "input/output error" message, and a suggestion that the CD reader is dirty or the hard drive is broken -- getting the same message when installing onto a USB stick makes me think that that none of these options is possible... so I'm really at a loss.  Just for fun, I tried installing SUSE linux and THAT also failed.  I don't have any idea what's going on, this has never happened to me before... Any ideas?  Thanks !

I have checked the md5sums, tried burning again, tried USB, etc.  I don't think the hard drive is actually damaged, given that install also failed when i tried to install onto a USB.

---

### Post by c9-3Rr0r on 2010-06-05
try to check your hard drive for errors

```

sudo fsck /dev/your disk

```

---

### Post by davidmohammed on 2010-06-05
are you sure you have downloaded the 32bit intel desktop edition and not a 32bit AMD or 64bit edition of lucid?  Using the wrong ISO could explain your issues.

---

### Post by ellipsic on 2010-06-06
Yes, all isos I use are i386

---

### Post by davidmohammed on 2010-06-06
longshot - [these guys]("https://bugs.launchpad.net/ubuntu/+bug/245794") have reported this issue.  One ran a memtest (from the live CD i guess) which showed a RAM issue.  Is this your problem?

---

### Post by ellipsic on 2010-06-18
This seems very possible, given that the install failed independent of whether i was installing onto the hard disk or onto a USB, whether using CD or USB.  I will look into it.

---

