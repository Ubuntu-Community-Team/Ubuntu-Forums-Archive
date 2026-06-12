---
title: "Dell Mini 12 won't boot from USB"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by jcoglan on 2010-01-11
I'm trying to boot my Dell Mini 12 from a USB boot disk with the ubuntu-9.10-alternate-lpia.iso image installed (I've also tried ubuntu-9.10-netbook-remix-i386.iso). I turn the machine on, press F12 to get to the boot menu, then select the USB disk. After this I just get a blinking cursor at the top left of the screen and nothing else happens. How do I get it to boot the installer?

---

### Post by mocoloco on 2010-01-12
How did you make your USB image bootable?  I usually use the "USB Startup Disk Creator" from another Ubuntu machine.

---

### Post by jcoglan on 2010-01-12
I used the Ubuntu program from System/Administration/Create a USB startup disk after formatting the stick to fat32 with gparted.

Interestingly, I've two .img images (one for 9.04 netbook, and one for some obscure 8.04 variant called UNR 1.0.1) and if I make USB sticks from those using the `dd` command, my Mini can boot from them.

---

### Post by PRC09 on 2010-01-12
There is a seperate tool for creating bootable usb drives from .img files called usb-imagewriter.....


[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

---

### Post by jcoglan on 2010-01-12
Thanks, but .img files aren't the problem. I currently have UNR 1.0.1 installed on my Mini. I tried installing 9.04 netbook remix but it won't support the full screen resolution. I have both as .img images, and USB sticks created from them using `dd` both boot my Mini to the desktop just fine.

The problem is I cannot boot from USB sticks created from any of the .iso images I have, and all the 9.10 versions (i386, amd64, netbook, LPIA) come as .iso files. After choosing the USB stick from the boot menu, I get a blinking cursor and nothing else happens. Pressing any key produces a beep but otherwise does nothing.

Anyone have another suggestion?

---

### Post by jcoglan on 2010-01-12
I should clarify, for making a USB stick from an IMG, I do:

```
sudo dd bs=1024 if=path/to/image.img of=/dev/sdg
```

For ISO files, I use the "Create USB startup disk" from Ubuntu's System menu.

---

### Post by snowpine on 2010-01-12
You could try Unetbootin, another tool for making a bootable USB from an .iso:

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

I am assuming you've already done the research about getting Ubuntu to work with the Dell Mini's Intel GMA500 graphics?

---

### Post by jcoglan on 2010-01-12
Thanks for the link, will check it out later. For graphics, there was a package for PSB in the repos under UNR 1.0.1. Ubuntu wiki says you can get this from a PPA now, so might try installing 9.04 again and updating from there.

What's weird is I have images that will boot to the desktop, albeit with a funky resolution, without installing PSB drivers, and a ton of .iso files that don't boot at all.

---

### Post by mocoloco on 2010-01-12
For info on installing 9.10 on a Dell Mini 12, including the Poulsbo driver, check the links I put in [this post]("http://ubuntuforums.org/showpost.php?p=8614829&postcount=831").

---

### Post by jcoglan on 2010-01-13
Thanks for all the pointers. Still no joy with .iso images but I managed to install from my Jaunty netbook image and upgrade that to Karmic. Got the PSB and Broadcom drivers installed as per above links and everything seems fine.

It is telling me my hard drive has bad sectors but I've seen that reported as a bug elsewhere.

---

