---
title: "grub help, moving to tri boot (winXP. ubuntu, fedora soemething)"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2011-03-20
I have tried this in the past, but I have always list the ability to boot the the first two OSs installed. I currently have XP (installed first on an ssd), ubuntu 10.04 (installed second on the first partition of a platter drive), and I want to add either cent or SL (both fedora) on the second partition of the platter drive. I will probably also want to install win7 on the third partition. In previous attempts, this was on a linux box where it didn't really matter if I lost the OS or not. They were more or less temporary installs just for testing. This time, I am installing on my main devel box, and it would be quite a bore to mess it up. I have images and such, but I would really rather not spend half a day fixing everything.

I need a procedure to allow me to add additional OSs without risking not being able to boot. I have tried supergrub in the past, but it was not able to repair the boot setup and I couldn't get back into the other systems I had installed.

I am still baffled that grub isn't installed after the fact. There should be an easy way to load a live linux cd that will scan the drives for bootable partitions and then ask you how you want grub setup. Having every OS have it's own version of grub that it tries to install over the other versions is just a bad idea.

If I install CentOS, should I not install grub, and then boot into ubuntu and try to add cent to the grub.conf? I am not sure how grub2 works, since it looks like you can't edit grub.conf anymore. What if cent doesn't have the option to not install grub.

The ubuntu boot loader (grub2) is in charge at the moment.

Thanks for the advice,

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-20
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

People can say what they want, the offical site says it rather well.

---

