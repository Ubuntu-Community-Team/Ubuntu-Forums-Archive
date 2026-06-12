---
title: "what linux distro for windows file rescue?!"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by Cew27 on 2008-04-02
hey i am a member on a computer forum and would like to make a tutorial on how to recover files from a windows partition when it has gone corrupt using a linux live cd 
what would be the best for this ? 
knoppix?
ubuntu?
dls?
thanks

---

### Post by mikewhatever on 2008-04-02
Any of the above with NTFS support should do, but there are better tools for that, like Testdisk or Photorec.

---

### Post by Crafty Kisses on 2008-04-02
> **Cew27 said:**
> hey i am a member on a computer forum and would like to make a tutorial on how to recover files from a windows partition when it has gone corrupt using a linux live cd 
what would be the best for this ? 
knoppix?
ubuntu?
dls?
thanks
Ubuntu or Knoppix would be great.

---

### Post by Pumalite on 2008-04-02
Ubuntu is a good candidate. Just have to know how to mount your drives/partitions and then use the appropriate software to backup/restore.

---

### Post by POW R TOC H on 2008-04-02
Try injector linux!
[http://injector.sourceforge.net/]("http://injector.sourceforge.net/")
It supports even the God-forsaken filesystems!
Here's a list of available filesystems (taken from their site) :
ReiserFS,
ADFS,
HFS,
BEOS,
BFS,
EXT3,
MSDOS,
FAT16,
FAT32,
ISO9660,
JFS,
Minix,
FreeVxFS,
NTFS,
HPFS,
QNX4,
EXT2,
SystemV,
UDF,
UFS,
UMSDOS,
AmigaFFS,
Joliet,
BFS,

---

### Post by Cew27 on 2008-04-02
i will im not aiming for a specialised live cd for this i am just trying to boost the popularity of linux in the forum

---

### Post by munkyeetr on 2008-04-02
[Puppy Linux]("http://puppylinux.com/") is good also.

---

### Post by Cew27 on 2008-04-02
i would prefer one with good wireless drivers and pidgin/web browser so can you list all of the candidates for me :)

---

### Post by Crafty Kisses on 2008-04-02
> **munkyeetr said:**
> [Puppy Linux]("http://puppylinux.com/") is good also.

Yeah, Puppy Linux isn't too bad. :)

---

### Post by Pumalite on 2008-04-02
Puppy is good setting up wireless.

---

### Post by metalf8801 on 2008-04-02
check out Trinity Rescue Kit 
you can get some more info here [http://distrowatch.com/table.php?distribution=trinity](http://distrowatch.com/table.php?distribution=trinity)

---

### Post by Cew27 on 2008-04-02
its for absolute n00bs to use i will explain the recovery but as you can guess having best networking would be ideal so that the users can ask online and i can help them while they are ont he cd

---

### Post by Ptero-4 on 2008-04-02
Just get yourself a kubuntu liveCD iso and use reconstructor to add photorec/testdisk from apt, you can also add clamav as well and you'll have a portable virus removal toolkit too, then take the resulting modded iso and burn it as usual.

---

### Post by diaa on 2008-04-03
I suggest Knoppix as a full fledged distro and [sysresccd]("http://www.sysresccd.org") as a minimal distro(~150 MB)

---

### Post by Cew27 on 2008-04-03
ill give dsl a try

---

### Post by Tomatz on 2008-04-03
I own a small pc repair business. I find the best live cd to do this is system rescue cd:

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Its lightweight boots fast even on something like a p3. 

It contains:

ntfs-3g (mount ntfs filesystem with read/write privileges)

Gparted (the best partition editor gui by far)

Firefox

Window maker (graphical desktop just type **startx** to use it)

Xterm

Midnight commander (powerful command based file manager type **mc** in Xterm to run)

and all your basic command line tools

The only drawback (for a new to linux user) is that you need a basic understanding of bash shell commands (e.g to mount partitions) but if you learn to use them you will find this disc a very powerful tool.

---

### Post by prshah on 2008-04-03
> **Cew27 said:**
> hey i am a member on a computer forum and would like to make a tutorial on how to recover files from a windows partition when it has gone corrupt using a linux live cd 
what would be the best for this ? 
knoppix?
ubuntu?
dls?
thanks

A windows LIVE cd is also availible, but unofficial. See Google BartPE

---

### Post by twin_57103 on 2008-04-03
I tried Puppy for this sort of thing a while back and found it confusing - obviously, it was the user (me), but it might not be the best choice for a recovery system for Windows users, especially if they are not very tech-savvy.  The system I was working on wouldn't boot with an Ubuntu live CD, so I ended up using Knoppix - it found the hard drive easily and I was able to mount my flash drive (no CD burner or network card).

---

### Post by Cew27 on 2008-04-03
ok i have made the tut (have a look n youtube for cew27) puppy linux was fine 
cheers

---

### Post by munkyeetr on 2008-04-03
> **Cew27 said:**
> ok i have made the tut (have a look n youtube for cew27) puppy linux was fine 
cheers

I checked it out, and I would suggest finding a way to mount your camera in a stable position. I made it to the point when puppy was booting and I couldn't take the in-focus/out-of-focus blur and jumpyness of the camera.

Just a suggestion. :)

