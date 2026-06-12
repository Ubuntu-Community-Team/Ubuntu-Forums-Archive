---
title: "Can not find operating system on startup"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by Episteme on 2006-09-01
I reformatted and re-installed ubuntu. On boot, I rec'd the error message:

kernel /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sda1 ro quite splash
Error 15: File not found

It gave me the option to boot from other kernels, but they give me the same error message.

I tried using dd if=/dev/zero of=/dev/sda and re-installing, but Grub reported Error 5 on boot.

I tried using my windows cd to reformat the drive, but it insisted on also reformatting my other drives as well - and since I don't want to lose what's on them, I disinclined to aquiess to it's request.

I used genome partition editor to clear up the partitions on sda and reinstal. On startup I got the message Can not find operating system.

I'm at a bit of a loss - what should I look into to resolve this problem?

---

### Post by galileon on 2006-09-01
um im not sure what you did with the dd thing, but thats something that scares the pants off me to be honest, and i believe (well lets hope im wrong) you have wiped all the partitions....and the gnome parted thing sounds bad as well...

but try to boot on a ubuntu dapper cd and have a look in System>Administrations>Disks and see if your partitions are still there, and try to mount them and see if your data is still there

into which partition did you install ubuntu? anyway it seems you wiped it now didn't you? in that case try to install it again, and cross your fingers...

---

### Post by galileon on 2006-09-01
i just saw your other thread,
[http://ubuntuforums.org/showthread.php?t=248556](http://ubuntuforums.org/showthread.php?t=248556)

actually the MBR is on the hdd device itself, ie /dev/hda, not /dev/hda1. 

(well, you can, but i never understood it, and it would need some special stuff on the MBR in /dev/hda anyway)

---

### Post by Episteme on 2006-09-02
ok - all fixed.

I downloaded the 'ultimate boot cd'  from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) - burned from iso and ran 'killdisk' - then installed to a squeeky clean hard drive.

Oh, I also tried to install Gentoo along the way... definately happier with ubuntu - that install was WAY too much for my lack of patience (it hung after 8 hours of compiling from source code).

---

