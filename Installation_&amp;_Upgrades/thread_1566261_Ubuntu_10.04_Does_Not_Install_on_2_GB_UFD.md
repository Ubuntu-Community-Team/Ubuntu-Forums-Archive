---
title: "Ubuntu 10.04 Does Not Install on 2 GB UFD"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by mavigozler on 2010-09-02
I have a LiveUSB form of Ubuntu 10.04 on one 2 GB UFD and wanted to make it persistent on another 2 GB UFD, so I used the Startup Creator utility (all within a VMware player, by the way) and it told me that of the partition(s?) required, it need to be 2.4 GB and if I wanted to install it anyway.  So I attempted to install it anyway and it aborted.

It used to be that a persistent form of Ubuntu could be installed on a 2 GB UFD.

So my questions:


[LIST=1]
[*]Should I use older version of Ubuntu?
[*]Should I use another environment of Ubuntu:  Kubuntu?  Xubuntu?  another?  I am comfortable with GUI or CLI
[*]There used to be recommendations for partitioning for any Linux system:  one partition for code (root, /), one for a swap, and one for data (the /home partition).  Do those still apply...does the installation package handle all that, or should I?
[/LIST]
I have noticed that some of the Community Forum help documents on installation may need updating.  In particular, I think many users will be getting 8 and 16 GB UFD storage devices and will use GRUB or other multi-boot systems with complex partitioning systems that give the ability to boot Linux, MS-DOS (for system rescue and hardware utilities), and full-fledged Windows OSes, and it would be nice if there were clear step-by-step flowcharts for anyone wanting to set up single and multiple OSes.

---

### Post by Mark Phelps on 2010-09-02
I'm not sure 2GB is large enough.  I would guess that you would need 4GB to be safe.

---

### Post by mavigozler on 2010-09-03
> **Mark Phelps said:**
> I'm not sure 2GB is large enough.  I would guess that you would need 4GB to be safe.

Hi Mark,

Did not older versions of Ubuntu (maybe Kubuntu, etc) run on less than 1 GB?  Or were these just the non-persistent ("live") versions?

---

### Post by Mark Phelps on 2010-09-03
> **mavigozler said:**
> Hi Mark,

Did not older versions of Ubuntu (maybe Kubuntu, etc) run on less than 1 GB?

Maybe so, but you're talking about 10.04, not older versions.

See the Minimum Requirements (of 5GB) in the link below:

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements")

---

### Post by oldfred on 2010-09-04
If you want a full install you really need 8GB and I used 16GB with 8 for root and 8 for home with no swap.

You can use grub2 to boot and install as many ISO as will fit and boot any of them. I have a 4GB flash with multiple ISOs and it is the one I use for all installs at all I have to do is copy the ISO to the flash ( and maybe edit grub.cfg).

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

Two scripts that automate the process. I still like doing it myself but scripts show how to boot some ISOs that will not loopmount.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644) 
Another - multibooting multiboot055.sh:
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

---

### Post by efflandt on 2010-09-04
It really depends upon what you mean by persistent.  A live iso with persistent data (casper-rw file loop mounted as ext2 file system) can be installed with Startup Disk Creator on 2 GB USB stick or other memory on USB card reader.  A CD iso takes up about 700 MB leaving about 1 GB for persistent data (or any remaining FAT32 space).

But for a full install a USB stick or other memory is USB reader should be at least 4 GB.  That only leaves 1 GB or less free space, so 8 GB or more is recommended.

---