---

### Post by carolus on 2008-04-03
One nice feature about Puppy Linux is that you can remove the live CD after booting and then use your CD/DVD drive to back up your hard drive.  I once had to repair a NTFS disk by running chkdsk /f under DOS bofore Puppy would read it, though.

---

### Post by Cew27 on 2008-04-04
sweet i didnt know that! 
also tere really was no place to mount the mobile phone and i do have a digi cam that can take vids but it eats through batteries in 3 minuits

---

### Post by munkyeetr on 2008-04-04
> **carolus said:**
> One nice feature about Puppy Linux is that you can remove the live CD after booting and then use your CD/DVD drive to back up your hard drive.  I once had to repair a NTFS disk by running chkdsk /f under DOS bofore Puppy would read it, though.

Correct me if I am wrong, but in order for that to work, you need to use the boot parameter:
```

puppy pfix=ram

```

in order to load the livecd completely into ram.

---

### Post by az on 2008-04-04
[http://ubuntu-rescue-remix.org](http://ubuntu-rescue-remix.org)

The Rescue Remix provides a Free-Libre Open-Source data recovery software toolkit based on Ubuntu

The Rescue Remix is an Ubuntu derivative and is current, up-to-date and stable.  It uses the very latest Ubuntu kernel/device drivers and live cd infrastructure.  It boots from CD or USB stick.  It is a complete GNU/Linux command-line-system and has every free-libre data-recovery solution included.

As for recovery files from Windows, it depends.  If the drive is damaged, you need to image it using gnu ddrescue.  If the filesystem is not fixable, you need to data-carve the files out without using the filesystem.  The tools needed for this are included with the Rescue-Remix.

---

### Post by Tomatz on 2008-04-04
That's great!

Just what i have been looking for as live cd gui's are crud on older hardware :)

---

### Post by carolus on 2008-04-04
> **munkyeetr said:**
> Correct me if I am wrong, but in order for that to work, you need to use the boot parameter:
```

puppy pfix=ram

```

in order to load the livecd completely into ram.

No, that is not necessary. The default is to load all of puppy linux  (80-90 Mb) into ram, if it will fit. I think the boot parameter you quote is used to ignore any prior puppy session you might have saved.

Puppy also has a decent WiFi configuration wizard, in marked contrast to Knoppix.

---

### Post by munkyeetr on 2008-04-04
> **carolus said:**
> No, that is not necessary. The default is to load all of puppy linux  (80-90 Mb) into ram, if it will fit. I think the boot parameter you quote is used to ignore any prior puppy session you might have saved.

Puppy also has a decent WiFi configuration wizard, in marked contrast to Knoppix.

Good to know, thanks.

---

