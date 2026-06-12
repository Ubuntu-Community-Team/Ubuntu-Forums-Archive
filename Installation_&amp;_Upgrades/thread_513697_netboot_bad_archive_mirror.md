---
title: "netboot: bad archive mirror"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by flexus on 2007-07-30
Hello everybody. I am trying to install xubuntu on my toshiba portege 3440CT via netboot. I am pretty sure I set up the network environment and the host computer correctly. I used [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot") guide.

I have managed to boot the laptop with netboot. I am also sure that the DHCP works as is should since I have an old windows installation on the laptop that gets an IP and is able to acces the internet when booted. 

The problem is when I choose the archive mirror it says bad archive mirror no matter which mirror I choose. 

Anyone out there who has a solution? The question has been asked a few times by others, but without posted solutions. Hence the post. 

Thank you very much in advance. I am new to Linux and Ubuntu so please bear with me..

---

### Post by kerry_s on 2007-07-30
just connect the laptop straight to the internet.
this guide is better> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
make sure you have the right image> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by flexus on 2007-07-31
Hi and thanks for responding!

I could not find any topic about installing via netboot on the site you recommended. Downloading an image is not going to do it I think because I have no cd drive for the laptop. Or do you mean that I should download an image to my winows computer and boot via netboot to somehow acces that image? 

thank you
k

---

### Post by pxwpxw on 2007-08-01
Try the Netinstall link in my signature for an outline of the procedure, ask if you have any queries.

---

### Post by kerry_s on 2007-08-01
> **flexus said:**
> Hi and thanks for responding!

I could not find any topic about installing via netboot on the site you recommended. Downloading an image is not going to do it I think because I have no cd drive for the laptop. Or do you mean that I should download an image to my winows computer and boot via netboot to somehow acces that image? 

thank you
k

my bag, you didn't say you didn't have a cdrom. so in that case the guide you are following is the right 1. i would just pull the hd and borrow a laptop with a cdrom drive to do the install, than move it back.

---

### Post by RUSHER on 2008-01-16
I'm gonna revive this dead thread because I have the same problem and no matter how much googling/forum searching I do I can't find a resolution. So does someone know why this is happening? Drivers, settings, crappy computers :p

~nick

---

### Post by Shrek X on 2008-02-07
I found this guide to be the best for setting up the TXE server

[http://home.allegiance.tv/~joem298/](http://home.allegiance.tv/~joem298/)

Then following this to setup the download files...

[http://ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot](http://ubuntuforums.org/showthread.php?t=327597&highlight=windows+install+netboot)


however, I am still having issues connecting to the correct mirror.  I start the install process, but it fails after the proxy information screen saying the archive mirror is not available or does not have a valid release file on it.  Try a different mirror.  


Anyone give us some wisdom?  :)

---

### Post by thechad8 on 2008-02-17
bump
I'm having the same problem.  :confused::confused::confused:

---

### Post by thechad8 on 2008-02-17
scratch that.  the US server is working now.

---

### Post by .maq on 2008-04-14
I seem to be having same problem.
No matter which mirror i try i get Bad archive mirror message. Even tho it seems like internet connection is working

And i got it working.
It seems i had to disable tftpd server and turn my router's DHCP back on... pity it wasn't mentioned anywhere (or i'm just blind? )

---

