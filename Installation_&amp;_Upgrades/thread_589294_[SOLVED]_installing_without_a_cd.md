---
title: "[SOLVED] installing without a cd"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by tetrafuran on 2007-10-24
My laptop is unable to install xubuntu because it says certain files cannot be installed. Apparently it thinks the cd is corrupted. I've checked it on another computer and it says it isn't corrupted at all while checking it with the laptop says the md5's don't match. I even re burned the cd at 4x and I'm still getting the same stuff. Even an old mandrake cd is unable to fully install due to some critical kernel files being corrupted. Strange. It didn't complain at all when I installed mandrake years ago on another computer. In any case I'm beginning to think there's something wrong with my laptop's cd drive. Under windows it was able to read cd:s without any problems. Of course I didn't read every bit of the cd at that time. I just checked if I could retrieve data from a it. Being able to start the xubuntu installation pretty much proves the same point. If the cd drive was totally busted it wouldn't even reboot from a cd. Fortunately in my case it seems to suffer from a minor technical difficulty. No matter what's wrong with it, I cannot use a cd for installing xubuntu or mandrake.

How can I install xubuntu or some another light weight distro without useing a cd? I prefer the tools that come with ubuntu, the good support for hardware and so on. Therefore using the non-graphical part of ubuntu and combining it with fluxbox or icewm would be just the thinng for me. Ubuntu and kubuntu as such are out of the question. Xubuntu 7.10 alterantive might work, but installing it requires a cd. So can I just install the terminal interface of ubuntu using a pile of floppy disks and then use apt-get to get the rest from the net? What should I do?

The laptop is a fujutsu siemens s-4510 400MHz 64MB ram and has 6GB of space.

---

### Post by zvacet on 2007-10-24
I hope this will be helpfull to you

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by tetrafuran on 2007-10-24
Thanks. That's just what I need.

---

### Post by tetrafuran on 2007-10-24
ok. Now I finally had time to test the guide and here's what I've got so far:
The installation from floppies went well untill I was supposed to start doing something with bootstrap. The guide mentioned old links so I had to improvise just about all urls. I chose a location near me which is ```
ftp://ftp.funet.fi/pub/mirrors/archive.ubuntu.com/pool/main/d/debootstrap/debootstrap_1.0.6_all.deb
```
After that I was spposed to get
```
/usr/sbin/debootstrap --arch i386 hoary /target http://ftp.bit.nl/ubuntu/ 
```
It seems that it doesn't matter which ftp address I give, it always says: "no pkgdetails available; either install perl, or build pkgdetails.c from source" What am I supposed to do? apt-get install perl? Somwhow I should also update the ftp, since I'm not that interested in hoary.

---

### Post by tetrafuran on 2007-10-25
Now I've installed feather linux and also used it's script to install it on the HD. Unfortunately it will not boot at all since the computer still thinks there's no OS on the HD. I suppose the installation went as it should have and the lilo.conf files as it should be. I checked that it is telling the computer to boot from hda1 where all the stuff was installed. Apparently during reboot it isn't even starting lilo. What should I do? How can I tell my laptop that there *is* a functioning OS waiting to be started?

It might be worth mentioning that during the installation of feather linux I formated and partitioned my  HD. I labelled hda1 as bootable so that bios would be able to acces that partition during boot up. Unfortunately during the formating there came an error. IT says that boot tables could not be checked or something. What ever these boot tables are, they could cause this... or not. Don't know. I've never done anything like this before.

---

### Post by tetrafuran on 2007-10-27
Now I finally realized I had to use the latest version of debian floppies in order to succeed. Therefore i downloaded boot.img, root.img and networkdrivers-orsomething-1.img and made floppies of them. Installing debian with them took about 3-4 hours. I don't really know since I started it in the aftrenoon, went to bed and continued in the morning. The system runs well even under gnome. Nevertheless I still installed fluxbox.

---

### Post by nooby on 2007-10-27
You could try out UNetbootin that program has its own thread here:
[http://ubuntuforums.org/showthread.php?t=427540]("http://ubuntuforums.org/showthread.php?t=427540")
> Install Ubuntu without a CD using UNetbootin


You only have to use a fast line to the iso file.

---

### Post by tetrafuran on 2007-11-07
I used the guid at: [https://help.ubuntu.com/community/Installation/WithFloppies]("https://help.ubuntu.com/community/Installation/WithFloppies")
I noticed that getting bootstrap was a bit difficult since ```
/usr/sbin/debootstrap --arch i386 hoary /target http://ftp.bit.nl/ubuntu/
``` forgot to mention that the link in question has changed. I had to improvise and after several attempts I actually managed to get it right.

next```

chroot /target /bin/bash 
mount -t proc proc /proc
``` Ok. that went just fine.

and then
```
vim /etc/network/interfaces 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
Command not found. I have no vim, emacs, nano, cat, more or less. What can I do now?

---

### Post by tetrafuran on 2007-12-27
I ended up using dsl. It had a similar hd install scipt. I just followed the instructions at dsl linux website and got it running with a usb stick. Ofcourse and old laptop didn't recognize the stick at first so I had to use dsl's own boot floppy.

---

