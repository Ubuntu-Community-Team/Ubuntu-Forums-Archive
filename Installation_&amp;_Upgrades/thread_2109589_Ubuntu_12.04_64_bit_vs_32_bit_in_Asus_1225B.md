---
title: "Ubuntu 12.04 64 bit vs 32 bit in Asus 1225B"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by zemega on 2013-01-28
Hi, I have tried 32 bit Ubuntu 12.04 on an Asus EEE PC 1225B, and it worked well for me. I'm wondering wheter I can run the 64 bit version as well. Below is the spec for the laptop/netbook (its pretty borderline). Windows 7 Upgrade Advisor reported everything is okay except for the RAM part. And seeing how the 32 bit version has no problem with RAM usage, I was wondering wheter I can run 64 bit version, and how much RAM will it be using.

AMD® APU E450 1.65GHz (dual core)
AMD® Radeon HD 6320
DDR3, 1 x On Board Memory, 2GB  (not upgradeable)
1 x HDMI


Beside that, I'm also looking into Xubuntu and Lubuntu. Although since Xubuntu uses Ubuntu Software Center 5.4.1.2, I'm more inclined to try Xubuntu instead. Any advice on this? I would only need to run GrADS, Scilab 5.4.0 (6.0 when it has stable release), and Firefox. I'm open to both 32 and 64 bit version.

Seeing how Lubuntu has low RAM usage, I was wondering If I can run Lubuntu inside a virtual PC inside Win 7 instead. How does this idea fare?

This might not be related, but if I used Xubuntu 12.04, would the snap to side function works? like Win 7 and Ubuntu. Even then, the snap didnt really work well with multiple monitors in Ubuntu 12.04.

---

### Post by Pandanus on 2013-01-28
Hello zemega,

regarding 32bit vs 64bit; you have 2GB memory, and 64bit will be of no use to you.
The x-bit determines how much memory you can address: a bit is binary (=two states 1/0), therefore you can assign addresses for 2^x bytes, 2^32 (~4.2 GB) and 2^64 (~18.4mio TB) respectively. If you have RAM below 4 GB you can access all with 32bit, and as long as you have RAM below 18mio TB you are fine with 64bit.

Hope that helps
Pandanus

---

### Post by ibjsb4 on 2013-01-28
> Seeing how Lubuntu has low RAM usage, I was wondering If I can run  Lubuntu inside a virtual PC inside Win 7 instead. How does this idea  fare?Your a bit on the low spec's side of things, but I think you could get away with it with either lubuntu or xubuntu in a VM.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

Think I would go with xubuntu 12.04.  It will run good on 512M of ram.

---

### Post by mastablasta on 2013-01-28
> **Pandanus said:**
> Hello zemega,
 
regarding 32bit vs 64bit; you have 2GB memory, and 64bit will be of no use to you.
The x-bit determines how much memory you can address: a bit is binary (=two states 1/0), therefore you can assign addresses for 2^x bytes, 2^32 (~4.2 GB) and 2^64 (~18.4mio TB) respectively. If you have RAM below 4 GB you can access all with 32bit, and as long as you have RAM below 18mio TB you are fine with 64bit.
 
Hope that helps
Pandanus
 
No, the 64bit is refered to CPU. 32 bit can also address up to 32GB ram. having more ram helps but to use the full power of 64bit CPU you can use 64bit OS on 2GB. 
 
> **zemega said:**
>  
AMD® APU E450 1.65GHz (dual core)
AMD® Radeon HD 6320
DDR3, 1 x On Board Memory, 2GB (not upgradeable)
1 x HDMI
 
Beside that, I'm also looking into Xubuntu and Lubuntu. Although since Xubuntu uses Ubuntu Software Center 5.4.1.2, I'm more inclined to try Xubuntu instead. Any advice on this? I would only need to run GrADS, Scilab 5.4.0 (6.0 when it has stable release), and Firefox. I'm open to both 32 and 64 bit version.

yes it will work quite well actually. i tried Kubuntu (though sitll only live as i need some time to prepare for dual boot - backup, repartitioning...). if necessary i can switch it to netbook plasma which should give an interface better suited to small screen.
 
.> 
 
Seeing how Lubuntu has low RAM usage, I was wondering If I can run Lubuntu inside a virtual PC inside Win 7 instead. How does this idea fare?
 
This might not be related, but if I used Xubuntu 12.04, would the snap to side function works? like Win 7 and Ubuntu. Even then, the snap didnt really work well with multiple monitors in Ubuntu 12.04.
 
 
Lubutnu works fine in vbox on such a cpu. give it 512MB ram and use 32bit version for vbox.
 
don't know about snap function. it does work in Kubuntu. you can use lowfat package to reduce system resources usage in Kubutnu (if necessary).

---

### Post by zemega on 2013-01-28
Thank you everyone, I have a clear idea on what I'm going to do.

---

