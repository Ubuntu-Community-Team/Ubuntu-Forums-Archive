---
title: "Cannot install ubuntu"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by 123brc on 2013-01-24
So I decided to try out ubuntu, I downloaded the file, put it on DVD.

When I tried to boot from CD it was impossible, in no place does it allows me to get to BIOS.

So I did the "can't boot from CD" install, when I restarted my PC and switched to ubuntu it said some short of error, and that it can be fixed by running dskchk /r so I did (it took like 40 minutes), after that I still could not get into ubuntu, shows somekind of error now (very hard to read, because every 10 sec or so the picture turns black and then back to normal).

How do I fix this?

When I restart my PC it shows nothing for few sec, then my PCs details (like ram etc), and goes on to loading operating system, then asks to choose between W7 and ubuntu. So no way to get to boot from CD or anything like that. 

Also I dont mind deleting W7 completely and leaving only ubuntu on this PC, as I have another machine.

---

### Post by furything on 2013-01-24
Never come across a PC that you cannot get into the Bios with 'Del' key or 'F2'
Anyway why don't you install from windows environment if you want dual boot (assuming you have free disk space)

see [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

I have always installed from CD and in dual boot (windows and kbuntu) although I do cheat a bit with my grub loader always being on a separate disk with my ubuntu installation. That way I can remove the linux disk and the windows MBR is intact and does not need replacing/repairing. You can also (from bios) tell the PC which hard drive to boot from.

Unfortunately I cannot convince my children to move from windows hence the dual boot.

---

### Post by dino99 on 2013-01-24
a few comments:

-  the windows tools are usefull for windows OS only : linux (ubuntu) use ext3 format, not ntfs
- while burning, always use the slowest speed to avoid errors; but its better to use an usb stick

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by 123brc on 2013-01-24
> **furything said:**
> Never come across a PC that you cannot get into the Bios with 'Del' key or 'F2'
Anyway why don't you install from windows environment if you want dual boot (assuming you have free disk space)

see [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

I have always installed from CD and in dual boot (windows and kbuntu) although I do cheat a bit with my grub loader always being on a separate disk with my ubuntu installation. That way I can remove the linux disk and the windows MBR is intact and does not need replacing/repairing. You can also (from bios) tell the PC which hard drive to boot from.

Unfortunately I cannot convince my children to move from windows hence the dual boot.



I did the windows installation, again the same error described in the OP, it asks me to run "chkdsk /r" and that doesn't solve anything, just a new error. 

I did try clicking f2, f12 every f basically. Also Del. Nothing helps me to get to BIOS.

---

### Post by furything on 2013-01-24
> I did the windows installation, again the same error described in the  OP, it asks me to run "chkdsk /r" and that doesn't solve anything, just a  new error. 

I did try clicking f2, f12 every f basically. Also Del. Nothing helps me to get to BIOS.     If you don't care about the windows 7 (suggest swapping hard drive anyway to preserve win 7), I would expect the bios boot to go through hard drive then cdrom anyway. This would mean with a blank hard disk or unbootable os that it would go to the cdrom. If you can run up a desktop from a live cd then you should have no problems installing.

You could try the usb option as suggested by dino99 as the bios might be set to boot from usb first. As you have tried every f key then the normal f11 to go to select boot is not there either. I have seen some bios that require the esc key to enter bios although this is normally reserved for skipping memory test.

Have you tried googling the motherboard part name or the PC if something like Dell or HP? You may be able to find the m/b instruction manual which should detail how to access the BIOS.

---

### Post by 123brc on 2013-01-24
> **furything said:**
> If you don't care about the windows 7 (suggest swapping hard drive anyway to preserve win 7), I would expect the bios boot to go through hard drive then cdrom anyway. This would mean with a blank hard disk or unbootable os that it would go to the cdrom. If you can run up a desktop from a live cd then you should have no problems installing.

You could try the usb option as suggested by dino99 as the bios might be set to boot from usb first. As you have tried every f key then the normal f11 to go to select boot is not there either. I have seen some bios that require the esc key to enter bios although this is normally reserved for skipping memory test.

Have you tried googling the motherboard part name or the PC if something like Dell or HP? You may be able to find the m/b instruction manual which should detail how to access the BIOS.

I tried with USB, no success. 

I'm not that technical, did not understand most of the 1st sentence. 

I will try motherboard suggestions.

---

### Post by 123brc on 2013-01-24
Ok, so this is my motherboard:

Gigabyte GA-A55M-DS2 

I didn't find any info on how to get to BIOS on google..

---

### Post by grahammechanical on 2013-01-24
I think it is poor quality service if a computer suppler does not provide a User Manual with the product.

You could look here for a manual. It might explain how to access the BIOS/UEFI setup utility.

[http://www.gigabyte.com/products/product-page.aspx?pid=3998#manual]("http://www.gigabyte.com/products/product-page.aspx?pid=3998#manual")

[http://www.gigabyte.com/products/product-page.aspx?pid=3998#ov]("http://www.gigabyte.com/products/product-page.aspx?pid=3998#ov")

Regards.

---

### Post by BlinkinCat on 2013-01-24
> **grahammechanical said:**
> I think it is poor quality service if a computer suppler does not provide a User Manual with the product.

+1   They can't want any return business

---

### Post by furything on 2013-01-25
I have had a quick look at your manual and as soon as you see the gigabyte boot screen logo press the delete key. I suggest keep pressing the key as opposed to holding it down.
(You'll here a beep after a while when pressing the key which means it has accepted your last key press and stop hitting the key).

You can also press the tab key to hide the logo screen and see the BIOS boot sequence. After pressing tab then press del and you should see on the screen entering setup.

You need the Advanced BIOS Features from the menu 
In the new menu and can see First Boot Device, Second and Third.
Select First and use up/down arrows to get the CDrom device and then enter
When you escape back out of this menu you need Save & Exit Setup

As another option F12 is the boot Menu so you can turn on PC and keep tapping this button, then the boot menu should come up.

I think you just need to turn on PC and keep tapping one of these keys (del or F12) and I am sure you will get into BIOS I suspect you have been pressing key to early or to late.

Download the manual and take a look at it. At worst case read the bit about clearing resetting CMOS. If that makes you nervous You may need to take it along to a shop.

As a minimal precaution if going inside the case, leave if connected to the mains but TURNED off at power pack. Always be in contact with the case and before touching anything inside to ensure static electricity is discharged.

---

