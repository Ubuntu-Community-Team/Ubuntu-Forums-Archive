---
title: "bad install = no CD boot"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by dracule on 2006-06-26
I had to reinstall ubunut 5.10 on my computer, but the problem is the installation froze and now it wont read any of my cd's. the system is set to boot from cd-rom first  but all it does it read the cd and boots from the HDD (it says Grub error 15). I  was wondering if there is a way i can download ubuntu (old or new) from a floppy disk(load vital modules and then download the rest from network). If I cant do this with ubuntu, could you tell me if any other linux distros let me do this.

---

### Post by x64Jimbo on 2006-06-26
Can you disconnect the hard disk and see if it will boot from CD then? that symptom is extremely weird and I don't know what could be happening. Troubleshooting is a good first step though.

---

### Post by zxee on 2006-06-26
[http://www.debian.org/](http://www.debian.org/)
and
[http://www.debian.org/distrib/](http://www.debian.org/distrib/)
You can definately do a net install of debian. I thought you could do that with ubuntu but I didn't see any links here..
I don't know why you're getting a grub error with the live/install cd in the drive-strange.

---

### Post by dracule on 2006-06-26
I installed debian, but it only installed script prompt... how do you install Gnome?

---

### Post by zxee on 2006-06-26
[QUOTE=dracule]I installed debian, but it only installed script prompt... how do you install Gnome?[/QUOTE]
Welcome to the world of debian and apt. I might migrate back to debian myself considering how poorly ppp is...well functioning would be good-nah it's entirely dysfunctional-don't mind me I keep trying to use dapper and ](*,) 
Whatever, as root use apt-get install gnome-common. Also check out man apt and look at the package list at debian. Hope that helps.

---

### Post by dracule on 2006-06-26
under installed pakages in Aptitude it has gnome listed but it will only boot up into script.

---

### Post by dracule on 2006-06-26
Ok now i got gnome running, but I hate Debian, it looks so old.... can you direct me to a link to install ubuntu from a USB storage device, without going through the boot process(like a normal install)?

---

### Post by zxee on 2006-06-27
[QUOTE=dracule]Ok now i got gnome running, but I hate Debian, it looks so old.... can you direct me to a link to install ubuntu from a USB storage device, without going through the boot process(like a normal install)?[/QUOTE]

There are threads here on this-a how to in the install & upgrade forum today but it might not be what you want. I think you're doing this the hard way though because if you enable the testing repo for debian you can upgrade to a more modern looking gnome. Also there's gnomelook.org that lets you change anything you want to. Take a look back at those first links I posted, there should be a how to for debian on enabling debian testing. I'm having problems with my connection-but do a search on enabling debian testing.

---

