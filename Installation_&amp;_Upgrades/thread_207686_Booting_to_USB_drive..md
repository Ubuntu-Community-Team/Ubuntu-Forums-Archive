---
title: "Booting to USB drive."
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by ebeyer on 2006-07-02
I have what I hope will be a really simple problem to solve.

I have a Windoze laptop I use extensively in my day job.  I don't dare mess with the hard drive (I also can't find my OEM recovery disk).  So I went so far as to buy a USB 100 Gb external HD (Maxtor) and installed Ubuntu on it.

Come to find out that the BIOS on my laptop (Sony VAIO VGN-T140P) won't look at USB drives for booting up.  Since I can't (okay, since I *won't*) touch the main HD (dha), I was thinking I could create a boot CD for the laptop that would point to the USB drive and let me boot up in ubuntu when I wanted to.

How do I do that?  Could I also just use the live ubuntu CD and just give it a command to look at the USB drive - something like 'boot: root = /dev/sda1/boot'' or somesuch?

Your thoughts and help are much appreciated.

EB

---

### Post by yager on 2006-07-15
Check out this HOWTO put together by Zerlinna.  It should meet your every need.

[http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)

---

### Post by ebeyer on 2006-07-15
Thank you for the link.

This gets me closer, but defeats the purpose of having a 100 Gb USB hard drive.   

Ideally, I'd boot to a CD that would "point" to the USB drive, where 99% of the system (programs, personal data, etc) would be.  This would also give me a real performance boost over a CD-based OS.

EB

---

### Post by ebeyer on 2006-07-15
Oh yeah - I also would need to load some commercial drivers and set a custom display resolution for my laptop.

---

### Post by yager on 2006-07-15
> **ebeyer said:**
> I'd boot to a CD that would "point" to the USB drive, where 99% of the system (programs, personal data, etc) would be.

The directions on that link appear to do that by pointing root to the device /dev/sda1.

> Here too, replace the number with your kernel and make sure that the copied file is renamed to initrd.img.
V. Then you'll create the isolinux.cfg file. Open kwrite and paste the following line:

    DEFAULT linux initrd=initrd.img ro root=(your-root-dev)

[B]
(your-root-dev) is the partition where you installed your new system, in our example the line would look like this:

    DEFAULT linux initrd=initrd.img ro root=/dev/sda1[/B]


Save the file in the bootcd folder.

If you have some time, you could review this very long thread on booting external drives.  It has over 442 messages in it, many of which are about the booting from CD due to BIOS issues.

[http://www.ubuntuforums.org/showthread.php?t=80811&page=34&highlight=Zerlinna](http://www.ubuntuforums.org/showthread.php?t=80811&page=34&highlight=Zerlinna)

I have you linked in on page 34.  If you want to start at the top, you will find the specifics for booting to an external drive assuming your BIOS allows you.  Page 34 appears to be the first reference to booting from a CD to get to your external drive.

---

### Post by ebeyer on 2006-07-15
I need to read that.

I also just found this link: [https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Thanks!

EB

---

