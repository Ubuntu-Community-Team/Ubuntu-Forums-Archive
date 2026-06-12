---
title: "Install ubuntu using raid 10?"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by andrewwk on 2007-06-21
Greetings All,

I am setting up a server with ubuntu.  I am using an Intel DG965WH mother board that supports Raid 0,1,5,0+1.  I can enable Raid 10 in the bios with four hard drives.  When I try to install ubuntu, I see all four hard drives in the partitioning section of the install.  This is where I'm stuck.  I have two questions:

1. Can I install ubuntu server 7.04 with the Raid 0+1 enabled in the bios?

2. If I can install ubuntu server 7.04 with Raid 0+1, how do I do it?

Thanks,
WK

---

### Post by andrewwk on 2007-06-25
Here's what I found out.  Apparently, most if not all motherboards have "fake raids".  Unfortunately, ubuntu server cannot be installed on a motherboard set to Raid 10 or Raid 0+1.  An extra raid card must be installed to install ubuntu server using raid 10 or raid 0+1.  I did some research and bought a [[COLOR="Blue"]3ware 9650SE[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042") card.  This card did the trick.  The card was easy to install.  When I was installing ubuntu, the installer only saw one drive, instead of the four drives when using the on board raid array.

---

### Post by iCara on 2008-01-04
> **andrewwk said:**
> Here's what I found out.  Apparently, most if not all motherboards have "fake raids".  Unfortunately, ubuntu server cannot be installed on a motherboard set to Raid 10 or Raid 0+1.  An extra raid card must be installed to install ubuntu server using raid 10 or raid 0+1.  I did some research and bought a [[COLOR="Blue"]3ware 9650SE[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816116042") card.  This card did the trick.  The card was easy to install.  When I was installing ubuntu, the installer only saw one drive, instead of the four drives when using the on board raid array.

Hi andrewwk, 

i ask you a thing.

I bought a 9650SE-4LPML controller and this is my "first time" with one of these devices.
I plugged it to 4 320 GB Sata II drives and created a raid 10 array.

I start Gutsy from livecd and it sees the array! :)

Installation goes on perfectly but at reboot... blinking cursor :(

Asus MoBo bios sees controller too and bios boot priority seems ok.

What does it go wrong in your opinion? Did i miss some steps?

Thanks...

---

### Post by iCara on 2008-01-13
Little update:

now i am booting from Ubuntu live cd and using command "boot from first hard-disc" --> grub starts and i can use my system.

:confused: anyone got an idea? Thanks!

---

### Post by dean123 on 2008-01-15
iCara:

Check Asus bios boot priority options .  If your Asus bios has "add-in bootable card" and "3ware", flip them. Sometimes change that boot order can help.

Also disable onboard SATA RAID if not used.

---

### Post by iCara on 2008-01-17
> **dean123 said:**
> iCara:

Check Asus bios boot priority options .  If your Asus bios has "add-in bootable card" and "3ware", flip them. Sometimes change that boot order can help.

Also disable onboard SATA RAID if not used.

It was actually a bios problem.

Boot device priority was and is set to:

1) Removable
2) CD-ROM
3) Hard-disk

Under sub-menu hard-disk:

1) 3ware SATA II controller
2) IDE spare disk (slave to IDE cd-rom master)

I tried to change to

1) IDE
2) 3ware

and all worked ok!

Thanks!

PS: 3ware controller very well "newbie supported" under Ubuntu.

---

