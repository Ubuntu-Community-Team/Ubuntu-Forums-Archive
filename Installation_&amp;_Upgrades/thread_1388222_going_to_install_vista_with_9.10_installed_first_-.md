---
title: "going to install vista with 9.10 installed first -plans"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by mr clark25 on 2010-01-22
i am wanting to install windows vista, but already have ubuntu installed. i have 100gb of my HD left over, and wish to install it there. but, windows says that my hard rive is bad.

i think i can fix this temporarily by putting a "." in front of my "boot" file. 

i think i will need to use the windows partitioner, because i can't format it as ntfs for some reason. (gparted) i would really like to use gparted (i dont trust the windows partitioner). the blank 100gb is recognized as "unknown". i think i should be able to use the "format to" to format it to ntfs, but it can't be clicked. any ideas on how to use gparted? 

then, after windows is installed, i remove the "." from the linux boot file, and put a dot in front of the windows "boot" file, and boot into linux, and run "sudo update-grub".

i think all should be well then. (working linux & vista)

to me, this sounds like it should work. if anyone spots any flaws, please say so.

sorry if i am hard to follow at times.

---

### Post by presence1960 on 2010-01-22
post a shot of your disk from gparted. Appications > Accessories > Take Screenshot.

---

### Post by mr clark25 on 2010-01-22
here are two screenshots of gparted.

it seems odd to me that so many formatting options aren't "clickable"

---

### Post by presence1960 on 2010-01-22
Do you have ntfsprogs installed? If not open a terminal and run ```
sudo apt-get install ntfsprogs
```

Then open gparted and ntfs should be an option to format to.

You can try deleting that sda1 first and creating a new partition from the unallocated space. But either way install ntfsprogs.

Another option is to leave that space after deleting sda1 as unallocated. The windows partitioner should recognize that and give you the option to either install to that or create a partition from the space to install to.

---

### Post by mr clark25 on 2010-01-22
thanks! i now have 100gb of my hard drive partitioned as ntfs for windows.

now, does the dot (".") idea sound like a good one?

i think it should work (but will it?). i wont be able to get back here until Sunday, so ill check back then.

---

### Post by presence1960 on 2010-01-22
> **mr clark25 said:**
> thanks! i now have 100gb of my hard drive partitioned as ntfs for windows.

now, does the dot (".") idea sound like a good one?

i think it should work (but will it?). i wont be able to get back here until Sunday, so ill check back then.

That is not a good idea, you will not need to change anything concerning directories or file names. Install Windows. Windows will overwrite GRUB on the MBR. When the install is complete reboot and make sure windows boots fine. Then you are going to have to reinstall GRUB. If you don't know how post back. Installing it to the wrong place can cause more problems. You want to install it to MBR not a partition. Depending on which version of GRUB you have will determine which method you will use to reinstall GRUB.

---

### Post by mr clark25 on 2010-01-24
ok, i will do that. but, i have one question. (i should know this) what is MBR?


i think to re-install grub, i have to chroot into my system from a live usb, and run some commands. ill look up the commands if this is right.

windows will leave my Ubuntu partition alone, wont it?

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> ok, i will do that. but, i have one question. (i should know this) what is MBR?


i think to re-install grub, i have to chroot into my system from a live usb, and run some commands. ill look up the commands if this is right.

windows will leave my Ubuntu partition alone, wont it?

1. Windows will leave your other partitions alone providing you select only the NTFS partition for the windows install. Do not delete or format any partitions from the windows installer. You already have then created.

2. In most cases to reinstall GRUB you do not need to chroot. Let me know what version of GRUB you were using and I'll give you instructions/commands.

3. Without getting technical MBR = Master Boot Record. It is on the very beginning of the disk before the first partition. It is a place that houses your bootloader among other things. Every hard disk has an MBR.

---

### Post by mr clark25 on 2010-01-24
ok, thanks.

i have grub legacy running, but i have the option to chainload into grub2, which works fine. so, whichever is easier is what i will end up using (i think) which do you think i should use?

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> ok, thanks.

i have grub legacy running, but i have the option to chainload into grub2, which works fine. so, whichever is easier is what i will end up using (i think) which do you think i should use?

