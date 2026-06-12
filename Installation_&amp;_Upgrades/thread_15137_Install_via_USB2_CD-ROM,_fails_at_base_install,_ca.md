---
title: "Install via USB2 CD-ROM, fails at base install, cant find Release file"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by kerignell on 2005-02-12
I solved it, see third post for solution.

--------------------------------------------------------------------------------------------------------

I have  an Compaq N410c laptop w/o builtin CD. I'm in the process of installing Ubuntu Warthy release. I´m installing from sent out printed CD´s, I have tried with two different and also one I burnt myself.

It booted alright from the USB2 CD-ROM, my first problem occurs at 'Detect and mount CD-ROM', my cd is not found by the installer. I solved it by mounting it manually, 'mount  /dev/scsi/host0/bus0/target0/lun0/disc /cdrom/' At  this stage my alt+F4 screen gives :

syslog.warn klogd: VFS: Can´t find ext2 filesystem on dev sda.
syslog.err klogd: cramfs: wrong magic
syslog.debug klogd: ISO 9660 Extensions: Microsoft Joliet Level 3
syslog.debug klogd: ISO 9669 Extensions: RRIP_1991A

Maybe I need to mount it with some options that  I´m unaware of?



Anyway, the installation continues, "Load installer components from CD" seems to work. All steps up to "Install the base system" are done w/o error messages.

I am able partition the HD, but when I try to start "Install base system" it gives an error message :

Debootstrap Error
Failed getting Release file /cdrom/dists//Release.

alt+F4 gives : No such file or directory and failed with error code 1

I also tried to copy the contents of the cd first to an USB-stick and then to a separate FAT-partition at hda with the partition-tool, I mounted that partition at /cdrom/, it seems to work up until the same moment where the CD fails, same error message.

Can someone point me to a solution? My initial workaround idea is to load the base system from the network, cos at the failing stage my nic is working and I have an ip. Is that possible? I´d prefer to load it from the CD though.  

Thank you for this lovely dist, I´ve had it working on another laptop and I love it.

---

### Post by kerignell on 2005-02-12
Could it be that the symlinks(?) are not in order? This thread mentions a similar problem, [http://www.ubuntuforums.org/showthread.php?p=60913](http://www.ubuntuforums.org/showthread.php?p=60913) 

If so, any ideas on how to mount it properly?

---

### Post by kerignell on 2005-02-12
haha, there is a f netinstall something :D all problems solved.

For others with the same problem:

1 Boot with expert
2 Mount CD as described above
3 When asked to choose additional installer components, mark 'Add mirror' or something like that

After this the installer alternated between internet and cdrom as source for files needed and everything went smoothly.

If you experience similar problem and cant solve them you may contact me via IRC, usually kringell or kerignell @EFNet.  Im always in #piratbyran.org if those nicks dont apply.

Happy ubunting! copyme

---

