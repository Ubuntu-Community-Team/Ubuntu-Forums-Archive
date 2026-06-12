---
title: "Installing 13.04 from Linux 3 thumbuntu (persistent)"
date: 2013-09-04
forum: Installation &amp; Upgrades
---

### Post by gannon2 on 2013-09-04
New (used) laptop, and no kidding, windows blue screened into an infinite reboot loop on day 2 (the "update 3 of 3" bug). Can't believe I didn't wipe it the second I got it! : (

Anyway.. I'm in Linux 3 right now running from a thumb drive (a much cherished gift I'm having to use for the first time) How would you recommend I get from here to 13.04 without having another thumb drive or cd to load the ISO onto?

Note that there is not an option to install Linux 3 from the thumb drive's boot menu. Also, I am not interesting in fixing windows.

-Gannon

---

### Post by andan on 2013-09-04
My fix would  be this download unebootin, on a USB drive, if unable to download on hdd use unebooting to load ubuntu and install from USB. not sure if 13.04 available directly from unebootin but in worst scenario install latest available ubuntu version then upgrade.

on unebootin page u can find handy info how to use unebootin.

cheers

---

### Post by oldfred on 2013-09-04
Welcome to the forums.

This is a bit more advanced, as you have to edit grub menu and understand path where ISO is saved.

Is your flash drive a full install? And booting with grub? Does it have room for the ISO as the ISO?

I directly boot ISO from flash drive or hard drive to install. But you have to manually add an grub ISO boot stanza to the grub menu. If a full install you can easily add it to 40_custom. But examples shows boot stanza entry and you just have to modify to your path. 

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by gannon2 on 2013-09-08
Interesting.. I didn't know installation without a CD or external was possible (good work folks!). So.. the day after my post I became impatient and fixed my windows issue; thought the thread was stagnant.

This means I can download this GRUB 2 jazz and do without UNetbootin and the USB drive. If I happen to still need help, I will start a different thread.

Thank you, thank you.

Be well.

EDIT: Actually, if anyone is interested in truly solving the problem in this thread, here is an example of the kind of help I was looking for:

Ex:1
"To protect the files on your USB, you can put them on a secure partition therein.
Make sure you have this utility: exampleutility
CD to your USB drive on the terminal and type, e.g. : "mkpart -unwrtable/unreadable/etc.. 10gigz nameofpart"
Now move the existing data on the usb to that partition
When you are done (and here instructions are provided to revert the USB to its original form)

Ex:2
"It doesn't matter, you won't mess up the USB by following the usual procedures for installing from it."

---

### Post by sudodus on 2013-09-09
Welcome to the Ubuntu forums :-)

There are many ways to make USB install drives and to install a linux operating system. See also the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by sudodus on 2013-09-09
> **gannon2 said:**
> 
Ex:2
"It doesn't matter, you won't mess up the USB by following the usual procedures for installing from it."

This is my experience :-)

---

### Post by coldraven on 2013-09-09
More options;
If your machine has a card reader you can install from a SD card if you have one somewhere. (I use a 1GB card)
I use Unetbootin to make the card bootable. A Windows version is available. See here: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

