---
title: "GRUB loader not letting me choose anything (and an X server afterwards)"
date: 2006-04-06
forum: Installation &amp; Upgrades
---

### Post by kaif on 2006-04-06
Help! Just installed Ubuntu on my system on a partitioned hard drive (which has XP installed on it). The installation went fine with no problems or error messages, but I have now encountered 2 major problems.

The first problem is the GRUB loader not letting me select what operating system I want to use. I press up and down and it just doesn't select anything, All the operating systems are listed correctly, it's just that pressing up and down does nothing (there's definately nothing wrong with the keyboard itself because I can navigate my BIOS menu just fine). I have no choice but to boot up in Ubuntu, which makes it a pretty useless bootloader and also leads me to my second problem...

Ubuntu won't load the desktop! I instead get an error message saying: 

"Failed to start the X server (your graphical interface) It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

then I'm just dumped into the command prompt.


This is very upsetting, now I can't actually use my PC at all because I can't even boot from windows because the GRUB loader doesn't work ](*,) 

Any idea what the problem could be? I don't understand how it can go so horribly wrong, I intalled ubuntu on my laptop with no problems whatsoever. :(

Just so you know, I have 2 hard drives one which has XP installed on it (the one I'm trying to install Ubuntu onto) and the other has all my files and stuff (I don't want to install Ubuntu on this). I also have an ATI 9800 and an AMD 64. Please help! Thanks.

---

### Post by kaif on 2006-04-06
Actually, just realised after having written that post, I think I may have installed the x86 version instead of the AMD64 version, Oops!

Do you reckon running the AMD64 installer (deleting the old Ubuntu partition and reinstalling) will solve my GRUB problems too? or am I still a bit screwed?

---

### Post by kaif on 2006-04-06
Hmm... no luck with the AMD64 version. Even tried using Dapper flight 6 (live CD version) and still got the X server problem.

Ah well, I guess it's just not meant to be...

(lol, I'm talking to myself now)

---

### Post by greenstar on 2006-04-06
I've run into a computer that wouldn't take Ubuntu. I think it was P4 64bit with a Sapphire Radeon (don't recall model), 1 DVD-RW and a single SATA disk. Most times it would flake out during installation of Breezy, but when I installed Hoary everything went well until I did apt-get dist-upgrade. After the upgrade, I got the same thing as you. I tried all kinds of special install options and never figured it out. Eventually I gave up and installed WinXP. I chalked that one up to hardware incompatibility.

Sorry I can't be more helpful.
Greenstar

---

### Post by kaif on 2006-04-06
That's a real shame, I was looking foward to having Ubuntu on my main PC.

Any ideas on what alternative (non-commercial) distros I should use? Bearing in mind that I'm totally new to Linux and want to avoid the problem mentioned above.

---

### Post by greenstar on 2006-04-07
I've been impressed with [PCLinuxOS]("http://www.pclinuxos.com/page.php?6") and [BLAG]("http://www.blagblagblag.org/"). You may have better success with another distro, and PCLinuxOS is reputed to have a great community also.

Greenstar

Edit: 

P.S. I think PCLinuxOS is somewhat of a Mandriva/Debian hybrid or maybe just Mandriva based with synaptic, apt-get, etc. BLAG is Fedora Core based with synaptic.

---

