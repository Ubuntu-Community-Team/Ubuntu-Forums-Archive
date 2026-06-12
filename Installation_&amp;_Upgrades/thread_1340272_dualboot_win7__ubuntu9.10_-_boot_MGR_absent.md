---
title: "dualboot win7 / ubuntu9.10 - boot MGR absent"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by Judas_e on 2009-11-28
Hi all 
i have a problem dual booting win 7 ultimate with my ubuntu 9.10 on:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c7b5717

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2675    21486906   83  Linux
/dev/sda2            2676       12389    78027705    5  Extended
/dev/sda3           12390       22468    80958464    7  HPFS/NTFS
/dev/sda4   *       22468       38914   132094976    7  HPFS/NTFS
/dev/sda5            2676       11866    73826676   83  Linux
/dev/sda6           11867       12389     4200966   82  Linux swap / Solaris

*-disk                  
       description: ATA Disk
       product: SAMSUNG HM320JI
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 2SS0
       serial: S1AKJD9S705187
       size: 298GiB (320GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=6c7b5717


i have an HP pavilion dv7, AMD X2, ATI rad
when i boot after the grub strage i got 

starting up 
boot MGR absent 
ctrl+alt+del to restart 

and my win7 is installed on dev/sda3 and not /dev/sda4 as u can see my boot * is on /dev/sda4 

i've tried many things and nothing did work till know so helpppppp

---

### Post by darkod on 2009-11-28
You have sda2 as extended partition and then sda3 and sda4 as primary. Not sure if that's a problem but I always try to avoid that.
In what order did you install the OSs, first Ubuntu then Windows?

---

### Post by Judas_e on 2009-11-28
first off all when i bought the laptop i used to have window vista the system crashed so i formated all the HDD installed ubuntu 9.04 then win 7 i used to got an error 2 something don't remember i fixed that with 

sudo grup 
root hd(0,0)
setup (hd0)  

and then edited my /boot/grub/menu.lst

the 3 or 4 first boots was fine then suddenly it crashed with that error 
boot MGR absent 

upgrade to 9.10 with an update of my app

and also tried the same error

sorry for my poor english 
thanks

---

### Post by phillw on 2009-11-28
> **Judas_e said:**
> first off all when i bought the laptop i used to have window vista the system crashed so i formated all the HDD installed ubuntu 9.04 then win 7 i used to got an error 2 something don't remember i fixed that with 

sudo grup 
root hd(0,0)
setup (hd0)  

and then edited my /boot/grub/menu.lst

the 3 or 4 first boots was fine then suddenly it crashed with that error 
boot MGR absent 

upgrade to 9.10 with an update of my app

and also tried the same error

sorry for my poor english 
thanks

If you only did the upgrade from 9.04 to 9.10, then it will not have updated you to Grub2 (You have to tell it do that)

For recovering Win and Ubuntu stuff, head over here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  Just bear in mind that you are STILL on the 9.04 Grub, even with a 9.10 upgrade.

I'd be tempted to try the recovery based on Grub Legacy before you consider upgrading to Grub2.

Doing an upgrade to Grub2 *may* get it to recognise your Win area, but a lot of the Howto's do rely on you having a Win boot disk (they also include instructions as to where to get one). If it doesn't see your Win area. Mine worked fine when I messed up my Grub2 update - you can a have a look at all that I did wrong over here -->  [http://ubuntuforums.org/showthread.php?t=1331465](http://ubuntuforums.org/showthread.php?t=1331465)

Regards,

Phill.

---

### Post by oldfred on 2009-11-28
I would use gparted to move the boot flag. Actually grub should with the makeactive command turn the boot flag on whichever version of windows you are booting.

IF that does not work you will have to use the windows CD to repair the windows install and then reinstall grub.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/Win7 Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by Judas_e on 2009-11-28
well i tried it all didn't work still got to try to make a recue disk and try with it. 
yeah am on grub and if it didn't work with the recue disk am gonna try to upgrade to grub2 
and then give a shot.
with gparted even if i change my flag it's the same 

thanks guys

i'll be back with news

---

### Post by wiseguyin on 2009-11-28
Hey Judas,
I just bought my new HP laptop and I am trying to create a dual boot system too. Within 24 hour of recieving my laptop, I managed to screw it up (Had to use the
recovery disks).
 
My problem  is, I have 4 partitions already created by HP. So I deleted the HP_TOOLS partition and created an extended partition instead.
 
But I think I need to delete the System recovery partition too... But I am scared.
Any suggestions? Look at the screenshot I have attached. This is my current system.
 

Thanks,

---

### Post by Judas_e on 2009-11-29
when i bought it there was only 2 partitions, C: my system and the recovery one D: i just screw it up all, new partitions and installed ubuntu and know trying the dual boot with win7 you can find all the drivers needed for your laptop after that it's just a question about the software warranty for one years that i lost buuffff it's not a big deal :D

---

### Post by wiseguyin on 2009-11-29
Ok cool... I guess , I will  just make a copy of recover partition and delete it ...
 
Thanks

---

### Post by Judas_e on 2009-11-29
you're welcomed 

guys still in the sh*t i did a recovery cd and tried didn't work got an error

missing operating system 

how can i do to fix that ?

---

### Post by Judas_e on 2009-12-06
Hey guys where have you gone heheh hope you're all doing fine for me am still stuck with my boot prob 

i updated to grub2 then on the screen boot i can see my win7 ultimate but can't boot MGR absent i try to boot from the chainload grub2 option can't boot got error 11

also there's an option saying after trying grub2 and being sure that it worked to continue the upgrade i choose it my laptop freeze and the caps lock start flashing can't do anything just turn it off 


on kernel 2.6.31.16 
 i got an error [1.840367] kernel panic-not syncing: VFS: unable to mount root fs on unknow-block (0,0)..

there's only my kernel 2.6.31.15 that i can boot from 

any suggestion am lost 
thankss

---

### Post by presence1960 on 2009-12-06
We need more specific info about your setup & boot process.

Boot into kernel 2.6.31.15 and do this:

Come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Judas_e on 2009-12-08
```

```
[SIZE=2]============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c7b5717

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848   102,901,759   102,694,912   7 HPFS/NTFS
/dev/sda2         102,901,760   205,301,759   102,400,000  83 Linux
/dev/sda3         205,301,760   412,147,711   206,845,952   7 HPFS/NTFS
/dev/sda4         412,147,712   625,139,711   212,992,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="541A7A7B1A7A5A46" TYPE="ntfs" 
/dev/sda2: UUID="20fb6fad-2af1-4bc1-9085-e3a96bdc0366" TYPE="ext3" 
/dev/sda3: UUID="88169CD3169CC39A" LABEL="Soft" TYPE="ntfs" 
/dev/sda4: UUID="6CDC015DDC0122C6" LABEL="Music" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/judas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=judas)
/dev/sda4 on /media/Music type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sda2/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# kopt=root=UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=20fb6fad-2af1-4bc1-9085-e3a96bdc0366

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

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        20fb6fad-2af1-4bc1-9085-e3a96bdc0366
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        20fb6fad-2af1-4bc1-9085-e3a96bdc0366
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        20fb6fad-2af1-4bc1-9085-e3a96bdc0366
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        20fb6fad-2af1-4bc1-9085-e3a96bdc0366
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        20fb6fad-2af1-4bc1-9085-e3a96bdc0366
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=20fb6fad-2af1-4bc1-9085-e3a96bdc0366 /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  52.6GB: boot/grub/menu.lst
  52.6GB: boot/grub/stage2
  52.6GB: boot/initrd.img-2.6.28-11-generic
  52.6GB: boot/initrd.img-2.6.31-16-generic
  52.6GB: boot/vmlinuz-2.6.28-11-generic
  52.6GB: boot/vmlinuz-2.6.31-16-generic
  52.6GB: initrd.img
  52.6GB: initrd.img.old
  52.6GB: vmlinuz
  52.6GB: vmlinuz.old
[/SIZE]
```

```

---

### Post by Judas_e on 2009-12-08
Presence 1960 10x man that's what i've got. yesterday i changed the whole partitions like you can see on the top of the thread i used to have other partitions.
know it's working fine but am facing problems with my sound (altec lansing) i have an hp pavilion dv7 model: 1428ca the output sound it's like there's a distortion and echos don't know weird.

thanks.

---

### Post by presence1960 on 2009-12-08
see here for error 11: [https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29](https://help.ubuntu.com/community/Grub2#Resolving%20an%20%22Unrecognized%20Device%20String%22%20%28Error%2011%29)

I can see you upgraded to Karmic from a dist-upgrade. Lots of problems there not just with yours. depending on your patience & tolerance you may want to do a clean install of Karmic. First back up your data and then use this little guide to have your packages currently installed on your machine to be installed on the new karmic clean install:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository.

---

### Post by Judas_e on 2009-12-08
alright !! am gonna install the .iso and then fresh install and i'll get back with news 
thanks

---

### Post by Judas_e on 2009-12-09
everything is working after the fresh install of ubuntu9.10 well like i can see my hole problem first was the bad organization of my partitions. 
while updating i left the grub like it's didn't update to grub2 both win7 and ubuntu are booting fine.
thanks guys a lot

---

### Post by presence1960 on 2009-12-09
> **Judas_e said:**
> everything is working after the fresh install of ubuntu9.10 well like i can see my hole problem first was the bad organization of my partitions. 
while updating i left the grub like it's didn't update to grub2 both win7 and ubuntu are booting fine.
thanks guys a lot

Glad to hear you got it working. As my friend raymondh would say: happy Ubuntu-ing!

---

### Post by raymondh on 2009-12-09
> **presence1960 said:**
> Glad to hear you got it working. As my friend raymondh would say: happy Ubuntu-ing!

Glad as well.

presence1960....LOL .... happy holidays, buddy.

---

### Post by Judas_e on 2009-12-11
i read somewhere don't remember where. 
when i did the account that after a thread is solved we should like say it was solved something like that how ?

---

### Post by raymondh on 2009-12-11
> **Judas_e said:**
> i read somewhere don't remember where. 
when i did the account that after a thread is solved we should like say it was solved something like that how ?

I think it's THREAD TOOLS > MARKED AS SOLVED.

Happy ubuntu-ing :)

---

