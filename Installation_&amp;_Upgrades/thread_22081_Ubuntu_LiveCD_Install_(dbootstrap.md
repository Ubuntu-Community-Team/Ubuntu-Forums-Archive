---
title: "Ubuntu LiveCD Install (dbootstrap"
date: 2005-03-25
forum: Installation &amp; Upgrades
---

### Post by twodeko on 2005-03-25
Hello All...

I am new to this Ubuntu (gentoo gave me some grief) and threw in the amd64 (warty 4.10) install cd downloaded from the university of minnesota mirror that is listed as a mirror.  I have gotten past the screen where I can partition the disks and set it up properly but to no avail, i always get the following error.

" No matching physical volumes found
No volume groups found
Reading all physical volumes. This may take a while...
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error
cp: Write Error: Input/output error "

I have tried the expert installation, flagging the partition to allow ubuntu to format them (I am unsure whether it actually does, since it just creates the file system and formats swap) but this error returns again and again.  I have looked through numerous posts here trying to figure it out but I can not for the life of me.

Multiple disks were burned (although some were not bootable) on different speeds since the error reports a debootstrap error and says the medium might be back.  A test on the medium comes up as a big NO every time even though i have verified the data being written with the program.  

Some ideas...
The CDROM drive has been used to install GENTOO and the Debian cd appears to work although i havent followed through with the install.  It appears to me that the CD isn't reading the install CD properly, is there anyway to slow down the read speed?

I have tried the noapic kernel config but that did now work either.  From what I have heard I would like to try Ubuntu but this is a pretty big step to get past  ;-)

[edit] my machine...
AMD64 3400+ / MSI K8N Neo Platinum
512MB Cas2 DDR / 2x WD160, 1x WD200, 2x WD36 Raptors (1 WinXP, 2 Linux)
ATI 9800 Pro / RME DIGI 8/96 PAD
PIONEER 106 DVD+/-R/RW / SAMSUNG 193P

solved: USE 5.04

---