### Post by LMHmedchem on 2011-03-20
> **Hakunka-Matata said:**
> [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

People can say what they want, the official site says it rather well.Thanks for the link.

It seems odd that the preferred method is to break the MBR and the fix it. Aren't we to the point yet where an installer can look at the existing grub setup and then just add something to it, or ask the user if they want grub installed with the new OS, and then bring over information from the current grub.conf? Some Linux distros have features like this, or at least that look like what I need, but I have never been able to get them to work. It may be that I am not selecting the right options, but it doesn't help that the explanations are so cryptic.

How can I best avoid having to repair things after the fact? I assume that I should not install grub with the new OS. How do I add the new OS to the existing grub if I don't install it with the new OS, or if I have to re-install grub in Ubuntu?

PG is a great tea, by the way.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-20
Since Release 9.10 Grub is Grub2, or Grub 1.98, 1.99 etc. and it's a very different sort of animal.  Do a search on Grub2 in the forums now and wow.  I've been following Forum Members 'oldfred, drs305, srs5694, Frogs Hair, kansasnoob and a few others who are very knowledgeable, learned heaps from them. you'll be educated and convinced of the wisdom of using Grub for your bootloader very quickly.  It updates new drives and OSes very quickly and *automatically *now.  There is no more Menu.lst.

[http://ubuntuforums.org/showthread.php?t=1694750](http://ubuntuforums.org/showthread.php?t=1694750) thread is a very good education.  And [http://ubuntuforums.org/showthread.php?t=1689533](http://ubuntuforums.org/showthread.php?t=1689533) this one is a famous, make that infamous thread, marathon, every base gets covered over and over, it's a famous thread in Grub land.  

If you want to understand it and approach your configuration surgically, first download and run the boot_info_script script in my signature.  and study the Results.txt file it produces.  I'll help when and if you want to get all your OSes and drives booting swell.

---

### Post by LMHmedchem on 2011-03-20
> **Hakunka-Matata said:**
> Since Release 9.10 Grub is Grub2, or Grub 1.98, 1.99 etc. and it's a very different sort of animal.  Do a search on Grub2 in the forums now and wow.  I've been following Forum Members 'oldfred, drs305, srs5694, Frogs Hair, kansasnoob and a few others who are very knowledgeable, learned heaps from them. you'll be educated and convinced of the wisdom of using Grub for your bootloader very quickly.  It updates new drives and OSes very quickly and *automatically *now.  There is no more Menu.lst.

[http://ubuntuforums.org/showthread.php?t=1694750](http://ubuntuforums.org/showthread.php?t=1694750) thread is a very good education.  And [http://ubuntuforums.org/showthread.php?t=1689533](http://ubuntuforums.org/showthread.php?t=1689533) this one is a famous, make that infamous thread, marathon, every base gets covered over and over, it's a famous thread in Grub land.  

If you want to understand it and approach your configuration surgically, first download and run the boot_info_script script in my signature.  and study the Results.txt file it produces.  I'll help when and if you want to get all your OSes and drives booting swell.Is this a script that I have to run from linux, or can I run it in cygwin bash?

I guess I have some more reading to do. It really seems like this should be a very straightforward process and I suspect that some of the complexity arises from different distros not being in a bit hurry to make it easy to use someone else's flavor, which is a bit disappointing.

Thanks again for the help, I'm sure there will be some additional questions when I get going. I'm in the process of downloading the 8CDs worth of isos for Cent.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-20
If it does not have grub2 and uses grub-legacy like fedora, CentOS and other red hat cousins that
use anaconda as an installer there is an option to not install any grub. Use it then boot into your grub2 install and update-grub. 
OS Prober in grub2 will find the other installs and include them in grub-config and make a menu entry and all is well. 
 If you do install grub-legacy it will have to be purged in live-cd from install and then grub2 from install of choice reinstalled in mbr 
and grub updated. So much easier just not installing legacy at all. 
 When windows installed after Ubuntu will overwrite grub in mbr and grub2 must be reinstalled through Live CD. 
 Always use same architecture of live cd (32 or 64 bit) should not be a problem some good 
links out there on using chroot and purging and reinstalling with or with out internet connection. Here is a couple that are popular.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Hakunka-Matata on 2011-03-20
bootinfoscript is run from a linux terminal, I mean we are in an Ubuntu forum.  That being said,
> Cygwin is: 

[LIST]
[*]a collection of tools which provide a Linux look and feel environment for Windows.
[*]a DLL (cygwin1.dll) which acts as a Linux API layer providing substantial Linux API functionality.
[/LIST]


Maybe it will run from Cygwin, I don't know.

---

### Post by LMHmedchem on 2011-03-21
> **Hakunka-Matata said:**
> bootinfoscript is run from a linux terminal, I mean we are in an Ubuntu forum.  That being said,

Maybe it will run from Cygwin, I don't know.
It doesn't run from cygwin, there are some packages missing. It is possible that I could find the missing packages in the manager and get it working, but I will just run it from linux for now.

I decided to try on another linux box to make sure the process was good. The box had ubuntu 9, and SL 5.2, but grub was only showing ubunut. I though I would try upgrading grub to grub2 and doing grub-update to see if I could get back into SL.

I ran the boot script, and it gave odd results. It shows one of my drives with several partitions of unknown format. If I remember right, this was a shared data drive. I am not able to mount sda, and I don't know if I am using the right syntax. The drive shows in the MOBO bios, but I really can't tell if it's still working.

I tried to upgrade to grub2 using aptitude install grub-pc, according to,

[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

This got to a screen that was telling me to select the chainload option, but there was no way to get out of the screen. There was an <OK> at the bottom, but I couldn't click on it, and keying enter did nothing. I ended up having to just close the terminal. I got a notification that the install had failed. Then I went to the package manager, and grub2 was listed as installed, so I marked it for reinstall. The reinstall seemed to go fine. There was a screen with a check box to use the chainload option, and a text field called linux command line. The instructions said to add "ENTER" to the linux command line text field, so I did that, and the install seemed to finish. I rebooted and the chainload appeared to work and I got back into ubuntu. The timeout was way too short, so I never really saw the menu. I did update-from-grub-legacy once back into ubuntu. It asked which drive to select and I selected sdb, which is where ubuntu is installed. When re-booting, I now get error 15 and am stuck. I don't know if the legacy grub was on sda1, but I don't see how since the only thing that will boot is ubuntu on sdb. I presume that means that grub legacy was installed on the MBR of sdb.

I attempted to fix with these instructions,

[http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu](http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu)

using a 10.04 live CD. When I get to dpkg-reconfigure grub-pc, I get the message dpkg-reconfigure, command not found.

So I am stuck without a way to boot at the moment. I ran the boot script again from the live cd and the results are posted below.

Any suggestions as to what to try next. I am tempted to just unplug sda until I have the rest fixed.

[COLOR=Navy]**LMHmedchem**[/COLOR]

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    230814820 on boot drive #2 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #3 for 
    /boot/grub/grub.conf.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.2 
                       (Boron) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sdb2           3,903,795   203,125,859   199,222,065   5 Extended
/dev/sdb5           3,903,858     7,807,589     3,903,732  82 Linux swap / Solaris
/dev/sdb6           7,807,653   105,466,724    97,659,072  83 Linux
/dev/sdb7         105,466,788   203,125,859    97,659,072  83 Linux
/dev/sdb3    *    203,125,860   254,325,014    51,199,155  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,897,087     7,897,025   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3f736a8c-8942-40da-9954-426b41c15a36   ext3       Data_Volume                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4972f29f-10ce-495f-95b2-b09358c28a08   swap                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb3        cd7875ae-8dfd-4e04-b32f-589f850118d2   ext3       SciLinux                      
/dev/sdb5        2fd034d1-ebb2-4840-b188-67d19db97fd2   swap                                     
/dev/sdb6        d30ec437-c8f4-4ee7-93c6-ddf90369de41   ext3                                     
/dev/sdb7        24b127c5-831e-44ec-9499-f9b957d879f0   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B8AF-9064                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb3        /mnt                     ext3       (rw)
/dev             /mnt/dev                 none       (rw,bind)
/dev/sdc1        /media/B8AF-9064         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
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
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-19-generic
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
menuentry "Scientific Linux SL (2.6.18-194.17.1.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
}
menuentry "ScientificLinux (2.6.18-92.1.6.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sdb6/boot/grub/grub.conf: ==========================

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
# hiddenmenu

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=4972f29f-10ce-495f-95b2-b09358c28a08 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2fd034d1-ebb2-4840-b188-67d19db97fd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## added to mount usb as rw
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

  /dev/sda1 /media/Data_Volume/ ext3 defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


  50.0GB: boot/grub/core.img
  49.9GB: boot/grub/grub.cfg
  50.0GB: boot/grub/grub.conf
  49.9GB: boot/grub/menu.lst
  49.9GB: boot/initrd.img-2.6.31-19-generic
  49.9GB: boot/initrd.img-2.6.31-20-generic
  50.0GB: boot/initrd.img-2.6.31-23-generic
  49.9GB: boot/vmlinuz-2.6.31-19-generic
  49.9GB: boot/vmlinuz-2.6.31-20-generic
  49.9GB: boot/vmlinuz-2.6.31-23-generic
  50.0GB: initrd.img
  49.9GB: initrd.img.old
  49.9GB: vmlinuz
  49.9GB: vmlinuz.old

========================== sdb3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd1,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Scientific Linux SL (2.6.18-194.17.1.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
title ScientificLinux (2.6.18-92.1.6.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img

#title        Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
#kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro #quiet splash 
#initrd        /boot/initrd.img-2.6.28-13-generic
#quiet

=============================== sdb3/etc/fstab: ===============================

LABEL=SciLinux          /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sdb3: Location of files loaded by Grub: ===================


 118.1GB: boot/grub/grub.conf
 118.1GB: boot/grub/menu.lst
 118.1GB: boot/grub/stage2
 118.2GB: boot/initrd-2.6.18-194.17.1.el5.img
 118.1GB: boot/initrd-2.6.18-194.17.1.el5kdump.img
 118.2GB: boot/initrd-2.6.18-92.1.6.el5.img
 118.1GB: boot/initrd-2.6.18-92.1.6.el5kdump.img
 118.1GB: boot/vmlinuz-2.6.18-194.17.1.el5
 118.1GB: boot/vmlinuz-2.6.18-92.1.6.el5

```

---

### Post by LMHmedchem on 2011-03-21
I successfully used supergrub2 to boot back into ubuntu. Now that I have an OS back up, what do I need to fix grub?
[B][COLOR=Navy]
LMHmedchem[/COLOR][/B]

---

### Post by Hakunka-Matata on 2011-03-21
See Hyperlink in post #2

---

### Post by garvinrick4 on 2011-03-21
Have nothing is sda drive at all:
Have 2 installs in sdb will put grub2 in mbr and purge grub-legacy
```
With Live CD remove grub from sdb3
#use whatever Scientific linux SL uses to mount and get into root
and remove grub grub-common grub-pc and do not reinstall:
*This is an example below: (get into the root of sdb3 and remove grub grub-common grub-pc is the idea)
Never used Scientific linux SL
  [code]sudo mount /dev/sdb3 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```  ```
yum remove grub grub-common grub-pc
``` ```
exit
```                                ```
 sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```above use whatever, replace yum with
whatever it uses zypper, yum, something else I do not know.
or if the linux is configured for sudo. (The jest is to remove grub grub-common grub-pc from sdb3)
#get out of root and continue on to sdb6
*Do not reinstall any grub at all in sdb3.[/CODE]Use Live Cd with internet connection
Remove all both grubs from sdb6 and reinstall grub2 (grub-pc)
```
Mount sdb6 into root:
                              [CODE]sudo mount /dev/sdb6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
apt-get purge grub grub-common grub-pc
``````
apt-get update
``````
apt-get install grub-common grub-pc
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```Should be good to go: Have grub2 in sdb6 Ubuntu and in mbr and none in sdb3 Scientific. 
Will now boot both installs from grub2.

  
 [/CODE]

---

### Post by LMHmedchem on 2011-03-21
> **Hakunka-Matata said:**
> See Hyperlink in post #2I re-installed grub2 from the package manager after doing a complete uninstall. I can not boot into either ubuntu or SL, so that is somewhat better.

I tried to install Cent5 to freespace on sdb. I did custom layout and set up a 20GB partition for the install. I also tried to set up a 2GB swap partition, but it said I didn't have enough space. There are 150GB of free space after the root partition was created, so I'm not sure what it thinks the issue is. I also tried the option to let it create the default layout in the free space, but that also fails. I tried without a swap partition and there was an untrapped exception and the installer failed.

Looking at this partition information for sdb (after grub update),
```

/dev/sdb1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sdb2           3,903,795   203,125,859   199,222,065   5 Extended
/dev/sdb5           3,903,858     7,807,589     3,903,732  82 Linux swap / Solaris
/dev/sdb6           7,807,653   105,466,724    97,659,072  83 Linux
/dev/sdb7         105,466,788   203,125,859    97,659,072  83 Linux
/dev/sdb3    *    203,125,860   254,325,014    51,199,155  83 Linux

```This really looks like quite a mess. I believe that ubuntu is on sdb6, and that SL is on sdb3. There appear to be quite a few unused partitions. How can I mount these and see if there is anything in them? This setup looks like quite a mess. I would expect to see a swap and root partition for each install. How can I best re-configure all of this so that it makes more sense and I am able to install a third OS?

If absolutely necessary, I can image the installed OS, copy the data out of the other partitions (if there is any), use gparted to create a reasonable partitioning scheme for sdb, and then copy back the current OSs from the images. I don't know if that is easier than trying to clean up the partitions from inside ubuntu.

What should the disk partitioning look like if I am going to have 3 or 4 OSs installed?

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by garvinrick4 on 2011-03-21
You can have 4 primary's and extended houses all logicals which you can have all you want, linux can exist in logical as well as primary. Extended counts as a primary.
example:

---

### Post by LMHmedchem on 2011-03-21
> **garvinrick4 said:**
> You can have 4 primary's and extended houses all logicals which you can have all you want, linux can exist in logical as well as primary. Extended counts as a primary.
example:I don't quite understand why Cent won't let me partition the freespace. I am back in the installer. It appears that sdb7 is an empty partition of 50GB. I deleted sdfb7 and added a 2GB swap in the resulting freespace. The partition appears as sdb4, which looks like a primary partition. If I then add a partition for the OS, it appears as sdb7, which is an extension of sdb2. Is there some reason why it defaults to sdb4 for the swap, but not for root? It doesn't matter which partition I add first, the swap always ends up as sdb4 and root as sdb7.

It seems I should have one primary partition that makes up the entire drive, and then use logical extended partitions for the OSs. Does the swap need to be in a primary partition? That would explain why sdb1 is a primary swap. Is it necessary to add a swap partition for every install, I seem to remember that different distros can share the swap.

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by garvinrick4 on 2011-03-21
Take screenshot of gparted and post here. Use paperclip icon on top of your message box.
If you do not have gparted installed:
```
sudo apt-get install gparted
```

---

### Post by LMHmedchem on 2011-03-21
> **garvinrick4 said:**
> Take screenshot of gparted and post here. Use paperclip icon on top of your message box.
If you do not have gparted installed:
```
sudo apt-get install gparted
```I will upload the gparted screenshot in a few minutes. 

I have installed CentOS 5.5 to sdb7, with sdb4 as swap. I did not install grub with Cent. I booted back into ubuntu and did update-grub, but I am getting a command not found message. Do I still not have grub2 installed after uninstalling and re-installing it again?

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by LMHmedchem on 2011-03-21
> **LMHmedchem said:**
> ... and did **[COLOR=Red]update-grub[/COLOR]**

I guess it would work better if I did sudo grub-update???

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-21
LMH, look @ post #13, he's telling you the reason.   But I'll say it here as well:

The **size** of your sdb7 is 50GB, but that picture tells you nothing about how much of it is used, only the size of the partition.


[COLOR=Red]**Sorry, the below details are according to the Thumbnail in post #13, garvinrick4's drive I guess**[/COLOR] that is.  But you understand by looking at it.

[LIST]
[*]You are allowed a MAXIMUM of 4 primary partitions.  In GParted's GUI, Primary partitions are not indented, Logicals are indented.
[*]Windows requires a primary partition.
[*]Linux can be installed to a Logical partition.
[*]Logical partitions are contained in an Extended partition, you can have many Logicals in one Extended.
[*]Swap is fine in a Logical partition.
[*]you only need one Swap partition, it can be on any drive, the active OS will find it.
[*]all your unallocated space totals approximately ~14.29 **MiB**
[*]if you want to change swap partition but it is mounted/in use, key Icon, right click it, and click 'swapoff', turn it back on same way.
[/LIST]

---

### Post by Hakunka-Matata on 2011-03-21
> **LMHmedchem said:**
> 

This got to a screen that was telling me to select the chainload option, but there was no way to get out of the screen. There was an <OK> at the bottom, but I [COLOR=Red]couldn't click on it, and keying enter did nothing[/COLOR]. I ended up having to just close the terminal. I got a notification that the install had failed. 

Use the **TAB **key

---

### Post by LMHmedchem on 2011-03-21
> **garvinrick4 said:**
> Take screenshot of gparted and post here. Use paperclip icon on top of your message box.
If you do not have gparted installed:
```
sudo apt-get install gparted
```Here is the gparted screenshot.
[ATTACH]186759[/ATTACH]

I believe that it is working now, grub-update found the cent install, so now I need to reboot and make sure I can get in.

I think you can see from the gparted capture that the partitioning is a bit of a mess, even if it is currently working. I guess what I needed to do was to create an extended partition with all of the remaining freespace, and then create root and swap there as logical partitions. It seems like anaconda tried to create both root and swap as primary partitions.

It probably makes sense to re-do this with something like a single extended partition with a bunch of logical partitions along the order of the capture garvinrick4 posted. Is there any advantage in having the swap in a primary partition, even though it can be in a logical?

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by LMHmedchem on 2011-03-21
I rebooted, and cent appears in the grub menu. When I select it, I get an error message, 

VFS: Cannot open root device "sdb7" or unknown-block(0,0)
Please append a correct "root=" boot option

I definitely specified the partition sdb7 as / in anaconda, so I'm not sure what the problem is now. Grub2 identified it as an operating system and added it to the menu. I will run the boot script again and post the results.

[COLOR=Navy][B]LMHmedchem
[/B]
[COLOR=Black]Here is the new results file,
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    230814820 on boot drive #2 for the stage2 file. A stage2 file is at this 
    location on /dev/sdb. Stage2 looks on partition #3 for /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.2 
                       (Boron) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004d20d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,704   312,576,642  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cdeb

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sdb2           3,903,795   203,125,859   199,222,065   5 Extended
/dev/sdb5           3,903,858     7,807,589     3,903,732  82 Linux swap / Solaris
/dev/sdb6           7,807,653   105,466,724    97,659,072  83 Linux
/dev/sdb7         105,466,788   166,899,284    61,432,497  83 Linux
/dev/sdb3    *    203,125,860   254,325,014    51,199,155  83 Linux
/dev/sdb4         254,325,015   262,518,164     8,193,150  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3f736a8c-8942-40da-9954-426b41c15a36   ext3       Data_Volume                   
/dev/sdb1        4972f29f-10ce-495f-95b2-b09358c28a08   swap                                     
/dev/sdb3        cd7875ae-8dfd-4e04-b32f-589f850118d2   ext3       SciLinux                      
/dev/sdb4                                               swap       SWAP-sdb4                     
/dev/sdb5        2fd034d1-ebb2-4840-b188-67d19db97fd2   swap                                     
/dev/sdb6        d30ec437-c8f4-4ee7-93c6-ddf90369de41   ext3                                     
/dev/sdb7        90cecb53-19e2-4605-b35a-74a27570a1d3   ext3       /                             

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro ENTER  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single ENTER
    initrd    /boot/initrd.img-2.6.31-19-generic
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
menuentry "Scientific Linux SL (2.6.18-194.17.1.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
}
menuentry "ScientificLinux (2.6.18-92.1.6.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 90cecb53-19e2-4605-b35a-74a27570a1d3
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sdb6/boot/grub/grub.conf: ==========================

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
# hiddenmenu

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=4972f29f-10ce-495f-95b2-b09358c28a08 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2fd034d1-ebb2-4840-b188-67d19db97fd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## added to mount usb as rw
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

  /dev/sda1 /media/Data_Volume/ ext3 defaults 0 0

=================== sdb6: Location of files loaded by Grub: ===================


  49.9GB: boot/grub/core.img
  49.9GB: boot/grub/grub.cfg
  50.0GB: boot/grub/grub.conf
  50.0GB: boot/grub/menu.lst
  49.9GB: boot/initrd.img-2.6.31-19-generic
  49.9GB: boot/initrd.img-2.6.31-20-generic
  50.0GB: boot/initrd.img-2.6.31-23-generic
  49.9GB: boot/vmlinuz-2.6.31-19-generic
  49.9GB: boot/vmlinuz-2.6.31-20-generic
  49.9GB: boot/vmlinuz-2.6.31-23-generic
  50.0GB: initrd.img
  49.9GB: initrd.img.old
  49.9GB: vmlinuz
  49.9GB: vmlinuz.old

=============================== sdb7/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0
LABEL=SWAP-sdb4         swap                    swap    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0

=================== sdb7: Location of files loaded by Grub: ===================


  56.1GB: boot/initrd-2.6.18-194.el5.img
  56.0GB: boot/vmlinuz-2.6.18-194.el5

========================== sdb3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd1,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Scientific Linux SL (2.6.18-194.17.1.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
title ScientificLinux (2.6.18-92.1.6.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img

#title        Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
#kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro #quiet splash 
#initrd        /boot/initrd.img-2.6.28-13-generic
#quiet

=============================== sdb3/etc/fstab: ===============================

LABEL=SciLinux          /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sdb3: Location of files loaded by Grub: ===================


 118.1GB: boot/grub/grub.conf
 118.1GB: boot/grub/menu.lst
 118.1GB: boot/grub/stage2
 118.2GB: boot/initrd-2.6.18-194.17.1.el5.img
 118.1GB: boot/initrd-2.6.18-194.17.1.el5kdump.img
 118.2GB: boot/initrd-2.6.18-92.1.6.el5.img
 118.1GB: boot/initrd-2.6.18-92.1.6.el5kdump.img
 118.1GB: boot/vmlinuz-2.6.18-194.17.1.el5
 118.1GB: boot/vmlinuz-2.6.18-92.1.6.el5
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  00 78 30 30 00 78 30 30  00 78 30 30 00 78 30 30  |.x00.x00.x00.x00|
*
00000200


```[/COLOR][/COLOR]

---

### Post by garvinrick4 on 2011-03-21
> **LMHmedchem said:**
> Here is the gparted screenshot.
[ATTACH]186759[/ATTACH]

I believe that it is working now, grub-update found the cent install, so now I need to reboot and make sure I can get in.

I think you can see from the gparted capture that the partitioning is a bit of a mess, even if it is currently working. I guess what I needed to do was to create an extended partition with all of the remaining freespace, and then create root and swap there as logical partitions. It seems like anaconda tried to create both root and swap as primary partitions.

It probably makes sense to re-do this with something like a single extended partition with a bunch of logical partitions along the order of the capture garvinrick4 posted. Is there any advantage in having the swap in a primary partition, even though it can be in a logical?

[COLOR=Navy]**LMHmedchem**[/COLOR] No you can get rid of sda4 swap and use the unallocated space in future. Swap sda4 is using last primary. Is messy and when you get the inclination you can redo your drive after backing up all your personals. If she works and is booting
into all your installs use like it is until you want to straiten her up. Enjoy your ubuntu.

---

### Post by Hakunka-Matata on 2011-03-21
You can delete both sda1 SWAP and sda4 SWAP.  Those two are primary partitions as well.  So get rid of them and leave the SWAP partition sdb5. sdb5 is an extended partition, so it's not eating up one of your 4 alloted primary partitions.  Good job.

---

### Post by LMHmedchem on 2011-03-21
I edited my last post in that cent isn't booting. 


> **LMHmedchem said:**
> I rebooted, and cent appears in the grub menu. When I select it, I get an error message, 

VFS: Cannot open root device "sdb7" or unknown-block(0,0)
Please append a correct "root=" boot option

I definitely specified the partition sdb7 as / in anaconda, so I'm not sure what the problem is now. Grub2 identified it as an operating system and added it to the menu. I will run the boot script again and post the results.


I also just updated the results file in post 21 after having posted the wrong one first. Can I just delete sda4 from gparted? I assume that the other OSs will find one of the existing swap partitions, is that right?

It seems I am close, but it looks like I need to tweak something to get cent to boot, even though it is in the grub menu. If I just add a boot flag to sda7 in gparted, will that fix things?

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-21
Linux doesn't pay any attention to boot flags, only Windows.  But then I don't know Cent either.  Cent told  you why it wasn't happy, but let me say something else at this point.

yes, you can delete the Swap sda4 using GParted.

you are mixing legacy Grub and Grub 2.  That might get confusing.

> [COLOR=Navy][COLOR=Black]post #21
============================= Boot Info Summary: ==============================   => 

Grub 0.97 is installed in the MBR of /dev/sda and looks at sector      230814820 on boot drive #2 for the stage2 file. A stage2 file is at this      location on /dev/sdb. 
Stage2 looks on partition #3 for /boot/grub/menu.lst.  =>
 Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in      partition #6 for /boot/grub.[/COLOR][/COLOR][COLOR=Navy][COLOR=Black]

Grub 0.97 is Legacy Grub

Grub 2 is the new and preferred Grub.  You could purge Grub from the MBR of sda and install Grub 2 there.  Then do the update-grub thing and be cleaned up better.
[/COLOR][/COLOR]

---

### Post by LMHmedchem on 2011-03-21
I'm not sure why there is still an old grub there. I tried to do uninstall grub legacy, but I also got a command not found. Maybe I typed that in wrong too.

Are the instructions to uninstall legacy grub and re-install grub2 to the MBR in the link you posted in post 2? I also think that is the way to go, and what I thought I was doing. I must have missed a step somewhere. The drive sda is suddenly working, and it is a data drive like I thought, but it did used to have  OSs installed on it. So it looks like sda is where the legacy grub is hiding?

What would be the best method for getting the old grub off of sda? How do I insure that grub2 goes to the MBR of sdb? I don't remember any options for where it is supposed to install.

I guess I'm getting closer, I'm going out for a bit now and will be back later.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-21
> **LMHmedchem said:**
> I'm not sure why there is still an old grub there. I tried to do uninstall grub legacy, but I also got a command not found. Maybe I typed that in wrong too.

Are the instructions to uninstall legacy grub and re-install grub2 to the MBR in the link you posted in post 2? I also think that is the way to go, and what I thought I was doing. I must have missed a step somewhere. The drive sda is suddenly working, and it is a data drive like I thought, but it did used to have  OSs installed on it. So it looks like sda is where the legacy grub is hiding?

What would be the best method for getting the old grub off of sda? How do I insure that grub2 goes to the MBR of sdb? I don't remember any options for where it is supposed to install.

I guess I'm getting closer, I'm going out for a bit now and will be back later.

[COLOR=Navy]**LMHmedchem**[/COLOR]
Grub installs to the MBR of a drive, like to the MBR of sda, or sdb.  Don't try to install it to a partition.

There is a forum member (oldfred) that is super with Grub.  Use the search function on the main page and designate Search by "Find posts by User".  Click on Search and select Advanced Search.  put 'oldfred' in the User box, and Grub in the Keyword box.  You'll get a extra super shot of hits.  Read some of his posts, it'll be clear as mud in nothing flat.

Time for food - Good luck, it's really fun to see people learn and advance, and achieve results, thanks.

---

### Post by garvinrick4 on 2011-03-21
Hi if you do a post and use a new boot script do not put it in an old post make a new one.
We cannot see what the old bootscript looked like now.

**First remove all forms of grub from sdb3** (A must)
I do not know commands for Scientific linux

#Below is for Ubuntu install: EDIT: you unplugged sda so now have changed to your new script sda instead of sdb
Purge and reinstall grub from sdb6 removing the grub-legacy:
#Use live cd and get the internet connection going.
                          ```
sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
apt-get purge grub grub-common grub-pc
``````
apt-get update

``````
apt-get install grub-common grub-pc
``````
update-grub
``````
exit
```                           ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
```

---

### Post by LMHmedchem on 2011-03-22
I have un-installed grub from inside SL, but there are still grub conf files in /boot/grub on sda3. I found a link that says that something like this can remove conf files for a package.
```
for package in package1 package2 package3
do
  echo "removing config files for $package"
  for file in $(rpm -q --configfiles $package)
  do
    echo "  removing $file"
    rm -f $file
  done
  rpm -e $package
done
```Should I try to remove the conf files with something like this, or should I just manually delete the files. The boot script references a stage 2 file on the MBR of sda. If I remove legacy grub, will this file be removed as well? I don't see any changes in the results file after uninstalling grub from SL, so I don't know if that did anything or not.

> **Hakunka-Matata said:**
> There is a forum member (oldfred) that is super with Grub. Use the search function on the main page and designate Search by "Find posts by User". Click on Search and select Advanced Search. put 'oldfred' in the User box, and Grub in the Keyword box. You'll get a extra super shot of hits. Read some of his posts, it'll be clear as mud in nothing flat.

Time for food - Good luck, it's really fun to see people learn and advance, and achieve results, thanks.I will look for some of these posts. It is satisfying to learn these systems in greater detail, even though it can be slow at times.

The boot script doesn't work in scientific linux (redhat 5.1.19.6) in case you didn't know that. It is missing the same dependencies as cygwin.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-22
Red hat: Put in ubuntu live Cd copy and paste these will remove grub files from sdb3 EDIT: Changed to sda after you have removed your sda drive as per later script.
```
sudo -i
``````
mount /dev/sda3 /mnt
``````
mount -o bind /dev /mnt/dev
``````
mount -o bind /dev/pts /mnt/dev/pts
``````
mount -o bind /proc /mnt/proc
``````
mount -o bind /sys /mnt/sys
``````
chroot /mnt
``````
yum remove grub
``````
exit
``````
umount /mnt/dev/pts
``````
umount /mnt/dev
``````
umount /mnt/proc
``````
umount /mnt/sys
``````
umount /mnt
``````
reboot
```So we haved removed grub from redhat sdb3 and purged grub grub-common grub-pc from sdb6 ubuntu and installed grub-common grub-pc in Ubuntu.
Post 30 first and then post 28 all from within a Live CD. (has to be same architecture 32 or 64 bit as install)

---

### Post by LMHmedchem on 2011-03-22
I ended up unplugging sda for now, since I can't find any way to remove grub legacy from the sda mbr. My results file now just shows grub2 on the mbr of the remaining disk.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.2 
                       (Boron) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cdeb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sda2           3,903,795   203,125,859   199,222,065   5 Extended
/dev/sda5           3,903,858     7,807,589     3,903,732  82 Linux swap / Solaris
/dev/sda6           7,807,653   105,466,724    97,659,072  83 Linux
/dev/sda7         105,466,788   166,899,284    61,432,497  83 Linux
/dev/sda3    *    203,125,860   254,325,014    51,199,155  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4972f29f-10ce-495f-95b2-b09358c28a08   swap                                     
/dev/sda3        cd7875ae-8dfd-4e04-b32f-589f850118d2   ext3       SciLinux                      
/dev/sda5        2fd034d1-ebb2-4840-b188-67d19db97fd2   swap                                     
/dev/sda6        d30ec437-c8f4-4ee7-93c6-ddf90369de41   ext3                                     
/dev/sda7        90cecb53-19e2-4605-b35a-74a27570a1d3   ext3       /                             

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
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
menuentry "Scientific Linux SL (2.6.18-194.17.1.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
}
menuentry "ScientificLinux (2.6.18-92.1.6.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 90cecb53-19e2-4605-b35a-74a27570a1d3
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sdb7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sda6/boot/grub/grub.conf: ==========================

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
# hiddenmenu

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=4972f29f-10ce-495f-95b2-b09358c28a08 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2fd034d1-ebb2-4840-b188-67d19db97fd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## added to mount usb as rw
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

  /dev/sda1 /media/Data_Volume/ ext3 defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


  49.9GB: boot/grub/core.img
  49.9GB: boot/grub/grub.cfg
  50.0GB: boot/grub/grub.conf
  49.9GB: boot/grub/menu.lst
  49.9GB: boot/initrd.img-2.6.31-19-generic
  49.9GB: boot/initrd.img-2.6.31-20-generic
  50.0GB: boot/initrd.img-2.6.31-23-generic
  49.9GB: boot/vmlinuz-2.6.31-19-generic
  49.9GB: boot/vmlinuz-2.6.31-20-generic
  49.9GB: boot/vmlinuz-2.6.31-23-generic
  50.0GB: initrd.img
  49.9GB: initrd.img.old
  49.9GB: vmlinuz
  49.9GB: vmlinuz.old

=============================== sda7/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0
LABEL=SWAP-sdb4         swap                    swap    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


  56.1GB: boot/initrd-2.6.18-194.el5.img
  56.0GB: boot/vmlinuz-2.6.18-194.el5

========================== sda3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd1,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Scientific Linux SL (2.6.18-194.17.1.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
title ScientificLinux (2.6.18-92.1.6.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img

#title        Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
#kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro #quiet splash 
#initrd        /boot/initrd.img-2.6.28-13-generic
#quiet

=============================== sda3/etc/fstab: ===============================

LABEL=SciLinux          /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sda3: Location of files loaded by Grub: ===================


 118.1GB: boot/grub/grub.conf
 118.1GB: boot/grub/menu.lst
 118.1GB: boot/grub/stage2
 118.2GB: boot/initrd-2.6.18-194.17.1.el5.img
 118.1GB: boot/initrd-2.6.18-194.17.1.el5kdump.img
 118.2GB: boot/initrd-2.6.18-92.1.6.el5.img
 118.1GB: boot/initrd-2.6.18-92.1.6.el5kdump.img
 118.1GB: boot/vmlinuz-2.6.18-194.17.1.el5
 118.1GB: boot/vmlinuz-2.6.18-92.1.6.el5

```The third primary partition, now sda3, still shows grub conf files, which I can remove manually if necessary. I can't find any other way to remove them.

After disconnecting the drive, I went through the steps in post 28 to remove grub2 and grub legacy. The shell said that grub legacy wasn't installed. Update-grub found all the OSs but that doesn't seem to get me all the way there.

I am still unable to boot into Cent, even though it shows up in the menu. I am still getting the message,

VFS: Cannot open root device "sdb7" or unknown-block(0,0)
Please append a correct "root=" boot option

Is the root= option something missing in the grub2 conf, or something else. The only thing I can see is that there is no initrd entry in the Cent section of sda6/boot/grub/grub.cfg. I can reinstall Cent, but I'm not sure what that would change, unless anaconda need you to designate a partition as boot, or something like that. I just created a root partition. I don't remember a "mark as bootable" checkbox, or anything like that.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-22
Just saw your last post of sda now instead of sdb so make those changes.
sda3 redhat
sda6 ubuntu
I will change my code to fit;

#If you ever need to use internet connection in redhat and its cousins use this
line of code before chroot command and will give you internet:
cp /etc/resolv.conf /mnt/etc/resolv.conf

---

### Post by Hakunka-Matata on 2011-03-22
@garvinrick4:


Retracted for lack of certainty

---

### Post by Hakunka-Matata on 2011-03-22
In Post #28:
```
apt-get install grub-common grub-pc
``` why the "grub-common"  I don't understand that line of code.  Is not **grub-common = grub-legacy**?  And is not **grub-pc = Grub 2**?  === EDIT : ANSWER IS NO, THOSE EQUATIONS ARE NOT CORRECT.  SEE POST #35 FROM garvinrick4.  Thanks gr4

---

### Post by garvinrick4 on 2011-03-22
Hakuna-matata here are the packages in question:

```
rick@rick-HP:~$ aptitude show grub
Package: grub                            
New: yes
State: not installed
Version: 0.97-29ubuntu61
Priority: optional
Section: admin
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 2,040 k
Depends: grub-common, udev (>= 117-5), ucf (>= 3.004-0ubuntu2), debconf (>=
         1.5.19) | cdebconf, util-linux (>= 2.15-1)
Suggests: grub-legacy-doc, mdadm
Conflicts: grub-coreboot, grub-efi-amd64, grub-efi-ia32, grub-ieee1275, grub-pc
Provides: linux-boot-loader
Description: GRand Unified Bootloader (Legacy version)
 GRUB is a GPLed bootloader intended to unify bootloading across x86 operating
 systems.  In addition to loading the Linux kernel, it implements the Multiboot
 standard, which allows for flexible loading of multiple boot images (needed for
 modular kernels such as the GNU Hurd).

rick@rick-HP:~$ aptitude show grub-common
Package: grub-common                     
State: installed
Automatically installed: no
Version: 1.99~rc1-4ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 4,563 k
Depends: base-files (>= 4.0.1~), dpkg (>= 1.15.4) | install-info | dpkg (<=
         1.14.25), lsb-base (>= 3.0-6), libc6 (>= 2.8), libdevmapper1.02.1 (>=
         2:1.02.36), libfreetype6 (>= 2.2.1), zlib1g (>= 1:1.1.4), gettext-base
Recommends: os-prober (>= 1.33)
Suggests: multiboot-doc, grub-emu, xorriso (>= 0.5.6.pl00)
Conflicts: grub-doc (< 0.97-29ubuntu60), grub-legacy-doc (< 0.97-29ubuntu60),
           mdadm (< 2.6.7-2)
Breaks: lupin-support (< 0.30)
Replaces: grub-coreboot (< 1.97+20091114-1), grub-efi (< 1.96+20080831-1),
          grub-efi-amd64 (< 1.98+20100527-1), grub-efi-ia32 (< 1.98+20100527-1),
          grub-ieee1275 (< 1.98+20100527-1), grub-linuxbios (< 1.96+20080831-1),
          grub-pc (< 1.98+20100527-1), grub-yeeloong (< 1.98+20100527-1)
Description: GRand Unified Bootloader, version 2 (common files)
 This package contains common files shared by the distinct flavours of GRUB.
Homepage: http://www.gnu.org/software/grub/

rick@rick-HP:~$ aptitude show grub-pc
Package: grub-pc                         
State: installed
Automatically installed: no
Version: 1.99~rc1-4ubuntu1
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 2,867 k
Depends: libc6 (>= 2.8), libdevmapper1.02.1 (>= 2:1.02.36), debconf (>= 0.5) |
         debconf-2.0, grub-common (= 1.99~rc1-4ubuntu1), ucf
Suggests: desktop-base (>= 4.0.6)
Conflicts: desktop-base (= 4.0.5), grub (< 0.97-54), grub-coreboot,
           grub-efi-amd64, grub-efi-ia32, grub-ieee1275, grub-legacy
Replaces: grub, grub-common (< 1.97~beta1-1ubuntu4), grub-coreboot,
          grub-efi-amd64, grub-efi-ia32, grub-ieee1275, grub-legacy, grub2 (<
          1.99~rc1-4ubuntu1)
Description: GRand Unified Bootloader, version 2 (PC/BIOS version)
 GRUB is a portable, powerful bootloader.  This version of GRUB is based on a
 cleaner design than its predecessors, and provides the following new features: 
 
 * Scripting in grub.cfg using BASH-like syntax. 
 * Support for modern partition maps such as GPT. 
 * Modular generation of grub.cfg via update-grub.  Packages providing GRUB
   add-ons can plug in their own script rules and trigger updates by invoking
   update-grub2. 
 * VESA-based graphical mode with background image support and complete 24-bit
   color set. 
 * Support for extended charsets.  Users can write UTF-8 text to their menu
   entries. 
   
 This package contains a version of GRUB that has been built for use with
 traditional PC/BIOS architecture.
Homepage: http://www.gnu.org/software/grub/

rick@rick-HP:~$ 

``` For reference below:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by Hakunka-Matata on 2011-03-22
Oh, I **LIKE** that post, and that command line - Muchas Gracias!```

aptitude show grub
```That's very, very good.  Wasn't aware of that "aptitude" command.  Just ran it on my console and now I understand.  Were you aware of the change in referencing hd(X,y)? between Grub 0.97 and Grub 2 (1.98 - 1.99)?

---

### Post by Hakunka-Matata on 2011-03-22
> Description: GRand Unified Bootloader, version 2 (PC/BIOS version)(PC/BIOS version) as compared with (GPT)?  Is there a Grub for GPT partition tables?

I'll answer this myself, 
grub-efi-amd64, grub-efi-ia32, 
is what I was thinking about

---

### Post by garvinrick4 on 2011-03-22
#Hakuna-Matata, His CenOS install went fine it is a redhat cousin and uses anaconda installer and grub-legacy with option to not install grub at install. And that is what is
there and will boot from grub2 in Ubuntu install fine.
#Redhat install has to have grub removed as it has grub-legacy also.
#Ubuntu needed to be purged of grub grub-common grub-pc and the grub-common grub-pc reinstalled and would go into mbr. When update-grub is ran OS-prober will go out and find other installs put them in new config file and as menu entry also. So we have one system Ubuntu grub2 running the show and all will be well.
# Have fedora on my system and have reproduced this code in practice so is not in theory
but in practice. 
# Different ways of accomplishing task. I figured Live CD and chroot best for this.
#There are lots of users who are good at grub around some better than I for sure but we
all try to help and I always use mine in practice before giving out in forums.

---

### Post by garvinrick4 on 2011-03-22
LMHmedchem notice sda9 here that is fedora with grub-legacy not installed at install
and is used in my grub2. Notice boot files /dirs:
After thru with post 30 and 28 and grub-updated lets see where CentOS sits:

```
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd
```

---

### Post by Hakunka-Matata on 2011-03-22
@garvanrick4:  Cheers, the explanations #38

---

### Post by LMHmedchem on 2011-03-22
So it appears that my current plan is,

1. boot into SL and manually remove
/boot/grub/menu.lst 
/boot/grub/grub.conf
or should I remove the entire grub dir?

I have already un-installed grub from the sda3 SL installation by booting into SL and doing yum uninstall grub. The only thing left are the conf files, which seem to remain after the uninstall. Should I still implement the steps from post 30 to re-remove grub from sda3 using the ubuntu live CD?

2. Live CD back into ubuntu and repeat the steps from post 28.

I am a bit mystified as to why the Cent install won't boot from something like supergrub2. The install is identified, and ii tries to try to boot, but doesn't find the boot files where they are supposed to be, even though grub.conf says the root is at (1,7), which is correct.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Quackers on 2011-03-22
Sorry to just chip in at the end here, but if you only have one hard drive, the correct address would be 0,7, not 1,7
Hard drives start at number 0, partitions start at 1.
However, not having read through the whole thread I may be misunderstanding. If so, ignore me :wink:

---

### Post by LMHmedchem on 2011-03-22
> **Quackers said:**
> Sorry to just chip in at the end here, but if you only have one hard drive, the correct address would be 0,7, not 1,7
Hard drives start at number 0, partitions start at 1.
However, not having read through the whole thread I may be misunderstanding. If so, ignore me :wink:That makes some sense, but all of the OSs use the drive number 1, and everything but Cent boots with no problem. The only difference I can see in the grub conf entries is that there is no initrd entry for Cent, like the others.

Looking at grub.d/30_os-prober more carefully,
```

menuentry "ScientificLinux (2.6.18-92.1.6.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img
}
menuentry "CentOS release 5.5 (Final) (on /dev/sdb7)" {
    insmod ext2
    **[COLOR=Red]set root=(hd1,7)[/COLOR]**
    search --no-floppy --fs-uuid --set 90cecb53-19e2-4605-b35a-74a27570a1d3
    linux /boot/vmlinuz-2.6.18-194.el5 [COLOR=Red]**root=/dev/sdb7**[/COLOR]
}

```
The Cent entry has set root=(hd1,7), which is correct, but also has root=/dev/sdb7, which doesn't exist. Is this what is causing the  problem? If so, how do I fix it?

I thought I ran grub-update from ubuntu after unpluging the old sda, so I'm not sure why  that entry would be there for sdb7.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Quackers on 2011-03-22
The address 1,7 corresponds with sdb7. The fact that sdb7 does not exist would almost certainly account for it not booting, I would say.
As to why your drive is numbered as 1 when you have only one drive I cannot say. The only thing I can think of is that something else was plugged in at the time they were numbered. A usb flash drive or usb HDD might do that.
Unless you are using raid1 perhaps.

---

### Post by LMHmedchem on 2011-03-22
> **Quackers said:**
> The address 1,7 corresponds with sdb7. The fact that sdb7 does not exist would almost certainly account for it not booting, I would say.
As to why your drive is numbered as 1 when you have only one drive I cannot say. The only thing I can think of is that something else was plugged in at the time they were numbered. A usb flash drive or usb HDD might do that.
Unless you are using raid1 perhaps.I think that the drive numbering comes from the bios. There was another drive before yesterday, and that was probably drive 0, and may relate to the sata port.

I have done update-grub, and now the root is shown as (hd1,7) and /dev/sda7, which are both correct. It still will not boot and I get the same error,

VFS: Cannot open root device "sda7" or unknown-block(0,0)
Please append a correct "root=" boot option

I have looked carefully through the fstab and the only thing that looks different there is that Cent has Label=/, where SL has LABEL=SciLinux.

I guess I will try manually removing the grub conf files from SL (I will just move them for now) and re-run grub update. The grub conf files on SL don't reference the Cent install, but I don't know enough about this to tell if that matters or not, obviously.

I don't know if this thread is relevant or not,
[https://www.centos.org/modules/newbb/viewtopic.php?topic_id=4737](https://www.centos.org/modules/newbb/viewtopic.php?topic_id=4737)

[COLOR=Navy][B]LMHmedchem

[/B][COLOR=Black]Here is the current boot info output,
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CentOS release 5.5 (Final) 
                       Kernel on an
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Scientific Linux SL release 5.2 
                       (Boron) Kernel on an
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003cdeb

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     3,903,794     3,903,732  82 Linux swap / Solaris
/dev/sda2           3,903,795   203,125,859   199,222,065   5 Extended
/dev/sda5           3,903,858     7,807,589     3,903,732  82 Linux swap / Solaris
/dev/sda6           7,807,653   105,466,724    97,659,072  83 Linux
/dev/sda7         105,466,788   166,899,284    61,432,497  83 Linux
/dev/sda3    *    203,125,860   254,325,014    51,199,155  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        4972f29f-10ce-495f-95b2-b09358c28a08   swap                                     
/dev/sda3        cd7875ae-8dfd-4e04-b32f-589f850118d2   ext3       SciLinux                      
/dev/sda5        2fd034d1-ebb2-4840-b188-67d19db97fd2   swap                                     
/dev/sda6        d30ec437-c8f4-4ee7-93c6-ddf90369de41   ext3                                     
/dev/sda7        90cecb53-19e2-4605-b35a-74a27570a1d3   ext3       /                             

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.10, kernel 2.6.31-23-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-23-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-23-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-23-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-23-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-23-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-23-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-23-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set d30ec437-c8f4-4ee7-93c6-ddf90369de41
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
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
menuentry "Scientific Linux SL (2.6.18-194.17.1.el5) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
}
menuentry "ScientificLinux (2.6.18-92.1.6.el5) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img
}
menuentry "CentOS release 5.5 (Final) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 90cecb53-19e2-4605-b35a-74a27570a1d3
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sda7
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== sda6/boot/grub/grub.conf: ==========================

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
# hiddenmenu

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
# kopt=root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=d30ec437-c8f4-4ee7-93c6-ddf90369de41

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=4972f29f-10ce-495f-95b2-b09358c28a08 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=2fd034d1-ebb2-4840-b188-67d19db97fd2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
## added to mount usb as rw
sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

  /dev/sda1 /media/Data_Volume/ ext3 defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


  49.9GB: boot/grub/core.img
  50.0GB: boot/grub/grub.cfg
  50.0GB: boot/grub/grub.conf
  49.9GB: boot/grub/menu.lst
  49.9GB: boot/initrd.img-2.6.31-19-generic
  49.9GB: boot/initrd.img-2.6.31-20-generic
  50.0GB: boot/initrd.img-2.6.31-23-generic
  49.9GB: boot/vmlinuz-2.6.31-19-generic
  49.9GB: boot/vmlinuz-2.6.31-20-generic
  49.9GB: boot/vmlinuz-2.6.31-23-generic
  50.0GB: initrd.img
  49.9GB: initrd.img.old
  49.9GB: vmlinuz
  49.9GB: vmlinuz.old

=============================== sda7/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0
LABEL=SWAP-sdb4         swap                    swap    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0

=================== sda7: Location of files loaded by Grub: ===================


  56.1GB: boot/initrd-2.6.18-194.el5.img
  56.0GB: boot/vmlinuz-2.6.18-194.el5

========================== sda3/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd1,2)
#          kernel /boot/vmlinuz-version ro root=/dev/sdb3
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=10
splashimage=(hd1,2)/boot/grub/splash.xpm.gz
hiddenmenu
title Scientific Linux SL (2.6.18-194.17.1.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
title ScientificLinux (2.6.18-92.1.6.el5)
    root (hd1,2)
    kernel /boot/vmlinuz-2.6.18-92.1.6.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-92.1.6.el5.img

#title        Ubuntu 9.04, kernel 2.6.28-13-generic
#uuid        d30ec437-c8f4-4ee7-93c6-ddf90369de41
#kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=d30ec437-c8f4-4ee7-93c6-ddf90369de41 ro #quiet splash 
#initrd        /boot/initrd.img-2.6.28-13-generic
#quiet

=============================== sda3/etc/fstab: ===============================

LABEL=SciLinux          /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sdb1               swap                    swap    defaults        0 0
/dev/sdb5               swap                    swap    defaults        0 0

=================== sda3: Location of files loaded by Grub: ===================


 118.1GB: boot/grub/grub.conf
 118.1GB: boot/grub/menu.lst
 118.1GB: boot/grub/stage2
 118.2GB: boot/initrd-2.6.18-194.17.1.el5.img
 118.1GB: boot/initrd-2.6.18-194.17.1.el5kdump.img
 118.2GB: boot/initrd-2.6.18-92.1.6.el5.img
 118.1GB: boot/initrd-2.6.18-92.1.6.el5kdump.img
 118.1GB: boot/vmlinuz-2.6.18-194.17.1.el5
 118.1GB: boot/vmlinuz-2.6.18-92.1.6.el5
```[/COLOR][/COLOR]

---

### Post by LMHmedchem on 2011-03-22
I have moved the grub folder out of SL /boot, and now SL will not boot either and I get the same error as with Cent. I also did another purge/re-install of grub from ubuntu and noticed an inconsistency.

Shell output from the grub re-install,
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-23-generic
Found initrd image: /boot/initrd.img-2.6.31-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Scientific Linux SL release 5.2 (Boron) on /dev/sda3
Found CentOS release 5.5 (Final) on /dev/sda7
done
```The drive designations at the top are wrong, there is only one drive attached and it is still finding hd0 as /dev/sda, where other parts of the system seem to show sda as hd1. Grub2 identifies Cent as being on /dev/sda7, but /boot/grub/device.map shows the following

```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```Now the /etc/grub.d/30_os-prober entries for SL and Cent are
```
menuentry "Scientific Linux SL release 5.2 (Boron) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 root=/dev/sda3
}
menuentry "Scientific Linux SL release 5.2 (Boron) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-92.1.6.el5 root=/dev/sda3
}
menuentry "CentOS release 5.5 (Final) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 90cecb53-19e2-4605-b35a-74a27570a1d3
    linux /boot/vmlinuz-2.6.18-194.el5 root=/dev/sda7
}
```These are setting the root as hd0, when device.map says the drive is hd1. Sdb was he drive that all of this was on when there were two drives, sda was removed and now there is only one drive. The question is why can ubuntu boot? It seems like the ubuntu roots are defined by UUID numbers and not relative to sd*.  The ubuntu fstab entries also use a UUID. The old SL grub.conf showed SL to be on hd1, and that must be why it still worked.

I guess I'm saying that the bios still thinks the drive is drive 1 and can't find a bootable image because it's looking on drive0, which doesn't exist. It works for ubuntu because it is looking for a uuid number. Does that make any sense?

The question is how to fix it, if that is indeede the issue. Should I change the device.map? Should I manually edit fstab and grub.conf to change the hd or change to UUID? Is there a command line argument to make grub2 use UUID locations?

Do you concur that this is the source of the issue, and if so,  are there suggestions for fixing it.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Quackers on 2011-03-22
I have seen problems where grub2 and grub are installed on the same system.
In your case grub2 is trying to boot files that are not meant for grub2, as I see it.
As far as I'm aware grub2 does not use /boot/grub/grub.conf and it definitely doesn't use /boot/grub/menu.lst, both of which are in your sda6 partition, which is the partition grub2 is using to try to boot things.
With this possible conflict I have no idea what would be the sensible thing to do.
I personally would purge then re-install grub2, then reconfigure grub legacy to install to the root partition of Cent OS system.
However I have no idea whether that is the correct thing to do, or even whether it would work - but I suspect so.
I will ask another member to look at your thread and make suggestions. His advice will be much more coherent than mine :-)

---

### Post by LMHmedchem on 2011-03-22
> **Quackers said:**
> I have seen problems where grub2 and grub are installed on the same system.
In your case grub2 is trying to boot files that are not meant for grub2, as I see it.
As far as I'm aware grub2 does not use /boot/grub/grub.conf and it definitely doesn't use /boot/grub/menu.lst, both of which are in your sda6 partition, which is the partition grub2 is using to try to boot things.
With this possible conflict I have no idea what would be the sensible thing to do.
I personally would purge then re-install grub2, then reconfigure grub legacy to install to the root partition of Cent OS system.
However I have no idea whether that is the correct thing to do, or even whether it would work - but I suspect so.
I will ask another member to look at your thread and make suggestions. His advice will be much more coherent than mine :-)Legacy grub is definitely not installed. Looking at the package manager, only gurb-pc, and grub common (which are the common files for grub2) are installed. There was a legacy grub installed on the mbr of the old sda, which is why I unplugged the drive. There were no OSs on sda anymore, so I couldn't figure out how to remove grub from the mbr. I don't know what files grub2 is supposed to use.

The current grub2 was installed after having done a purge of grub legacy, which the shell said wasn't installed, and grub2. Then grub2 was re-installed followed by grub-update. I also manually moved the old grub directory from sda3, which also had a grub install in the past, but no longer. The report from the boot info script indicates that,

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

This is now the only indication of grub that is on the system. The only difference I can see between Ubuntu, which will boot, and the other OSs is the use of UUID to declare the root. I don't know if that matters or not.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Quackers on 2011-03-22
There are grub legacy boot files on at least 2 partitions.
Don't do anything just yet. I'm hoping for guidance in the near future :wink:

---

### Post by drs305 on 2011-03-22
I'm new to the thread and to be honest I dont have the time at the moment to read each of the posts thoroughly. But regarding your Centos menuentries, and the others in Post #46 they don't have an *initrd* line. 

I've only dabbled a bit with Centos and not at all with SL. I installed Centos so I could understand how it boots to help someone in an older thread. My Centos menuentries have an initrd line and I would expect yours should as well; it looks wrong without one.

For this thread in general, as was previously mentioned, I think the advice given earlier on purging (not uninstalling) grub and grub-pc and 'starting over' was probably what I would have recommended. Side note: grub-common isn't grub legacy; Grub legacy is *grub*; grub 2 is *grub-pc*.

Anyway I'll start watching from here on and if I can catch up and offer anything useful I will.

---

### Post by Quackers on 2011-03-22
Thanks drs305.
I wonder if it's possible that Cent OS did not install fully or properly?

---

### Post by LMHmedchem on 2011-03-22
> **Quackers said:**
> Thanks drs305.
I wonder if it's possible that Cent OS did not install fully or properly?It may be, but a bad install of Cent doesn't explain why SL won't boot, now that I have removed the old grub files from sda3. My guess is that the key lies in the old files, which allowed SL to boot via grub2 on ubuntu. What I could see there was that the root for SL was given as being on hd1, and not hd0. Since the device map sees two drives, it is clear that something in the OS still thinks that there is an hd0 and hd1, instead of just hd0. The error is an indication that the bios isn't able to find the OS where grub tells it to look. It something in the OS is still pointing hd1 to to sda, that would explain why grub isn't able to boot the OS from hd(0,7).

I think looking at the ubuntu entries, which do boot, and the old grub conf from SL, which also booted, and comparing to the current entries for SL and Cent should show what is wrong. There doesn't seem to be any what to manually edit the grub files, or I could test some of this.


This is the shell output from my latest implementation of the steps given in post 30 and 28.

from removal of grub lagacy from sda3
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda3 /mnt
root@ubuntu:~# mount -o bind /dev /mnt/dev
root@ubuntu:~# mount -o bind /dev/pts /mnt/dev/pts
root@ubuntu:~# mount -o bind /proc /mnt/proc
root@ubuntu:~# mount -o bind /sys /mnt/sys
root@ubuntu:~# chroot /mnt
[root@ubuntu /]# yum remove grub
Loaded plugins: kernel-module
Setting up Remove Process
No Match for argument: grub
Package(s) grub available, but not installed.
No Packages marked for removal
[root@ubuntu /]# exit
exit
root@ubuntu:~# umount /mnt/dev/pts
root@ubuntu:~# umount /mnt/dev
root@ubuntu:~# umount /mnt/proc
root@ubuntu:~# umount /mnt/sys
root@ubuntu:~# umount /mnt
root@ubuntu:~# reboot
```from purge and reinstall of grub-pc from sda6
```
untu@ubuntu:~$ sudo mount /dev/sda6 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# apt-get purge grub grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 19 not upgraded.
After this operation, 4,235kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 194127 files and directories currently installed.)
Removing grub-pc ...
Saving menu.lst backup in /boot/grub/menu.lst_backup_by_grub2_prerm
Running update-grub Legacy to remove our core.img in it
    Searching for GRUB installation directory ... found: /boot/grub
    Searching for default file ... found: /boot/grub/default
    Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
    Searching for splash image ... none found, skipping ...
    Found kernel: /boot/vmlinuz-2.6.31-23-generic
    Found kernel: /boot/vmlinuz-2.6.31-20-generic
    Found kernel: /boot/vmlinuz-2.6.31-19-generic
    Found kernel: /boot/memtest86+.bin
    Updating /boot/grub/menu.lst ... done
    
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for install-info ...
root@ubuntu:/# apt-get update
Hit http://archive.canonical.com karmic Release.gpg
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://archive.canonical.com karmic Release                                
Ign http://grey.colorado.edu karmic Release.gpg                                
Ign http://grey.colorado.edu karmic/main Translation-en_US                   
Ign http://grey.colorado.edu karmic Release               
Hit http://archive.canonical.com karmic/partner Packages  
Hit http://archive.canonical.com karmic/partner Sources   
Ign http://grey.colorado.edu karmic/main Packages         
Ign http://grey.colorado.edu karmic/main Packages         
Hit http://grey.colorado.edu karmic/main Packages
Hit http://ftp.freepark.org karmic Release.gpg
Ign http://ftp.freepark.org karmic/main Translation-en_US
Ign http://ftp.freepark.org karmic/restricted Translation-en_US
Ign http://ftp.freepark.org karmic/multiverse Translation-en_US
Ign http://ftp.freepark.org karmic/universe Translation-en_US
Hit http://ftp.freepark.org karmic-updates Release.gpg
Ign http://ftp.freepark.org karmic-updates/main Translation-en_US
Ign http://ftp.freepark.org karmic-updates/restricted Translation-en_US
Ign http://ftp.freepark.org karmic-updates/multiverse Translation-en_US
Ign http://ftp.freepark.org karmic-updates/universe Translation-en_US
Hit http://ftp.freepark.org karmic-security Release.gpg
Ign http://ftp.freepark.org karmic-security/main Translation-en_US
Ign http://ftp.freepark.org karmic-security/restricted Translation-en_US
Ign http://ftp.freepark.org karmic-security/multiverse Translation-en_US
Ign http://ftp.freepark.org karmic-security/universe Translation-en_US
Hit http://ftp.freepark.org karmic Release
Hit http://ftp.freepark.org karmic-updates Release
Hit http://ftp.freepark.org karmic-security Release
Hit http://ftp.freepark.org karmic/main Packages
Hit http://ftp.freepark.org karmic/restricted Packages
Hit http://ftp.freepark.org karmic/multiverse Packages
Hit http://ftp.freepark.org karmic/main Sources
Hit http://ftp.freepark.org karmic/restricted Sources
Hit http://ftp.freepark.org karmic/universe Packages
Hit http://ftp.freepark.org karmic/universe Sources
Hit http://ftp.freepark.org karmic-updates/main Packages
Hit http://ftp.freepark.org karmic-updates/restricted Packages
Hit http://ftp.freepark.org karmic-updates/multiverse Packages
Hit http://ftp.freepark.org karmic-updates/main Sources
Hit http://ftp.freepark.org karmic-updates/restricted Sources
Hit http://ftp.freepark.org karmic-updates/universe Packages
Hit http://ftp.freepark.org karmic-updates/universe Sources
Hit http://ftp.freepark.org karmic-security/main Packages
Hit http://ftp.freepark.org karmic-security/restricted Packages
Hit http://ftp.freepark.org karmic-security/multiverse Packages
Hit http://ftp.freepark.org karmic-security/main Sources
Hit http://ftp.freepark.org karmic-security/restricted Sources
Hit http://ftp.freepark.org karmic-security/universe Packages
Hit http://ftp.freepark.org karmic-security/universe Sources
Reading package lists... Done
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 19 not upgraded.
Need to get 0B/1,453kB of archives.
After this operation, 4,235kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 193904 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4.1_amd64.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu4.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4.1) ...

