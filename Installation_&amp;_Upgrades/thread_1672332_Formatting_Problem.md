---
title: "Formatting Problem"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by KNBsk8 on 2011-01-20
Hello, just recently I have buillt a new pc. I installed a copy of the Ubuntu v10.10 64-bit iso and burned it to a disc. I ran it on my newly build PC and chose to format the whole disk on the formatting options menu. The disk is a WD 160GB caviar. The installation began but halted half-way through exclaiming there was a batch of corrupt files. So, I downloaded a new copy burned it this time with InfraRecorder. And tested it for corrupt files. None found. So I am now confused on what option to choose on the formatting menu that appears after the keyboard identification test that appears when I put it the freshly made 'non-corrupt' CD.

The formatting options are:
Resize partition #1 and use free space
Use entire partition #1
Use entire disk **[COLOR=Red](Option I chose before)[/COLOR]**
Use entire disk and set up LVM
Use entire disk and set up encrypted LVM

Please help!

Thanks,
  KNB

---

### Post by garvinrick4 on 2011-01-20
# Use entire disk is fine
#You can if you choose to go into Ubuntu live CD (install CD using Try Ubuntu)
Choose gparted in System/Admin:
You can format there:
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted) 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by KNBsk8 on 2011-01-20
I chose "Use entire partition #1"

The download comensed but turns out there are corrupt files.. ugh. I am using alternate download btw. so its text base my CDs are only 700MB.

---

### Post by garvinrick4 on 2011-01-20
Have not used alternative, are you attempting to install Natty 11.04?
It is in Alpha stages and some daily iso's are buggy.
## I am sorry I see you are using 10.10 that is under 700 meg for desktop versions
and very stable and easily installed.

---

### Post by KNBsk8 on 2011-01-20
Nope just 10.10 64bit.. The main install is 9 more MBs more then the text-based alt.
Can I put my soon to be Ubuntu HDD into this pc and install ubuntu onto it and then move it back to my other pc?

---

### Post by garvinrick4 on 2011-01-20
695 meg link below

[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by KNBsk8 on 2011-01-20
But i cant just install onto the HDD via my main PC, remove the HDD, put the HDD into my second PC, and boot up with ubuntu??

---

### Post by garvinrick4 on 2011-01-20
It is said to be OK but I have never done it or found a reason to remove a drive to install an Operating System so do not want to give an opinion on anything I have not done.
Some one will come along that has done it before. This reply will bump your thread up.

---

### Post by presence1960 on 2011-01-20
You can put the hard disk into another PC and do the install, under certain conditions. Since the disk will be sda in your new build you must set that disk in BIOS to first in the hard disk boot order  in the "install" machine prior to starting the installation. This will avoid having to boot to the Live CD when you put it back in the new machine to edit grub.cfg and possibly fstab.

Once the install is complete put the disk in the new machine and then return the hard disk boot order in BIOS of the "install" machine to it's original configuration.

P.S. Make sure you put GRUB on sda on the install.

I learned the hard way about setting the  "new disk" as first to boot in BIOS. The first time I attempted it would not boot.. But I booted a Live CD and made the changes in grub.cfg.  I have done this about 3 times all with success

---

### Post by KNBsk8 on 2011-01-20
Awesome! Should work super then.. the only problem is my PC is not recognizing the HDD under "My Computer", I can find it under disk management but nowhere else.. Odd, any ideas?

---

### Post by presence1960 on 2011-01-20
> **KNBsk8 said:**
> Awesome! Should work super then.. the only problem is my PC is not recognizing the HDD under "My Computer", I can find it under disk management but nowhere else.. Odd, any ideas?

My Computer or Windows Explorer will not recognise it as it is not formatted. Even though your install failed you still have an unformatted disk. Under disk management format the disk as NTFS and see if it succeeds. if it does and windows recognizes the disk you can then set up ubuntu on it. Boot the Live CD USB and choose use entire disk, but make sure you have the proper disk selected.

P.S. after it is formatted and recognized make sure it is set to first disk in the hard disk boot order in BIOS prior to installing ubuntu.

---

