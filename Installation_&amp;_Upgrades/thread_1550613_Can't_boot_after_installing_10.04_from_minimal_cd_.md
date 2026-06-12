---
title: "Can't boot after installing 10.04 from minimal cd on USB stick"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by entropy1 on 2010-08-11
I used unetbootin (on another machine) to put the ubuntu 10.04 minimal amd64 .iso onto a usb stick.  I used it to install a minimal system on a new 64-bit laptop (dual booting with Windows 7).  Now, when I turn on the machine I get my choice of OS.  When I pick Ubuntu, I get a blinking cursor, the harddrive is accessed.  Then the cursor disappears, the harddrive is quiet, and nothing else happens.  How can I fix this?

---

### Post by entropy1 on 2010-08-12
bump

---

### Post by gordintoronto on 2010-08-12
Can you boot and run from the USB stick? Please describe the computer: CPU, memory, video card, desktop or laptop?

Was there some reason you wanted the minimal?

---

### Post by entropy1 on 2010-08-12
Computer is:

HP EliteBook 2740p (laptop-tablet)

Intel(R) Core(TM) i5 CPU M 540 @ 2.53 GHz 2.53 GHz
4.00 GB (3.80 usable)
64-bit OS
Pen & Touch Input Available with 2 Touch Points

Intel(R) 82577LM Gigabit Network Connection
Intel(R) Centrino(R) Advanced-N 6200 AGN

Intel(R) Graphics Media Accelerator HD (Core i5)

I wanted a minimal install because I wanted to install only the software that I use.

The laptop does not have a cd/drive drive, but I have the laptop in a docking station that has a usb-connected cd/dvd drive.  I have burned (at slowest speed) a 64-bit 10.04 desktop live CD on another machine.  But the CD does not work on the HP; it does work on the other machine.   Interestingly, I have an old 8.04 32-bit live CD from ShipIt that doesrun on the HP.

I have also put the 10.04 64-bit live CD iso on a usb stick.  This stick works in the other machine, but not the HP.

---

### Post by gordintoronto on 2010-08-12
I'm fairly sure the graphics adapter is the issue. You might try Googling it and Linux and see what shows up.

---

### Post by DjSesso on 2010-08-12
Probably display. Have you tried booting the generic kernel? If you let it sit at the blank screen for awhile can you hit ctrl alt F1 and get a login?

---

### Post by cob on 2010-08-12
I am having the same problem after a USB stick installation, 10.04 AMD64 server.  I installed to a RAID-1 array on an AMD785 chipset, and it sits with the blinking cursor forever after rebooting into the installation.  I went back into the BIOS and set my disk configuration back to AHCI, rebooted to try to re-install and use software RAID, but it failed to boot from the USB stick.  Now, the strange thing is, it booted into my installation off one of the disks after failing to boot from USB, and is event behaving as though it's still in a RAID-1 array.

More info, here is my mounted array:

/dev/mapper/pdc_cdjdbbegdd1 on / type ext4 (rw,errors=remount-ro)

And a screenshot of the disk manager:

[http://imgur.com/6Ub1Z.png](http://imgur.com/6Ub1Z.png)

---

### Post by entropy1 on 2010-08-12
Thank you gordintoronto.  I think you are right.

I had a 9.04 64-bit desktop live cd and was able to install and boot.  However, it tells me there is no internet connection.  It may not have a driver for my network card or wireless (see post #4 above for card details).

So it seems that the ubuntu's after 9.04 can't handle my display, and the 9.04 and earlier can't handle my network/wireless...

Now that the 9.04 system boots, I cannot try DjSesso's suggestion.

---

### Post by entropy1 on 2010-08-13
I remembered that I had an old usb wireless card.  I plugged it in it was recognized by 9.04.

---

### Post by gordintoronto on 2010-08-14
Terrific!  Today I set up my new HP G62. It works very nicely, although I "cheated" and used a wired connection to activate hardware drivers. Everything works great, playing DVDs, webcam in Cheese, accessing shared folders on other computers.

But Ubuntu doesn't play my choice of live radio station -- yet. (The fan 590 in Toronto.)

---

### Post by dedede on 2010-08-25
If you want wireless internet (wifi), youll need a wired internet connection to download that driver. Yeah, I know...
Its the 1st in the list of resticted drivers.

---

### Post by entropy1 on 2010-10-17
Install of Ubuntu 10.10 Desktop works fine on HP EliteBook 2740p.  I guess the software caught up with the hardware.  After living with Windows 7 since July, I am now back running Ubuntu :)

---