Setting up grub-pc (1.97~beta4-1ubuntu4.1) ...

Creating config file /etc/default/grub with new version
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda
(hd1)    /dev/sdb
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-23-generic
Found initrd image: /boot/initrd.img-2.6.31-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Scientific Linux SL release 5.2 (Boron) on /dev/sda3
Found CentOS release 5.5 (Final) on /dev/sda7
done

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-23-generic
Found initrd image: /boot/initrd.img-2.6.31-23-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Scientific Linux SL release 5.2 (Boron) on /dev/sda3
Found CentOS release 5.5 (Final) on /dev/sda7
done
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
ubuntu@ubuntu:~$ 
```I selected sda as the location to install grub, and left the "linux command line" text field blank.

This makes no change and I am still not able to boot either Cent or SL. At this point I am tempted to replace the grub folder to sda3/boot and to try placing a similar grub folder in the Cent sda7/boot to see if that will let me boot.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by drs305 on 2011-03-22
The terminal commands you posted all look like they ran correctly. 

Your SL Linux entry also doesn't list an initrd line. I don't know if it should, but most Linux-based entries do, so that could explain why it won't boot either. It's odd to me that both Centos and SL are missing the initrd lines and/or the initrd images...

---

### Post by LMHmedchem on 2011-03-22
> **drs305 said:**
> The terminal commands you posted all look like they ran correctly. 

Your SL Linux entry also doesn't list an initrd line. I don't know if it should, but most Linux-based entries do, so that could explain why it won't boot either. It's odd to me that both Centos and SL are missing the initrd lines and/or the initrd images...The SL entry used to have a initrd line, when there were still conf files in SL /boot/grub when update-grub was run. Here is a previous entry from post 21.
```
menuentry "Scientific Linux SL (2.6.18-194.17.1.el5) (on /dev/sdb3)" {
    insmod ext2
    set root=(hd1,3)
    search --no-floppy --fs-uuid --set cd7875ae-8dfd-4e04-b32f-589f850118d2
    linux /boot/vmlinuz-2.6.18-194.17.1.el5 ro root=LABEL=SciLinux rhgb quiet crashkernel=128M@16M
    initrd /boot/initrd-2.6.18-194.17.1.el5.img
}
```
I removed the grub folder from SL sda3 /boot/ in case they were causing an issue, and re-ran update-grub. Following that, the new entry for SL doesn't have an initrd entry anymore and also won't boot anymore.

I can't edit the grub 2 conf files to test any of this. I could make new grub style conf files and put them in /boot/grub/ on the systems that aren't running. I could then re-run update-grub and see if it picks up the information. SL booted before when it still had it's own grub conf, even though grub wasn't installed in the OS.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by drs305 on 2011-03-22
The initrd references should be in the menuentry, but the images also have to still exist in the /boot folder. 

Generally, os-prober and Grub2 do a good job of finding boot files. If you have run update-grub and the initrd line is missing, there is a good chance it doesn't exist in the correct location. You should probably mount your Centos and SL Linux partitions and inspect them to see if the initrd images exist.

From an operating OS, you can restore initrd images *within* the OS with the *mkinitramfs* command, but I don't think you could even use chroot to do it unless you were using the Centos LiveCD. (You could do it from there.) If you really are missing the initrd.img file, you may have other problems as well, but as a minimum you'd need to restore the image for the kernel you want to boot into /boot of the partition of that system.

---

### Post by garvinrick4 on 2011-03-22
If you do not have live cd for CentOS or Redhat I have used Ubuntu Live CD just because I have tried it before. I have had most all redhat and cousins Fedora, CentOS and such installed beside Ubuntu. This is fedora14 below, once you are in chroot use yum commands chroot from Ubuntu live CD. umount the same as before. 
*Using Live CD from install is the best but this is if you only have a Ubuntu Live CD.
```
rick@rick-HP:~$ sudo mount /dev/sda9 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
[sudo] password for rick: 
[root@rick-HP /]# yum update
Loaded plugins: fastestmirror, presto, protectbase, refresh-packagekit
Loading mirror speeds from cached hostfile
updates/metalink                                         | 6.7 kB     00:00     
 * fedora: archive.linux.duke.edu
 * rpmfusion-free: mirror.hiwaay.net
 * rpmfusion-free-updates: mirror.hiwaay.net
 * rpmfusion-nonfree: mirror.hiwaay.net
 * rpmfusion-nonfree-updates: mirror.hiwaay.net
 * updates: fedora.mirror.netriplex.com
