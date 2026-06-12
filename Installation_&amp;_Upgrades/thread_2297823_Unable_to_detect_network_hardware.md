---
title: "Unable to detect network hardware"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by boyshawn on 2015-10-06
Hi I am facing issue with the installation of the ubuntu server. Will like to get some help from the community. 

**Network issue**
I seemed not to be able to have the installer to detect my network hardware, but there is no issue with the hardware. Pre-installation, I was using Windows and I have no issue surfing the internet with it. There error message is 
!! Configure the network
Your network is probably not using the DHCP protocol. Alternatively, he DHCP server may be slow or some network hardware is not working properly. 
[ATTACH=CONFIG]264838[/ATTACH]

**Mirror issue**
The installation ask me to select the mirror. As my installer does not detect any internet connection, I had problem proceed with the installation even when I have selected the closest mirror. 
[ATTACH=CONFIG]264839[/ATTACH]

Information:
O.S: Ubuntu 15.04 Server 64 bit
Install from USB, format with Universal-USB-Installer-1.9.6.1

---

### Post by sandyd on 2015-10-06
Moved to *Installation & Upgrades*

---

### Post by gordintoronto on 2015-10-08
Download Ubuntu Server instead of the Network Installer.

By the way, support for 15.04 will end in January. We're just days away from 15.10, which will be supported until the next LTS version.

---

### Post by boyshawn on 2015-10-10
Hi 

I have already downloaded the full version of Ubuntu Server with the following [link]("http://mirror.nus.edu.sg/ubuntu-ISO/15.04/ubuntu-15.04-server-amd64.iso").However, there is still the requirement to use ask for closest mirror. May I know if there is there an issue with the USB installer? I am using Pen Drive Linux to load my image onto the USB.

---

### Post by gordintoronto on 2015-10-10
In my experience, Pen Drive Linux works very well.

During installation, did they ask if you wanted to install updates? I'm almost certain that I have installed Server without an Internet connection, but it probably wasn't 15.04.

---

### Post by cariboo on 2015-10-10
What type of network interface are you using? Wired or wireless?

---

