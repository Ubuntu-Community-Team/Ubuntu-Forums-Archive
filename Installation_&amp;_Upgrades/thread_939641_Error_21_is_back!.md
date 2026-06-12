---
title: "Error 21 is back!"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by ArcTrooper1773 on 2008-10-06
Hi all,

First off, apologies if I've posted this in the wrong forum.  I know how annoying it is, and I *think* this is the right place :)

I'm a student at university, currently in my second year.  As I have a lot of experience with computers (though unfortunately it seems to be the Micro$oft side of it), I'm generally the one my friends go to if they have a problem with their machine.  Today, it seems, is no different.

I received a phonecall from one of my friends rather later than I'd like last night, informing me that he'd completely formatted an external HDD (Western Digital *tuts*) and attempted to install Ubuntu 8.04 LTS.  Now, as far as I am aware, you *cannot* install an operating system on a USB hard drive (flash drive, maybe, but HDD?  Never heard of that working) because the USB cable can't cope with the data transfer rate (please, correct me if I'm wrong!)  The install went smoothly, as far as I can tell, and he now has a 40 gigabyte Ubuntu partition on a 250GB external drive.  Upon restarting, he enters his BIOS password for the machine, and the error 21 for GNOME appears.

My experience of Linux-based systems and dual-booting is at present very limited (I hope to learn some valuable information off of you guys, if possible! :D), but as far as I and [color=blue]G[/color][color=red]o[/color][color=yellow]o[/color][color=blue]g[/color][color=green]l[/color][color=red]e[/color] can tell, Gnome is an environment that allows you to choose which OS you'd like to boot into.

This seems to me to be a rather big problem, if I can't choose which I'd like.

At this point, I'd like to say that we have already looked at putting Linux on his machine - originally we would have liked to put it on the internal drive, but as the drive is partitioned into Windows-allocated drivespace and a 10 gig recovery partition, we couldn't alter the values without a third party partitioning tool (which I've become *very* wary of from past experience).

I suggested buying a larger hard drive and, using Acronis TruImage, cloning the drive with the same amount of space allocated to Windows (160GB +/- 5), with the rest of the space free to allocate to Ubuntu.  It seems he got a little excited and went ahead without me, and now we have said error.

I know it's a spiel, and if you've got this far, thanks for reading :)  Question is, can we restore the machine to Windows-only?  Any help would be greatly appreciated, as a very paranoid friend's university work is at stake! :P

***EDIT***

After looking a little more on our DEAR AND GLORIOUS LEADER, I've discovered that Error 21 seems to be a "missing drive".  Does this mean I'm right, and an OS really *really* can't be installed on an external HDD?

Does this mean the sinking feeling in the pit of my stomach's also right, and the only way forward is a complete reformat of the internal drive?

---

### Post by Elfy on 2008-10-06
> I've discovered that Error 21 seems to be a "missing drive"What this means is that grub is looking in one place and it's not there - it needs to be chnaged so it's looking in the right place.

Yes you can install on an external drive - but has to be set up correctly, obviously the drive has to be plugged in atm for it to boot correctly.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

There is more information, but to start with we'll be needing the result of this command run from aterminal

```
sudo fdisk -l
```

It will be sufficient to run it from the livecd.

---

### Post by issih on 2008-10-06
First things first...don't worry, the windows install is almost certainly fine, and easily recoverable.

The ubuntu installer has a quirk, that catches lots of people out.
By default, it installs grub (which is the boot loader that allows you to choose which os to run, gnome is the desktop environment once ubuntu is loaded) onto the master boot record (mbr) of the primary drive of the system it is installing on.

In this case that means that whilst all of ubuntus system files were installed onto the usb drive, the grub boot loader was installed into the mbr of the internal hard drive.

In a system with two or more internal hard disks this is fine, as grub is quite capable of booting into windows and linux. Your problem is that grub doesnt really know how to cope with removable drives, so when the usb drive is unplugged it crashes...this is what causes error 21.

First of all your best bet is to reinstall the windows bootloader onto the mbr of the internal hard drive, that will make windows bootable again.

to do that fish out your xp/vista install cd and follow these instructions:

[http://askbobrankin.com/fix_mbr.html](http://askbobrankin.com/fix_mbr.html)

alternatively if you can't find the appropriate disk, download and use supergrub disk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Once that is done and the computer is back to normal, your best bet is to reinstall ubuntu onto the usb drive, this time however, on the last page of the installer, the summary you get before hitting install, click advanced, and select to install grub into the mbr of the usb drive rather than the internal one.

Once that is done you can boot into ubuntu simply by selecting to boot from the usb drive via the system bios rather than booting from the internal drive.

Hope that helps

---

### Post by Elfy on 2008-10-06
It  helped me - I always get confused with booting usb drives :)

---

### Post by caljohnsmith on 2008-10-06
ArcTrooper1773, if your friend's computer supports booting his USB drive from BIOS, you shouldn't have any problems running Ubuntu from the USB drive (data transfer rate shouldn't matter that I'm aware of). If his BIOS doesn't support booting from USB, then he could install Grub to the MBR (Master Boot Record) of his internal drive and have Grub point to his external USB drive for its system files (menu.lst, etc); that assumes though that his USB drive is at least accessible by BIOS on start up, even if his BIOS won't boot to USB. If he does install Grub to his internal drive though, he will always have to have his USB drive connected in order to boot, so that is the disadvantage. 

I agree with forestpixie though, please post the output of the fdisk command so we can see your friend's setup. :)

---

### Post by ArcTrooper1773 on 2008-10-06
Thank you all very much for the prompt replies - using the supergrubdisk utility, we managed to boot the machine into the recovery console, and from there we sent rescuable data to another external HDD, then restored the main machine to factory settings - from there, we've got no problems - Windows has booted up and everything is working now :)  Again, thank you!

Just to clarify, now:  The external drive still does have Ubuntu installed - to allow the machine to dual-boot into windows or linux, the only thing we need to specify is to put the Ubuntu MBR into the partition on the **external hard drive** and not the **internal hard drive**, no?

---

### Post by issih on 2008-10-06
Yup pretty much, all you need is to get grub installed into the mbr of the usb drive.

To do this the simplest way is to reinstall as I suggested before, alternatively boot from the live cd and follow the command line instructions here:

[https://help.ubuntu.com/community/GrubHowto#Command%20line](https://help.ubuntu.com/community/GrubHowto#Command%20line)

Once that is done you can either set the boot order in bios so that the usb drive is tried ahead of the internal one, or just hit the appropriate hot key on boot to select what device to boot from (most modern bioses offer this)

Hope that helps

---

### Post by ArcTrooper1773 on 2008-10-06
Brilliant.  Thank you all again!

---

