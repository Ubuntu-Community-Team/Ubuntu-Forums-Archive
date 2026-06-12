---
title: "Live CD boot fails on AMD phenom II X6"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by iloveubun on 2011-09-12
I was trying to boot from the Live CD which I created using the 10.04.3 desktop i386 image file and the system does not boot properly. It gives the error message:
 
(initramfs): mounting /dev/loop0 on //filesystem.squashfs failed. Input/output error
cannot mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs 
 
and it drops to busybox shell (with the prompt initramfs). From here nothing can be done excepting executing a bunch of shell commands. If I exit from the shell, the kernel panics, requiring a hard reset.
 
Has anyone experienced this kind of issue ? My hardware is Gateway DX 4350 PC with AMD Phenom II X6 1055 T processor with 6 GB RAM. 
 
Thanks in advance

---

### Post by mörgæs on 2011-09-12
Hi, welcome to the fora.

This error is mostly connected to booting from CD. Have you tried from USB?

---

### Post by Karlchen on 2011-09-12
Hello, iloveubun.

Hm, more a question than a piece of advice, because none of my machines have got 6 GB of RAM, so I cannot test myself, but:
Could the source of the problem not be that you are trying to boot a 32-bit Ubuntu live system which can definitely not address more than 4 GB of RAM on a machine having 6 GB?

Karl

---

### Post by mörgæs on 2011-09-12
I doubt that is the problem. You are right (and thanks for pointing it out, since I missed that part) that a 32 bit system can not see 6 GB memory without modifications, but it can run nevertheless. 

Best is to try the 64 bit version from USB.

---

### Post by iloveubun on 2011-09-13
Hello Morgaes and Karlchen,
Thank you for your replies. I had to use USB stick, 64-bit version and 11.04 (instead of 10.04.03) to solve this problem.

While the 64-bit (amd64 iso) got me beyond the point of mount error at squash file system, it failed when installing the software on my hard disk due to I/O errors, caused due to bad writing on the live CD. So, I had to use USB stick as a media to install the software and from  then onwards it worked without a problem !

Thanks !

---

### Post by mörgæs on 2011-09-13
You are welcome. Please mark the thread 'solved' using 'thread tools'.

---

