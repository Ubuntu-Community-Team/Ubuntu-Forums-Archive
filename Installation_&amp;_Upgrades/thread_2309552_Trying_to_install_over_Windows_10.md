---
title: "Trying to install over Windows 10"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by rich2506 on 2016-01-11
W10 is stubbornly hanging in there. Got it on a new Dell desktop and am trying to wipe it and replace it with Ubuntu. Tried putting the expanded 15.10 download on both a CD and a flash drive. No luck, it keeps booting into Windows. Tried re-doing the boot order so that it goes into both IPV4 and IPV6. Still boots into Windows. Any other ideas/inspirations?

---

### Post by sandyd on 2016-01-11
Have you tried pressing F12 (At least on this Dell laptop, it is F12), and booting from there?

On mine, the usb drive shows up right under UEFI OPTIONS.

---

### Post by rich2506 on 2016-01-11
Hmm, well, I got it to go to a black screen, where it then says 

checking media......
media present.....
start PXE over IPv6.

then after a few minutes, it changes the last line to read 

start PXE over IPv4

and then goes to Windows. So it appears that it tried to boot into Linux, but something's preventin it from doing so.

---

### Post by sandyd on 2016-01-11
Hi, I just noticed that in your first post, you said it was "expanded".

Was the ISO written directly to DVD/USB, or was it extracted first?

The ISO should be written directly to DVD/USB.

Some instructions below for DVD/USB

USB: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
DVD: [http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

---

### Post by rich2506 on 2016-01-11
I think I downloaded it as an ISO and then expanded it to go onto the CD/Flashdrive. I'll try your suggestion!

---

### Post by rich2506 on 2016-01-11
rasm, frasm %$#@%!!! Nope. I got the flash drive properly formatted and I could tell that the flash drive was clearly reacting to instructions from the computer, but it went back to Windows, just as before.

---

### Post by yancek on 2016-01-11
>  			 			I think I downloaded it as an ISO and then expanded it to go onto the CD/Flashdrive. I'll try your suggestion! 		

No chance the above will work.  Do you set the DVD or flash drive to first boot priority in the BIOS?
What software did you use to put Ubuntu on the flash drive?  Common software used would be pendrivelinux, unetbootin and others.

---

### Post by rich2506 on 2016-01-12
Yes, I've set the BIOS so that it boots from te "IPv6" and then the "IPv4."  As  said, it clearly TRIES to boot from the flash drive. 
Initially, I was using a Windows software to expand it and then switched to what Sandyd suggested.

---

### Post by Mark Phelps on 2016-01-12
Using IPv4 and IPv6, you're trying to boot from your Network!

You can't just either copy an ISO file to a DVD/USB stick or expand the ISO file into its directories and copy those.

If you're using a DVD, you have to use a DVD "burning" app that will use the ISO image file.

If you're using a USB stick, you have to use a boot USB creation app, that will create a bootable USB from the ISO image file. Yancek mentioned some of the apps that are used to do that.

---

### Post by rich2506 on 2016-01-12
Yeah, I was puzzled over the fact that the Wndows BIOS didn't include any way to boot from either a flash drive or from a DVD. I'll give Sandyd's DVD-booting program a try and then those other programs too. Thanks!

---

### Post by rich2506 on 2016-01-12
Woo-hoo! Got it to work! Got detailed instructions on how to arrange the boot order and used the flash drive (Thanks, SandyD!), it's installing now!
:D

---

