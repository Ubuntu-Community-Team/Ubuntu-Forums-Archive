---
title: "Another way to install unbuntu?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by deathfinderxx on 2010-03-02
Ok well my friends lappy is really pooped out right now. Somehow it got a virus which deleted all his drivers. So it cant access the internet nor read an sd card or a usb while in windows. Plus it has no built in cd drive. Its a Portege 205 and well im trying to figure out away to install the unbuntu remix os so he can get his system up and running again. Does anyone have a way to do this? Only bootable ways on his bios is hdd,fdd,sum sort of lan thingy, cd-rom,

---

### Post by amrypma on 2010-03-02
has it got a spare usb port? you can make a bootable usb stick which will install ubuntu.

---

### Post by d3v1150m471c on 2010-03-02
Ubuntu doesn't rely on windows to install. Make a Live cd on a cd-r or usb drive and boot from it.

---

### Post by deathfinderxx on 2010-03-02
But like i said, it wont boot with a usb because its not on the boot priority list, and it has no cd-rom drive.

---

### Post by utnubuuser on 2010-03-02
Can you enable booting usb in BIOS?  - Many machines can boot USB, but have to be so enabled in BIOS to recognize USB at boot.

There are different types of USB-disk types too, some of which emulate floppy drives etc.

You could also boot/install from network.

---

### Post by deathfinderxx on 2010-03-02
No it doesnt have that option >.<, umm how can i emulate the floppy or the network one? Will the network one work even if it doesnt have a network driver? Stupid virus erased all the drivers >.<

---

### Post by pricetech on 2010-03-02
However you boot the computer, winders will have nothing to do with it.

Does the computer have a bay for an optical drive ??  If not, it would almost have to boot to a USB device even though USB is not on the boot list.

For example, it may not boot to a thumbdrive, but if you attach a USB Optical drive, it might.

---

### Post by deathfinderxx on 2010-03-02
I do not have a usb optical drive like i stated before, and it has no attatchment for an optical drive, its ment to be used with a usb optical drive. But how would i do this emulating of a floppy drive or the network thing. Please i need to get this setup asap.

---

### Post by Sef on 2010-03-03
Check [Ubuntu Documentation Installation]("https://help.ubuntu.com/community/Installation").   There are a number of different ways to install Ubuntu.  Perhaps one of them will work for you.

---

### Post by deathfinderxx on 2010-03-03
well i was able to make my flash drive a hdd, and it reads it. Is there away to run it off of it while windows is running? and that it installs on the other hard drive and not this one?

---

### Post by deathfinderxx on 2010-03-03
ok i finnaly installed ubuntu9.10 remix thingy but the thing is it seems like the netbook launcher is taking up alot of cpu. Also it still has windows and most of the files still there but i want it all tobe gone and just have ubuntu. Is there a possibile way to have that and also how to make this run faster?

---

### Post by deathfinderxx on 2010-03-03
anyone? i tried installing the desktop version but it wouldnt even load after the little logo. Now im reinstalling the remix. But im expecting to have the same laggy experience. Could someone please help me out with this

-edit-
just installed it works, but as before its lagging horribly.
Im useing a Toshiba Portege m205. It has 2 gigs of ram and i believe 1.5GHz Intel Pentium M,Nvidia GeForce FX Go5200, Please reply asap because i gotta give this pc back in like 8 hours and i need it to run atleast smoothly.

-edit2-
i think there might be a hardware driver that im missing or something because its not showing up i believe. were can i find it?

---

### Post by deathfinderxx on 2010-03-03
well i just did a update on ubuntu downloaded like 136 programs then it said it needed to be rebooted. So i pressed accept and now it restarted and it loads to the little logo but theres no animation then a black screen comes up saying
init:udevtrigger main process (394) terminated with status 1 and more stuf
whats going on?

---

### Post by amrypma on 2010-03-10
I've ran into this on Sunday. It turned out the problem was the size of the usb drive. The startup disk creator uses a fat32 (windows 95) partition the same size as the drive. And fat32 only goes to 4 Gb. So everything looks ok until you try to boot from an 8 Gb flash drive.

In the end I bought a usb flash drive *small* enough for the installer to run.

I never thought I'd post this.

---

