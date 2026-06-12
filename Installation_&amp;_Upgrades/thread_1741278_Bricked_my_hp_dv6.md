---
title: "Bricked my hp dv6"
date: 2011-04-27
forum: Installation &amp; Upgrades
---

### Post by homeschool on 2011-04-27
First I tried to create a new partition within windows but Ubuntu never liked it. Finally I just went to intall it on the whole hard drive and it froze during the who are you screen trying to get a time from the network time server. I read something that said restart and now I cant boot my laptop
 
HELP

---

### Post by RJARRRPCGP on 2011-04-27
> **homeschool said:**
> First I tried to create a new partition within windows but Ubuntu never liked it. Finally I just went to intall it on the whole hard drive and it froze 

Probably bad HDD, sorry bro.

---

### Post by homeschool on 2011-04-27
It was ok.  No way to get it to boot to a disk?   now it just humms and goes to a blinking "_"

---

### Post by homeschool on 2011-04-27
No way to get into the system to change the boot options?

---

### Post by RJARRRPCGP on 2011-04-27
Your MBR is screwed!

(master boot record) 

(The master boot record is a data piece that links to the boot loader, so the BIOS can load an OS.)

---

### Post by lkraemer on 2011-04-28
When you power up, Keep the DELETE Key Depressed, or whatever key is 
needed to access the BIOS.  See if you can set the CDR/DVD or USB for first
Priority in the Boot process.  That should allow you to boot from
a LiveCD or USB Device.  If you can't get into the BIOS then you have a Hardware
Issue.  You should already know what gets you into the BIOS of your Compaq/HP.
If not use GOOGLE to search for those Keystrokes.......

When you Partition, you need to Boot from a LiveCD of Gparted (or other
software so your Hard Drive isn't mounted.......)  You also can do it from
the Ubuntu LiveCD, or make a bootable USB version with Unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You should have Downloaded the Ubuntu ISO (or Distro of your choice), booted
from the LiveCD, and made 100% sure that everything seemed to work before
you tried the install.

You are going to have to Download a LiveCD of Supergrub, or another software
program that will let you restore the MBR.

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)
[http://www.supergrubdisk.org/?page_id=54](http://www.supergrubdisk.org/?page_id=54)

Read how to create the LiveCD, then how to replace the MBR.  If you are lucky,
you should be able to boot into windows, depending what has been
done to your Hard Drive's Partitions.

Worst Case, you just need to remove all the Partitions, and then create
the ones you need for Ubuntu, and Install Ubuntu from the LiveCD.
I always start out booting a LiveCD of Gparted, set up the Partitions,
then Boot the Ubuntu or Debian LiveCD and install from there.

REMEMBER, the Physical Hard Drive can ONLY have a MAXIMUM of FOUR PRIMARY Partitions.
Typically I use the following for Dual Boot:
1. Windows XP
2. \   - for Ubuntu       
3. \home - for Ubuntu
4. Swap - for Ubuntu

You may use a Extended Partition (LOGICAL) and create many more Partitions
in the Logical Partition.  It's your Choice.

So, Start Downloading the LiveCD's and doing one thing at a time.
I's suggest booting the Gparted LiveCD first and having a look at the 
existing Partitions to get an idea of what remains on your Hard Drive.
Then, Boot SuperGrub LiveCD, and try replacing the MBR, if the previous
step shows that the Windows Partition still exists.  And if you have DATA 
on the Windows Partition, you may want to get that saved or backed up before
it gets blown away.  Or you can remove all partitions, then Boot the Ubuntu LiveCD
and install letting Ubuntu guide you through the Install, after testing Ubuntu
from the LiveCD.

That should give a good idea of the process.....

lk

---

### Post by coffeecat on 2011-04-28
> **homeschool said:**
> First I tried to create a new partition within windows but Ubuntu never liked it. Finally I just went to intall it on the whole hard drive and it froze during the who are you screen trying to get a time from the network time server. I read something that said restart and now I cant boot my laptop
 
HELP

If you chose the install to whole hard drive option, then the install would have deleted **all** the pre-existing partitions and created just two partitions, a large ext4 partition for your Ubuntu/Edubuntu / (root) partition and a small swap partition. When the installer  froze, the system was only half-installed and, in particular, the grub bootloader would not have been setup.

If you really did choose the whole hard drive option, then your only practical choice is to re-install. It would take too long to repair what is a broken system. But before you do, check the md5sum of the downloaded ISO and if you were installing from a live CD, tap any key when you first boot it (when the two small icons against a purple background appear) and choose the disc integrity check from the text menu. This is to ensure that the install medium is OK. Also - try installing without the network connected. Less to go wrong.

If you are not sure whether you opted to install to the whole hard drive, let's see what is on your system. Boot up the live Ubuntu/Edubuntu CD or USB and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions there to download and run the boot info script and post the contents of the RESULTS.txt file in code tags for legibility.

---

