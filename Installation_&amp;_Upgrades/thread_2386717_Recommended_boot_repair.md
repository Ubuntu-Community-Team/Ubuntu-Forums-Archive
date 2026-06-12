---
title: "Recommended boot repair"
date: 2018-03-09
forum: Installation &amp; Upgrades
---

### Post by upshift on 2018-03-09
Hello,
Trying to do a boot-repair.  The report is attached and is at: [http://paste.ubuntu.com/p/Hg9tmYgF44/](http://paste.ubuntu.com/p/Hg9tmYgF44/)
This was a pretty much standard ubuntu 16.04 installation before a rogue script caused this problem.  Luckily I was able to recover my home directory.  Now trying to see if I can repair the boot up before reinstalling.

Thanks,
John D.

---

### Post by oldfred on 2018-03-09
I do not know LVM.
But believe you have to make sure you have mounted the LVM & unencrypted your / (root) partition before running Boot-Repair.
Or manually chroot into system to fix it.

But related to this?
 LVM with encryption Issues with newer kernels 4.13.0-32-generic xenial
[https://ubuntuforums.org/showthread.php?t=2385932](https://ubuntuforums.org/showthread.php?t=2385932) 

      
 [SOLVED]Secure boot issue - fix with Boot-Repair LVM with encryption
[https://ubuntuforums.org/showthread.php?t=2350963](https://ubuntuforums.org/showthread.php?t=2350963)

It looks like you have a newer UEFI system but installed in the older BIOS/MBR configuration.
Which is ok, just not taking advantage of some of the features of gpt and UEFI. (Some just do not like UEFI).

---

### Post by upshift on 2018-03-09
Thanks very much for the pointers.  I figured it had something to do with the encryption

---

