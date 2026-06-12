---
title: "Installing 64 bit ubuntu..."
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by marksibly on 2008-04-16
Hi,

I want to install 64 bit ubuntu on my system, but it's not working. I need 64 bit as I am developing an application that requires a large virtual address space (but not that much physical mem).

After booting from a dvd burned from a downloaded iso, the system eventually just hangs - it gets up to the initial splash page with 'boot/install' etc options but after that nothing.

I actually suspect my dvd drive as it has given me occasional problems, but before replacing it I'd like to double check that my system is even capable of running 64 bit ubuntu.

Here are the cpu/ram/mobo/gfx/dvd specs:

Intel Core 2 Duo Q6600 Quad Core 2.4Ghz
Corsair 2GB(2X1GB) DDR2-800 4-4-4 Dual Channel Kit 
ASUS  P5E Intel X38 LGA775 ATX 1333FSB
BFG mVidia 8800GTX OC2 768MB PCI Express
Asustek 1814BLT SATA DVD Writer

It's a pretty grunty system, but I guess it's possible there's some kind of incompatibility somewhere.

Thanks in advance for any help!

Mark

---

### Post by PmDematagoda on 2008-04-16
At what speed did you burn the ISO?

Also did you try using options such as "nosplash"?

Edit:- I realise that I moved this thread to the wrong place, it should have been in the Installation and Upgrading section, sorry:).

---

### Post by marksibly on 2008-04-16
Hi,

I burned the CD on a Mac - 2X I think, but the Mac's pretty reliable.

I'm pretty sure it's the dvd unit on the PC that's the problem (which is what I'm wanting to install Ubuntu64 on), but I still can't find any hard info on what the hardware requirements are for Ubuntu64.

Anyway, turns out I can get a replacement dvd player under warranty, so I'll give that a whirl.

Bye,
Mark

---

### Post by GTengineer on 2008-04-17
I don't see any reason it would be incompatible with Ubuntu x64.

Try editing the booting command (I believe it is F6 function key) and remove "quite splash" from the end. I have had problems like this with my 8800GT. I would also recommend giving Hardy a shot, even in beta stages it was able to handle my 8800GT much better. Although I think I still had to delete quite splash to install it.

---

### Post by st0nedpenguin on 2008-04-17
Definitely give the suggestion by GTengineer a shot, removing splash solves the problem for me every time.

You'll also probably need to edit Grub post install to remove it there too, or change the resolution for the splash to something it likes.

---

### Post by marksibly on 2008-04-17
Hi,

Ok, removing 'splash' from the booting command helped.

It eventually gets to a blank brown screen with a mouse pointer, then after a time of wonderment the display disappears again.

However, if I then hit 'Enter', I get to a Linux desktop!

I'm a little nervous to install at this point...

The version I'm trying to use is the 64 bit 7.10 version from here...

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Is there an older version available that doesn't have these display problems?

Perhaps 6.06 'LTS'?

---

### Post by GTengineer on 2008-04-18
> **marksibly said:**
> Hi,

Ok, removing 'splash' from the booting command helped.

It eventually gets to a blank brown screen with a mouse pointer, then after a time of wonderment the display disappears again.

However, if I then hit 'Enter', I get to a Linux desktop!

I'm a little nervous to install at this point...

The version I'm trying to use is the 64 bit 7.10 version from here...

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Is there an older version available that doesn't have these display problems?

Perhaps 6.06 'LTS'?

Try 8.04 like I said it was able to handle my 8800GT much better than 7.10

---

### Post by warp99 on 2008-04-18
> **marksibly said:**
> Hi,

I burned the CD on a Mac - 2X I think, but the Mac's pretty reliable.

I'm pretty sure it's the dvd unit on the PC that's the problem (which is what I'm wanting to install Ubuntu64 on), but I still can't find any hard info on what the hardware requirements are for Ubuntu64.

Here are the requirements for Ubuntu 8.04:

[https://help.ubuntu.com/community/Installation/SystemRequirements?highlight=%28requirements%29](https://help.ubuntu.com/community/Installation/SystemRequirements?highlight=%28requirements%29)

as for the requirements with the 64-bit install they are the same except you need a 64-bit processor to run them. Since the release version of Hardy is less than a week you should install that one instead.

---

### Post by sippnonacorona on 2008-05-18
I installed HARDY onto a P5E-VM mainboard. The problem I had was that 8.04 does not support the Intel G35/X3500 chipset used by this board. 

At install time, to avoid what seemed to be a frozen dark screen was to hit F6 and add VGA=795 to the options line. This forced a VESA 1280x1024x24bit screen. It worked fine. I then added the same VGA= to the grub menu.lst file. Eventually, I'm hoping there are native drivers to support this chipset in a future upgrade.

---

### Post by criskat777 on 2008-05-18
you should try 8.04 Hardy i installed it on 1 desktop and 1 laptop that had given me problem with 64bit 7.10 Gutsy and hardy is rock solid even video drivers was a breeze with envyNG:popcorn:

---

