---
title: "Can't Remove Grub from MBR"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by CulleyS on 2007-08-18
I'm attempting my third dual-boot XP/Ubuntu build.

Only, this time I'm trying the AMD64 build and am trying the Server Edition disk with a later apt-get install ubuntu-desktop.

Nothing has gone smoothly as happened before when I simply ran the Desktop non-64 installs.  I got everything installed, but my network settings were all wonky and I could not for the life of me keep a network connection.

So, I decided to start over from scratch.  I get through the Server Edition menu and get right to the point where I need to do my first reboot... remove the CD, etc.  However, the old Grub menu I built still pops up.  None of the choices in that menu (outside of the Windows XP choice) work.  They all just go to error messages and the PC locks up.  Well, the memtest works too.

I found a tutorial which said I should use the Recover function of my Windows XP boot disk to do a "fixmbr" to remove Grub.  I've done that.  Didn't help.  I still get the same Grub menu with my old choices when I reboot.  

Any other ideas?  Just keep trying the fixmbr over and over again hoping it removes Grub eventually?  :)

Thanks.

---

### Post by CulleyS on 2007-08-18
Well, I've made some progress, I guess, but not really.  I loaded into Windows and deleted all partitions on my Linux drive (a separate physical drive from XP).  I then ran the Windows XP Recovery.  I ran fixboot, followed by fixmbr.  Now, instead of getting the Grub menu, I get a Grub Error 22.

I noticed when running the Windows XP Recovery and doing a fixboot, it said it would write a new partition on C.  I don't have a drive named C.  I have a D drive, E drive, K drive, and Linux was on a drive labeled P, which is now a blank drive in need of partitioning and formatting.  Windows is on D.  K is an external.  E is the CD/DVD-ROM, and P is another SATA drive (now empty) just like my D drive.

I'd really rather not have to uninstall Windows XP, roll everything back to zeros and start over.   Backing up is just not going to be fun and having reinstall all of my programs is not going to be fun either.

So, if anybody has any other suggestions than that, I'm open! :)

---

### Post by bulldog on 2007-08-18
If you have more than one hdd,I think you recover your MBR from the wrong hdd.
The menu.lst which you see is NOT in the MBR but in /boot/grub
So if you deleted your ubuntu partitions you shouldn't see your menu.lst anymore and you get the error instead.
So think a second on which hdd you installed GRUB in the MBR.

---

### Post by CulleyS on 2007-08-18
Ah, good suggestion.  I will try unplugging one hdd, run Windows XP Recovery and fixboot/fixmbr.  Then, plug that drive back in, unplug other drive, and repeat.

Right now, I am formatting, so it may be an hour or so before I can try.  But I will post when I am done.

Thanks!

---

### Post by bulldog on 2007-08-18
Nice going,but I'm  gonna take some sleep in a moment,it's one hour past midnight over here.:)
But it's very simple,your hdd's are called (hd0) and (hd1) if you have two of them.
Your IDE hdd is very likely (hd0) so if you didn't change anything when you installed ubuntu,GRUB is in the MBR of this hdd.

Maybe some thought's.
I have similar system with three hdd's and several linux distro's.
Try to keep all your windows related files on the windows hdd.
And do the same for your linux install.
Make the linux hdd the master boot device in your BIOS and the windows hdd the second one.
Now install GRUB into the MBR of  the linux hdd,don't disconnect the windows hdd,and GRUB will detect your windows and add it to the menu.lst.
It's possible you have to alter the menu.lst and add some mapping lines into the windows section because windows likes to think it's booting from the first hdd.

map (hd0) (hd1)
map (hd1) (hd0) 

Now you can boot windows from the grub menu.lst and in case of grub disaster,you can set the windows hdd as the master boot device in your BIOS and just boot windows with it's own boot loader.

---

### Post by maybeway36 on 2007-08-18
Find a FreeDOS boot floppy (or an MS-DOS/Windows boot floppy) and type
```
fdisk /mbr
```
Then reinstall Windows and Ubuntu.

---

### Post by CulleyS on 2007-08-19
Yeah, like I said, I didn't want to reinstall Windows as it was working fine.

So, I did as suggested... and as I did when I configured a dual-boot set-up before:  unplug ALL drives EXCEPT the drive for Linux.

Ran Windows XP Recovery:  fixboot found no boot partitions on this drive, fixmbr ran okay.  Reboot.  Then I installed Ubu.

Plugged in ALL drives.  Configured Grub for dual-boot XP/Ubuntu.  Reboot.

Everything is working again.

Thanks!

Culley

---

