---
title: "Partition trouble"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by damijit on 2008-10-31
I've been using hardy for a few months, but decided to clean install to intrepid so that I can "start over" now that I've gotten used to it. I think I've done something stupid, though--in gparted, I deleted the partition for 8.04 (and the extended partition)

When try to install intrepid, all partition options ("guided--whole disc", "guided--largest continuous free space", and "manual") all say the entire disc will become intrepid after install. I have a windows partition I don't want to lose, so this is not an option. Is there any way to force it to ACTUALLY use the "largest continuous free space"? The install option isn't doing it.

P.S. even my windows partition won't start up now, it says "grub error" then some number. I'm writing this from a different computer.

---

### Post by logos34 on 2008-10-31
the reason for the boot error is that you deleted the ubuntu root partition--grub needs it (where the menu.lst is).  

You may have to choose 'manual' partition option.  Or maybe check gparted to see what's up with the free space Desktop>system>admin>partition editor

---

### Post by laney_1 on 2008-10-31
[CENTER]_**getting windows working**_
have you got a windows install disc?

if you have you can use recovery console.

when it loads up select your windows system. (usally 1)

then type in fixmbr.

this will fix the mbr and allow windows to boot.

sorry can't really help with the partition side.

laney_1[/CENTER]

---

### Post by damijit on 2008-10-31
I don't have a Windows install disc, at least not near me.

When I choose "manual" from the radio buttons, it still says "Ubuntu 100%" for the partition"--which I don't want.

I think what I'm going to try to do is get an external HD, put windows on that, and make the whole thing Ubuntu so I don't have to worry about this anymore (it's a tiny HD).

How would I go about copying the windows partition to an external HD? Is there a tool I can use in the Ubuntu live CD?

Also, if I do this, and install intrepid on the whole drive, will I be able to boot again, or will I still get the grub error?

---

### Post by laney_1 on 2008-10-31
a fresh install should work fine in terms of booting. 

i am not sure about tools 

laney_1

---

