---
title: "Installer freezes on 'Grub' package"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by Goatee on 2006-04-12
I have very recently bought and built a new PC with:
-Athlon64 x2 3800,
-2* Nvidia 6600Gt (SLI)
-1GB corsair valueselect ram
-939SLI-esata2
-DVD (read write and do the cancan) drive
-CD read drive
-Floppy drive 250GB western digital Sata2 drive
-Creative labs (old) sound card
I have downloaded Breezy Badger 64bit and it installs until...
'Installing Grub package'
It then sits on 0% and does nothing.
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

I have also tried to install:
Suse 9.2 (64 bit) (doesn't recognise the hard drive),
Mandriva 2006 (32 bit) (refuses to "go graphical" or install nvidia drivers).

I am not going to buy xp or 2k.

Any ideas what I can do to make it run?

:rolleyes:  Thanks in advance  :rolleyes:

---

### Post by dbd on 2006-04-12
Does the ubuntu live CD work? It might be worth testing that first.

Also, have you tried the 32bit version?

---

### Post by towsonu2003 on 2006-04-12
other than trying the live cd, make sure you do these with the instal cd:
1. after downloading iso, check md5sum
2. burn to cd at slow(est?) speed

---

### Post by lanux on 2006-04-12
I have same problem with grub install
With LiveCD and install CD I get grub install error

---

### Post by Goatee on 2006-04-13
I've reburnt it but I have a download limit and can't get the live disk.
Hope it works.:mrgreen:

---

### Post by cyrus7580 on 2006-04-13
Same problem here. Breezy AMD64 5.10. Athlon 64 x2 3800.

---

### Post by Goatee on 2006-04-14
I did as suggested and I have re-burnt the ISO. For the record if you select verify written data in K3B it will check the MD5 sum. (I first tried in nero) and it failed so...

The lesson I have learned from this is that if you want something to work avoid commercial software (if you can). ;)

---

### Post by Goatee on 2006-04-14
Aka:
It Is Fixed!
:d :d :d

---

### Post by cyrus7580 on 2006-04-14
This is NOT solved yet.

I'm really not sure why the integrity of the CD or how it's burned has anything to do with whether or not the grub package installs. But, against my judgement, I used k3b to burn another CD, this time burning at the slowest rate and verifying the data.

It was a giant waste of time. It did nothing to help the situation.

I think, basically, the install program is broken. Have other people had success installing on AMD 64 3800 X2 systems before or is the technology simply too new?

---

### Post by towsonu2003 on 2006-04-15
[QUOTE=cyrus7580]
I think, basically, the install program is broken. Have other people had success installing on AMD 64 3800 X2 systems before or is the technology simply too new?[/QUOTE]
I see this as *the* time to file a bug report. Go to [https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)
and file a bug report under the package base-installer (they will fix it for you if this is the wrong package). 

Do **hurry** so they fix it before the stable release (if it's broken in Dapper as well) so you can happily install Dapper (along with everyone else using your hardware). 

PS. There is no "too new technology", just "not-yet-fixed/filed bug" ;)

Did you by the way try the install CD? for Dapper I mean? If it doesn't work in Dapper either, you can relax a little because they will then fix it almost for sure...

Edit: if you try Dapper and it doesn't work, make sure to note that in the bug report.

---

### Post by cyrus7580 on 2006-04-15
Bigtime bonehead move on my part. Believe it or not, my SATA hard drive was plugged into the wrong slot (SATA3 as labeled on my motherboard) when it should have been plugged into SATA1. I'm assuming that the Breezy installer program got mixed up when trying to write the boot record or grub or whatever.

(I was tipped off to the wrong drive cable when FC5 install complained of something about ttys2)

Thing is, though, maybe this still is a bug. Why shouldn't the install program just use my hard drive anyway? even if it's not plugged into the first serial port?

---

### Post by Goatee on 2006-04-15
Hard drives are both mysterious and fussy
](*,) :confused: ](*,) :confused: ](*,)

---

### Post by cyrus7580 on 2006-04-18
Still having some trouble.

Having the SATA plugged into slot 3 definitely was a problem and, yes, moving it to SATA 1 did fix that problem.

However, I'm now trying to set up a RAID array and have run into (yet again) the grub install problem. My Raid setup is like this

Disks: 4x400GB SATA
/boot: RAID1 ext3 made from one 110 MB logical partition on each disk
swap: one 2GB logical partition on first disk
/ (root): RAID5 ext3 made from the remaining 400GB logical partition on each disk

So, I'm back to hanging at the grub install again. Grub is installed in the master boot record right? So maybe the installer is having trouble installing grub on my RAID1 array?

---

