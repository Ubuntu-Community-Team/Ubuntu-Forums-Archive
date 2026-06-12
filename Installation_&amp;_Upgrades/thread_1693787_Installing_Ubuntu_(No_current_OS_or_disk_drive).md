---
title: "Installing Ubuntu (No current OS or disk drive)"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by 138 on 2011-02-23
Hi guys,

I'm a total beginner here so sorry if I'm asking a stupid question but I can't seem to figure it out or find any answers anywhere else.

I bought a laptop and the previous owner must have completely wiped the harddrive before I got it (I.E When I turn it on it says "No os installed") 

I have no disk drive, so I downloaded the Ubuntu 10.10 ISO and put it on an empty partitioned external harddrive (partitioned a 30gb FAT32 for Ubuntu) and changed the boot order to boot from USB only, but when I try that nothing happens, the screen just says "missing operating system". 

Any ideas folks? Any help would be greatly appreciated.

---

### Post by Quackers on 2011-02-23
Did you change the boot order in the bios to USB flash drive, or USB HDD. Check that first.

---

### Post by 138 on 2011-02-23
Hey Quackers, thanks for the reply. Yep, I did that but to no avail.

---

### Post by Quackers on 2011-02-23
Ok, a couple more questions :-)
Is there a hard drive in the laptop already?
And, how did you put the iso file on to the USB HDD?

---

### Post by 138 on 2011-02-23
There's no harddrive in the laptop at the moment, I took it out and connected it to another netbook to put a copy of Ubuntu on it, and now just booting it from USB.

---

### Post by 138 on 2011-02-23
I have a USB SATA caddy, I just put it into that, btw.

---

### Post by Quackers on 2011-02-23
Sorry, but I'm not clear on this.
Is the USB HDD that you are trying to boot from, the original HDD from the laptop?

---

### Post by 138 on 2011-02-23
Yep, I guess I should just try sticking it back in the laptop right?...

---

### Post by Quackers on 2011-02-23
I see no reason for removing it. What can be done from a caddy can be done from inside the laptop.
Does your laptop support booting from usb flash drive? Do you have a 2GB or bigger usb flash drive?

---

### Post by 138 on 2011-02-23
I only took the drive out because I lost my flash drive so it was the only way of getting the file on. A roundabout way of doing thing, I know! :)

It gives me the option to boot from usb in bios so I presume the laptop is capable of it, it's only maybe a year or so old.

---

### Post by Quackers on 2011-02-23
USB yes, but USB what? :-) Basically if you have no cd drive and no flash drive, I think you're going to struggle installing Ubuntu to the drive.
You didn't answer a previous question. How did you put the iso file on to the drive please?

---

### Post by 138 on 2011-02-23
I just downloaded the .ISO file and drag & dropped it onto the FAT32 partition.

> Basically if you have no cd drive and no flash drive, I think you're going to struggle installing Ubuntu to the drive.

So does there need to be a harddrive in the laptop already, and boot from another external source (say another harddrive or USB key)? I thought I would be able to just have the .ISO on the harddrive and boot from that?

---

### Post by Quackers on 2011-02-23
No, that's not the case. What happens is this.
The iso file is basically an image of a cd. That image must be burned (as an image - not a file) to a cd/dvd or usb flash drive.
Then after changing the boot order in bios, you boot from the cd/dvd or usb flash drive and the "cd" begins its work. After a minute or so you should get a screen asking whether you want to "try Ubuntu" (which is like running a temporary Ubuntu desktop, to make sure everything works ok) or "install Ubuntu", which will install Ubuntu to your hard drive.
When the installation is run, it will want to reboot, when you can take out the cd/dvd or usb flash drive and, hopefully, reboot from your new hard drive installation.

---

### Post by 138 on 2011-02-23
Ok, reading that I reckon the mistake may have come from the ISO end of things.

Can you run me through how to correctly burn the ISO as an image to the harddrive? Or else if you know of a thread or tutorial that you can direct me to that'd be great too.

---

### Post by Quackers on 2011-02-23
It is pointless to burn the iso image to the hard drive unless you have a spare hard drive to use as an external boot device (and I've never done that, so am unsure whether that would work, but I suspect it might).
Normally the image is burned using an existing operating system (or a separate computer) to a cd/dvd or usb flash drive. If it is a Windows system, ImgBurn can be used for that purpose.

---

### Post by 138 on 2011-02-23
I have a second netbook and a second external harddrive I can use if I need it.

So the right order of things would be to burn the ISO disk image using second laptop and the program ImgBurn to the external harddrive, and try boot that I guess. I'll give that a go.

Thanks for all the help so far! Hopefully I'll get it to work. :)

---

### Post by Quackers on 2011-02-23
That's definitely worth a try. Presumably the other laptop is using Windows. ImgBurn is a free program and has worked well for me.

---

### Post by oldfred on 2011-02-23
Note that the normal installs of the ISO to a flash drive reformat entire drive. So if using hard drive, it will probably reformat the entire thing. But even though FAT partitions can be larger the installer only creates a max of 4GB FAT partition.

If you have another Ubuntu install you can install grub2 to the same drive as you copied the ISO and grub2 will directly boot the ISO (loop mounted). It is a little more work to set up and requires some manual edited of grub.cfg on the drive. (not really for beginners)

Info if interested:
Hard drive:
Boot ISO from harddrive. To install it would have to be different partition

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

