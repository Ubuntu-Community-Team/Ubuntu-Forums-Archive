---
title: "ALERT! /dev/sda1 does not exist. - Installing on external HD"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by Nrbelex on 2005-11-16
Hi,

I'm attempting to install Ubuntu on a 4Gb drive in an Adaptec ACS-100. I followed the instructions at [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) (see below) and then at [http://www.ubuntuforums.org/showthread.php?t=57741&highlight=%2Fdev%2Fsda1+dropping+shell](http://www.ubuntuforums.org/showthread.php?t=57741&highlight=%2Fdev%2Fsda1+dropping+shell) (also below) but I'm still getting an error saying ALERT! /dev/sda1 does not exist.

The external HD is running through a USB expansion port if it matters.

> Here is what I now do to successfully load UBUNTU v5.10 on this EXTERNAL USB DRIVE ...

(1) Instead of using "expert" mode to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).

(2) During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning ... which sets up an ext2 or ext3 partition and a swap partition for you.)

NOTE: Look for the line during the partitioning phase that might say ...
erase entire disk SCSI (0,0,0) (sda)

BE VERY CAREFUL on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!

Once again ... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!

(3) When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.

The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the SDA (external USB) drive where we want to install the GRUB bootloader.
(Mine was /dev/sda)

NOTE: at this point, the install program loads some stuff and ejects the CD ... wanting you to do a reboot.

(4) BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode)

Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.

(5) When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your drive from the list.
(Mine was mount /dev/discs/disc1/part1)

(6) When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.

(7) Type in these lines before we start editing out files ...

mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>

NOTE: I used vim to edit the files. It is weird to use at first until you learn what a few keys do in it ... The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ... And hitting : x (colon x) saves the file and exits out of vim.

( 8 ) Run vim to edit the modules file to make sure USB support is added/loaded during UBUNTU startup ...

vim /etc/mkinitramfs/modules <enter>

Right below the last line of text, enter these lines ...

ehci-hcd
usb-storage
scsi_mod
sd_mod

Be sure to save the file changes (using : x)

(9) Run vim to edit the initramfs.conf file to make sure enough time elapses for USB support to load before UBUNTU gets running ...

vim /etc/mkinitramfs/initramfs.conf

At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up ...

WAIT=12 (in all caps here, not sure if necessary though)

Be sure to save the file changes (using : x)

NOTE: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.

(10) Recompile (recreate) the initrd.img file to include USB support from these edited files ...

mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386

(11) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst

Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector.

NOTE: You may want to change the root line for the Windows XP section to (hd1,0) just in case you want to boot XP from this menu.

Be sure to save the file changes (using : x)

(12) Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.

BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS

(13) After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU


then

> I fixed this myself by adding mptbase and mptscsih to /etc/mkinitramfs/modules and then running 'sudo mkinitramfs -o /boot/initrd.img-2.6.12-6-386.new /lib/modules/2.6.12-6-386'

Any thoughts would be appreciated.
~ Brett

---

### Post by andrewsawyer on 2005-11-16
I know this is probably a stupid question to ask, but are you sure that your USB disk is mounted on /dev/sda1?  Try typing sudo fdisk /dev/sda and make sure it can open the device.  Then type 'p' to check you have a partition 1.  If all is ok, just type 'q' to quit.

If fdisk can't open it either, then try sudo fdisk /dev/sdb.  If this loads up and you can see it is your device, then just use /dev/sdb1 when going through the howto.

Andy

---

### Post by Nrbelex on 2005-11-16
From Fdisk:

Disk /dev/sda: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 499 4008186 83 Linux
/dev/sda2 500 525 208845 5 Extended
/dev/sda5 500 525 208813+ 82 Linux swap / Solaris

Then stuff about my internal HD

Thanks!

---

### Post by Nrbelex on 2005-11-17
Anybody with ideas?

Thanks!

~ Brett

---

### Post by geekburgerx on 2005-12-04
i'm having this same exact problem.. ive tried reinstalling and going through that guide a few times but i haven't been able to solve my problem or find any more information on it anywhere else.

---

### Post by psYchotic on 2005-12-22
Hey guys,
I was having the exact same problem and reinstalled a couple of times until I found out what was going wrong. You'll see that when you try to boot Ubuntu, during the init it says that the kernel is trying to assign a name to the device, but it won't work.
So what I have to do (each time I reboot...) is turn the computer completely off, then turn my external disk off, then turn the disk back on and wait for it to be up and running, and finally turning your pc back on. If all went well you should be able to boot into Ubuntu again.

And if any of you comes up with an idea to fix this problem, please post about it, coz it's "slightly" annoying to have to turn the pc off each time I wanna reboot.

EDIT : Also, DaBruGo says in his thread that in your /boot/menu.lst, the name of your drive should always be hd(0,0), but in my case, I had to change that to hd(2,0).

---

### Post by jpinzonc on 2006-01-13
HI How do I add mptbase and mptscsih to solve the ALERT

---

### Post by werdnav on 2006-08-28
i have the exact same problem, but its not solved by adding mptbase and mptscsih. HELP:(

---

### Post by werdnav on 2006-08-29
3 weeks and still no solution. 

I have attempted to install Ubuntu 5.01 to an external HDD by following [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) I keep getting the error ALERT: /dev/sda5 does not exist. … blah blah blah. 

By way of background, my external HDD is partitioned as follows: 
/dev/sda1  boot
/dev/sda5  root
/dev/sda6  data
/dev/sda7  backup

I attempted to correct the error by following [http://www.ubuntuforums.org/showpost.php?p=1100888&postcount=406](http://www.ubuntuforums.org/showpost.php?p=1100888&postcount=406) but that didn’t help. I then attempted to correct the error by following the suggestions of Marty [http://www.ubuntuforums.org/showthread.php?p=686867](http://www.ubuntuforums.org/showthread.php?p=686867) and included the script:
----------------------------------------
#!/bin/sh

PREREQ=""

sleep 10

prereqs()
{
        echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
        prereqs
        exit 0
        ;;
esac

modprobe -q fan
modprobe -q thermal
-----------------------------------
But that didn’t work either! I’m completely stumped. Can anyone help? 

-Andrew

PS: USB HDD has jumper set to master.

---

### Post by aroland on 2006-10-18
hello all,
I am getting the "ALERT! /dev/sda1 does not exist" error. I have read ALL the posts and it still happens. My ubuntu desktop mounts the drive and see's the install and gparted see's the partitions.

I have an HP 5170 laptop (internal drive removed) and a Lacie Porche 80GB usb.

Here are the last lines I see:
Begin: Loading Modules ....
Done.
Begin: Initializing /dev ....
Done
Begin: Running /scripts/init-premount ...
Done.
Begin: mounting root filesystem ...
Begin: Running /scripts/local-top ...
Done.
ALERT! /dev/sda1 does not exist.

then it drops to shell (BusyBox)
/bin/sh: can't access tty; job control turned off

then it lists:
SCSI device sda blah blah 80GB
sda: assuming drive cache: write through
/dev/scsi/host0/bus0/target0/lun0: p1 p2 <p5>
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

and thats it.

Thanks for reading my post and any help would be great.

Adam

---

### Post by pudland on 2006-10-21
Lacie 80GB USB HD w/ pavilion ze5170 laptop

I junked brezzy install and tried dapper alternate install..... i selected oem install and it installed with-out a hitch.

---