Personally I would recommend GRUB2. All the complaining and whining you hear about GRUB2 on the forums is mostly not because GRUB2 is "bad" but due to human nature. people are familiar with legacy GRUB and don't invest the time to learn about GRUB2. GRUB2 is very different but that does not make it "bad". But that is human nature- to resist change even if the thing you are clinging to is inferior. By clinging to the old there is a sense of control because no matter what the problems are with it, at least one knows what to expect. I am not saying Legacy GRUB is "bad", but with all the advances in hard disks, etc today Legacy GRUB will soon have to be buried.

Here are a couple links for you about GRUB2:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by OrangeCrate on 2010-01-24
Honestly, you might want to do a quick read of this, before you go much further...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Vista and Windows 7 really, really, don't like to be installed second.

---

### Post by mr clark25 on 2010-01-24
ok, so i want to update to grub2 before i install vista, right? or would that not make any sense because its about to be wiped? 

does this give me the go-ahead to install vista?

---

### Post by presence1960 on 2010-01-24
> **OrangeCrate said:**
> Honestly, you might want to do a quick read of this, before you go much further...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Vista and Windows 7 really, really, don't like to be installed second.

I installed Vista OEM after Karmic, Sabayon & Lucid. I did it to get rid of XP. There was no problem reinstalling GRUB2 to MBR. See here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Note #11- subtitle #1- Reinstalling GRUB2 from Live CD

Most of the problems with GRUB2 that people rant about  are because of ignorance about GRUB2. While there are a few issues still existing for the most part GRUB2 does what it is supposed to do. Just as for the most part Legacy GRUB does what it is supposed to. neither are perfect, but whether we like it or not Legacy GRUB is deficient when it comes to the advances with hardware and will be retired with Lucid going forward. Everyone must take the time to learn about GRUB2 which is not hard or else...

Besides when was the last time legacy GRUB was updated? So much for all those who want bleeding edge or the most current stuff.

That is a myth about windows not liking to be installed second. Are you telling me someone who has linux installed and wants to add Vista/7 must remove a perfectly good install to put windows first? That is a bunch of bolderdash! The only thing that happens when windows is installed after linux is GRUB is replaced on the MBR by windows bootloader. All you need to do to recover is boot the Live CD and reinstall GRUB to MBR. That windows must be installed first myth is one of the biggest fallacies perpetuated in this community. It continues to live on because those who shout it fail to investigate what really happens when you install windows after linux and what the simple- yes simple- fix is for that.

P.S. sorry if I am ranting but this is my biggest pet peeve in here. It is not meant for you personally. I am not attacking you but rather the faulty information.

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> ok, so i want to update to grub2 before i install vista, right? or would that not make any sense because its about to be wiped? 

does this give me the go-ahead to install vista?

Install Vista.

---

### Post by OrangeCrate on 2010-01-24
@ mr clark25,

Along with the first link I provided, it would be helpful to read this too...

