---
title: "mounting &quot;/&quot; to non bootable device?"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by moyd on 2011-03-05
== Background: ==

- Old laptop with only PATA
- Bought a PCMCIA ESATA card and a SATA SSD in an external enclosure
- Bios is too old to support booting from the PCMCIA device

I bought an SSD to speed things up a little, but having some issues.

Since I can not boot from the SSD, I thought I'd load the kernel from the old PATA disc and then mount / to the SSD.

== What i've tried: ==

(sda = internal pata)
(sdb = external ssd)

1. Installed ubuntu to sda with seperate paritions for /boot /var /srv and /

moyd@A:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9              4804736   2012760   2547908  45% /
none                    508764       376    508388   1% /dev
none                    512980       228    512752   1% /dev/shm
none                    512980        88    512892   1% /var/run
none                    512980         0    512980   0% /var/lock
none                    512980         0    512980   0% /lib/init/rw
/dev/sda5               456796     15524    416901   4% /boot
/dev/sda6               960504    181904    729808  20% /var
/dev/sda7              1921036     35648   1787804   2% /srv


2. Also made an install to sdb with only one parition + swap space

3. Tried changing /etc/fstab for mounting / to sdb instead (Also tried using UUID)

moyd@A:~$ more /etc/fstab

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
/dev/sdb1 /    ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=b64f1aa1-f3ae-4825-9ddf-4e5c7603157b /boot           ext2    defaults        0       2
# /srv was on /dev/sda7 during installation
UUID=3eb31571-02f2-4697-b69a-e856958d8829 /srv            ext4    defaults        0       2
# /var was on /dev/sda6 during installation
UUID=8c8a2742-740a-4bc6-a16c-3c4aa4decd5d /var            ext4    defaults        0       2
# swap was on /dev/sda8 during installation
/dev/sda8 none            swap    sw              0       0

==RESULT==

The boot process still mounts / on sda instead of sdb as expected.

moyd@A:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda9              4804736   2012772   2547896  45% /
none                    508764       376    508388   1% /dev
none                    512980       228    512752   1% /dev/shm
none                    512980        88    512892   1% /var/run
none                    512980         0    512980   0% /var/lock
none                    512980         0    512980   0% /lib/init/rw
/dev/sda5               456796     15524    416901   4% /boot
/dev/sda6               960504    181904    729808  20% /var
/dev/sda7              1921036     35648   1787804   2% /srv



Spent the last few days using google, but for no good..

Any ideas?

---

### Post by vanadium on 2011-03-05
I am not quite familiar with all technical ins and outs, but the bootloader is grub. Grub (at least the very first part) must be on a bootable device. All the remainder can be on any drive in the system. Study grub, and there you will find the solution to configure booting an OS from the non bootable flash drive. Someone else may pass by who can give you more specific help on this.

---

### Post by moyd on 2011-03-05
Well, not quite. Since the pcmcia device is not recognized by the BIOS, grub has no way of knowing it exists as far as i know.

Therefore I have to load the kernel before I can mount the partitions on the external drive..

---

### Post by moyd on 2011-03-06
Update:

Getting closer.. Secret was in the initrd. Had to make a new initrd image with modules for pcmcia referenced, once that was up it could find sdb and mount the root file system there.

Still wont start X and insists on dropping me to a 'terranova' shell, but big step forward..

---

