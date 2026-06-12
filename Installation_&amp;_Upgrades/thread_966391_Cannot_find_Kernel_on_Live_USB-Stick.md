---
title: "Cannot find Kernel on Live USB-Stick"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by adieb on 2008-11-01
Hello,

I am running Intrepid 32Bit and i wanted to try the 64Bit Version. So I downloaded the CD-Image.

With usb-creator I created the Image on my Kingston 4GB Usb Stick. Fine. Reboot.

It finds the "USB-Disk" and there is something like "syslinux, version...." and some other stuff (but no menu)

and then there is a line just with
```
boot:
```

If i hit enter it tells me
```
could not find kernel image linux
```

If i write anything, like vmlinuz or whatever, it just tells the same, but instead of linux the word i wrote.


What can I do? I already tried the option with the persistent Dataspace and without. I downloaded the .iso image again. No success.


---------
Core 2 Duo E6750
4 GB Ram
Kingston Datatraveller 4GB

---

### Post by Emill on 2008-11-01
I have the same problem.
I am using Kingston 4GB DataTraveler.

---

### Post by adieb on 2008-11-01
Do you think it is because of the Stick?

I took a look at the things that are copied on the stick. It seems to be alright though.
Or is it a file-system-problem?

I hope somebody knows something about it...

Shall we file a bugreport at launchpad?

---

### Post by C.S.Cameron on 2008-11-01
Kingston 4G do not seem to be working with usb-creator.
The only way I have been able to do to get mine to work is to install to a 2G Kingston and then clone that to the 4G using dd.
I then create two ext3 partitions in the free space.
I label the first casper-rw and the second home-rw, then delete the casper-rw file from the U-C install.
This is a bit of a hassle but persistence works.
This bug has been reported, but a few more confirmations might help.

---

### Post by Jcord on 2008-11-01
I have the same problem however my flash drive is a Transcend jetflash V30 / 4 GB 
and I am using a iso of the 32 bit version

I have no other drives to try. But I have tried from multiple computers using 8.10 live cd and 8.04 freshly upgraded to 8.10.

---

### Post by adieb on 2008-11-02
Which Bug is it?
Can you post a link here?

---

### Post by C.S.Cameron on 2008-11-05
Sorry for the delay, missed your post:
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/276822](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/276822)

---

### Post by ktraglin on 2008-11-06
I've been doing some testing with a couple of different machines.  The first has a Biostar TA770-A2+  motherboard, while the second has a Gigabyte GA-M61SME-S2.  I'm using a 2GB Feiya Technology Corp Memory Bar.  Instructions from Pen Drive Linux ([http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd)) creates a device that boots just fine on either machine, but when using Ubuntu's new "Create a USB Startup Disk" (usb-creator), the same flash device only boots on the first machine.  The second machine ends up at a terminal session boot prompt.  Pressing [enter] yields the message, "Could not find kernel image: linux".  I've also tried entering "vmlinuz", as well as "/casper/vmlinuz", with the similar results.  I wan't to help Ubuntu continue to succeed as the best Desktop Linux available, but I'm not sure how else I can help.

---

### Post by Horny on 2008-11-22
Well... Im with this problem too but I notice USB Live boots based in the session where it was created.
 
Examples: 
Using "Create USB startup disk" from my machine's Ubuntu creates a stick who boots the machine's Ubuntu kernel.

Using "Create USB startup disk" from a running Live CD session creates a stick who boots a Ubuntu's Live CD session. It returns a error if no Live CD is present.

Anybody else notice this?

---

### Post by sai.m on 2008-11-27
I tried to create a USB start up disk from an ibex64 iso on my patriot xporter (16 GB) with my laptop using the tools ibex 64 came with. I also ran into the "could not find kernel image: linux" error when I tried to boot it on my desktop, even though my .cfg files and the iso's md5 were correct.

I decided to format the drive into FAT32 with gparted and added the boot and lba flags manually, instead of letting the live usb creator do it. Then, I used the live usb creator to add in the files. At first, I thought this made it worse because my desktop would not even boot from USB to get to that error sceen. It turns out that it made the drive recognize as a normal hard disk, and I just had to give it a higher priority than my main drive.

It runs much faster than a live CD, so its useful. I can finally get rid of optical media.

---

