---
title: "Dvd drive not detected on karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by vocs on 2009-10-26
Hello,

I installed ubuntu karmic 9.10 with a usb pen drive on my laptop. Unfortunately my dvd drive isn't detected by ubuntu but it's working fine under windows. It also worked with previous versions of ubuntu. However it isn't detected by ubuntu karmic now. Ubuntu created automatically the directory /media/cdrom0 but there's nothing about that in my /etc/fstab. What should I do?

---

### Post by fancypiper on 2009-10-27
Assuming you have cdparanoia installed:
Open a terminal and command:
cdparanoia -vsQ
Post the results here

---

### Post by vocs on 2009-10-27
With "cdparanoia -vsQ" I obtain "No such file or directory" for everything except this:

Checking /dev/sg0 for cdrom...
	Testing /dev/sg0 for SCSI/MMC interface
		Could not access device /dev/sg0 to test for SG_IO support: Permission denied
		no SG_IO support for device: /dev/sg0
		Could not access device /dev/sg0: Permission denied
		generic device: /dev/sg0
		ioctl device: not found
		Could not open generic SCSI device /dev/sg0: Permission denied
	Testing /dev/sg0 for cooked ioctl() interface
		/dev/sg0 is not a cooked ioctl CDROM.


If I run "sudo cdparanoia -vsQ" I obtain:

Checking /dev/sg0 for cdrom...
	Testing /dev/sg0 for SCSI/MMC interface
		SG_IO device: /dev/sg0
		Drive is neither a CDROM nor a WORM device

	Testing /dev/sg0 for cooked ioctl() interface
		/dev/sg0 is not a cooked ioctl CDROM.

---

### Post by fancypiper on 2009-10-27
That's strange, I have never seen one not supported. Do you know the make and model number of the drive?

---

### Post by vocs on 2009-10-27
My dvd drive is supported by all the older versions of ubuntu. My laptop is four years old and I tried several versions of ubuntu before.

---

### Post by vocs on 2009-10-27
I don't know where to find the model of the dvd drive...

My laptop is a Dell Inspiron 6400/E1505 with a Sony 8X DVD +/- dual layer recorder.

---

### Post by fancypiper on 2009-10-27
Did you install with that drive or do the network upgrade?

What is the result of this?:

sudo lshw | less

Scroll until you find something like this:

        *-cdrom
             description: DVD-RAM writer
             product: DVD A  DH20A1P
             vendor: ATAPI
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             logical name: /media/cdrom0
             version: 6X16
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready

---

### Post by vocs on 2009-10-27
I installed ubuntu by an usb pen drive (with the standard ubuntu iso in it) and it was the first time that I installed it in this way.

I've run "sudo lshw | less" but there is nothing about my cdrom drive.

---

### Post by phillw on 2009-10-27
> **vocs said:**
> Hello,

I installed ubuntu karmic 9.10 with a usb pen drive on my laptop. Unfortunately my dvd drive isn't detected by ubuntu but it's working fine under windows. It also worked with previous versions of ubuntu. However it isn't detected by ubuntu karmic now. Ubuntu created automatically the directory /media/cdrom0 but there's nothing about that in my /etc/fstab. What should I do?


