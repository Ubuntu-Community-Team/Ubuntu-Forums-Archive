---
title: "wubug"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by AndreiQC on 2012-09-28
First, i want to say that i'm a very satisfied user of Ubuntu working in a PC using only Linux system. 

But about this wubi software pretending to work inside Windows, i never saw such a buggy software in my entire life.

First, i downloaded wubi and it start to extracted in a directory inside my first windows partition. I reboot and it seems to work. I was able to login, and install some of the software needed by ubuntu. Once this installed software was made, i restart my computer, choosing ubuntu, i had a red screen and nothing else could be done, so from windows i uninstalled ubuntu.  

Secondly, i installed it still with wubi, there were a basic installation process, and i had to reboot and made the installation process with a ubuntu dvd. That's what i did. Everything work fine, but when i clicked, i have a good internet connection, i have the minimum of 4 gig, and when i click on the button to continue the installation, i never been able to install ubuntu, it never went to the second part of the installation. 

I give it a last chance with another dvd, another partition, and it was worst, i lost all my boot loader and i had to recover it from files that i had. 

So is this WUBI is something working or not ? I read so many bad experiences since i tried to make it work. I don't know but Linux mint work like a charm but in my point of view Linux mint is not as serious as ubuntu is, i do prefer Ubuntu. But how a customer who would like to experienced Ubuntu will choose this system if wubi is so unstable. 

Why WUBI is such a mess for a system who work so good in a linux environment ?

---

### Post by AndreiQC on 2012-09-28
Does anyone had a good working wubi ubuntu installation ? If there is no answer i understand that there is something wrong with it. So instead of using wubi can i have a unbuntu partition beside windows ? I mean i have three windows 7 partitions for my working purpose. Is there any way to have a fourth partition who will be a Ext4 partition with a linux swap partition at the end of all my windows?  partitions ?

---

### Post by bcbc on 2012-09-28
Yes create a fourth partition, make it an extended partition, and you can create multiple logicals to install Ubuntu.

Wubi works on win7, but... it sounds like you might have a graphics card issue. If you have a radeon or nvidia try booting with 'nomodeset': [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

