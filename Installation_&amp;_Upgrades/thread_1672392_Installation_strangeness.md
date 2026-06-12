---
title: "Installation strangeness"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by Tedwin on 2011-01-20
Hi all. I am having a problem that I hope someone can help with. I'm running a Lenovo G550 laptop with an intel celeron 900 @ 2.20GHz, 4GB RAM and Win7 64bit. I successfully installed a dual boot of ubuntu 10.10 32bit but then uninstalled it cause I wanted to put the 10.04LTS on my machine. I got it uninstalled ok (fixed MBR w/ win start disc), but when I boot with the 10.04 disc it starts, but then the screen fills up with this and freezes:
[   0.000101]  [<c0041aca>] ? acpi_init+0x0/0x10c
[   0.000150]  [<c00192c9>] do_basic_setup+0x47/Ox57
[   0.000198]  [<c00193de>] kernel_init+0x105/0x19d
[   0.000247]  [<c00192d9>] ? kernel_init+0x0/0x19d
[   0.000297]  [<c010363e>] kernel_thread_helper+0x6/0x10
these are just the last five (i can post the rest if it'll help).
I tried to re-install 10.10, but now when I try to boot that disc it'll start but then says:
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
I did get the 11.04 alpha to install but when I realized it didn't even have the main menu ready yet, so I uninstalled it.


Does anybody know what's going on. Thanks in advance.

---

### Post by Tedwin on 2011-01-20
It just seems really weird that the 10.10 worked fine, but now it doesn't. What is causing this??
I really want to like ubuntu, please help.

---

### Post by sikander3786 on 2011-01-21
Welcome to the forums :-)

And apologies for the late reply. I think forum weirdness in the last couple of days has something to do with that.

So, first of all check the downloaded image for any possible defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the sums match, check your disk for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Or if using a USB drive, try unetbootin,

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

If the errors persist, you probably need to put in some boot parameters from F6 menu. There are 6 of them and you might need to try all of them, one by one.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Keep us posted ;-)

---

### Post by Tedwin on 2011-01-22
Alright. I checked the 10.04 image with md5sum and it was off, so there  was something wrong with that image. The 10.10 image had matching sums,  but it still froze as I mentioned before. I tried the install DVD in  a older compaq presario 5000 with only 256Mb of RAM and it gave me a  sector read error. I figured that the DVD got scuffed and was no good so  I burned the image to a CD on the slowest setting to make sure it  worked. When I tried to boot on the lenovo the same error I mentioned  initially took place. Booting the CD in the compaq worked and I was able  to verify that the disc was good. I was even able to get to a desktop  running the live cd. Long story short, by **disabling acpi** in the  boot options I was able to install ubuntu 10.10 on the lenovo and am  running it now :-) It wasn't obvious to me that I  had to push a key to  get to the menu to access boot options. The pictogram went over my head.  I just kept putting the disc in and patiently waiting while my computer  crashed. I'm curious to know why my machine booted and installed  fine  the first time, but was unable to after uninstalling without disabling  acpi. Anyways, thanks for helping me get set up. I think I'm going to  stick with running 10.10. Thanks again..                    ~Tedwin

---