[https://bugs.launchpad.net/ubuntu/+bug/451668](https://bugs.launchpad.net/ubuntu/+bug/451668)

Have you got the latest RC ?

This, with a couple of other 'auto-mount' issues was late being fixed.

Phill.

---

### Post by vocs on 2009-10-27
> **phillw said:**
> [https://bugs.launchpad.net/ubuntu/+bug/451668](https://bugs.launchpad.net/ubuntu/+bug/451668)

Have you got the latest RC ?

This, with a couple of other 'auto-mount' issues was late being fixed.

Phill.

I installed ubuntu beta and I constantly updated it until now, so I have the rc. Isn't there any other solution than reinstalling it?

---

### Post by phillw on 2009-10-27
> **vocs said:**
> Hello,

I installed ubuntu karmic 9.10 with a usb pen drive on my laptop. Unfortunately my dvd drive isn't detected by ubuntu but it's working fine under windows. It also worked with previous versions of ubuntu. However it isn't detected by ubuntu karmic now. Ubuntu created automatically the directory /media/cdrom0 but there's nothing about that in my /etc/fstab. What should I do?

There is one suggestion here.

[http://ubuntuforums.org/showthread.php?t=1302603](http://ubuntuforums.org/showthread.php?t=1302603)

That area is for 9.10 - I'm sorry I can't help you further, I'm just about to start 'playing' with the RC in Live Mode in readiness for Thursday. I have a LAMP server, mod-security, 4 websites etc.. so have been holding back.

Regards,

Phill.

---

### Post by fancypiper on 2009-10-27
Are you fully updated?

# Upgrade and clean system
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

---

### Post by vocs on 2009-10-27
> **fancypiper said:**
> Are you fully updated?

# Upgrade and clean system
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoremove

Yes, I am fully updated.


@Phill: my problem isn't that I can't mount my dvd drive without being root, my dvd drive isn't detected at all.

---

### Post by fancypiper on 2009-10-27
I am out of ideas.

---

### Post by vocs on 2009-10-27
So you think that I should reinstall ubuntu?

---

### Post by MaindotC on 2009-10-27
did u properly shut down your machine in windoze?

---

### Post by vocs on 2009-10-27
> **strAlan said:**
> did u properly shut down your machine in windoze?

Yes, I did.

---

### Post by phillw on 2009-10-27
> **fancypiper said:**
> I am out of ideas.

Can u see the drive if you use a liveCD ?

i.e., can u boot a live cd from your drive ?

I'm also struggling here a bit .....

Phill.

---

### Post by vocs on 2009-10-27
> **phillw said:**
> Can u see the drive if you use a liveCD ?

i.e., can u boot a live cd from your drive ?

I'm also struggling here a bit .....

Phill.

Ok, now I start to download the ubuntu iso to try that.

---

### Post by phillw on 2009-10-27
Like I mentioned earlier ... I'm JUST about to try out RC on a liveCD disk on my system.

Burning the disk as I type this.

My questions are in this thread

[http://ubuntuforums.org/showthread.php?t=1303001&highlight=phillw](http://ubuntuforums.org/showthread.php?t=1303001&highlight=phillw)

You aren't the only one to have raised the matter of mounting / auto-mounting - and, as I replied earlier, some of the fixes were pretty close to 'freeze' time for the RC.

The bug whereby a LiveCD could actually change a system was..... well, un-settling .... thankfully that one is marked as resolved :D

Now, all I can do is [-o<

I'll say one for you :p

Hope not to be doing this for 3 years from here !!!

BTW, I've started a 'blog' - anyone is welcome to join in.

[http://www.vpolink.com/showthread.php?t=2880](http://www.vpolink.com/showthread.php?t=2880)

Usual forum rules, valid e-mail address, etc.

Phill.

---

### Post by VMC on 2009-10-27
Does lsusb show any devices attached? Example:

```
$ lsusb
Bus 001 Device 002: ID 046d:09c1 Logitech, Inc. QuickCam Deluxe for Notebooks
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``` Shows my webcam on device 2.

---

### Post by vocs on 2009-10-27
Yes, this is what I get:

```
$ lsusb 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 005 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by VMC on 2009-10-27
I'm sorry, I mis-read the first post. I thought your dvd drive was a usb type. 

BTW - What type is it? IDE, SATA?

```
wodim -checkdrive
``` , should find your CD.DVD drive, if it detects it.

---

### Post by vocs on 2009-10-27
> **VMC said:**
> I'm sorry, I mis-read the first post. I thought your dvd drive was a usb type. 

BTW - What type is it? IDE, SATA?

```
wodim -checkdrive
``` , should find your CD.DVD drive, if it detects it.

This is what I get by running "wodim -checkdrive":

```
Device was not specified. Trying to find an appropriate drive...
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
```

I don't know if my drive is IDE or SATA...

---

### Post by vocs on 2009-10-27
> **vocs said:**
> Ok, now I start to download the ubuntu iso to try that.

Since I don't have any cd right now, I loaded the latest ubuntu rc live iso with my usb pen drive and it doesn't detect my dvd drive...

---

### Post by VMC on 2009-10-28
> **vocs said:**
> Since I don't have any cd right now, I loaded the latest ubuntu rc live iso with my usb pen drive and it doesn't detect my dvd drive...

I know. Boot using Windows and look under hardware devices to see what the drive is, what type, how its attached, etc.

---

### Post by vocs on 2009-10-28
> **VMC said:**
> I know. Boot using Windows and look under hardware devices to see what the drive is, what type, how its attached, etc.

My dvd drive is a Sony DVD RW DW-Q58A, it is IDE and its firmware is called UYS4.

---

### Post by fancypiper on 2009-10-28
Google gives this as it's first hit.

[Sony Electronics drivers]("http://www.bioticaindia.com/sony-dvd-rw-dw-q58a.html")
Good luck!

---

### Post by 6205 on 2009-10-28
> **fancypiper said:**
> Google gives this as it's first hit.

[Sony Electronics drivers]("http://www.bioticaindia.com/sony-dvd-rw-dw-q58a.html")
Good luck!

That was not funny.. Anyway, seems like even in 2009 are very basic things not working in wonderfull world of free software.

---

### Post by 6205 on 2009-10-28
> **vocs said:**
> My dvd drive is a Sony DVD RW DW-Q58A, it is IDE and its firmware is called UYS4.

If i were you, i would try first flash latest BIOS and firmware.
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INSPIRONI6400/E1505&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INSPIRONI6400/E1505&os=WW1&osl=en&catid=&impid=)

It might help.. But i am skeptical regarding linux plug and play capabilities. It's not Windows :(

---

### Post by vocs on 2009-10-28
> **6205 said:**
> If i were you, i would try first flash latest BIOS and firmware.
[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INSPIRONI6400/E1505&os=WW1&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INSPIRONI6400/E1505&os=WW1&osl=en&catid=&impid=)

It might help.. But i am skeptical regarding linux plug and play capabilities. It's not Windows :(

I already have the latest firmware on my dvd drive and I updated my BIOS two years ago (unfortunately I can't do that now because I have problems with my battery). Anyway with my actual configuration the older versions of ubuntu were able to detect my drive without any problem. Isn't there a way to pick the driver I need from an older ubuntu and use it?

---

### Post by MaindotC on 2009-10-28
Absolutely.  The way you find out what modules are loaded is "lsmod".  Here's my output, looking for the module relative to my cd drive:
```

gosu@gosu-desktop:~$ lsmod | grep cd
cdrom                  37408  1 sr_mod
ehci_hcd               37900  0 
uhci_hcd               27024  0 
usbcore               146412  9 snd_usb_audio,snd_usb_lib,usb_storage,libusual,usbhid,gspca,ehci_hcd,uhci_hcd
gosu@gosu-desktop:~$

```

It looks to me like sr_mod is the driver used to communicate with my dvd drive.  Here's where modules are located:
```

gosu@gosu-desktop:~$ locate sr_mod | more
/lib/modules/2.6.24-23-generic/kernel/drivers/scsi/sr_mod.ko
/lib/modules/2.6.24-24-generic/kernel/drivers/scsi/sr_mod.ko
/lib/modules/2.6.24-25-generic/kernel/drivers/scsi/sr_mod.ko

```

You'll have to see what cd/dvd drivers Ubuntu uses, and those drivers will end in ".ko"  Then, try findind how to install different drivers.  Maybe Synaptic has modules if you just search for "module" and "dvd" in the same search.  Maybe linux-restricted-modules will be a package that will have what you need, but that's just a suggestion to get you in the right direction.  Please let me know if that helps.

---

