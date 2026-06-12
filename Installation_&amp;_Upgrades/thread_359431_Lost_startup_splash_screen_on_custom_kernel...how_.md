---
title: "Lost startup splash screen on custom kernel...how do I recover it?"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by mr.v. on 2007-02-12
Hi all--

I've been using a kernel from kernel.org (2.6.20) on dapper and when I compiled it, I lost the ubuntu splashscreen with the progress bar. It seems to be something akin to fbsplash. I was wondering where or if there's an ubuntu kernel patch to re-enable the splash screen for the 2.6.20 kernel?

Thanks!

---

### Post by GoingDown on 2007-02-12
I think it doesn't need any specific kernel patch, but only kernel frame buffer support must be compiled in (or as an modules of course) and enabled for it to work.

---

### Post by mr.v. on 2007-02-12
Thanks for the reply!

I've got kernel framebuffer support in there. In fact, I can even get the penguin logo to show up when I selected bootup logo and run with a 1024x768 8-bit framebuffer (though with/or without it I still don't see the Ubuntu splash) 

I've tried all sorts of combinations with framebuffers. Will it not work with the VESA framebuffer? I haven't specifically tried the nvidia framebuffer driver however. Is the Ubuntu splashscreen incompatible with the VESA framebuffer driver?

I've also tried including/excluding the VGA-16 color console to no avail as well as I've tried both with and without tile blitting since I've read that conflicts with **fbsplash** so I thought it may be the same with Ubuntu. Where did you read where the splash screen is not implemented in the kernel source itself? I'm curious because I can't find any documentation about it at all despite searching. The best I've found is something in the gentoo wiki about gensplash (previously named fbsplash). What does Ubuntu use to achieve this?

---

### Post by GoingDown on 2007-02-13
OK, you got me interested, so I tested it myself with my 2.6.20 kernel...

It requires you have frame buffer support AND that you use initrd, but no any custom kernel patches. (without initial ramdisk, splash screen doesn't show up even if you have fb support)...

So, here is what I did:

* check that you have quiet and splash options on your #defoptions= line on /boot/grub/menu.list (to make sure that the update-grub does right things). If you prefer to modify your menu.lst file manually, just add "quiet splash" to the end of your kernel .... line, see example of mine:

```

title           Ubuntu, kernel 2.6.20
root            (hd0,1)
kernel          /vmlinuz-2.6.20 root=/dev/hda8 ro reboot=b vga=791 quiet splash
initrd          /initrd.img-2.6.20
quiet
savedefault
boot

```

Then I installed usplash (I had removed it...), made an initrd and then updated grub automatically (only if you want to use auto method)

```

apt-get install usplash usplash-theme-ubuntu
mkinitramfs -o /boot/initrd-2.6.20
update-grub

```

That did it!

EDIT: And yes, I am using vesafb, which is compiled-in to the kernel, not a module. If you use module, make sure that it gets to the initrd as well.

EDIT2: Some time ago (quite long time...) somebody somewhere said that ubuntu splash goal was that it must work without any modifications to kernel. fbsplash and gensplash work different way. 
Easy way to find things about usplash is to go to [http://ubuntuforums.org/tags/index.php/usplash/](http://ubuntuforums.org/tags/index.php/usplash/)

---

### Post by mr.v. on 2007-03-02
Sorry for the late reply! I got so busy and I forgot to subscribe to the thread it left my brain...

So you're absolutely right! That worked like a charm. You definitely get a gold :KS

The only thing is that I noticed some "FATAL" modprobe lines flash for a second before the ubuntu usplash.

That may be because I compiled most things I wanted statically into the kernel and it's still trying to modprobe them in the init scripts. But going through all those commenting out modules sounds painful.

That was one nice thing about slackware. It assumed that you loaded agpgart and alsa and that's it so it was fairly easy to get rid of modprobe fatalities if you statically compiled 'em in.

Anyway, again thanks a lot. Here are some more
:KS :KS :KS :KS :KS :KS :KS

---

