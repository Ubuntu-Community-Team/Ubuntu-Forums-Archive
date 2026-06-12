---
title: "windowss drivers in ubuntu for  y5 connection"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by devipriya on 2011-06-25
Gud morning  ,i am new to ubntu,nd i hav lots of doubts regarding ubuntu.


1).My lap is dual boot , i hav y5 connecton for my windows xp,nd im  trying 2 instal windows drivers in ubuntu for y5,for dat i need install ndiswrapper software,afer dat i hav to idedntify da windows drivers in ubuntu9.04, how can i identify?
Plz tel me da step by step procedure to instal windows drivers in ubuntu.

2)Problem wth synaptic packge manager, if i download any package , it shows warning like not authenticated , how  can i solve this?
Some body are telling this is repogitory prob,i changed to  main server and so on , but  no use.


thanks in advance.

---

### Post by varunendra on 2011-06-25
Hi,

Using ndiswrapper is a workaround if the driver doesn't exist for linux. So why don't you try the native method first? That is, linux drivers for your Wifi adapter.

From one of your other posts, I found that the laptop you are talking about is perhaps Samsung R528 (please confirm). Its [specs]("http://bharatlines.com/samsung-r528-specifications-reviews-features-price-in-india/") show that it has a Core i3-350 processor with 2GB DDR3 RAM, which is quite a decent configuration for any modern OS.

Ubuntu 9.04 (if that's you are using as you mentioned) is pretty old now and is no more supported (probably a reason for some of your synaptic problems too). So why don't you try Ubuntu [10.04.2 LTS]("http://releases.ubuntu.com/lucid/")? I'd suggest to use a [torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso.torrent") if you decide to download it.

Being an LTS release, it will be supported till April 2013, has a good chance of having native drivers for your Wifi adapter, and hopefully, would give you no headaches with synaptic :).

If you still want to go ndiswrapper way, we'll try to help here, but frankly, you should have better luck with 10.04.2 LTS.

One more thing:- while in ubuntu, open a terminal, enter the following command and post its output here:
```
lshw -C network
```
This will tell us about your network adapters which may help to determine if they are natively supported in newer ubuntu versions or not.

Sorry for talking about everything except what you originally asked for, but this may be better, I hope.

---

### Post by devipriya on 2011-06-27
Thanks ,ya my laptop is samsung R528.I typed dat commad (which ur send to mi)in terminal,its showing  so many things like network unclaimed ..Defenetly i il upgarde to 10.4.
linux drivers for your Wifi adapter means what?, i hav 2 download adapters na?,i dont know tel me clearly.


Thanks.

---

### Post by varunendra on 2011-06-27
> **devipriya said:**
> linux drivers for your Wifi adapter means what?, i hav 2 download adapters na?,i dont know tel me clearly. By linux drivers I mean that if your network adapters are natively supported in linux, then all you need is to install the latest stable version of ubuntu (10.04.2 LTS), and most probably it will work with those adapters out of box! That's because most of the supported drivers are supplied with the distribution (the Operating System you install), and are automatically picked up during boot-up. No need to force windows drivers with ndiswrapper.

But in order to be able to predict whether or not they are supported, we need to look at the output I requested. After entering the command (lshw -C network) in terminal, select the output with your mouse cursor, copy it and paste in your next post. To make it more readable, select (only) the pasted text, and click the '#' icon located at the top of the box in which you type your post.

But regardless of these issues, I think you should do at least one thing immediately - that is - download the Live CD iso of Ubuntu 10.04.2 LTS from [here]("http://releases.ubuntu.com/lucid/"), burn the image to a CD, and boot your laptop with that CD to see how it works with its hardware. If everything goes well, then you may install it on your laptop without doubts.

[**Note: **Burning iso to a CD is different than burning data to a CD. If you don't know how, this guide will make it easy for you: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) ]

If you are familiar with downloading via torrents, I'd suggest to download via [this torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.2-desktop-i386.iso.torrent").

---

