---
title: "Installing as if on USB"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by Cosmic1 on 2010-08-25
Hey,

I have a usb drive which can sore about 300 GB. I want to install Ubuntu on it just like if it were on a USB stick. However, it is shown under "My Computer" in windows under hard disk drives. When I use the USB installation program for windows the selection box to select the USB only shows A:\, when I want to install Ubuntu on H:\

Is there any way I can do the very same as I would do for a USB drive on this 300 GB drive? 

Thanks in advance. 

P.S. I want to make it so when I plug in the drive into my computer then it loads Ubuntu on the drive and if I don't then it loads windows. Am I doing the right thing to do that?

---

### Post by GenBattle on 2010-08-25
I'm assuming you're using unetbootin ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)) to write the image? It has a checkbox in the bottom left corner to show all drives. It does advise caution though, as you could accidentally overwrite your main drive if you don't select the right drive (this is why they limit you to USB sticks in the first place).

---

### Post by oldfred on 2010-08-25
The standard USB installer is just that. It is more like a liveCD but there are ways to save some data with a USB where with a liveCD you cannot.

If you have a full drive you will want to do a full install. As part of the install is an advanced button that lets you decide where to install grub2 and you definitely want to install it to the external drive.
[http://members.iinet.net/~herman546/p28/032_install-now.png](http://members.iinet.net/~herman546/p28/032_install-now.png)

An external drive is just another second drive so this is a useful howto:
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Cosmic1 on 2010-08-25
@GenBattle: [http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe)

I was using that 

I guess you recommend I use the one you linked me to instead then?

@oldfred: How do I get to the install dialog on my windows XP computer/

---

### Post by GenBattle on 2010-08-25
unetbootin will give you a checkbox which will let you turn any drive into a "live CD". If you plan on using it for regularly working off, i would recommend doing a full install to the drive as per oldfred's suggestion. Note that running from an external drive via USB will be a fair bit slower than booting off an internal hard disk.

---

### Post by oldfred on 2010-08-25
You do not get the installer from windows. You have to boot a liveCD or a USB that you have copied the liveCD to:

Also has link to USB Flash drive instructions:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

