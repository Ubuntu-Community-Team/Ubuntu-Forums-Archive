---
title: "Installing Gutsy, Windows XP Home, Dell Mediadirect"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by teabuntu on 2007-11-15

Hello,
Although I'm still at a stage where I'm using the Live CD to become familiar with Ubuntu and Linux (this is my very first time in learning about Linux and Ubuntu), I'm considering installing Ubuntu on a USB flash disk, while keeping Windows XP Home Edition with Dell Mediadirect (either version 2 or 3).  How can I make this happen?

Also, this might sound like a stupid question, but upon reading various documents regarding installation and so forth, I got the feeling that when you install Ubuntu (regardless of whether it's on a single disk with Windows or seperately like on a USB flash stick), the Ubuntu installtion changes the BIOS of my computer.  Is this correct?  

When installing Ubuntu on a USB flash stick, wchich option should I choose when during the installation, I am asked about partition and so forth.  Do you know of a web site which describes in detail about the kind of installtion that I would like to do?

Thank you for any help or advice on this matter.

---

### Post by bulldog on 2007-11-15
You can find more info here,

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive).

---

### Post by teabuntu on 2007-11-15
Thanks for the reply. 

Is there a website where it talks directly about installing the three that I meantion above?  Thanks.

---

### Post by teabuntu on 2007-11-16
bump

---

### Post by inaneframe on 2007-11-16
[Here]("http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/")

I did it with a 2GB thumb drive, it's not that hard but I would recommend that you make sure that your bios can load from a thumb drive.  Many machines built as late as a year ago cannot boot from a thumb drive, very lame.

As regards your question about the BIOS and ubuntu, no.  Ubuntu does nothing to your BIOS.

GOOD LUCK!!!

---

### Post by staticvoid on 2007-11-16
> **teabuntu said:**
> Hello,
 [...]How can I make this happen?
[...] the Ubuntu installtion changes the BIOS of my computer.  Is this correct?  
[...]Do you know of a web site which describes in detail about the kind of installtion that I would like to do?

Thank you for any help or advice on this matter.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

It does not edit your BIOS, it just adds a GRUB boot loader to the beginning of your hard drive. If you have a dual boot then you can boot into Ubuntu, ubuntu memtest, windows recovery or windows... basically :)

hope that helped. I've never done a linux on a pendrive thing before. you shold first make sure your computer can boot from USB. newer computers can, but just to be sure :) check your bios for the boot order and see if removable drives or something is listed.

SV

p.s. 6 hours to bump?

---

### Post by staticvoid on 2007-11-16
Hey, I just took this pendrivelinux.com ubuntu 7.10 tutorial and it worked. SUPER easy if you just go step by step.  the main thing is though:

MAKE SURE YOUR COMPUTER CAN BOOT FROM USB.

some don't :)

sv

p.s. its cool, you can save your settings and stuff :)

---

### Post by teabuntu on 2007-11-16
Hi,
Thank you guys for your post.  I'm taking a look at it now, but it does not mention installing Mediadirect as well.  I found on another forum that installing Linux changes the Master Boot Record.  I'm not at all familiar with computer termnology so I hope you bear with me when I ask if MBR is the same thing as BIOS?  

I found a forum about installing Windows, Ubuntu and Mediadirect, and it said that installing Linux changes the MBR, and changing the MBR will not allow Mediadirect to function..... I've been doing searches over the internet to find someone who has acutally done this and hoepfully can explain the detials of the process in easy to understand language.  Unfortunately, I have yet to find such a web site...

---

### Post by bulldog on 2007-11-16
> **staticvoid said:**
> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

It does not edit your BIOS, it just adds a GRUB boot loader to the beginning of your hard drive. If you have a dual boot then you can boot into Ubuntu, ubuntu memtest, windows recovery or windows... basically :)

hope that helped. I've never done a linux on a pendrive thing before. you shold first make sure your computer can boot from USB. newer computers can, but just to be sure :) check your bios for the boot order and see if removable drives or something is listed.

SV

p.s. 6 hours to bump?

That is a very nice link.staticvoid,thank you.

---

### Post by teabuntu on 2007-11-16
bump

---

### Post by teabuntu on 2007-11-20
Hi,
I guess no one has really done this kind of a install before?

---

