---
title: "trouble upgrading from unsupported version"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by elindauer on 2012-10-06
Hi!

I'm trying to get into Ubuntu and have just installed it from a disk I had lying around.  The version is 7.04, and I would like to upgrade to a more recent version.

I've tried using update manager, but I get an error message that it "Could not download all repository indexes" with a list of maybe 20+ websites.  Most of these start with security.ubuntu.com or us.archive.ubuntu.com.

Can anyone help me?

---

### Post by jerrrys on 2012-10-06
7o4 is long dead, EOL in 2008.  You need to burn a new copy of ubuntu.  Whats your computer specs?

And welcome to the forum  :)

---

### Post by elindauer on 2012-10-06
I was afraid you might say that.  I have tried burning an iso to a disk, but I'm struggling to actually boot from it.  I also have the iso on my hard drive, but haven't found a way to upgrade from inside Ubuntu.  I guess I just need to figure out why the iso won't run from disk.

I'm running a Pentium dual core 3.2Ghz processor with a 1 Tb hard drive.

---

### Post by jerrrys on 2012-10-06
Your specs are good, running full blown Ubuntu should not be a problem.  You may or may not have to install video drivers.  This link may help with the install.  Any other questions you may have, just post them :)

[http://www.ubuntu.com/download/help/install-ubuntu-desktop](http://www.ubuntu.com/download/help/install-ubuntu-desktop)

---

### Post by elindauer on 2012-10-06
I have burned a CD containing "ubuntu-12.04.1-desktop-i386.iso" as a single file.  Every help page seems to think I can just drop this in my CD-ROM and install now, but this doesn't seem to work.  My computer just goes straight to Ubuntu.

The CD seems good, I can see it on my Ubuntu desktop and browse the iso contents.  The motherboard recognizes the CD-ROM... after all, I installed this old version of Ubuntu this way!

I'm at a loss.  Any ideas?

---

### Post by elindauer on 2012-10-06
ok, I think I understand... it seems that you don't burn iso files to a CD the same way you burn, say, a text file to a CD.  It's not drag and drop, you need to "burn the image" onto the CD.

I am trying this now, and I suspect this is going to solve my problems.  Thanks for the help!

---

### Post by kurt18947 on 2012-10-06
> **elindauer said:**
> I have burned a CD containing "ubuntu-12.04.1-desktop-i386.iso" as a single file.  Every help page seems to think I can just drop this in my CD-ROM and install now, but this doesn't seem to work.  My computer just goes straight to Ubuntu.

The CD seems good, I can see it on my Ubuntu desktop and browse the iso contents.  The motherboard recognizes the CD-ROM... after all, I installed this old version of Ubuntu this way!

I'm at a loss.  Any ideas?

The .iso file is what you downloaded. You have to create either a bootable  CD/DVD or a live USB.  What functional computer do you have access to?  Quite a few people prefer a live USB to a CD though I've never had a CD fail to boot.  Many CD burning programs will create a bootable CD from an .iso file.  To create a live USB, I've had good luck with Unetbootin,  google will find it.  If you choose the live USB option, you may have to change the boot order in your BIOS.

---

