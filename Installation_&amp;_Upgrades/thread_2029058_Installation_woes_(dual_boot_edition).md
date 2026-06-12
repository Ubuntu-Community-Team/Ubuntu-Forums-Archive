---
title: "Installation woes (dual boot edition)"
date: 2012-07-19
forum: Installation &amp; Upgrades
---

### Post by mousestalker on 2012-07-19
I've built a totally new PC. As per almost everyone on the web, I installed Windows 7 first, left plenty of room on the boot hard drive for another OS and installed all drivers and programs.

I have tried to install 12.04 using two live cd's and a flash drive. I tried installing wubi. Every time installation hangs on a blank purple screen. The screen remains blank for at least six hours (overnight).

Here are the build hardware components:

[Gigabyte z77x-d3h motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128546")
[Intel i5-3450 3.10 GHz CPU]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819116506")
8 gigs Ballistix memory in 2 sticks (memory has tested out)
[ocz vertex 3, 120 gb ssd ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227706")
[seagate 2 TB barracuda hd 64mb cache, 7200 rpm]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148910&Tpk=stbd2000101")
[evga geforce gtx550ti graphics card(1024 mb)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814130625")
[ocz xsteam-pro 700w power supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817341018")
The DVD/CD burner is a generic oem model


All the hard drives are on sata 3. FWIW Linux Mint also hangs very early on.

Any suggestions?

---

### Post by darkod on 2012-07-19
Don't use wubi. It only installs virtual inside windows which is not really a dual boot. And it has more chance to break sometimes. Also, you will need to remember not to use tutorials written with dual boot ubuntu in mind, because wubi is different.

One possibility is that you have issues with the video drivers with nvidia. You usually need to use the nomodeset parameter.

You have more details here, have in mind it's written for proper ubuntu:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

