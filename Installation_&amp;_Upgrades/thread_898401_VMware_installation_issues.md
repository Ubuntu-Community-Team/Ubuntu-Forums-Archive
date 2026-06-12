---
title: "VMware installation issues"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Kolfinna on 2008-08-23
Hey, all.

I set up a new virtual machine within VMware server edition and designated it as a linux box. I downloaded both the server edition and the desktop edition of Ubuntu and I haven't had any luck with server... I'm installing the desktop edition now.

Basically, I can start the server installation but it says it can't install the base operating system because the kernel is missing. Is this expected...? Do I need to compile my own kernel? If so, how?

Thanks,

~K

---

### Post by Partyboi2 on 2008-08-23
Did you check the[[COLOR=Blue] md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") after you downloaded?

---

### Post by Kolfinna on 2008-08-23
Actually, no... I'm creating a new virtual machine and will let you know the results in a few minutes...

Machine details, btw:
Single processor (should it be dual?)
1024 MB RAM
20 GB hard drive
has access to internet
set up for generic Ubuntu

Thanks!

~K

---

### Post by Kolfinna on 2008-08-23
The md5sum was fine...

Also checked the integrity of the CD, it was okay.

...Hmm. Seems to have managed to fix itself, because this time it actually loaded and installed. o.O

Thanks anyway!

~K

---

