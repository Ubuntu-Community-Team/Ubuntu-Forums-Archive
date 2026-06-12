---
title: "Install ubuntu as a secondary OS"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by UKCamaroSS on 2007-10-10
Hi,

I am completely new to Linux.

I currently have a pc which I built myself, running Windows XP MCE. I have had this pc for 2 years and have lot's of items stored on it, such as movies, tv, photos, email etc - which I do not want to loose.

I would like to set ubuntu up to run as a dual boot alongside my current XP. 

Do I need to completely reformat my harddrives, or will the ubuntu install allow me to keep my existing items?

Thanks,
UKCamaroSS

---

### Post by Pumalite on 2007-10-10
Post your specs.How many drives' Graphics?Memory?

---

### Post by UKCamaroSS on 2007-10-10
Hi,

Thanks for the quick response.

I have :
AMD Athlon 64 3000 cpu.
Nvidia Geforce FX5700 LE graphics card
75 GB main hard drive
250 GB secondary hard drive
512 MB memory

Thanks,

---

### Post by phr0ze on 2007-10-10
The Ubuntu install will automatically resize and partition your drive for you if there is enough room. It happens on Step 4 of the install. When you boot up you will have a new menu to choose XP or Ubuntu.

It's standard thing to always tell anyone to backup their data before doing anything on a computer. So there you have it.

---

### Post by Pumalite on 2007-10-10
Dual booting in one same drive or installing Ubuntu in it's own drive and in that case, which one?

---

### Post by phr0ze on 2007-10-10
Ohh, Sounds like you copy, move and delete lots of files, so don't forget to defrag in windows before installing.

---

### Post by Pumalite on 2007-10-10
Ideally XP should be installed first. If you can give Ubuntu an entire drive, better. If not: defrag several times, erase all temp files, backup your data and use Gparted to 'shrink' your XP partition.
A good scheme for Ubuntu is:
10 GB for '/'
2xRAM up to 1 GB for /swap
The rest for /home.

---

