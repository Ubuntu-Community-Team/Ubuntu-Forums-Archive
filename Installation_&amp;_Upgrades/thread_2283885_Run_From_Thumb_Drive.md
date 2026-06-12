---
title: "Run From Thumb Drive"
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by Michael_Sinsabaugh on 2015-06-25
I've been in IT for a good while.  Whenever possible, if I'm learning a new software package or new (to me) OS I like to have it to play with while I'm learning.  Partially because of an article I read about personal security I'm looking to learn Linux and run it from a DVD (or maybe a thumb drive).  To that end I'm starting with  making a bootable thumb drive.

I downloaded Pen Drive Linux's USB Installer for that, chose the 32 bit Ubuntu iso (I want this to work on pretty much any computer) and went to town.  It worked.  I booted from the thumb drive.  Here is where the question comes...

I was presented with a screen to choose between installing Ubuntu or trying Ubuntu.  It seems to me that this isn't quite what I'm looking for.  As I understand it, Install will install Ubuntu onto my hard drive (or a partition) and while I might want to do that at some point that's not what I'm looking to accomplish right now.  When I choose to "try" it, Ubuntu loads and takes me to a desktop.  It looks (though I haven't done much experimenting yet) like this is an image that would load each time.

What I'm thinking of is a thumb drive that when I boot from it, I go to my desktop however I have it configured.  Ultimately I want to get a setup with applications and tools that I want and make an iso of it and burn it and run it from a DVD.

Could anybody here a) straighten me out on getting the thumb drive to boot the way I'm thinking (or let me know that I can't), b) give me any good links to help me learn the system, c) give me links to any tools that would be good to have, d) give me any pointers on making an iso to burn to DVD,, and/or e) point me to any good forums/posts

Any help would be greatly appreciated

---

### Post by dino99 on 2015-06-25
an old question, but still a good howto
[http://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive](http://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive)

---

### Post by grahammechanical on 2015-06-25
The Ubuntu ISO image when burned to a DVD disc will give us the choice or Try Ubuntu or Install Ubuntu every time we load the disc and because it is a DVD disc any changes we make will be lost every time we shut down the live session.

The same thing will happen if we use a USB memory stick unless we install Ubuntu with something called persistence. If the memory stick is large enough a few GB will be set aside for storage and we do not lose our configuration when we shut down the OS.

There is something that you need to keep in mind if you want to use this method on all kinds of hardware. The Ubuntu live session uses an open source video driver and that allows it to work on all kinds of video cards. When we install Ubuntu we get an option to also install third party software. If we tick that box we not only get some proprietary video and audio codecs but also a proprietary video driver that suits the video adapter in that machine. That particular video driver will not work with other video adapters from other manufacturers . So, do not tick that box. We can install the video and audio codecs after installation. They are in the software centre as Ubuntu Restricted Extras.

This is one way to do it.

[http://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive](http://askubuntu.com/questions/170454/can-i-install-ubuntu-to-my-32-gb-usb-pen-drive)

This is another

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Note image #3 and the slider that sets the size of the persistence file. The size of the space for the persistence file will vary according to the size of the USB memory stick. The larger the memory stick the larger the persistence file and the more data that can be stored.

The boot loader (grub) needs to be installed on the memory stick. Watch out that it does not get installed to the machine's hard disk (sda in Linux language).

Regards.

---

