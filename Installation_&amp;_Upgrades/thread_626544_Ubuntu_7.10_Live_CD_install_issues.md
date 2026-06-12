---
title: "Ubuntu 7.10 Live CD install issues"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by trayion on 2007-11-29
Howdy ya'll

I've recently gotten my own Gutsy installed and as such have been trying to convert my dear older brother as well.
Well, first part of that missions succeeded, but now we've run into some install issues.

He downloaded a fresh 7.10 Live CD (tried both X86 and X64) and it checks out fine on the MD5.

The issue is that when trying to boot into the live disc it simply doesn't load all the way through.

removing quietboot and setting it to nosplash gives some info about the squashntfs hanging.
Now from all I've read this is an issue with the CD, but we've tested with 2 different DVD drives in his machine and with both discs, neither work.

I'm semi-suspecting it to be the hardware but i'm not sure, setup is as follows:
Asus P5-N32 SLI deluxe motherboard
XFX 8800 GTS graphics card, 320MB memory
4 GB PC6400 DDR2 dual-channel memory
Intel E6700 (i think) Duo-core 2.66ghz cpu
Turtle beach montego DDL sound card

Now, in my ignorance i'm either thinking it's because of the graphics card (doesn't make much sense since it seems to be going through fine on that step) or the amount of ram (haven't found any info on how Ubuntu 7.10 handles 4GB memory)

Tried alternately with the UnetBootin manager solution and this hangs straight after having run the XresProbe and selected the Display resolutions.

Anyone have any good ideas what's wrong with this one?

Quick answers would be very appreciated since that baseball bat he is currently waving around over my head is a wee bit intimidating ;)

*Edit*
I think I've narrowed it down a bit actually, has anyone encountered issues with SATA based DVD drives? my brother has two of these and they both cause issues, but the same disc runs fine in my ancient IDE DVD drive.

---

### Post by ghstwalker on 2007-11-29
Trayion
I've been having the same problem with almost the same setup. You seem more advanced of a user than i am, though. 
With the board i believe its the APIC control from the the motherboard.... and maybe something else i have not identified. 
When you hit the load option screen press f6 and enter 
> noapic nolapic
for the boot command arguments...
Mind you I have only gotten this to work with 6.06 as i still get a blank screen with 7.10.
Lemme know if this helps. here's some resources the forums have helped me with. 
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html]("https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html")
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html]("http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html")Also update your bios for P5N32SLI. 
I haven't been able to do this, because i dont have a floppy drive.

---

### Post by trayion on 2007-11-29
gonna give that a spin and see if it helps, updating the BIOS is definately on the to-do list as well.
will report back and see if it yields any results, thanks for the feedback though :)

---

### Post by ghstwalker on 2007-11-29
no problems

---

### Post by ghstwalker on 2007-11-29
any luck?

---

### Post by trayion on 2007-11-29
haven't had the chance to test everything just yet, should be loads of time for it this week-end though, hopefully a few quick fixes will sort this aggravating little problem out.

---

### Post by trayion on 2007-11-29
okay, we just got it tested and after a BIOS update and using the noapic nolapic (note to self, spell them properly or they don't affect anything) and it's gotten the live session running.
Big cheers and a virtuals case of brew on it's way to ya ;)

Time to see how the install itself behaves now... oh dear.

---

### Post by Jaszczak on 2007-11-29
Hey fellas Im the one with the Alubat, also known as Trayions bigbrother.

Ubuntu is now installed, but alas, it fails during boot, basically same issue as when we tried to install it.

so my best guess would be that I need to add the noapic nolapic command in the boot.ini ( or what ever its called in linux, YES I have never touched this stuff before but its never to late to learn)

I dont have a problem booting in safe mode, but the graphical interface mode seems to have some problems.
I can get to edit the boot loader, but i'm not entirely sure what to add where

do I need - before the noapic and nolapic , example -noapic -nolapic, and do I put it in init.rd or kernel ??

thanks in advance
Jaszczak

Oh Ghstwalker I updated the bios and enabled the Memory Remap Mode in Bios, that seemed to speed up things quite a bit.
But we still seem to have the same problem. Ill get back to you if I/we find a solution

---

### Post by trayion on 2007-11-30
*sigh* took untill now to figure out that all that had to be done in order to boot into GNOME was simply to set change

splash
into:
nosplash

in the kernel options for the /boot/grub/menu.lst

and voila, it boots like it's supposed to.

---

