---
title: "Ubuntu LiveCD crashing at desktop"
date: 2016-04-01
forum: Installation &amp; Upgrades
---

### Post by coreyspledger on 2016-04-01
Howdy all. I'm new to the forum but I've been browsing the topics here for months. I'm still not certain if this is the proper sub to post in but I'll give it a go anyway.

I forgot the Windows password to my HP s5737c Slimline (only non-factory part is the RAM, up from 3gb to 4) that I'm trying to do a few things on, first to get my Windows key through copying the config info, and second to turn this box into a proper Ubuntu machine that I can learn on. So on to the problem.

I used a bootable flash drive with 14.04.2 and selected Try before Install. It loads the desktop which promptly freezes up. So after some searching, I tried again after selecting nomodeset in the F6 options. Same result. I've done this multiple times now after testing the memory and the hard drive, all apparently fine, with few differences and all ending up frozen, black screened, or a screen full of static mess. I've noticed several times that small pixelations appear around my cursor, errors in small areas of pixels on the desktop, and every time I cannot select any icons in the left side tray to open anything. I'm led to assume that it has something to do with the graphics drivers, but I have no idea what to do. I can't even access the terminal.

As I've said, I'm still learning, so forgive me if I don't immediately understand something.

Thanks for reading :D

---

### Post by RobGoss on 2016-04-02
Hello and welcome, I'm not sure how old your machine is but the heaver distributions will not preform well on older machines unless you get a lighter distro like Lubuntu , Xbuntu, and a few others that are available.

Also here is a list of graphic card that are supported for Ubuntu
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards) 

I would recommend trying a lighter distro before you decide to upgrade any of the components for your machine.

---

### Post by mörgæs on 2016-04-02
> **RobGoss said:**
> 
Also here is a list of graphic card that are supported for Ubuntu
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards) 


Yes, these cards are supported but many others are, too. The list has not been updated for a long time.

---

### Post by RobGoss on 2016-04-02
> **mörgæs said:**
> Yes, these cards are supported but many others are, too. The list has not been updated for a long time.

Yes I was under that impression also I would think there are much more supported

---

### Post by coreyspledger on 2016-04-02
Thanks for the list. I'm pretty certain this computer's not so old as to have its graphics component be unsupported, I've successfully installed Ubuntu on much older equipment (but I suppose that's not much of an argument). 

I've tried every fix I'm capable of understanding so far and still nothing. I do wonder though if a different distro might function better. I was considering trying with Linux Mint even though I don't really care for it.

---

### Post by $yl9pAR%t on 2016-04-02
HP website shows, you have probably nvidia 6150 graphic card. From my experience with this card, Unity (because of Compiz) doesn't work properly when using proprietary nvidia-304 driver. It works with nouveau driver, but in this case cpu usage is very high and system works very slow and even freezes.

Both Xubuntu 14.04 and Xubuntu 16.04 work very well with this gpu.

---

### Post by RobGoss on 2016-04-02
> **coreyspledger said:**
> Thanks for the list. I'm pretty certain this computer's not so old as to have its graphics component be unsupported, I've successfully installed Ubuntu on much older equipment (but I suppose that's not much of an argument). 

I've tried every fix I'm capable of understanding so far and still nothing. I do wonder though if a different distro might function better. I was considering trying with Linux Mint even though I don't really care for it.


You can also try Lubuntu and Xbuntu, there're lighter distro's and might work better.

---

### Post by coreyspledger on 2016-04-02
> **mefisto888 said:**
> HP website shows, you have probably nvidia 6150 graphic card. From my experience with this card, Unity (because of Compiz) doesn't work properly when using proprietary nvidia-304 driver. It works with nouveau driver, but in this case cpu usage is very high and system works very slow and even freezes.

Both Xubuntu 14.04 and Xubuntu 16.04 work very well with this gpu.

> **RobGoss said:**
> You can also try Lubuntu and Xbuntu, there're lighter distro's and might work better.

mefisto888, yep that's the one.

Thanks guys. Good to know my graphics card is known at least to cause an issue. I've got an ISO for almost every distro short of Xubuntu and Lubuntu but I guess this gives me an excuse to play with those too.

---

### Post by RobGoss on 2016-04-02
The best thing about Ubuntu is there are so many to choose from. I only have one problems with one of my older laptops can't seem to get any distro to run smoothly on it but one out of five machines I'm not complaining.. Let us know how it goes...

---

### Post by coreyspledger on 2016-04-02
> **RobGoss said:**
> The best thing about Ubuntu is there are so many to choose from. I only have one problems with one of my older laptops can't seem to get any distro to run smoothly on it but one out of five machines I'm not complaining.. Let us know how it goes...
Will do. Just got the ISO's for both, starting with Xubuntu first.

I've had some good luck playing with Arch Linux on an ASUS Eee PC that wouldn't run any other distro with stability but I'm still not adept with that enough to recommend it.

Update: Xubuntu is working and it's flipping beautiful. Doesn't seem to want to move the System32 folder for me but I guess I'll have to work that out as I go.

Final Update: Copied files and ripped necessary product keys. I think this one's wrapped up. Thanks again for the advice and info! On to install!

---

