---
title: "PPC (Dual G5) question"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by blortuga on 2013-11-22
I have reviewed the PowerPC faq (and related documentation).

I am posting to ask if anybody has SPECIFIC experience in successfully installing onto a 2001-era Dual G5 PowerMac (2 Ghz).  

This machine has the new-world ROM, and two ATI Rage128 cards.

My monitor is plugged into the VGA port of one of the cards.  (oddly, the second card does not have a VGA port, it has two of the "newer" style connectors, and I don't have one of those cables).

Unfortunately, the internal DVD drive has gone kind of flaky.  I don't know if it's because it's really old firmware, or if there is an actual problem.  It can read some disks, and writing is hit-or-miss, depending on media.  That said: my main problem is that it does not recognize a Ubuntu LiveCD (12.04 PPC x64), at boot time.  StartupDisk won't recognize it as a startup volume. 

As far as I know, everything else on this machine is in perfect working order.  The PRAM battery is even fresh.

I have also made a USB drive of the LiveCD; this reads, mounts, and "looks" just fine in the Finder.

I have also modified this image, by "fixing" the /install/ofboot.p file (as described in [https://bugs.launchpad.net/ubuntu-cdimage/+bug/1051313](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1051313) )  (I experience my "problem" in both configurations).

I have tried booting from this USB flash drive installed in all three USB ports (two in back, one in front). 

Command-Option-Shift-Delete -> does not work.

Option -> does NOT give me the "boot drive selection menu".

Command-Option-O-F ->  here's the weird thing.
I do remember, when I first got this machine, that I could get into Open Firmware using this method.  
But now, when I use this combo, and boot, the machine starts up, (chimes), the monitor goes blank, and then, instead of the normal "grey Apple logo" screen that's usually displayed at a startup, the screen stays blank (monitor is not getting a signal).  The Open Firmware console is not displayed.  

Then, the machine's fans ramp-up, like it's on high-power chugging. (they don't go to full-speed, like you'd see during an automatic fsck, they just power up to a medium level, higher than the normal low-idle).  The machine then, just sits there. 

I assumed that I need a new-style connector for the other video port on the card, and that's why the Open Firmware screen isn't displaying.  (the VGA connector works fine for the standard OS display when I boot to 10.4.11).

So I have blindly typed in all the variations of the: "boot usb0/disk@1:2,\\yaboot" that I can think of. And I tried that with the USB drive in all three ports.  I tried it with the /install/ofboot.p file in both configurations (stock 12.04, and with the 1051313 fix).

I also tried using the "bless" command on the /install/ folder.  (also did not do anything).

I have to assume that either:
1. My machine is too old to support USB boot, and I'm just not seeing whatever error message is being generated in the OF console.
2. I don't have the correct device ID, (as listed in the FAQ), and I can't get it without an OF console.
3. There is something wrong with the 12.04 image that will not boot on my machine no matter what I type in the OF console.
4. OF has broken on this machine, and I'm not really *in* OF, and it's locked up, and I'm typing for nothing.

I'm trying to track down one of these newer video cables so I can connect to the other output ports of the card to see if I can view the OF output.

I'm also going to try the daily "Trusty" build, to see if there are new fixes that get around my problem.

I may try dropping-in a second hard-drive, to see if I can dd the Live ISO to that, boot from that, and install.

So my questions are:
1. When you enter OF in THIS model Power Mac, is the fan-speed increase that I noted, "normal"? (can I use this as an indicator that I'm in Open Firmware console?)

2. Has anybody successfully booted from a LiveCD USB flash drive on THIS model?

3. Doesn't the /install/ folder need to be "blessed" (with either the "bless" command on a Mac, or hattrib -b ?)

4. Should I expect that the current daily "Trusty" build is going to be more stable than the latest-supported 12.04?

---

### Post by blortuga on 2013-11-23
Okay, here's where it gets deep:

I got the full DVI cable, and connected it to my OTHER Rage128 card. (apparently, they're different rev cards).  The OTHER card turns out to be what OF considers to be "primary" on the tree, so the console would not appear on the screen from the second ATI Rage128 card.  

I was able to get into the OpenFirmware console this way.

My open firmware is reported as "1.4f".  (this is actually called "version 4", as reported by the "sudo bless --info --verbose" command".

I did some more reading, and decided that the boot disk MUST be formatted HFS+, in order to successfully boot.  
Therefore, booting from a USB disk would be impossible - there is no way to put-on the tbhxi attribute in FAT.
I also tried using Disk Utility to "Restore" the downloaded ISO DIRECTLY to a second hard drive.  This failed (error (2)).  

My last attempt was to install a second hard-disk drive into the machine.
I used a hybrid of the instructions here:
[http://ubuntuforums.org/showthread.php?t=780320](http://ubuntuforums.org/showthread.php?t=780320)
and here:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
(copying files the flexible way)

I didn't have access to "mac-fdisk", or hattrib. (I created this disk under Mac OS).
I copied the root files (incl. yaboot) (as-directed).

(it was tricky, because there is no "hd-media" directory under powerpc64, so I had to use the files from powerpc, hd-media, to obtain a boot.img.gz.  I don't know if this is right.)

Then, I used the mac "sudo bless --volume /volumes/Ubuntu_PowerPC_precise" and "sudo bless --mount /volumes/Ubuntu_PowerPC_precise --setBoot".   The command appeared to succeed, but ultimately, I don't think this worked, because the disk still does not appear in the Startup Disk control panel, nor in the Option screen at startup.  I had to go back into OF.

In OF, the devalias command revealed an sd1.  I did:
"dir sd1:,\"  and it WORKED!
Then I did 
"boot sd1:,\yaboot"   AND IT WORKED!!

I get to a black console screen. 
The fans wind up to FULL BLAST in this mode.

I ran "install" - and it walked through language and keyboard setup (etc).  However the installer insists on pulling install packages from CD/DVD.  I have a drive, and a disk in the drive BUT IT IS FLAKY (otherwise I would go ahead and just install from CD).

The installer could read the DVD I made, but could not copy files (read failed).  Because the installer is hard-coded to install from CD, I couldn't do anything.

---

### Post by blortuga on 2013-11-23
If I run the installer, and let the cd rom fail, I can get into a comand shell.  
I can see my install disk is mounted at /cdrom.  (?!?!?)  The CD ROM is fine and I can see and read all the files.



/mnt and /media are empty.  /dev has a full compliment of sda, sda1, sdb, sdc devices, but none can be accessed or mounted.

I think that I need to run the installer in "expert" mode, but I couldn't get that to work.  Not sure how to do this install this way.

---

### Post by blortuga on 2013-11-24
I did finally succeed.  I would write-up a howto, but I think that my case is probably pretty unique: dual G5 with a bad DVD drive.

I eventually installed my second hard-drive.
I formatted it HFS+, and I copied the ubuntu precise ppc files to this drive. (straight drag-n-drop).

I followed the instructions in THIS:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
(Copying Files The Flexible Way)

(from files at:  [http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/](http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc/))

I used the ubuntu ppc precise image's /install/yaboot.conf, and I copied it to the / of the volume).

My second hard drive was named "installdisk".
I used the Mac OS X Terminal command "bless --folder /volumes/livedisk" and "bless --mount /volumes/livedisk --setBoot".
I don't think that these did anything, though.

I booted in OF (command-option-O-F), from the DVI connector of the ATI card which was closest to the CPU on the motherboard - this is the primary adapter, and Open Firmware's console would not be displayed on the second adapter, (that's why I couldn't see it before).

I used this command to find my hard drive:
devalias
and it showed that "sd0" is my primary hard drive, and "sd1" was my secondary.
When I did "dir sd1:,\" - this listed the files in the root of the partition, and confirmed that the disk was readable by Open Firmware.
(I couldn't get this to work on any CD, DVD, or USB drive - period.   Must have been some weird thing about this specific machine?)

to boot, I used "boot sd1:,\\yaboot".

When I used the \yaboot.conf file from - [http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc](http://ports.ubuntu.com/dists/precise/main/installer-powerpc/current/images/powerpc) , and ran "install", I got a text-based GUI installer, which failed to complete, because it was hard-coded to copy packages off the DVD (which it could not read).

When I copied the /install/yaboot.conf file to /, I was able to get the regular ubuntu GUI installer to run, and I was able to successfully install.

Unity was horribly slow on this machine.  I have 3.5 GB of RAM. IO-related things were always very slow on this machine, but it's mad-speedy when I was doing anything that used the alti-vec units, (like ripping CD's - it's still like 8-times as fast as a brand-new macbook pro.)

I uninstalled Unity, and installed Lubuntu-Desktop, and it was much more responsive and snappy.

---

