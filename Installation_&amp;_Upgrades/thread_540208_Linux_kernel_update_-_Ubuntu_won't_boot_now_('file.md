---
title: "Linux kernel update - Ubuntu won't boot now ('file not found' error)"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2007-09-01
This morning (minutes ago) I had a mundane system update, so I clicked to start and saw that the Linux kernel was being updated.  A restart was required after the updates were installed, but after the restart, I can't load Ubuntu.
For each of the 4 Ubuntu boot options (kernel 2.6.20-16 and 2.6.20-15, both generic and generic recovery mode), the following error message appears:
> Error 15: File not found

Press any key to continue...
How do I fix this and point the grub loader to the right kernel?
If there's a thread already started about this issue, please point me there.
Thanks

---

### Post by Pumalite on 2007-09-01
Your update probably changed your fstab or your menu.lst or both. Do have a command line? Have you tried Ctrl+Alt+F1? If not, then boot Live CD, mount your filesystem(partition) and post:
sudo fdisk -l(small L)
cat /boot/grub/menu.lst
blkid
Post your fstab too.

---

### Post by xzero1 on 2007-09-01
Same problem here my partition was 'not found'. BTW, you can still boot Ubuntu with super grub disk.

---

### Post by Robotman on 2007-09-01
Ok, here's the info:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       19104   153452848+  83  Linux
/dev/hda2           19105       19457     2835472+   5  Extended
/dev/hda5           19105       19457     2835441   82  Linux swap / Solaris

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       60801   488384001   83  Linux

Disk /dev/hdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       24792   199141708+  83  Linux

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          14      112423+   0  Empty
/dev/sda2              15        7296    58492665    b  W95 FAT32

```

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d69b3389-019c-4b7b-9234-79a815999513 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

```
ubuntu@ubuntu:~$ blkid
/dev/sda2: LABEL="MIKE'S IPOD" UUID="783E-2836" TYPE="vfat" 
/dev/sdf1: UUID="46A4-ED7B" TYPE="vfat" 

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
/dev/hda1         /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
/dev/hda5         none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1      /media/hdb1     ext3       defaults      0 1
/dev/hdd1      /media/hdd1     ext3       defaults      0 1

