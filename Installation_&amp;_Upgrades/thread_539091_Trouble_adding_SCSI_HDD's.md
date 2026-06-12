---
title: "Trouble adding SCSI HDD's"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by okeefe415 on 2007-08-30
im having some issues installing my scsi hdd's into my new box...

ive done all the /dev/xxxxxx stuff, but i cant get it to work... pretend im a baby, what do i do REALLY, step by step...

theres a pci raid controller in the mix as well...

---

### Post by Pumalite on 2007-08-30
You have to explain your problem better. And if you have a Raid Array make it clear too.

---

### Post by okeefe415 on 2007-08-30
what else would you like to know, ill tell ya whatever ya need

---

### Post by Pumalite on 2007-08-30
I want to know everything. If you want to know the truth, I don't know if you are trying to build a computer or trying to install Ubuntu.

---

### Post by okeefe415 on 2007-08-30
kk heres the system

an older server at my work that i was given, literally JUST installed ubuntu, and the only hd it sees is the IDE drive. It sees the scsi controller and i DO beleive (but am not sure) that it is indeed set up in a raid array.


it has 5 hard drives...

one IDE
and 4 SCSI hot swapable

im gonna go crack it open and try and take a look, but as of now, this is all i know...

---

### Post by okeefe415 on 2007-08-30
kk i check the system and the SCSI's all come together through one PCB, from there via ONE SCSI ide cable, they attack directly to the motherboard.

---

### Post by Pumalite on 2007-08-30
Do you have a working Ubuntu now? If so, then post: sudo fdisk -l (small L)
If you do not have Ubuntu installed, then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and take a look at your drives and report what you see.

---

### Post by okeefe415 on 2007-08-30
yes, i do have ubuntu installed allready... by post what do you mean? im fairly new to ubuntu, but know alot about pc's in general...

---

### Post by Pumalite on 2007-08-30
Applications>Accessories>Terminal>sudo fdisk -l>Copy and paste in your post here.

---

### Post by okeefe415 on 2007-08-31
allright tomorrow ill post what i get when i do that.

---

