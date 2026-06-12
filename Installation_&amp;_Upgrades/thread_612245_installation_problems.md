---
title: "installation problems"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by davebridges on 2007-11-13
Hi everyone, I had 7.10 installed on my home computer, but decided to install windows in a new partition.  I put in the windows install cd, and it said it had to mask the linux install, which seemed like an ok idea at the time.  Problem is, the windows wouldnt install (something about a NTLDR file missing).  Worse, now i cant get back into ubuntu.  I tried re-installing, but the machine hangs while trying to do the linux live cd disk.  It gives me many many SQUASHFS errors, then eventually  gives the ubuntu warrantly disclaimer and thats it.  No commmand line or anything.  Anyone here have any idears?

---

### Post by Pumalite on 2007-11-13
Try Super Grub, but it looks like a reinstall. This time install Windows first. Try DNuking your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD to format your drive ntfs prior to installing Windows: 
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Then, boot Gparted again and resize your XP partition, then install Ubuntu. If Vista, install it, then use Vista partitioner to allocate space for Ubuntu.

---

### Post by davebridges on 2007-11-13
crap

there is also a bunch of buffer i/o errors.  

so is the order xp then ubuntu important?

---

### Post by davebridges on 2007-11-13
ok actually this time i got a command prompt instead of the live cd gnome display.  does that mean anything?

---

### Post by Pumalite on 2007-11-13
Try booting with your Live CD now and post:
sudo fdisk -lu

---

