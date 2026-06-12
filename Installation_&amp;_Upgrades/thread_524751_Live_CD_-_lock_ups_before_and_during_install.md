---
title: "Live CD - lock ups before and during install"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by ecowarrior on 2007-08-13
Hi all

I'm using a PC I've basically (re)built myself over time, with various upgrades etc.  It's getting on a bit but basically it's got an AMD64 3000 on a Foxconn something-or-other mobo (NVIDIA3), with 2x512Mb RAM.  Two hard disks and a ton of fans to keep everything cool.  Video card is a NVIDIA FX 5500 and it's got a soundblaster card in there too.

Windows XP is on it on one hard disk and it's rock solid.

I have the 7.04 live cd.  If I boot off that, and it starts up OK, then after a while it just locks up.  Solid.  Frozen.

I looked up some suggestions and I thought I was getting an improvement by modifying the startup options using noirqdebug and noapic and starting in safe graphics mode, but still locked up after a while.  I also found that if I tried to actually install it (boot up, run the INSTALL icon), it would get to the partitioning option and lock up at 6%.  Tried this two or three times, always 6%..  Not sure if this is any kind of clue or a complete red herring.

I'm a bit of a newbie at Linux, and I'm not sure really what logs etc. to look at for help, or any other options to try.

Help?

---

### Post by dabl on 2007-08-13
If memory serves, that Nvidia3 motherboard chipset has been a cause of trouble for others, so I dunno about that one.  Otherwise, your hardware should work.

2 suggestions to get around issues with the Live CD:

1. Download and burn yourself a GParted Live CD, to use for all things partitioning-related.  It comes from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

While it is true that a version of GParted is on the Live CD, I've always found it more straightforward to deal with the partitioning as one thing, and the installation of the OS on the partitions as the other thing.

2. You might have better luck installing with the Alternate Install CD.  In other words, the Live CD tries to do everything in GUI mode and sometimes gags on the video hardware, where the Alternate CD uses VGA/text mode and you can get your OS installed as you want it, and then deal with the video display.

Good luck!  :)

---

### Post by ecowarrior on 2007-08-13
OK, sounds like a reasonable set of suggestions.  Thanks!

---

### Post by ecowarrior on 2007-08-13
Touch lots of wood, I seem to have a fairly stable installation for once.

As suggested I downloaded the text-install version of the install, and decided to risk the 64-bit one this time.

Installed fine, but when started up the usual lock ups occurred.

So if anybody else finds this thread, hopefully you'll find the following useful, this is roughly what I did:

Boot up and when X starts to Ctrl-Alt-F1
sudo /boot/grub/menu.lst

To the end of the relevant "kernel" line I added:

noapic nolapic acpi=off

Reboot.

sudo apt-get install update
sudo apt-get install upgrade

I then installed the latest NVIDIA driver using albertomilone's envy script.

When booted up and into X, more updates were reported.  Took them which I think updated my kernel.

Once rebooted, I realised my extras on the end of the kernel like in menu.lst weren't there, so repeated the steps above to add noapic etc... to the end of the new kernel line.

Rebooted, and all is well.  Installed "beryl" (I wanted to see what all the fuss is about) and the system has been running for about 15 minutes and all seems well, whereas before it was consistently locking up after about 20 seconds!

Cheers all

---

