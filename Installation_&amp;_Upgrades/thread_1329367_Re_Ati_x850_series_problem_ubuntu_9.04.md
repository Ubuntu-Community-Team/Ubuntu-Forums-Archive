---
title: "Re: Ati x850 series problem ubuntu 9.04"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Biosteel on 2009-11-17
Hello im a neewbie at ubuntu but really want to learn. I've been sitting with this operating system for 2 years. and now i've found a problem that i cant solve myself thats why i turn myself into the pro's.


I cant install the driver for my graphics card (ati radeon x850 series).

when im looking in hardware drivers there are nothing there to enable. and i have allready tried Envy and that made me loose my GUI so i did an reinstall. 

so what do you guys think about this ?:o

---

### Post by Biosteel on 2009-11-17
> **Biosteel said:**
> Hello im a neewbie at ubuntu but really want to learn. I've been sitting with this operating system for 2 years. and now i've found a problem that i cant solve myself thats why i turn myself into the pro's.


I cant install the driver for my graphics card (ati radeon x850 series).

when im looking in hardware drivers there are nothing there to enable. and i have allready tried Envy and that made me loose my GUI so i did an reinstall. 

so what do you guys think about this ?:o

quoting myself. no one has an idea ??;)

---

### Post by sylentdogg on 2009-11-17
Your card is not supported by the proprietary driver any more.  :(  All the x series cards are only supported with the open source driver now.  The open source driver does support 3d effects with most of the older Ati cards. It should be the driver you are currently running. There is also the radeonhd driver, but some features aren't finished yet. You can find that on [Launchpad]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd").

---

### Post by Biosteel on 2009-11-17
> **sylentdogg said:**
> Your card is not supported by the proprietary driver any more.  :(  All the x series cards are only supported with the open source driver now.  The open source driver does support 3d effects with most of the older Ati cards. It should be the driver you are currently running. There is also the radeonhd driver, but some features aren't finished yet. You can find that on [Launchpad]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-radeonhd").

i've seen that to over the internet but how do i do an install wich provides me to use the desktop effects. im kind of loosing the mood right now. I've never ever had this kind of problem. because i used the drivers in envy once installed it and so on. and on reboot my GUI dissaperd so i had to reinstall the whole computer. Could you share some information about what i should do and the most easy way to install it ?.:popcorn:

---

### Post by sylentdogg on 2009-11-17
The open source driver is installed by default when you install ubuntu. So you don't have to install anything. It should work out of the box. I'm using it right now with an x1550 and compiz works on it. All you should have to do is enable desktop effects and it should work.

---

### Post by Mark Phelps on 2009-11-17
While envy was a great tool in the past (I used it several times!), it won't do you any good with 9.04 or newer Ubuntus, because as already said, there are no ATI restricted drivers that will work with your card and the newer Ubuntus.

Just wanted you to know that using Envy now is only going to make your problem worse, not solve it.

---

