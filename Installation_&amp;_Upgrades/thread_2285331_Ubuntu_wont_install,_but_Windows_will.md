---
title: "Ubuntu wont install, but Windows will"
date: 2015-07-04
forum: Installation &amp; Upgrades
---

### Post by john409 on 2015-07-04
So I built my first computer:

[B]Case - Corsair Obsidian 750D Black Aluminum / Steel ATX Full Tower Computer Case
Motherboard - ASRock 990FX Extreme9 AM3+ AMD 990FX + SB950 8 x SATA 6Gb/s USB 3.0 ATX AMD Motherboard with UEFI BIOS
CPU - AMD FX-8350 Black Edition Vishera 8-Core 4.0GHz (4.2GHz Turbo) Socket AM3+ 125W FD8350FRHKBOX Desktop Processor
RAM - CORSAIR Vengeance Pro 16GB (2 x 8GB) 240-Pin DDR3 SDRAM DDR3 1866 Desktop Memory Model CMY16GX3M2A1866C9R (Red)
Graphics - GIGABYTE GV-R927XOC-2GD Radeon R9 270X 2GB 256-Bit GDDR5 PCI Express 3.0 HDCP Ready CrossFireX Support Video Card
SSD - Corsair Force LX Series CSSD-F256GBLX 2.5" 256GB SATA III MLC Internal Solid State Drive (SSD)
HDD - Seagate Barracuda ST1000DM003 1TB 7200 RPM 64MB Cache SATA 6.0Gb/s 3.5" Internal Hard Drive Bare Drive
Optical Drive - Pioneer Black 16X BD-R 2X BD-RE 16X DVD+R 12X BD-ROM 4MB Cache SATA Blu-ray Burner BDR-209DBK
[/B]
But Ubuntu won't load.   :-(

Out of desperation I purchased a copy of Windows 8.1, just so I could test all my hardware, and it loaded just fine.

I used Ubuntu 14.04 trusty install USB that I tested on a laptop and works just fine.
Symptoms:
     I put the USB in a 2.0 slot on the front of the case (yes I tried the back too, just in case)
     After POST the screen loads with a dark purple background and a icon at the bottom of a rectangle with something in it and an arrow pointing at a circle with a man in it.
     A few seconds pass and the screen goes blank, then a underscore curser "_" appears in the upper left corner and blinks for about 10 seconds.
     Then the screen completely blanks out, and refreshes with a blank black screen that is slightly lighter than as if it was completely turned off.
     The system does nothing after that except spin its fans and wait.

I'm guessing it is an issue with the video card, and hoping somebody knows a good solution. I hate to have to go without ubuntu on a machine I built from scratch (or at least components).

---

### Post by Bucky Ball on 2015-07-04
When the purple screen with the icon appears, hit any key (or might be F6) and that should take you to an options screen. Now hit F6 and choose 'nomodeset' option. Proceed. Any luck?

I recently read Ubuntu doesn't support Crossfire, but doubt this is a problem unless you're actually using that. The vid card, on the other hand, I suspect is the problem also. That can hopefully be tweaked once you're installed and at a desktop. There is an open source Radeon driver and there may be a third-party one for that card, too. Unsure.

PS: Are you intending to run a lot of virtual machines or do pro-level resource intensive video/audio editing (or take a fleet of shuttles to Mars) because 16Gb is TONS of RAM which will probably never get touched otherwise. You don't mention a PSU, but you shouldn't need more than 500-650W for that rig. Looks nice. :)

---

### Post by john409 on 2015-07-04
WooHoo!!! I'm in!!!

Will I have to do this every time I load Ubuntu? 

Oh, I am in with 15.04 instead of 14, I had created a loader for the newer version wondering if whatever I was missing might be in it instead.

Thank you sooooooo much!!!

I plan on running windows (apparently my windows I bought last night comes with a complementary upgrade to the new 10), so I gotta have alot of ram and hard disk space. lol. and yes, power supply is a Corsair RM750, and there is also a H100i cooler in there. Maybe I will run some games on it sometimes.

---

### Post by Bucky Ball on 2015-07-04
You can add 'nomodeset' permanently like this.

Open the /etc/default/grub file:

```
sudo nano /etc/default/grub
```

Look for this line, in bold (your other stuff will probably look different from mine but disregard):

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"**
GRUB_CMDLINE_LINUX=""
```

Add it to the end of the line in bold, with a space after 'quiet' (or possibly 'splash' in your case), so it looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"
```

Control+X then 'y' to save and exit the file, then:

```
sudo update-grub
```

Once that's finished reboot. All good?

If you check with this command:

```
sudo lshw -C video
```

... that should tell you what driver you are using. Probably 'radeon'. There might be a third-party driver available for your machine, depends if you actually are going to need one as to whether you bother. You can look in 'Additional Drivers' after you've updated and see what's there. :)

Enjoy!

PS: With that much RAM, you could easily run Win as a virtual machine. Also remember that when you boot into Windows, Ubuntu uses NO RAM. Ubuntu may as well not be there. Only one OS is booted at a time. Vice versa with Ubuntu. Win is NOT running at all. Good luck.

PPS: Not sure if you install with the 'nomodeset' option on that it stays that way after install. You'll need to experiment. If it doesn't, you know what to do. :)

---

### Post by john409 on 2015-07-05
nomodeset stayed after I installed.

Like a dork I hit the windows partition when I was setting up extra drive partitions after getting everything running smoothly. Things went downhill from there, and I lost several hours staring at a grub error and only being able to boot from my USB. I eventually got it installed, but now I have a weird partition eating up my entire 120 GB SSD that I am afraid to delete. (the grub error was pretty simple to fix, once I figured it out. Just tell BIOS to ignore the drive on startup.)

set up Windows with dual boot. Timed it, from the time I choose to switch from Ubuntu to Windows it takes 19 seconds, and that includes typing my password in Windows. (Im sure that will change as I add things to startup)

The VGA controller that it installed was Curacao XT [Radeon R9 270X]. Does that seem like it is appropriate? It seems close, but I'm not sure how to, or if I even should stress test it. I did stress test the new GPU, CPU, and RAM with windows. (Seemed like I should find out if there are issues before the RMA period runs out from Newegg.)

---

