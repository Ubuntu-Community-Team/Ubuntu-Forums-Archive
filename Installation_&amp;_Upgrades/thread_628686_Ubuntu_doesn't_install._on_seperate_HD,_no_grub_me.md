---
title: "Ubuntu doesn't install. on seperate HD, no grub menu for dual"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by pood on 2007-12-01
I've tried installing this on my desktop 3 times and failed all 3 times.

I have successfully installed it on my other desktop and laptop without a hitch.

My system is setup weird that if you installed a fresh copy of Winxp, it will try to boot into my old IDE hardrive when it's suppose to boot into my SATA drive. So to mitigate that, I just unplug eveything else before I do a fresh install of windows.


So, I made an ext2 for Ubuntu on my other SATA drive, I had to do it manually in Windows because I didn't have the option to auto make the partitions in Ubuntu. 12 gig for "/" and 300 for swap (I have 3 gigs of ram). DO I also need to make a some space for the "/home" directory?

Each time that I've tried, it would complete, but I never get the window that says the installation is complete, please restart. And if i restarted, it just boots into Windows without the Grub menu.

I have set the grub install to the drive that I'm installing my ubuntu, but I get an error.

Should I try putting the Grub install on to my main drive with WindowsXP?

Also, I tried the 64-bit version, it wouldn't even boot into the Live cd.

---

### Post by perixx on 2007-12-01
Hi pood,


Firsty, I'd recommend using Feisty - it seems to be the most stable version to me and easiest to install. 

I didn't completely catch on with how you've set up your system, but have you made sure, if your main (Windows)-HDD is on the primary controller channel that you have set up your BIOS' bootup sequence in a way that the IDE-drive is the second one?

If I understood correctly, you've set up your Linux-partition (ext2) with Windows ?!? Use your Linux Live-CD and the 'Gparted' parttion manager for that purpose instead, please! [Btw., don't forget to defragment your XP-partition (with Speedefrag or Powerdefrag) before resizing it with Gparted, should you desire to install Ubuntu on your XP-drive]

Read this link about Grub/booting:
[http://wiki.ubuntuusers.de/GRUB]("http://wiki.ubuntuusers.de/GRUB")

IDE-HDD's are addressed as follows: primary(1st) - called hda/hd0 in Linux/Grub and secondary(2nd) - called hdb/hd1 in Linux/Grub. SATA-drives are named 'sda', 'sdb'... (for HDD1, HDD2...). 

You need the Grub notation hd0/ hd1/ (1st and 2nd HDD) for the Grub command-line and to tell Grub the location of the Linux root-partition in your Grub-menu /boot/grub/menu.lst (e.g. root (hd0,1) for 1st HDD, 2nd partition).

The Linux notation is used in the menu.lst.

In order to have your BIOS booting from the second (SATA) drive, you've got to set your bootup-sequence accordingly (1st DVD, 2nd SATA, 3rd IDE). 

I'm not sure where your XP is residing, but I believe you got it on the first partition of your IDE drive (primary). That would be addressed as root (hd0,0) then. 
When booting directly from the second drive via BIOS, I'm not perfectly sure how Grub 'sees' the SATA-HDD with Ubuntu - as root (hd0,0) or as root (hd1,0). Perhaps it's best to create two different entries into the menu.lst for Ubuntu; boot from the Live-CD, open a terminal and enter
```
sudo mousepad /dev/sda1/boot/grub/menu.lst
```
to edit the file (or sudo-open mousepad and navigate there):

```
# Linux bootable partition config begins
  title 1 Xubuntu 7.04 Feisty (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro vga=normal quiet splash
  initrd=/boot/initrd.img-2.6.20-15-generic
  boot
# Linux bootable partition config ends
#Linux bootable partition config begins
  title 1a Xubuntu 7.04 Feisty (on /dev/sdb1)
  root (hd1,0)
  kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb1 ro vga=normal quiet splash
  initrd=/boot/initrd.img-2.6.20-15-generic
  boot
# Linux bootable partition config ends

```

This way you can choose and try which one works. Proceed for the Windows-entry respectively:

```

# Windows bootable partition config begins
title 2 Windows XP (on /dev/hda1)
rootnoverify (hd0,0)
chainloader +1
# Windows bootable partition config ends
# Windows bootable partition config begins
title 2a Windows XP (on /dev/hdb1)
rootnoverify (hd1,0)
chainloader +1
# Windows bootable partition config ends

```

You might also alter your boot-lineup in the BIOS and set your XP IDE-drive as 2nd. Then, you should be able to work with the following entries:

```
# Linux bootable partition config begins
  title 3 Xubuntu 7.04 Feisty (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sda1 ro vga=normal quiet splash
  initrd=/boot/initrd.img-2.6.20-15-generic
  boot
# Linux bootable partition config ends
# Windows bootable partition config begins
title 4 Windows XP (on /dev/hdb1)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1
# Windows bootable partition config ends 
```

Since you want to boot XP from the second HDD, you've got to use the trick with 'map' here in your Grub menu, to makebelieve Windows that it's on the primary HDD, first partition. See also:
[http://tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html#AEN72]("http://tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html#AEN72")

Tell me, how this worked out for you, please...


perixx

---

