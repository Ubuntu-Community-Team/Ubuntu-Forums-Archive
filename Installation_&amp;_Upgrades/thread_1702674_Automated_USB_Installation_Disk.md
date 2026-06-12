---
title: "Automated USB Installation Disk"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by Jaybeekay on 2011-03-08
I have been given a task to make a USB flash drive that you insert and it installs a specific iso (the iso: a customized installation of a debian distrubution cloned to a iso) to the hard drive.

in basic (or sort-of):
1. should partition hard drive to specific details
  (fdisk /dev/sda
   p1 - +200M,p2 -  +1G,p3 -  +10G,p4 -  wteva space Partition 4 respectively,
   with p1 bootable and p2 swap
2. then mkfs.ext3 for p1, p3, p4
3. make some dirs and then copy the iso contents (cpio) to the respective folders.

is there any way how i cn just make a small bootable flash drive with the iso on make some scripts as to tell it to just to those in order and automatically?

How can this be done please help! ](*,)

---

### Post by Dutch70 on 2011-03-08
> **Jaybeekay said:**
> I have been given a task to make a USB flash drive that you insert and it installs a specific iso (the iso: a customized installation of a debian distrubution cloned to a iso) to the hard drive.

in basic (or sort-of):
1. should partition hard drive to specific details
  (fdisk /dev/sda
   p1 - +200M,p2 -  +1G,p3 -  +10G,p4 -  wteva space Partition 4 respectively,
   with p1 bootable and p2 swap
2. then mkfs.ext3 for p1, p3, p4
3. make some dirs and then copy the iso contents (cpio) to the respective folders.

is there any way how i cn just make a small bootable flash drive with the iso on make some scripts as to tell it to just to those in order and automatically?

How can this be done please help! ](*,)

Welcome to UF!!! 

 If you're making a bootable usb stick, do you really need to partition it? 
Short of that, check out...

[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

---

### Post by dirty_harry on 2011-03-08
unattended linux installation:

[http://fai-project.org/](http://fai-project.org/)
[requires network, dhcp-server, nfs, but USB and full customization is support]

I never installed one of those. But in this setup your image is served via NFS, not via your USBdrive. 
To install only form USB I think this would rather mean customization of your debian image.

---

### Post by Jaybeekay on 2011-03-09
> **Dutch70 said:**
> Welcome to UF!!! 

 If you're making a bootable usb stick, do you really need to partition it? 
Short of that, check out...

[[COLOR=Blue]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")


The steps 1 - 3 i made its not for the usb its what i want the flash drive to do to the pc.

---

### Post by Jaybeekay on 2011-03-09
Anyone?

The iso im talking about its not actually a operating system iso. (say for instance a Ubuntu 10.04 Disc)
Its a iso with an installed operating system already.
I just want the flash drive to be plugged in configure the hard drive to my specs make some directories and extract the iso into the folders they're suppose to go in. all automated from booting from the flash drive?

---

### Post by dirty_harry on 2011-03-09
try scripting clonezilla:
[http://clonezilla.org/customized-clonezilla-live.php](http://clonezilla.org/customized-clonezilla-live.php)
[http://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/99_Misc/00_live-initramfs-manual.doc#00_live-initramfs-manual.doc](http://clonezilla.org/fine-print-live-doc.php?path=clonezilla-live/doc/99_Misc/00_live-initramfs-manual.doc#00_live-initramfs-manual.doc)

some examples:
[http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3850916](http://sourceforge.net/projects/clonezilla/forums/forum/663168/topic/3850916)
[http://raymii.org/cms/index.php?title=Custom-Clonezilla](http://raymii.org/cms/index.php?title=Custom-Clonezilla)

actually it would be easier to clone a whole drive, without the hassle of scripting the process.

are you doing this for an embedded system?

---

### Post by Jaybeekay on 2011-03-10
Systems ill be using the flash drive on will all have the same hardware.

I`ve decided to go into the direction of DSL. (Damn Small Linux)
got my flash drive booting into it, set it up using Unetbootin.

Now I Need some DSL experienced guys or i dnt knw if its the same as  because i see it runs off a Knoppix.

1. How do i set up DSL to boot into the terminal enviroment straight automatically?
(I saw some options in the grub list or whatever DSL is using).

2. How do i add/install CPIO capabalities to this distro?

---

