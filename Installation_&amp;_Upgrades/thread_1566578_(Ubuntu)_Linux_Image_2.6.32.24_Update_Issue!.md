---
title: "(Ubuntu) Linux Image 2.6.32.24 Update Issue!"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by Jeffey on 2010-09-02
Ladies and Gents,

I seem to be having issues with updating my version of Ubuntu as of late, I've enclosed my terminal reading...please excuse my 'tardedness as I'm just now starting to get into the Linux World.

Setting up linux-image-2.6.32-24-generic (2.6.32-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Could not find postinst hook script [update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.32-24-generic


Can anyone please shed some light on my issue or help me alleviate this problem?  I'm trying to install Conky and just update my Ubuntu...thanks in advance!

Jeffey

---

### Post by davidmohammed on 2010-09-02
does any of the suggestions [here]("http://ubuntuforums.org/showthread.php?t=975190") help you?

---

### Post by Jeffey on 2010-09-02
Well, that information was back from 2008...but I pulled up the kernel-img.conf anyways:

do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = update-grub
postrm_hook   = update-grub

There isn't a "\" before the update-gub command and there is no path either.  I ran this through the root in the terminal and it still opens up as a "read-only" anyways so I can't seem to edit it. =/

---

### Post by davidmohammed on 2010-09-02
the link said to reinstall grub

sudo apt-get install grub-pc

if it says its installed, try a reinstall

sudo apt-get install --reinstall grub-pc

---

