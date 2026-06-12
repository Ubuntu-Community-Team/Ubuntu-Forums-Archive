---
title: "Can't boot in ubuntu after installing windows 7, please help asap"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by himanee on 2011-01-10
hello,
 i have intel pentium dual core T4300 2.10ghz processor in dell inspiron  laptop. i had windows vista home basic by default and then i got ubuntu  9.04 installed on it from one of my friend. i was using ubuntu mostly  (and upgraded it to ubuntu 9.10)as i never liked vista. so i installed  windows 7 over windows vista. now vista is gone and windows 7 is  working. but i no more see the boot options and cant access ubuntu at  all. the boot options (F12) does not show linux partition at all.  however the linux partition is seen in device manager. but its only  seen. 
how do i retrieve my old boot options including linux os? which asks me which os to boot from.

please help me asap. i am in genuine urgency.
thanks and regards,
himanee.
 		 	 		 		 		 		  		 		 		 		 		 	 	   	  [IMG]http://static.linuxquestions.org/questions/images/icons/useragent/icon_windows_7.gif[/IMG] 		  [IMG]http://static.linuxquestions.org/questions/images/statusicon/forum_new.gif[/IMG]    		 			[[IMG]http://static.linuxquestions.org/questions/images/buttons/reputation.gif[/IMG]]("http://www.linuxquestions.org/questions/reputation.php?p=4219533") 			 		  		 		 		  	  	 	 	 		 	 	 [[IMG]http://static.linuxquestions.org/questions/images/buttons/report.gif[/IMG]]("http://www.linuxquestions.org/questions/report.php?p=4219533")

---

### Post by cgroza on 2011-01-10
Windows deleted the GRUB boot loader. You need to boot a Live CD and reinstall GRUB.
Let me google for a tutorial about it.

---

### Post by cgroza on 2011-01-10
This should do it.
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
There are plenty out there.

---

### Post by matt_symes on 2011-01-10
Hi

Have a read of the this..

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

and the section

SIMPLEST - Copy GRUB 2 Files from the LiveCD

Kind regards

---

