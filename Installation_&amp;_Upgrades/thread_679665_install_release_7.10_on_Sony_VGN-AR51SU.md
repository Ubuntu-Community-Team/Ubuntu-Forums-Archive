---
title: "install release 7.10 on Sony VGN-AR51SU"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by pinan on 2008-01-27
I have been trying to install release 7.10 on a Sony VGN-AR51SU

I would like to be able to keep the visa partition. I followed the instructions given in [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) on how to install ubunto 7.4 and vista by shrinking the visa partition. I then booted ubuntu.
The ubuntu disk tool had a look at my machines disk and did'nt find any spare disk space.

It just offer me a choice of either format sda worth no existing partitions or reformating a files system of type ext3 on sdb1.

In the end I wrote to sdb1, loaded ubuntu, when I rebooted, I had to disable the raid settings on the 2nd disk to get the machine to boot.  This procedure as expected had crapped all over vista.

Has anybody had any success in installing any versions of ubuntu of this machine?


The machine has two 250 disks set up as a raid0 volume.

---

### Post by Pumalite on 2008-01-27
Read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by pinan on 2008-01-27
A useful document, when I read it I thought great :)

 I did try it.

The dmraid command generate the logical volume names.

But the machine always bailed out with an error when I attempt to create a file system.:(

A dig around with the results off dmesg , indicate some errors to with the machine attempting to disk blocks outside of the size of disk.

Has anybody got any other suggestions?

---

### Post by pinan on 2008-01-27
problems encountered are the same as described in the thread 

[http://ubuntuforums.org/showthread.php?t=559784&highlight=VGN-AR51SU&page=2](http://ubuntuforums.org/showthread.php?t=559784&highlight=VGN-AR51SU&page=2)

The suggested solution was to turn off raid,  having trashed vista twice so  far will try this solution, but I suspect that reinstall vista is going to reset the status of the riad discs. to be riad drives instead of the non raid setting I set them to.

---

### Post by emivik on 2008-01-28
First of all, try the alternate install CD. I think it should work properly but I haven't tried it yet.
Ok here's how I did it (only the basics, I did it 2 months ago and I don't remember everything, if you need more in-depth explanations feel free to ask! :) ):
- start Vista, resize Vista partition to have enough free space for Ubuntu (I reserved some 40 GB, there's plenty of them); you can do this in administration tools or whatever.
- restart with Ubuntu CD
- within the live Ubuntu, install dmraid, then start to create partitions with gParted; this is one of the tricky parts. Every time you create a partition, you have to shut down gParted (it crashes by itself eventually anyway, don' know why) and, from terminal, run **sudo dmraid -ay**, in order to refresh RAID partition table. Create a root (mount point '/') ext3 partition and a swap partition
- now I think you have to format partitions (again, close and restart gParted, after running the same command as above)
- install Ubuntu WITHOUT bootloader
- restart, Vista will show up as always
- install EasyBCD, an utility to manage Vista bootloader
- create a new entry, call it Ubuntu or whatever you like, selecting Linux as O.S.; this will install NeoGrub among other things
- be sure to set a timeout long enough (5 seconds for example) and to save every change you make
- restart AGAIN WITH THE UBUNTU CD
- reinstall dmraid, etc..
- from terminal, run **sudo dmraid -ay**
- now there should be some crappy devices in /dev/mapper/, named something like ****Volume03, etc..if you have done things right, the last two should be the ext3 and swap partitions (depends on which you created before)
- **take note of the device corresponding to the ext3 partition**
- mount the ext3 partition under any directory you like (e.g. /media/ubuntu_root/); this will give you access to the filesystem of the distro you installed before
- from the live filesystem, copy /boot/initrd<something> (don't remember the file exactly) to /media/ubuntu_root/boot/; this will give you the initialization ramdisk access to raid partitions
- remove the live CD and restart
- in the boot menu, select the Ubuntu entry; this will give you access to a grub prompt
- remember the device name you noted before? it should be something like *****Volume03 or Volume04 or something; if it was Volume04, type **root (hd0,3)**, or (hd0,2) if it was Volume03, and so on..
- type **kernel /vmlinuz root=/dev/mapper/<name of the device you noted before> splash ro**
- type **initrd /initrd.img**
- type **boot**
- if everything went Ok, you should now enter THE REAL Ubuntu installation
- install dmraid (DON'T FORGET THIS)
- reboot in Vista
- edit the file C:\NST\menu.lst as follows:

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

default 0
timeout 0

title Ubuntu
root (hd0,<number of partition as described above>)
kernel /vmlinuz ro quiet splash root=/dev/mapper/<volume name>
initrd /initrd.img
boot

- and there you (should) go! reboot and see if both vista and ubuntu start normally

let me know if there's any problem. I managed to get a neat tri-boot (Vista, XP and Ubuntu) with only one bootloader, it took me time but now I have three perfectly working OSs on this one awesome machine.

---

### Post by pinan on 2008-01-28
I was wrong after turning of the raid support in the bois, doing a factory reinstall of vista does'nt turn the raid support back on.

Thanks for the advice everybody

I will try the  the alternate install CD and after discovering that it somebody else has managed to get  the raid working means that I am prepared to give it another go.:)

---

### Post by pinan on 2008-01-30
Hi emivik



Tryied you suggestions, did'nt get very far.  The smallest size that windoz vista wants to use as a partation 228.32 gb.

My disk is currently set up as 9.45 GB , 228.32 on C: and 228.0 for Linix grand total  465.77 gb

According to the blurh this machine has 500 gb of disk space, so where did the other 35 gb go?
According to the control I settings to access the raid settings this machine has two Fukitsu disks of 232.9gb disk space, total 465.8gb with a stripe size of 128kb.

Attempting to access the disks from gpartd, reports errors about accessing cycinders that lie outside the disk space.
eg libparted 1.7.1
Can't have a partation outside the disk

Booting unbuntoo reports lots of errors eg Buffer I/O error on device sda2, logical block 59851774 etc

Nut sure whats actually going on, but I suspect that Linix is using the advertised size of the disk at 500gb where as windows has the size of 465.8.

From the information returned by gparted, the size of the NFS filesystems setup by windows are correctly reported.]
Q.  Is there something wrong the with bios settings for my machine, is 128kb the correct stripe size?
I tried the alternative image dvd/cd  it wanted to use lvm to format the entire disk.
Q.  What is the correct size for the machines disk?  is the advertised size, or the size after a file system has been constructed ? 

Any suggestions anybody ?

---

### Post by emivik on 2008-01-31
did you install dmraid?
did you run dmraid -ay?
by the way, the advertised 500 GB are in fact 500 billions of bytes, which in common computer nomenclature are 465 GB (see [http://en.wikipedia.org/wiki/Gigabyte]("http://en.wikipedia.org/wiki/Gigabyte"), section "consumer confusion").

---

### Post by pinan on 2008-01-31
Yes I tried dmraid as suggested and ran in to problems as described in the thread 

[http://ubuntuforums.org/showthread.p...-AR51SU&page=2](http://ubuntuforums.org/showthread.p...-AR51SU&page=2)

Several devices did appear, creating a partation with gpart always said it worked, but it generated diagonstics about attempts to write out side of the partation size.  The reread of data structure was alread reported as an error.

I also tried chfdisk.

And loads of dmraid -ay when ever I had fired a disk editing program.
I only created or made one change before quiting from gpartd and chfdisk, before rerunning dmraid -ay.


Dave.

---

### Post by emivik on 2008-01-31
the devices should be (in this order): 
- system restore partition
- vista partition
- free space you created for linux
is that so?
a screenshot of gparted would be helpful :)

E

---

### Post by pinan on 2008-02-09
Done it after much mucking arround.
disk partition table is (from fdisk)

Command (m for help): p

Disk /dev/mapper/isw_bedaghfgcg_pinan: 500.1 GB, 500113342464 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe14b9459

                           Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bedaghfgcg_pinan1               1        1235     9912320   27  Unknown
/dev/mapper/isw_bedaghfgcg_pinan2   *        1235       32083   247790592    7  HPFS/NTFS
/dev/mapper/isw_bedaghfgcg_pinan3           32606       60801   226484370    5  Extended
/dev/mapper/isw_bedaghfgcg_pinan5           33128       60801   222291405   83  Linux
/dev/mapper/isw_bedaghfgcg_pinan6           32606       33127     4192902   82  Linux swap / Solaris

Partition table entries are not in disk order

Grub set up is
title   Ubuntu 7.10
root    (hd0,4)
kernel  /boot/vmlinuz-2.6.22-14-386 root=/dev/mapper/isw_bedaghfgcg_pinan5  ro quiet splash
initrd  /boot/initrd.img-2.6.22-14-386

title   Ubuntu 7.10 (recovery)
root    (hd0,4)
kernel  /boot/vmlinuz-2.6.22-14-386 root=/dev/mapper/isw_bedaghfgcg_pinan5 ro single
initrd  /boot/initrd.img-2.6.22-14-386

### END DEBIAN AUTOMAGIC KERNELS LIST


title   Windoz Vista
root   (hd0,1)
chainloader  +1
boot


Managed to set the sound dvd and video working

To thinking
Motion Eye

Wireless 
Up for ten 30 seconds  then dies, claims its out of range, but this problem never seems to bother visa, so its not a hardware problem.  Wireless is a 4965,' Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)'

Thanks to those to helped:):):):):):):)

---

### Post by TerminatedTomatoe on 2008-03-18
Hi, I've got the same notebook. I never got a stable WLAN connection with 7.10 but with Hardy (alpha 6) it works quite good and stable. Connecting does take minutes though but this may be because of WAP, hidden SID and my particular router...
I'd really like to know what features you've got working on your machine. Brightness control, power saving modes, special keys, cam, .... ???
There doesn't seem to be much info about Linux on AR on the web, stuff working for other VAIOS didn't work for me.
THX!

---

### Post by pinan on 2008-03-19
I just got the basic machine working.

I did'nt bother with the brightness and other keys.

I did  manage to get it to driver tow montiors

---

