---
title: "error 19 wont let me install"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by leetmode on 2007-01-18
Hi, im trying to do a fresh install, and it seems when ubuntu tries to load i get an error 19 that says something about not being able to map a certain drive... Any help please ?!
](*,)

---

### Post by john_spiral on 2007-01-18
Hi leetmode,

what is the exact error message you are getting?

---

### Post by kebes on 2007-01-18
I'm guessing you're running into "Grub error 19" which, if you look here:
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Is supposed to mean:
> 19 : "Loading below 1MB is not supported"
This error is returned if the lowest address in a kernel is below the 1MB boundary. The Linux zImage format is a special case and can be handled since it has a fixed loading address and maximum size.

However it's not always easy to figure out why grub is reporting an error. You mentioned something about not being able to map a drive? The exact error message would certainly help.


If you're looking for things to try, you can try reinstalling grub from a LiveCD session (using "grub" and/or "grub-install")... If you're using an older motherboard and you have the linux partition far in the hard drive (not first partition), there may be a problems with grub being able to see the "/boot/" directory. You can then either move the partition somehow, or use LILO as the bootloader instead. For instructions on installing LILO from a LiveCD environment, see this thread:
[http://ubuntuforums.org/showthread.php?t=230384](http://ubuntuforums.org/showthread.php?t=230384)

---

