---
title: "Upgrading from Alternate from boot..?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by faceless-21 on 2010-10-12
Hey all I recently took apart my laptop(Dell Inspiron 9300) and cleaned it and put it back together.  Afterward it seemed to work fine but the next day it gave me the "gave up waiting for root device" error and I have been trying to get around that.  I tried this fix [http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/](http://zeeis.me/ubuntu-error-gave-up-waiting-for-root-device/) because I saw a lot of people do it that way but when I got to the "apt-get update, etc)part it wouldnt let me cause I couldnt connect to internet even though I was connected to wireless internet, so I tried the fix that the page gave for if the internet didnt work in chroot and that told me that I am unable to resolve host ubuntu.  and "cannot create regular file /media/fix/etc/resolv.conf" or something along those lines.  oh and I tried to plug into my modem via cable but the live CD wont connect to the ethernet port connection, which worked within the last few months but could be out of commission...

  So I am wondering if there is a way to upgrade Ubuntu from the Alternate CD without booting into the OS itself?  Or perhaps I could install Ubuntu on a USB drive and when I boot into the LIVE CD and do all that the above fix says, could I update from the ISO instead of the internet?

  Thanks in advance :)

---

### Post by faceless-21 on 2010-10-13
Bump...  Anyone?

---

### Post by faceless-21 on 2010-10-14
Bump?  Wow this is the first time I have not had a reply to a question within a day!  Must be a tough answer :(

---

### Post by dino99 on 2010-10-14
what do you expect ? chroot cant help if you have not a net connection anyway :confused:

[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

---

### Post by faceless-21 on 2010-10-14
Is there anyway I can upgrade from a CD iso in chroot?  like an ISO that is on an external HDD or flash drive?

---

### Post by TNT1 on 2010-10-14
> **faceless-21 said:**
> Is there anyway I can upgrade from a CD iso in chroot?  like an ISO that is on an external HDD or flash drive?

Create a usb live "cd" with unetbootin on another pc, should be good to go. I'm not sure I understand your first question, but yes, if your laptop can boot from cdrom, then an alternate cd will also do fine...

---

### Post by faceless-21 on 2010-10-14
> **TNT1 said:**
> Create a usb live "cd" with unetbootin on another pc, should be good to go. I'm not sure I understand your first question, but yes, if your laptop can boot from cdrom, then an alternate cd will also do fine...

  Hey TNT I am booting from a live CD trying to access a corrupt linux partition to fix and am going into chroot to try to upgrade the partition's OS but it wont let em cause I cant access the internet and so I want to try to upgrade it through chroot with the alternate ISO but I dont know the commands to do so... or if its possible.

---

### Post by TNT1 on 2010-10-14
Right. What version is corrupt, and what alternate upgared cd version do you have? Also, just out of interest, what other than cleaning the machine could have corrupted it? Cause if it's a hardware failure, then the hd is probably toast and this is all moot...

---

### Post by faceless-21 on 2010-10-14
> **TNT1 said:**
> Right. What version is corrupt, and what alternate upgared cd version do you have? Also, just out of interest, what other than cleaning the machine could have corrupted it? Cause if it's a hardware failure, then the hd is probably toast and this is all moot...

I think its 9.04 but it could be 8.04.  And I dont know what else could have corrupted it, its not the HD cause I am booting onto my windows partition from it so if the HD was toast nothing on it would work.  Oh I have the 10.04 alternate CD iso.

---

### Post by TNT1 on 2010-10-14
Is there data you need off the borked partition that you can't get? If you can, back it up from a live cd, and than run the alternate upgrade from boot and you should be good. I upgraded a 9.04 system to 10.04 booting from alternate upgrade cd, and didn't lose a drop of data, so it does work... (yikes! no guarantees, huh...)

---

### Post by faceless-21 on 2010-10-14
Yes I have some data that for some reason says that it is locked and I need rights to open the folders or copy the files, I also have a virtual box that I didnt backup and would REALLY like to get into it cause it has some photos and settings that I dont have backed up very recently :(  How can I run the alternate upgrade from boot?  It says I can install but it doesnt say that it has the option to upgrade...

---

### Post by faceless-21 on 2010-10-14
Before I head to bed Bump...

---

### Post by faceless-21 on 2010-10-15
Wake up Bump.

---

### Post by TNT1 on 2010-10-15
Try chown from live cd to access the data you want to back up?

---

### Post by faceless-21 on 2010-10-15
> **TNT1 said:**
> Try chown from live cd to access the data you want to back up?

chown...  never used that command, how would I open up my drive with that command?

---

### Post by TNT1 on 2010-10-15
You can see the drive, right? But you can't access it due to permissions? chown will let you change ownership of the files/folders to the liveuser.

[http://www.cyberciti.biz/faq/how-to-use-chmod-and-chown-command/](http://www.cyberciti.biz/faq/how-to-use-chmod-and-chown-command/)
[http://www.computing.net/answers/linux/what-and-how-to-chown/29529.html](http://www.computing.net/answers/linux/what-and-how-to-chown/29529.html)
[http://www.tuxfiles.org/linuxhelp/fileowner.html](http://www.tuxfiles.org/linuxhelp/fileowner.html)

---

### Post by faceless-21 on 2010-10-15
Ok so from the LIVE CD terminal what would the command be to access my drive(lets call it SDA1)?

---

### Post by faceless-21 on 2010-10-16
Morning bump

---

### Post by faceless-21 on 2010-10-17
another morning bump

---

### Post by faceless-21 on 2010-10-18
bump

---

### Post by TNT1 on 2010-10-18
> **faceless-21 said:**
> Ok so from the LIVE CD terminal what would the command be to access my drive(lets call it SDA1)?

No, follow the links I posted earlier, and use chown to change the ownership of the drive before you access it.

---

