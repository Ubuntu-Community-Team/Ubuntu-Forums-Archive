---
title: "Can't install 12.10 on Sony Vaio T-series SVT13125CXS"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by azile19 on 2013-01-25
I bought this ultrabook with the intent of wiping Windows 8 as fast as humanly possible so that I could get a real operating system running on it.  I had seen the forums talking about UEFI and such nonsense, but there seem to be decent work-arounds, and had at least one first-person tale of successfully giving W8 the boot and getting ubuntu up and running.

That being said, this install seems to have come with a new kind of crazy.  First off, finding the BIOS was a problem.  W8 posts extremely fast, so Sony gave us a special "assist" button.  Pressing this button from the shut down mode turns on the computer into some super strange pre-bios menu.  Here, we have options for "Recover or maintain your system", "start from media", "Start from network", "Start BIOS setup", "Shut down", "Start Windows" (blech), "Select Language."

I can go into BIOS from here, which is weirdly bare-bones, and do things like switch between UEFI and legacy, turn off the secure boot option, etc.  What is weird is I have options for switching the boot order, but I only have three things listed: External Device, Internal Hard Disk Drive, Network.  I would have figured that since I have two USB ports those should have shown up separately.  

Ok, so with legacy on, secure boot off, external device boot enabled (it's disabled by default, arg) and the boot order moved around, I can start to boot from my 12.10 thumb drive.  I see an Ubuntu screen with the moving dots, it sits there for a long time, then sends me to a shell prompt with the following:
```

BusyBox v1.19.3 (Ubuntu 1:1.19.3-7ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

```
This does seem to be a working shell, although I don't have a lot of options in terms of commands.

Ok, so my guess is that ubuntu can't find my hard drive.  Does anyone know a fix?

---

### Post by Double.J on 2013-01-25
Sounds like the boot loader on the stick can't find the installer's squash partition?

Have you tried reflashing the stick/ booting it on a separate machine?

---

### Post by Cuchaz on 2013-01-25
Two (very) separately-created USB live images do the same thing. The kernel boots, but it can't find the filesystem on the USB stick, then drops into BusyBox. Sadly, this busybox environment doesn't have fdisk, so it's really hard to tell what devices are present.

Also, hi =)

EDIT: the second USB stick had been previously used on another machine to install Ubuntu 12.10 without problems. Therefore, the USB stick/image is probably not the problem.

---

### Post by azile19 on 2013-01-25
Just by way of explanation, Cuchaz is my go-to tech support, so he knows way more of what he's talking about than I do.  Also, I owe him several beers.

---

### Post by m3topaz on 2013-02-05
I've had some "fun" with a Vaio SVS1512 and W8/Ubuntu, EFI boot. I think my root problem was that the power button could activate some mode which wrecked the partition on the disk. The Vaio hardware is definitely looking for W8.

The 64-bit 12.10 regular USB installer works. Sort of. I think that the problem you might have could relate to the partition scheme of the hard drive, and your legacy install has flattened it in such a way that booting is... difficult. The out of the box partition scheme for my Vaio is not pretty:

```

Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): <---->
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048&#8212;sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number Start (sector)	End (sector)	Size		Code	Name
1 	2048		534527		260.0 MiB	FFFF
2 	534528		3553279		1.4 GiB		2700
3 	3553280		4085759		260.0 MiB	EF00	EFI System partition
4 	4085760		4347903		128.0 MiB	0C01	Microsoft reserved part
5 	4347904		500118158	236.4 GiB	0700	Basic data partition

```
Partitions 1 and 3 hold EFI boot code. I'm guessing, but one or more of these should have a legacy boot sector. I wouldn't be surprised if the Vaio can't boot properly from that.

I can suggest two things:
1) Get a Super Grub 2 disk, CD, and boot from the "Assist" menu option "start from media". See if you can find a bootable install of anything. If you can, boot Ubuntu, install and run boot-repair.
2) Re-install, with the USB drive you already used. Before this install, set BIOS to UEFI, and before or during install make a 200MB FAT32 EFI boot partition, then partitions for /, swap and /home. That should allow UEFI booting and might work better than legacy boot on your Vaio.

Good luck!

---

### Post by azile19 on 2013-02-05
Thank you for the help, topaz!

So I actually got this party working a few days after that post.  I'll explain the basics, although Cuchaz can tell you the specifics.

I was happy to get rid of W8, so I set my BIOS to legacy.  For some reason the computer wouldn't get into the Ubuntu install GUI off of a USB drive, but it would from an external CD player plugged into the same USB drive.  Still no idea why that is, and I actually still have an issue with one of the USB ports that I haven't gotten around to fixing.

Anyways, once we booted from the CD, I was crashing repeatedly as soon as ubuntu tried to load the partition table (like you said).  We guessed, correctly, that the issue came from ubuntu not being able to understand the strange hybrid HD in this little beastie.  Again, Cuchaz knows better what he did, but it had something to do with completely wiping the hard drive(s) and reformatting.  Once that happened, we could put the / filesystem on the SSD portion, the /home on the regular hard drive portion, and then all was well with the world.

---

### Post by pimgux on 2013-04-19
hi i am wanting to buy the vaio 13125, what is your opinion about this ultabook regarding linux (compatibility, support for the touch screen, speed)
thanks .. .

---

### Post by azile19 on 2013-04-21
I didn't get the touch screen version, so I can't say anything about that.  Otherwise, I've been quite happy with it now that I got past the initial install issues. The battery lasts for about 3-4 hours for standard usage.  Anything in particular you're curious about?

---

### Post by salva84 on 2013-08-06
Same problem here, impossible to install on a t13.... :(((((((((((((((

---

