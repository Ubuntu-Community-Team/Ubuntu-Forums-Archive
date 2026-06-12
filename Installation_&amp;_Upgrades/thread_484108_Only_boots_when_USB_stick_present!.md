---
title: "Only boots when USB stick present!"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by crimson on 2007-06-25
I just installed Ubuntu Feisty using the mini.iso on a USB stick. The installation seemed to go well, and I chose to completely erase and repartition the hard drive, as I don't need dual boot.

On restarting, I was greated only with an "Error loading operating system" message. So I went to reboot with the USB stick again and instead of the installer, it automatically started up my new installation on the hard drive! So everything works great, except that I can't directly boot the hard drive -- which is bit of a PITA.

Any ideas what could be wrong with the hard drive format, and what I could use to fix it? The machine is a Dell Precision 470 with an 80 GB SATA hard drive, if that makes a difference. I've no previous experience with the machine; I'm on site on a contract and just trying to set up a workstation on the hardware they've given me. If I have to reformat, that's okay, as I haven't set much up yet, but I'd like to know what to do differently next time to avoid the problem.

Thanks!

---

### Post by cam_tram on 2007-06-25
If you erased the hard rive, then there is no operating system installed i.e. nothing to boot.  Your computer boots when the USB stick is plugged in because thats where the OS is stored.

---

### Post by crimson on 2007-06-25
> **cam_tram said:**
> If you erased the hard rive, then there is no operating system installed i.e. nothing to boot.  Your computer boots when the USB stick is plugged in because thats where the OS is stored.

No, I did install the OS onto the hard drive (after erasing it). It's all there; it's only the boot record or something of that sort that seems to be messed up.

---

### Post by happysmileman on 2007-06-25
Try installing grub onto that drive... If that doesn't work it may be missing an important file for GRUB which you could then copy from USB stick to PC

---

### Post by timcredible on 2007-06-25
did it install the boot stuff on the usb stick instead of the mbr of the hard drive?

---

### Post by joe.turion64x2 on 2007-06-25
Forgive my ignorance but, in order to boot from an ISO image, is it enough to copy the image to an empty USB stick (FAT32 formatted), set the parameters in the BIOS to boot from USB, and restart?

Thanks.
Joe.

---

### Post by crimson on 2007-06-25
> **happysmileman said:**
> Try installing grub onto that drive... If that doesn't work it may be missing an important file for GRUB which you could then copy from USB stick to PC

Thanks! That seems to have done it. I noticed the menu.lst file had lines "root (hd1,0)", when my actual setup had the drive as (hd0,0). I suspect that, when I booted from the USB stick, it may have been mounted as hda0, and the hard drive as hda1, so the grub menu was built incorrectly. And perhaps it wrote the MBR to the wrong drive as well (as timcredible suggests).

So, in case anyone else runs into this, what I did was:

1) Edit the /boot/grub/menu.lst file to change (hd1,0) to (hd0,0)
2) sudo grub
3) root (hd0,0)
4) setup (hd0)
5) quit
6) reboot  # without USB stick! hurray!

Actually, I didn't do step 1 initially, and while I got to the boot menu, I got stuck because the root line was wrong. I was able to edit the root line on the fly to complete boot up, and then fix it permanently once I got back to the desktop.

---

### Post by crimson on 2007-06-25
> **joe.turion64x2 said:**
> Forgive my ignorance but, in order to boot from an ISO image, is it enough to copy the image to an empty USB stick (FAT32 formatted), set the parameters in the BIOS to boot from USB, and restart?

Thanks.
Joe.

You need to copy the contents of the ISO image onto the stick. For the mini-ISO, copy all the files into a directory called syslinux. I'm not sure about the full image.

More info here: [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by girasquid on 2007-06-25
Could this be a BIOS issue, too? I remember having systems setup to boot from CD that would mysteriously break on startup if there wasn't a CD that they could boot off of present.

---

### Post by crimson on 2007-06-26
> **girasquid said:**
> Could this be a BIOS issue, too? I remember having systems setup to boot from CD that would mysteriously break on startup if there wasn't a CD that they could boot off of present.

No, I don't think so. Once I (re)installed grub on the hard drive, it booted fine. To boot from the USB stick, I had to hit F12 at startup to get into the boot setup screen and select it each time I wanted to start from the stick. It was just a one-time setting; it reverted to the hard drive on the next startup.

---

### Post by joe.turion64x2 on 2007-06-26
> **crimson said:**
> You need to copy the contents of the ISO image onto the stick. For the mini-ISO, copy all the files into a directory called syslinux. I'm not sure about the full image.

More info here: [Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
Thanks for the hint, I really stop myself burning CDs/DVDs for whatever Linux that comes out the door. I wonder, using that method, if I change settings of the 'liveCD', would changes be saved?

---

### Post by bitumen on 2007-07-11
I  am  here to say that it is not an isolated incident related to incorrect installation from a flash drive.

similar situation through partitioning and formatting using live CD

 after installing 7.04 to a western 80 gig hard drive last week (first experience with Linux) 

I had decided to use it as my OS of choice 

due to the previous weeks hacking, installing and removing software 
and the few times I was able to crash the system decided to play safe and add second hard drive
for home(files and back up software and script that I didn't want accidents happening to):) 

purchased new Seagate Sata 250 gig 
partitioned it to 
1 gig swap file
140 gig home                                                 
40 backup 

 and then reformat and installed ubuntu 7.04 to the 80 gig hard drive and made it boot able 
which then add the sata drive as the home folder and backup 

yahoo exactly what I wanted 

after installing restarted on the new install

frozen at intel's bio's screen (wtf)

after testing by resetting with live cd and floppy and various configurations to the bio's setting
still couldn't get past bio's screen 

in desperation and luck inserted a pen flash drive - 
**NOTE** at no time during the install or the formatting was the pen drive connected 

so much to my surprise and a lot of relief that grub boot loader showed and 3 seconds later ubuntu loaded 

to cut this short

tested with empty flash i.e. 0 kb used and I can boot from all drives 

without the flash drive-- can not get passed bio's configuration 

Run the procedure on last page and it has fix that problem

thanks

---

### Post by ceekay on 2008-01-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/181908](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/181908) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I ran across this post while looking for examples of other people having this problem. Sorry to bump this old thread but I figured it might help others looking for answers.

I have run across the same problem and the workaround is to remove the pendrive as soon as it gets to the "loading additional modules" stage. Otherwise it loads the usb storage module before your hard disk and your /dev/sda and /dev/sdb are swapped from how they are when you reboot.

My mailing list posts

[https://lists.ubuntu.com/archives/ubuntu-installer/2007-December/000131.html](https://lists.ubuntu.com/archives/ubuntu-installer/2007-December/000131.html)

---