adobe-linux-i386                                         |  951 B     00:00     
rpmfusion-free-updates                                   | 3.3 kB     00:00     
rpmfusion-nonfree-updates                                | 3.3 kB     00:00     
http://fedora.mirror.netriplex.com/updates/14/x86_64/repodata/repomd.xml: [Errno 14] HTTP Error 404 : http://fedora.mirror.netriplex.com/updates/14/x86_64/repodata/repomd.xml 
Trying other mirror.
updates                                                  | 4.7 kB     00:00     
0 packages excluded due to repository protections
Setting up Update Process
No Packages marked for Update
[root@rick-HP /]# 

```*All installs using anaconda installer were installed without grub and grub updated from within Ubuntu grub2.
#I have got to believe messing around inside of installs instead of just using terminal commands has made rather a mess
of your grub situation. It is normally pretty cut and dry purging and reinstalling. You also went from sdb installs to sda now.
Might be easier to reinstall redhat and CentOS and just use grub2. 
*dr305 and Quackers are in this now also so they can suggest other options available. Mine is to leave Ubuntu and reinstall the yum's
and not install any grub at all in anaconda. Boot into Ubuntu and update your grub. Just to messy right now.
##The mkinitramfs command while in chroot of install looks like would be worth a try!!

---

### Post by LMHmedchem on 2011-03-22
> **drs305 said:**
> The initrd references should be in the menuentry, but the images also have to still exist in the /boot folder. 

Generally, os-prober and Grub2 do a good job of finding boot files. If you have run update-grub and the initrd line is missing, there is a good chance it doesn't exist in the correct location. You should probably mount your Centos and SL Linux partitions and inspect them to see if the initrd images exist.

From an operating OS, you can restore initrd images *within* the OS with the *mkinitramfs* command, but I don't think you could even use chroot to do it unless you were using the Centos LiveCD. (You could do it from there.) If you really are missing the initrd.img file, you may have other problems as well, but as a minimum you'd need to restore the image for the kernel you want to boot into /boot of the partition of that system.The initrd file is there in the Cent install.

Just to see what happens, I replace the grub folder in SL and did update-grub. The new files created by grub2 include the initrd for SL again, and I can boot into it. For some reason, it appears that grub2 doesn't include the initrd line in the menu for these redhat installs that it finds on its own, unless the found install already has a grub.conf that includes the initrd location. I don't know if that's a bug, or if I'm somehow not using it properly. It is hard to tell, since this started as an odd setup with grub installed  in several places, including places where there are no longer OS installs.

I am going to place a grub directory in /boot for Cent with an entry of the same format as the SL entry and re-run update-grub. I will see if that shoehorns the initrd line into the menu or not. It can't hurt to try.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by oldfred on 2011-03-22
I do not think the os-prober finds other installs & writes its boot stanza but copies boot stanzas from menu.lst, grub.conf or grub.cfg files. We have seen before where problems in a menu.lst get copied into grub.cfg by the prober.

---

### Post by LMHmedchem on 2011-03-22
Well this worked for some reason.

I created the following file called grub.conf,
```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/vmlinuz-2.6.18-194.el5 ro root=/dev/sda7
#         initrd /boot/initrd-2.6.18-194.el5.img
default=0
timeout=10

