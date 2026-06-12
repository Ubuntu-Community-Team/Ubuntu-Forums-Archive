---
title: "Creating a bootable RAMDISK"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2008-09-11
Is it possible to create a Bootable ramdisk and set it up in grub to boot either Ubuntu or the Ram disk.

I just want a quick booting Linux install that i can use to Create Backups of my Linux and Windows partitions.

Somewhat like a LiveCD but running only from RAM not a CD. 
It just needs to:
- Fit well within 512Mb of ram
- Be a simple CLI install 
- Run Partimage and a Partition editor.
I don't need to save the RAM disk Have a static image which is loaded into ram when it is booted.

---

### Post by Vivaldi Gloria on 2008-09-11
> **solitaire said:**
> Is it possible to create a Bootable ramdisk and set it up in grub to boot either Ubuntu or the Ram disk.

Ram deletes its contents when it's powered of. So not possible. I suggest you make a little partition on your disk and install one of these:

[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

or use a disto on a usb memory.

---

### Post by solitaire on 2008-09-11
> **Vivaldi Gloria said:**
> Ram deletes its contents when it's powered of. So not possible. I suggest you make a little partition on your disk and install one of these:

[http://www.linuxlinks.com/Distributions/Floppy/](http://www.linuxlinks.com/Distributions/Floppy/)

or use a disto on a usb memory.

Laptop can't boot form USB, Floppy drive is spotty at best.

I Know Ram contents are lost when powered off that's why i'm looking for a solution that will load a pre-made Image into ram then run from there.

---

### Post by Vivaldi Gloria on 2008-09-11
> **solitaire said:**
> i'm looking for a solution that will load a pre-made Image into ram then run from there.

There are distros like [[COLOR="Sienna"]slitaz[/COLOR]]("http://www.slitaz.org/en/") who can keep themselves in ram. Some of the floppy distros I linked above can also do that. But I cannot see how you can get away without making a seperate partition on your disk if cd/usb/floppy is not an option. Grub can handle the following:

> The currently supported filesystem types are BSD FFS, DOS FAT16 and FAT32, Minix fs, Linux ext2fs, ReiserFS, JFS, XFS, and VSTa fs.

See [[COLOR="Sienna"]manual[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html"). So you need a partition with one of these filesystems. Maybe there is an another bootloader which can do the things you want, but I haven't used any bootloader other than grub. Sorry.

---

### Post by Herman on 2008-09-12
> I just want a quick booting Linux install that i can use to Create Backups of my Linux and Windows partitions.

Somewhat like a LiveCD but running only from RAM not a CD. 
It just needs to:
- Fit well within 512Mb of ram
- Be a simple CLI install 
- Run Partimage and a Partition editor.
I don't need to save the RAM disk Have a static image which is loaded into ram when it is booted. I don't know about the 'quick booting' part, but GParted LiveCD can boot and run in RAM, (so you can boot it, then spit the CD out and it will continue running entirely in RAM, something the same as Puppy Linux). GParted LiveCD is available in USB versions, and you should be able to install the USB version to a small partition in your hard disk and boot it with GRUB. You should be able to get it to boot into RAM if you use the same boot options as the Live CD uses to boot into RAM.
GParted Live CD contains Partimage and TestDisk and of course, it is a partition editor. [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") 

 -! or you could use Puppy Linux! That contains GParted as well. Just install Puppy Linux to a small partition. [Puppy Linux Home Page]("http://www.puppylinux.org/").

---

### Post by solitaire on 2008-09-12
I've not tried Ejecting my Ubuntu Live CD once installed (It keeps accessing it when i run the Live CD)

I'm actually looking for something like a modified "Inital Ramdisk" Linux uses to boot.

I'll take a look at puppy linux see if i can make that into a "*.img" and use Grub to load it in to a RAMDisk.

---

### Post by Herman on 2008-09-12
> I've not tried Ejecting my Ubuntu Live CD once installed (It keeps accessing it when i run the Live CD):) If you have over 1 GB of RAM you might be able to do that with a Ubuntu Live CD, but you would need to make special modifications to the .iso file before burning it to the CD first, specifically to the boot options.
I don't think the standard Ubuntu CD is designed to work that way, or at least it wasn't the last time I checked. There are more and more computers these days with enough RAM to do it though. :)

Puppy Linux, GParted Live CD and a few others come with that ability as standard.
> I'm actually looking for something like a modified "Inital Ramdisk" Linux uses to boot. You mean an initrd.img file?
You should be able to find an initrd.img file in /boot, one for each kernel. I have eight of them in my system at the moment.
You can copy a kernel and a matching initrd.img file to another disc or partition and use them to boot with if you enter the right commands in GRUB.
Is that what you mean or am I still not understanding you correctly?

---

### Post by solitaire on 2008-09-12
Laptop has only 512Mb or ram.

You're getting it. Herman :)
I just need to get initrd.img and add in Gparted and partimage. Then creating an additional boot option to the menu that loads that image into memory without continuing to load the main linux install.

i.e. getting Grub to 1.5 then stopping letting me use the Ramdisk.

I don't want to go through the hassle of repartitioning my hard drive if i don't need to. I might spend sunday dismanteling the Floppy drive and giving it a good clean out see if that fixes it.

---

### Post by snowpine on 2008-09-15
+1 to SliTaz. Boot it from CD, then spit out the CD and it runs entirely in RAM.

---

### Post by gamhead on 2010-11-02
Ever get this going?

I want to create a recovery partition that I can use to repartition my drive without inserting a disk or usb stick so the machine can be reconfigured standalone

---

### Post by skralljt on 2011-02-24
Another vote here for the slitaz cd.  It won't necessarily install a working slitaz installation to a partition but slitaz will boot up to a very workable linux distro all in memory with gparted and a lot of wireless drivers etc.  Though I can't recommend trying to use it as a day to day operating system because of several glaring issues such as a tendency for x not to start I do find it indispensable for helping out friends when they need files recovered off of their borked laptop or I need to resize a partition or something.
Of course, none of this helps if you don't have a burned copy of it.  There is information [http://forum.slitaz.org/index.php?p=/discussion/2408/option-to-load-slitaz-to-ram-during-hd-installs/p1]("http://forum.slitaz.org/index.php?p=/discussion/2408/option-to-load-slitaz-to-ram-during-hd-installs/p1") there for how to install slitaz to a partition of your choice and then get it to load into ram.  Quite a bit of work imho but your time may have different value than mine.

---

### Post by dino99 on 2011-02-24
ramdisk is totally useless, let swap on

---

