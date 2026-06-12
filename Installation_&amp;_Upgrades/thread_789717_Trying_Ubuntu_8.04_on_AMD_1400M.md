---
title: "Trying Ubuntu 8.04 on AMD 1400M"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Linux_oid on 2008-05-10
**Ubuntu:** ubuntu-8.04-desktop-i386

**System:** AMD 1400M processor; 256M RAM; wireless PCI adapter (D-Link's WDA-1320); NVIDIA GeForce FX5200, 128M, PCI video card.

I couldn't install 7.10 on any of my old boxes.
 
8.04 did go easy on this box. The installer looked like one from previous release. It did recognize Mandriva 2008.1 on one partition and "another linux" (Puppy 3.01) on another one. It didn't ask question about where and how to install GRUB. Existing GRUB was replaced with ubuntu's one and Puppy's got unaccessable. 

Configured wireless adapter started working after reboot. It did happen before so

Networking doesn't work immediately. You have to reboot after manual configuration.

Now the funny staff

[I]sudo gedit /boot/grub/menu.lst 
sudo: unable to resolve host AMD1400 

gksudo gedit /etc/hosts 

Failed to run gedit '/etc/hosts' as user root. 
 
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

gksu gedit /etc/hosts

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/I]

After reboot I have bigger problem: Ubuntu doesn't work.

Just below is a limited list of screen messages

[I]chown: invalid group 'root:tty'
chown: invalid group 'adm'
chown: invalid group 'poolkituser:polkituser
FATA: error inserting battery: [...]
chown: invalid group 'syslog:admin'[/I]  
(repeated 13 times and finally got [OK])
       [I] *Doing Wacom setup                     [OK] 
        *Staring kernel log deamon           [OK]
chown: invalid group 'klog:klog'[/I]
Sometimes after this message I had 
"The GDM group 'adm' doesn't exist. Please correct GDD configuration and restart GDM". 

Pressing 'Enter' logged me in to console mode.

---

### Post by Pumalite on 2008-05-10
Better try Xubuntu Alternate CD.

---

### Post by Linux_oid on 2008-05-10
I'd be better installing Ubuntu and xubuntu-desktop after that.

Anyway, *SAM linux* and *Vector* are my choices for Xfce distros.

---

### Post by Pumalite on 2008-05-10
Mint is pretty good too.

---

