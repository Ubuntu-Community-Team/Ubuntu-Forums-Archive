---
title: "Input Not Supported"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by abbasali31 on 2007-05-28
I have Dell Desktop OptiPlex GX1 running Pentium III 600Mhz, Memory 256.  I downloaded the ISO image version 7.04 and burned an image CD.  Currently, my PC is running Windows XP.  I simply put the CD, and booted from it.  It got through the menu fine, and now whatever option I choose, error message prompts, "Input Not Supported".  After few minutes, I will command prompt with error messages such as I/O errors.

Any help will be appreicated for a new user to Linux.

Thanks,

---

### Post by ryanVickers on 2007-05-28
That's not exactly new hardware, but it's not *that* old, so I would think it should work ok (alot better than windows!)

where are you talking about when you choose the "option", and what are you choosing?

---

### Post by abbasali31 on 2007-05-28
What I meant to say by option is that after I boot from CD:

There is a menu appears:

Install Ubuntu
Graphic Image
Install with Latest CD Update
Check Memory
Boot from First Hard Drive.

I simply chose Install Ubuntu, and then the error appears, Warning "Input Not Supported", but still try to load the Unbuntu, and then I will see series of messages " I/O errors".

 Regards,

---

### Post by ryanVickers on 2007-05-28
Interesting,..
fyi - it's not your fault

Um, perhaps some of your hardware is not being detected proporly or is unsupported.  What kind of:
-mouse
-keyboard
-video card
-processor
-cd drive
-hardrive
-motherboard
-monitor

do you have? :)

---

### Post by abbasali31 on 2007-05-28
Mouse:  Ps/2 Compaitable

Keyboard:  Future Power (Standard Keyboard)

Hard Drives:  St and WD

CPU:  Intel Pentium III

CD ROM:  Samsung 

Video Card:  ATI, 3D Rage PRO AGP 2X

Monitor:  Planar 19 Flat Monitor

MotherBoard:  Don't Know  (Sorry)

---

### Post by ryanVickers on 2007-05-28
Ok, I wouldn't know anything about the motherboard anyways, just for someone elses help to help you :)

anyways, your mouse, keyboard HD, CPU, CD all look fine.  I don't follow the ATI line of card very well though, and I've never heard of that monitor, but if's common, then it's not the problem most likily.  I would look into the possibility that ubuntu doesn't like that video card.  Does anyone else have some ideas too?

---

### Post by abbasali31 on 2007-05-28
Actually, I downloaded the OS again, but this time with Alternate CD option (Text Based).  I am good to go now.

Going through the Install process rightnow, and seems okay.   Will let the forum know if something happens.

Thanks You So Much.

Can't wait to replace Windows.

---

### Post by abbasali31 on 2007-05-28
Well, I talked too soon.

The install process was going smooth until it reached "Install the base system".  The error is

The base system installation int /target/ failed.

Check /var/log/syslog or see virtual console 4 for details.

---

### Post by ryanVickers on 2007-05-28
sounds like it couldn't write to the disk or something.  Well, I'm glad you managed to get a more useful error this time :) but this is now over my head.  See if someone else can help!

Just be glad you're not using windows!  My favorite is when you do a windows check disk from the command line, the output goes something like this:

checking or fixing some files
checking or fixing some more files
checking or fixing some more files
checking or fixing some more files
one or more files were checked or fixed

I'm not kidding. :p :lolflag:

---

### Post by abbasali31 on 2007-05-29
I totally agree.  I am done with Windows, and wants to explore the world of Linux as I always hear that there is no comparision between Linux and Windows.
Anyway,  I just tried around with different partitions settings, and finally got it to work.  I don't have any logical backup that why it installed now by just using different partitions, but it did.  My HDD may have some problems, I guess.

Other question,  I would like to install Windows XP as well on this same system that is running Ubuntu just because for my wife as she is comfortable using Windows XP.

What will I need to do to run both Linux and Windows on a same hardware.

Regards,

---

### Post by ryanVickers on 2007-05-29
As long as they both worked at one point or another, there is nothing special you have to do.

I would usually recommend installing windows first, but it's no big deal.

1. So, shrink the ubuntu partition, and then make the empty space FAT32.
2. Boot from the windows install disk and install it on the FAT32.  Durring this process, re-format it as NTFS (all the while leaving the ubuntu untouched)
3. when it says that there is something else handling the boot loader, and would you like to change it, say no.  This will ensure only ubuntu boots, instead of windows (important!)
4. to make windows bootable along with ubuntu (select which to use every bootup) add a section to your /boot/grub/menu.lst file near the end that will add an option for windows.  I don't know exactly how it goes, but try this:

at the very end, below the last line, put this:
>  title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1
where the (hd0,0) the first number is the hd number (probably 0) and the second is partition number (probably 1 (second))

this allows for you to pick windows or ubuntu before you boot to either one!

---

### Post by abbasali31 on 2007-05-30
Thank You So Much.  I will let you know how it goes.

Best Regards,

---

### Post by ryanVickers on 2007-05-30
It's pretty simple, and good luck - hope everything turn out like you like!
It should work ok, I just say is "should" work and not that it "will" work because I just took the example from the file.  I would have just posted the real bit that it created when I had windows, but I don't have that anymore.  No need :)

---

