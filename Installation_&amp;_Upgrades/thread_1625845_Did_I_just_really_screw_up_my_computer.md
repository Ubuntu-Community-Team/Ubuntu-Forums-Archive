---
title: "Did I just really screw up my computer?"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by beasdd on 2010-11-19
howdy

ok, so i am a noob to ubuntu, linux, and "advanced" computer use in general.  last year, my friend partitioned some of my hard drive (vista) and installed ubuntu 9.04 on it.  for a while, I didn't really use it too much.  But recently I've started to see that it's a better coding environment for me (cs major).  
i was having a few problems here and there, so i decided to update to 9.10 through the update manager.  i was no longer able to use my mouse pad after doing this, but i eventually found a solution online that worked.  
then i decided i might as well go up to 10.04.  when it was installing, it asked me if i wanted to change a "menu", or keep the current one.  I said to change it (stupid, i know).
after the installation was complete, i have a few problems that i have NO idea how to fix.  i've searched all over the internet, but nothing has worked so far.
here are the problems:

1) keyboard in ubuntu doesn't work.  i can use the onboard while logging in, but it disappears after log in and i don't know how to get it back up.  when i go into the recovery mode, i'm able to use the keyboard in the prompt, but i really don't know what to do.  i tried these solutions:
[http://ubuntuforums.org/showpost.php?p=9203674&postcount=5](http://ubuntuforums.org/showpost.php?p=9203674&postcount=5)
[http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/](http://blog.ichinmay.com/2010/05/03/ubuntu-10-04-upgrade-from-9-10-usb-keyboard-mouse-problem/)

another thing i did was edit the Xorg.0.log file
it said
"AddAutoDevices" "False"
and i changed it to "True"

nothing has made a difference.. still no keyboard!

2)  FIXED
3)  when i shutdown in the command line (while in ubuntu recovery mode), my speakers make this loud fuzz-static sound.  it's not really a big deal if it can't be fixed, but it's annoying when i'm in the library and trying to keep it down.  any way to fix this?  i haven't really done any research on this one

so, any ideas would be awesome.  i've pretty much exhausted my net-surfing abilities, and it seems like the more common solutions don't work at all for me. 
if someone needs more info, just ask me.  try to be specific if you can- like i said, i'm new to this stuff :wink:  
thanks in advance!

EDIT: Fixed everything

---

### Post by oldfred on 2010-11-20
Sometimes keyboard & mouse are BIOS related. Check BIOS settings for USB or PS/2 settings and the type of connections you use. My USB keyboard & mouse would not work in Grub but did in Windows & Ubuntu until I changed BIOS settings.

Run this to see what is installed where:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by beasdd on 2010-12-03
thanks for the reply.  i fixed the boot menu, but not the other two problems.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   381,158,189   381,158,127   7 HPFS/NTFS
/dev/sda2         381,158,190   412,613,459    31,455,270  83 Linux
/dev/sda3         412,614,656   465,045,503    52,430,848   f W95 Ext d (LBA)
/dev/sda5         412,616,704   465,045,503    52,428,800   7 HPFS/NTFS
/dev/sda4         465,045,504   488,390,655    23,345,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5D5AFA9978E89F55                       ntfs                                     
/dev/sda2        08ea5089-d0a1-4441-9e33-672944e35bbf   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        5E18BC5318BC2C41                       ntfs       HP_RECOVERY                   
/dev/sda5        4AAA6B9BAA6B81F5                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,relatime,errors=remount-ro)


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
# kopt=root=UUID=08ea5089-d0a1-4441-9e33-672944e35bbf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=08ea5089-d0a1-4441-9e33-672944e35bbf

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

title        linux        
uuid        08ea5089-d0a1-4441-9e33-672944e35bbf
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=08ea5089-d0a1-4441-9e33-672944e35bbf ro quiet splash 
initrd        /boot/initrd.img-2.6.32-21-generic
quiet

title        broken linux
uuid        08ea5089-d0a1-4441-9e33-672944e35bbf
kernel        /boot/vmlinuz-2.6.32-21-generic root=UUID=08ea5089-d0a1-4441-9e33-672944e35bbf ro  single
initrd        /boot/initrd.img-2.6.32-21-generic


title        memtest    
uuid        08ea5089-d0a1-4441-9e33-672944e35bbf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title        windows     
root        (hd0,0)

makeactive
chainloader +1
    
title        windows repair    
rootnoverify    (hd0,3)
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
UUID=08ea5089-d0a1-4441-9e33-672944e35bbf /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 196.8GB: boot/grub/menu.lst
 196.8GB: boot/grub/stage2
 196.8GB: boot/initrd.img-2.6.28-11-generic
 196.8GB: boot/initrd.img-2.6.28-15-generic
 196.8GB: boot/initrd.img-2.6.28-19-generic
 196.7GB: boot/initrd.img-2.6.32-21-generic
 196.8GB: boot/vmlinuz-2.6.28-11-generic
 196.8GB: boot/vmlinuz-2.6.28-15-generic
 196.8GB: boot/vmlinuz-2.6.28-19-generic
 196.7GB: boot/vmlinuz-2.6.32-21-generic
 196.7GB: initrd.img
 196.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb 


