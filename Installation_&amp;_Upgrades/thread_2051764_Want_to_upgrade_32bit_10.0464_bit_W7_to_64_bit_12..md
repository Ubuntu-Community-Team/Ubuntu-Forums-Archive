---
title: "Want to upgrade 32bit 10.04/64 bit W7 to 64 bit 12.04/64 bit W7"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by tahitiwibble on 2012-09-02
Good evening one and all,

I have this 32bit 10.04/64 bit W7 dual boot system which works beautifully. I have access from both operating systems to all my documents, music, videos, photos etc etc files from both sides. I run Thunderbird and Firefox from either OS seamlessly, along with Tomboy Notes which I keep in a Dropbox folder.

I just need some reassurance that this is not going to turn into the catastrophe I remember that it was the last time I didn't do a clean install. It's taken so long to get where I am today but I'm not sure that I would be capable of redoing everything all over again if the worst happens.

```
dad@dad-laptop:~$ sudo fdisk -l
[sudo] password for dad: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76692ca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15357116   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1913        7366    43807488    7  HPFS/NTFS
/dev/sda3            9922       38913   232870208+   f  W95 Ext'd (LBA)
/dev/sda4            7366        9922    20532224   83  Linux
/dev/sda5            9923       38913   232870207+   7  HPFS/NTFS

Partition table entries are not in disk order
```

sda1 is the laptops' restore partition
sda2 houses W7
sda3 & sda5 is my 'data' partition
sda4 is my beloved home folder

What's going to happen when I hit the "Upgrade" button? Should I just bite the bullet and do another clean install :sad: ? What should I watch out for here?

Any hand-holders out there? :-({|=

A thousand thanks for any encouragement/advice.

---

### Post by 2F4U on 2012-09-02
I think a lot depends on how customized/tweaked your Ubuntu installation is, i. e. how much it deviates from a "stock install". In my experience, the more customized the installation is the more chance are that an in-place upgrade fails. In the end, probably no one can tell you whether it will work or not and you have to try it. I strongly recommend to make a backup of your valuable data before to do attempt to upgrade.

---

### Post by opensshd on 2012-09-02
Looks like you're using the windows boot manager?

A couple things I'll advise:

Backup your data. Be prepared for critical failure! Make sure you get all those configuration files in your home directory as well.

Have another computer on hand to access the net during the upgrade in case you need support during the process.

Decide what boot loader you are going to use.

If you are willing to do a clean install you have nothing to lose by trying the upgrade first.

An operating system has become a disposable thing to me. The data is what is important, not so much the OS and related settings. There are some easy strategies for making the 'move in' process to a new operating system easy and painless.

[http://lglinux.blogspot.ca/2007/11/backup-ubuntu-debian-package-selection.html](http://lglinux.blogspot.ca/2007/11/backup-ubuntu-debian-package-selection.html)

When you have your data backed up - tear into that OS ;)

---

### Post by oldfred on 2012-09-04
You cannot upgrade from 32bit to 64bit, so you have to backup and reinstall anyway. 

I created a new 25GB partition, so if I forgot anything I could still boot my old partition. But either way it is important to have good backups.

Most of your settings are in /home. If you did some system changes they are in /etc, but new versions may not need the same settings or has totally new settings,  so do not just copy /etc back into a new install.

My backup procedure is a new clean install. So my backup is intended to restore my system. I export list of packages and hard ware configuration as part of my rsync backup.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

---

### Post by tahitiwibble on 2012-09-04
Well first of all thanks to the three of you for the moral support and encouragement!

Here's what I did;

Backed up all the content of the 3 partitions (/, W7 & Data).

Burned a live 12.04.1 CD to play around with a bit, and discovered that 12.04 looks very nice indeed.

Was going to let update manager take care of the update but it was going to take 7+ hours of downloading and another, I don't know how many, of installing.

Anyway, I eventually hit the install button on the live CD and was flabbergasted to see one of 4 options be  something like "you have a dual boot W7 and 10.04, do you want to keep things as they are and just upgrade 10.04 to 12.04?" ....... so I hit "OK".

Incredible! just absolutely amazing! after re-starting at the end of the update EVERYTHING worked. I was fully expecting to have to do a fresh install but all I had to re-install were a few of my favourite apps.

The only slight hiccough came when I tried to install a couple of utilities and I ran into the same trouble that [this guy had]("http://ubuntuforums.org/showthread.php?t=2052115") ---- my solution was to uncheck Update Manager>Settings>Other Software the "Cdrom with Ubuntu 12.04 'Precise Pangolin' and bingo!

**opensshd**, you're dead right when you say "An operating system has become a disposable thing" ....... throw out the old and bring in the new! **after you've backed up your important data** :)

---

### Post by oldfred on 2012-09-04
Glad that worked, Was this a change to 64bit or just a upgrade of the 32bit?

---

### Post by tahitiwibble on 2012-09-04
> **oldfred said:**
> Glad that worked, Was this a change to 64bit or just a upgrade of the 32bit?

I was hoping that the chance to upgrade to 64bit would have been offered, but you're correct in saying that it's not possible to upgrade from 32 to 64. Am I missing anything in sticking to 32bit?

I'm tempted to try a 25gig partition with the 64bit version. Is it worth fiddling with?

---

### Post by oldfred on 2012-09-04
If you have more than 3GB of RAM it probably is better to convert to 64Bit. If you have the 25GB available it is relatively easy to create a another boot. You will have to decide which grub2 has its boot loader in the MBR and will be first on the menu.

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

