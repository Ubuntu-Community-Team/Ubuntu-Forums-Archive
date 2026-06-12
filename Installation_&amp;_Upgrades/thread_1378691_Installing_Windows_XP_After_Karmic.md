---
title: "Installing Windows XP After Karmic"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Theist17 on 2010-01-11
Hey guys, 

I'm considering dual-booting Ubuntu Karmic Koala and Windows XP. It's only so I can use Rosetta Stone stress-free (WINE isn't an option) and play a couple of Windows-only games (again, no WINE for me) while having the wonderful goodness that is Ubuntu Karmic. VirtualBox is  also not an option, due to Rosetta Stone's language pack discs' DRM.

The problem is that I've already installed Karmic. That's right, folks, I've installed Ubuntu BEFORE XP. It's foolish, I know, but I've been using Ubuntu exclusively for the last year; and this XP idea just came about today. 

So, I come to you. I've heard that XP's setup automagically hogs all boot options and that restoring GRUB can be a kind of a hassle. What I need is some help with this. 

Can you help a brother out?

---

### Post by darkod on 2010-01-11
No hassle at all, especially if you already have unallocated unpartitioned space on your hdd to allocate to XP. If not, shrinking ubuntu to allow unallocated space for XP will be some hassle.

As far as restoring grub2 to the MBR is concerned, if you know your root partition it takes only two commands. Full instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by studmf on 2010-01-11
Install XP in VirtualBox instead!!!!

---

### Post by JC Cheloven on 2010-01-11
Install xp on a spare partition (I assume you know how to do this). Then:

- Boot your karmic live cd. Run the following commands as root. 
- fdisk -l  			# to find out where your ubuntu is
- mount /dev/[COLOR="Red"]sda1[/COLOR] /mnt  	# hey! replace sda1 with your ubuntu partition
- mount --bind /dev /mnt/dev  	# this mounts also the devices found in your live session
- chroot /mnt			# access as root your linux install
- grub-install --recheck /dev/sda	# loads grub to mbr
- reboot			# will hopefully boot into your ubuntu
- update-grub2                  # this one to be run from your ubuntu install

Reboot, and the grub menu will have both karmic and xp.

---

### Post by Theist17 on 2010-01-11
This is why I love these fora. 

I'm backing up all my super-important files right now, and as soon as that's done, I'll be embarking on my journey! I've my LiveCD on hand (thanks to Canonical's generosity,) and will be setting aside a partition for XP shortly. 

Thanks for all the help, guys.

---

### Post by Theist17 on 2010-01-11
Okay, I've followed the directions given me by JC Cheloven, and at this command: chroot /mnt I'm hitting a wall. Here's the terminal output:

chroot: cannot run command `/bin/bash': Exec format error

Any ideas?

---

### Post by presence1960 on 2010-01-11
> **Theist17 said:**
> Okay, I've followed the directions given me by JC Cheloven, and at this command: chroot /mnt I'm hitting a wall. Here's the terminal output:

chroot: cannot run command `/bin/bash': Exec format error

Any ideas?

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

provides a simpler solution to restoring GRUB to MBR after you install windows.

---

### Post by JC Cheloven on 2010-01-12
> **Theist17 said:**
> Okay, I've followed the directions given me by JC Cheloven, and at this command: chroot /mnt I'm hitting a wall. Here's the terminal output:

chroot: cannot run command `/bin/bash': Exec format error

Any ideas?
As far as I understand, this means either that 
1) some of the previous commands were not successful, or
2) there is some problem in the (system) files at your partition

--> Did you ran the commands as superuser, right?

For the shake of confidence: The procedure worked for me several times. For example yesterday I recovered a system with xp in primary partition, karmic in logical, windows7 in logical (the user messed the boot installing that). After the outlined procedure everything was bootable.

Nevertheless, if you're sure you've kept the steps and still can't chroot to your ubuntu install, and you have no success with the other procedures adviced above, you can try [super grub disk]("http://super-grub-disk.softonic.com/linux")

---

### Post by Theist17 on 2010-01-12
Well, after following the instructions given me by darkod, I am now happily posting this from my new XP install. I plan to take a few Hebrew lessons immediately. 

Thanks for your help, everyone. You've been most supportive.

---

