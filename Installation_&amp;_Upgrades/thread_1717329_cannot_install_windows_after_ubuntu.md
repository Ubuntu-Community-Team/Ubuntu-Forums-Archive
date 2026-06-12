---
title: "cannot install windows after ubuntu"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by eladriels on 2011-03-29
my friend who is new to linux, installed ubuntu and deleted win. now wants to reinstall windows. i used gparted to create a partiton ntfs format (for beginning:)). when i try to boot computer with windows 7 cd , computer doesnt recognize it and installs grup, ubuntu. i cannot install windows. i mean my problem is now i cant install windows. i searched  but couldnt find the solution.

Any help would be appreciated.
thanks in advance

---

### Post by eladriels on 2011-03-30
Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code:

1)Create an NTFS partition for windows (using fdisk, GPartEd or 2)whatever tool you are familiar with)
3)Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1
4)Install windows
5)Boot into a LiveCD
6)Mount your root partition in the LiveCD
7)Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
8)Restart and Ubuntu will boot
9)Setup grub to boot windows

*this is what i saw on help.ubuntu site, and what i want. im at 4th step and cant  move on:) when i try to boot from win cd to setup, pc doesnt recognize it . is it because ubuntu? and what can i do to install win?

Any help would be appreciated.
thanks in advance

---

### Post by Sean Moran on 2011-03-30
> **eladriels said:**
> Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code:

1)Create an NTFS partition for windows (using fdisk, GPartEd or 2)whatever tool you are familiar with)
3)Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1
4)Install windows
5)Boot into a LiveCD
6)Mount your root partition in the LiveCD
7)Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
8)Restart and Ubuntu will boot
9)Setup grub to boot windows

*this is what i saw on help.ubuntu site, and what i want. im at 4th step and cant  move on:) when i try to boot from win cd to setup, pc doesnt recognize it . **is it because ubuntu?** and what can i do to install win?

Any help would be appreciated.
thanks in advance
I'd guess not because of Ubuntu. The Windows 7 DVD  should just see the ext4 partitions as unknown, and still carry on with what NTFS partitions it can find. Do you mean that the PC doesn't recognise the Windows Install CD/DVD, or is it that the installation program doesn't recognise the disk partitions?  I assume you mean the former, but just ask to be sure.

---

### Post by eladriels on 2011-03-30
yes,PC doesn't recognise the Windows Install CD/DVD.

---

### Post by Sean Moran on 2011-03-30
> **eladriels said:**
> yes,PC doesn't recognise the Windows Install CD/DVD.
That one's got me baffled then.  Does the PC recognise ANY CDs?  If so, I'd probably try to burn up another Windows DVD just in case.  I installed Win 7 eval a couple of weeks ago, and Ubuntu and half a dozen other ext4 partitions were all there on the hard disk.  The Windows 7 DVD just saw them as unknowns and went about installing on the /dev/sda1 NTFS partition.  (I don't use those extra little boot partitions - waste of space on my hard disk)

---

### Post by eladriels on 2011-03-30
of course recognise others like ubuntu liveCD, but its problem i think with just windows:) i burned again and again another cd but still same problem:(

---

### Post by eladriels on 2011-03-30
any idea? :(

---

### Post by Sean Moran on 2011-03-30
> **eladriels said:**
> any idea? :(
Not really.  I'm lost for an answer as to why your friend's CD-ROM can read other CDs but not the Windows CD/DVD.  I call it a DVD because the WIn7 Eval I installed was 2.2GB from memory.  Anyway, the Windows CD/DVD should boot up something, regardless of what partitions and other OSs you have.

If it's possible to remove EVERYTHING, and start from scratch, you'll no doubt isolate the problem if there is one.  In any case, it's usually best to install Windows first, and Linux later, to avoid having to backup and restore the MBR and GRUB.  The trouble is, I don't see how removing Linux will make the Windows CD suddenly start working if it isn't already, but if you've tried the Windows CDs a few times and it still isn't working (while other CDs are), then that's about all I can think to do.

---

### Post by coffeecat on 2011-03-30
@eladriels, a couple of times you said  Windows 7 **CD. **There is no such thing as an installation CD for Windows 7. Windows 7 installation comes on a DVD. However, there is a Windows 7 repair CD which looks a little like the installation DVD when you first boot it up.

Please confirm: are you using a CD or DVD?

---

### Post by eladriels on 2011-03-30
@Sean Moran, thanks a lot:)

---

### Post by eladriels on 2011-03-30
Sorry, it is Win 7 DVD of course that i am using, my bad.

---

### Post by eladriels on 2011-03-30
> **coffeecat said:**
> @eladriels, a couple of times you said  Windows 7 **CD. **There is no such thing as an installation CD for Windows 7. Windows 7 installation comes on a DVD. However, there is a Windows 7 repair CD which looks a little like the installation DVD when you first boot it up.

Please confirm: are you using a CD or DVD?
sorry, of course it is Win 7 Dvd that im using, my bad...

---

### Post by eladriels on 2011-03-30
i also have a ntfs format partition and its flag is boot, still win7dvd isnt working. on boot i choose my disc drive but then grup is loading:)

---

### Post by Sean Moran on 2011-03-30
> **eladriels said:**
> i also have a ntfs format partition and its flag is boot, still win7dvd isnt working. on boot i choose my disc drive but then grup is loading:)
I really get the feeling that something might be wrong with the Windows7 DVD.  If you boot the DVD and it sees something it doesn't like, it should at least render an error message.  It's stranger than weird, this one.

