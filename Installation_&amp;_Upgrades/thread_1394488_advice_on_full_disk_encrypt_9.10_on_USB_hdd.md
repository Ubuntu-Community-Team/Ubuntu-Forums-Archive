---
title: "advice on full disk encrypt 9.10 on USB hdd"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by DizzyCoder on 2010-01-30
Okay, so I have an external USB TB hdd that I keep stuff on.  Surely, I would not want to lose it or have it stolen, but it happens.  My idea is this:

* install 9.10 using alternate CD w/ LVM encryption
* boot off the drive while on the go and access my data
* plug in and mount only the 'data' partition while at home

I can get so far w/ this setup, but it's not portable -- I can only get it to boot from the computer I installed it on... otherwise I get a "no such partition" error.  

at the grub rescue> prompt an 'ls' gives me just (hd0) and (hd0,1) whereas the /boot partition (as we know from the 'guided setup with LVM encryption') should be at (hd0,5)

1) I wonder if it's just a weird BIOS thing that makes it so I can't boot from my workstation, figured I could chainload the disk if I wanted to boot from USB at my workstation

2) would it not be just as adventageous to use USB Live install on FAT32 partition at the front of my disk and create a LUKS partition for my data after that...
 a) I ask, b/c from a security stand point, the whole disk is not encrypted and (although unlikely) it is possible to gleen information needed to break the encryption from the persistence file and/or swap (does the live USB even have a swap partition??)

3) I've read VARIOUS tuts on the subject but none seem to be exactly this "portable ubunut 9.10 on LUKS full disk encrypted USB" -- am I over complicating this?  What would you do if you wanted a way to boot the USB drive on multiple computers but keep your data safe?  
 a) I also wanted to have an unencrypted partition that could contain downloaded files, etc, which are not sensitive in nature and could help while plugged into a windows PC... ie: FreeOTFE, ISO's that could be chainloaded from GRUB (ie: backtrack, antivirus live CD's, etc)

---

### Post by DizzyCoder on 2010-01-30
Well, I'm thinking that my booting problem has to do with my workstation... "no such partition" is kind of vague and can't understand why GRUB w/ load from the MBR but not see the /boot partition on same drive.

Anyhow, I used the this post about [resizing an encrypted filesystem]("http://ubuntuforums.org/showthread.php?p=4530641") to help me accomplish my partitioning needs, and what I ended up with is this:

1x LVM Encrypted volume group of 988GB
-> 10GB root (ya, ya, it's a lot, but there's room to spare =)
-> 1GB swap
-> 977GB NTFS partition 'data'

1x extended partition with 
-> /boot
-> 12GB FAT32 'unsafe' (with a copy of FreeOTFE, and hopefully soon some ISO's to chainload)


So I can keep this drive hooked up to my workstation (Karmic) and then grab n' go and hookup to a Win box or boot a USB bootable PC w/ my encrypted karmic and all my data is safe if I lose it.  Also fun is that b/c the install is persistent, I can continue to add tools to the repatoir and use it as a portable workstation / repair boot.  I've configured it to autologin as well so that I only enter the passphrase on boot up and wait for desktop to finish loading.

Thoughts, questions, flames?


Further thoughts are that I'm going to (am open to other neat suggestions):
* add a secondary encryption pass phrase using cryptsetup (so my wife will be able to unlock)
* export a key file to USB and mail to a relative (in case I get hit by a bus and my wife forgets her strong keyphrase)
* not sure if I'm fancy on it yet, but I might put the Netbook Remix configuration on it

---

