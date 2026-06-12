---
title: "Boot Diskette for Ubuntu??"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by narayanb on 2006-09-12
im new 2 ubuntu...but i instantly liked its interface... i seldom switch 2 windows.. nwadays..
i hav updated my sys with latest packages and now i dont want 2 lose my installation..
if atall i lose d bootloader or wish 2 reinstall windows(i might very well) how 2 i restore d bootloader for ubuntu? can i create a boot floppy for it??

also, when installing ubuntu..it never asked d bootloader options... i hav 2 hdds...one is sata(new one) and a normal ata hdd.. dat was my 1st hdd and wer windows was installed.. now with my new sata i installed ubuntu... need 2 knw wer actually grub is installed??
wen i created a new partition in d sata(at beginning cylinder,ofcourse) i lost my bootloader and i REINSTALLED ubuntu(ie i lost my old one)..i dont want dis 2 happen again
sorry for d long post..

---

### Post by MikeMLP on 2006-09-12
it is best 2 use d alternate install disc so u can decide where 2 put d grub bootloader on ur own. ubuntu desktop doesn't have an option for dis.  selecting d "repair broken system" option will let u decide where 2 put d grub bootloader and evn let u change d location after d install.  if d grub fails completely, try  using gag (sry coudln't post link bcuz there site is down, but do a google).
or install d grub only on d linux partition or hd, and not on d windows hd.  (installing only on d linux partition will make it impossible to boot into  d linux partition without using gag (for example: i didn't want to tuch d windows bootloader-ntldr, at first (grub writes ovr it on the mbr by default) so I just installed d grub bootloader on my linux partition, and used a gag livecd 2 boot into linux everytime). oterwize when u reinstall d windows you'll over-right d grub bootloader with d windows bootloader-ntlder.  windows does dis automatically.

edit: here r some useful linkz:

[http://http://gag.sourceforge.net/index.html]("http://http://gag.sourceforge.net/index.html")
[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

in fact, deez r teh 1s i used when i first installed ubuntu - highly recommendeded

edit2:
d grub bootloader is most likely on d drive wer ubuntu was installed, in d drives master boot record.

---

### Post by narayanb on 2006-09-14
"selecting d "repair broken system"..."
where is dis option??? in the livecd menu?
cud u pls explain on that?
thanx

---

### Post by MikeMLP on 2006-09-14
no, it is not on d livecd, only d alternate install:

[http://www.ubuntu.com/download//]("http://www.ubuntu.com/download//")

choose ur country, and select d proper disc with "alternate" in d name

d alternate install disc is not a livecd, it is just an install cd

dis is an excerpt from d main usa link:

> Alternate install CD

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM. 

There are three images available, each for a different type of computer:

PC (Intel x86) alternate install CD
    For almost all PCs. This includes most machines with Intel/AMD/etc type processors and almost all computers that run Microsoft Windows. Choose this if you are at all unsure.
Mac (PowerPC) alternate install CD
    For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks.
64-bit PC (AMD64) alternate install CD
    For computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon). It is not necessary for all (even most) processors made by AMD -- only their 64 bit chips.

A full list of available files, including BitTorrent files, can be found below.

Kubuntu 6.06.1 and Edubuntu 6.06.1 are also available here.

If you need help burning these images to disk, see this guide.

d alternate disc should have what ur looking for.

---