[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

---

### Post by mr clark25 on 2010-01-24
thanks for the links.

going to try to install vista now...   wish me luck.

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> thanks for the links.

going to try to install vista now...   wish me luck.

no luck is involved. prepare and have the knowledge. Then do it.

---

### Post by mr clark25 on 2010-01-24
i prepared, but something happened.

windows didn't like my hard drive, so i put the drivers&utilities disk in with the vista disk, and i got the same result. then, i tried to boot to ubuntu, and nothing happened at the bios screen. i think grub may have been killed.

i changed the boot order in my bios, so ill change it back and see if that fixes it.

windows gave me the following error:

"windows could not determine if this computer contains a valid system volume."

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> i prepared, but something happened.

windows didn't like my hard drive, so i put the drivers&utilities disk in with the vista disk, and i got the same result. then, i tried to boot to ubuntu, and nothing happened at the bios screen. i think grub may have been killed.

i changed the boot order in my bios, so ill change it back and see if that fixes it.

windows gave me the following error:

"windows could not determine if this computer contains a valid system volume."

why did you change the boot order? I thought you wanted to put windows on sda1 which was formatted to NTFS?

You never mentioned a second hard disk before either. I need to see exactly what you have on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by mr clark25 on 2010-01-24
i had to change the boot order because i had my hard drive set to boot first, and i have a windows disk.

whats really strange is that i can now boot into Ubuntu again. (changed the hard drive back to first) i think i have a faulty bios.

i think the bios bug might also be related to why i can't install windows.

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> i had to change the boot order because i had my hard drive set to boot first, and i have a windows disk.

whats really strange is that i can now boot into Ubuntu again. (changed the hard drive back to first) i think i have a faulty bios.

i think the bios bug might also be related to why i can't install windows.

exactly what happened when you tried to boot the windows install disk?

---

### Post by mr clark25 on 2010-01-24
it did what it was supposed to, up untill the partitionizer. it let me select the ntfs partition, and then i hit continue. then it said that the installetion was cancelled, and gave me that error message. ("windows could not determine if this computer contains a valid system volume.")

it all seems very odd to me.

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> it did what it was supposed to, up untill the partitionizer. it let me select the ntfs partition, and then i hit continue. then it said that the installetion was cancelled, and gave me that error message. ("windows could not determine if this computer contains a valid system volume.")

it all seems very odd to me.

Try this: Boot the windows install disk. At the partitioner highlight the NTFS partition and delete it. You may have to hit change/modify or something like that. Then create the NTFS partition (from the unallocated space) from the installer and try installing to it. Sometimes, not often windows does not recognize NTFS partitions created from gparted.

---

### Post by mr clark25 on 2010-01-24
ok, ill try that tomorrow. its time for bed now.

---

### Post by presence1960 on 2010-01-24
> **mr clark25 said:**
> ok, ill try that tomorrow. its time for bed now.

kool, rest well!

---

### Post by OrangeCrate on 2010-01-25
> **mr clark25 said:**
> thanks for the links.

going to try to install vista now...   wish me luck.

You're welcome, and good luck.

:)

---

### Post by mr clark25 on 2010-01-25
well, it was a bios bug. i fixed it by hitting F12 during startup (loads boot manager) and selected to boot from the cd instead of my hard drive.

so, it did take to the partition that i created with gparted.

now, what do i need to do to get grub back?

---

### Post by presence1960 on 2010-01-25
> **mr clark25 said:**
> well, it was a bios bug. i fixed it by hitting F12 during startup (loads boot manager) and selected to boot from the cd instead of my hard drive.

so, it did take to the partition that i created with gparted.

now, what do i need to do to get grub back?

Boot the 9.10 Live CD and choose "try ubuntu without any changes". When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo mount /dev/sda5 /mnt
```
This will mount your ubuntu / partition. Then in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB back on MBR. Reboot without the Live CD and when Ubuntu boots open a terminal and run ```
sudo update-grub
```
You should be good to go & next time you boot try booting windows.

---

### Post by mr clark25 on 2010-01-25
ok, will do when windows update gets done. its at 93% done downloading right now, so ill report back after i do that.

---

### Post by presence1960 on 2010-01-25
If you don't have a 9.10 Live CD do this. Boot the 9.04 Live CD and choose "try ubuntu without any changes". When the desktop loads open a terminal and do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

Boot into Ubuntu, open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```
That is a lowercase L in .lst
Scroll down to here
### END DEBIAN AUTOMAGIC KERNELS LIST 

skip one line and add:

```
title          Windows Vista
rootnoverify   (hd0,0)
chainloader    +1
```

Click Save on top toolbar & close file. Reboot & try booting to windows.
Reboot and try using the chainload to GRUB2 entry to check if GRUB2 works.
If you can successfully boot both OSs from the chainload to GRUB2 link for a couple days I would then upgrade to GRUB2 since it is all inplace. All you need to do is run this command from terminal ```
upgrade-from-grub-legacy
```
You may need to preface that command with sudo if it does not work. After this you will be on GRUB2 and will need a 9.10 Live CD to make repairs or adjustments.

---

### Post by mr clark25 on 2010-01-25
well, i got grub & ubuntu back, but now windows is gone. (grub didnt find it) it says 1.97 beta grub, so that means grub2, doesnt it?

when i run "sudo update-grub" i get this:

```
sudo update-grub
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Generating grub.cfg ...
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
error: cannot open `/dev/sdc' while attempting to get disk size
Found memtest86+ image: /boot/memtest86+.bin
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
done

