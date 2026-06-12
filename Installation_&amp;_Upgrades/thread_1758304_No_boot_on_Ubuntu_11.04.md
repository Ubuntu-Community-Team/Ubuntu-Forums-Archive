---
title: "No boot on Ubuntu 11.04"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by sid.mallya on 2011-05-14
Hey guys ! I downloaded both 64- and 32-bit versions of Ubuntu 11.04. I run Ubuntu 10.04 LTS on my desktop and Linux Mint 10 on my laptop. 

The 32-bit version doesn't create a startup disk at all, giving me an "Input/Output Exception - Installation failed" message on both the laptop and desktop.

The 64-bit version goes into bootloader but on selecting the "try ubuntu without installing" option, just displays a blank screen.

What is going wrong ? I am using a usb-stick installation.

(I am trying to use Ubuntu on my Dell XPS 15)

---

### Post by MAFoElffen on 2011-05-14
> **sid.mallya said:**
> Hey guys ! I downloaded both 64- and 32-bit versions of Ubuntu 11.04. I run Ubuntu 10.04 LTS on my desktop and Linux Mint 10 on my laptop. 

The 32-bit version doesn't create a startup disk at all, giving me an "Input/Output Exception - Installation failed" message on both the laptop and desktop.

The 64-bit version goes into bootloader but on selecting the "try ubuntu without installing" option, just displays a blank screen.

What is going wrong ? I am using a usb-stick installation.
Please vidt this sticky and read post 3 for instructioons on using a "nomodeset" startup[ option with the LiveCD. Does have pictures to show the screens you should see and what options to use.

Summary:
When you get to the keyboard select screen, press <esc> > Press <F6> > Arrow down to the nomodeset option to highlight it > Press shift or enter > Press <Esc> to back-out to the menu (option will be remebered) Select "try..."

---

### Post by Dutch70 on 2011-05-14
If the 64-bit version works, there is no reason the 32 bit wouldn't. There is probably something wrong with your downloaded .iso. That being said, I would recommend the 64-bit version anyway.

I'm not sure what MAFoElffen meant by "vidt this sticky" I think he just forgot to put the link in there & I'd say we've all done that a few times. Anyway here is the link for the nomodeset boot option.
[[COLOR="Red"]How to set NOMODESET and other kernel boot options in grub2 [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by sid.mallya on 2011-05-15
Haha .. Ya ! I was wondering what was he talking about too. Anyway, I tried the solution outlined in the "nomodeset" thread and that didn't work either.

I dont think there is a problem with the ISO cause it is working fine on my VirtualBox .. =/

Right now the error I am  getting is "unable to mount /dev/sr0" or "unable to mount live filesystem"

---

### Post by sid.mallya on 2011-05-15
Quick question. Why isn't the md5 checksum posted on the Ubuntu website. I generated the local checksum to see if the ISO downloaded wholly or not. But there is nothing to compare against. =/

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by sid.mallya on 2011-05-15
Bump !

---

### Post by drs305 on 2011-05-15
Try this link for Natty MD5SUMs

[http://releases.ubuntu.com/natty/MD5SUMS]("http://releases.ubuntu.com/natty/MD5SUMS")

---

### Post by sid.mallya on 2011-05-15
Ok ! From the checksums its clear that there is nothing wrong with the ISO. Neither of the ISOs (32- or 64-bit) one are booting up .. It keeps saying 

```
unable to mount /dev/sr0
```

---

### Post by drs305 on 2011-05-15
At this point I usually recommend inserting another type of bootable CD/DVD (movie, software, etc) and see if it will boot. If a commercial product won't boot, the chances are very good it's your hardware.

---

### Post by sid.mallya on 2011-05-15
I highly doubt that something is wrong with the pen drive. It worked like a charm as a Linux Mint 10 liveUSB just yesterday. Anyway, Ill give it a shot and get back to you on this one.

Thank you.

---

### Post by drs305 on 2011-05-15
> **sid.mallya said:**
> I highly doubt that something is wrong with the pen drive. It worked like a charm as a Linux Mint 10 liveUSB just yesterday. Anyway, Ill give it a shot and get back to you on this one.

Thank you.

I misunderstood. I thought it was CD trouble...

---

### Post by sid.mallya on 2011-05-15
There was a problem with the Flag management of the pen drive. Since, I have tried making it a liveUSB so many times, the boot flag was staying on even after formatting the pen drive. Strange, but I guess that can happen.

Anyway, after manually deselecting the flag and reinstalling the ISO on the USB, the process was a success; well, atleast barely. Now there is a new problem --> 

[http://ubuntuforums.org/showthread.php?p=10819629](http://ubuntuforums.org/showthread.php?p=10819629)

---