hiddenmenu
title CentOS release 5.5 (Final) (2.6.18-194.el5)
    root (hd0,7)
    kernel /boot/vmlinuz-2.6.18-194.el5 ro root=/dev/sda7
    initrd /boot/initrd-2.6.18-194.el5.img
```I did sudo su to become root, and then chown to make root the owner of the file. Then I did cp -fp grub.conf /media/_/boot/grub/. The install partition for Cent appears as / in the ubuntu file browser. It is a big help the ubuntu lets you mount other install partition by just clicking on then and entering the root password.

After copying the grub.conf file to the /boot/grub/ directory on the install that wasn't booting, I ran sudo update-grub again. This time, the initrd line is in the menu entry for Cent, and I can successfully boot into Cent. That might imply that you want to install grub with every additional distro, and then un-install it as soon as you boot in, but leave the config files. That seems a bit scary. I guess what I did is a work-aground as well, but it is hard to understand why it is necessary when others seemed to have installed red hat distros without grub and were able to get in by just doing update-grub in the OS where grub2 was installed. Is there any reason why grub2 would leave out the initrd menu line like it did for me.

**EDIT:**
> **oldfred said:**
> I do not think the os-prober finds other installs & writes its boot stanza but copies boot stanzas from menu.lst, grub.conf or grub.cfg files. We have seen before where problems in a menu.lst get copied into grub.cfg by the prober.This would explain what happened, and imply that there needs to be a grub.conf file on every installed OS. Reading about grub2, the recommended instructions for multi-boot don't seem to imply that is necessary though.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by LMHmedchem on 2011-03-22
If someone who know will tell me that what I did was a reasonable work around, I will write it up a bit more like a set of instructions. It my hack is not a recommended fix, please let me know that as well.

I posted this afternoon in the Cent forum, in case someone there had run into the same thing. There was only one response,
[https://www.centos.org/modules/newbb/viewtopic.php?topic_id=30639&forum=37](https://www.centos.org/modules/newbb/viewtopic.php?topic_id=30639&forum=37)

which was to recommend,

"Go ahead and install GRUB, but rather than letting it overwrite your GRUB2 MBR write the CentOS boot record to the CentOS boot partition using the Advanced option in anaconda."

This would imply always having a boot partition, and always installing multiple instances of grub, and then doing a chainload, if I understand correctly.
```