```

does this give any hints to what the problem might be?

---

### Post by oldfred on 2010-12-03
I see you added a windows entry in the grub menu. I thought for win7 rootnoverify worked or worked better.

You still are using grub legacy which should work. Are you able to boot to a command line in recovery mode.

If so you can try booting to a gui with 
startx

You can also run updates that may fix some things. All lines with # are comments and if on same line only before the # is the command.
#houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by endotherm on 2010-12-03
in terms of keyboard and mouse, they work in the terminal and gdm, but not after logging onto a desktop, right?
that means it works fine with X, but not with gnome. the answer would usually be to go to System -> Preferences -> Keyboard and reapply the correct layout for your keyboard, but you can't do that can you?

as for xorg.0.log, it is a log of your last boot up, so it;s a good resource, but editing it will not do anything. if you wish to edit the xorg configuration, in the cli, enter this:
```
sudo nano /etc/X11/xorg.conf
```
when you wish to save, just use ctrl X, and it will ask you if and where to save. but keep in mind, your xconfig does not look to be the problem, since it works in gdm. 

if you want, rename ~/.gconf and login to gdm to see if there is any improvement. if not, delete the new ~/.gconf (it gets generated on login if not present) and rename your old one back to .gconf.

---

### Post by beasdd on 2010-12-09
thanks for responding
> **oldfred said:**
> I see you added a windows entry in the grub menu. I thought for win7 rootnoverify worked or worked better.

You still are using grub legacy which should work. Are you able to boot to a command line in recovery mode.

If so you can try booting to a gui with 
startx

You can also run updates that may fix some things. All lines with # are comments and if on same line only before the # is the command.
#houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
(code stuff)
sudo dpkg --configure -a

oldfred,
I can boot to the command line in recovery mode.  i tried using startx, and the gui started fine - but still no keyboard once in that mode.  i also tried adding all those updates, but the keyboard still isn't working.  i think when i tried to do "sudo apt-get update" it gave me a few errors.  i can't remember what they were, but i could write them down if that helps figure this out.

> **endotherm said:**
> in terms of keyboard and mouse, they work in  the terminal and gdm, but not after logging onto a desktop, right?
that means it works fine with X, but not with gnome. the answer would  usually be to go to System -> Preferences -> Keyboard and reapply  the correct layout for your keyboard, but you can't do that can you?

as for xorg.0.log, it is a log of your last boot up, so it;s a good  resource, but editing it will not do anything. if you wish to edit the  xorg configuration, in the cli, enter this:
```
sudo nano /etc/X11/xorg.conf
```when you wish to save, just use  ctrl X, and it will ask you if and where to save. but keep in mind,  your xconfig does not look to be the problem, since it works in gdm. 


hi endotherm.  to clarify, i found a fix for the mouse problem before downloading 10.04  but yea, the keyboard works everywhere except for gnome.  i can use the linux recovery to boot to command line, and the keyboard works there, so that's how i've been trying to fix these problems.  because the mouse works, would it be possible for me to fix it through System -> Preferences -> Keyboard, or would I also need the keyboard working?

So you're saying I shouldn't have to edit the xconfig?  

I'm kind of confused about this part...
> if you want, rename ~/.gconf and login to gdm to see if there is any  improvement. if not, delete the new ~/.gconf (it gets generated on login  if not present) and rename your old one back to .gconf.do you think that renaming it would fix a problem?  or should i try to edit it somehow?  and sorry, is gdm just logging into ubuntu 
haha, i feel like this stuff is just way over my head. :confused: lol though there is only one way to learn...

EDIT: Ok so i booted into the linux recovery and tried "boot failsafe with low graphics" or something like that.  the keyboard is working when i do this? but before it loads it gives me the error message:
[QUOTE=computer]
Ubuntu is running in low-graphics mode
The Following error was encountered.  You may need to update your configuration to solve this.
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching 'kbd'
[/QUOTE]
The keyboard is completely working in this mode, though.  and it seems pretty much exactly like ubuntu.  this is a good temporary fix, but is there anything i can do now that i have access to keyboard in the gui?

---

### Post by oldfred on 2010-12-09
I have not actually edited xorg for years, but your issues sound like an xorg issue.

The low graphics mode is probably using the xorg failsafe version and the version you edited has some minor editing issue. Not sure but it may be better to start over with a new xorg?

What video card do you have?

If able to boot to recovery mode & netroot
list of recommended drivers
jockey-text -l
Install a driver
sudo jockey-text -e <driver>

To see video:
sudo lshw | grep -A 11 display
Reconfigure graphics
sudo dpkg-reconfigure -phigh xserver-xorg
copy failsafe to xorg to use vesa as default - low graphics?
sudo mv /etc/X11/xorg.conf.failsafe /etc/X11/xorg.conf

---

### Post by beasdd on 2010-12-09
ahh, I fixed it!  what i ended up doing was going into the xorg.conf file and simply changing the "AddAutoDevices" "False" to "True", then saving over the original.  i'm surprised it worked so easily, but it seems that did the trick.  it's funny how there can be one common problem on an OS, yet each might require a different solution.  Thanks for the help everyone!

---

