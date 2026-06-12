---
title: "acer s7 (windows 8 problems.. i think?..)"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by mothership2 on 2014-01-03
so I was able to get into linux mint for half a second on this laptop and tried to install but it ended up just deleting windows 8 and not installing anything so I switched my usb over to a fresh copy of ubuntu 13.10.
Basically I am in legacy mode, ive tried switching off of the raid settings, but the only thing that happens when I boot is it gets to a black screen with a white cursor blinking in the top left corner.. I cant type, I have no options.. Nothing ubuntu or from the usb ever even shows up! just black. do I need to set nomodeset in the usb before i even try booting from it?
Im not even sure how I had got into linux mint except for just legacy mode/no raid. should i try booting ehfi or whatever that crazy windows 8 "bios" **** is..
thanks for the help!
Its my dads new laptop, he hates windows 8 but loves his laptop. Hasnt been able to use it for a week now because there is no OS (deleted from linux mint)

---

### Post by Mark Phelps on 2014-01-03
> he hates windows 8

The vast majority of folks who "hate" Win8 in reality, only dislike the new "Tiles" interface.  I'm one of those folks although I use Win8 every day.

With a little work, Win8 can be make to look and work much like Win7 -- with the previous Desktop and menu interface.

I recommend that to folks before they erase what they paid good money to get.

---

### Post by Bucky Ball on 2014-01-03
Welcome. Did you check the md5sum to make sure no defects on the USB flash?

Have you tried installing from a disk? If you have no Windows on (and effectively nothing on there) maybe boot from the Linux Mint media, open Gparted and erase partitions on the drive and any UEFI stuff/partitions, then try Ubuntu again.

Sorry if this is a silly question, but are you positive the machine is booting from the USB?

---

### Post by fantab on 2014-01-03
If you can then recover Windows 8. I think 'factory reset' might work. If not contact 'acer' and they might help you.
Like 'Mark' above says, Win8 can be easily made to look and feel like Windows7, if you install '[classic shell]("http://classicshell.net/")' in Win8. 

If you want to take advantage of the new hardware techologies then it will be a good idea to boot your OS in UEFI.

Tell us more about the laptop:
What graphics card does it have and are there more than one?
Did the 'acer' came pre-loaded with an SSD?

---

