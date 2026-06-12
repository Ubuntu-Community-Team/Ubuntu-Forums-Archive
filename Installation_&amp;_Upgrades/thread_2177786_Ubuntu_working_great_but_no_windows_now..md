---
title: "Ubuntu working great but no windows now."
date: 2013-09-30
forum: Installation &amp; Upgrades
---

### Post by poppys-boat on 2013-09-30
hi i installed Ubuntu and it is working great but my computer was set up with a duel boot with win7 and win8.1 on setting up Ubuntu i put down for it to install alongside windows but for some reason i cannot get windows to boot up either win 7 or 8, i have even tried to reinstall windows but it just says it cannot install as disk is locked which i have no idea about.

is it posible to unlock the drive and then run the old windows or if needed unlock then install a new install of windows 8.

i have one 120 GB SSD drive all one partition which is my C drive and the one i think is locked,

one 500 GB hard drive which i removed everything from to do the Ubuntu install on but somehow it is now showing three partitions 
one partition of 6 GB ext 2
one partition of 465 GB ext 4
one partition of 31 GB Linux swap (0x82)

one 1TB hard drive all one partition type HPFS/NTFS (0x07)

plus one DVD/CD drive and an external 1 TB hard drive

if possible i would like to try and keep my old win 8 along with the ubuntu install as if i loose my win 8 i loose some registration of some programs and will have to try and re register them with the seller.

any help gratefully received

regards 
Poppy Ann.


forgot to add [http://paste.ubuntu.com/6175939/](http://paste.ubuntu.com/6175939/)

---

### Post by theDaveTheRave on 2013-09-30
Poppy Ann,

It's not the first time I've seen this on the forums in the last week or so... [the other thread]("http://ubuntuforums.org/showthread.php?t=2176824") seemed to have a similar problem, and again involved SSD hdd.

so I would put the same suggestion to you.

have a read of the thread and see if any of it makes sense.

David

---

### Post by poppys-boat on 2013-10-01
hi Dave,

i took a look at the other thread but it is not like my problem i can see the ssd as a drive and under Ubuntu i can access it but i cannot get it to log onto it for booting up even when i change the boot drive in bios if i set it to boot from either the SSD which should boot win 7 or the 1 TB drive which should boot win 8.1 
i have even tried to reinstall win 8 but it will not install it just says the drive is locked and cannot complete the installation, i may have to format the drive and start all over again which i was hoping to avoid.
thanks for trying anyway
regards Poppy Ann.

---

### Post by oldfred on 2013-10-01
The auto repair under boot repair installs one grub to the MBR of every drive as many users do not know they have to reset BIOS to boot correctly drive.
Better to turn off auto fix MBR and just check update MBR. Under advanced option choose the operating system in each drive and update its MBR with that system. Or install the Windows boot loader to sda & sdc and install Ubuntu/grub for sdb1 or sdb2 to sdb and sdh5 to MBR of sdh.
Boot Ubuntu (or each Ubuntu) from BIOS or one time boot key and run this;
```
sudo update-grub
```

---

