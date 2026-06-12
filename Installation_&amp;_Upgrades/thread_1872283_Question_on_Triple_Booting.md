---
title: "Question on Triple Booting"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-10-30
Hey fellow nerds,

I'm currently dual booting Windows 7 (64 bit) and Ubuntu 11.04 Natty Narwhal (64 bit).  I'm trying to install Ubuntu 10.10 on another (third) partition also.

I figured that I'd have to do this manually from a Live USB.  The guide I'm using is [http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html").  I found this from the thread [http://ubuntuforums.org/showthread.php?t=1654585](http://ubuntuforums.org/showthread.php?t=1654585).  I resized my 11.04 ext4 file system  (using GParted) to make some free space.  Then I made a 4054 MB swap allocation.  I went to use the rest of the free space as an "EXT4 journaling file system," but the guide tells me to mount it as "/".  (If I don't select a mount point, the program complains that no root system is specified)  On my 11.04 partition (/dev/sda6, ext4 system), the program does not list it as having  a mount point.  Is the mount point actually "/", but the program just doesn't show it for some reason?

I'm just a little confused about all this.  I want the 10.10 partition just like my 11.04 partition, but be able to choose either of them (as well as Windows 7) in GRUB.

Should I just go ahead and mount the new file system as "/"?  One other thing: for the boot loader, I should choose the whole disk, right?  Not just the new partition?  If I do this, will it screw up the kernel list for Ubuntu 11.04?  I'll attach some screen shots...
[ATTACH]205880[/ATTACH]
[ATTACH]205881[/ATTACH]
[ATTACH]205882[/ATTACH]

Thanks a ton, guys.  I love the support for Ubuntu.

---

### Post by GreenRaccoon on 2011-10-30
I guess I've got another question.  I've already got two swap areas on my hard disk for some reason (one each from installing Windows 7 and Ubuntu 11.04, I'm guessing).  Do I need a separate swap area for each of my 3 partitions?  Or could I just use one that would work for Windows 7, 11.04, and 10.10?

---

### Post by Starfleet on 2011-10-30
You need to highlight the partition you have created. Click change and tick the format box. Creat it with Ext4 jounaling file system. Mount it as '/' (root). It should set up Grub bootloader to see all you sytems. If not it will need loading from a live cd. 

You should only need one swap partition for any Ubuntu installations to use. Windows will need it's own NTFS file system swap. Any new Ubuntu installation will find the relevant swap with an ext4 file system on it or it may even make another one if you don't tell it not to do so. This won't matter in the slightest.

---

### Post by oldfred on 2011-10-30
Your second install of Ubuntu will write its grub2 boot loader to the MBR and you will be booting from it. Its os-prober should find both Windows and your other install.

But you may have issues on grub2 updates as both systems are set to rewrite the grub2 boot loader to the MBR.

I have several / (roots) in my sdc drive as I have installed many versions of Ubuntu and not overwritten the older ones.

You may want to also make a shared NTFS partition for data. That data then can be used by Windows (d: ) and both installs of Ubuntu. I have my Firefox & Thunderbird profiles in a shared NTFS partition so I have the same bootmarks & email in whatever system I boot.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

One user posted this a long time ago.
> I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/debconf/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep 'stage1' install in sync.


---

### Post by GreenRaccoon on 2011-10-30
> **oldfred said:**
> Your second install of Ubuntu will write its grub2 boot loader to the MBR and you will be booting from it. Its os-prober should find both Windows and your other install.

But you may have issues on grub2 updates as both systems are set to rewrite the grub2 boot loader to the MBR.

I have several / (roots) in my sdc drive as I have installed many versions of Ubuntu and not overwritten the older ones.

You may want to also make a shared NTFS partition for data. That data then can be used by Windows (d: ) and both installs of Ubuntu. I have my Firefox & Thunderbird profiles in a shared NTFS partition so I have the same bootmarks & email in whatever system I boot.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

One user posted this a long time ago.

Well, "sudo dpkg-reconfigure grub-pc" got stuck on the "configuring grub-pc" page and wouldn't go any further, so I decided to just install 10.10.  The MBR was overwritten, of course, and I couldn't figure out how to bring it back.  After searching for a long time, I found out that I just had to do "sudo grub-setup /dev/sda" under my original 11.04 OS.

GRUB's fine now, and I've got all three OS's working on my laptop.  Thanks a bunch, guys!

---

### Post by GreenRaccoon on 2012-01-01
> **GreenRaccoon said:**
> Well, "sudo dpkg-reconfigure grub-pc" got stuck on the "configuring grub-pc" page and wouldn't go any further, so I decided to just install 10.10.  The MBR was overwritten, of course, and I couldn't figure out how to bring it back.  After searching for a long time, I found out that I just had to do "sudo grub-setup /dev/sda" under my original 11.04 OS.

GRUB's fine now, and I've got all three OS's working on my laptop.  Thanks a bunch, guys!

I just replaced my third partition with Xubuntu 11.10.  After running "sudo grub-setup /dev/sda" on my other partition (Ubuntu 11.04), I got a scary grub-rescue prompt. #-o Luckily, I've run into some GRUB problems before, so I referred back to a thread I created a while back: [http://ubuntuforums.org/showthread.php?t=1873849]("http://ubuntuforums.org/showthread.php?t=1873849")

If anyone is reading this for help, you should go to that thread (for better instructions) and do the first set of codes. In them, "/dev/sda" and "/dev/sda5" could be different for you, but this is what I ran:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Done! No GRUB screen of death anymore. :mrgreen:

---

