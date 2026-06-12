---
title: "Will not run or install."
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by alt_f13 on 2007-04-21
Hi,

I tried installing Ubuntu three ways, none of which worked out. So far I haven't seen anyone else with the same problem on the forum.

Help?

Using wubi:---------

So I tried using wubi to install Ubuntu. It installed nicely so I rebooted and tried to load it. 

It never showed an Ubuntu loading title screen and instead it skipped right to a bunch of numbers in square brackets counting load time in the left column with what looked like hex numbers in the middle column followed by what looked like parameter names and hex number pairs. It did this for 5 minutes w/o HDD activity before I turned it off.

Rebooted and tried again. Same thing. Booted to windows, reinstalled Ubuntu. Same thing.


Using beta-alternative:--------------

So decided to put the kibosh on Wubi and used the *beta-alternative iso* I downloaded for Wubi to install Ubuntu to a *blank drive*. 

When trying to load *NTFSresize* it would crash with a message stipulating that the Windows drive had "*hopelessly many bad sectors*." Well it doesn't. 

I assumed that it was the ntfs compression of about 50000 files on the drive so I unplugged the ntfs drive and tried again. No errors.

I formatted the blank drive using the ubuntu formatter with 10Gigs for ubuntu, 1GB for swap, 15 as FAT32, and left 1.4 blank after the swap just in case I wanted to resize the swap later.

After installing for *eight hours*(!) in the red and blue screen area and rebooting, Ubuntu would show a bunch of commands too quickly for me to read and just stop on a black screen with a blinking cursor on it, never showing a boot screen.


Using latest desktop:-----------------

So I put the Windows drive back in, downloaded the latest desktop non-alternative iso and tried that minus the XP drive again. 

I used the run/install command from the menu. It shows the boot title screen this time, but then does the 3 column numbers counting thing again. The first time it got to a point where it cycled between "init_centaur..." and "inflate_dynamic..." really quickly with the same hex numbers and all, still counting the load time.

I tried it with the safe graphics mode option and got just a blinking cursor for ten minutes before I shut it down.

The next time it did the numbers scrolling thing came up again but stopped on "work_notifysig" with 23 equal signs on the line below and a blinking cursor beneath it. I tried it again with the drive wiped and no partitions at all and got the work_notifysig thing again.


You guys have mentioned errors in the forums for this type of thing, but I haven't seen any. I can't seem to figure out where to find log files either.

Ideas?


Monitor: LCD
Ram: 512mb
HD: 27.4GB IDE (though ubuntu seemed to be calling it a SCSI drive during the first beta-alternative format.)
Graphics: NVideo FX5200 (with disabled intel 82845G integrated graphics controller, no output showing on monitor)
CPU: P4 2.4 84845G/GL/GE/PV/GV/E
MainBoard: Asrock Intel 845G
Ethernet: Don't know. Mobo integrated

Used ubuntu-7.04-desktop-i386.iso as install disk on the last 3 attempts.

Thanks in advance.

---

### Post by alt_f13 on 2007-04-23
I had to disable my nVidia card. I have Feisty running off the CD well now, well as can be expected off a CD. It's still up to a 10 minute load time... but that's better than the installed version:

Once it is on the hard drive, it barely runs; it takes 25 minutes to even show the background and I've never even gotten to the GUI. It makes no sense to me. I'm reinstalling it now to see if my original partition configuration was the problem, but now that I see that it's taking 20 minutes on 94% and "Configuring Hardware" in the installer, I doubt that it's going to work.

Why does it run off the CD and not off the hard drive?

Even the slightest bit of help would be appreciated.

---

### Post by Makrie on 2007-04-23
Hi

Sorry not help, just sympathy - I'm having a nightmare installing it as well. 

Good luck to you!

Mark

---

### Post by alt_f13 on 2007-04-23
Forget it.

It ran for 8 hours under Wubi. I followed the instructions on how to install nvidia drivers and beryl I found on the net and it went back to the numbers loop thing.

I'm not even going to attempt installing ASIO drivers.

An OS shouldn't be this hard to pick up.

---

