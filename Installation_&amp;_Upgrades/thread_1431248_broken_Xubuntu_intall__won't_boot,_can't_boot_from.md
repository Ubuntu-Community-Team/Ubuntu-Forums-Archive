---
title: "broken Xubuntu intall : won't boot, can't boot from CD"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2010-03-16
hello all
I was having a hard time installing Xubuntu on a an old Japanese FMV Biblo LOOX S73A, trying both from a USB stick and from a CD ( I think the USB's were USB 1's) but it was finally rolling--- yet things happen, power shortage and the battery was out-

I'm stuck with a broken Xubuntu intall

I've tried to reinstall forcing the computer to boot from the CD in the bios, but get "no os found"
If  I let it boot from the hard drive, I get to Busybox/initramfs commands that I know nothing of. I just want to do a clean reinstall of the whle thing, but cannot find out how to do so.

the other OS is a Japanese windows XP, which I wanted to keep as a side by side install, but right now anything bootable would be good.

can somebody kindly help me out here ?
I have 3 grub options, regular, recovery mode and mem test

trying to boot from a CD, or GParted won't work

thanks

ben

---

### Post by spyrule on 2010-03-16
You can tell the grub to boot straight from your USB drive...

See here:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)


If you need any help with that, let me know :)

---

### Post by bjaz on 2010-03-16
this bios has an option to boot from USB CD ROM DRIVE, hard disk, or floppy

if I choose USB CD ROM with the disk in it, it will just say OS not found--i'll try the grub command line ways, thanks

b

---

### Post by bjaz on 2010-03-18
hello again, after quite a few tries, I would need help.
thebios can boot directly from the USB CD drive, and I  used pen drive linux to make USB drives, but as of now i'm getting nowhere.
`
the bios booting priorities are USB CD R, HDD, floppy
if I disable the HDD and stick to the the USB CD drive, with my Xubuntu live cd in it, I get no OS found
If I let it boot from the HDD, it starts booting Xubuntu, then parachutes erros which land me in  Busybox/initramfs commands-

the grub options are standard, recovery mode and mem. test.
I can access the command lines if i press C while the grub is loading

is there a way I can access the USB CD drive and boot from there again to re-install ?
that's what it was doing before the powercut, so i'm figuring it's probably the best way to go.

otherwise i have another box running Xubuntu, and also windows, and mac os, should software be needed--, non burned iso's and lives CD's, including Gparted, and 3 USB keys which can be formated, including an 8G one-

I'd really appreciate your help on this one

thanks in advance

---

### Post by bjaz on 2010-03-29
bump
can anybody help ? I can get into the command line options, by pressing "esc" whille the grub is loading- yet the problem remains--i need to use a cd to make the USB1 ports access the drive. I then need to restart the install from the CD

the bios supports cd booting, but the USB1 ports are in the way. the install was going find before the powershortage, now i'm really stuck.

thanks

b

---

### Post by bjaz on 2010-04-07
is there anyway I can use the command lines to fix the broken install ?
or access the ext. cd drive ?

I've been trying to boot / install anything, from the CD, but it refuses to boot. I've tried verified versions of GPArted, crunchbang linux, xubuntu, even a japanese windows xp...to no avail
the only thing that works is enabling the hard disk drive, which gives me a 3 choixed grub, and then starts to boot xubuntu before landing in the busybox iniframs commands that i can't make sense out of.

thanks

b

---

### Post by bjaz on 2010-04-07
it's the same machine discussed in this thread

                         [installing ubuntu on an old japanese mini-pc :  Fujitsu FMV BIBLO loox S73A]("http://ubuntuforums.org/showthread.php?t=1205513") 

but at the time I still had a bootable japanese windows xp in there...now i'm really stuck

using the windows xp, and unetbootin i'd managed to install xubuntu and puppy linux

but now, with this broken xubuntu install only, it's not running or booting anything at all.

I don't really know where to start and really need help on this one.  i can't find my way around the grub command lines

thanks for your patience and help, trying trying

b

---

### Post by bjaz on 2010-05-08
I'm still stuck.

the main issue being that this old netbook style computer has no CD rom drive, just two USB ports

meaning I need to use a USB drive.

normally USB booting is supported, as stated in the bios,, yet in this case, as explained, it is not working.

I'm trying to find a way to erase the drive and reinstall (of ubuntu, or another flavour), or clone and existing bootable partition onto it but cannot find a way around this. anything to be able to use this computer again

can somebody please help me out on this one ?

thanks in advance for your help

---

