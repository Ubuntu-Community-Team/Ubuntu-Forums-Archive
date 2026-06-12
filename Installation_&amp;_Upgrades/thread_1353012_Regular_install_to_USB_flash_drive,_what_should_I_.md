---
title: "Regular install to USB flash drive, what should I watch out for?"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Cadmus on 2009-12-12
I'm wanting to do have a USB stick I can use over the Christmas period at my folks. Last year I used the USB creator to make a live-USB on my 4GB stick, but I found the space got rapidly eaten up when I cusomised things, and it was a little slow with some odd issues having multiple users.

So this year I want to go for a plain old regular install, I know 4GB is a little tight but it is enough space for a basic xubuntu install right?

I know about making triply sure that grub gets put on the stick, not on the system hard disk of the machine I use for the installatio. But what else can catch you out when you use a 'mobile' install of ubuntu on multiple computer?

---

### Post by aysiu on 2009-12-13
As long as Grub installs to the stick and not the MBR, you're cool. You can get even more minimal than Xubuntu, though:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Mighty_Joe on 2009-12-14
I posted a link [over here]("http://ubuntuforums.org/showthread.php?t=1193680") to some things you can do to optimize your install and minimize unnecessary writes to the drive

---

### Post by C.S.Cameron on 2009-12-16
A regular install to USB stick uses a lot more space than a persistent disk image install, and does not have that many advantages over the short term, (Christmas holidays).
4GB should work ok if you don't load it up with too much stuff.
You can save downloaded item, photos, MP3s to a second flash drive or you can even place your home directory on a second flash drive.
If you disable your HDD when creating the bootable flash you should not run into any other problems.
It is not that easy to modify the host machines hard drive while booted from the USB stick. You need to enter your password to even see the contents of the HDD.

---