title chainload CentOS GRUB
        root (hd0,6)
        chainloader +1
title chainload Scientific Linux GRUB
        root (hd0,2)
        chainloader +1

```This seems more like the legacy grub approach.

Installing grub all over the place just doesn't seem like a good idea. The task of booting an OS from a specific location in the storage system is really a quite simple one. I am just amazed at how involved it seems to become when there are more than one or two OSs installed. It appears that all that is necessary is to have /boot/grub/grub.conf included with each install (not grub itself) and then to have grub2 on the MBR of the primary boot drive. There should probably be an option in grub2 to find additional OSs at boot time, so you don't have to boot into something and do update-grub. I don't see any reason why there would ever need to be anything more complex than that.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-22
It is not complex you just do not install grub legacy at install and update grub in your grub2 install and all is fine: 
Have done it with Fedora, openSuse,Redhat and CentOS.
Here is bootscript with Fedora as sda9. Is not a problem grub2 and osprober takes care
of everything. Does not really need to be over thought. If installed correctly it works.
Example below:

```

               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   256,794,621   256,385,022   7 HPFS/NTFS
/dev/sda3         256,799,086   578,433,023   321,633,938   5 Extended
/dev/sda5         342,955,620   366,506,909    23,551,290  83 Linux
/dev/sda6         256,799,088   279,322,154    22,523,067  83 Linux
/dev/sda7         279,322,218   342,955,619    63,633,402  83 Linux
/dev/sda8         366,506,973   407,954,609    41,447,637   7 HPFS/NTFS
/dev/sda9         407,954,673   429,047,954    21,093,282  83 Linux
/dev/sda10        429,048,018   472,070,024    43,022,007  83 Linux
/dev/sda11        472,072,192   492,910,591    20,838,400  83 Linux
/dev/sda12        492,922,458   513,951,479    21,029,022  83 Linux
/dev/sda13        513,953,792   578,433,023    64,479,232  83 Linux
/dev/sda4         578,436,390   625,137,344    46,700,955   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       cbb12bc7-02fe-46b5-b7b0-edf1cc02833d   ext4       pae                           
/dev/sda11       e912b98d-4e07-40b1-86d8-25715df0f9ee   ext4       maverick                      
/dev/sda12       439491c0-b533-48a3-8971-d2953bdb53f4   ext4       test                          
/dev/sda13       04282cb8-4baa-4f21-aecd-729df9bc35e2   ext4       meerkat                       
/dev/sda1        C6EECCF3EECCDCB5                       ntfs       SYSTEM                        
/dev/sda2        66B0BDBFB0BD95D1                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        524C43ED4C43CB05                       ntfs       RECOVERY                      
/dev/sda5        eb110c40-c8a5-45d3-8b72-8cfb165f9bdb   ext4       natty                         
/dev/sda6        d03f894f-94ce-4c00-9c43-19c25f2af12c   ext4       lucid                         
/dev/sda7        0f7c5de9-c3b4-4c50-b288-d34e9ef6e119   ext4       home                          
/dev/sda8        1927A02F2C3A884A                       ntfs       data                          
/dev/sda9        928df639-e6cf-4c3b-9c17-965a91e60efc   ext4       fedora                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 2.6.38-4-generic ...'
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-4-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 2.6.38-3-generic ...'
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-1-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 2.6.38-1-generic ...'
    linux    /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-1-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux    /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.37-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.37-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    echo    'Loading Linux 2.6.37-12-generic ...'
    linux    /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.37-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda12)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.9-64.fc14.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 180.1GB: boot/grub/core.img
 180.4GB: boot/grub/grub.cfg
 180.8GB: boot/initrd.img-2.6.37-12-generic
 176.8GB: boot/initrd.img-2.6.38-1-generic
 181.9GB: boot/initrd.img-2.6.38-3-generic
 183.2GB: boot/initrd.img-2.6.38-4-generic
 179.0GB: boot/vmlinuz-2.6.37-12-generic
 179.7GB: boot/vmlinuz-2.6.38-1-generic
 177.3GB: boot/vmlinuz-2.6.38-3-generic
 182.8GB: boot/vmlinuz-2.6.38-4-generic
 183.2GB: initrd.img
 181.9GB: initrd.img.old
 182.8GB: vmlinuz
 177.3GB: vmlinuz.old

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" {
    insmod ext2
    set root='(hd0,13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" {
    insmod ext2
    set root='(hd0,13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c /               ext4    errors=remount-ro 0       1


