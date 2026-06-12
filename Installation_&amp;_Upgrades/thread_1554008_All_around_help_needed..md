---
title: "All around help needed."
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by triunenature on 2010-08-16
To start off, i am attempting to install ubuntu server 10.04 on a computer i just built.  And am having the worst time ever getting this to work.  Note, I've used ubuntu for a few years now on plently of different systems, never had this much trouble.

The first thing i tried was using a usb thumb drive to install, only resulting in a "boot error" (no more information to give, because that was the entire output, after the computer loaded and attempted to boot to the usb).  Later i found the problem to be that my bios only accepted usb-zip not usb-hdd.  I tryed to format my usb-hdd to mimic the usb-zip geomatry... lets just say that failed beyond imagination.

Next i took my hard drive out of my new computer, placed it in my older one, and installed the server via my old computer (which happens to run ubuntu-desktop).  And then placed the hard drive back into the new computer.  That got me to the grub recovery screen, but alas i couldn't get ubuntu to boot.

Next i bought (and planning on returning) a usb-cd drive, and attempted to install ubuntu via that... made the cd, booted to it, via my old computer, did a cd check, and it passed.  so i threw it into my new, usb-cd drive and i got (after the initial install screen - chose english - install ubuntu):

```
udevadm settle - timeout of 180 seconds reached, the event queue contains:
   /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0/block/sda (80 *moves out of screen, so i can't read it*
   /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0/block/sda/sda *moves out of screen*
(805)
   /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0/block/sda/sda *moves out of screen*
(806)
   /sys/devices/pci0000:00/0000:00:1f.2/host2/target2:0:0/2:0:0/block/sda/sda *moves out of screen*
(807)
[  211.313389] Kernel Panic - not syncing: Attempted to kill init! 
```

The boot options for my computer are:

Hard Disk
USB-ZIP0
CDROM
USB-CDROM
Legacy Lan

I am willing to try any method to install the ubuntu server on my computer.  If you want more detail on any of my previous install attempts please ask.  If you know a cool alternitive way to install, PLEASE tell me.

As for other systems, i have 2 other computers running ubuntu, one dual boots to windows xp (so i can play video games!!!).  I have a cd/dvd drive/burner on one of the computers.  I also have a usb-cd drive.(duhh)

The computer in question, currently has a 500G drive on it (will be upgraded to 5T after install is compete), 2G ram, Intel core Duo processer, and some cheap *** graphics chip (not that it should matter because this computer will never see the wonder of graphics.. i only use CLI with my servers..

Thank you for reading all of this, and please, i am willing to go for a hail mary!

Thanks again!

---

### Post by mörgæs on 2010-08-16
Have you tried other versions than 10.04?

---

### Post by triunenature on 2010-08-17
> Have you tried other versions than 10.04?
8.04 LST( i really prefer long term support) server
8.10 server and desktop (just happened to have a desktop cd around)
9.04 server and desktop

Update** I tried with a cf card, failed.  Same error message as the usb-hdd. I'm thinking not a coincidence....

Update** Using a cd, i got the system to install to my flashdrive.  Soo my multiteribyte system, is currently working on 8 gigs of SSD.  Which is by the way completely useless... but at least i am making progess.  So the problem is NOT fixed... but maybe the fact that it was able to install to my usb drive, is a clue....

---

### Post by mickwombat on 2010-08-17
You may be stuck with the only option being a pxe network install.
It's frustrating, but sometimes these things just don't work for reasons unknown.

Have a look at the guide here, [https://help.ubuntu.com/community/Installation/Netboot]("https://help.ubuntu.com/community/Installation/Netboot") and once you set everything up, boot the PC up choosing 'boot from dhcp' or whatever.

The PC will load up the Netboot image, which will then download the appropriate files from the internet.

I've tested on some VMs and it works nicely, though a bit of a pig to set up.

Good luck

;-)

---

