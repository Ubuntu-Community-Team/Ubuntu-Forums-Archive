---
title: "Cant install from HD, following advice in the online guide"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by DavidTangye on 2007-07-24
Hi all,

This laptop needs Feisty, but its CD seems flakey. So I want to install with no CD. Its running Puppy linux, and boots via grub.

I read on [https://help.ubuntu.com/7.04/installation-guide/i386/boot-drive-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-drive-files.html) under - 
**> Hard disk installer booting using [B]LILO** or   **GRUB**
[/B]>  Copy the following files from the Ubuntu archives to a convenient location on your hard drive, for instance to /boot/newinstall/.[LIST]
[*]                 vmlinuz (kernel binary)
[*]                 initrd.gz (ramdisk image)[/LIST]That's all it says (plus 'configure the bootloader' to boot into it, which I have done).

I got the above files plus all the installation out of the iso. That seems to be my problem. When  I boot, it starts fine. The problem is that the installer is bent on installing from CD. How do I tell it to just install from the files found where it resides on the HD? Or do I need a different kernel or initrd or both? And whatever of those I use, surely I need to have the install files locally on the hard disk? 

None of this is explained in the online help.

---

### Post by DavidTangye on 2007-07-24
Bump. No replies. Maybe I have not asked a clear question...

Does anyone know how to install using just the hard drive?

---

### Post by pxwpxw on 2007-07-24
Section 4 of the guide, images link has hd-media, net install, and cdrom, kernel and initrd sets, hd-media uses an install iso on your hard drive.

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/")

---

### Post by DavidTangye on 2007-07-26
Thanks for the reply.

Its a bit hard to understand what you are saying, but I followed the link to what must be the kernel and initrd to use, and shall check out Section 4 of the guide shortly.

---

### Post by DavidTangye on 2007-07-26
> **pxwpxw said:**
> Section 4 of the guide, images link has hd-media, net install, and cdrom, kernel and initrd sets, hd-media uses an install iso on your hard drive.

[http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/](http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/)
Thanks for the reply.
Its a bit hard to understand what you are saying, and section 4 does not explain hard disk booting much at all. However I shall resort to the usual method, download the files you gave me the link to, boot them and see what happens.

I can boot [vmlinuz]("http://archive.ubuntu.com/ubuntu/dists/feisty/main/installer-i386/current//images/hd-media/vmlinuz")   , and use the initrd.gz. What is the boot.img.gz for? And where is the installation stuff? .. not in initrd.gz, as it is too small.

 I just wish people in ubuntu and open source would explain things better. Its like I am out on the last great frontier all the time :-(.

---