```looks to me like something is missing. i followed the first set of instructions you gave me since i have a 9.10 bootable USB.

i ran the boot info script again. maybe that will help. here it is:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,711,103   209,709,056   7 HPFS/NTFS
/dev/sda2         209,712,510   488,279,609   278,567,100   5 Extended
/dev/sda5         419,425,083   485,355,779    65,930,697  83 Linux
/dev/sda6         485,355,843   488,279,609     2,923,767  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1977 MB, 1977614336 bytes
64 heads, 63 sectors/track, 957 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                 135     3,858,623     3,858,489   6 FAT16


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="37A74BB00D62AB25" TYPE="ntfs" 
/dev/sda5: UUID="430e8379-70a1-4e2c-a3da-e3762ef6c44c" TYPE="ext3" 
/dev/sda6: UUID="090437ab-200c-4fcd-a6fe-abf98e50de4a" TYPE="swap" 
/dev/sdf1: SEC_TYPE="msdos" UUID="6531-3036" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)
/dev/sdf1 on /media/6531-3036 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/37A74BB00D62AB25 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=430e8379-70a1-4e2c-a3da-e3762ef6c44c

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro quiet splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro quiet splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro quiet splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        430e8379-70a1-4e2c-a3da-e3762ef6c44c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=-1
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 430e8379-70a1-4e2c-a3da-e3762ef6c44c
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c ro single 
    initrd    /boot/initrd.img-2.6.28-16-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=430e8379-70a1-4e2c-a3da-e3762ef6c44c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=090437ab-200c-4fcd-a6fe-abf98e50de4a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 214.7GB: boot/grub/core.img
 214.7GB: boot/grub/grub.cfg
 214.7GB: boot/grub/menu.lst
 214.7GB: boot/grub/stage2
 214.7GB: boot/initrd.img-2.6.28-16-generic
 214.7GB: boot/initrd.img-2.6.31-14-generic
 214.7GB: boot/initrd.img-2.6.31-15-generic
 214.7GB: boot/initrd.img-2.6.31-16-generic
 214.7GB: boot/initrd.img-2.6.31-17-generic
 214.7GB: boot/vmlinuz-2.6.28-16-generic
 214.7GB: boot/vmlinuz-2.6.31-14-generic
 214.7GB: boot/vmlinuz-2.6.31-15-generic
 214.7GB: boot/vmlinuz-2.6.31-16-generic
 214.7GB: boot/vmlinuz-2.6.31-17-generic
 214.7GB: initrd.img
 214.7GB: initrd.img.old
 214.7GB: vmlinuz
 214.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by presence1960 on 2010-01-25
Looks like your device.map has a sdc device in there. You don't have an sdc device so remove it from device.map

Open a terminal and run ```
gksu gedit /boot/grub/device.map
```
Remove the entry for sdc. Click save on top toolbar and close file. Try running command ```
sudo update-grub
```

P.S. If after the above it still does not work try running this in terminal ```
upgrade-from-grub-legacy
```

---

### Post by mr clark25 on 2010-01-25
i had to remove /dev/sdc and /dev/sdb from the device map.
i ran [FONT=monospace]"[/FONT]sudo upgrade-from-grub-legacy" because it complained about permissions, but still got this:
```

$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found memtest86+ image: /boot/memtest86+.bin
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
done

