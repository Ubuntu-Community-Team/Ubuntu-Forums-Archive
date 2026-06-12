---
title: "Unable to install Adobe Flash or Chromium"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by danny10 on 2013-09-08
Hello everyone, I am new to Ubuntu. New as in I just downloaded and installed it on my Windows 7 64 Bit machine earlier today, and haven't been able to watch much football because I'm really enjoying exploring the new world. HOWEVER, I'm really frustrated with one thing so far. The Ubuntu Software Center looks simple enough and everything I have tried to install has went without a hitch. EXCEPT I cannot install Adobe Flash or Chromium. It will only say, "package dependices cannot be resolved". Like I said I am new to Ubuntu and Linux. I am very computer literate, I just need some help from someone with experience. I have tried Google with no luck. I have tried installing through the Terminal and still can't get any results. I have also tried Synaptic Package Manager to install them and it didn't have any luck. I have Ubuntu 12.04 LTS everything is up to date (at least it says it is) and all have installed is VLC Media Player and the Ubuntu Restricted Extras and the Synaptic Package Manager. Please anyone who enjoys helping noobs, help me out :)

---

### Post by claracc on 2013-09-09
What are the dependencies problems you are finding?, what are the packages involved?

I understand You have installed ubuntu 12.04 dual boot with windows 7, is it correct?.

I would try to install the pepperflash addon instead the old adobe flash player, following the instructions given in this link:

[http://linuxg.net/how-to-install-pepper-flash-for-chromium-on-ubuntu-13-04-12-10-and-12-04-via-ppa/](http://linuxg.net/how-to-install-pepper-flash-for-chromium-on-ubuntu-13-04-12-10-and-12-04-via-ppa/)

---

### Post by danny10 on 2013-09-09
Claracc thank you for replying. Yes I have a dual boot setup. Believe it or not, just about 15 minutes after I posted, a red triangle popped up in the top right hand corner. It said something to the effect of Ubuntu is not updated but it thinks it is. I had already used the update manager several times after installing to make sure it was up to date as I had read this was important. Each time it said it was up to date but finally last night it found 151mb of updates. After they installed and I rebooted flash and chromium installed without any problem, and the overall performance was improved. I don't know why it took 12 hours for it to realize it needed to update, but I'm glad it worked. Can I install pepperflash with flash installed too? Or will this cause conflict? My only other question at this point is regarding additional drivers. I read on the web not to mess with this unless you were an advanced user, I'm not advanced in Linux lol. I noticed Ubuntu doesn't recognize my Laptops onboard Nvidia graphics card. I don't plan on any heavy graphics use but was wondering if this was an easy fix and if I should be afraid of clicking on the addition drivers tool in system. Thanks again for your help. I enjoy learning.

---

### Post by coldraven on 2013-09-09
AFAIK if the Nvidia driver is not mentioned in "Additional Drivers" then your card is only supported by the open source driver that is installed already.
It won't hurt to open "Additional Drivers" and look, you can just exit without changing anything.
You can open "Details" to see which version you have.

---

### Post by claracc on 2013-09-10
Yes, I think you can install pepperflash apart from adobe flash player in chromium, for it, you can use the link I provided or this other link: [http://www.ubuntugeek.com/how-to-install-pepper-flash-for-chromium-web-browser-on-ubuntu-gnulinux.html](http://www.ubuntugeek.com/how-to-install-pepper-flash-for-chromium-web-browser-on-ubuntu-gnulinux.html) I have found.

Then you only have to enable it, for it, you write in the address bar  ```
about: plugins
```, enable pepperflash and disable the adobe flash plugin.

---

