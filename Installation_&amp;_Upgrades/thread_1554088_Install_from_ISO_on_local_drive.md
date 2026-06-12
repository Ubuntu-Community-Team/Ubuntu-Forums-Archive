---
title: "Install from ISO on local drive"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by jmore9 on 2010-08-16
Hello !  I am trying to install ubuntu from an ISO on a FAAT32 Partition.   Is there a way of booting into the FAT32 partition with the ISO on it, and mount it to install from, from the Debian installer ?

I have been searching for over a month now and still have not found anything that gives some information on how to do that.  I remember that i was able to make a rescue disk for Fedora 5 and use the installer from it and select the partition and then the iso i wanted to use.

Thanks in advance for any help.:P

---

### Post by jmore9 on 2010-08-16
I have found this web page , but a question .

[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

After running the network installer and using the locally mounted cd will it install a full desktop or just a partial desktop ?

It just doesn't seem like there is a way to only install off a fat32 partition mounted iso.  oh well

---

### Post by jmore9 on 2010-08-16
I also found this , this is similar to what i want to do , except that it requires a system to be installed already 

I want to be able to do the following without the linux system being installed already :




Install from hard drive

Use this method for a faster system installation and if you don't have a CD/DVD-ROM drive! For this method, you will need to have a working Ubuntu system on the computer on which you want to install the new Gutsy OS.

First of all, you need to use GParted or PartedMagic to create a new primary partition and format it to ext3. For example, let's say that the partition is /dev/sda3 (for a SATA drive) or /dev/hda3 (for a IDE drive). You will need to copy the ISO's contents over to the new partition. Open a Terminal (Applications -> Accessories -> Terminal) and type:

mkdir /tmp/installcd
sudo mount -o loop /path-to/ubuntu-7.10-desktop-i386.iso /tmp/installcd (for an i386 PC)

or

sudo mount -o loop /path/to/ubuntu-7.10-desktop-amd64.iso /tmp/installcd (for an AMD 64/Intel 64 PC)
sudo mkdir /mnt/installer
sudo mount /dev/sda3 /mnt/installer (for the SATA drive)

or

sudo mount /dev/hda3 /mnt/installer (for the IDE drive)
sudo cp -r /tmp/installcd/* /mnt/installer
cd ~/
sudo umount /tmp/installcd


Next, you'll need to edit your current Grub configuration file to boot the new partition. To do this, open the /boot/grub/menu.lst in a text editor with:

sudo gedit /boot/grub/menu.lst

...and add the following lines at the end of the file:

title Ubuntu Hard Drive Installation
root (hd0,2)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz

    NOTE: the root line tells Grub which partition contains the installer. If in your case, the partition you created is /dev/hda1, you'll need to edit that line to root (hd0,0). Grub starts counting your partition from 0, therefore the fourth partition will be (hd0,3) and so on. If you have a secondary hard disk, you will have to modify the first number from 0 to 1 (e.g. hd1,0 - for the second hard disk, first partition).

Save the file, close the text editor, reboot the computer and choose 'Ubuntu Hard Drive Installation' from the grub boot menu and install Ubuntu 7.10 Gutsy Gibbon.

---

### Post by mörgæs on 2010-08-16
Are you aware that 7.10 is unsupported?

---

### Post by oldfred on 2010-08-16
the loop mount only works on new versions of Ubuntu. I think it was 9.04 or newer, but not sure. It works for sure with 9.10 and 10.04 as I have done it.

[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

---

### Post by jmore9 on 2010-08-17
Yes i am aware that the info was for 7.10.  That was the only info on what i want to do that i could find.

I am still looking for a way to put a ubuntu iso on a fat32 partition mount it and then install from that mounted iso.

I guess i will have to dig through all my old cds ( 5 or 6 years worth )and see if i can find the fedora 5 one i did that with.  Maybe i can revers engineer it to work with debian installer.

---

