---
title: "Can't boot into bootable usb"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by AmbiguousOutlier on 2013-11-02
Hello, 

I've just built a brand new computer, Celeron 2.6Ghz G1610 LGA1155, Gigabyte H61M-D2H-USB3 and 2Gb of corsair value ram. I'm using the same CPU and ram in another machine running a version of ubuntu.  

The problem I'm having is I can't get the machine to boot into the live usb. I've pulled out HDD and optical drive, so just the CPU and RAM are installed. I've tried 12.04 64 and 32 and 13.04 32 bit. I've also tried the Live usb in another computer and it works first time. 

Every time I boot, I get the man = keyboard icon and I can press enter to bring up the menu at this point, I've tried "Try Ubuntu without installing" and "Install Ubuntu" and I've just let it run without pressing enter. 

I then get a black screen with a flashing cursor, then everything goes black. 

I reboot after a few minutes and about 1 in 20 times, with no changes to hardware or software I'll get the Ubuntu splash screen. Twice it's booted into the desktop but crashes shortly after I click install Ubuntu. 

I've been quick enough on the splash screen to press Alt+enter a couple of times, however the point at which it crashes is always different it's crashes along the starting/stopping services.

Anyone experienced anything similar? This is the 4th dedicated Ubuntu machine I have and I've been installing Ubuntu since Hardy, I've just never has this much difficulty installing before.

---

### Post by heir4c on 2013-11-02
Is it 1 bar of ram or two? When there are two, change them from place. Have you different colours of memory holders for putting the RAM in then use the same colours.
Is the usb a new created or using an old one? When it is new, recreated it again. Maybe there is a error in the usb.
And why you pulling out the HDD? Try it with the HDD in.

---

### Post by AmbiguousOutlier on 2013-11-02
The HDD was the only pre-existing part to this build, so to make sure it wasn't causing the error, I tried it with and without. 

Mobo can take 4 sticks of RAM, however I've only got 1 in the first slot. And the machine wont post with the RAM with any other slot. 

My USB is a few years old however I've only just re-built it using "Startup Disk Creator". I've also tried with a live CD using the optical drive, but I get similar results.

---

### Post by heir4c on 2013-11-02
Maybe create an new usb with unetbootin or multisystem. I use all the time multisystem and it work always fine. Not all distro can used on multisystem but all the ubuntu iso doing it fine. And you can set more than one on it. I have a 32GB USB3 with more than 20 iso on it:
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)
Direct Downloadlink:
[http://liveusb.info/multisystem/install-depot-multisystem.sh.tar.bz2](http://liveusb.info/multisystem/install-depot-multisystem.sh.tar.bz2)

Alternative:
Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by AmbiguousOutlier on 2013-11-03
Unetbootin seems to be working. It's currently installing now. 

Cheers.

---