### Post by presence1960 on 2011-01-10
It would be great if we can know which GRUB you are using, either Legacy GRUB or GRUB 2? I also hate to blindly issue solutions or commands to be run in terminal when it is a boot problem. I prefer to see your setup & boot process prior.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by himanee on 2011-01-11
thanks a lot to all,
 i am in deep trouble now :(
i loaded ubuntu 9.10 moblin remix on usb using lili usb creater. i coulden't find the exact 9.10 desktop version to create an usb.
i booted in usb device and got ubuntu destop, which is not lie one i had earlier in ubuntu 9.10(on my laptop). in this live usb i could access files in my ubuntu partition as well as windows and other partitions. i could see grub folder in boot directory. however grub folder doesnot contain menu.lst and grub.cfg file. also in terminal "sudo grub" it shows "command not found". however it let me gedit menu.lst. then i followed some link and installed grub through this live terminal and it got installed in sda5. btw, in the "fdisk -l" command it shows two linux partitions both with id 83(other than swap one). i don't know which one is booting partition and which one is actual ubuntu partition.

after that i noticed that in the boot/grub folder it is showing "grubenv" which when opened in text says "grub blocked" or something like that.

finally i got fade and decided to take some advice in person. so removed usb and intended to boot my windows 7 again. but to my agony, i am not able to access either of the systems :(
now only see a black command prompt screen where on top it says "grub 1.97~beta4"
and [minimal bash like line command prompt......]
it shows "sh:grub>" (i think it is bash:grub>
anyways, now i am totally stuck. when  i press tab whole lot of commands list is seen but i have no idea which one to use. when i do "ls", it shows all the partitions hd0,1,2,,3,4,5
when i type "ls /" it shows my linux home ie lost+found, himanee and boot directories
it lets me to set prefix and set root  but doesn't accept "vmlinuz" at all. i tried various commands but sometimes it shows some error regarding  "no kernel". 

now i am in very bad condition, even if i reboot it comes in the same prompt with grub2 screen. 
PLEEEASE HELP ME OUT.

---

### Post by Quackers on 2011-01-11
Please follow the instructions given by presence1960, one post up from yours.

---

### Post by himanee on 2011-01-11
thanks quackers and presence1960,
but i can't access internet from my comp now only thing i can see is the grub2 screen nothing else i can do. i am accessing net from other comp. i first have to come out of this command prompt/boot mode. and get back to some os. ok, i can still restart comp and pressing F12 boot from usb and go to ubuntu 9.10 moblin remix live desktop. i can't connect to net from there though.

thanks and regards

---

### Post by Quackers on 2011-01-11
Can't you boot from a live cd/usb and select "try ubuntu"?

---

### Post by himanee on 2011-01-11
i see only live mode, installer, file integrety check and memory analyze option. out of which live is default one.
 are you online? can u help me through chat? i have restarted my comp in usb drive ie in ubuntu 9.10 moblin remix.  so i can open temporary terminal in it

---

### Post by Quackers on 2011-01-11
Selcet the live mode, then you should get a live desktop which can connect to the internet. Many problems can be fixed from the live desktop.

---

### Post by himanee on 2011-01-12
thanks quackers u r responding very quickly. but i am not yet out of trouble. i downloaded ubuntu 9.10 karmic koala (which is my version) desktop live cd and burned it onto a dvd. if i run it on other comp it runs correctly but when i try to boot it from my comp it does not boot and grub screen is back. when i start booting in dvd, it makes a familiar noise of loading cd/dvd and in a second say grub loading.
i just want to get out of this grub

it still recognizes and takes me to moblin live, which is on a pendrive. but i can't find karmic koala desktop version to create usb.

please please help.

---

### Post by Quackers on 2011-01-12
So let's get some things straight first.
You had vista and over-wrote that with Win 7, which was working.
You then installed Ubuntu 9.04, with which you had a problem? so over-wrote that with 9.10.
Now nothing boots and you've made a 9.10 live cd and it doesn't boot either?
How did you install 9.04 and 9.10 without cd's or usb's?

Please also give details of your computer's graphics card.

---

### Post by himanee on 2011-01-12
NO, here is the chronological developments.
 
 1. i had vista then i got ubuntu 9.04 with partitioning done by my friend. 
 
 2. afterwords, i upgraded it to ubuntu 9.10 karmik koala, 
 
 3. then a few days ago i installed windows 7 in the partition of vista. grub was gone so no access to karmik. 
 
 4. then i created usb with ubuntu moblin 9.10 on it. because i didn't  have cd/dvd readily available and had usb. i created it using lili usb  creater from the site pendrivelinux.com. i could not find usb creater to  make karmik live on usb.
 
 5. i booted in moblin could access terminal but "sudo grub" says  "command not found". i found from files folder that boot/grub directory  does not contain either of menu.lst and grub.cfg. i installed grub on  sda5 which is my linux partition. it successfully installed. 
 
 6. now the comp boots in either grub mode or in moblin on usb. it does  not recognize cd/dvd which has ubuntu karmic. the dvd with karmic runs  well on the other comp.
 
 7. i can't access internet in moblin on usb.
 
 8. in grub mode it does not recognize "vmlinuz" command. it sets prefix  and root correctly. but grub folder doesnot have menu.lst and grub.cfg.  it has grubenv file which when opened in text says grub something is  blocked (sorry i don't remember the exact line).
  
 8. i have windows 7 cd but don't have any proper cd/dvd for linux systems.

9. i have intel pentium dual core T4300 2.10 ghz processor. i ran "lspci  -v" command.but it gives whole lot of output and i don't know what to  tell you out of it.

 thanks and please take me out of this grub mode.

---

### Post by Quackers on 2011-01-12
So reading back over the thread it seems that you have a 9.10 dvd that you've installed Ubuntu on a different pc with? That dvd only gets to the "try ubuntu" "install ubuntu" screen, then it goes black?
Is that right?
This could possibly be a video card problem - maybe. That's why I asked about your graphics card.
And what is moblin?

---

### Post by himanee on 2011-01-12
NO. 
when i restart my comp and boot with usb which has moblin it boots from it and i can access live moblin. i can probably install moblin, but i don't want it.

BUT, when i try to boot it from dvd with ubuntu karmic, it just blinks and "loading grub" and back to grub black screen.

---

### Post by Quackers on 2011-01-12
But you can't connect to the internet from the moblin live usb desktop?

---

### Post by himanee on 2011-01-12
yes. that is a big problem.

---

### Post by Quackers on 2011-01-12
It is indeed.
What we need to do is to re-install grub. To do that we need to know what hard drive and what partition number your Ubuntu /root is in. Once we find that out we need to run a live cd/usb desktop so that the commands can be put into the terminal to put grub back where it should be.
The bottom line is that you need to get a working live cd or usb with 9.10 on it. Another method may be possible, but I don't know of it :-(

I would suggest that you visit the Ubuntu website and download the 9.10 desktop edition .iso and burn the image (NOT the files) to dvd, then try this again.

Sorry, but that's all I can think of.

---

### Post by Quackers on 2011-01-12
Another option would be to download version 10.04 and make a live cd or usb, then boot that and find out what's where. Then you can backup anything you need to backup and then you could install 10.04 over the top of whatever Ubuntu installs are currently present.
That might be best.

---

### Post by himanee on 2011-01-13
thank god. a good news i could somehow make an bootable usb for ubuntu 9.10 karmik koala. and the better part is i can access internet. right now i am posting this from my comp, through live ubuntu. now i have also downloaded boot info script. can you please elaborate me once again what to do next. so that no mistaks are done again. i am afraid to get that black grub screen.
i didnot get that "#" part in presence1960's post.

btw, "sudo grub" is not recognized in this terminal also. this live system is the same as mine. so i am happy to see the all familiar format unlike moblin.

one more thing, filesystem contains /boot/grub directory. but grub directory contains only one file namely grubenv and in the text editer it shows;
# GRUB Environment Block
########################################################

---

### Post by Quackers on 2011-01-13
If the boot script is on your desktop run in the terminal
```
sudo bash ~/Desktop/boot_info_script*.sh
```
If it's not copy/paste it there first.
When the results.txt file appears on your desktop open the file and copy all of its contents then in your next reply just type [code ] (without the space before ] ) and paste the contents of the file, then type [/code] and your post will appear in code tags.

---

### Post by himanee on 2011-01-13
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   419,432,447   209,715,200   7 HPFS/NTFS
/dev/sda3         419,441,085   458,495,099    39,054,015  83 Linux
/dev/sda4         458,495,100   625,137,344   166,642,245   5 Extended
/dev/sda5         458,495,163   613,409,894   154,914,732  83 Linux
/dev/sda6         613,409,958   625,137,344    11,727,387  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4009 MB, 4009754624 bytes
51 heads, 51 sectors/track, 3010 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          1,144     7,831,551     7,830,408   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0E5CA3A95CA38A53                       ntfs                                     
/dev/sda2        BE527F78527F346D                       ntfs       D                             
/dev/sda3        ab025bdf-78d5-42f2-9762-731a99d17543   ext3                                     
/dev/sda5        7d5d55d9-2c26-4820-8085-f03cf084aedb   ext3                                     
/dev/sda6        0158b031-6ada-4da5-a6a5-60f9a7570eee   swap                                     
/dev/sdc1        3433-3231                              vfat       HIMANEEAPTE                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda3/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ab025bdf-78d5-42f2-9762-731a99d17543

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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ab025bdf-78d5-42f2-9762-731a99d17543 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        ab025bdf-78d5-42f2-9762-731a99d17543
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


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=ab025bdf-78d5-42f2-9762-731a99d17543 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7d5d55d9-2c26-4820-8085-f03cf084aedb /home           ext3    relatime        0       2
# swap was on /dev/sda6 during installation
UUID=0158b031-6ada-4da5-a6a5-60f9a7570eee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 225.8GB: boot/grub/menu.lst
 225.7GB: boot/grub/stage2
 215.7GB: boot/initrd.img-2.6.28-11-generic
 225.1GB: boot/initrd.img-2.6.28-15-generic
 215.7GB: boot/initrd.img-2.6.31-22-generic
 215.7GB: boot/vmlinuz-2.6.28-11-generic
 224.5GB: boot/vmlinuz-2.6.28-15-generic
 215.8GB: boot/vmlinuz-2.6.31-22-generic
 215.7GB: initrd.img
 225.1GB: initrd.img.old
 215.8GB: vmlinuz
 224.5GB: vmlinuz.old

=================== sda5: Location of files loaded by Grub: ===================


 245.2GB: boot/grub/core.img
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by himanee on 2011-01-13
now what?
btw, "sudo grub" is not recognized in this terminal also. this live system is the same as mine. so i am happy to see the all familiar format unlike moblin.

one more thing, filesystem contains /boot/grub directory. but grub directory contains only one file namely grubenv and in the text editer it shows;
# GRUB Environment Block
##################################################  ######

---

### Post by himanee on 2011-01-13
i am waiting. what am i supposed to do next?

---

### Post by Quackers on 2011-01-13
Your Windows partition looks good :-)
You have grub2 installed in the mbr of sda (your hard drive), but you have Grub legacy files in sda3 (your Ubuntu 9.10 partition), but for some reason one of Ubuntu's boot files is in sda5 (your /home partition, I believe).
What I would suggest is to purge and re-install grub2, following drs305's guide below, using the Full chroot procedure.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Have a look at the chroot section of that guide and get a feel for what you need to do. Take your time. Any questions come back and you will get assistance. Sadly I am going out shortly, but many people here can help you.
I will write out the first few commands for you, then refer you to the rest of that guide.

---

### Post by Quackers on 2011-01-13
Be patient! These things take time :-)
From your live cd/usb desktop after making sure you are connected to the internet, open a terminal and copy/paste ALL of these lines in ONE AT A TIME, then press enter after each line
```
sudo mkdir /mnt/temp
sudo mount /dev/sda3 /mnt/temp
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
sudo chroot /mnt/temp

```
At this point your terminal prompt should change from ubuntu@ubuntu to root@ubuntu

Then please follow instructions 2 to 8 in the chroot section of the guide below

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by himanee on 2011-01-13
ok. thanks again. i read most of the part from the link you sent to me. to follow it i need to know whether i have separate boot partition for linux or not and if yes, which one is that. how do i know this?

---

### Post by Quackers on 2011-01-13
You have no separate /boot partition.
See post above - and take care :-)
Any problems, come back.

