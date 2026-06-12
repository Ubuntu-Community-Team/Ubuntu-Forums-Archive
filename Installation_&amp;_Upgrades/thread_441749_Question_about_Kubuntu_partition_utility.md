---
title: "Question about Kubuntu partition utility"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by PerlMountain on 2007-05-12
Hello,

I'm doing an install of Kubuntu with a new install of Xp Pro.

When I went to the partition utility, I picked guided and I partitioned off the Windows install.

Then I was taken to the page I enter my computer name. I filled it in and clicked next and saw that I couldn't create the other partitions there.

I hit back and created my swap, and the utility said it was formatting it to EXT3, I didn't get any choice.

I hit back again and told it to use the rest of the available free space, again, it said EXT3 file system and that it would be created in /

Well, I wanted to use that one for the shared files, so FAT32, but I don't know if it's been created in the right place ( in / ) for Xp to access it.

Ideas? It's copying the files now, I just want to see if that sounds right before I try to trouble shoot something that's right looking for some issue. 

It didn't ask me anthing about the GRUB loader yet.

Thank you,

P.M.E

---

### Post by PerlMountain on 2007-05-12
Here's what it says, no mention of my last, large partition though.

P.M.E

---

### Post by louieb on 2007-05-12
All guided partitioning is going to do is shrink the XP partition and use the space for a /  (root) and a swap partition.   For complete control of how many partitions are  created and what they are used for you will need to use the manual partition option.  Don't know  whst partitioner the Kubuntu installer uses but it should be similar to GParted.  [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by PerlMountain on 2007-05-12
Ok, thank you. Yes, something is not right. It rebooted straight to Kubuntu with no option to pick which OS to use.

I wonder if I should partition the disk and then install Windows, then Kubuntu? I didn't try that, I just installed Xp and then tried to use Kubuntu to do all the partitioning.

P.M.E.

---

### Post by louieb on 2007-05-13
OK well at least you got Kubuntu installed. Now to fix the dual boot. I'm kinda surprised that the installer did not set  it up automatically. but stuff happens. 
Anything you need to know about dual booting can be found at [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/").
Any way if you need help figuring out how to set it up the way you want or just get dual booting to work. Need two things.
1st list the partition table. open a terminal window (can't remember how to do it in KDE) and copy and paste the output of ```
sudo fdisk -lu  
```
2nd copy and paste the content of you GRUB configuration file.
Press Alt+F2  and enter ```
kate /boot/grub/menu.lst
```.

Its good your doing a fresh install of everything. Now is the time to set things up the way you want.

---

### Post by PerlMountain on 2007-05-13
Ok, it's worth a note that I read much documentation and watched a couple of videos. I think I did everything step by step but 2 things are a big issue.

I can see windows from Super GRUB but I cannot boot to Windows.
I cannot see the partition that I made for shared storage (when the Kubuntu utility made it, it created EXT3 without giving me a chouce to make it FAT32.

Here is the -lu
```
perl1-compaq@Perl1-Compaq:~$ sudo fdisk -lu
Password:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders, total 58605120 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     1092419      546178+   7  HPFS/NTFS
/dev/sda2         1092420    56147174    27527377+  83  Linux
/dev/sda3        56147175    58605119     1228972+   5  Extended
/dev/sda5        56147238    58605119     1228941   82  Linux swap / Solaris
perl1-compaq@Perl1-Compaq:~$

```

Here is what I see in terminal when I type 'kate /boot/grub.menu.lst
```
perl1-compaq@Perl1-Compaq:~$ kate /boot/grub/menu.lst
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

.. and here is the output of the file /boot/grub/menu.lst
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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=51e9ee6b-b4ee-48f4-b3ad-6b425fb4ce0a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51e9ee6b-b4ee-48f4-b3ad-6b425fb4ce0a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=51e9ee6b-b4ee-48f4-b3ad-6b425fb4ce0a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thank you for helping (everyone)!

P.M.E

---

### Post by PerlMountain on 2007-05-13
Here is what I'm trying to accomplish on a 30 GB drive.

[img]http://perlmountain.com/0-temp/3038.jpg[/img]

I *could* just hose the whole OS and then partition the drive and THEN start installing Xp and then Kubuntu (again), but the reason I'm trying to do it this way is to learn how to do it with a live OS that I don't wanna hose.

I have a really nice Xp install on my main work rig that I don't want to hose when I make it into a dually, so this laptop project is for training and also to set up my backup machine first.

I just want to be successful with my own custom setups beore I help other people switch over :)

Thank you,

P.M.E

---

### Post by louieb on 2007-05-13
your fdisk look like a typical guided partition install. 
Lets see if you can get it booting XP. open config file for edit.
Alt+F2 ```
kdesu  kate /boot/grub/menu.lst
``` and paste the following at the bottom of config file reboot and see what happens.
```
 
title Win XP Home
      rootnoverify (hd0,0)
      makeactive
      chainloader +1

```

---

### Post by PerlMountain on 2007-05-13
Ok, this is what I've pasted.

```

..
...
....
title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

title Win XP Home
      rootnoverify (hd0,0)
      makeactive
      chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```

.. rebooting.

---

### Post by PerlMountain on 2007-05-13
I can see Xp, but this is what happens (sorry, phone pics).



PME

---

### Post by PerlMountain on 2007-05-13
I am going to nuke it :(

I can't even get gPartEd to load up anything except a very limited GRUB menu that doesn't seem to do anything. Not GUI, text.

I guess it's worth a mention that the HD in this Laptop is SCSI.

Need 1 answer:
Set up partitions and then install Xp?
Install Xp and THEN set up my partitions?
Or, make one extra partition (Xp + 1) and then install Xp, then work on the other freespace to make my Linux partition and my shared partition and then install Kubuntu?

I always erase a disk first by zeroing it out to start factory fresh.

Ugggh.

PME

---

### Post by louieb on 2007-05-13
[B]Congratulations 
Grub error 13 [/B]you should Google it. But basically it means your XP install is trash.   Which is probably why the installer  did not add an XP entry to GRUB automatically.   
What did you do to shrink the XP partition? it looks very small. and the swap partition looks very large.
Get a GParted live CD Go through [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") it shows you how to use it to shrink, delete and add partitions. Try it again and see if you can get Kubuntu installed on the laptop without trashing XP.

---

### Post by PerlMountain on 2007-05-13
The problem with gParted is v 0.3.4-6 will not work for me.

v 0.3.4-5 is working like it's supposed to.

The example I showed is just an image I made in an editor. My goal here is 5,20,4,1

5 = Xp
20 = Shared files
4 = Linux
1 = Linux Swap

I only used the utility in Kubuntu to make the partitions that exist now.

I'm going to start over, but I don't know if I should erase > partition > install 
or
erase > install > partition > install Linux
or
erase > install and try to let Kubuntu do the partitioning for me.

This is what gParted shows me now:

---

### Post by louieb on 2007-05-13
Just saw your last post.  Not sure SCSI makes a difference. But when you reinstall XP make the XP partition and the shared data partition the size you want and leave the space for kUbuntu unallocated.  
Haven't used the live CD since Dapper came out. But I think there is an option to use the unallocated space for the kUbuntu install.   [Psychocats Ubuntu Linux Resources]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by PerlMountain on 2007-05-13
Ok, perfect. That makes great sense. Ok, erasing now :)

PME

---

