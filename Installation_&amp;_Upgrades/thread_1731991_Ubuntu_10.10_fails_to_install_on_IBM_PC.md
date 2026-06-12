---
title: "Ubuntu 10.10 fails to install on IBM PC"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by sqaeng on 2011-04-17
Ubuntu Desktop 10.10 installer crashes using the "Install Ubuntu" option to install from CD onto IBM Aptiva 2139-E5D PC. Crash message preceded by several occurrences of error message "Warning! Error fsyncing/closing /dev/sda: Input/output error". (PC has IDE drive but Ubuntu uses SDSI device label?)
 
The "Try Ubuntu" option boots and operates without incident from the same CD on the same PC .
 
During the startup for both options, the same error message occurs: "[126.012xxxxx] piix4_smbas 0000:00:07.3: IBM system detected: this module may corrupt your serial eeprom: Refusing to load module! ISO 9660 Extensions: RIP_1991A0xa0".
 
I'm unable to access the /var/log/syslog and /var/log/partman files that were requested in the Installer Crash dialog box.

---

### Post by mörgæs on 2011-04-18
This is an older machine. Please give the specifications, especially how much memory it has.

---

### Post by sqaeng on 2011-04-18
> **mörgæs said:**
> This is an older machine. Please give the specifications, especially how much memory it has.
 
Thank you for responding.
 
The PC is about 14 years old, has a Pentium II 400 MHz processor, and 384 MB RAM which is the maximum supported by this hardware model. The BIOS Version is V66EN2M, dated 10/12/98, which I believe is the latest available.
 
I had hoped to devote this PC for experimenting with Ubuntu. Because the CD-resident option of Unbuntu 10.10 runs quite well on this PC, I expected the same with the disk-resident option. Don't both options require the same hardware resources, with the exception of the hard disk space?

---

### Post by mathgeek2000 on 2011-04-18
> **sqaeng said:**
> Thank you for responding.
 
The PC is about 14 years old, has a Pentium II 400 MHz processor, and 384 MB RAM which is the maximum supported by this hardware model. The BIOS Version is V66EN2M, dated 10/12/98, which I believe is the latest available.
 

You may want to try 'lubuntu' a lightweight version of Ubuntu, without the Gnome Shell:

> lubuntu  is targeted at "normal" PC users running on  low-spec hardware. Improvements of the latest lubuntu version include  autologin support in ubiquity,  support of install only mode in  ubiquity, support for lubuntu-restricted  package in ubiquity. lubuntu  10.10 comes with a completely new theme by Rafael Laguna. Lxpanel now  supports Ubuntu indicators applets. Added applications and tools are  Update-notifier, to get notification for available updates, Xpad, to  create quick notes and Ace-of-penguins, to provide some games.  Parcellite, which is not maintained upstream, was removed and  Pyneighborhood was replaced by gvfs support of pcmanfm. LXtask replaces  Xfce4-taskmanager for tasks monitoring. Evince is now used for reading  PDF. During new installations a slideshow now describes features of the   system.
 

Minimum  requirements for lubuntu are comparable to  Pentium II or Celeron  systems with a 128 Mb RAM configuration, which  may yield a slow yet  usable system with lubuntu.


homepage:

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by mörgæs on 2011-04-18
If you are satisfied with the speed of a live Ubuntu on this machine, you will be chanting when you get Lubuntu installed :-)
Remember to have wired internet access while installing. 

You could also try this:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by sqaeng on 2011-04-19
Thank you all for your time and guidance.
 
I'd much prefer to try the full Gnome Shell version than the Ubuntu Minimal CD or ubuntu versions, if possible. And according to the manual you referenced, "Getting Started with Ubuntu 10.04", it should be.
 
The manual states that if my PC permits operating Ubuntu 10 from the Live CD, it should support it installed on the HD. The PC does allow operating in Live CD mode, with no error messages (except for refusing to load one module at boot time), with full hardware including graphic and network support, and at a very tolerable response speed.
 
Any suggestions why installation on HD fails?

---

### Post by Dutch70 on 2011-04-19
This happens often with 10.10 on older hardware, something to do with the installer. Doesn't happen quite as often on 10.04. 

Have you tried the alternate cd install? 

If it doesn't work out for you, I suggest Xubuntu before Lubuntu, but they're both very nice.

---

### Post by sqaeng on 2011-04-21
> **Dutch70 said:**
> This happens often with 10.10 on older hardware, something to do with the installer. Doesn't happen quite as often on 10.04. 
 
Have you tried the alternate cd install? 
 
If it doesn't work out for you, I suggest Xubuntu before Lubuntu, but they're both very nice.
 
Thank you, Dutch70. I will try your suggestions in the order you gave them, and report back with the results. (This may take me a few days)

---

