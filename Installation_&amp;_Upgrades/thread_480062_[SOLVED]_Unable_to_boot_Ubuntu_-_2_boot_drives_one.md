---
title: "[SOLVED] Unable to boot Ubuntu - 2 boot drives one with XP"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by rplourde on 2007-06-21
I am new to Linux (Ubuntu) and am trying to setup my environment for dual boot (XP and Ubuntu). I don't want to replace the MBR and I am unable to setup grub to dual boot.
From XP my env. look like this:
C: 152 gigs NTFS system
E: 27 gigs NTFS active
F: 157 gigs FAT32
1.5 gig swap unknown
74 gigs active

My boot sequence (from bios) is:
1. USB FDD
2. CD/DVD
3. IDE maxtor (which is c: in fact)


From Ubuntu (after booting V7.04 from CD) GPARTED is reporting:
/dev/HDA /dev/HDA1 NTFS 152 gigs boot
/dev/SDA
/dev/SDA1 FAT32 157 gigs lba
/dev/SDA2 LINUX-SWAP 1 gig ---
/dev/SDA3 EXT3 74 gig boot

/dev/SDB
/dev/SDB1 NTFS 27 gigs boot
/dev/SDB2 FAT32 1 gig hidden,lba


I did install UBUNTU on SDA3. When I do
sudo grub
find /boot/grub/stage1
I get (HD1,2)


With this setup, I boot Windows without any problem. However I haven't been able to get to Ubuntu.

Can somebody help? I saw many references to dual boot and GRUB but nothing specific to my situation.

Thanks.

---

### Post by logos34 on 2007-06-21
I've reread your post a few times and I'm still not clear about several things:

Are you booting successfully to windows on your main drive C:\ by choosing windows from the grub menu screen, or is just windows splash screen coming up? If the former then grub installed to its normal default location (the first ide disk detected) and overwrote the windows bootloader; if the latter then most likely either grub failed to install at all, or it's on the MBR of the linux drive (or maybe even sdb).    

Is sda, your linux drive, a sata drive or external usb?  

If you're booting windows via grub, and the ide disk is as you say the first hard drive in the bios boot order, then grub is on the mbr of that disk, or (hd0), and the linux drive should be (hd1) IF it is (still) the second hard drive in the bios boot order.  In that case, assuming you haven't changed the order of sda and sdb, root on sda3 should be accessible at '(hd1,2)'.

- If you're not getting grub menu at all, try putting the linux drive first in the bios boot order.  If this manages to bring up the grub menu, but you can't boot the linux kernels, highlight the first ubuntu entry and hit 'e' to edit.  Change the 'root' line to '(hd0,2)' or '(hd2,2)'.  Hit enter after each change and b to boot.

- If you are getting the grub menu when you boot to the ide drive, do the same as above and edit the root line.

You can also try reinstalling grub to the mbr of one of the disks using this [howto]("https://help.ubuntu.com/community/RecoverGrub?highlight=%28grub%29").  If you don't want to replace the windows bootloader on the ide disk you could make sure it goes on the linux drive or a floppy.

---

### Post by rplourde on 2007-06-22
I removed one of my USB drive. So now I have two disks:
1.  internal IDE XP NTFS only (Windows bootloader).
2. external USB drive 
           partition1 - FAT32
           partition 2 - swap
          partition 3 - Ubuntu

I did reinstall 7.04 from CD on external USB drive. At the point during the installation where I got the message about the boot I  did specify (hd1,2). 
After installation was completed, I rebooted my machine (BIOS was changed to boot external USB before internal IDE), didn't get any GRUB messages except the message "Missing operating system".

---

### Post by logos34 on 2007-06-22
Ok, that cleared things up.  
So windows bootloader is still on your main ide drive;
and linux is on a **external usb**

By specifying '(hd1,2)' Grub *should* have gone to the *root partition* of linux drive--if it was listed second in the BIOS hard disk boot order at the time.   

Try reinstalling grub but this time to the MBR/master boot record of the linux drive.

(using the live cd): 
Boot to the ubuntu live cd, load the desktop, open a terminal and type:  

> **sudo grub**  (puts you in the grub shell)

>**find /boot/grub/stage1**
(enter the output '(hd1,2)' or whatever in next command)
[B]root (hd1,2)
setup (hd1)
quit[/B]

(if using the alternate install cd):
> **'Rescue a broken system>reinstall GRUB bootlader**

Now you need to edit your grub config files menu.lst and device.map, because as soon as you change the BIOS hard disk boot order to boot the  USB drive first, it will change from '(hd1)' to '(hd0)'.  If you're on the live cd you'll have to mount your root partition first to get to your files:

> [B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda3 /mnt/ubuntu
sudo nano /mnt/ubuntu/boot/grub/device.ma[/B]p

(if the alternate install cd):
> [B]Enter rescue mode>Device to use as root filesystem (/dev/sda3)>Execute shell on root filesystem /dev/sda3
nano /boot/grub/device.map[/B]

Change it thus:
> [B](hd0) /dev/sda
(hd1) /dev/hda[/B]

Now for menu.lst:
> **sudo nano /mnt/ubuntu/boot/grub/menu.lst**
or (alternate install cd)
**nano /boot/grub/menu.lst**

Change all instances of root '(hd1,2)' to '**(hd0,2)**'.  Do this for the 'groot' line + kernels (main, recovery and the memtest86) in the automagic section.

If you want to have the option of booting windows from the grub menu on your linux drive, you'll need alter the windows entry at the bottom (should be there) thus:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[B]title		Windows XP
root		(hd1,0)
savedefault
makeactive
map           (hd0) (hd1) 
map           (hd1) (hd0)
chainloader	+1[/B]

This is to trick windows into thinking that it's on the first hard disk in the bios boot order--it doesn't want to boot any other way.

Hopefully that'll get you into your ubuntu install on the external usb drive.

---

### Post by rplourde on 2007-06-26
I did try the procedure but it doesn't work.
At the command  

sudo mount -t ext3 /dev/sda3/mnt/ubuntu
 
the command doesn't seems to be right. I got the msssage
 sudo mount -t ext3 /dev/sda3/mnt/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .





____________________________________



Anything else I should be doing


Thanks

---

### Post by confused57 on 2007-06-26
> **rplourde said:**
> I did try the procedure but it doesn't work.
At the command  

sudo mount -t ext3 /dev/sda3/mnt/ubuntu
 
the command doesn't seems to be right. I got the msssage
 sudo mount -t ext3 /dev/sda3/mnt/ubuntu
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .





____________________________________



Anything else I should be doing


Thanks

If you get a grub boot menu when you boot first to the external hard drive, highlight your Ubuntu entry, press "e" to edit, highlight the line with root, press "e" again, change the root from (hd1,2) to (hd0,2), press "enter", then press "b" to boot...this is temporary, but if it works, you can make it permanent.

Added:  logos34, didn't mean to intrude, but you weren't logged into the forum when I replied so thought I'd put in my 2 cents worth of advice.

---

