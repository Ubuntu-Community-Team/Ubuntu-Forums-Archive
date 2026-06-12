---
title: "Modem Problems"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by imortlco on 2005-09-13
Hi!

I'm a total newbie to anything other than Windows.  I'm REALLY wanting to try out, and have work, ONE of the Linux distros.

I just got by Ubuntu CD's and installed it on my Dell Inspiron 3800 laptop.  It looks GREAT, and I am impressed already.  It is slim, neat and tidy, but I CANNOT get my modem to dial or do anything.  

It seems as if it's recognized in device manager, and I've searched the forum and tried the sudo pon/poff etc., and sudo pppconfig.  All SEEMS to go OK, and I actually get a 'connected time 0:00' flag when the mouse goes over my dial up phone icon.  When I try and connect, the window flashes real quick where I see my provider, and then nothing happens.  Sometimes I get an error window like SICOGOT or something.  Sorry, I can't recall exactly and it's not in front of me right now.

Any help would be appreciated.  I am downloading some more other free distros to see if one will eventually work with my systems or not.

THANKS!!!

BOB

---

### Post by mlomker on 2005-09-13
Laptops use winmodems.  The free linux distributions are not going to include drivers for them.  Xandros and Linspire are likely to work for you but they usually cost a few bucks.

The only alternative is to figure out how to install the drivers yourself.  [www.linmodems.org](http://www.linmodems.org)

---

### Post by imortlco on 2005-09-14
THANK YOU mlomker!!!  I appreciate the quick reply, and the info.

I'm glad to hear you say-so about Linspire, as I just downloaded my free copy from their site.  I will try it and see what happens.

I will try Ubuntu on my desktops and see if it works on them, although they are Conexant modems, which I think are winmodems too right?

Anyway, THANKS again, and I'll keep searching and researching.

BOB

---

### Post by goldrush on 2005-09-14
As another newbie I also fell into the Modem problem trap, although I eventually got mine installed and recognised.
Then I spent hours trying to get it to work.. because I forgot to set it up.
The GUI set up system did not work in my case.. sugggest you read "DialUpModem Howto" on Wiki. Other info on some types of "winmodems" there also

---

### Post by imortlco on 2005-09-14
THANK YOU.  I have just found that article and will give it a try.

BOB

---

### Post by mlomker on 2005-09-14
Conexant modems usually use a driver called slmodem.  You can also purchase a driver from [Linuxant](http://www.linuxant.com/company/).  I bought one for my previous laptop and it worked perfectly.

---

### Post by imortlco on 2005-09-14
THANKS again!

I will look into both of those possibilities, as the "How-To" article didn't make any difference for me today.  I'm sure it's because I'm just plain missing the driver.

BOB

---

### Post by imortlco on 2005-09-15
I just found the slmodem driver on the Smartlink site, downloaded it, and the readme file.  I'll give that a try and see what happens.

I appreciate all the help, ideas and suggestions.  THANKS!!!

BOB

---

### Post by nikink on 2005-09-21
For ubuntu 5 try this
[http://linmodems.technion.ac.il/packages/smartlink/snapshots/slmodem-2.9.11-20050816.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/snapshots/slmodem-2.9.11-20050816.tar.gz)
or another from here [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
because the driver from smlink.com doesn't work with the ubuntu version of the kernel

---

### Post by imortlco on 2005-09-22
THANK YOU!!!  I will it.

---

### Post by foxiness on 2005-09-22
this it work with me and i hope it will work with you 

[http://www.ubuntuguide.org/#installsmartlinkdriver](http://www.ubuntuguide.org/#installsmartlinkdriver)

---

### Post by imortlco on 2005-09-23
THANK YOU too!  I'll try it.

---

