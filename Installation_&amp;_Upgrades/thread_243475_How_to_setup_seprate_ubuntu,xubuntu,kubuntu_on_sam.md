---
title: "How to setup seprate ubuntu,xubuntu,kubuntu on same system?"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by orb9220 on 2006-08-25
Do I need to do three seprate installs to three seprate partitions for complete isolated enviroments?

I want to setup so that a bad install of packages or me tweaking and  learning in kde won't mess up my gnome or xfce and vica-versa.

I had gnome and xfce and each of their apps would showup in the menu's, bad form as far as I am concerned. 

I want to be able to even break xserver or logon etc.. and still be able to log into the other two.

Any help is appreciated. I need to make a system of all three with each protected from the other.

---

### Post by awkward1234 on 2006-08-25
> **orb9220 said:**
> Do I need to do three seprate installs to three seprate partitions for complete isolated enviroments?


I would say that that would be the best way to do it, don;t know of any other way, although I am a bit of a newbie, although you could use seperate harddrives for one or more of them. And remember; always back up important data before doing stuff like this!!!

Mark

---

### Post by orb9220 on 2006-08-25
Thanks for the info. And I know about backing up first.

---

### Post by aysiu on 2006-08-25
Sounds as if you need separate partitions for them, then.

---

### Post by orb9220 on 2006-08-25
How would grub end up handling them and should I install the one I want as default last?

---

### Post by aysiu on 2006-08-25
You should install Grub to the MBR on the last one--that's all that matters. It should automatically add the others to the boot menu. It may not label them correctly (I think they'll all be called *Ubuntu*--not Kubuntu, Xubuntu, etc.), but they should be there.

---

### Post by wpshooter on 2006-08-25
If you installed all three of these on one system would it not force you to use logical partitions instead of just primary partitions ?

Isn't there a limit of 3 or 4 primary partitions ?

Thanks.

---

### Post by confused57 on 2006-08-25
I just installed Dapper server using the alternate cd to a partition on my hard drive, in order to dist-upgrade to Edgy...I wanted to experiment with the development process without affecting my main installation.  By using the alternate cd, I chose to install grub onto the root partition(hd0,5) or hda6.
  I then added the entry into my main Dappper menu.lst to boot the partition:

```
title    Edgy Eft
rootnoverify   (hd0,5)
chainloader +1
```

Boots up fine to the menu.lst of "Edgy"...another option, if you want to use the alternate install cd's.

I already had an extended partition containing a logical swap partition, I set up 2 additional partitions to install Edgy and another OS, using the alternate cd, which automatically set them up as logical partitions within the extended partition.

---

### Post by randell6564 on 2006-08-25
> **orb9220 said:**
> How would grub end up handling them and should I install the one I want as default last?

If you have seperate partitions for each OS, then you should be fine. As long as you get grub installed to the MBR.

---

