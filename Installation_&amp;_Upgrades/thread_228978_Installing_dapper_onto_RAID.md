---
title: "Installing dapper onto RAID?"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by wr0x2 on 2006-08-03
I have a system with two 320GB drives in hardware raid0. My chip is made by silicon image, and I'm fairly sure that it works because here in the Disks admin, my two drives are listed seperatly, however on the first appears 1 partition approx 600gb in size. I can mount it and all that good stuff, but I've had some trouble getting ubuntu installed on the entire raid, and not just the first drive. Should I make my partitions before I do the install process so I don't have to use gparted? Someone with experience please help!

---

### Post by wr0x2 on 2006-08-04
There has to be an easy way to do this. Is dmraid what I'm looking for?

---

### Post by mdelorme on 2006-08-04
I wasn't successful with getting hardware raid working on my machine with Ubuntu.  Unfortunately my machine does not run a true hardware raid, but instead uses AHCI (fakeraid... see [http://linuxmafia.com/faq/Hardware/sata.html)](http://linuxmafia.com/faq/Hardware/sata.html)).  Check to see if your chipset is listed on this site.  The description provided there (assuming it's listed) will give you a better idea of where to start looking for a solution.

Alternatively, Fedora Core 5 detected my "hardware raid" automatically at install time.  Should you absolutely need to run hardware raid (as opposed to a linux software raid) but cannot get it working with ubuntu, i'd investigate other distros.

---

### Post by mdelorme on 2006-08-04
as far as i know, dmraid is only used for linux software raid.  I am not positive, but i don't think it will solve your issue.

---

### Post by wr0x2 on 2006-08-04
I installed dmraid, and now gparted shows a sil_$bunchofchars device thats the correct size of my raid. only problem is that last time I installed doing this, my system would not boot, even though I had boot from RAID in my bios...

---

