---
title: "Grub loading, please wait ..."
date: 2004-12-01
forum: Installation &amp; Upgrades
---

### Post by frontline3k on 2004-12-01
Hi.
I tried today to install Warty on my home system, as my second OS, beside WinXP Pro (using a CD with the ISO image, also used to install in VMWare).

Everything was fine, until the system rebooted first time.
I get an prompt with
"Grub Loading stage 1.5
Grub loading, please wait ..."

I have 2 IDE hdds, first with 4 windows partitions, second with 2 windows partitions and some free space for Ubuntu.

I choose Manual partion in Ubuntu installer and made /hdb6 (ext3, 4.3 GB, mount point /) and /hdb7 (swap, 450 MB), both logical partitions.

Before that, I installed Ubuntu in VMWare and all was ok.
I don't think I made something wrong, I installed some Linux distro until now (I tested Mandrake, RedHat, Fedora, Vector, Gentoo on different systems, but I think all of them are using Lilo as default boot loader, and I'm somehow familiar with it).

I have to boot with the XP CD and run fixmbr to revive my system.

Any clue ?

Regards,
frontline3k

---

### Post by $K1NN3R on 2004-12-01
I'm having exactly the same problem. I searched through the rest of the forum but didn't find anything. I'm running a similar setup aswell
2 disks: 1st disk with 4 windows NTFS partitions and some space for Ubuntu, and the 2nd disk with 2 partitions. 

The first session went like a breeze and after the reboot it gave me exactly the same message.  ](*,)

---

### Post by frontline3k on 2004-12-01
So, at least I'm not alone  #-o 

Maybe some one can hear us ?
Any ideea ?

---

### Post by tjwhaynes on 2004-12-01
[QUOTE=frontline3k]So, at least I'm not alone  #-o 

Maybe some one can hear us ?
Any ideea ?[/QUOTE]

No - you're not alone. See that post about needing LILO on AMD64? That's the same problem.

The same issue has been reported for Fedora Core 3 as well and I've seen it on Mandrake 10.1. If I get a fix sorted out I'll post it here.

Cheers,
Toby Haynes

---

### Post by frontline3k on 2004-12-03
This could be a lead: [http://ubuntuforums.org/showthread.php?t=2689](http://ubuntuforums.org/showthread.php?t=2689)

I tried last night with Ubuntu Grub / Lilo and Mandrake 10.1 Official with Lilo, and the same problems.
With LILO I get only an "L' at boot.

I will try with Knoppix.

Cheers

---

