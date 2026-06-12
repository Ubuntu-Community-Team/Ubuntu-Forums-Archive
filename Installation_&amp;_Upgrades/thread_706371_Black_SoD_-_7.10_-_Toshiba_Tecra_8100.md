---
title: "Black SoD - 7.10 - Toshiba Tecra 8100"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Sientz on 2008-02-24
I have an old Toshiba Tecra 8100 laptop that I figured I would experiment and play around with so I downloaded the Ubuntu 7.10 CD.  I did the checksum and I burned it with Nero because the recommended free ware program did not want to let me (the 'Ok' button was grayed out).

When I boot off of the CD I get the installation menu.  I have tried doing the memory test as well as the OEM install and then 'Start or Install Ubuntu'.  They all take me to a black screen with a blinking cursor near the top left hand side.  

I have looked around for a cure for this and unfortunately none of them seem to be easy.  I guess there is an 'alternate' cd some where that I will go look for.

In a way it is a bit disappointing that this CD does not work.  I mean if you go buy windows and it doesn't work you dont have to get an 'Alternate CD'.  It just makes me wonder how hard this is really going to be for someone that doesn't know anything about linux.  I thought the whole goal was to make it so anybody could use this software and not have to be above average in the computer department.

Again just to clarify, I have a **Toshiba Tecra 8100**

:confused:

---

### Post by Pumalite on 2008-02-24
Post your specs. 256 MB of RAM or less>Xubuntu Alternate CD: [http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Sientz on 2008-02-24
256 it is, ok I will give the xubuntu disc a try.  Thanks for the heads up.

---

### Post by Pumalite on 2008-02-24
You are welcome. Good luck.

---

### Post by Sientz on 2008-02-24
Ok so now I have the Xubuntu cd and when I press enter on the 'Start or Install' it just resets the computer and I have to press F2 to get back to the boot menu, otherwise it just goes into windows again.

---

### Post by Pumalite on 2008-02-24
Did you get the Alternate Xubuntu?

---

### Post by Sientz on 2008-02-24
Yes I got the Alternate, I tried the option to 'Install in Text Mode' but it just goes to the blinking cursor.

Maybe it has to do with the screen resolution the F4 option?  I don't know but so far I have had no luck what so ever with this.  And I am now the proud owner of 3 CD's of Ubuntu, Xubuntu, and Xubuntu Alternate that don't seem to do anything besides pop up a menu lol.

---

### Post by Pumalite on 2008-02-24
You have a hardware incompatibility. Here is a guide and some boot parameters to try alone or in combinations:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317
The last line is to try each one separately or in different combinations.

---

### Post by Sientz on 2008-02-24
So basically I just press F6 and try adding various ones in there and cross my fingers?  There's no way to know which ones I should maybe try first or might apply to my situation?

I guess this operating system really isn't a solution for the average person.

---

### Post by Sientz on 2008-02-25
I've tried playing with various boot parameters but none of them seem to do anything different.

When I press ESC and then goto the 'boot:' prompt and then press 'Enter' I can see what it is doing, partially anyways.

This is what I see:

Loading /install/vmlinuz.............................................
Loading /install/initrd.gz.....................................................................

then death occurs.

](*,)

---

### Post by Pumalite on 2008-02-25
Let's look at this another way. Do md5sum on your iso, burn at 4x or less as image in good quality CD-R media. Clean the lens in your burner or try the CD's in a different computer.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Ghuloomo on 2008-02-25
Ubuntu has abseloutly no problem with installing, it's much easier than even windows xp, and it takes aproxiamally 25 minutes.

For me the Live CD doesn't work, but someone gave me a parameter to add to the boot options with the F6. It was something with the graphic, and I think it is your problem too. Specify your Graphic Card.

So I downloaded the Ubuntu alternative CD that has no Graphical user interface installation. And it's totally perfect. I have tested it with many weird old computers and it has been working fine, though I never honestly tested it on a laptop.

---

