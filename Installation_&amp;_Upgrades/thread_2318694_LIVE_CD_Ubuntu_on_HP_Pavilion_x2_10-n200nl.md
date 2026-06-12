---
title: "LIVE CD Ubuntu on HP Pavilion x2 10-n200nl"
date: 2016-03-28
forum: Installation &amp; Upgrades
---

### Post by sandrag2 on 2016-03-28
Hi,
I am a new user, i am italian so first of all sorry if my english is not perfect. For days I was trying to prepare a usb with the live of lubuntu to try it on my device. 
I prepared it by doing these things:
- using unetbootin to load the iso on the USB
- disabling Secure boot from BIOS and positioning the USB on the top of the boot priority list. Legacy option isn't available in the BIOS and every time I try to boot from USB this message is displayed :"The selected boot device failed"
- trying to force the boot with F9 but there are only empty directories...
Every time the boot failed the loading and I tryied to find something on Internet about my device. I found this article:
[https://wiki.debian.org/InstallingDebianOn/HP/Pavilion%20x2%2010%20(2015%20model)/Jessie](https://wiki.debian.org/InstallingDebianOn/HP/Pavilion%20x2%2010%20(2015%20model)/Jessie) 
Obviously this iso is plenty of bugs and I would like to get Ubuntu but I am not sure that it can be possible so I am asking to all of you if there is any way to use ubuntu on this device that seems to want a 32bit bootloader with a 64bit processor...
I am not expert but i tried to install ubuntu on another laptop and it works (because it is a normal laptop not like this one)...
Thank you

---

### Post by Bucky Ball on 2016-03-28
Welcome. You've tagged the thread 'lubuntu' but titled it Ubuntu, so I'm going with Lubuntu, but would apply to Ubuntu, too, probably. 

If you are using a supported release the ISO isn't full of bugs. Try 14.04 LTS for support until 2019 or 15.10 til half way through this year and download from [the Lubuntu download page]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu"). You can also [check the md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") if you think the ISO might be faulty.

Are you dual-booting with Windows? If so, is that installed in UEFI? If so, you need to install Ubuntu in UEFI.

You need to boot into Win and switch off hibernation then try again, but boot the USB in UEFI.

---

### Post by sandrag2 on 2016-03-28
Hi, thank you so much for your answer!!!
I have Windows 10 installed but I haven't tried to install linux in dual-boot. I was only trying to create and boot a live USB to try Ubuntu on this device before installing it but the boot is always failing... Every time I try to boot I first go in BIOS first and this is what appears: 
[IMG]http://i68.tinypic.com/2lxw85v.jpg[/IMG]
My BIOS is set in this way:
[IMG]http://i68.tinypic.com/104qbv9.jpg[/IMG]
In this photo the secure boot is enabled but I disabled it.

---

### Post by Bucky Ball on 2016-03-28
Second pic:  

> UEFI Boot Order
USB Diskette on Key

First one on the list.

Please attach large pics using Adv Reply or Go Advanced and the paperclip icon there. Some (potential helpers) have slow connections and/or vision issues. ;)

---

### Post by sandrag2 on 2016-03-28
Excuse me, I didn't know...
Loading images in this way?
Here is the BIOS boot settings (Secure boot disabled and the USB diskette on the top of everything)
[ATTACH=CONFIG]268040[/ATTACH]
Here is the boot list but when I go into Boot from efi file there are only empty directories...
[ATTACH=CONFIG]268041[/ATTACH]
The only way that I found is to Install Debian by using this guide:
[https://wiki.debian.org/InstallingDebianOn/HP/Pavilion%20x2%2010%20(2015%20model)/Jessie](https://wiki.debian.org/InstallingDebianOn/HP/Pavilion%20x2%2010%20(2015%20model)/Jessie) but I would like to have Ubuntu.

---

### Post by Iuly on 2016-03-28
Hi there! Welcome! I'm quite old but too quiet so far (thing I must correct)
Back to the thread, I have found this link from an hp forum. It seems you are not the only one 
[http://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/Linux-on-HP-Pavilion-x2-detachable-PC-10/td-p/4810665](http://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/Linux-on-HP-Pavilion-x2-detachable-PC-10/td-p/4810665)

---

### Post by sandrag2 on 2016-03-28
Hi!! Thank you very much for answering!
Yes, I've already seen it but it helps only to get Debian, and there isn't a live version of the iso supported by my device... There is always an italian guide but they say that the wifi don't work so I can't install debian without trying it... Isn't there a way to get Ubuntu on it?

---

### Post by Bucky Ball on 2016-03-28
> **Bucky Ball said:**
> Second pic:  

First one on the list.

Please attach large pics using Adv Reply or Go Advanced and the paperclip icon there. Some (potential helpers) have slow connections and/or vision issues. ;)

Have you done this? You have not responded. :-k

Let's forget about Debian. What happens when you do the above?

---

### Post by sandrag2 on 2016-03-29
Yes, I put USB Diskette on the top, disabled Security Boot and also I tried to force the boot from usb but no way...

---

### Post by Bucky Ball on 2016-03-29
And you have hibernation switch off in Windows, or you can't boot to Win?

---

### Post by sandrag2 on 2016-03-30
I can correctly boot to Windows, the problem is the Linux Bootloader :(

---

### Post by Wayne_Anderson on 2016-03-30
If you have the option, change the option os windows 8.x to windows 7 in the bios.

 See 2nd pic here: [http://www.guruht.com/2014/09/how-to-install-windows-7-on-asus-x200m.html](http://www.guruht.com/2014/09/how-to-install-windows-7-on-asus-x200m.html)

---