=================== sda6: Location of files loaded by Grub: ===================


 133.8GB: boot/grub/core.img
 135.0GB: boot/grub/grub.cfg
 138.8GB: boot/initrd.img-2.6.32-27-generic
 139.8GB: boot/initrd.img-2.6.32-28-generic
 135.8GB: boot/vmlinuz-2.6.32-27-generic
 139.8GB: boot/vmlinuz-2.6.32-28-generic
 139.8GB: initrd.img
 138.8GB: initrd.img.old
 139.8GB: vmlinuz
 135.8GB: vmlinuz.old

=============================== sda9/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Fri Jun 25 09:33:30 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=928df639-e6cf-4c3b-9c17-965a91e60efc /                       ext4    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sda9: Location of files loaded by Grub: ===================


 217.5GB: boot/initramfs-2.6.35.10-74.fc14.x86_64.img
 216.9GB: boot/initramfs-2.6.35.9-64.fc14.x86_64.img
 212.7GB: boot/initrd-plymouth.img
 218.0GB: boot/vmlinuz-2.6.35.10-74.fc14.x86_64
 216.6GB: boot/vmlinuz-2.6.35.9-64.fc14.x86_64

========================== sda10/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,10)'
search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    echo    'Loading Linux 2.6.32-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" {
    insmod ext2
    set root='(hd0,11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda12)" {
    insmod ext2
    set root='(hd0,12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" {
    insmod ext2
    set root='(hd0,13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" {
    insmod ext2
    set root='(hd0,13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod ext2
    set root='(hd0,9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d /               ext4    errors=remount-ro 0       1

