---
title: "Boot from USB on Dell Dimension C521"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by ticket on 2010-07-31
I haven't been able to boot Ubuntu from USB on Dell Dimension C521.
The machine currently runs XP and I wanted to try out Ubuntu, in particular to assess the performance of flash video.

This means I need to load the nvidia drivers and the adobe flash package.

The Ubuntu live  / install CD works, but you can't install the nvidia drivers without rebooting.  

I had the same problem with a Linux Mint live CD (this has the adobe flash built in).

I then made a bootable USB memory stick holding the live Linux Mint. On another Dell machine this booted perfectly, but on the C521 it got ignored and it simply booted XP.  

I transferred the Linux mint live CD to a hard disc with a USB connector and tried that, with exactly the same results - it was ignored,

I then tried connecting a 9.1 Ubuntu system disc via USB.  This did get recognised, but the boot stopped within a mysterious grub text console (sh:grub), with no clue on how to proceed. Guessing, I tried typing 'boot', but the shell would say no kernel found.  There was no 'kernel' command.  Typing 'exit' booted me back to XP again. I tried this also with the XP internal O/S disc disabled via the BIOS - and got the same result.

Anyone got any ideas on how to do this?

---

### Post by Joe of loath on 2010-07-31
So, I'm assuming you're pressing F12 to get to the boot menu, then booting from 'USB Device' yes?

---

### Post by ticket on 2010-07-31
Yes, I did that. I also set the boot priority in the BIOS to try USB devices first, then the CD ROM and finally the hard discs.  Either way the results are the same.

---

### Post by Joe of loath on 2010-08-01
How are you writing the cd image to the usb stick, and have you tried a few different sticks?

---

### Post by efflandt on 2010-08-01
I have had trouble with some Dell laptops that go through their splash screen so fast, before a USB hard drive spins up that BIOS does not see the hard drive.  In that case they do automatically boot from USB even if first in drive order, and the USB drive does not show up when pressing F12 to select boot order.  So I either have to go to CMOS setup and change something insignificant (like order of floppy and CD/DVD boot order), or boot Windows first, and then restart with the drive already connected.

I don't recall if I had that problem with live/install iso on USB flash, but I might have still needed to use F12 (maybe a safeguard to avoid accidentally booting from possibly infected CD or DVD).  The only virus I ever caught was a boot sector virus spread by floppy disks (long ago).

Note: In order to add programs or drivers to live iso on USB, you need a persistent data file (casper-rw).  If you create that using Startup Disk Creator in Ubuntu, there is a slider for persistent data, but sometimes the maximum might not work and might need to be at least one click (0.1) down from maximum.

Anyway, if that computer keeps booting XP first, try warm rebooting and see if you can select the USB drive with F12 from BIOS splash screen.

---

### Post by ticket on 2010-08-08
> How are you writing the cd image to the usb stick, and have you tried a few different sticks? 

I downloaded the Linux Mint iso (based on Ubuntu 10.4) and used the Ubuntu 10.4 "Start up disc creator" utility on it.   

The USB this created boots fine on a Dell XPS machine, but is completely ignored by the Dell C521. I have tried a warm restart and using F12.  Under XP on the Dell C521, the USB is readable, showing all its files.

> If you create that using Startup Disk Creator in Ubuntu, there is a slider for persistent data, but sometimes the maximum might not work and might need to be at least one click (0.1) down from maximum

I'll have to investigate this.
- edit: I remember I set the persistent data to zero (The persistent data allow you to save stuff from a live session). I doubt it has anything to do with the BIOS detecting the USB stick (well, you never know ...)

---

### Post by erikzon on 2011-04-12
if you take away a small piece inside your Dimesion and put it back, your BIOS settings will reset and may accept "boot"with usb, I happened to me when I was cleaning my computer ... is a small piece in the center of the motherboard ... I hope I've helped

---

### Post by Joe of loath on 2011-04-12
> **erikzon said:**
> if you take away a small piece inside your Dimesion and put it back, your BIOS settings will reset and may accept "boot"with usb, I happened to me when I was cleaning my computer ... is a small piece in the center of the motherboard ... I hope I've helped

This 'small piece' is the BIOS battery. Will be a small lithium button cell about 2/3 of an inch (1.7cm) across, usually in a plastic holder near the edge of the board, but not always. Remove the power, open the case, remove the battery, and hold the power button down for 10 seconds. After that, it should be reset.

---

### Post by Dutch70 on 2011-04-12
If the OP hasn't solved this problem in the last 8 months, I doubt if he/she is going to. ;)

---

### Post by Joe of loath on 2011-04-13
Damn, I should find a way to make my email subscriptions cancel after a few weeks of inactivity :lol:

---

### Post by Dutch70 on 2011-04-13
Hahaa, wouldn't that be nice. I've done the same exact thing. Who knows though, maybe someone will find it on a google search and it will help them.

---

### Post by ticket on 2011-06-14
> **Joe of loath said:**
> Damn, I should find a way to make my email subscriptions cancel after a few weeks of inactivity :lol:

Patience!!

I just got this to work.
I installed Ubuntu 10.04 to a USB stick, upgraded it to 10.1 (probably not necessary), inserted it in one of the rear USB ports, turned on the power and up came Ubuntu!  I did not disable the main HD either. Although I pressed F2 and F8 during boot, I didn't get the BIOS or boot menu to come up - maybe I pressed the keys too late.

Edit: In fact, inserting the USB stick in the front USB port also works. No need to press F12 or whatever to get a boot menu - Ubuntu just comes up!  I guess I may have configured the BIOS boot order to go for USB devices first.

I note that 10.4 has a new boot loader, so maybe that did the trick.  Also, using a full Ubuntu installation on the stick, and not a 'live version', may have helped.

I then tried playing some HD youtube vids.  At 720p they are just playable (the graphics card is an nVidia 6150LE).  Unfortunately, after doing that a few times, the system started to lock up - I think it was paging to swap, probably because HD chewed up all the available RAM.

I noticed that the sound wasn't working - that probably just needs a re-configure somewhere.

So yes, it can be done!

---

