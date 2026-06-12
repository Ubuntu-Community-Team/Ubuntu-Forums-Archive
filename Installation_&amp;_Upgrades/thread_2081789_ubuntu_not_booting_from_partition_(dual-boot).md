---
title: "ubuntu not booting from partition (dual-boot)"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by PortableSounds on 2012-11-07
So yesterday I finally installed ubuntu onto my main 2.2 TB HDD beside my Windows 7 Home Edition (on a different partition). I made a /, /home,  swap with plenty of space (24 GB home, 8200 MB swap, and 800 GB root (which will be shrunk at some point)). I also created a 2 MB BIOS boot partition with GRub2's core.img in it. I booted up my computer today, and when my HDD loaded, it only gave me an error about windows 7 being unable to boot. I said boot normally, and it did just fine. The error doesn't show up any more, but ubuntu is totally ignored. The results from my boot info script (sda1 being my HDD) are attached below. My computer specs are as follows: Motherboard: MSI 890FXA-GD70, RAM: 8 GB Corsair Vengeance, HDD: Seagate Barracuda 2.2 TB, CPU: AMD Phenom II x4 975 OC'd to 4.06. Thanks!  -Portablesounds

---

### Post by Bucky Ball on 2012-11-07
Welcome to the forums. You should have sizes of /home and / the other way around. /home is where all your personal data - music, movies, documents, whatever - are going to go. For that, 800Gb is better; 24Gb will get you nowhere and is far from 'plenty of space' for /home, in fact just the opposite. ;)

You don't need anything bigger than probably 15-20Gb for /. Only the OS and apps are stored there (I've never used anything bigger than 15Gb for /).

You should give Boot Repair a go. Check the repositories as it might be in there now, but if not:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

/ = 15-20Gb
/home = big as you want
/swap = 2Gb is all you need. 8Gb a waste of space.

In that order. One other thing to remember, although you may be aware, is that 4 primary partitions is the max on one physical drive. Generally, 3 primary and an extended partition with as many logical drives as you like inside that.

---

### Post by PortableSounds on 2012-11-07
> **Bucky Ball said:**
> Welcome to the forums. You should have sizes of /home and / the other way around. /home is where all your personal data - music, movies, documents, whatever - are going to go. For that, 800Gb is better; 24Gb will get you nowhere and is far from 'plenty of space for /home, in fact just the opposite. ;)

You don't need anything bigger than probably 15-20Gb for /. Only the OS and apps are stored there (I've never used anything bigger than 15Gb for /).

You should give Boot Repair a go. Check the repositories as it might be in there now, but if not:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Sorry, i believe i may have reversed those #s anyways. sorry about that. Will try the boot repair. Thanks for quick response!

---

### Post by PortableSounds on 2012-11-07
Okay, I used the repair, but it still didn't work. Same error, along with an unrelated error on my Linux Live USB about MDR login and authentication error or something. Anyways, I was unable to move the boot partition (since it's located past my windows 7 1 TB boot partition). I also have no free space at the beggining of the disk.

---

### Post by oldfred on 2012-11-07
You have installed Ubuntu in BIOS mode and have Windows in UEFI mode. They both must be in the same mode to work.

Boot-Repair can convert a BIOS install of Ubuntu into a UEFI install. It uninstalls grub-pc and installs grub-efi. And updates fstab and entires in efi partition.

You do not need bios_grub partition if using UEFI only with BIOS.

How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
UEFI installs in BIOS, Boot-Repair to fix
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)
[http://ubuntuforums.org/showthread.php?t=2058453](http://ubuntuforums.org/showthread.php?t=2058453)

grub2's os-prober also creates a BIOS chain load boot entry. Boot-Repair will add a correct efi chain entry for Windows.

---

### Post by PortableSounds on 2012-11-07
Okay, after several hours of work, I have still been unable to get it to work. I made sure that the bios_grub partition was deleted and also that the boot for ubuntu was in the efi file with windows. It won't read it and only says that windows was unable to boot due to changes in the boot files. Time for me to hit the sack, but I will check tomorrow afternoon for any updates. If there's any other info you need, just tell me.

---

### Post by oldfred on 2012-11-07
The os-prober entries from updating grub create the BIOS style boot entries. With efi you have to have a different entry. Boot-Repair can fix it.

Chainload entry:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
[http://ubuntuforums.org/showthread.php?t=1934773](http://ubuntuforums.org/showthread.php?t=1934773)

---

