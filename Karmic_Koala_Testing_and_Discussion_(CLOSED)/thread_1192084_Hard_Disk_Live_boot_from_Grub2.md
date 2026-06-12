---
title: "Hard Disk Live boot from Grub2"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-06-19
This is "live" running from a 1 GB partition on Karmic and booted by Grub2.

Wow.  I'm surprised Grub2 would do this.  At Alpha2 level, anyway.

Before I write a CD I like to boot the .iso from a 1 GB partition to see if it will work on this pc.

If you don't mind living dangerously and have already backed up anything you want to keep.... 

Bring up gparted and create a 1 GB partition.  This one's labelled Live7 it's on /dev/sda7.  I couldn't find gparted on karmic so I used a CD.  apt-get install said gparted was already there but no way I could find to start it.

I make this executable file:

# Live7
mkdir /tmp/install_cd
sudo mount karmic-desktop-i386.iso -o loop /tmp/install_cd
sudo mkdir /mnt/installer
sudo mount /dev/sda7 /mnt/installer
sudo cp -rv /tmp/install_cd/* /mnt/installer
sudo cp -rv /tmp/install_cd/.disk /mnt/installer
sudo umount /tmp/install_cd

In the old days if this ran you could actually do an install.  No more, install won't format a partition if another is mounted.  Gparted can do that just fine.  I think it's a "safety" check to protect us from ourselves only.

I then change grub.cfg file permissions:

sudo chmod 644 /boot/grub/grub.cfg

sudo gedit /boot/grub/grub.cfg and insert something like this:

menuentry "Ubuntu karmic CD Live (on /dev/sda7)" {
	set root=(hd0,7)
	linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=524388 rw quiet splash
	initrd /casper/initrd.gz
}

Do note I've got 1 gb ram so ramdisk will fit in that.  I use ramdisk 384000 on a pc with 512 mb ram.

Do note Grub has /dev/sda7 as (hdo,6) while Grub2 on the karmicA2 I'm booted on uses /dev/sda7 as (hdo,7).

Do note no UUID's.  Also if you do an update-grub you'll have to add changes back in.  Maybe adding it to /etc/default/grub would copy it in I don't know.

You can try persistent by creating an ext3 partition labelled casper-rw and add the word persistent above after quiet splash.  I assume it will work since it did on jaunty.  For simplicity I use 1 gb partition.

Another caution, if the CD Live works, and you do make a CD, and try to boot it to install, you get something funny.  It boots off the CD, finds the "live" partition, then promptly starts running from that instead of the CD.  Faster, but won't install because installer won't format a target partition with another mounted.

So when I want to do an install, I re-format Live7 partition to ext3.

Sounds a bit complex but it is a fun way to test out .iso without writing CD or USB.  This PC won't boot from USB anyway.  My experience on another PC that will boot USB, this running pseudo CD Live from a partition is faster to do and runs faster.

Have fun...

Jerry

---

