---
title: "Help install - broken int. CDdrive - int. Floppy - ext. usb CDRW drive"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by frafu on 2007-03-29
Hello,

A friend of mine has an old Acer laptop and he would like to try Xubuntu on it. 

As the cd drive of the laptop is broken, could you please help us with the installation Xubuntu? 

The laptop also has a working floppy disk. Other devices that might be of help: 
- external CDRW drive from HP with an usb connection 
- dlink dwl122

For the moment, the laptop has Windows 98.

Would it be possible to prepare a floppy disk, from which we can boot the laptop and start the installation. I suppose that this floppy disk should also have drivers for the cdrw from HP. 

Any help about how to proceed and where to find the necessary software to put on the floppy disk will be greatly appreciated. 

Thanks in advance. 

Francesco

---

### Post by pepsi_max2k on 2007-04-05
I'm trying to do the same kinda thing for the past couple of days. Broken CD drive and no floppy. Cept I don't have an external cdrw, just usb hd.

Here's some stuff i found, the stuff i've tried doesnt work, everything else i either can't do or is a bit too complicated...


Wubi. It's an exe to install from windows, but it must be XP (so no good with 98 like i've got)
[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

Instlux. Another exe from windows, I don't know if it should work with 98 or not but i tried and it just installs, reboots, loads windows then uninstalls itself. that's it.
[http://sourceforge.net/projects/instlux/](http://sourceforge.net/projects/instlux/)

PXE boot.
[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows](http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows)
If you can boot from pxe (network thing..) you can install via a tftp server. i can't, so not an option for me.

Netboot install.
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
Tried this with both the suggested files (for ubuntu) and some ones i thought mightbe better to install xubuntu, and after the loadlin command i just get a "RAMDISK: Incomplete write (28672 != 32768)" error. dunno if it's memory related or bad instructions or old programs or a prob with my laptop...

Network install
[http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive](http://efod.se/blog/archive/2006/11/29/installing-ubuntu-on-a-machine-with-no-cdrom-drive)
You need to config stuff like tftp and dhcp servers, and it doesnt really say how to do the latter and i'd rather only spend time figuring out how to install ubuntu, not a million other things. i already do t6hat far too much with suse...

Grub install
[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)
You need to repartition disks / learn to use grub for this. then it's mucht he same as the netboot one, which i've already found doesnt work for me...

Usb install
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
If you can boot from usb, great. Again, I can't.

Other methods...
[https://help.ubuntu.com/community/Installation/](https://help.ubuntu.com/community/Installation/)
I've tried a few. so far no luck.


Preferably I'd just like to stick a floppy in, have it load network card drivers / start network install, then do everything else over the net. I can do this with other distro's, just seems a lot harder to do with ubuntu :(

---

### Post by Nepherim on 2007-04-19
Unfortunately I had the same experience -- pretty much seems to be impossible to install from floppy. Recently I came across [this installation guide]("https://help.ubuntu.com/community/InstallingXubuntu")  for xubuntu, and it looks promising. What I'm going to try and do is boot another flavor of *nix from the floppy, and then launch the install server from the CD. Who knows, maybe that's work.

 ~ ~ Dave

---

