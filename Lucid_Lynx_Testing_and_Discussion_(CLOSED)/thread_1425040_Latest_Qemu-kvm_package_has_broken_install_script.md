---
title: "Latest Qemu-kvm package has broken install script"
date: 2010-03-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Ibidem on 2010-03-08
Well, I tried installing qemu-kvm (to try out a Suse Studio cd I made). Aptitude gave an error, complaining about the *install* script trying to *delete* /etc/kvm.  (This is on an Atom without virtualization.)  Of course, /etc/kvm does not exist, so it fails.  
Now, the way apt+dpkg works, every time I try installing any software dpkg attempts to run the script, and (consistently) fails.  It gets annoying after 3-4 packages.

Launchpad: [https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/533090](https://bugs.launchpad.net/ubuntu/+source/qemu-kvm/+bug/533090)
Ibidem

---

### Post by cyberkilla on 2010-03-09
I can't even upgrade because I have kvm and qemu-kvm dependency issues - they are held back...

It's been like that for about a week.

---

