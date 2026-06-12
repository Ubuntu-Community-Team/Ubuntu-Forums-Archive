---
title: "Can't install ubuntu 12.04 LTS"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by l3b00 on 2012-05-08
Hi all just joined:), hoping to bother you with alot of dumb questions:P

Ok so i recently decided to start the switch over to ubunut and installed it on my laptop using the usb installer and my usb stick, this worked fine and now that i know a bit more about ubuntu i decided to put it on my desktop system. My problem is i cant seem to install it at all, ive tried 4 ways: 
1. tried to install it from a mounted image in windows, after running wubi.exe on the ISO nothing happens waited for like an hour (same as 4)
2. used the universal usb installer to create a  bootable flash but when i boot from it it says configuration file not found.
3. made a bootable dvd disk when i select the cdrom option from the boot menu it just starts up in windows normally (as if there was no cdrom to boot from)
4. windows installer was my last effort but it doesnt even load, downloaded the wubi.exe but when i run it nothing happens.

System
Intel core 2 Duo 2.6
Nvidia Geforce 8800GT
4Gb DDR2 800MHz 
HDD's
250Gb<-- windows drive (need that for diablo 3)
1Tb
200Gb<-- will be used for the ubuntu install

ISO: 12.04 LTS which i downloaded last night.

EDIT:
Tried all the same methods with my laptop and they work fine using the same ISO,disk and USB. Everything is 64bit.

EDIT2:
Tried to boot a windows 7 and a Ubuntu 11.10 install which didnt work either. Flashed my BIOS, unplugged the HDD that i thought was the problem. now i no longer get the configuration file not found when trying to boot to the USB or CDROM it just skips to the windows startup even if i change the boot order. So i plugged the HDD in again deleted the partition and left it as unallocated for a new install, still nothing.

Any help would be greatly appreciated:)

---

### Post by oboedad55 on 2012-05-08
> **l3b00 said:**
> Hi all just joined:), hoping to bother you with alot of dumb questions:P

Ok so i recently decided to start the switch over to ubunut and installed it on my laptop using the usb installer and my usb stick, this worked fine and now that i know a bit more about ubuntu i decided to put it on my desktop system. My problem is i cant seem to install it at all, ive tried 4 ways: 
1. tried to install it from a mounted image in windows, after running wubi.exe on the ISO nothing happens waited for like an hour (same as 4)
2. used the universal usb installer to create a  bootable flash but when i boot from it it says configuration file not found.
3. made a bootable dvd disk when i select the cdrom option from the boot menu it just starts up in windows normally (as if there was no cdrom to boot from)
4. windows installer was my last effort but it doesnt even load, downloaded the wubi.exe but when i run it nothing happens.

System
Intel core 2 Duo 2.6
Nvidia Geforce 8800GT
4Gb DDR2 800MHz 
HDD's
250Gb<-- windows drive (need that for diablo 3)
1Tb
200Gb<-- will be used for the ubuntu install

ISO: 12.04 LTS which i downloaded last night.

Any help would be greatly appreciated:)

How did you burn the install disk? Did you do it in Windows and burn the .iso?

---

### Post by l3b00 on 2012-05-08
Used nero to burn a bootable copy of the iso.

Forgot to mention all 4 methods work fine on my laptop using the exact same media as i tried on my desktop.

---

### Post by plant on 2012-05-08
forgive I am saying anything stupid. Your laptop may be  64-bit and you have downloaded 64-bit ubuntu( which will defenitely work in your laptop) and your desktop may be 32 bit.

---

### Post by l3b00 on 2012-05-08
Both are 64bit:)

---

### Post by rimibchatterjee on 2012-05-08
Is your desktop connected to the internet? If you are getting a blank screen you might not be getting the right video driver from inside the installation disk. If you are online Ubuntu can get the right version off the cloud and install it. I seem to recall there was a similar thread some time back. let me try to reference it.

---

### Post by rimibchatterjee on 2012-05-08
l3b00
you will need to tweak something called NOMODESET to get your video drivers to install properly. here are some links that might help.
Grub2 is just the initial logon screen. It has a few options but they might not be immediately visible to you. follow the instructions in the links and you should be fine.
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by l3b00 on 2012-05-08
Hi Rimi

Thanks ill try that tonight when i get home. and yes i am connected to the internetat all times.

