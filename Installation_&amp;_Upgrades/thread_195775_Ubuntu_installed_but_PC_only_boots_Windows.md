---
title: "Ubuntu installed but PC only boots Windows"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by avocado on 2006-06-13
Hulloo!

I have P4 with WinXP installed.
4x sata hard drives, 2 of these as striped raid.
I am new to Linux.
I have installed Dapper Drake to its own hard drive with nothing else on it. 
Install seemed to go fine with no errors returned.
But on reboot I get no choice of OS and my PC boots straight into Windoze.
I have tried re-installing several times, including using XP recovery console to *fixmbr*. All without probs until attempting to boot.
I have tried re-installing grub to MBR using a terminal as per another thread. 
I have tried using "super grub disk".
Still just boots into Windoze and I'm a-gaggin to get going with ubuntu!

I am now lost for direction!
Any advice very welcome.

---

### Post by localzuk on 2006-06-13
The problem is likely where you are installing grub. It needs to go the MBR of the primary boot disk.

---

### Post by avocado on 2006-06-13
[QUOTE=localzuk]The problem is likely where you are installing grub. It needs to go the MBR of the primary boot disk.[/QUOTE]
I am just going with the default install .. which puts grub into the MBR of the primary boot disk as I understand from other threads, no? I watched the install closely and that seemed to be the case. How do I find out where it is?
Cheers.

---

### Post by localzuk on 2006-06-13
My guess is that it is to do with your disks being sata. Try setting each one as the primary and see if any of them get it to work.

---

### Post by avocado on 2006-06-14
I had already started on a different course of action before reading your post, localzuk.
I disconnected the 2 raid drives. Then formatted and re-installed ubuntu.
I now get a grub menu with choice of ubuntu and XP.
But - boot hangs as soon as OS choice is made - so no Ubu and no Windoze!
Just says 'booting ubuntu' and a few lines about root, file system, initrd and then 'savedefault' and hangs there.
Or 'booting windows' some similar lines and 'savedefault'.

This is now getting depressing on my 4th day of what promised to be a simple install!! 
Any suggestions welcome.

---

### Post by rcarring on 2006-06-14
Pull out all the drives except the one you have Windows installed upon.

Get windows to boot, if necessary repair the mbr on the Windows drive.

Remove grub.

Next, add back in the second hard disk.

Install using the alternate cd in expert mode and install grub to floppy. Then you can boot ubuntu from the floppy bypassing the sata mbrs altogether.

---

### Post by avocado on 2006-06-16
[QUOTE=rcarring]Pull out all the drives except the one you have Windows installed upon.

Get windows to boot, if necessary repair the mbr on the Windows drive.

Remove grub.

Next, add back in the second hard disk.

Install using the alternate cd in expert mode and install grub to floppy. Then you can boot ubuntu from the floppy bypassing the sata mbrs altogether.[/QUOTE]

Thanx. Ok. I was a little nervous of using text install but it was straightforward enough. Installed fine, no errors (except 'could not configure network with DHCP' which I set to 'configure later'). Starts GRUB menu from floppy offering Ubu or XP.

But:
Won't load either system- (inc ubu in recovery mode).
Same sort of details onscreen as my previous post.
ie Just says 'booting ubuntu' and a few lines about root, file system, initrd and then 'savedefault' and hangs there.
Or 'booting windows' some similar lines and 'savedefault'.

I tried also installing lilo to the hard drive but this didnt work either.

Aggghhh!Whassgoinon?
I have now spent the better part of my working week trying to do this.
Thoroughly fed-up with it.
I would very much like to make the switch from The Dark Side but this is proving quite a struggle.
Thanks localzuk and rcarring for the guidance thus far.
Any further suggestions very welcome.

---

### Post by avocado on 2006-06-19
Anyone? Please.

---

### Post by soapyfish on 2006-07-20
Ok Ok this is a long shot but I have a similar arrangement I have windows installed on a Raid 0 (stripped)  and another Raid 0 for data and a 5th drive for ubuntu I found it was much easier to change my bios settings to tell the machine where to boot from rather than using a boot loader as this way I do not have to worry about the fixmbr command in windows if I remove ubuntu etc I have a Pentuim 4 based system with an Asus P4C800 motherboard and the bios allows me to configure the driver boot sequence as well as define the primary and secondary  Disks I don't know if that will help you but it was the easiest and safest way to do what I wanted :-) you might find that by playing with the bios drive and boot sequence you can make boot ubuntu :-k

---

### Post by avocado on 2006-07-20
Hey soapyfish,
Thanx for that. I have given up on the dual boot. I bought a cheap (GBP30) secondhand pc and installed ubuntu without probs to that. I am now finding my way around kubuntu. They are both superb. I will continue familiarising myself, without upsetting my current set-up and make the jump when I feel ready. This has been a much easier way of doing it than teh dual boot thing.
Cheers for you thoughts. Good luck.
:)

---

