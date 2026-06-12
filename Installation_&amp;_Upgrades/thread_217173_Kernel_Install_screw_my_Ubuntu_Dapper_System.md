---
title: "Kernel Install screw my Ubuntu Dapper System"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by guru369 on 2006-07-16
Hi All.

I had a perfect new install of Ubuntu Dapper.
I wanted to install linux-686-smp and in the same install process I selected to remove the 386 kernel version I had.
I got a warning on removing a running kernel but selected to remove it anyway.
(I know I did a mistake so dont flame me....)

Now when I reboot grub is showing me an error about problems extracting the kernel image (Maybe corrupted?).
I lost my ubuntu system!!!!

I want to recover without the need to reinstall.. Is there a way.

I am currently on my Gentoo partition and able to mount the Ubuntu partition.


Please help!
Thanks in advance to all the community.

---

### Post by Choad on 2006-07-16
could try booting gentoo then chrooting in to ubuntu and running the grub configuration tool.... can't remember what its called tho...


or actually... could you not simply configure grub from in gentoo...

unless of course your processor is not a 686...

what proc u got?

---

### Post by guru369 on 2006-07-16
Hi,

I have a P4 Prescott 3.0
I can run Grub install from gentoo on Ubuntu Boot partition. The problem is that the kernel image seems to be corrupted.
Grub loads perfectly, I was woundering is there a way to get the kernel image from another source and copy it to my /boot partition?

Dekel

---

### Post by matthew on 2006-07-16
Hmm. I haven't done anything like this. I would say the first step would be to get a working kernel. Try here:
[http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-23-686](http://packages.ubuntu.com/dapper/base/linux-image-2.6.15-23-686)

or choose one from here
[http://packages.ubuntu.com/dapper/base/](http://packages.ubuntu.com/dapper/base/)

They are packaged, so you will still need to figure out how to decompress them and get them installed, but if you've installed Gentoo, you ought to be able to figure it out. :)

---

