---
title: "uninstall /reinstall ubuntu"
date: 2013-03-19
forum: Installation &amp; Upgrades
---

### Post by 10thmntvet on 2013-03-19
good afternoon,

I would like to reinstall windows 8 and perform a daul boot of ubuntu after clean install of widows 8. The problem is that I think i may have wiped out the bios when i installed ubuntu.  I have a bootable windows 8 usb and wheni  try to boot it on start up it doesn't reconize it ubunto will not even reconize a bootable DVD either.  When I try to enter the bios using any of the combinations F8, F2, F12 or 0 I just get the avanced options for ubuntu.  I have a toshiba laptop.  Is it possable to wipe out the bios when installing.  
Thanks for the help.
Seth

---

### Post by MAFoElffen on 2013-03-19
In the past I would have said no. In the present, currently there are some laptops that have a few boot manager issues that need certain programs to get into their BIOS.  The BIOS is still intact, you just somehow sometimes lose the ability too get into it via the hotkeys. I'm thinking the DVD setting in BIOS changed, but now you can't get into it to correct that...

If you post the make and model of your laptop (assuming by your problem), or search via the make/model and on "can't get into BIOS settings"... There are may threads here and on the internet describing how to resolve this... but each fix varies to that specific make and model.

---

### Post by Andrew Bastin on 2013-03-19
Anyway, you need to install windows 8 before ubuntu.
So try uninstalling ubuntu and insert the Installation disk and install windows 8 then make partition and install ubuntu.

---

### Post by solarghost on 2013-03-19
Hi Seth,

No it's not possible to wipe out the BIOS, so don't stress about that. I would guess that your laptop is not set up to boot from those devices before it boots from the hard drive.

[COLOR=#ffa07a]When my laptop boots up I have a small message that tells me to press F12 to load BIOS and F2 to select boot device, towards the bottom of the screen, but this shows up for only about 3 seconds and then my laptop just boots from the hard drive if I don't press one of those two.

Have a look at your laptops manual online and see what the key is, it could even be the delete key.[/COLOR]

****EDIT*****
I did not realise that sometimes something might prevent you from accessing your BIOS, please ignore the text in red. :)
LiveLearn

---

### Post by 10thmntvet on 2013-03-19
how do you unistall ubuntu? I have a toshiba satellite-C855D.

---

### Post by MAFoElffen on 2013-03-19
> **solarghost said:**
> Hi Seth,

No it's not possible to wipe out the BIOS, so don't stress about that. I would guess that your laptop is not set up to boot from those devices before it boots from the hard drive.

[COLOR=#696969]When my laptop boots up I have a small message that tells me to press F12 to load BIOS and F2 to select boot device, towards the bottom of the screen, but this shows up for only about 3 seconds and then my laptop just boots from the hard drive if I don't press one of those two.

Have a look at your laptops manual online and see what the key is, it could even be the delete key[/COLOR][COLOR=#ffa07a].[/COLOR]

****EDIT*****
I did not realise that sometimes something might prevent you from accessing your BIOS, please ignore the text in red. :)
LiveLearn
Yes, the BIOS is still intact, but some recent laptops, when you start moving around Windows and/or installing other OS's moves a "file" that the Laptop needs to get into the BIOS... Can't specifiaclly rember which laptops this affects right off the top of my head, but it came up about a month ago. Without that file, it doesn't recognise the keyboard interupt to get into the BIOS. Before that, I didn't realize that was even possible. To me, that would be a design flaw. All other's boot POST directly from the Chipsets until evn touching the hdd.

So on "those" laptops, there is a fix.... a certain file (from the laptop vendor) that needs to be on a specific location of a disk, to make it all work again. As I remember, a month ago it was a certain file that needed to be in a service partition.

---

### Post by Andrew Bastin on 2013-03-19
> **10thmntvet said:**
> how do you unistall ubuntu? I have a toshiba satellite-C855D.
Just delete the partition in windows or anyother os if you receive a error as:

error:no such partition
grub rescue>

Then boot to ubuntu installation disk and go to terminal and type:

sudo apt-get install lilo

and ignore the errors

Then type:

[COLOR=#000000]sudo lilo -M /dev/sda mbr

[/COLOR][COLOR=#000000]May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.[/COLOR]

---

### Post by 10thmntvet on 2013-03-19
I do not have another OS Ubuntu is the only one at this time that is on this laptop is there a way to reboot into usb using terminal while ubuntu in up and running

---

### Post by tejpatel98 on 2013-03-19
When you first boot the computer it should give you an option to hit a f series key, but this option will only last for a few seconds. Once there either change the boot order in the BIOS settings, or just do a one time boot from the USB drive.

---

