---
title: "How do I install Ubuntu Server from a USB without the Internet?"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by curtis8 on 2014-04-08
Pretty simple straight-forward question yet I cannot find an answer on the net. All I want to do, is use Universal USB Installer, or YUMI or any other image-to-usb loading program to put a distro of Ubuntu Server (an .iso direct from Ubuntu.com) on my USB, boot from it, and install the thing on another drive WITHOUT USING THE INTERNET. It seems that no matter what I do the installation from a USB always attempts to start downloading the package contents, and there's no option to load the contents from the USB (similar to how you load the contents from a CD/DVD when you install it that way). Seriously, what is the difference between burning the .iso to a disc and loading the .iso to a USB? I've downloaded the image specifically so that I don't have to download anything else and install Ubuntu as many times as I want without the internet. 

Am I going about this process completely wrong? It's driving me insane :confused:

EDIT:

This program will do the trick for most Linux distributions.

[http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager)

---

### Post by mastablasta on 2014-04-08
somewhere in the porcess you probably set it to install updates. [https://help.ubuntu.com/12.04/serverguide/installing-from-cd.html](https://help.ubuntu.com/12.04/serverguide/installing-from-cd.html)

or it needs internet connection to give suggestion like for time setting etc.

also there should be no difference installing from CD or from USB appart from the fact that USB is faster and has a read and write option.


you can unplug it from internet if you do not want it to connect to internet

---

### Post by curtis8 on 2014-04-08
> **mastablasta said:**
> somewhere in the porcess you probably set it to install updates. [https://help.ubuntu.com/12.04/serverguide/installing-from-cd.html](https://help.ubuntu.com/12.04/serverguide/installing-from-cd.html)

or it needs internet connection to give suggestion like for time setting etc.

also there should be no difference installing from CD or from USB appart from the fact that USB is faster and has a read and write option.

you can unplug it from internet if you do not want it to connect to internet

Nope, I never tell it to install updates, I set the time and location manually, and I'm trying to install this with no network connection.

---

### Post by sudodus on 2014-04-08
I think you might have problems installing Ubuntu Server 12.04 LTS from USB, while it works from CD/DVD. It is the same with the mini.iso. But the newest version, 13.10 can be installed from USB (and most likely also the next version, 14.04 LTS to be released very soon). At least it works from a USB drive that is flashed directly from the iso file using ***mkusb*** according to this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

If you have problems also with this method and version, I suggest that you install a mini system (text only) with the experimental ***9w*** installer, add what you want to install and tweak, and port the installed system (move the HDD) to the target computer. This system will have a network that is portable (so it works in 'any' computer when you connect it to the internet, at least it is working without any manual settings with wired internet).

See this link, posts #88 and #89 and the following posts

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

---

### Post by curtis8 on 2014-04-09
> **sudodus said:**
> I think you might have problems installing Ubuntu Server 12.04 LTS from USB, while it works from CD/DVD. It is the same with the mini.iso. But the newest version, 13.10 can be installed from USB (and most likely also the next version, 14.04 LTS to be released very soon). At least it works from a USB drive that is flashed directly from the iso file using ***mkusb*** according to this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

If you have problems also with this method and version, I suggest that you install a mini system (text only) with the experimental ***9w*** installer, add what you want to install and tweak, and port the installed system (move the HDD) to the target computer. This system will have a network that is portable (so it works in 'any' computer when you connect it to the internet, at least it is working without any manual settings with wired internet).

See this link, posts #88 and #89 and the following posts

[http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586](http://ubuntuforums.org/showthread.php?t=2209683&page=5&p=12957586#post12957586)

Version 13.10 yields the same problem. 

Does anyone know how to avoid this problem using a Windows-based USB-boot program, eg Universal USB Installer or YUMI?

I don't want to use **mkusb** because it looks like a very long, tedious process and has to be done via a Linux OS which is really inconvenient compared to using the Windows process I mentioned above.

---

### Post by sudodus on 2014-04-09
Then I would recommend [http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager), that is available for Windows and does what you can do with mkusb (flash the iso file to a USB drive).

---

### Post by curtis8 on 2014-04-10
> **sudodus said:**
> Then I would recommend [http://sourceforge.net/projects/win32diskimager](http://sourceforge.net/projects/win32diskimager), that is available for Windows and does what you can do with mkusb (flash the iso file to a USB drive).

After testing, I can confirm that this method works perfectly for most Linux distributions. It is exactly what I needed to install Ubuntu Server from a USB without the internet after using a Windows USB-boot program, but as I just said it doesn't seem to work for some images.

---

### Post by sudodus on 2014-04-11
It works for hybrid iso files. In Ubuntu you can use the program ***isohybrid***, that can convert many (non-hybrid) iso files so that they will boot when flashed to USB drives.

All current Ubuntu versions and flavours are hybrid iso files.

---

