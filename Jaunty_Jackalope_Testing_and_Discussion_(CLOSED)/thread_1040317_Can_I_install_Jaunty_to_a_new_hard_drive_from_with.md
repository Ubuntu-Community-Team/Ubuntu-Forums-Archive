---
title: "Can I install Jaunty to a new hard drive from within a running Jaunty?"
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-01-15
Posting this as it's an odd one to search for and I haven't yet found an answer. :)

Basically, I want to install onto a new (another) hard drive so I can test out ext4 without touching my running install. If possible I don't want to download a new CD image that supports ext4.

I've already tried installing ubiquity onto the running install and it works up to the asking "am I sure" and I've set where I want the bootloader to go. It fails when it tries to unmount my running system even though I've said not to touch it.

Basically, is what I'm trying to do possible? Or do I just bite the bullet and download the image (again)?

(In case you're wondering I'm limited to 20GB p/m download 8am-11pm, so I don't like to download much until after that. I'm looking for a new ISP.)

---

### Post by Gina on 2009-01-15
A new ISP sounds a good idea :)  

I'm not entirely sure but I think you need to restart to install.  Surely if you've already downloaded the ISO you have it on your hard drive ??  You can then burn it to CD/DVD, put it on a USB memory stick, or even copy it to a bootable partition and install from there.  You can install the new system on another hard drive (or partition) in dual-boot with your existing system.  Nothing to stop you having two (or more) Ubuntu systems.  I often have several versions in a multi-boot setup.  You just choose which you want at startup.

---

### Post by jfernyhough on 2009-01-15
I've not yet downloaded a Jaunty ISO - so far each time I've done an Intrepid-> update-manager -d ->Jaunty

So while I have an Intrepid CD I don't have a Jaunty one - yet!

Basically I was wondering if it's possible to set up an installation environment from within a running system - but if not I can wait until tomorrow to test it out (I get unlimited downloads, though only 2Mb/s, at work ;) )

---

### Post by jerrylamos on 2009-01-15
Jaunty doing fine with jaunty Daily Live Ubuntu, Xubuntu, or Kubuntu running CD Live or installing from 1 gb partitions like they were CD's. 

Make a 1 gb partition. Or 50 mb larger than the .iso.  If gparted isn't installed on your jaunty, then Synaptic or sudo apt-get install gparted. Achtung! Use test system and backup anything you want, futzing around with gparted can trash a hard drive instantly!

sudo gparted
select 1 gb partition
# Achtung! Note what partition it is, in this case sda10
format ext3
apply
quit

I use rsync to get the latest Daily Build, for example make an executable file:

#filename rsyn or whatever you use
rsync -avzpPv --stats rsync://cdimage.ubuntu.com/cdimage/daily-live/current/jaunty-desktop-i386.iso .
rsync -Lvv --progress rsync://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS .
md5sum jaunty-desktop-i386.iso >> MD5SUMS
less MD5SUMS
#

then sudo chmod 777 rsyn

Create CD image on the 1 gb partition, I use an executable file in the same directory as the rsyn and the .iso:

# filename LivePartition10 hda(0,9) note these must match gparted
mkdir /tmp/install_cd
sudo mount jaunty-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
#Achtung! Dangerous - which sda?
sudo mount /dev/sda10 /mnt/installer
sudo cp -rv /tmp/install_cd/* /mnt/installer
sudo cp -rv /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd
#

of course sudo chmod 777 LivePartition10 or whatever filename you used.

Now update menu.lst to enable booting the CD image:
sudo gedit /boot/grub/menu.lst. I copy the following file into menu.lst just after the "...Automagic..." line.

#name Livesda10 or whatever you choose, (hd0,9) to match sda10
title jaunty Live
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw quiet splash
initrd /casper/initrd.gz

title jaunty Live recovery
root (hd0,9)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw single
initrd /casper/initrd.gz
#

If you don't have a large memory, for example if you have 512 mb, then use ramdisk_size 384000. It could be smaller I think if you want to play around. I don't know much about root=/dev/ram.

Enjoy....I've found it pretty quick to do rsyn most days to get the latest daily build, then LivePartition10 to copy it to the CD image on the 1 gb partition. The exec complains it can't create the directories since they exist already, then goes right on to finish the copy. 

Reboot and find out that my launchpad bugs still aren't fixed: 310982 312332 313452 ...

Do note if you find you are running the CD Live more than once, you can have a persistent mode by using gparted to create a 512 mb partition formatted ext3 and labelled casper-rw.  Then add the word persistent to the kernel line in menu.lst.  Remember if you re-do the .iso better re-format and re-label casper-rw.

Jerry

---

