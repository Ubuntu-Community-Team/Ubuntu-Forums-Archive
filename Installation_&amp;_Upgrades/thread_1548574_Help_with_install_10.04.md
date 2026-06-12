---
title: "Help with install 10.04"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Alm3ga on 2010-08-08
I downloaded the Ubuntu 10.04 Desktop Edition .iso, and after I extracted the .rar to a folder, I ran the wubi.exe. This brought up a window that said you are about to install Ubuntu 10.04 and it gives me the option to install on my C: drive, I'm running Windows Vista 32 bit by the way, if I install it will it let me dual boot? or is this going to make it so I can only boot Ubuntu 10.04? I'm also new to Ubuntu so lots of help would be appreciated :)

-Alm

---

### Post by Rubi1200 on 2010-08-08
> **Alm3ga said:**
> I downloaded the Ubuntu 10.04 Desktop Edition .iso, and after I extracted the .rar to a folder, I ran the wubi.exe. This brought up a window that said you are about to install Ubuntu 10.04 and it gives me the option to install on my C: drive, I'm running Windows Vista 32 bit by the way, if I install it will it let me dual boot? or is this going to make it so I can only boot Ubuntu 10.04? I'm also new to Ubuntu so lots of help would be appreciated :)

-Alm
If you choose to install using Wubi it will create a virtual drive **within** Windows that acts **as if** it is a separate Ubuntu partition.

You will then be able to boot both Windows and Ubuntu, with the option given between the two when the computer starts.

Be aware that Wubi is really only intended as a way of trying Ubuntu and is not meant to be a replacement for a regular installation to the hard-drive.

See here:

[http://wubi-installer.org/](http://wubi-installer.org/)

and here

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

for more information.

---

### Post by phillw on 2010-08-08
> **Alm3ga said:**
> I downloaded the Ubuntu 10.04 Desktop Edition .iso, and after I extracted the .rar to a folder, I ran the wubi.exe. This brought up a window that said you are about to install Ubuntu 10.04 and it gives me the option to install on my C: drive, I'm running Windows Vista 32 bit by the way, if I install it will it let me dual boot? or is this going to make it so I can only boot Ubuntu 10.04? I'm also new to Ubuntu so lots of help would be appreciated :)

-Alm

Hi, and welcome to the forum area.

Wubi installs itself within the Windows area. It gets quite technical, but basically makes a little area for itself. Wubi can be removed as a programme from the Windows "add and remove programmes"

[All about Wubi](https://wiki.ubuntu.com/WubiGuide) does what it says:-)

Regards,

Phill.

/edit Thanks Rubi1200 you posted as i was getting the links together :-)

---

### Post by computerfreak4284 on 2010-08-08
I would just burn the iso to a CD and install it via the CD and u can still dual boot via grub.

---

