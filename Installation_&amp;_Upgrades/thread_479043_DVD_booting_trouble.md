---
title: "DVD booting trouble"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Andrew07 on 2007-06-19
I do some audio reproduction.. so I decided to try out Ubuntu Studio. Burned the .iso onto a DVD without any trouble and reset my boot order to boot from USB-CDROM first (it's a external USB DVD drive and there was no "USB-DVDROM" option). However, it doesn't seem to want to boot the DVD. It comes up with the normal "Boot from CD:" prompt... then a second later starts booting from the hard drive (which is the second option.)

The DVD drive light flash's some whenever it tries to boot from it, but that's all it ever does. 

Any idea what might be causing it?

---

### Post by dayhawk4 on 2007-06-20
Hello Andrew,

     Bootable CD-Roms can be tricky, especially when using USB based systems.  First off, I would like to go ahead and throw some pieces at you.  Have you ever successfully booted from a CD-Rom before using this DVD drive and this computer.  Have you ever been able to boot to another bootable DVD drive using this system?  What programs are we using to burn the ISO image?  I've subscribed to your thread, so go ahead and reply, and I will see what I can do.  The first thing that I am thinking is that I would like to make sure that the hardware likes each other.  If you haven't, give another image a try and let me know how it works for a bootable cd-rom.  Perhaps a different bootable DVD-rom image may work.  Go ahead and see what you can do.  For additional information on the El Torino Specification and different bios compatibility, my favorite site on this subject is:

[http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/)

This site has a wealth of information including some different packages under windows, and ways to make different multi-boot disks......

Read, Write, Try, and tell.....

dayhawk4

---

### Post by Andrew07 on 2007-06-20
> **dayhawk4 said:**
> Hello Andrew,

     Bootable CD-Roms can be tricky, especially when using USB based systems.  First off, I would like to go ahead and throw some pieces at you.  Have you ever successfully booted from a CD-Rom before using this DVD drive and this computer.  Have you ever been able to boot to another bootable DVD drive using this system?  What programs are we using to burn the ISO image?  I've subscribed to your thread, so go ahead and reply, and I will see what I can do.  The first thing that I am thinking is that I would like to make sure that the hardware likes each other.  If you haven't, give another image a try and let me know how it works for a bootable cd-rom.  Perhaps a different bootable DVD-rom image may work.  Go ahead and see what you can do.  For additional information on the El Torino Specification and different bios compatibility, my favorite site on this subject is:

[http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/)

This site has a wealth of information including some different packages under windows, and ways to make different multi-boot disks......

Read, Write, Try, and tell.....

dayhawk4

To answer your questions, this is the first time I've tried to boot a .iso from this DVD-Drive. I don't own another DVD-Drive... so I don't know if I can. I used Active@ Iso Burner to burn the iso image. I have burned images to a CD-ROM and used the built in CD-ROM drive to boot them and it worked perfectly. It's only with the DVD-Drive that I seem to have trouble. 

I'm looking at the site now.

Edit: Trying to boot a normal CD-ROM from the DVD-Drive does the exact same thing, but works fine for my other drive.

---

### Post by Andrew07 on 2007-06-21
Anyone have any idea what the problem is?

---

### Post by dayhawk4 on 2007-06-22
It sounds like there is an incompatibility with your bios and your dvd drive.... I know that this is not what you wanted to hear...  We are not dead in the water though.  It is just that we will have to do a little more work.  If you do enough digging, there will probably be documentation somewhere (I would start with your motherboard documentation) which lists the usb drives that this motherboard was tested with.... just as trivia knowledge.  Anyhow, the next step is to get away from the bios as your booting driver, and get to something which can boot your dvd drive.  The options are usb thumb drive (if your motherboard supports booting from that), and also there is the option of booting to a custom cd-rom drive which will give you a minix system, and then bootstrap to the DVD drive.  Basically, your booting up to another OS, and then using that OS's drivers to support your DVD drive.  While I have both seen it done with several different varients of hardware, and also done it with several myself, I am afraid that I can't give step by step instructions as hardware is going to be different.

The website that I cited before shows some multi-boot configurations and points to some software that might help.  That would be one source to try.  Heck, if you have a floppy, it wouldn't be beyond reason to try and use grub directly off a floppy to access the DVD.  I don't know if it would work, but it would be worth a try.  Give some of these a try.... I wish I could give more exact directions, but I hope these will help get you started.  As far as getting this to work directly, the only way that that will work is if the bios manufacturer fixes the problem.  This sometimes happens.  I would look-up your motherboard manufacturer, and see if they have an update for your motherboard.  I have had luck down this alley several times.  Unfortunately, if the motherboard manufacturer doesn't post a fix, there isn't anything else that can be done to make it work directly  (unless your game for something like a linux bios.....  depends on your motherboard if you can do this)

dayhawk4

---

