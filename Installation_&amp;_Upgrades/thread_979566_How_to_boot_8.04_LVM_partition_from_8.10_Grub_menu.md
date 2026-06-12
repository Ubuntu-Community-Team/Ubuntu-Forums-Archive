---
title: "How to boot 8.04 LVM partition from 8.10 Grub menu?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by ruudschellekens on 2008-11-12
Dear all,

I have upgraded my Hardy release to Intrepid last Sunday but got lots of annoyances like window decorations that looked awkward. Since I have 2 hard disks I decided to do a clean install on the second hard drive using the installation cd of Intrepid. Installation was succesful, yet after a reboot I got Grub error 21.

So I installed again using the second drive fully (guided partition use full disk) and disconnected the first drive containing my upgraded Hardy system. This worked. Now I want to setup grub so that it will boot my upgraded Hardy release again. The problem is that I set up my Hardy release with LVM and I do not know how to add the lvm partition to the grub boot loader so I can boot the old installation again.

Can anyone help me here? I can mount the lvm with lvm 2 commands found here:
[http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html](http://linuxwave.blogspot.com/2007/11/mounting-lvm-disk-using-ubuntu-livecd.html)

Kind regards,

Ruud

---

### Post by littlebat on 2008-11-12
Mount your Hardy partition, copy items(vmlinuz and initrd.img ) in its "/boot" into your Intrepid's "/boot" directory.
Edit your menu.lst in "/boot/grub/" in Intrepid, add the boot items of hardy.

Here is a boot item of Hardy "/" on lvm over raid0 for refering:
> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel          /vmlinuz-2.6.24-19-generic root=/dev/mapper/ubuntuvg-ubunturoot ro quiet splash 
initrd		/initrd.img-2.6.24-19-generic
quiet


It's isn't clear of your question. Need detail. Where did you get stuck?

---

