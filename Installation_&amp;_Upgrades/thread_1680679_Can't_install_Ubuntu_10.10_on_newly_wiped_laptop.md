---
title: "Can't install Ubuntu 10.10 on newly wiped laptop"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by lukegvoigt on 2011-02-02
Hi everyone! Great forum, and I love it. 
I recently decided to wipe my laptop using Dariks Boot and Nuke. This, of course irreversibly wipes out a hard drive. I downloaded 10.10 and burned to a CD and booted from cd, then this error comes up.

"Busy Box v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

I have installed Ubuntu 10.10 on my laptop before. Then I had wiped it and put Windows 7 and now I wiped and want to install Ubuntu again. 
Anyone ever seen this?

Thanks!):P

---

### Post by stkrzysiak on 2011-02-02
I'd check your install media.  Did the iso md5 check out?  Does the install media boot into a live environment on another box?

---

### Post by sikander3786 on 2011-02-02
> **stkrzysiak said:**
> I'd check your install media.  Did the iso md5 check out?  Does the install media boot into a live environment on another box?
@ **lukegvoigt**:

Welcome to the forums :-)

In order to add to the above quoted post, first of all check the MD5SUM of your downloaded image.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that is ok, check your burnt disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

If the image is corrupt, download a new one. If the disc is corrupt, burn a new one and remember, burn at the lowest possible speeds.

And also let us know your laptop specs please.

---

