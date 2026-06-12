---
title: "Partitioning and Disk Manager"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by GhostCrew on 2006-07-06
Dear all,

I am sure this has been answered, but thought I could ask for some help on the disk sizing and partitioning for Ubuntu.

I initially install Ubuntu 5.04 and ran update manager, I now have the latest Ubuntu version.

As a new user :( but very exited:) , I came across the DISK MANAGER menu.  I noticed that my Linux HD 9.3gb is made up of 2 partitions 1 and 5.  1 is /boot (Extended 3) and is 243mb and 173mb is free. Partition 5 is unformatted and is unaccesible.

My question is when I install application where does it get installed?  How can I use Partition 5?  Basically, I have dedicated the secondary HD 9.3gb for Linux and would like to make sure that I don't run out of space.

Basically, how would you partition 9.3 second HD for Ubuntu only.???

I am coming from a windows background and loving Linux and especially Ubuntu.

Please advice and help
Regards
--
GhostCrew

---

### Post by Nunana on 2006-07-06
Strange it looks like you have no  /
can you pass me the output of: df -h
for some more information
Afcourse you can format (as ext3) and mount the 9 Gb as datapartion with a name like /u01 (or whatever you like). If there is no other data on it (Windows NTFS?)

---

### Post by GhostCrew on 2006-07-07
Hi,

Please find df -h result below.

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                      8.8G  3.1G  5.3G  37% /
varrun                506M   96K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  180K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-25-386/volatile
/dev/hdb1             228M   37M  180M  17% /boot



Thanks
GhostCrew

---

### Post by Nunana on 2006-07-07
ok
it looks like you have 8.8 Gb for /
its called /dev/mapper/Ubuntu
normally there is aa disk like the ona at the bottom /dev/hdb1
Maybe its a LVM i dont know. I hope somebody can tell us.
Normally i don't use LVM. My partitioning depends on what i want.
standard /boot /root and / on different partitions.
/boot 100Mb
/root data for user root
/home user data
/ for all your programs the more/bigger the programs, more space
if you use it as mail server
/var Big. All e-mail goes there.
Extra data partitions if you need
/u01 /u02 
There must be simple guidelines for this available. please dont ask me where.

---

### Post by cotcot on 2006-07-07
I confirm. Your installation used LVM (logical volume management). That is why your hda5 is not recognised. 
Your "/root" is "/dev/mapper/Ubuntu-root".
When you go in Gparted you will see it as a separate "disk" with this name besides hda.

See [http://www.tldp.org/HOWTO/LVM-HOWTO/]("http://www.tldp.org/HOWTO/LVM-HOWTO/") for more info. 
I use LVM with a seperate home partition and reiser as filesystem. The /boot partition (logical volume /dev/mapper/Ubuntu-home) has to be a primary partition because grub cannot boot from LVM partitions.

---

### Post by GhostCrew on 2006-07-07
Hi Everyone,

Many thanks, this is making sense now.  Is it right to assume that the LVM would expand (within 8.8gigs) as and when space is required for / - /root - /home etc.

Additionally, thanks for the link will have a read tonight.  Is the sizing based on the memory, Linux Distribution, HD etc (any best practice for Linux?)

Sorry for the dumb questions

Thanks again
GhostCrew

---

