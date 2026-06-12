---
title: "Cannot install"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by quantumcat on 2010-11-08
Hi,

Im a comlete noob to Linux and this is my first post and install so please be gentle! I would like to use Ubuntu or any format of linux instead of win 7 which is now too dull....I have just downloaded the Ubuntu-10.10-netbook-i386 ISO. and tried to install Via win 7 in Wubi.

I cant get a 2GB usb stick so i used Wubi to install. there are links (provided on request) saying that you can download the ISO and run it direct via windows so i tried this and it fails. ( i have also allowed Wubi to connect to the net and this took a respective 2 hours to fail and the second time only 45 mins to fail) to hence why i tried the direct download install and there lies the problem.. 

I have placed the ISO in the same folder as reqested and run wubi, firstly it tried to download again so I canceled and uninstalled then turned my Wifi off to prompt it to run direct but there is no option to allow this.  

Basicly I have a samsung NC10 (out of the PC world config) with Win 7 (enterprise) 

I managed to get puppy linux to run off the USB (with massive problems with drivers etc which iis why I am trying Ubuntu) 

The irony is that I could of got my netbk with Ubuntu pre installed to save my self the conversion/ hassle lol

Can some one please advise me how to install Ubuntu (latest version) to my NC10 via Windows 7 using Wubi??

All your help would be greatly appreciated and sorry for such a discriptive post but information is key.... I can upload the logs of the failed installs if you need

Kind regards 

QC

---

### Post by bcbc on 2010-11-08
the current wubi.exe on ubuntu.com is set at version 10.04.1. So it will ignore the 10.10 .iso you downloaded. Plus, there is no netbook version 10.04.1 (they didn't release one) so it will repeatedly try to download 10.04 and then reject it (this is a bug that is not receiving any attention so no fix likely).

Right... so if you want 10.10 then you need a 10.10 wubi.exe. You can get one here: [http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)

But I've heard from many that the 10.10 netbook isn't the greatest. If you want 10.04 you should use the wubi here: [http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe](http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe)

---

### Post by quantumcat on 2010-11-08
Ubuntu up and running 

thank you bcbc 

Im already starting to love the Ubuntu community 

Kind regards

QC

(BTW i went for the 10.10 version & works well on the NC10, *i will report bugs*)

---

### Post by bcbc on 2010-11-08
> **quantumcat said:**
> Ubuntu up and running 

thank you bcbc 

Im already starting to love the Ubuntu community 

Kind regards

QC

(BTW i went for the 10.10 version & works well on the NC10, *i will report bugs*)
Great! You're welcome.

Also, welcome to the community. The forum is a great place to learn about Ubuntu (but it sounds like you already know that).

---

