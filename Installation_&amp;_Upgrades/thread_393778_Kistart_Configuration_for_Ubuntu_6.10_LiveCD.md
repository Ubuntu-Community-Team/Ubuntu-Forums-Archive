---
title: "Kistart Configuration for Ubuntu 6.10 LiveCD"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by zipho on 2007-03-26
Hi! Community
 
I am kinda new to  the Ubuntu family, and I have a couple of computers that I need to install Ubuntu 6.10 on, and all are supposed to have identical configuration (e.g hostname, etc..). 
Having searched on-line, I found that Kickstart is available for Redhat distros and I tried doing the same for ubuntu.

I remaster the Ubuntu Lice CD with ks.cfg on the cd root directory and includ the kernel parameters on  /isolinux/isolinux.cfg file.

[INDENT]LABEL kickstart
  menu label ^Install in text mode
  kernel /install/vmlinuz
  append  ks=cdrom:/ks.cfg initrd=/install/initrd.gz ramdisk_size=16384 root=/dev/ram rw quiet --
LABEL linux[/INDENT]

But the problems:(  comes when, I boot from the CD with intent to install my Ubuntu, :confused: when I do the install as normal, the kickstart doesn't seem to work at all. (My guess is that, its either not supported, or the ks.cfg file can't be found). I tried putting the ks.cfg file on a webserver, but that also didn't work. 

The idea is to have an Ubuntu CD with all standard install promptings automatically being filled-out when I install from the CD *(Hence I decided to include the ks.cfg on the CD, rather than other methods)*

I desparately need your assistance community, any help will be higly appreciated...

Thousand apologise for my English....

Thanks in advance;

Zipho

---

