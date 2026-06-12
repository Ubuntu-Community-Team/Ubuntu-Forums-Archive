---
title: "GRUB Legacy issues: no web access"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by Shmook on 2011-11-27
Hi all, so I spent this weekend installing about 6 OS's and messing around with GRUB2 enough times to make me go back to "menu.lst" GRUB (awesome social life here;)

And now I thought I'd done everything properly but now when I boot up there seems to be no web access and one (Zenwalk) won't boot at all!

I'll post my menu.lst and I'm hoping someone can point out a simple step I missed:
```

## ## End Default Options ##

title		Ubuntu 11.10, kernel 3.0.0-13-generic
uuid		5689510b-7c34-4ceb-b87a-88b98052a058
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=5689510b-7c34-4ceb-b87a-88b98052a058 ro quiet splash 
initrd		/boot/initrd.img-3.0.0-13-generic
quiet

title		Ubuntu 11.10, kernel 3.0.0-13-generic (recovery mode)
uuid		5689510b-7c34-4ceb-b87a-88b98052a058
kernel		/boot/vmlinuz-3.0.0-13-generic root=UUID=5689510b-7c34-4ceb-b87a-88b98052a058 ro  single
initrd		/boot/initrd.img-3.0.0-13-generic

#title		Ubuntu 11.10, kernel 3.0.0-12-generic
#uuid		5689510b-7c34-4ceb-b87a-88b98052a058
#kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=5689510b-7c34-4ceb-b87a-88b98052a058 ro quiet splash 
#initrd		/boot/initrd.img-3.0.0-12-generic
#quiet

#title		Ubuntu 11.10, kernel 3.0.0-12-generic (recovery mode)
#uuid		5689510b-7c34-4ceb-b87a-88b98052a058
#kernel		/boot/vmlinuz-3.0.0-12-generic root=UUID=5689510b-7c34-4ceb-b87a-88b98052a058 ro  single
#initrd		/boot/initrd.img-3.0.0-12-generic
#quiet

#title		Ubuntu 11.10, memtest86+
#uuid		5689510b-7c34-4ceb-b87a-88b98052a058
#kernel		/boot/memtest86+.bin
#quiet

title		#! LINUX
uuid		0ca4144a-6ffa-4f7e-a765-69d08bba5b15
kernel		/boot/vmlinuz-2.6.39-bpo.2-486 root=UUID=0ca4144a-6ffa-4f7e-a765-69d08bba5b15 single
initrd		/boot/initrd.img-2.6.39-bpo.2-486

### END DEBIAN AUTOMAGIC KERNELS LIST
title		Windows XP
rootnoverify	(hd0,0)
makeactive
chainloader	+1

#EXAMPLE LINUX INPUT
#title           Linux
#uuid	   	 xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
#kernel          /vmlinuz root=/dev/hda2 ro

title		ArchBang
uuid		50141814-a343-48e6-b13f-44ecd5c43522
kernel		/boot/vmlinuz-linux root=UUID=50141814-a343-48e6-b13f-44ecd5c43522 single 
initrd		/boot/initramfs-linux.img

title		PCLOS
uuid		6186f696-ce05-431f-8552-9164c2685ce0
kernel		/boot/vmlinuz-2.6.38.8-pclos3.bfs root=UUID=6186f696-ce05-431f-8552-9164c2685ce0 single
initrd		/boot/initrd-2.6.38.8-pclos3.bfs.img

title		Zenwalk
uuid		1abe28ad-534a-4d59-989b-2dec40edfbd2
kernel		/boot/vmlinuz-2.6.37.4 root=UUID=1abe28ad-534a-4d59-989b-2dec40edfbd2 single
initrd		/boot/initrd.splash

```
thanks in advance -- and please don't say "just reinstall GRUB2" I wasted an entire night doing this

---

### Post by ottosykora on 2011-11-27
I also do use grub legacy as it is mor elikely to survive upgrades and is much simpler to configure. I even do not use the uuid and such things, just the oldfashioned (hd.... ) lines.

The web acces has on the other hand nothing to do with the bootloader, it is in each os specific set up. It could have something to do with the kernel in use, such as it does not support the ethernet adaptor or so, but those kernels are not that old.

Why the last one refuses to boot, no idea, but the initrd name, is it really true it is called there so? Looks to me kind of strange, but well, one can call it what ever, but check it please.

---

### Post by dabl on 2011-11-27
Two points:

1. Network access is 100% irrelevant to Grub.  If you don't have network access in you OS, then something is wrong with either your network interface hardware, or you networking configuration in the OS.

2. Legacy Grub is history -- you are clinging to the old version and it will sooner or later leave you stuck unbootable.  Grub2 is the currently supported Linux bootstrap package, and it works just fine if you will learn to use it.  Works on hard drives, USB sticks, SDHC cards, and probably a floppy diskette if needed.

---

### Post by Shmook on 2011-11-27
@ottosykora: yes I noticed that too, but found no other initrd files in /boot -- however that was the last one i'd set up that night so I didn't see the README file describing how to build the initrd file that it seems slackware-based distros don't need...?

And yes, dabl, perhaps that's true, but I'm holding on to the one that makes more sense to me for the time being -- I gave GRUB2 a good shot, as well as the additional tools that help when you've got 6 OS's wanting to install a bootloader to their respective partition or the MBR (grub customizer, startupmanager, supergrubdisk, boot-repair-disk), but thanks for the info.

Oh but what about syslinux or lilo? Are they on their way out too or worth looking in to?

---

### Post by ottosykora on 2011-11-28
>how to build the initrd file that it seems slackware-based distros don't need...?<

hmm, well it looked strange to me ;-)
I used SLAX some years ago a lot, the thigs might work different here, but there has to be some boot environment.


As far as lilo, the problem with it when I used it was that it wanted to be pointed to the kernel to start and after a kernel update it had to be updated too otherwise it was kind of hassle to get the system bootale again.
The syslinux is more flexible so far, but I prefer for daily use something more simple and I am not seeking any programming lessens before I am able to set up something like bootmanager.

Therefore I use a real bootmanager, something what can be installed with a mouse click and similar unistalled with mouse click, a feature grub is missing still and does not even make backup of items it is going to overwrite. I mean we are in 2011 now so writing some complex scripts to be able to do some siple tasks should be over.

I use grub legacy to actually start linux and so it has to go into the partition. In such configuration, grub2 behaves bad, so far did not survive any distro upgrade. Grub legacy did survive fine so far.

---

### Post by dabl on 2011-11-28
The initrd line for your Zenwalk OS looks odd, but I admit I don't know anything about Zenwalk.  Normally the initrd is a .img file, not a .splash file.  :confused:

---