Can you test the Windows7 DVD on another machine to see if it's good?

Can you try out something like a standard Windows XP CD on this machine to see if it gets to the setup startup Press F8 to install kind of page?  

All in all, it should work.  Maybe I'm just too lucky to know what I'm talking about.

---

### Post by eladriels on 2011-03-30
> **Sean Moran said:**
> I really get the feeling that something might be wrong with the Windows7 DVD.  If you boot the DVD and it sees something it doesn't like, it should at least render an error message.  It's stranger than weird, this one.

Can you test the Windows7 DVD on another machine to see if it's good?

Can you try out something like a standard Windows XP CD on this machine to see if it gets to the setup startup Press F8 to install kind of page?  

All in all, it should work.  Maybe I'm just too lucky to know what I'm talking about.

DVD is okay, its working another computer, i tested. i used vista dvd also, but same as before :s

---

### Post by Sean Moran on 2011-03-30
> **eladriels said:**
> DVD is okay, its working another computer, i tested. i used vista dvd also, but same as before :s
I'm out of ideas, mate.  The Windows DVD works on other computers, but doesn't work on your friend's computer.  Other CDs work on your friend's computer.  Your friend's computer has a blank hard disk with nothing there for Windows to whinge about, but of all the CDs, only the Windows7 DVD doesn't work but all the other ones do.  Can you see how this leaves me without an answer?

Maybe now this has become purely a Windows problem.

Good luck mate.

---

### Post by coffeecat on 2011-03-30
Sorry to keep going on about CDs vs DVDs, but this has to be asked. Are you sure the optical drive on your friend's computer can read DVDs? It's not an old-fashioned CD-ROM drive, is it?

---

### Post by eladriels on 2011-03-30
yes i'm sure, i can access win7 DVD on ubuntu and optical drive also support it , the problem is i can't boot with it

---

### Post by kansasnoob on 2011-03-31
> **eladriels said:**
> yes i'm sure, i can access win7 DVD on ubuntu and optical drive also support it , the problem is i can't boot with it

