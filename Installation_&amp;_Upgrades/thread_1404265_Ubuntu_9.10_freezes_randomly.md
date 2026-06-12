---
title: "Ubuntu 9.10 freezes randomly"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by MulitheFinn on 2010-02-11
I know that there are many of this kind of topics here but I haven't found a solution for my problem. So last week I installed Ubuntu 9.10 on my older computer. Before the installation I used Windows Vista and Windows 7 and I decided to do a clean installation. When I ran Ubuntu from DVD it was perfectly healthy and no problems appeared. After the installation there became random freezes. The system freezes but mouse is still moving and can't do anything else than reboot. 

From the other topics I read that it might be a problem with GPU drivers and I heard about this Envy program which might be able to install some drivers but don't know how to install that. :P

The computer is pretty old:

AMD Athlon 64 Processor 3200+
ASUS M2R-FVM (includes integrated ATI Radeon Xpress 1150)
1 GB of RAM
320GB Hard drive 


and I couldn't find any Linux drivers for the graphic card from AMD's internet page. So any suggestions what can be done here? 

Thanks! :)

---

### Post by lidex on 2010-02-11
Try envy. To install use this command in a terminal. "Applications>Accessories>Terminal"
```
sudo apt-get install envyng-gtk
```
Use that install your drivers. If you still have problems have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=853377]("http://ubuntuforums.org/showthread.php?t=853377")

---

