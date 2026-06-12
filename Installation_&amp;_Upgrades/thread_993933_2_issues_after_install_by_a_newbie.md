---
title: "2 issues after install by a newbie"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by LudoMo on 2008-11-26
Hi, I have decided to come and join this great community by trying the latest install of UBUNTU 8.10  Have installed inside my XP-Pro-setup via WUBI. Most of it works fine, but I have 2 issues which stop me form continuing at the moment. Have checked the web and forums and tried a couple of things, but still no luck.
Issues:
1) my wireless network connection doesn't work. I have a ATMEL Corp MiniUSB FASTVnet (AR) adapter. Have connected via cable and downloaded all updates, also tried to install the "Windows .inf file" for my adapter with ndisgtk, but it comes back with "Invalid driver".
2) I cannot mount CDs, not even the one I used with the UBUNTU image, they keep trying and in the end give up telling "unable to mount".

Hope someone can help as I would really like to explore UBUNTU further and have the time for a while !

One more thing I noticed (though not sure if relevant): during install from DvD the full installation package was downloaded from Web again, though it should be on the disc, in my opinion....

Cheers.

---

### Post by TFX360 on 2008-11-26
Wireless can give you a hard time. Your card doesn't seem to be supported. I would try googling for ndiswrapper.

To mount CD/DVD-ROM:

```
sudo mount /media/cdrom0/ -o unhide
```

To unmount CD/DVD-ROM:

```
sudo umount /media/cdrom0/
```

---