---

### Post by himanee on 2011-01-13
the trouble is not yet gone :(
i followed the exact instructions and got the output also same as mentioned. then as instructed i was supposed to reboot. but i had some imp personal work so i shut down my comp and started a few min back. but now i am not able to connect internet. earlier also, to connect internet the computer instructed me to install something and the i got connected to internet. i did the same but when i press password the computer goes blank. meaning a gray screen without prompt or anything. i tried restarting comp many a times. once it got connected neatly but when i opened firefox it got hung. 

also, when checked from files. my linux partition still does not contain menu.lst and grub.cfg file in grub folder and that grubenv is present. however there is some 20gb partition in which both the files are there in grub folder.
has my comp got corrupted due to repeated restarting? :( :(

---

### Post by Quackers on 2011-01-13
You're not making yourself clear to me.
Does the machine boot anything now? If so what? Do you see a grub menu? Give us a clue.

---

### Post by himanee on 2011-01-13
hi. sorry i was away. now here is the current situation.
1. i can boot in usb with karmik. however i am not able to connect to internet. do i need it anyway? when i try to connect internet the comp goes blank or shuts off.

2.  in the terminal "sudo grub" says "command not found"

3. in the filesystem, in my normal linux partition /boot/grub folder does not contain grub.cfg and menu.lst files. however, in some other partition of size 20gb i can see those files in /boot/grub folder.

now what should i do next?

---

### Post by Quackers on 2011-01-13
So if you take the Karmic cd out of the drive and try to boot the computer what happens?
You should now be using grub2, so menu.lst should be empty now, because it is not used by grub2.
Sudo grub is not a command - and as stated previously, "sudo update-grub" will not work from a live cd environment. It is used from a normal Ubuntu desktop.

---

### Post by himanee on 2011-01-13
when i boot comp without live cd it goes back to that grub2 screen mode

menu.lst and grub.cfg are not present in grub folder in my ubuntu partition. but grubenv is still there.

menu.lst and grub.cfg both are present in grub folder in some other partition (which is what i don't know. you might know as you know all my partitions.)

---

### Post by Quackers on 2011-01-13
If you can't boot Ubuntu, then something went wrong when you re-installed grub, I would say.
Please re-run the boot script so that we can see what has changed. Thanks.

---

### Post by himanee on 2011-01-13
Hey, GOOD NEWS. how and why i don't know. but all of a sudden, everything is working well. my ubuntu n windows booting nicely. back to normal.

thank a lot for your help.

---

### Post by Quackers on 2011-01-13
Lol, you're welcome :-)
Maybe divine intervention :-)

---

