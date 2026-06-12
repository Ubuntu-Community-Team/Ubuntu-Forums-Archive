---
title: "flash for linux installation"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by aeby on 2007-04-11
Hi,

I am trying to install flash for linux, i have already downloaded it from [http://linux.softpedia.com/get/Multimedia/Graphics/Flash-for-Linux-407.shtml](http://linux.softpedia.com/get/Multimedia/Graphics/Flash-for-Linux-407.shtml)
Can anyone please tell me how to install it. Is there any other links for installing flash application on ubuntu, if so please can you provide me with the links and how to install it.

Thanks in advance

---

### Post by taurus on 2007-04-11
Looks like you need to unpack it and then build it!

---

### Post by justsee on 2007-04-11
If you're only after the Flash player, then Adobe now has a linux version: [http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

If you're after an equivalent of the Flash IDE, then you can actually run the Flash 9 alpha under WINE and it seems to work okay. Download [http://labs.adobe.com/technologies/flash9as3preview/](http://labs.adobe.com/technologies/flash9as3preview/) and install wine: sudo apt-get wine then you should be able to install and run the flash 9 IDE.

However for best performance you probably should try out the free VMWARE server, which allows you to install and run windows within Linux. Once you've set that up you can boot into a windows session and install the Flash IDE. Performance is really good enough that this is what I do professionally at work.

Hope this helps.

cheers,
justin.

---

### Post by aysiu on 2007-04-11
It's not the Flash *player*. It's the Flash *maker*.

---

### Post by FrostyFlames on 2007-04-11
Search Synaptic for "flash", you should get 2 options the mozilla version, and the non-free version. Install either one. I know the non-free version works like a champ.

Edit: Bleh, ok nvm. You're trying to get the actual program that makes the flash stuff. Ignore this I guess. (wish I knew how to delete)

---

### Post by aysiu on 2007-04-11
> **FrostyFlames said:**
> Search Synaptic for "flash", you should get 2 options the mozilla version, and the non-free version. Install either one. I know the non-free version works like a champ.

Edit: Bleh, ok nvm. You're trying to get the actual program that makes stuff working. Ignore this I guess. (wish I knew how to delete)
This is the Flash *maker*, not the Flash *player*.

A little old, but it may still work:
[HOWTO: Install F4L](http://ubuntuforums.org/showthread.php?t=69156&highlight=f4l)

---

### Post by justsee on 2007-04-11
ayishu if you read my post half of it is devoted to running Flash IDE on Linux

---

### Post by mech7 on 2007-04-15
There is an explanation on WINE which works for me on feisty :D


[[IMG]http://img361.imageshack.us/img361/4425/screenshot1vs1.th.png[/IMG]](http://img361.imageshack.us/my.php?image=screenshot1vs1.png)

[http://bkcreation.info/Blog_Macromedia8OnWine.html](http://bkcreation.info/Blog_Macromedia8OnWine.html)

---

