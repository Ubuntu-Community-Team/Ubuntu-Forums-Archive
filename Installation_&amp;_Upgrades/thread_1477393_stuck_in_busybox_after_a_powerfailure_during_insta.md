---
title: "stuck in busybox after a powerfailure during install-no internal CD drive, USB boot ?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2010-05-08
hello all
I was having a hard time installing Xubuntu on a an old Japanese FMV  Biblo LOOX S73A, with no internal drive.
 trying both from a USB stick and from a CD ( I think  the USB's were USB 1's, not sure) but it was finally rolling with the CD---the bios lists USB booting- yet things happen,  power shortage and the battery was out-

I'm stuck with a broken Xubuntu intall
I have 3 grub options, regular, recovery mode and mem test

I've tried to reinstall forcing the computer to boot from the CD in the  bios, but get "no os found"
If  I let it boot from the hard drive, I get to Busybox/initramfs  commands that I know nothing of. I just want to do a clean reinstall of  the whle thing, but cannot find out how to do so.
                                                  as mentioned this bios has  an option to boot from USB CD ROM DRIVE, hard disk, or floppy

if I choose USB CD ROM with a disk (install disk, Gparted...) in it, it will just say OS not  found--i'll don't know how to fix things using the grub command line ways,
if I disable the HDD and stick to the the USB CD drive, with my  live cd in it, I get no OS found
If I let it boot from the HDD, it starts booting Xubuntu, then  parachutes errors which land me in  Busybox/initramfs commands-
I can access the command lines if i press esc while the grub is loading

trying to boot from a CD, or GParted won't work. I would like to tell the grub to boot from USB but i'm not sure how to do this.
I've been trying to boot / install anything, from the CD, but it refuses  to boot. I've tried booting to verified versions of GPArted, crunchbang linux,  xubuntu, even a japanese windows xp...to no avail
the only thing that works is enabling the hard disk drive, which gives  me a 3 choixed grub, and then starts to boot xubuntu before landing in  the busybox iniframs commands that i can't make sense out of.


s there a way I can access the USB CD drive and boot from there again to  re-install ? 
that's what it was doing before the powercut, so i'm figuring it's  probably the best way to go.


otherwise i have another box running ubuntu, and also windows, and mac  os, should software be needed--, non burned iso's and lives CD's,  including Gparted, and 3 USB keys which can be formated, including an 8G  one-
 i don't think there's anything like target-disk mode which would help  out here

the main issue being that this old netbook style computer has no CD rom  drive, just two USB ports

meaning I need to use a USB drive.

normally USB booting is supported, as stated in the bios,, yet in this  case, as explained, it is not working.

I'm trying to find a way to erase the drive and reinstall (of ubuntu, or  another flavour), or clone and existing bootable partition onto it but  cannot find a way around this. anything to be able to use this computer  again

can somebody please help me out on this one ?

thanks in advance for your help

ben

---

### Post by bjaz on 2010-05-10
ok,upon closer inspection, when booting in memtest i386 the ext. USB CD R drive is detected, yet through an SCSI adapter...don't really know why.
is there anyway to get the computer to boot from this through the busybox commands ?
i just want to restart an install

thanks so much

ben

---

### Post by bjaz on 2010-05-10
as a side note, I had already installed xubuntu and crunchbang linux on the computer, using a USB cd drive. 
the bios supports USB booting, but doesn't for a reason.

as of now, and for the past few months, this computer has been unuseable because of the broken xubuntu install-- i really have no clue how to get out of this. 

I would like to delete the grub and wipe the whole drive, using Gparted for instance yet i don't know how to do this, since the computer doesn't boot onto the usb cd drive or a pen drive linux type of install.

if anyone, anyone out there can help me wipe the drive / and or reinstall an linux flavour of any kind- you'd really save me

as of now i can't even reinstall / boot any os on this machine, which worked fine before the install crash

 can somebody please help me ?

thanks

edit- I think the solution will consist of buying an ide to 2.5 IDE adapter, then performing the install from another machine-- the HDD is easily accessible and it's the only way out I see for this...

---

### Post by bjaz on 2010-05-11
note - i can also access command lines by pressing C in grub

yet I can't find out how to get things to boot from a CD

b

---

### Post by bjaz on 2010-05-16
ok, still stuck, I got the 2.5 IDE adapter, removed the hard drive, erased it, I now have 2 working hard drives.
no grub booting now.


since i'm not going anywhere with the USB installs ( from a hard disk or a flash drive), I did the install to HDD from another machine-- chose boot from hdd in the bios, and....nothing, zilch, a flashing cursor...

if I choose USB boot, and place a working live CD in the drive (any, GPARTED, xubuntu, ubuntu, ubuntu netbook remix, crunchbang, puppy...) I get "no os found"- same for a unetbootin flash drive- must be the usb-- yet what about the HDD booting, why isn't it booting ? is it a path issue since the HDD was setup as external when i installed from another machine ?
is there any way to get the hdd to booting, correct the path with the full install on it ?
I could probably boot another computer from this 2.5 HDD, placing it in its USB enclosure.

i don't get it, what could be up ?

this was a UMP which once ran xubuntu and puppy linux with no issue-
which once supported usb booting (it's in the bios)

now i'm really struggling to get it working again

any idea on how to fix this, or what could have possibly gone wrong, would be extremely welcome

---

