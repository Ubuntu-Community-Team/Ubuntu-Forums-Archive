---
title: "Upgrade from Jaunty to Lucid"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by maljaros on 2010-03-21
It seems that one should not (cannot?) upgrade from 9.04 Jaunty to 10.04 Lucid without first upgrading to 9.10 Karma.  This seems messy and I am thinking of rather clearing out the Jaunty partition and loading Lucid from scratch. Is this a bad idea? In addition to copying and backing up my /home directory are there other precautions I should take before doing this?  Perhaps you can point me to a Wiki on this topic.
Thanks for suggestions, MalJaros

---

### Post by mikewhatever on 2010-03-21
If Lucid is your goal, why install Karmic at all? Wait another month (the RC is due on April 22) and install Lucid instead.

---

### Post by maljaros on 2010-03-21
Sorry Mike.  That was a typing error in my query, which has now been corrected.  
I don't intend to load Karma at all.  Apparently the Lucid Beta is stable and not expected to change much before the official release so I want to load it over my Jaunty install.
With apology from MalJaros

---

### Post by phillw on 2010-03-21
> **maljaros said:**
> It seems that one should not (cannot?) upgrade from 9.04 Jaunty to 10.04 Lucid without first upgrading to 9.10 Karma.  This seems messy and I am thinking of rather clearing out the Jaunty partition and loading Lucid from scratch. Is this a bad idea? In addition to copying and backing up my /home directory are there other precautions I should take before doing this?  Perhaps you can point me to a Wiki on this topic.
Thanks for suggestions, MalJaros

Hi, as pointed out, for you, it's most likely going to be easier & less messy to go 9.04 --> 10.04 via a re-install. While you're waiting for 10.04 to launch (End of April), hive off your home directory so that you keep all your 'stuff' like pictures / music / bookmarks etc. That way you can erase the partition with 9.04 on, without touching your /home area.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Also, an important note. The new default filesystem is ext4, the grub on systems before 9.04 may well not be able to access ext4. So, if you're thinking of hiving off your /home upgrade to grub2. Grub2 (Now simply referred to as grub, with the 'old' grub referred to as grub-legacy) will happily work on older releases of Ubuntu. There's a nice How To over here --> [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)


Regards,

Phill.

---

### Post by maljaros on 2010-03-22
> **phillw said:**
> Hi, as pointed out, for you, it's most likely going to be easier & less messy to go 9.04 --> 10.04 via a re-install. While you're waiting for 10.04 to launch (End of April), hive off your home directory so that you keep all your 'stuff' like pictures / music / bookmarks etc. That way you can erase the partition with 9.04 on, without touching your /home area.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Regards,

Phill.

Thanks Phillw.  Between your very informative link and some advice I got from [https://answers.launchpad.net/ubuntu/+question/105061](https://answers.launchpad.net/ubuntu/+question/105061) I feel much more confident about going forward with this upgrade.

---

### Post by phillw on 2010-03-22
I'm going to revise my posting concerning /home. It dawned on me that 9.04 is running grub-legacy. If you make your new /home as ext4 grub-legacy will likely not be able to use it.

So, before you go hiving stuff off, upgrade grub legacy to grub2. Grub2 will happily work with 9.04 and older releases, there's a nice How-To over here --> [https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

Regards,

Phill.

---

