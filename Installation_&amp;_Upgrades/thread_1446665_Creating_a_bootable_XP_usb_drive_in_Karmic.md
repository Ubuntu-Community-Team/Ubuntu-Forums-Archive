---
title: "Creating a bootable XP usb drive in Karmic"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Zombiekiller00 on 2010-04-04
I would like to install Windows XP on my netbook after some annoying issues. I haven't been able to find any solutions to this problem on Linux based systems after hours and hours and hours of surfing the Google. A lot of people say 'well use the usb startup disk creator!' Don't say that in here. It doesn't work. I already wasted about 3 hours on that. Any helpful advice would be greatly appreciated! (I have a 16GB thumb drive and Windows XP sp2)

---

### Post by a.walker on 2010-04-04
> **Zombiekiller00 said:**
> I would like to install Windows XP on my netbook after some annoying issues. I haven't been able to find any solutions to this problem on Linux based systems after hours and hours and hours of surfing the Google. A lot of people say 'well use the usb startup disk creator!' Don't say that in here. It doesn't work. I already wasted about 3 hours on that. Any helpful advice would be greatly appreciated! (I have a 16GB thumb drive and Windows XP sp2)

Okay, this is an Ubuntu forum but I've suffered through enough of XP to give you the following advice:

1) Make sure that you download all the XP drivers for your netbook before you try to install XP. After installing XP your network card, wireless card, video card, and sound card may not work. Place these files on some sort of external media other than the 16GB thumb drive you're going to be installing from.

2) You should probably create the bootable USB disc from a different Windows computer following instructions like [these]("http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html"). I would not try to create it inside linux.

3) If you do not have access to a Windows computer you may have to break down and buy an external USB cd drive.

After you install XP you should install the XP drivers for your  hardware. You may have to do it from safe mode (press F8 repeatedly once the BIOS posts). Once you install XP and get it working you might want to use something like clonezilla to make an image of your working setup and store it somewhere. XP can be a real pain to install and needs to be reinstalled often (at least once a year) in order to keep good performance.  Hope it goes well.

---

### Post by Zombiekiller00 on 2010-04-04
Thank you. I'll try the guide you linked to. I do have access to a machine running XP (even though it's quite slow) and if that doesn't work I'll just give in and do number three.

---