I received a PM from eladriels and (s)he included  the output of fdisk -l and df -H:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf112641c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3990    32049643+   7  HPFS/NTFS
/dev/sda2            9236       10937    13671315    5  Extended
/dev/sda3           10938       19457    68436900    7  HPFS/NTFS
/dev/sda4            3991        9235    42130462+   7  HPFS/NTFS
/dev/sda5            9236       10451     9767488+  83  Linux
/dev/sda6           10452       10937     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d8fd9a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       48641   390708801    7  HPFS/NTFS

ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  1,1G   2,5M   1,1G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1,1G   2,5M   1,1G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                  1,1G      0   1,1G   0% /lib/init/rw
varrun                 1,1G   107k   1,1G   1% /var/run
varlock                1,1G      0   1,1G   0% /var/lock
udev                   1,1G   164k   1,1G   1% /dev
tmpfs                  1,1G    78k   1,1G   1% /dev/shm
rootfs                 1,1G    45M   1,1G   5% /
/dev/sr0               733M   733M      0 100% /cdrom
/dev/loop0             708M   708M      0 100% /rofs
tmpfs                  1,1G    13k   1,1G   1% /tmp
/dev/sdb1              401G   209G   192G  53% /media/disk


```

I'm guessing that df -H was run from the live CD, eh? So we do know for sure you can run a live CD on that machine which would verify that BIOS settings are correct to allow for booting from CD/DVD.

It's also been mentioned that the Win7 DVD was "burned" but I wonder what source it was burned from :confused:

I do know that I've tried branded recovery discs that were user-created after the purchase of a PC to perform simple tasks like recovering the Win MBR on a different machine and they totally fail because Microsoft has made it even harder to "bootleg" it's crap, or to use it on any machine other than that it was originally installed on.

Now, XP was usually somewhat easier if it's "unbranded". You'd just be unable to register the sucker and get past reinstalling every 30 days. Of course you'd also be unable to update. Why your XP disc would fail to boot I'm not sure :confused:

Again I'd question the source of the Win OS, the integrity of the discs, and the condition of the hardware - specifically the CD/DVD optical drive and BIOS settings.

The output of fdisk -l does raise some questions however. I can see the box has two drives, a 160GB drive and a 400GB drive. The 400 is all one partition so I'd assume it's data :confused:

The 160 still shows what I'd suspect to be a small boot partition left over from the original Win7, but it appears you have two larger primary NTFS partitions as well.

So, if you've not already, stop booting the installed Ubuntu!

Next boot the Ubuntu Live CD and post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions for BIS here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

I'd also like you to include a physical description of the two hard drives. Are they both internal drives?

Regardless, answer that, but also include the output of:

```
sudo parted -l
```

And also post a screenshot of both drives using Gparted and the screenshot tool in Accessories :)

---

### Post by eladriels on 2011-04-02
here is  Boot Info Script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     Grub 0.97 in the file /mbr.bin looks at sector 1 of 
                       the same hard drive for the stage2 file. A stage2 file 
                       is at this location on /dev/sda. Stage2 looks on the 
                       same partition for /boot/grub/stage2.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf112641c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    64,099,349    64,099,287   7 HPFS/NTFS
/dev/sda2         148,360,275   175,702,904    27,342,630   5 Extended
/dev/sda5         148,360,338   167,895,314    19,534,977  83 Linux
/dev/sda6         167,895,378   175,702,904     7,807,527  82 Linux swap / Solaris
/dev/sda3         175,702,905   312,576,704   136,873,800   7 HPFS/NTFS
/dev/sda4          64,099,350   148,360,274    84,260,925   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        29A827EA37B9DB1D                       ntfs       c:/                           
/dev/sda3        594A90AF7C3BEEBE                       ntfs                                     
/dev/sda4        08D90C0B557CED97                       ntfs                                     
/dev/sda5        ddafdc74-fc71-4b0e-a674-20b62a24a846   ext4                                     
/dev/sda6        3b17fd22-825b-4443-9526-9c2a85849927   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/menu.lst: ================================

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
# kopt=root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ddafdc74-fc71-4b0e-a674-20b62a24a846

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.10, kernel 2.6.31-23-generic
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.31-23-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-23-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.31-23-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro  single
initrd		/boot/initrd.img-2.6.31-23-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


  26.2GB: menu.lst

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
# kopt=root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ddafdc74-fc71-4b0e-a674-20b62a24a846

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 9.10, kernel 2.6.31-23-generic
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.31-23-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-23-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.31-23-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro  single
initrd		/boot/initrd.img-2.6.31-23-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		ddafdc74-fc71-4b0e-a674-20b62a24a846
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=ddafdc74-fc71-4b0e-a674-20b62a24a846 / ext4 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=3b17fd22-825b-4443-9526-9c2a85849927 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda5: Location of files loaded by Grub: ===================


  79.9GB: boot/grub/menu.lst
  77.7GB: boot/grub/stage2
  76.4GB: boot/initrd.img-2.6.28-11-generic
  77.5GB: boot/initrd.img-2.6.31-23-generic
  77.8GB: boot/vmlinuz-2.6.28-11-generic
  79.1GB: boot/vmlinuz-2.6.31-23-generic
  77.5GB: initrd.img
  76.4GB: initrd.img.old
  79.1GB: vmlinuz
  77.8GB: vmlinuz.old


```


