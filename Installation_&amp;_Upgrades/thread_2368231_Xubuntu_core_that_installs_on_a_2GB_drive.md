---
title: "Xubuntu core that installs on a 2GB drive?"
date: 2017-08-08
forum: Installation &amp; Upgrades
---

### Post by v47 on 2017-08-08
I'm looking for some ubuntu version that would be small enough to install on a 2GB drive - tried Xubuntu core 17.04 (xubuntu-17.04-core-i386.iso), but it needs 2.2Gb, wanted to try 16.04 (xubuntu-16.04-core-i386.iso), but couldn't find a valid download anywhere.

Suggestions? Thank you.

---

### Post by texpat on 2017-08-08
You may find something here: [https://xubuntu.en.uptodown.com/ubuntu/old](https://xubuntu.en.uptodown.com/ubuntu/old)

If it does not necessarily have to be Ubuntu, you could go for something like Puppy Linux ([http://www.puppylinux.com/](http://www.puppylinux.com/)) which claims to be "extraordinarily small" (<200MB)

Good Luck
Tx

---

### Post by v47 on 2017-08-08
Puppy is not going to cut it, doesn't seem like it's possible to get Firefox and youtube working - that's basically all I need. So yeah, looking for an ubuntu version that has a regular UI and Firefox, and is small enough to fit on a 2GB hdd. Atom based CPU and 4GB ram, so no problems in other departments.

---

### Post by sudodus on 2017-08-08
***What 2 GB drive is it - a USB pendrive, a memory card, or a small internal drive?***

I would say that 2 GB is really too small for a full size installed linux operating system. See this link:

[Installation/FromUSBStick#Notes_about_size](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_size)

***General tips:***

You can install a Lubuntu or Xubuntu *live* system, or better yet, a* persistent live* system, where approximately 1 GB will be used for the image of the iso file. The remaining drive space can be used for a casper-rw partition to store data (and some drive space will also be used for some 'infrastructure').

Another alternative is to install a super light system from the Ubuntu mini.iso file (or Ubuntu Server iso file), boot into the system and after that install only the most necessary program packages, for example not a full desktop environment, but only a window manager, for example Fluxbox, xinit, xterm and a light-weight web browser (instead of Firefox) plus the necessary multimedia program packages to play youtube video-clips.

-o-

An alternative might be to boot from a separate live-only DVD or USB drive with Lubuntu or Xubuntu and have a casper-rw file or partition on this 2 GB drive.

---

### Post by oldos2er on 2017-08-08
Server + a wm? Haven't checked sizes though.

---

### Post by v47 on 2017-08-08
persistent live system sound like something that might do - any step-by-step guide?

---

### Post by sudodus on 2017-08-08
If you want a persistent live system in one single drive, this 2 GB drive, you can try mkusb according to this link (and links from it),

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

and more spefically the following link,

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Install mkusb and it does the job pretty much automatically for you.

-o-

If you want a persistent live system in two drives, the image of the iso file in one drive and the persistence in the other drive, there are tips at the following link,

[Simple Persistence](https://help.ubuntu.com/community/mkusb/sp)

---

### Post by v47 on 2017-08-08
ok, I'll try that soon, in the meantime, any chance someone would have xubuntu-16.04-core-i386.iso somewhere? I believe that is what I'm looking for.

---

### Post by oldos2er on 2017-08-08
It's available as a deb file from [https://packages.ubuntu.com/xenial/i386/xubuntu-core/download](https://packages.ubuntu.com/xenial/i386/xubuntu-core/download)

---

### Post by v47 on 2017-08-09
ok, looks like persistent live is the only way to go. checked the links, but it's a bit too much for me to handle I'm afraid - simplified instructions would be much appreciated. so I've got a bootable usb thumb drive with xubuntu 16.04, the iso is on it as well, the target drive is the 2GB ide flash in the computer. what do I do next? boot into xubuntu live, load mkusb? software center doesn't seem to work in livecd mode.


//ok, some tweaks might be needed, but Debian9 core plus Xfce does fit, so I'l be going with that.

---

### Post by sudodus on 2017-08-10
Which way do you want to go:

**1. a persistent live system in one single drive, this 2 GB drive?**

**2. a persistent live system in two drives, the image of the iso file in one drive and the persistence in the other drive?**

*. **How big is the usb thumb drive**, how many GB memory? (An alternative might be to have a persistent live system in the usb thumb drive or i combination of the two methods in order take advantage of the available drive space.)

-o-

**Details about alternative 1:**

There is a quick start manual for mkusb at these links (try the second link, if the first link does not work),

[mkUSB-quick-start-manual.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

[alternate link to mkUSB-quick-start-manual.pdf](https://help.ubuntu.com/community/mkusb?action=AttachFile&do=view&target=mkUSB-quick-start-manual-12.pdf)

**Details about alternative 2:**

Don't forget the following link,

[Simple persistence](https://help.ubuntu.com/community/mkusb/sp)

-o-

**How to install mkusb into an Ubuntu family operating system**

The method works in installed systems as well as live-only and persistent live systems:

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

---

