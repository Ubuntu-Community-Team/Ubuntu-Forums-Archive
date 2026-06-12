---
title: "nviidia graphics card bios flash"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by kiwin on 2011-06-22
Hi
Has anybody got any idea how to flash the bios on an nvidia graphics card from ubuntu. I have no windows or mac boxes available - I haven't used anything except linux for years. The card is in a box I am using for mythTV and other media and the graphics card has a fault with the bios which makes the fan run at full speed all  the time. The new bios fixes this.

cheers

---

### Post by BicyclerBoy on 2011-06-22
Are you really sure this is necessary ?
You do not mean driver update ?
You can use "CoolBits" with linux driver, needs to be enabled in xorg.conf file.

The video card firmware flashing tools seem to be DOS based fortunately.
This statement is only based web search & personal experience from years ago..

The difficulty of using DOS is creating a bootable floppy disk or USB stick.

There was a HP utility that let you make USB memory stick boot like a MS-DOS floppy disk.
The mem stick had to be the earlier generation FAT16 <=100MB ? 
And the PC BIOS has to support USB booting.

Can use this USB stick to flash PC BIOS & play old DOS games..

Modern PC BIOS have built-in flash utilities (only form mobo BIOS).
Search nvflash

---

### Post by kiwin on 2011-06-22
yes it is definitely necessary. The noise level will drop by half and there is a  fix for a known bug with vdpau artifacts also.I guess i will have to look at a dos bootdisk on usb, as there is no floppy.

---

### Post by kerry_s on 2011-06-22
i think you can use unetbootin to grab freedos & put it on usb.
[http://www.freedos.org/](http://www.freedos.org/)

---

### Post by kiwin on 2011-06-22
thanks I will try it

---

### Post by BicyclerBoy on 2011-06-22
Can  you let us know what video card model ?
And how you get on with flashing it ?

There will be lots of MythTV/XBMC users that could be interested..

---

### Post by kiwin on 2011-06-22
I will when I get around to it. It may not be for a few days. The card is an Nvidia gt250

---

### Post by BicyclerBoy on 2011-06-23
Do you mean GTS250

or GT520

There shouldn't be many MythTV/XBMC users with GTS250 because it is not really appropriate for the job.

---