```

btw, what's a Super Grub disk?

---

### Post by Pumalite on 2007-09-01
I don't see a bootflag anywhere. Menu.lst points to 2nd hard drive, 1st partition. I assume your Ubuntu is in hdd1. Am I correct or is menu.lst wrong?

---

### Post by Robotman on 2007-09-01
menu.lst must be wrong.... Ubuntu used to be on hdd1, but now it's on hda1.  I moved it when I got rid of Windows.

---

### Post by xzero1 on 2007-09-01
Just fixed it. In my case menu.lst was modified. My root and uuid was changed. Use /dev/disk/by-uuid to list your partition uuids. Get your partition number by using system monitor.


Super Grub is a boot loader iso that you download and burn on a cd that can boot various operating systems (it is like a menu driven grub).

---

### Post by heot on 2007-09-01
My PC is quit simple. No SATA etc.
No floppy drive and during upgrade of the kernel and GRUB it went wrong. 
My floppy drive was not disabled in the BIOS....
Ubuntu changed all lines in menu.lst from my installation disk (hd1,4) to (h0,0,)! And added the "right" UUID with it.
Happely I had another menu.lst in my Suse boot/grub with the UUID of (hd1,4) so after replacing this, all went right again.

Now I have turned off the floppy drive in the BIOS.
Will it happen again at next kernel upgrade?

---

### Post by Pumalite on 2007-09-01
Backup your menu.lst first:
cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Change Ubuntu 'root' from (hd2,0) to (hd0,0)(in all instances)
Save changes
Reboot and let's see.
( we haven't looked at the issue of the UUID's yet. I found your blkid kind of rare)

---

### Post by xzero1 on 2007-09-01
The update did revert to some other UUID probably because I had changed my Ubuntu partition since installation. Shouldn't the update consider the current menu.lst as the valid one?

---

### Post by Robotman on 2007-09-01
I edited menu.lst and rebooted.... I didn't get the file not found error, but the Ubuntu boot screen hung.  I pressed CTRL+ALT+F1 and got the following error message:
> Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc modules ls /dev
ALERT! /dev/disk/by-uuid/d69b3389-019c-4b7b-9234-79a815999513 does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

Now what? :confused:

---

### Post by Pumalite on 2007-09-01
You can boot your Live CD, mount your filesystem, change the menu,lst to what it was and start again trying to find the problem. Or you can backup all your data and do a fresh install.

---

### Post by Robotman on 2007-09-01
I think I'll opt for the backup/fresh install.  How can I back up the contents of hda1 using the live CD?
EDIT: Also, how can I set up my 2 storage hard drives to be automatically mounted with the right permissions when I boot the system?

---

### Post by Pumalite on 2007-09-01
We need logos34 here. I have to leave you ( there has been sometime since I used the Live CD. I don't even remember if it has a Burner. Beyond that, what you are asking me require hands more skilled than mine, Somebody will chime in,.You only have to save /home BTW)

---

### Post by Robotman on 2007-09-01
Ok, thanks for your help this far. :D
I have lots of space on another hard drive, so i don't need to burn anything to DVD/CD.  If I remember correctly, there's a way of doing it using a terminal.

---

### Post by Pumalite on 2007-09-01
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by Robotman on 2007-09-01
The total contents of my hda1 drive are only 6.8GB.... so I'm thinking about just copy/pasting the entire contents to a USB drive.  Will the live CD allow me to do that, or will some important files be missing?

EDIT: Ok, copy/paste the contents to a USB drive doesn't work... I don't have "permission" to do that.  What's a simple way to backup the entire contents of my hda1 drive to the USB drive?  Would it be easier to change permissions (don't know how) or is there a set of commands I can enter in a terminal?

---

### Post by quixote on 2007-09-01
Grub did not find the Ubuntu boot partition (Error 22), so I figured I had to reinstall grub, like I'd done once before.  Instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

However, that didn't solve the problem.  I pulled out my trusty bible (Hitchhiker's Guide, of course) and re-read the relevant page: Don't Panic.

After using another computer to access this thread, and looking at /boot/grub/menu.lst, I saw that it had listed Ubuntu as being on (hd0,10).  On my system it's actually /dev/hda9.  So, it should have had it as (hd0,8 ) [no space after 8, inserted to avoid smiley!] given grub's numbering convention.  These are the steps I followed:

I booted from a LiveCD.
opened a terminal window
entered sudo -i at the command prompt.
root@ubuntu# mkdir /mnt/good-ubuntu         [you can use any name for the dir] 
root@ubuntu# mount -t ext3 /dev/hda9 /mnt/good-ubuntu    [insert your own location for "hda9"]
root@ubuntu# cd /mnt/good-ubuntu/boot/grub
root@ubuntu# cp menu.lst menu-lst-bak.txt            [so you have a copy just in case]
root@ubuntu# gedit menu.lst

that brings up gedit, and then I changed all the references to (hd0,10) to (hd0,8 ) in my case.

Saved.  Closed everything.  Rebooted.  And it all worked.

Hopefully I have all the commands listed right.  A real Ubuntu expert: please vet!

My guess is that in the update files, the relevant variable was either initialized at 1 instead of 0, or  maybe there's a minus sign missing somewhere, to subtract 1 instead of add it to the existing partition numbers.

Hope this is useful!

---

### Post by Robotman on 2007-09-01
I tried reinstalling the GRUB loader too.... no effect.
I've given up on trying to fix any of the boot files, and my plan is now to backup the entire hda1 drive (only 6.8GB) to a USB drive and reinstall Ubuntu on hda1...... but I'm stuck because I don't know how to backup the data/change the permissions or whatever else is necessary.

---

### Post by -SpaZ on 2007-09-01
When I upgraded, my hard drive had to remount.  Of course that isn't as bad as what other people are experiencing.  I wonder what's wrong with the updates.

---

### Post by Kheldin on 2007-09-01
Sounds like I'm going to wait on installing this update in hopes that another one that doesn't mess things up is pushed out soon.

---

### Post by rahimveron on 2007-09-01
Mine update went fine

---

### Post by crbennett on 2007-09-01
Hm...I ran the update a few moments ago. I was a little concerned that I saw an error message phrased something like:  "Calling /sbin/-update grub" and followed by "Don't use /sbin/update-grub!  Use /usr/sbin/update-grub instead!"

So...I reboot the machine and the top kernel in the list yields:  "Error 18: Cylinder exceeds maximum supported by BIOS"  

Yuck.

So I reboot again, choose the 20-15 kernel and I'm back in.  I head over to grub's menu.lst and make sure the option in the grub configurations is to keep all the kernels in the list.

Having read this thread, I'll go review that something funky hasn't gone on with the disk references. It's possibly a different result of the same problem, just causing a different outcome on this laptop.

Good luck to all with this!

Ross

---

### Post by Cuchulainn on 2007-09-02
I had the same problem, after the kernel upgrade ubuntu wouldn't boot anymore. Here is what I did to fix it:
[LIST=1]
[*]In the boot menu, go to the line with the Save Mode in it.
[*]Press c to open a command line.
[*]type 'root (hd'. Now press tab to see what the options are, for example hd0 and hd1. Choose one, the line now says 'root (hd0', and press tab again. If the harddrive has more than one partition, it should name them. This way you can find out which drive has your root partition.
[*]Go back to the grub menu, and press e to edit.
[*]Check that the line 'root (hdx,0)' has the same drive you just found. Change if necessary.
[*]In the line with root=UUID=.... replace the UUID=... part with the root partition, in the case of (hd0,0) this would be /dev/hda1 or /dev/sda1
[*]Now keep your fingers crossed and boot...
[*]If all goes well, you're now in root mode, and can edit the /boot/grub/menu.lst. What I did was to pass the UUID's to the menu.lst with 'blkid >> /boot/grub/menu.lst', and edit the menu.lst, using the same disk as in step 5 as root.
[/LIST]

---

### Post by Raffo on 2007-09-02
Same error here, fixed by myself in a second. The bad thing is that a kernel upgrade should not modify menu.lst because there's no need to do it. The kernel image selected in menu.lst should be a link to the real image and after the upgrade the only thing that should be modified is the link to the newer image...

---

### Post by Robotman on 2007-09-02
Just as an update to this, I did have to reinstall Ubuntu on the affected computer.  However the kernel update went perfectly on my laptop.... nothing out of the ordinary happened and everything on that computer works like it should.  I think the problem I had stemmed from the fact that none of my drives had a boot flag... and that I [removed the UUIDs]("http://ubuntuforums.org/showthread.php?t=480293") from fstab a while ago.

---

### Post by Cuchulainn on 2007-09-26
It happened again with the latest kernel update.... luckily I now know how to fix it.....

---

### Post by billrad1 on 2007-09-26
I've been through this a few times now.

1. boot a live cd

2. open a command window

3. type sudo su 

4. type fdisk -l

5. record the location of your boot partition, like /dev/sda1 or hda1 or hde1 or whatever

6. type sudo -c nautilus

7. use nautilus to go into file system /media, and find the grub folder, under boot

8. backup menu.lst, and edit the line uuid 98908098 and replace it with /dev/sda1 or whatever

9. check that the hd 0,1 setting is correct. If not, edit. 

10. save it all and reboot


hope this helps somebody.

Bill

---

### Post by i22yb on 2007-10-09
I'm having the same problem with Gutsy 7.10 beta.  I have to edit my menu.lst every time Ubuntu updates the kernel.  This only started happening AFTER I moved around the SATA connections for my harddrives on my motherboard in order to set up a raid array.  I can't change them back without messing up my raid array, so I have to edit the menu.lst on each kernel update.

Super Grub Disk is a great tool, but isn't needed for this problem.  When you reboot your computer and the grub boot menu comes up:

1) Highlight the latest kernel (or one you want to boot with) and press "e" to edit the boot options.
2) Highlight the line that says root (hdx,x) and press "e" again.
3) Change the (hdx,x) to whatever it should be based on your setup and press "enter".
4) Press "b" to boot the system with these changes.

This is a temporary change, once your system boots you still need to edit your menu.lst to make the changes permanent (at least until the next kernel update).

UPDATE:  PROBLEM SOLVED!
----------------------------------------
I found some references on another forum to grub using the line:
# groot=(hdx,x)

What I read said that grub uses this command even though it is commented out.  I believe this is accurate because I just edited this line and set it to the drive/partition that grub is installed on.  Then I ran synaptic and updated to the latest kernel.  To my pleasant surprise, ALL of my grub boot choices (including Windows) worked properly without having to edit menu.lst again!

---

### Post by tanas on 2007-12-19
Thanks cuchulainn!!

In my case the problem was that the upgrade changed my menu.lst, from hd0,0 to hd0,1. 
First I really don't get why menu.lst is totally rewritten in every kernel upgrade (keep getting different problems with it).
Second, why does the ubuntu upgrade ASSUME that I have windows installed???? (Notice that my kernel is in hd0,0 not in hd0,1... so only ubuntu here)

---

### Post by Pumalite on 2007-12-19
To prevent changes have to permanently change the lines:
#groot, and
#kopt

---

### Post by Pumalite on 2007-12-19
[http://ubuntuforums.org/showthread.php?t=644661](http://ubuntuforums.org/showthread.php?t=644661)

---

### Post by karachuonyo on 2007-12-19
Did the kernel upgrade this morning as suggested by adept and works fine.

---

### Post by SomeLuser on 2007-12-24
Kernel update today...
I'm getting the GRUB file-not-found-error...

 I'm on one of those Dell desktops that come preinstalled with Ubuntu, so I know they messed with the partitions a bit and I'm afraid to do anything to them, since I'm sure someone here can walk me through it if I need it ;-) .

I'm successfully not panicking, so... what should I do?

---

### Post by Pumalite on 2007-12-24
Lightbulb  HOWTO stop Kernel update wrecking your custom grub menu.lst
Recently I had installed a Kernel update, after rebooting I found that not only would Ubuntu not boot but it had removed all the other OS'es I had in my menu.lst

So I did a bit of research on this subject and looked at the settings of the /boot/grub/menu.lst file and I discovered how to stop a kernel update from ruining my menu.lst

Step 1) change groot

There is an option for groot in your menu.lst this should be set to where your current Ubuntu / partition is. For example if groot is
Code:

# groot=(hd0,0)

Then /dev/hda1 or /dev/sda1 MUST be where / is mounted
To find out where / is mounted issue the following command at the prompt
Code:

$ mount | grep on./.type
/dev/hda3 on / type ext3 (rw,errors=remount-ro)

To understand how Linux drive mapppings convert to grub drive mappings
i.e. that /dev/sda1 is (hd0,0)
Use the following table and the following rules

    * Grub starts counting drives from 0 but skips every optical drive (so if you have a DVD at /dev/hdb then grub will make a drive at /dev/hdc 1 instead of 2)
    * Linux starts counting drives at a and goes through the alphabet
    * Grub starts counting partitions at 0
    * Linux starts counting partitions at 1

Note: originally in Linux drives marked /dev/hd? were IDE drives and those marked /dev/sd? were SCSI drives. However due to changes in the kernel it is possible to have IDE drives named /dev/sd?
Code:

Linux Partitions                    Grub Partitions
/dev/hda1        /dev/sda1          (hd0,0)
/dev/hdb1        /dev/sdb1          (hd1,0)
/dev/hdc1        /dev/sdc1          (hd2,0)
/dev/hdd1        /dev/sdd1          (hd3,0)

/dev/hda1        /dev/sda1          (hd0,0)
/dev/hda2        /dev/sda2          (hd0,1)
/dev/hda3        /dev/sda3          (hd0,2)
/dev/hda4        /dev/sda4          (hd0,3)
/dev/hda5        /dev/sda5          (hd0,4)
/dev/hda6        /dev/sda6          (hd0,5)

/dev/hdc5        /dev/sdc5          (hd2,4)

So my /dev/hda3 maps to (hd0,2)

Then I get that value and copy it into the groot line in menu.lst
Code:

# groot=(hd0,2)

Note: it is okay to have the comment character (#) at the beginning of the groot line

Step 2) Change kopt=root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro

There is another option for kopt this has the parameters that are passed to the kernel. The most important one here is the root parameter. This can be given to the Kernel as a UUID (Unique Identifier for a partition and disk) or as a straight linux drive mapping like /dev/sda3. It is preferable to use UUIDs since they can be used if drives are swapped around.
This is what kopt on my system looks like.
Code:

# kopt=root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro

to find out the UUID for my system I again look at my / partition
Code:

$ mount | grep on./.type
/dev/hda3 on / type ext3 (rw,errors=remount-ro)

That will give me something like /dev/hda3 yours will probably be different
I then look for the UUID of /dev/hda3 as follows. Please insert your drive mapping in here.
Code:

$ sudo vol_id -u /dev/hda3
e7cf76ab-c3bf-468a-8359-a77f65d99346

Then I get that value and copy it into the kopt line in menu.lst
# kopt=root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro
Where the value in Green is the bit I alter

Note: it is okay to have the comment character (#) at the beginning of the kopt line

Step 3) Move the lines for other operating systems out of the way

When the kernel gets updated everything between
Code:

## ## End Default Options ##

....... and ..............

### END DEBIAN AUTOMAGIC KERNELS LIST

Gets rebuilt from the settings above for instance if you delete everything between those two lines then a kernel update puts back in the three Ubuntu boot options.

Code:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Note that it uses my groot to get (hd0,2) and my kopt to get UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346

So if you have any settings for any other operating system, including other Linux installs or even other Ubuntu installs move them below the line that says.
Code:

### END DEBIAN AUTOMAGIC KERNELS LIST

For example in my system it looks like this
Code:

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Slackware 11
root		(hd0,1)
kernel		/boot/vmlinuz root=/dev/hda2 ro

title		Slackware 11-Safe
root		(hd0,1)
kernel		/boot/safe root=/dev/hda2 ro single

title		WinXP
rootnoverify	(hd0,0)
makeactive
chainloader +1

Please point out any mistakes in my post.
__________________
"A tool is but the extension of a man's hand, and a machine is but a complex tool. And he that invents a machine augments the power of man and the well-being of mankind."
Henry Ward Beecher (1813-87)
Thanks

---

### Post by quixote on 2007-12-25
> **SomeLuser said:**
> Kernel update today...
I'm getting the GRUB file-not-found-error...

 I'm on one of those Dell desktops that come preinstalled with Ubuntu, so I know they messed with the partitions a bit and I'm afraid to do anything to them, since I'm sure someone here can walk me through it if I need it ;-) .

I'm successfully not panicking, so... what should I do?

Pumalite has the long and, I believe, permanent answer.  I use a kludge which I think is a bit simpler, but has to be repeated every time the Ubuntu folks decide to fuss with the kernel or its headers.  WHY THEY DON'T FIX THIS PROBLEM, I DON'T KNOW!  (Are you listening, Ubuntu gods?)

**The short version is: 1) figure out which partition Ubuntu is on;  2) edit /boot/grub/menu.lst to reflect that.**  

**1)** Take one of your LiveCDs and boot from that.  Your hard drives will not be mounted.  Check under /media for the partitions on your system.  Finding the right partition is the only hard part.

Mount the one you think is your Ubuntu partition (Right-click and choose "mount").  It's usually possible to tell by the size.  If it's the right one, it'll have files like these in the / directory: > bin    dev      home        lib    mnt   root     srv  usr boot   etc      initrd      lib64  opt   sbin     sys  var cdrom  initrd.img  media  proc  selinux  tmp  vmlinuz
and like these in /boot: > config-2.6.18-3-686      initrd.img-2.6.18-3-686.bak  System.map-2.6.18-3-686  grub   lost+found     vmlinuz-2.6.18-3-686
initrd.img-2.6.18-3-686  memtest86+.bin (It doesn't need to match perfectly, but it should be similar.)

What you want to do is edit /boot/grub/menu.lst on the ubuntu partition:

**2)** Open a terminal window.  Type "sudo gedit /media/ubuntu-partition/boot/grub/menu.lst"  (No quotes, and the "/media/ubuntu-partition" should match whatever your actual pathname is.)  (It's also good practice to make a backup copy *before* messing with it:  cp /media/ubuntu-partition/boot/grub/menu.lst /media/ubuntu-partition/boot/grub/menu-lst-not-working)

It'll open gedit.  Look for the lines that concern booting ubuntu, usually toward the bottom.  As in Pumalite's example, for instance:>  title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e7cf76ab-c3bf-468a-8359-a77f65d99346 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic

What the kernel update does for some reason is increment the "root (hd0,2)" to the wrong number.  So, if you know your Ubuntu partition is (hd0,5) --following grub's bizarre numbering scheme, as pumalite shows -- you'll see that it's been renumbered to (hd0,7). 

All you have to do is change all the Ubuntu lines with the wrong numbers to the right ones. Save.

Unmount the partition.  Shut down.  Reboot with no CD, and if you've given it the right (hd#,#) designation, grub will be working away as usual.  If it worked, write down the correct (hd#,#) for your partitions, and keep it with your liveCD.  You'll need it the next time the kernel is updated and they haven't fixed this... :-?

---

### Post by SomeLuser on 2007-12-27
> **quixote said:**
> What you want to do is edit /boot/grub/menu.lst on the ubuntu partition:


I understand all of this, and thank you for yor time; unfortunately, despite having found all my files (they're still there)... /boot is empty! I believe I forgot to mention that I didn't actually tell my computer to reboot; I think it was on for a few days, back and forth through 'suspend', and one time I left it to eat or something unusual like that, and when I got back, 'file not found'... :-(

Any way I can put /boot back? I have some backups eating up loads of disk space in /var, perhaps I can put both the kernel and grub's lists back from there? I'm pretty sure Dell put GRUB itself on its own partition.

I'm still not panicking, since my personal files seem more or less safe, however if there's anything I can do to fix it without using black magic and arcane UN*X spells, I'd be quite appreciative.

---

