---
title: "Grub does not list Ubuntu As Boot After Installation"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by dkjain on 2014-07-28
Hi,

I installed ubuntu via USB on nettop (no CD/DVD drive) which already had the following:

1. C: (ntfs) - Win XP
2. D: (ntfs) - Win 7
3. E: (ntfs) - DATA
4. F: (ntfs) - DATA

Deleted E: drive with Ubunutu Installer and then created / (20gb) swap (4gb) and /opt/myspace/ (6.9gb). Installation Finished and rebooted however GRUB lists  the following without a Ubuntu 12.04 entry:

1. memtest86+
2. memtest86+ [some tech jargon]
3. Windows 7

Ubuntu 12.04 is installed and there on the disk however GRUB does not list it.

I am not sure why this occured. Kindly help resolve this. 

Thanks
dkj.

---

### Post by yancek on 2014-07-28
If you have used the arrow keys on the keyboard to scroll up and down on the menu and the Ubuntu entry is not there, that would be very unusual.
You could go to the site below and download and run the bootinfoscript from the Ubuntu installation medium and post the output, a results.txt file which has some detailed information on your system.  This might give enough information to someone to suggest a possible solution.  There is a link in the Description box at the site explaining how to use it.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by Bashing-om on 2014-07-28
dkjain; yancek; Hello,

Are we dealing here with a bios (MBR) partitioning limitation of 4 primary partitions ?

@ dkjain; Show us what we are working with, maybe make that 4th partition as 'extended' and within that 'extended' partition make up the 'logical' partitions to hold the ubuntu operating system ?? (ubuntu will happily install onto logical partitions) 
Post back the outputs - between code tags - of terminal commands:
```

sudo blkid
sudo fdisk -lu
sudo parted -l

``` so we know what the partitioning is, prior to making any further recommendations.

[INDENT][INDENT][INDENT]just what I think
[/INDENT][/INDENT][/INDENT]

---

### Post by dkjain on 2014-07-29
Please find results.txt (of bootinfoscript) attached. 
thanks

---

### Post by oldfred on 2014-07-29
It looks like you do not have any kernels. Not sure how you could install and get grub installed but not have kernels. Did you houseclean old kernels and include current one by mistake?

I think Boot-Repair's total uninstall & reinstall of grub also reinstalls the most current kernel.
If not while in chroot that Boot-Repair walks you thru run this.
       apt-get dist-upgrade

Or do a full chroot yourself, be sure to use correct partition or sda8 in your case:
      
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Once in chroot run all of these. # are comments, do not copy or type them.

 #houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

You also have Windows 7 boot files in your sda1 XP install partition. I might copy Windows 7's boot files to sda. Many users have uninstalled XP and then could not boot 7 as they also deleted all boot files. If you moved boot flag to sda2 and run Windows repairs it would be directly bootable from grub also.

---

