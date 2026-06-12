---
title: "HELP! Install Ubuntu without CD-ROM drive?"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by ale1981 on 2007-06-12
Hi,

The CD-ROM drive on our server fails the integrity CD test and will not install from the CD.
I have the ISO on a second hard drive on that machine.

Is there any way i can install using the ISO?

Any help appreciated, i have searched but could not find how to do this.


Thanks.

---

### Post by neorou on 2007-06-12
Maybe you can re-partition one of your drives and image the ISO to that? Then you can boot from that image/partition?

What hardware are you using?

---

### Post by ale1981 on 2007-06-12
I can still boot into windows.

If i extracted the ISO to the D: and told it to boot up off that, would it work?

---

### Post by pxwpxw on 2007-06-12
You can install from the iso, with the hd-media installer images from here 

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/)

---

### Post by ale1981 on 2007-06-12
Thanks for the replies. Which ISO do I use and how do I go about pointing the install at that image?

Sorry but never installed without the CD before!

---

### Post by pxwpxw on 2007-06-12
Well, you need to download the hd-media vmlinux and initrd from the hd-media set, this is for i386, and the manual attempts to explain, but I have only used the applemac ppc set, so cant help much with i386 booting procedur. But  you put the downloaded  alternat cd.iso file on a partition, you boot from the hd-media kernel, and that brings up the alternate install menu, which takes you to load from the iso, very easy once you get booted. Sorry cant advise on the i386 grub/lilo booting, maybe you can find a howto for booting from iso, or someone else can advise. If you are using applemac I can help more. Check the install manual section 4.

[https://help.ubuntu.com/7.04/installation-guide/i386/downloading-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/downloading-files.html)

This howto might help you:for i386

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by ale1981 on 2007-06-13
Is the alternative CD ok to install the server edition?

---

### Post by pxwpxw on 2007-06-13
There should be a downloadble iso version of this.

Server install CD

[http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)

---