=================== sda10: Location of files loaded by Grub: ===================


 228.4GB: boot/grub/core.img
 222.3GB: boot/grub/grub.cfg
 221.6GB: boot/initrd.img-2.6.32-27-generic-pae
 230.3GB: boot/initrd.img-2.6.32-28-generic-pae
 230.1GB: boot/vmlinuz-2.6.32-27-generic-pae
 230.2GB: boot/vmlinuz-2.6.32-28-generic-pae
 230.3GB: initrd.img
 221.6GB: initrd.img.old
 230.2GB: vmlinuz
 230.1GB: vmlinuz.old

========================== sda11/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.9-64.fc14.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda11/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda11 during installation
UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee /               ext4    errors=remount-ro 0       1

=================== sda11: Location of files loaded by Grub: ===================


 244.4GB: boot/grub/core.img
 246.2GB: boot/grub/grub.cfg
 248.0GB: boot/initrd.img-2.6.35-24-generic
 249.3GB: boot/initrd.img-2.6.35-25-generic
 247.9GB: boot/vmlinuz-2.6.35-24-generic
 247.7GB: boot/vmlinuz-2.6.35-25-generic
 249.3GB: initrd.img
 248.0GB: initrd.img.old
 247.7GB: vmlinuz
 247.9GB: vmlinuz.old

========================== sda12/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos12)'
search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.txt
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-4-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-4-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-4-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    echo    'Loading Linux 2.6.38-4-generic ...'
    linux    /boot/vmlinuz-2.6.38-4-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-4-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-3-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-3-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-3-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    echo    'Loading Linux 2.6.38-3-generic ...'
    linux    /boot/vmlinuz-2.6.38-3-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-3-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos12)'
    search --no-floppy --fs-uuid --set=root 439491c0-b533-48a3-8971-d2953bdb53f4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6EECCF3EECCDCB5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sda10)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos10)'
    search --no-floppy --fs-uuid --set=root cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos11)'
    search --no-floppy --fs-uuid --set=root e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro quiet splash
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Ubuntu, with Linux 2.6.35-26-generic (recovery mode) (on /dev/sda13)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos13)'
    search --no-floppy --fs-uuid --set=root 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single
    initrd /boot/initrd.img-2.6.35-26-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 66B0BDBFB0BD95D1
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos4)'
    search --no-floppy --fs-uuid --set=root 524C43ED4C43CB05
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-4-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-4-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-4-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-3-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-3-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-3-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.9-64.fc14.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda12/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=439491c0-b533-48a3-8971-d2953bdb53f4 /               ext4    errors=remount-ro 0       1

=================== sda12: Location of files loaded by Grub: ===================


 254.6GB: boot/grub/core.img
 262.3GB: boot/grub/grub.cfg
 259.9GB: boot/initrd.img-2.6.38-3-generic
 260.6GB: boot/initrd.img-2.6.38-4-generic
 257.9GB: boot/vmlinuz-2.6.38-3-generic
 259.9GB: boot/vmlinuz-2.6.38-4-generic
 260.6GB: initrd.img
 259.9GB: initrd.img.old
 259.9GB: vmlinuz
 257.9GB: vmlinuz.old

========================== sda13/boot/grub/grub.cfg: ==========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos13)'
search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux    /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    echo    'Loading Linux 2.6.35-26-generic ...'
    linux    /boot/vmlinuz-2.6.35-26-generic root=UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos13)'
    search --no-floppy --fs-uuid --set 04282cb8-4baa-4f21-aecd-729df9bc35e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set c6eeccf3eeccdcb5
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sda10)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos10)'
    search --no-floppy --fs-uuid --set cbb12bc7-02fe-46b5-b7b0-edf1cc02833d
    linux /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=cbb12bc7-02fe-46b5-b7b0-edf1cc02833d ro single
    initrd /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-25-generic (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-25-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro quiet splash
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set e912b98d-4e07-40b1-86d8-25715df0f9ee
    linux /boot/vmlinuz-2.6.35-24-generic root=UUID=e912b98d-4e07-40b1-86d8-25715df0f9ee ro single
    initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda12)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set 439491c0-b533-48a3-8971-d2953bdb53f4
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=439491c0-b533-48a3-8971-d2953bdb53f4 ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 66b0bdbfb0bd95d1
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set 524c43ed4c43cb05
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.38-1-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.38-1-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.38-1-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.37-12-generic (recovery mode) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set eb110c40-c8a5-45d3-8b72-8cfb165f9bdb
    linux /boot/vmlinuz-2.6.37-12-generic root=UUID=eb110c40-c8a5-45d3-8b72-8cfb165f9bdb ro single
    initrd /boot/initrd.img-2.6.37-12-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-27-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-27-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-27-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set d03f894f-94ce-4c00-9c43-19c25f2af12c
    linux /boot/vmlinuz-2.6.32-26-generic root=UUID=d03f894f-94ce-4c00-9c43-19c25f2af12c ro single
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
}
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.9-64.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.9-64.fc14.x86_64.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda13/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda13 during installation
UUID=04282cb8-4baa-4f21-aecd-729df9bc35e2 /               ext4    errors=remount-ro 0       1

=================== sda13: Location of files loaded by Grub: ===================


 267.7GB: boot/grub/core.img
 266.2GB: boot/grub/grub.cfg
 269.4GB: boot/initrd.img-2.6.35-26-generic
 269.4GB: boot/vmlinuz-2.6.35-26-generic
 269.4GB: initrd.img
 269.4GB: vmlinuz
```

---

### Post by LMHmedchem on 2011-03-22
As far as I can tell, I did what was advised, which was to install Cent without grub, and then go into the distro from which grub2 was installed and do update-grub. Even when we got all of the old grub stuff cleaned out, that didn't work. It was necessary to put a correct older style grub.conf file in /boot/grub of each of the red hat install in order for os-prober to create a valid entry in the boot menu. Without the grub.conf  files in the new distros,  the menu item was created, but didn't work. 

Looking at your menuentry for Fedora /dev/sda9
```

menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos9)'
    search --no-floppy --fs-uuid --set=root 928df639-e6cf-4c3b-9c17-965a91e60efc
    linux /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 root=/dev/sda9
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
}
```an initrd line has been included. The question is why the initrd line was missing when I implemented the same steps you did? Why did update-grub fail to include this line and why was it necessary to add the old style grub.conf files to the distros in order to get the initrd line into the menu entry?

I agree that the proposed system is a significant improvement over the type of chain load thing suggested in the Cent forum, I just don't know why it didn't work in my case. Perhaps something goofy happened because of the multiple grub installations that were on the drives when I started. When I was done with all the cleaning you suggested, my boot file looked like yours with grub2 at one location and no other grub, but it still wouldn't work. Whatever happened was not correctable after the fact it appears.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by garvinrick4 on 2011-03-22
You are up and running that is what counts. A lot of different users and a lot of different
ways to maintain a system. Linux is enjoyable that is for sure. Was a good thread, enjoy your linux.

---

### Post by LMHmedchem on 2011-03-22
> **garvinrick4 said:**
> You are up and running that is what counts. A lot of different users and a lot of different
ways to maintain a system. Linux is enjoyable that is for sure. Was a good thread, enjoy your linux.Well at any rate, thank you all very much for the help and the whirlwind tour of grub2. I am sure I would still be slogging through the weeds for quite some time without the assistance of the forum. I will probably rebuild this box at some point, and it will be interesting to see if the process goes more smoothly on a fresh partition setup.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by drs305 on 2011-03-23
Just a follow-up for those following this thread.

I did some testing last night and have multiple distros on my system. I checked some of the menuentries and they were also missing the "initrd" line, even though the image files existed. So at some point (I haven't used several of the distros in more than a year) G2 was failing to properly build the menuentry. It's just something to watch for in future threads.

G2/os-prober will import the entries from other distros (I'm pretty sure it gathers the information from the 10_linux entries). If it doesn't find the Grub folder, it will mine data and find the kernels/images and build a new menuentry.

@ *LMHmedchem*
If you don't have any more issues you can mark the thread 'SOLVED' via the 'Thread Tools' link at the top right of the first post (it's reversible). Happy Linux-ing !

---

### Post by Quackers on 2011-03-23
I use the same method as wilee-nilee to boot all my OSes from one controlling grub2 installation. There are other methods used as well, though.
Glad to see that you are up and running anyway.
Thanks drs305 for the extra info. Interesting.

---

### Post by LMHmedchem on 2011-03-23
> **drs305 said:**
> G2/os-prober will import the entries from other distros (I'm pretty sure it gathers the information from the 10_linux entries). If it doesn't find the Grub folder, it will mine data and find the kernels/images and build a new menuentry.

This could be the source of the issue. The Cent install includes a /boot/grub directory, but it had nothing in it other than a splash.xpm file because I didn't install grub with Cent. Possibly os-prober didn't look far enough because the grub folder was there. In cases where a /boot/grub/grub.conf file existed and contained accurate boot information, os-prober was able to pick that up a make a valid boot entry, so that is a possible fix if someone else has the same issue. It's hard to edit a file in a root directory, so I created it in my home directory, and then used chwon to make root the owner of the file. A not about this approach is that there is nothing checking that file for changes, such as if your drive numbering changes for some reason. That would require a manual edit of those files.

It also looks like the initrd line in the menu is something important to check.

Thanks again to everyone for the help.   :KS

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by Hakunka-Matata on 2011-03-24
Official Documentation with a great index

[http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

---

