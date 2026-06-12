---
title: "MAJOR problem after using alternative cd to install 64bit"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Deeee on 2008-03-02
<edit>Ubuntu 7.10 64bit

Having succesfully installed windows xp to a small 40gb partition at the start of the drive being seen as drive 0, and making a 20gb one as a placeholder for ubuntu, and another afterwards for data (170gb), i proceeded to try to install using the alternative install cd . installing went alright after a few hiccups getting it to start (lack of a floppy drive broke its brain and was getting block i/o errors untill i disabled the controller in the bios). so i deleted the placeholder partition and made a 19gb main partition and 1gb swap, installation continued no problems, untill i reboooted.
this gave me an "Error loading operating system" error, so i booted into my handy dandy recovery live cd, and well the mess that had been made of the partition table was bad... the start sectors and heads were between 23- and 200 from the correct values, and neither partition was set as bootable.
im wondering if theres anything that could be causing this that i can fix ?

motherboard is a Asus p5k-3
ram is 4gb of DDR2-1066
cpu is a Core 2 Quad 6600
GFX is Asus EN8800 GT 512mb (nv gf)

---

### Post by zvacet on 2008-03-02
[Here](http://users.bigpond.net.au/hermanzone/p3.htm) is guide for alternate Cd install.

---

### Post by Deeee on 2008-03-02
Ive tried again, and this time it worked, the process in that how to is pretty much exactly what i did, the only difference is this time where there was a partition there was an empty space where i removed the bad partition the first install made.

I have had to edit my grub menu.lst thing to be able to boot at all though as the harddrive numbers were all in the incorrect order, leaving it unable to find anything (wierd quirk with how the bios chooses the primary boot harddrive)

---

