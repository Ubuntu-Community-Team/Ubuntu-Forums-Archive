---
title: "HP LaserJet 3300 scanner not found"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by brett.ras on 2010-11-30
Hello,
I've got an HP LaserJet 3300 all-in-one that I can't seem to get working as a scanner.  Printing and copying work fine, but not the scanner function.  I'm running kubuntu 10.04, but my guess is that kubuntu vs. ubuntu doesn't matter here.

I'm using an IEEE-to-usb cable to connect the device to my box.  When I first plug it in, cups recognizes it, and I see a popup in the lower right of my screen entitled "printer applet" and saying "configuring new printer".  Then it says "hp-laserjet-3300-3310-3320 is ready for printing".  After this, printing works fine.

But no scanning.  lsusb doesn't see the device:

[brett@grox:~]$ lsusb
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:0808 Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sane-find-scanner says "no usb scanners found".

I've tried this: 

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

which didn't work but led me to the following idea:

I uninstalled all the hplip pacakges I had installed, downloaded hplip afresh from hp, and reinstalled it from the command-line: "sh hplip-3.10.9.run".  It installed a bunch of extra packages from the ubuntu repos, including the one it said was required for the scan function.  Then it told me to unplug and re-plug-in the usb cable.  As I did, the cups notifications came up again as I described above.  That happened in separate windows right as the hplip installer was launching hp-setup for me.  I run hp-setup and get the error "no devices found on bus: usb" after hitting "next" on the "device discovery" screen.

So my guess is that maybe hp-setup would see it if it got recognized as a usb device.  I tried stopping the cups daemon, deleting the printer in system settings, and re-plugging in the usb cable, just in case it was cups that was catching it and somehow preventing it from being seen as a usb device.  It still isn't found by either lsusb or hp-setup.

I also get this at the start of hp-setup, which is interesting but I don't know what it means or if it's relevant:

QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/brett/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon

This is also interesting, from dmesg as I plug it in:

[ 8694.260081] usb 5-1: new full speed USB device using ohci_hcd and address 4
[ 8694.428354] usb 5-1: configuration #1 chosen from 1 choice
[ 8694.469195] usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x067B pid 0x2305
[ 8695.753424] usb 5-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

And then in dmesg after I hit "cancel" in hp-setup, which gives a segfault:

[ 8759.141727] python[23425]: segfault at 0 ip (null) sp bfca48ac error 14 in python2.6[8048000+1e0000]

Don't know if any of that stuff is relevant.

Can anyone give me any guidance?

Thanks in advance for any help.

---

### Post by brett.ras on 2010-12-04
Ok, I just noticed something that might change the whole nature of my question (maybe it was obvious to those more knowledgeable than I):

I didn't see any printer or scanner in my lsusb output, but on a whim I tried unplugging my all-in-one's usb cable and doing another lsusb to see if any of the devices listed disappeared.  Lo and behold, there was one:

Bus 005 Device 007: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port

So the printer-to-usb cable shows up as a PL2305 Parallel Port.

I'm assuming this means that my device doesn't really show up as a usb device to the operating system at all, but a parallel-port printer.  Is that correct?

If so, can I even use HPLIP at all, since it doesn't seem to support parallel printers?  Is there a way to use the HPLIP driver on this device so that I can get scanning capability?  Or is there some other approach to this?

Thanks.

---

### Post by oldsoundguy on 2010-12-04
go to synaptic via system and search for and install sane .. that is the scanner front end driver.

---

### Post by brett.ras on 2010-12-06
Thanks for the reply.

I've had xsane and libsane installed since the beginning, and I've been trying to get sane to recognize the scanner using sane-find-scanner.

But I just looked, and sane itself wasn't installed.  I installed it and nothing seems to have changed. I open up xsane, and it says "no devices found".  sane-find-scanner doesn't see anything either.

---

### Post by brett.ras on 2010-12-10
Anyone have any ideas?  I'd sure appreciate it.

---

