---
title: "Dual Boot Ubuntu and Win 2000 prof"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by oab on 2005-07-15
Yes, its another one of those 'wonderful' dual-booting threads! Before you ask, I did search the forums, I googled it, and I was not able to find the answer I needed.

Here is my particular situation.

I have one SATA drive, and one IDE drive. My SATA drive has one partition, NTFS, and its 160gb. It has Windows 2000 Professional on it, and it has the standard windows boot-loader.

My second drive has four partitions on it, it is an 80gb hdd. The first partition is a 30gb NTFS partion. The second partition is a 10gb FAT32 partition (for sharing files between Linux and Windows), the third partition is a 27gb is the root partition for ubuntu in EXT3 format, the fourth is a 2gb swap partition (one gb RAM, 2gb swap, pretty standard).

When Ubuntu installed GRUB, it detected my win2000 partition, but when I choose that from the GRUB menu, it gives me an error. It ways "NTLDR not found, press ctrl+alt+del to reset". Of course, when I go into my BIOS to change the options so that the SATA drive is primary, not the IDE (GRUB is on teh IDE drive) it boots perfectly. Obviously I do not want to have to go into the BIOS every time I want to start an OS.

Question, what is the GRUB config file (so that grub-install will work) for my situation?

I have an Asus K8V mobo, with the SATA drive on the VIA RAID controler (no raid set up though), and the IDE is on the standard IDE channel (its a master too).

I installed Gentoo once, so I have a somewhat vague idea of how to do this, but I dont trust myself to do so.

Thanks in advance.

---

### Post by al7kz on 2005-07-16
Hi oab,
You need to make this the entry for windoze in /boot/grub/menu.lst:

title Windoze
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive 
chainloader +1

The reason is windoze has to boot from the first hard drive, so this fools it into thinking it is. See

[http://ubuntuforums.org/showthread.php?t=48652](http://ubuntuforums.org/showthread.php?t=48652)

---

### Post by oab on 2005-07-16
Hey, thanks. Fedora was able to do this by default, too bad Ubuntu wasnt.

---

### Post by j.hill on 2005-07-27
Ok, here's a variation on the same question:

When I try to boot into Win2k, I get this message:

root (hd1,0)
     Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

Now it looks like I ought to do that mapping thing that al7kz was talking about.  My question is:  do the mapping lines replace "savedefault" in the menu.lst file?  or does "savedefault" stay in there?

Thanks --

---

### Post by al7kz on 2005-07-27
Salut, j.hill:

You can leave "savedefault" in or take it out. If you have

default 0  ###this defaults to the first entry in the grub menu###
timeout 10

it will have no effect, but if you have

default saved
timeout 10

and have 

savedefault

in every entry, then the last entry selected becomes the default.

For more grub fun google grub manual.

Ciao, al7kz

---

### Post by j.hill on 2005-07-28
[QUOTE=al7kz]Salut, j.hill:

You can leave "savedefault" in or take it out. [/QUOTE]

Merci al7kz, tout va bien maintenant.

---

### Post by jgibby on 2005-08-25
I have an IDE master that is partitioned twice, both NTFS with win2k loaded on them.  I installed Kubuntu on the IDE slave and have it running, but I cannot dual boot.  I get the same "ntldr is missing" message.  

I have been reading for a day or so and really can't comprehend what I am really supposed to do. 

Anyone here speak noob?  ](*,)

---

### Post by nkessler2000 on 2005-08-25
I have almost the exact same setup and exact same problem as oab. What's the solution?

---

### Post by Lord Hammer on 2005-08-26
I did it like this:

Installed Sys Commander v8 from Win2000.
Prepered space for 3 Linux partitions an 3 swaps (made partitions from within Sys commander).
I heard that there is the way to have only one swap partition for all installed distros but I didnt find that info yet.

I installed, and in this order ubuntu, kubuntu and linspire.

For some reason the Linspire has to be last installation. If not GRUB is reporting that partition is not recognised (error code 17) an i'm not able to boot the linspire partition.

thats it

---

