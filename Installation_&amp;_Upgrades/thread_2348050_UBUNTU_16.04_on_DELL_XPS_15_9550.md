---
title: "UBUNTU 16.04 on DELL XPS 15 9550"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by fdanai on 2016-12-31
I'm using a brand new DELL XPS15 9550 laptop, with preinstalled WIN10 Home, I7, 8GB RAM, USB3.0 only and **256GB SSD type: PC300 NVMe SK hynix-SMSNG PM951**.
I'd like to install alongside WIN10 the UBUNTU 16.04 using a properly made bootable UBUNTU 16.04 USB stick.
Using this USB stick I can boot and run the **live **version of UBUNTU 16.04 on RAM, but when I'm trying to install UBUNTU on this laptop **I can't see the internal SSD at all **and I can't install UBUNTU any further... :(
Any advice to resolve this problem, please??
Is latest UBUNTU 16.10 maybe solving this problem??

---

### Post by Bucky Ball on 2016-12-31
You probably have Windows in hibernate. Try switching that off and you should be able to access the SSD.

---

### Post by lisati on 2016-12-31
*Thread moved to **Installation & Upgrades**.*

---

### Post by fdanai on 2016-12-31
Hi Bucky Ball, thanks for reply.
I set both (battery and mains) hibernate power settings to NEVER, but **I ****still **[B]can't  see the internal SSD...
HNY 2017 [/B]

---

### Post by coffeecat on 2016-12-31
> **fdanai said:**
> 
I set both (battery and mains) hibernate power settings to NEVER, but **I ****still **can't  see the internal SSD...


That won't be enough. Unless you disable fast startup in Windows you are, in effect, still hibernating the machine when you shut down. Here's how you disable fast startup in Windows 10:

[https://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](https://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

After you have followed all those steps, shutdown the machine. Don't reboot. You need to shutdown properly and then do a cold boot from the live Ubuntu USB stick.

---

### Post by oldfred on 2017-01-01
Lots of threads on your model Dell.
Is system in RAID or AHCI?

 Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241) 
   XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960) 
   Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by fdanai on 2017-01-01
HNY coffeecat and thanks for advice.
I **followed all directions **on link indicated by you above to disable fast startup and I did so successfully, but unfortunately I **still can't see the internal SSD **to install UBUNTU either 16.04 or 16.10...

---

### Post by fdanai on 2017-01-01
HNY 2017 oldfred and thanks for indicating related links.
My WIN10 DELL XPS15 9550 laptop came with BIOS>SATA Operation>**RAID On> button checked**.
When changing it to AHCI, a very scary attention note appear indicating that even **WIN10 reinstallation could be needed **after such change!! 
So, I'm still sceptical to try this BIOS change...
Any advice oldfred, please??

---

### Post by oldfred on 2017-01-01
Do not know what issues are, some discussion by users in this link I posted above.
XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/commen...install_guide/]("https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/")

---

### Post by fdanai on 2017-01-01
Thanks again oldfred

---

