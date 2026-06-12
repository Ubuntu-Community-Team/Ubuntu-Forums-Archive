---
title: "How to install Ubuntu on a PC with no cd rom?"
date: 2004-10-15
forum: Installation &amp; Upgrades
---

### Post by nico1278 on 2004-10-15
I'm a Linux newbie and have tried previously Mandrake,Knoppix and others but since i found Ubuntu i really felt in love with it . My 2 computer is an old note book with no cd rom but still 400mhz / 192 Mba / 12 GB.  How do I install Ubuntu by just using the floppy dics and my network connection?

---

### Post by bronson on 2004-10-15
It's not trivial, but maybe this page will help:

[http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://archive.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)

And, though it presumes you're coming from Knoppix, I've elaborated on some steps on:

[http://wiki.ubuntulinux.org/InstallFromKnoppixHowto](http://wiki.ubuntulinux.org/InstallFromKnoppixHowto)

---

### Post by nico1278 on 2004-10-16
Actually this is my 2 computer and for the moment there is no operating system on it... I'm looking for a way to boot from the floppy get the network working and install all the system fron the net. Is it possible to do that with ubuntu ?

---

### Post by Choi on 2004-10-22
[quote=nico1278] I'm looking for a way to boot from the floppy get the network working and install all the system fron the net. Is it possible to do that with ubuntu ?[/quote]

This is what I wanna do aswell...  Has anyone done this before on Ubuntu?  It works great on Fedora, but it so fukn big to download...

I want Ubuntu to be able to do a net install..    Plz..  someone...  can anyone help us with this?  

Cheers!

---

### Post by FLeiXiuS on 2004-10-22
This is a very good situation to explain.  

If you have an internet connection download the warty-4.10.iso then extract it to a folder of your choice using whichever method pleases you most.  

NOTE: copy the iso to a seperate partition

I haven't viewed the warty ISO and I can't right now because im at school, but if you can locate the vmlinuz and the kernel then you can procede!

Copy vmlinuz and the initrd.img to your /boot folder.

(RENAME THESE TO vmlinuz-ubuntu AND initrd-ubuntu)

Edit /boot/grub/menu.lst boot the vmlinuz-ubuntu and the kernel-ubuntu

```

title Ubuntu Install
	root &#40;your info&#41;
	kernel /vmlinuz-ubuntu
	initrd /initrd-ubuntu

```

This will allow you to boot the ubuntu install kernel.  Once doing so you may choose to install from your hard drive.  Select the path where the ubuntu.iso is.  (un extracted)

Then it should begin to install..

I will correctly edit this when I get home so I can try it my self and give a further defination of where the files are located and their names.  I'm just giving a breif definition of what to do!  Hope it helps!

---

### Post by carivera on 2006-11-03
I have an old ThikPad, It does have external Cdrom and external wireless, connected to the USB port. I want to install Ubuntu. Can anyone help me????

---

### Post by lazyart on 2006-11-03
Thinkpads should be able to boot from a USB device.  Hit F12 when the IBM logo appears and it will go to a boot menu.  Select the USB device and it should kick off the process.

---

### Post by tuxcantfly on 2007-09-04
Sorry for reviving the old thread, but if you want to install Ubuntu, Debian, or Fedora without a CD, from either Windows or an older Linux install, try using UNetbootin at [http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