```

---

### Post by presence1960 on 2010-01-25
I noticed from your mount output from your last boot info script that your vistta partition is mounted. Are you running those commands with sda1 mounted? I don't think it should make a difference but unmount it and run those commands.

Also take out the flash disk if you have it plugged in.

---

### Post by mr clark25 on 2010-01-25
tried that to, and it still didnt work. :(

---

### Post by presence1960 on 2010-01-25
> **mr clark25 said:**
> tried that to, and it still didnt work. :(

I have never seen those error messages before. maybe you can try createing a custom entry for Vista. See the link here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

see #6 near bottom of #6 Manual windows entry.

I have to give my daughter a bath and read her a story. i will be back later to research this and maybe contact someone who may know what those errors are.

---

### Post by OrangeCrate on 2010-01-25
> **mr clark25 said:**
> tried that to, and it still didnt work. :(

Please go back, and read the links I provided from the Ubuntu Guide series, and do the installation as they suggested. I've done a half dozen dual boot setups for friends and family just in the last couple of months alone, and it always works for me.

Short version:

1. Backup your Home Folder (dragging the files and folders to a stick is probably the easiest way).

2. Use GParted from a Live CD to reformat the drive to NTFS.

3. Install a fresh copy of Vista.

4. Cut out a chunk of the hard drive (I always use 30 gig), to install Ubuntu in (follow the instructions from the links).

5. And finally, get a cold beverage of your choice, and enjoy your new dual booted computer.

Frankly, I think your grand experiment here, is going from bad to worse. But hey, that's just my opinion.

---

### Post by mr clark25 on 2010-01-25
> **OrangeCrate said:**
> Please go back, and read the links I provided from the Ubuntu Guide series, and do the installation as they suggested. I've done a half dozen dual boot setups for friends and family just in the last couple of months alone, and it always works for me.

Short version:

1. Backup your Home Folder (dragging the files and folders to a stick is probably the easiest way).

2. Use GParted from a Live CD to reformat the drive to NTFS.

3. Install a fresh copy of Vista.

4. Then cut out a chunk (I always use 30 gig), to install Ubuntu in.

5. Then get a cold beverage of your choice, and enjoy your new dual booted computer.

(Frankly, IMO, I think your grand experiment here, is going from bad to worse.)

that would be a lot more work than it sounds like :(
i have (mostly my parents) almost 30gb of data, and my parents wouldn't like me doing it that way. (risk)

for now, i still have what i started with, so it will work for now.

---

### Post by OrangeCrate on 2010-01-25
> **mr clark25 said:**
> that would be a lot more work than it sounds like :(
i have (mostly my parents) almost 30gb of data, and my parents wouldn't like me doing it that way. (risk)

for now, i still have what i started with, so it will work for now.

Fair enough. Then stick with what you guys are doing, and hopefully, it'll all work out. Not much more I can contribute here, so, good luck.

:)

---

### Post by mr clark25 on 2010-01-25
looks like its been reported on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/387093](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/387093)

looks like they fixed it by "temporarily removing /bin/mapdevfs", but im not to sure about that...

and found it again here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535727.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535727.html)

---

### Post by presence1960 on 2010-01-25
> **mr clark25 said:**
> looks like its been reported on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/387093](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/387093)

looks like they fixed it by "temporarily removing /bin/mapdevfs", but im not to sure about that...

and found it again here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535727.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1535727.html)

Ok, that is definitely a bug, but this is the first time I am hearing of it. I have installed Vista after Linux many times on my machine & for clients without a hitch. So try what the bug report says to do-"temporarily removing /bin/mapdevfs.

First I removed it from my system and ran sudo update-grub and it updated the grub.cfg successfully so it looks like no harm was done by removing mapdevfs from /bin and placing it in /home.

Open a terminal and run ```
gksu nautilus
``` from Ubuntu.

When the root file browser opens highlight Filesystem in the left pane. Open the bin directory on the right. Find mapdevfs, right click on it and choose cut, then in filesystem open the home directory, then your user directory and right click and paste the file in home. Open a terminal and run ```
sudo update-grub
``` and see what happens. If it detects windows or not return the file to bin with the same procedure that you used to move it.

I would also try updating Ubuntu as I read somewhere that the problem seemed to go away with updates.

---

### Post by mr clark25 on 2010-01-26
it worked!

found the vista kernel, and will now see if i can boot into vista.

booted into vista, and it works great!

thanks for the help!

---

### Post by presence1960 on 2010-01-26
> **mr clark25 said:**
> it worked!

found the vista kernel, and will now see if i can boot into vista.

booted into vista, and it works great!

thanks for the help!

Glad you got it working. You really helped me out by finding that bug report. I had never heard of that bug before. Thanks!

---

### Post by presence1960 on 2010-01-26
**_Moral of the story: you do not have to install any windows OS first to create a dual boot setup! The notion that you must have windows installed first is one of the biggest fallacies propagated in this community._**

Note that while we had a difficult time here that was not because windows was installed after linux, but rather it was caused by a bug in ubuntu. So it would not have mattered even if ubuntu was installed after windows- the bug still would have prevented sudo update-grub from detecting the windows installation unless you used the workaround from the bug report.

---

