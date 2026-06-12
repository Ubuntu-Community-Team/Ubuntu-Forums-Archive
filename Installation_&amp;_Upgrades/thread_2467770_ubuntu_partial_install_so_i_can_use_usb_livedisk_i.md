---
title: "ubuntu partial install so i can use usb livedisk iso only"
date: 2021-10-07
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2021-10-07
(1) sorry about grammar 
(2) thanks for help ??

dual operating system (Windows xp) and i`d like to to use Ubuntu 20.04 as second operating system
BUT i`d like to install Ubuntu like how Puppy Linux install`s
with just a small foot print on HD 
So is there a way to do this with Ubuntu
Example
boot Windows normally and boot Ubuntu USB ISO with all of its settings saved permanently on HD ,,. but not the whole Ubuntu Operating system
Thanks for Help

---

### Post by ActionParsnip on 2021-10-07
Do you mean a virtual machine within Windows. You can dual boot Ubuntu and Windows and you choose which OS to bootup when you turn the system on. Puppy Linux is the same. If you have Puppy Linux installed on the system then you can choose to boot Puppy or Windows (I don't suggest you use Windows XP for anything unless you have all networking disabled. It is not secure and will not get any updates from anyone ever)
If you want a small footprint OS based on Ubuntu then you can use the minimal ISO to install a bare bones Ubuntu OS then install something like LXDE
```

sudo apt install lxde

```
You can then  choose your login manager and get a very small punchy OS using minimal resources.

Is this what you mean?

---

### Post by grahammechanical on 2021-10-07
Normally, a Ubuntu ISO image burned to a USB memory stick will lose any configuration changes and data created once Ubuntu is shutdown. The way to prevent this from happening is to create a live Ubuntu USB stick with something called persistence. Of course, you would still get the full Ubuntu distribution with all the default applications.

But you could try it with Ubuntu minimal. I have never tried that. It would make an interesting experiment. You could try and tell us how it goes by opening a thread in the Ubuntu, Linux, and OS chat section of the forum. You will benefit by using MKUSB to create the USB memory stick with Ubuntu minimal on.

[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu minimal gives you options that range from something like a Linux server install to Linux with a desktop of your choice and a few utilities upward to selecting which applications you want.

Regards

---

### Post by jimbean on 2021-10-07
opening a thread in the Ubuntu, Linux, and OS chat section of the forum

---

### Post by jimbean on 2021-10-07
[https://ubuntuforums.org/showthread.php?t=2467770]("https://ubuntuforums.org/showthread.php?t=2467770")
and i`ve got to go now {work
and i did not give enough info on my previous post
I`ve got a core2duo with 2 gig ram and 160 gig hd 32 bit operating system
so its a no go for virtual box and skype and or the other face internet chat programs, not enough machine



And i dont have xp to well connected to the internet {it`s Sandboxed} somewhat ive disabled ethernet for virus`s

---

### Post by grahammechanical on 2021-10-07
The operating system is 32 bit but the CPU might not be. I have a Core2Duo and it is 64 bit. Run this command

```
lscpu | grep mode
```

This is what I get.

> graham@sdb1-sdb8:~$ lscpu | grep mode
CPU op-mode(s):                  32-bit, 64-bit

I have run 32 bit Ubuntu in the past (I only had 1GB RAM) but I now run 64 bit Ubuntu (now have 4GB RAM). With Ram of 2 GB you should not install Ubuntu because it has the Gnome desktop environment. As suggested in the other thread install LXDE desktop environment. 

What do you think of the suggestion to install Ubuntu minimal on the USB stick and during installation specifically choose the desktop environment and applications?

If the CPU turns out to be 32 bit and not 64 bit we will have to think again. 

Regards

---

### Post by poorguy on 2021-10-07
If I may make a suggestion.

LXLE

Based on Ubuntu 18.04.3 and is offered in 32bit.
 It's designed to run on older less powerful computers.
Comes with a lot of usable installed software OOTB.

Have a read.
[https://lxle.net/](https://lxle.net/)

32bit download.
[https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download](https://sourceforge.net/projects/lxle/files/Final/OS/18.04.3-32/lxle-18043-32.iso/download)

---

### Post by QIII on 2021-10-07
You were still seeking assistance, so a chat area was inappropriate.

Threads merged.

---

### Post by sudodus on 2021-10-08
> **grahammechanical said:**
> Normally, a Ubuntu ISO image burned to a USB memory stick will lose any configuration changes and data created once Ubuntu is shutdown. The way to prevent this from happening is to create a live Ubuntu USB stick with something called persistence. Of course, you would still get the full Ubuntu distribution with all the default applications.

But you could try it with Ubuntu minimal. I have never tried that. It would make an interesting experiment. You could try and tell us how it goes by opening a thread in the Ubuntu, Linux, and OS chat section of the forum. You will benefit by using MKUSB to create the USB memory stick with Ubuntu minimal on.

[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Ubuntu minimal gives you options that range from something like a Linux server install to Linux with a desktop of your choice and a few utilities upward to selecting which applications you want.

Regards

[mkusb](https://help.ubuntu.com/community/mkusb) can create **persistent live** drives from Ubuntu Desktop iso files as well as iso files with the [Ubuntu community flavours](https://releases.ubuntu.com/). I would suggest using a flavour with a small footprint for your computer with core2duo: Lubuntu or Xubuntu version 20.04.x LTS.

mkusb can create an installer drive from the **mini.iso** file 'MinimalCD' (but it cannot create a persistent live drive from that iso file). If you go the mini.iso way, you need to make a 'regular' installation into a second USB drive, and it helps a lot, if you can unplug, disconnect or otherwise disable the internal drive of your computer. After the installation you can plug the internal drive in again, and use a temporary menu to select between booting the internal drive and the external drive with Ubuntu. [This link](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312) may help you with the installation (although not quite on the spot). It can also help you **install Lubuntu or Xubuntu (installed like into an internal drive, but in this case into a USB drive)**.

---

### Post by oldfred on 2021-10-08
My 2006 Toshiba laptop is Intel Core2 T5500 with 1.5GB of RAM. It is 64 bit. 
It would not install Ubuntu at all. 
I was able to install Kubuntu which is a mid-weight and it works ok. Lightweight flavors should work well.

Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

---

