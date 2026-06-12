---
title: "Grub Installation dilemma !!"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by blooboy on 2008-01-19
Hi Folks !

I have two hard disks. My $dows hard disk is Primary and Linux is secondary drive.Due to fear of overwriting the MBR of my $indows disk(primary)
, I removed this primary Windows Disk physically and installed PCLinuxOS and later Ubuntu Gutsy on my slave Disk.

Now Ubuntu's grub runs when I run my system.  Now I am pressing F11 while booting to select whether I need to work on Win or Linux. 

My problem is that since I attached my Windows disk as primary later, my Grub is not showing Windows partition. 

How do I enable $indows (in primary disk) in the grub of my slave disk??

Primary Disk - $indows - hda
Slave Disk   - Linux   - hdd

I tried using Super Grub Disk but got confused !!

Please help.

---

### Post by torgrot on 2008-01-19
My suggestion is to swap the drives.  Make the primary the slave and the slave the primary.  Then follow the instruction at this link.[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
That way nothing happens to your windows disk at all, and you will be able to boot either operating system.  If ubuntu isn't for you, then all you have to do to remove is switch the hard drives back and fdisk the ubuntu drive.

torgrot

---

### Post by blooboy on 2008-01-20
Thanks for suggestion. But Ubuntu is like an airplane with elaborate gears and meters. You can't expect a noob to just climb over the plane and fly it like a bird. So noobs like us need advice from u techies and not sarcastic comments :|

---

### Post by blooboy on 2008-01-20
Bytheway **Torgrot** , that [Bigpond]("http://users.bigpond.net.au/hermanzone/p15.htm#Bigpond") page was fantastic !

---

### Post by c0met on 2008-01-20
Blooboy, I'm sorry, but I do not see how Torgrot was being sarcastic. The way that I read his typing is that he was offering you some sound and sensible advice.

---

### Post by innoBy on 2008-01-20
I'm a noob at this as well, and frankly the only reason to use windows is if you game at all. That's it, Ubuntu does the rest of it perfectly well, you've got all your drivers natively supported, and it also supports bittorrent and other programs that most windows users use alot.

You have to admit having an OS that the people making it don't come and screw with you when they can is nice.

---

