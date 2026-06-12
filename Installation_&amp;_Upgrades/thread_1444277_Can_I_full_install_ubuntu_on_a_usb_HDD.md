---
title: "Can I full install ubuntu on a usb HDD ?"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by Wanas on 2010-04-01
I want to install ubuntu to a usb HDD to take all my data and my own OS configuration every where, I tried to fully install ubuntu on my 4GB flash but it failed to boot after the grub menu, I tried to install it using unetbootin but when I restart the computer all my configuration gone its like a LIveCD.

So my question is Can I make a full installation on a USB HDD?

---

### Post by bigsmitty64 on 2010-04-01
I believe this is what you need:  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Good luck!
[ ]("http://www.pendrivelinux.com/")

---

### Post by eksasol on 2010-04-01
I run Ubuntu from USB drives all the time, both from USB thumbdrives and microSD cards in USB reader.

It has to be some problem with GRUB not installing or configured correctly on your USB drive. During installation wizard, the part where it ask where to install bootloader, you need to select the USB drive, because it might point to your internal harddrive. Also here is how to install GRUB manually to a drive: [Recover Grub 2 via LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

If you want to make a liveUSB that save settings, you need to use the "System -> Administration -> Startup Disk Creator" . You might get problems with this such as installing too many updates and might stop working, so I still recommending installing the full operating system.

---

### Post by simon_w on 2010-04-01
Yeah, you can definitely do this - I've done it many times.  I actually use the vmdk method to boot my usb stick under virtualbox, so I can install / configure / generally fiddle with it while I'm doing other stuff on my main OS.

Don't know why you were having trouble with grub, but it can be a finicky thing sometimes.  if you have specific problems, post them here and I or someone else will surely be able to help you.

There are many methods, of course, and the UUnetbootin and Ubuntu's own "Startup Disk Creator" are often good choices.  Pendrivelinux has many different methods too.  Like eksasol, however, I much prefer having a full install on my stick, though.

Which leads me to a question:

My experience has been that when I use the full install method, and run a full ubuntu installation from my USB stick, the performance is not good.  In particular, I get frequent brief lock-ups.  If I use the "USB Startup Disk Creator", for example (same stick, same ISO), the performance is noticeably better.

Can anyone else confirm this from their own experience?  Does anyone have any suggestions as to what the difference might be?

I've been wondering about some standard SDD optimization tricks (moving /tmp in to RAM, using the noop ioscheduler, etc.) - anyone think this'll help?  Does the startup disk creator do this?

---

### Post by C.S.Cameron on 2010-04-01
This is how I made a Unetbootin install to 4 GB flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw", (optional)
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

