---
title: "Ubuntu Geek cannot install Ubuntu on his computer!!! HELP!!!"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-03-23
Howdy, people!  I have run into a little problem.  I just got a custom-built Pentium4 3.2GHz, 512MB DDR2 400MHz RAM, 128MB MSI ATI RADEON video card, and 16x DVD-ROM, Floppy, and an old sound card I found in the garage, and PCI Ethernet (note sound card is NOT the problem).  I cannot boot anything that runs off of any variant of a Linux Kernel.  I cannot boot from CD/DVD: Puppy Linux CD, Ubuntu CD, and Ubuntu DVD.  The disks are fine, and they boot into the screen asking me how I want to boot (boot live CD in text mode, normal mode, install mode, disk integrity checker, etc.), but as soon as I try any of them, it gets stuck.  It tries to load the kernel, but it has a "Kernel Panic-Not Syncing!"  error message.  I have an MSI 951g combo motherboard, in case that helps.

Note: I am a heavy Linux/Open source user, and do not want to be stuck on Windows forever!!!  I know a pretty good amount about Ubuntu, and I have fixed a lot of installations, and installed it on a lot of systems, and have burned a lot of Live CDs.  I am not a beginner.

Thanks in advance!
:guitar:

---

### Post by nanotube on 2008-03-24
did you run a memtest? :)

---

### Post by uDanimal on 2008-03-24
I had similar issues with my spare.  I changed out the cdrom drive, and it is working fine.  The drive would work until I tried to boot livecd or run installer.  Its probably unrelated, but its an easy problem to find/fix.

---

### Post by jesusfreak107 on 2008-03-24
Yeah, that worked for me, too, I forgot to mention that.  However, that is a DVD drive, and we have no DVD drives available, and I do not have a job, so I cannot but another one.  Also, I was booting it off of an external USB 2.0/Firewire 16x Dual-Layer DVD-R/RW.  I also tried the internal.  Same result.

---

### Post by jesusfreak107 on 2008-03-24
Thanks, I did not think of that, I think I have Memtest installed on my computer.  It shows up in GRUB, but, with hy lifestyle, I would give it a 40% chance that it actually exists.  I thought the Memtest checked the RAM for errors.  My current peice of RAM is a WHOPPING 3 Days old.  I just bought it.  I ordered another identical peice last night.

---

### Post by nanotube on 2008-03-24
> **jesusfreak107 said:**
> Thanks, I did not think of that, I think I have Memtest installed on my computer.  It shows up in GRUB, but, with hy lifestyle, I would give it a 40% chance that it actually exists.  I thought the Memtest checked the RAM for errors.  My current peice of RAM is a WHOPPING 3 Days old.  I just bought it.  I ordered another identical peice last night.

precisely /because/ you just bought the chip, you should memtest it to make sure it's good. first thing you should do when you get a new ram chip, run it through memtest. can't tell you how many times (a few) that i tried a new chip and it turned out to be a dud.

iirc, there's a mem test option on the livecd, you can use that one (if it works... :) ).

---

### Post by jesusfreak107 on 2008-03-24
Okay, ran it through the Memtest (yes, it works on the CD, too).  The test did not get any errors... BUT:
the Memtest recognized the RAM as "FSB : 200MHz," and it is a 400MHz card.  does this have anything to do with it being DDRII?  Also, my motherboard is a hybrid, meaning it has the old, and the new hardware.  Here are it's capabilities.  As you will notice, it can support a lot of stuff, which I am thinking is the problem, it is getting confused:

Chip: Intel 915G, ICH6R
Memory(PROBLEM:) _***2xDDR, OR 2XDDRII(DUAL CH)(2GB MAX)***_
CPU: Socket 775.  FSB: 533/800. 
VGA: CHIP: OnDie (8x AGP). Port: x1
PCI: 3 slots
PCI-E: 1 x16, 2 x1 slots
SOUND: Intel ICH6R
LAN: Realtek 8110S (10/100/1000Mbps)
IDE: 1x100, 2x133
SATA: 4xSATA
USB 2.0: 6xUSB2.0 (now 4, two went bad)


I think it is getting confused because it can take both DDR, and DDR2 chips.  Any suggestions/corrections?

---

### Post by jesusfreak107 on 2008-03-24
Oh, and, by the way, the internal DVD drive is working now, I... had... pluggeditintothewrongslot...
heh heh...
It was plugged into the SATA, it is an IDE.

---

### Post by nanotube on 2008-03-24
heh well, good news about the dvd drive, at least. :) i suppose booting from it still doesn't work eh?

at this point all i can think of is to do a web search on your motherboard model + linux, and see if anyone else is reporting similar problems or workarounds.

---

### Post by jesusfreak107 on 2008-03-24
I am going to try booting off the the DVD drive, now, i'll bet the problem was I had a IDE object trying to communicate with Linux through a SATA connection.

---

### Post by nanotube on 2008-03-24
> **jesusfreak107 said:**
> Okay, ran it through the Memtest (yes, it works on the CD, too).  The test did not get any errors... BUT:
the Memtest recognized the RAM as "FSB : 200MHz," and it is a 400MHz card.  

also, the fsb is /supposed/ to be at 200mhz, the 400 rating of the mem chip comes from its ddr2 type. see [http://en.wikipedia.org/wiki/DDR2_SDRAM](http://en.wikipedia.org/wiki/DDR2_SDRAM) for more info. :)

so that seems as it should be.

---

### Post by jesusfreak107 on 2008-03-24
Internal DVD drive will still not Boot the CD.  Same error.

---

### Post by jesusfreak107 on 2008-03-24
would it help if I booted off of an external HDD, maybe?

---

### Post by nanotube on 2008-03-24
> **jesusfreak107 said:**
> Internal DVD drive will still not Boot the CD.  Same error.

could you paste the complete text of the error that occurs? and maybe some lines leading up to it, too?

---

### Post by jesusfreak107 on 2008-03-25
YAY!!! I FIXED IT!!!!
I googled the motherboard, and Linux, as you suggested, and, tada, there WAS a problem between the two.  However, I figured out the solution as well.  All I had to do was add this to the boot line:
"boot:linux pci=nosort"   
And it works like a charm!  I have installed Ubuntu, and am writing from it.  GOODBYE, WIMPDOWS!!!  I have the special graphics effects turned up as high as possible, and it still runs super-fast.

---

### Post by nanotube on 2008-03-25
awesome, congrats! :) enjoy your ubuntu :)

---

