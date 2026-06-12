---
title: "Blank screen while trying to USB boot with UNetBootin"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by PeterChris on 2010-02-25
I put together a new computer (Intel Atom D510 motherboard, without an optical drive, no operating system yet).  On my Windows XP computer,   I downloaded (and verified) ubuntu-9.10-desktop-i386.iso.   Created a USB stick with latest version of UnetBootIn (unetbootin-windows-408.exe) using the iso file I had already downloaded. 

On the new computer, I changed the BIOS to make sure of the following:
BIOS Boot = enabled
USB Boot First = enabled
USB MASS STORAGE EMULATION TYPE = All Fixed Disc

I booted with this new USB stick and get the UnetBootIn menu but just these three options:
Default
Help
oem=OEM install

I'm new to Linux but I believe there are supposed to be several more options available when the UnetBootIn menu appears.

After the ten second delay, I then get a screen with this message:

Loading /ubnkern
Loading /ubninit.........ready

The screen then goes blank and stays that way.    I've left it alone for up to 20 minutes but nothing seems to be happening.    I see no Ubuntu logo, just a blank screen.    I've tried this whole process several times with different USB sticks but always have the same results.  

Any ideas on what's wrong?

---

### Post by mörgæs on 2010-02-25
Does it work better with 10.04?

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is an alpha, but surprisingly stable.

---

### Post by C.S.Cameron on 2010-02-25
If I recall right your UNetbootin options sound OK.
You might try booting your Windows machine with the Live CD and use usb-creator, (the built in option), to install to flash drive.
Have you tried booting your Windows machine with the Live USB?

---

### Post by PeterChris on 2010-02-26
Thanks for the tips guys.   I decided to do an installation from an external USB DVD drive I had.   I started another posting regarding that.   Everything is fine now.   Too bad I could never get Unetbootin to work.  

[http://ubuntuforums.org/showthread.php?t=1416347](http://ubuntuforums.org/showthread.php?t=1416347)

---

### Post by GIRI MURALI on 2010-06-24
Follow these simple steps for creating live USB

1.Download UNetbootin from the link
[http://unetbootin.sourceforge.net/unetbootin-linux-latest](http://unetbootin.sourceforge.net/unetbootin-linux-latest)
2.For running UNetbootin in Ubuntu, open the terminal and type the command "./unetbootin-linux-365"

3.From the new window select the distribution from drop down menu
eg: Ubuntu
4.select disk image as ISO and browse the ISO image
5.From the drop down menu right side of the "type" select USB drive and select your pen drive
6.then click OK

if you feel any any problem please visit this page.it will help you
[http://www.beubuntu.co.cc/2010/06/create-live-usb-for-ubuntuwindows-and.html](http://www.beubuntu.co.cc/2010/06/create-live-usb-for-ubuntuwindows-and.html)

---

