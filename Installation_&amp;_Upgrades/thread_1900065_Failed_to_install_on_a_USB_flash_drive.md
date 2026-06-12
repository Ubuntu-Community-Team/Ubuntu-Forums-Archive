---
title: "Failed to install on a USB flash drive"
date: 2011-12-25
forum: Installation &amp; Upgrades
---

### Post by dannyarcher on 2011-12-25
Hi, I'm a newbie to ubuntu & linux.
For some reason, I need to install the ubuntu linux on a 8GB USB flash drive to provide myself a portable linux solution.

I just need to install ubuntu using the whole USB flash drive, but the installer said "**The attempt to mount a file system with type ext4 in ...... at / failed**" everytime after i have passed the step to choose which device or partition to install on.

I have tried file system type of either ext2 or ext4 , and also ubuntu version 11.10 and 10.10, all just got the same error.

Any idea about the problem?
Sorry for my bad English. thanks.

Here are some screenshots of the error message:
[http://img37.imageshack.us/img37/9315/ubuntu1b.jpg](http://img37.imageshack.us/img37/9315/ubuntu1b.jpg)
[http://img651.imageshack.us/img651/7291/ubuntu2.jpg](http://img651.imageshack.us/img651/7291/ubuntu2.jpg)
(can't resize the photos in the editor so i just give links to the photos)

---

### Post by JD8182 on 2011-12-25
Are you able to load up Ubuntu Live from the USB Thumb Drive? Instead of installing, try it first "live" from the USB.

---

### Post by dannyarcher on 2011-12-25
> **JD8182 said:**
> Are you able to load up Ubuntu Live from the USB Thumb Drive? Instead of installing, try it first "live" from the USB.
Boot Error.
What should i do?

I created the live usb with the Start Up Disk Creator and have no problem in creating other live usb.
Is it the problem of my USB flash drive?

---

### Post by darkod on 2011-12-25
What are you installing from? Another usb stick? CD?

You are not trying to install onto the same usb stick you are running the install from, right?

---

### Post by West201 on 2011-12-25
Did you verify MD5 of the ISO ?

---

### Post by dannyarcher on 2011-12-25
> **darkod said:**
> What are you installing from? Another usb stick? CD?

You are not trying to install onto the same usb stick you are running the install from, right?
Absolutely not.
I have tried installing from both CD and another USB stick.

---

### Post by darkod on 2011-12-25
Download a new image, best with torrent because it checks for corruption during download. If it doesn't work with new image I'm running out of ideas.

---

### Post by dannyarcher on 2011-12-25
> **jessejj89 said:**
> Did you verify MD5 of the ISO ?
There's no MD5 provided on the official download site.
Where should i find it?

But as i remember, i have once used the current ISO to install ubuntu on one of my PC.

---

### Post by dannyarcher on 2011-12-25
> **darkod said:**
> Download a new image, best with torrent because it checks for corruption during download. If it doesn't work with new image I'm running out of ideas.
I may try.
But i think the ISO should not be corrupted because i have used it before.
Anyway thanks for helping.

---

### Post by darkod on 2011-12-25
Depending what version is it, look towards the top of the links:
[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)

---

### Post by dannyarcher on 2011-12-25
> **darkod said:**
> Depending what version is it, look towards the top of the links:
[http://releases.ubuntu.com/oneiric/](http://releases.ubuntu.com/oneiric/)
Thank you so much.
Just verified and there is no corruption.

---

### Post by West201 on 2011-12-25
Well one other method is to install a different version and then upgrade to the current. I've found myself doing this a few times.

---

### Post by dannyarcher on 2011-12-25
> **jessejj89 said:**
> Well one other method is to install a different version and then upgrade to the current. I've found myself doing this a few times.
I have tried both 11.10 and 10.10.
May be i should try some even older versions ?

---

### Post by West201 on 2011-12-26
> **dannyarcher said:**
> I have tried both 11.10 and 10.10.
May be i should try some even older versions ?

Just curious, which application are you using to burn the ISO to the USB ?

---

### Post by dannyarcher on 2011-12-26
> **jessejj89 said:**
> Just curious, which application are you using to burn the ISO to the USB ?
The **Startup Disk Creator** that comes with the ubuntu.

---

### Post by West201 on 2011-12-26
> **dannyarcher said:**
> The **Startup Disk Creator** that comes with the ubuntu.

I would download Ubuntu again and check the ISO integrity using MD5. If it's possible burn it to another device perferably a CD/DVD. I'm running out of ideas, but keep me update :)

---

### Post by dannyarcher on 2011-12-26
> **jessejj89 said:**
> I would download Ubuntu again and check the ISO integrity using MD5. If it's possible burn it to another device perferably a CD/DVD. I'm running out of ideas, but keep me update :)
I've already checked it and the ISO ok.
May be i should find another USB flash drive and try.
It's so strange that i can't even load my 8GB USB flash drive up as Live USB, it just said Boot Error.
I've got another 4GB Kingston USB stick running as Live USB perfectly, but met the same error of unable to mount when i tried to install ubuntu on it.

---

### Post by kurt18947 on 2011-12-26
I've gotten the "boot error" problem when creating a LiveUSB.  The LiveUSB would load in some machines but not on one, a Gigabyte M.B. w/ award modular BIOS, it would show the error message.  What finally worked was to format the USB drive in Windows 7.  The factory format wouldn't boot, would produce the "boot error" message but format the same drive to FAT32 in Win 7 then create a Live USB (I used Unetbootin, not sure it matters) and it would boot properly.  Win 7 sets some flag or something that particular BIOS looks for.  If the BIOS doesn't find that flag, it gives an error.  I've tried reformatting USB flash drives to an ext* format and install Ubuntu in the usual way.  It did not work for me.

---

### Post by dannyarcher on 2011-12-26
Still can't find a working solution.
I'm going to try alternative install.

btw, thanks for all your help.

---

### Post by dannyarcher on 2011-12-26
Even alternative install resulted in the same error.
I'm over with this USB flash drive, gotta buy a new one.

---

### Post by West201 on 2011-12-26
Are you using a netbook ?

---

### Post by dannyarcher on 2011-12-26
> **jessejj89 said:**
> Are you using a netbook ?
No, I'm using Desktop.

---

### Post by dannyarcher on 2011-12-27
Just bought a new SanDisk Cruzer Blade 8GB Flash drive and had ubuntu working flawlessly!!!
THANKS FOR ALL YOUR HELP.

---

### Post by West201 on 2011-12-27
> **dannyarcher said:**
> Just bought a new SanDisk Cruzer Blade 8GB Flash drive and had ubuntu working flawlessly!!!
THANKS FOR ALL YOUR HELP.

I'm glad you were finally able to get Ubuntu working, don't forget to mark this "thread" as solved ;)

---

### Post by dannyarcher on 2011-12-28
> **jessejj89 said:**
> I'm glad you were finally able to get Ubuntu working, don't forget to mark this "thread" as solved ;)
Thanks:)

---