But tbh i dont see how this is going to work since i cant run the wubi.exe in windows either, and thatl download the correct driver wouldnt it?

---

### Post by darkod on 2012-05-08
Just to remind you that wubi ia an installation inside windows, not a proper dual boot.

One thing that could help with wubi.exe is not to double click it, instead right click and select Run As Administrator. Sometimes you need that on vista/7.

I still wouldn't install wubi though.

If the dvd boots correctly on another computer but not on the desktop, make sure CD-ROM is before the HDD in the BIOS boot options of the desktop.

---

### Post by l3b00 on 2012-05-08
First i only used the change boot order for one boot utility thingy then after that didnt work i went into the BIOS and changed my boot order, first to every single of the 4 usb options using the usb then i changed it to cdrom when i used the DVD. still nothing.

---

### Post by darkod on 2012-05-08
Can you boot any other CDs on this computer? Do you have any to try will it boot them?

Also, the most commonly used option to boot with a usb stick is USB-HDD. It considers it the same as external usb hdd.

Try recreating the usb stick, it might not have been done correctly. The error about the configuration file might be from it which means at least it's trying to boot it.

---

### Post by l3b00 on 2012-05-08
Ill try other disks when i get home and see what happens then ill get back to you. and yes i know it is but hoped one of the other would work for no logical reason:)

---

### Post by l3b00 on 2012-05-08
Ok so ive found the problem, it was the hard drive that i plugged in to install the ubuntu on. the moment I removed it everything went back to being happy clappy. But now i have nowhere to put my ubuntu install any ideas on why the HDD would cause this and how to fix it?

---

### Post by iMurshaq on 2012-05-08
Use a slave drive?

---

### Post by darilon on 2012-05-08
If your second drive (the one causing problems) is an IDE/ATA drive (with the thick ribbon cable) then you may need to check the master/slave settings on the jumpers for both of your drives.  This can be a sticky point since some work with one as master and the second as slave, but some drive manufacturer combinations can require different settings including setting both as cable select.  Also ensure that you have cdrom set as top priority boot device in CMOS settings.

---

### Post by l3b00 on 2012-05-09
Both drives are SATA.

---

### Post by darkod on 2012-05-09
> **l3b00 said:**
> Ok so ive found the problem, it was the hard drive that i plugged in to install the ubuntu on. the moment I removed it everything went back to being happy clappy. But now i have nowhere to put my ubuntu install any ideas on why the HDD would cause this and how to fix it?

If you are referring to this disk having a bootloader that you want to delete, you can. But you still need to boot into live mode from cd or usb to be able to delete the bootloader on the hdd.

It doesn't make any sense. Regardless what you have on the hdd, when usb-hdd or cd-rom are priority boot devices it should boot from your usb/cd.

Try playing with the sata ports, move this problematic hdd in another port(s).

---

### Post by l3b00 on 2012-05-09
Darkod i added some more info in my original post of some more things i did last night.

EDIT2:
Tried to boot a windows 7 and a Ubuntu 11.10 install which didnt work either (USB and DVD). Flashed my BIOS, unplugged the HDD that i thought was the problem. now i no longer get the configuration file not found when trying to boot to the USB or CDROM it just skips to the windows startup even if i change the boot order. So i plugged the HDD in again deleted the partition and left it as unallocated for a new install, still nothing.

---

### Post by darkod on 2012-05-09
That still doesn't explain why it doesn't boot from cd or usb. Go through your BIOS settings again, and even through your board manual. Maybe there is something you are missing. The boards these days have so many different options that it's sometimes easy to miss something.

---

### Post by Mopar1973Man on 2012-05-09
I had a similar problem with a laptop that refused to look at the CD-ROM of Ubuntu at boot time. What I found that worked prefect and resolved it for me was do a CMOS reset or a BIOS reset and then only configure what you need for the install of Ubuntu (Boot CD-ROM first).

I knew the disk was good because it boots in all the other computers I've got but not the laptop so that told me there is a issue with the laptop BIOS settings...

Hopefully this gives you a clue... ;)

---

### Post by l3b00 on 2012-05-09
Thanks all for the help:) Ive figured it out, seemed to have been a problem with my BIOS flashed it and did a complete reconfigure from start to finish and it works now. 

Now i need to upgrade to 12.04 after installing 12.04 lol

Special thanks to darkod for all the ideas really helped me fix this:)

---

