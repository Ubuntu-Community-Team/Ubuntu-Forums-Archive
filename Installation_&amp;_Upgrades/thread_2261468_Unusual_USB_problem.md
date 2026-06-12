---
title: "Unusual USB problem"
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by Brad wilkinson on 2015-01-19
So I have a bit of a story to tell that ends with an odd problem with USB devices.

I have been using 12.04 as my main PC basically since it was released, and never had any problems with the way it handled USB devices. This included all the legacy USB1/2 ports, and a recent USB3 PCIe add-in board that I use connected to a USB3-SDcard box to download video I have shot.

Anyway, this morning my PC decided to throw it's toys out of the pram (stop working). I eventually decided that the problem was either the motherboard or the HDD packing it in, so I went and purchased replacement parts to rebuild my PC.

So I put the new motherboard and the new HDD in the box with all the other parts, and then booted from a 8Gb USB2 drive with 12.04 on it. Then I installed 12.04 on the new HDD.

Since I was rebuilding anyway, I decided to upgrade to 14.04 while I was at it. So I set the machine to upgrade, after a reboot it looks like everything has worked out fine.

Except now it doesn't matter what I plug in to any of the USB ports, none of the devices are found (the USB drive, HDD's in portable chassis, the USB3-SDcard reader). Which is very odd, especially since the USB drive was actually used to boot from and then installed sucessfully to the HDD.

This is a dump of 'lsusb' from the machine:

bradley@UbuntuDesktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So you can see the various things in this list, and I can identify them. The trackman wheel is obvious, the Standard Microsystems hub/reader is my dell monitor, there is the motherboard USB3 and the add-in board USB3.

But anything I plug in after boot is not recognised.

What have I done wrong?

System Details:
AMD Phenom IIx6
Asus M5A78L-M USB3
8gig ram
2gig HDD
Gigabyte Radeon 5850 with 1gig vram

---

### Post by Brad wilkinson on 2015-01-20
ok, so I have done a little more investigating. I plugged in a v.old USB1.1 128Mb thumb drive and a USB2 8Gb thumb drive while the system booted.

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 002: ID 0951:1666 Kingston Technology 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

You can see them in the lsusb dump above, the JMTek is the USB1.1 device, and the Kingston Technology is the USB 2 device. So they show up if they are present at boot time.

bradley@UbuntuDesktop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bradley@UbuntuDesktop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 002: ID 0c76:0005 JMTek, LLC. Transcend Flash disk
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0424:2228 Standard Microsystems Corp. 9-in-2 Card Reader
Bus 001 Device 004: ID 0424:2503 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 003: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 003: ID 0951:1666 Kingston Technology 
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2109:3431  
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bradley@UbuntuDesktop:~$ 

Actually, they disapear, and show back up if you unplug them and plug them back in.

But I cannot find them in the file structure. They don't pop up a file window when inserted like they did on 12.04, and they don't show up in the LH column of the file directory window along with "home" and all the others either.

Also a BIOS question:

Is Ubuntu Linux 14.04 a "plug-and-play" OS for the purposes of the boot sequence? i.e. in the BIOS where it has a setting to let the BIOS fully configure the system or to hand over early to the OS and let it do the device configuration, should I leave it as a legacy BIOS-does-the-configuration or should I change it so that the OS does the configuration.

All help greatfully appreciated!

---

### Post by Brad wilkinson on 2015-01-20
So I've done some more googling and came across two pages that looked relevant:

**_One:_**
[https://help.ubuntu.com/community/Mount/USB#Seeking_Further_Help](https://help.ubuntu.com/community/Mount/USB#Seeking_Further_Help)

I looked at the Automounting -> Configuring Automounting section, then opened dconf-editor and browsed to the two mentioned locations. Automount and Automount-open are both already set to true, and thus nautilis should mount and open a folder containing any USB drives attached to the system.

But it doesn't. Even after rebooting.

**_Two:_**
[http://askubuntu.com/questions/285539/detect-and-mount-devices](http://askubuntu.com/questions/285539/detect-and-mount-devices)

I looked at Solution 1 and both devices (the 128Mb and 8Gb drives) were both set with automatic mount options set to "on".

Despite both of these settings, (and considering that lsusb shows the system can see the devices just fine) nothing opens in Nautilis like it is supposed to.

I was wondering if perhaps my user doesn't have the correct permissions to see the devices? If so, how do I change that?

---