here is gparted's screenshot
[http://img689.imageshack.us/i/gpartedp.png/](http://img689.imageshack.us/i/gpartedp.png/)

and parted -l screenshot
[http://img848.imageshack.us/f/partedl.png/](http://img848.imageshack.us/f/partedl.png/)

and 400gb hard disk is an external hard disk, dont mind that.other one is internal.  



Thanks in advance:)

---

### Post by kansasnoob on 2011-04-03
Thanks for the PM, seriously. I stop looking after 24 hours :)

I'm in the middle of something but I'll have a look at this ASAP, unfortunately that could be tomorrow :(

---

### Post by kansasnoob on 2011-04-04
Well I don't like that partitioning arrangement at all, but that doesn't explain why the Win7 DVD won't even boot.

We know that the BIOS settings must be right because you can boot an Ubuntu Live CD, also the Win7 DVD will boot on another machine so I assume the DVD is good.

That really leaves only one option I can think of and that's the optical drive itself. If you install the package "hwinfo" from the repos using your preferred method you can then just run the command:

```
hwinfo --short > hwinfo.txt
```

Then if you look in the home folder you should find a new file named hwinfo.txt, open it and just as an example here's what mine looks like (with the cdrom info in red):

```
cpu:
                       Intel(R) Atom(TM) CPU  230   @ 1.60GHz, 1600 MHz
                       Intel(R) Atom(TM) CPU  230   @ 1.60GHz, 1600 MHz
keyboard:
  /dev/input/event2    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      ImExPS/2 Logitech Wheel Mouse
printer:
  /dev/usb/lp0         HP Deskjet 5400 series
graphics card:
                       Intel 945G
sound:
                       Intel 82801G (ICH7 Family) High Definition Audio Controller
storage:
                       Floppy disk controller
                       Intel 82801GB/GR/GH (ICH7 Family) SATA IDE Controller
network:
  eth0                 Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             WDC WD5000AAKS-0
  /dev/sdb             WDC WD800JB-00JJ
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sda7            Partition
  /dev/sda8            Partition
  /dev/sda9            Partition
  /dev/sda10           Partition
  /dev/sda11           Partition
  /dev/sda12           Partition
  /dev/sda13           Partition
  /dev/sda14           Partition
  /dev/sda15           Partition
  /dev/sda16           Partition
  /dev/sda17           Partition
  /dev/sda18           Partition
  /dev/sdb1            Partition
  /dev/sdb2            Partition
  /dev/sdb5            Partition
[B][COLOR="Red"]cdrom:
  /dev/sr0             ASUS DRW-24B1ST[/COLOR][/B]
usb controller:
                       Intel 82801G (ICH7 Family) USB UHCI Controller #1
                       Intel 82801G (ICH7 Family) USB UHCI Controller #2
                       Intel 82801G (ICH7 Family) USB UHCI Controller #3
                       Intel 82801G (ICH7 Family) USB UHCI Controller #4
                       Intel 82801G (ICH7 Family) USB2 EHCI Controller
bios:
                       BIOS
bridge:
                       Intel 82945G/GZ/P/PL Memory Controller Hub
                       Intel 82801G (ICH7 Family) PCI Express Port 1
                       Intel 82801G (ICH7 Family) PCI Express Port 2
                       Intel 82801 PCI Bridge
                       Intel 82801GB/GR (ICH7 Family) LPC Interface Bridge
hub:
                       Linux 2.6.38-7-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.38-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-7-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.38-7-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
  /dev/lp0             Parallel controller
                       Intel 82801G (ICH7 Family) SMBus Controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Serial controller
                       HP Deskjet 5400 series
```

So I could then google the exact model of optical drive, eg: ASUS DRW-24B1ST. In that case I'd find that it's a true multi-drive so it should work with all DVD discs whether they're DVD-R or DVD+R. Some drives are not compatible with both.

Perhaps you could borrow a USB DVD drive? Or if it's a desktop replacing the drive should be fairly simple and inexpensive. Otherwise I'm stumped.

But about the existing partition setup, well if I were you I'd back up any data you wish to save from Ubuntu and then wipe the drive, start fresh with Windows only, and then carefully install Ubuntu afterwards.

I mean that's Ubuntu 9.10 which is only supported until the end of this month, and the partitioning arrangement is rather a mess.

---

### Post by eladriels on 2011-04-04
Well, i guess the optical device supports what i need :)
```
cpu:
                       Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz, 2000 MHz
                       Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz, 800 MHz
keyboard:
  /dev/input/event4    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Elan Microelectronics Optical Mouse
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      SynPS/2 Synaptics TouchPad
graphics card:
                       Intel 965 GM
                       Intel Mobile GM965/GL960 Integrated Graphics Controller
sound:
                       Intel 82801H (ICH8 Family) HD Audio Controller
storage:
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
                       Intel 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
network:
  eth0                 Intel 82562GT 10/100 Network Connection
  wlan0                Hewlett-Packard Company Compaq 6710b
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wmaster0             Network Interface
  wlan0                WLAN network interface
  pan0                 Ethernet network interface
disk:
  /dev/sda             Hitachi HTS54161
  /dev/sdb             Kingston DT 101 II
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda3            Partition
  /dev/sda4            Partition
  /dev/sda5            Partition
  /dev/sda6            Partition
  /dev/sdb1            Partition
cdrom:
  /dev/sr0             MATSHITA DVD-RAM UJ-861H
usb controller:
                       Intel 82801H (ICH8 Family) USB UHCI Controller #4
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #1
                       Intel 82801H (ICH8 Family) USB UHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #3
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel Mobile PM965/GM965/GL960 Memory Controller Hub
                       Intel 82801H (ICH8 Family) PCI Express Port 1
                       Intel 82801H (ICH8 Family) PCI Express Port 2
                       Intel 82801H (ICH8 Family) PCI Express Port 5
                       Intel 82801 Mobile PCI Bridge
                       Intel 82801HEM (ICH8M) LPC Interface Controller
hub:
                       Linux 2.6.31-23-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-23-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.31-23-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.31-23-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.31-23-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.31-23-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
bluetooth:
                       HP Integrated Module
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
                       Unclassified device
```

so, as you said, i should try to get a usb dvd drive or something like that:) and actually right now ,my data on ubuntu isnt important i dont need any backup, so how can i "wipe the drive", i couldnt understand what did you mean by that? because i tried to format the drive where ubuntu was installed, next when i try to boot same thing happened:) i thought it was mbr problem.

anyway, thanks for all:) i appreciate you taking the time:))

---

### Post by eladriels on 2011-04-22
Hi again:)

finally i installed win 7 on my computer without any problem:)
the problem's reason was my optical driver's broken. i tried usb optical driver and problem was solved:) 

i just want to add this:) thanks for all help:)

---

