---
title: "Can't install to external USB Hard Drive???"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-26
I burned a Live iso of Xubuntu to an 8GB USB stick and want to install it to an external Hard Drive that's in an enclosure that plugs into USB.  I can select the Hard Drive but it tells me something like "No root file system installed, please fix this in the what ever it was." but no matter what I do it just won't take.  What is it wanting me to do or install?  
I figured it be a simple click "install" pick the drive I want and bang, it'd install but it's just not working out that way. I have the external hard drive in FAT 32 same as my usb sticks but it's just not working out. HELP!!:confused:

---

### Post by ubfan1 on 2013-06-26
Select "something else" for the install type, then "use as" should be ext4, and mount point as "/", and click format.  Make a swap partition on the usb if you don't have one on the internal hard disk (which should be faster than a swap on USB).  You cannot do a full install to a fat32 filesystem, the live media is a totally different setup.

---

### Post by TNFrank on 2013-06-26
> **ubfan1 said:**
> Select "something else" for the install type, then "use as" should be ext4, and mount point as "/", and click format.  Make a swap partition on the usb if you don't have one on the internal hard disk (which should be faster than a swap on USB).  You cannot do a full install to a fat32 filesystem, the live media is a totally different setup.

I had selected "something else", it was the ext4 journalling file system and the "/" root that I was missing. I found it by doing a bit more research on the net. Thanks for the info though, I appreciate it.  
Now my "problem" is getting my laptop to boot to the external hard drive, for some reason it doesn't "see" it even though I have USB set as First on my boot order and internal hard drive as 7th(i.e. last) but it will "see" a USB stick on reboot, go figure.LOL.

---

### Post by ubfan1 on 2013-06-26
The sad fact is that some external USB enclosures work better than other for booting.   Two out three 3.5 USB encl I have simply won't boot, but work fine as external storage.  Had better luck with a 2.5 encl, but then it started being "not seen" at boot.  Could be a fault of my controller chip, they do fail on me pretty regularly, I'm on my third motherboard.  Never had a problem booting off a stick though.

---

### Post by TNFrank on 2013-06-26
I guess I'll probably just have to use the external hard drive as storage. I think it might be because they're powered(at least mine is) externally(not USB power) so by the time the BIOs looks at the USB the external drive hasn't had time to spin up and be seen. Guess it's time to buy a few more USB sticks and just install to them. :KS

---

### Post by ubfan1 on 2013-06-26
You could just install grub to the sticks, and have the grub.cfg menu items point to the external USB installation.  That way, you are booting off the stick, but running off the USB disk (which should be faster than a stick).  Use the uuid's in the grub.cfg instead of the /dev/sdx devices.

---

### Post by TNFrank on 2013-06-26
> **ubfan1 said:**
> You could just install grub to the sticks, and have the grub.cfg menu items point to the external USB installation.  That way, you are booting off the stick, but running off the USB disk (which should be faster than a stick).  Use the uuid's in the grub.cfg instead of the /dev/sdx devices.

Ok, I caught about 1/2 of what you said there,LOL.  So I'd hook up my USB stick and my USB hard drive and when the computer boots to the USB stick I'd have an option to boot to the USB hard drive too?  Ok, in plain, simple English can you walk me though how I'd do that because it sounds like a winner.:KS

---

### Post by varunendra on 2013-06-26
> **TNFrank said:**
> Now my "problem" is getting my laptop to boot to the external hard drive, for some reason it doesn't "see" it even though I have USB set as First on my boot order and internal hard drive as 7th(i.e. last) but it will "see" a USB stick on reboot, go figure.LOL.
Some USB drives may not get listed under USB devices, especially hard disk drives. Check them under the list of Hard Disks (even some USB flash drives sometimes get listed as "Hard Disk" under the list of HDDs. Check other expandable catagories as well to see if your external drive was recognized as such.

> **ubfan1 said:**
> Two out three 3.5 USB encl I have simply won't boot, but work fine as external storage...... Never had a problem booting off a stick though.
ubfan1, I'd like to let you know that your statement above is the first one I've seen that says that a usb stick works but not a usb hard disk. So far I've seen and experienced exactly opposite of this. That is, usb sticks may be tricky, but usb HDDs are almost guaranteed to boot on every BIOS that supports booting from USB.

I think your issue might have been due to a poor quality signal on the 2 mtr lead that usually comes with externally powered drives, and/or drive not getting ready within the time that BIOS can wait for external drives. In case of signal quality issue, a shorter cable helps. In the latter case, you can check if your BIOS has an option to adjust the delay time before probing for boot drives (internal or external). If there's no such option, a crude workaround that has always worked for me is to do a hot reboot (ctrl+alt+del) so that the boot sequence restarts without re-initializing the external drive (so it gets extra time to get ready).

> **TNFrank said:**
> I think it might be because they're powered(at least mine is) externally(not USB power) so by the time the BIOs looks at the USB the external drive hasn't had time to spin up and be seen.
You are guessing in the right direction. There is really no reason why an external hard disk drive can't boot when a USB stick can. Just try what I suggested above.

---

### Post by ubfan1 on 2013-06-26
@varunendra,  The USB enclosure I never had any problems with booting was a MAXTOR, which came with it's own disk.  The cheap powered USB enclosures I added my own disk to, whether a new disk or one pulled from another PC, had boot problems, and I believe I tried everything to make them boot by themselves reliably.  One would boot about 20% of the time, the other only 1%.   Nevertheless, both worked fine as storage, and both could be booted when grub was  running off another device (like a USB stick).  The booting laptop was an  HP with the dreaded MPC51 controller, which does everything from video, wireless, hard disks, as well as USB.  The controller had no cooling, tended to overheat  and crack solder pads, so the fault may well be partially the laptop's fault (but remember, never any problems with the MAXTOR).

@TNFrank, TNFrank,  First problem will be to figure out how your disks are named when your USB stick, USB hard disk, and internal disk are present. 
If you have a booting stick, look at the /boot/grub/grub.cfg file. grub uses hd? for the disk, and msdos? (or gpt? if UEFI) for the partition.
Pre 12.04, the disk enumeration was pretty stable, and hd0 was the internal hard disk and the usb disks followed at hd1 and hd2.  Lets assume your grub.cfg refers to hd1 as the stick itself, so I'd guess the USB hard disk would be hd2.  If your usb disk has an installation on it already, you can find out  the uuid of the filesystem by running sudo blkid to list all the uuids on the system.  Or look in the disk's /boot/grub/grub.cfg, the uuid's set up on the disk will not change.
Post 12.04, I'm starting to see the booting usb named hd0 much more frequently.
If the internal hard disk gets hd1, you may still have the second USB on hd2.

There should be some setup using (hd1,msdos?) before the actual menu entries.
Lets hope those can remain the same (adding another non-boot USB hopefully will be after the booting USB, but who knows how the numbering is done, it may well be dependent upon which port you plug into.  The menu entries all start with "menuentry" and end with a "}"
You should be able to copy a whole menuentry from one file to another, and only have to change any hd? references.

which should have a linux line with an entry like "root=UUID=xxxxxxxxxxxxxxx".
That should be the uuid of the stick's root filesystem.
It might appear in a few other places within the menu entry.
Ensure you can edit the file as root (sudo chmod 744 grub.cfg), edit the file and copy the first menu entry, and paste it in right after the first,
then change the uuids.  Also, my experience is that hd0 will be the internal  hard disk (99.9% for 4000+ USB boots), and hd1 will be the USB boot device.
  Change every the hd1  to hd0, and use the msdos? for the installed UBuntu on the USB

---

