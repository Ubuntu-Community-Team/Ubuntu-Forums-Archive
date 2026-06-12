---
title: "SUCCESS - Breezy loaded on external USB drive !"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2005-10-23
**[COLOR=red][B][COLOR=red]Newsflash[/COLOR]** ... [COLOR=seagreen]INSTALLING FIESTY (7.04) is possible using some changes to this tutorial[/COLOR] !!![/COLOR][/B][COLOR=red]
**[COLOR=dimgray]( Kudos to "el_dorado" for sharing his success [COLOR=darkslategray]in post #502[/COLOR]. )[/COLOR]**
 
[/COLOR]**[COLOR=red]Newsflash[/COLOR]** ... [COLOR=seagreen]UPGRADING from a BREEZY USB install to DAPPER is possible[/COLOR] !!!
( Kudos to "Killeroid" for sharing his success in [this post]("http://www.ubuntuforums.org/showpost.php?p=971692&postcount=383"). )
 
 
Hi Folks,
 
Since my first post on this topic, I have learned quite a bunch about the UBUNTU install process ... and managed to successfully load UBUNTU a number of times on my external USB drive. (Call me crazy, but I wanted to run the install a few times to make sure that what I was doing would work every time.)
 
I would like to share my updated outline with others who may also be struggling with this process.
 
**BACKGROUND**: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up initially as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a [Seagate 40GB Portable External Hard Drive]("http://www.walmart.com/catalog/product.do?product_id=3910242") that was purchased at Walmart for around $120
 
**REQUIREMENTS**: Make sure you have your bios set to boot the CDROM first and then the USB device, or you will have problems down in step 4. (Kudos to "joess" for pointing out my omission!)
 
*pre-install tip*: If you feel comfortable performing one of the suggestions in [post #141]("http://www.ubuntuforums.org/showpost.php?p=669047&postcount=141") then it should make the installation to the external drive (especially tip 2) run smoother. (Kudos to "Sephatine" for suggesting this.)
 
**IMPORTANT**: Don't forget that Linux is case sensitive on everything, including file and directory names. (There is a difference between an uppercase and a lowercase letter.) *Example*: According to Linux, a file named "DaBruGo" and a file named "dabrugo" are considered two completely different files.
 
 
 
**Here is what I do to successfully load UBUNTU v5.10 on my EXTERNAL USB DRIVE ...**
 
 
**( STEP 1 )** Instead of using "expert" mode to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).
 
*INSTALL NOTE*: The installation process will ask you for some information when it starts up ...
 
first it will ask for your language,
then your (language) location,
then your keyboard type,
then it will detect your cdrom(s),
then it will attempt to detect your network configuration,
then it will ask you to give your PC a name (hostname),
then it detects hardware and starts up the partition phase of the install.
 
*INSTALL NOTE*: When you get to STEP 2 (the partition phase), there is a simple way to determine how the install program assigns device names to your hard drive(s). Before starting any partitioning activity in STEP 2, choose the GO BACK option in the lower left corner of this screen and then choose EXECUTE A SHELL farther down in the Ubuntu installer menu that appears. Choose CONTINUE at the next prompt. In the shell window that appears, type in fdisk -l (that is FDISK -L in all lowercase). This will give you a list of all the storage devices the installer program sees. Make a note of the device names (/dev/hd? or /dev/sd?) and then type in exit to return to the partition phase (STEP 2) of the install. (Kudos to "RyanGT" for suggesting this in post #257.)
 
**( STEP 2 )** During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning ... which sets up an ext2 or ext3 partition and a swap partition for you.)
 
*INSTALL NOTE*: Look for the line during the partitioning phase that might say ... erase entire disk SCSI (0,0,0) (sda). Be careful here as some people have had problems when choosing any partitioning options that include the text "and use LVM" (Kudos to "brucetan" for sharing this in post #268.)
 
Feel like learning about LVM anyway? Check this [link]("http://www.ubuntuforums.org/showthread.php?t=141900") out. (Kudos to "SD-Plissken" for sharing this info.)
 
*BE VERY CAREFUL* on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!
 
Once again ... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!
 
**( STEP 3 )** When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.
 
The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the SDA (external USB) drive where we want to install the GRUB bootloader.
(Mine was /dev/sda [NOT sda1] ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: I loaded GRUB to sda (the bootsector of the external drive) and NOT to sda1 (which would be the first partition on the external drive). 
 
*INSTALL NOTE*: at this point, the install program loads some stuff and ejects the CD ... wanting you to do a reboot.
 
**( STEP 4 )** BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode) ( Review REQUIREMENTS at the beginning of this guide! )
 
Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.
 
**( STEP 5 )** When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your external drive from the list.
(Mine was mount /dev/discs/disc1/part1 ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: /dev/discs mount points start with disc0 (with 0 meaning the first drive in a system). So, my mount point of /dev/discs/disc1/part1 was really the second disk [disc1] (the sda drive we are working with) and the first partition [part1] on that disk. 
 
**( STEP 6 )** When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.
 
**( STEP 7 )** Type in these lines before we start editing out files ...
 
mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>
 
*INSTALL NOTE*: I used vim to edit the files. (There is a great [vim cheatsheet]("http://www.tjl2.com/sysadmin/vim_cheatsheet.pdf") in pdf format available from "TimL".) It is weird to use at first until you learn what a few keys do in it. The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ... And hitting : x <enter> saves the file and exits out of vim. (IMPORTANT TIP ... that's a colon and a lowercase x with NO SPACE between the colon and the x) 
 
**( STEP 8 )** Run vim to edit the modules file to make sure USB support is added/loaded during UBUNTU startup ...
 
vim /etc/mkinitramfs/modules <enter>
 
Right below the last line of text, enter these lines ...
 
ehci-hcd
usb-storage
scsi_mod
sd_mod
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Some PCs may need a more comprehensive list added here. Please take a look at [post #181]("http://ubuntuforums.org/showpost.php?p=705797&postcount=181") or [post #406]("http://www.ubuntuforums.org/showpost.php?p=1100888&postcount=406") if you are having startup issues after these edits. (Kudos to "brotorious" for his efforts on this, and to "Jonathan.Martin" for posting his successful resolution to the problem as well.)
 
**( STEP 9 )** Run vim to edit the initramfs.conf file to make sure enough time elapses for USB support to load before UBUNTU gets running ...
 
vim /etc/mkinitramfs/initramfs.conf
 
At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up ...
 
WAIT=12 (in all caps here, not sure if necessary though)
 
Be sure to save the file changes (using : x)
 
*INSTALL NOTE*: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.
 
**( STEP 10 )** Recompile (recreate) the initrd.img file to include USB support from these edited files ...
 
mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
 
*INSTALL NOTE*: When you are done with the previous step #9 (and before performing this step), you can run the "ls /lib/modules" command (without the quote marks) from a terminal window to see what kernel version number you should use for this install step. They may be using a kernel version higher than 2.6.12-9-386 that was available when I originally created this help guide. (Kudos to "Saxegaard" for bringing this to my attention in [post #235.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=754862&postcount=235"))
 
**( STEP 11 )** Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...
 
vim /boot/grub/menu.lst
 
Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).
 
There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 
 
*INSTALL NOTE*: You will also want to change a "# groot" line in a section of your menu.lst file that may look something like this ...
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) <<< CHANGE THIS LINE TO READ # groot=(hd0,0)
(Kudos to "archis" for his excellent documentation of this farther down in [post #227.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=749354&postcount=227"))
 
*INSTALL NOTE*: You may want to change the root line for the Windows XP section in this file to (hd1,0) just in case you have XP loaded on an internal drive and want the option to boot into XP from the GRUB menu. (See post #2 for more info.) You may have to edit this section whenever you update your kernel version. If you have problems pulling up XP after a kernel update, check this section of your menu.lst file to see if you need to edit it again.
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Feel more comfortable editing this file in Windows? See [post #171]("http://ubuntuforums.org/showpost.php?p=692413&postcount=171") for a program that will let you edit files on linux partitions from within Windows. (Kudos to "mickola" for the suggestion.)
 
**( STEP 12 )** Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.
 
BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS
 
**( STEP 13 )** After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU
 
 
That's the process I've successfully used to install UBUNTU v5.10 on an external USB drive. I hope this helps anyone whose been wrestling with this process. Let me know if it works out for you.
 
DAVE
 
 
 
**OTHER PROBLEMS AND POTENTIAL FIXES** ...
 
* Booting Ubuntu from Windows XP without loading GRUB to the MBR ...
[http://www.ubuntuforums.org/showthread.php?t=56723](http://www.ubuntuforums.org/showthread.php?t=56723)
(Kudos to "celticmonkey" for documenting this.)
 
* Problems booting XP from an internal drive ...
[( message #2 )]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") + [( message #203 )]("http://ubuntuforums.org/showpost.php?p=723454&postcount=203")
 
* Problems starting UBUNTU after a kernel update using Ubuntu's automatic update app ...
[( message #112 )]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112") + [( message #161 )]("http://www.ubuntuforums.org/showpost.php?p=686867&postcount=161")
 
* Using Windows XP to format drives larger than 32GB AS FAT32 ...
[( message #188 )]("http://www.ubuntuforums.org/showpost.php?p=715722&postcount=188")
 
* Re-installing GRUB in a relatively painless manner ...
[( message #205 )]("http://ubuntuforums.org/showpost.php?p=723618&postcount=205") (Kudos to "RyanGT" for hunting this down.)
 
* Creating a bootable GRUB CD (sketchy details but seems to make sense) ...
[( message #207 )]("http://ubuntuforums.org/showpost.php?p=723735&postcount=207") + [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html](http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html)
 
**REFERENCE MATERIALS** ...
 
* GRUB Manual (section 14.3 shows what error codes mean)
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by DaBruGo on 2005-10-25
Hi Folks,

Some people have had problems getting Windows XP to boot from GRUB.

By putting these lines in the menu.lst file (/boot/grub/menu.lst) that GRUB uses, I was able to get XP to boot properly from the GRUB menu on my home PC (that has just one partition on it) ...

title Windows XP Professional
root (hd1,0)
map (hd1) (hd0)
chainloader +1

*INSTALL NOTE*: I installed GRUB (and UBUNTU) to my external USB hard drive during installation and NOT to my internal hard drive (where XP is loaded).

*COMMENT*: If you have A DELL or COMPAQ computer, you may want to read [( message #203 )]("http://ubuntuforums.org/showpost.php?p=723454&postcount=203") for a possible change to the root line listed above (Kudos to "srirampcl" for sharing this.)

EXAMPLE: My PC at work is a Dell Optiplex model and the internal hard drive has two partitions on it.

* The first partition (hd0,0 which should be seen as hd1,0 to GRUB since we loaded it to the external drive and NOT the internal drive) is a Dell utility partition that the factory uses for new PC setups.

* The second partition (hd0,1 which should be seen as hd1,1 to GRUB since we loaded it to the external drive and NOT the internal drive) actually has Windows XP loaded on it.

* So for this example, my root line above should read as "root (hd1,1)" to correctly find and boot XP from the GRUB menu.


See the second *INSTALL NOTE* of **STEP 1** in the first post of this thread to find out how your internal hard drive may be partitioned.



Hope this helps,
DAVE

---

### Post by CrunchyDoodle on 2005-10-27
Excellent procedure. Better than the one I came up with. 

I decided to try your method after I got tired trying to get past this weird networking problem where DNS stops working for no good reason and reinstall ubuntu.

Bye.    :cool:

---

### Post by javier.blazquez on 2005-10-30
I followed your directions and was finally able to install Ubuntu 5.10 Server on a 512MB USB stick plugged into a VIA EPIA MII motherboard.

Thank you very much.

---

### Post by moonlord on 2005-10-30
I've been trying to get Breezy boot from my external harddrive last night.
Unfortunately it doesn't work yet, even though I followed your step by step tutorial.
Grub always hangs with just saying "Grub " on the screen during the reboot. So my laptop finds the harddrive, it just can't get grub to work properly somehow :(
Any ideas what could be wrong here?

---

### Post by DaBruGo on 2005-11-01
[QUOTE=javier.blazquez]I followed your directions and was finally able to install Ubuntu 5.10 Server on a 512MB USB stick plugged into a VIA EPIA MII motherboard.

Thank you very much.[/QUOTE]

hey javier,

Would you mind sharing the outline you used to get Ubuntu loaded on your USB stick? Is it different from my outline?

I have a 1GB flash stick and I was wondering what type of install you used and what applications you chose for the install. 

I have another thread going where I'm tryin to get help with installing the Live CD onto a USB flash stick as well.



Any help from you would be much appreciated.

DAVE

---

### Post by DaBruGo on 2005-11-01
[QUOTE=moonlord]I've been trying to get Breezy boot from my external harddrive last night.
Unfortunately it doesn't work yet, even though I followed your step by step tutorial.
Grub always hangs with just saying "Grub " on the screen during the reboot. So my laptop finds the harddrive, it just can't get grub to work properly somehow :(
Any ideas what could be wrong here?[/QUOTE]

moonlord,

Is there any way you could post your menu.lst file that grub uses during startup. That may be the problem. I'll be more than happy to take a look at it for ya.


DAVE

---

### Post by moonlord on 2005-11-01
I'll try to get my menu.lst. Do you know any method to access an ext3 from windows?
Btw, I changed the hd(0,0) to hd(1,0) like you explained and therefore I think there shouldn't be any differences. Or do you know where the problem could also lie?

What made me wonder was the device.map in the grub folder because it says
(hd0)  /dev/hda and (hd1)  /dev/sda  shouldn't it be the other way round?

Also I wondered why you use WAIT=12 where others used DELAY in other tutorials? Any differences in that?

Another thing: the initramfs.conf says at the end Resume=/dev/sda5 but I thought sda5 is my swap partition?

any help is appreciated. Thanks :)

---

### Post by moonlord on 2005-11-01
ok, just found a great tool called EXT2 IFS which adds ext2 and 3 support to windows xp :)

so here is my menu.lst:

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.12-9-386 
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
chainloader    +1

```

---

### Post by Kyral on 2005-11-01
I'm curious, whats the performance like?

At any rate, ***very*** good job.

---

### Post by DaBruGo on 2005-11-02
[QUOTE=moonlord]I'll try to get my menu.lst. Do you know any method to access an ext3 from windows?
Btw, I changed the hd(0,0) to hd(1,0) like you explained and therefore I think there shouldn't be any differences. Or do you know where the problem could also lie?

What made me wonder was the device.map in the grub folder because it says
(hd0)  /dev/hda and (hd1)  /dev/sda  shouldn't it be the other way round?

Also I wondered why you use WAIT=12 where others used DELAY in other tutorials? Any differences in that?

Another thing: the initramfs.conf says at the end Resume=/dev/sda5 but I thought sda5 is my swap partition?

any help is appreciated. Thanks :)[/QUOTE]


moonlord,

I would tend to agree that the device.map should be the other way around. But, I am not 100% sure. Supposedly, the (hd0) device should be the one where the grub bootloader was loaded. But, I will have to see what mine looks like.

As far as the WAIT command ... In Ubuntu versions before Breezy (5.10), I think they used the mkinitrd command to recreate/recompile the kernel and that is why the DELAY parameter was used in the config file. But in Breezy, we use mkinitramfs to do this and the WAIT parameter is what works with it.

As far as the initramfs.conf file ... I am not sure what the RESUME line is. I will look at my initramfs.conf file and see if there is a difference.


DAVE

---

### Post by moonlord on 2005-11-02
the problem is, after changing the device.map just now didn't make any difference :(
GRUB still only shows "Grub "
At least it means my harddrive is able to boot, so it shouldn't be a problem with my laptop...

thanks for clearing up why you used the WAIT command :)

btw, i found out, that resume shows which partition used to read data after suspend modes...

so, any more ideas what I could do??
I'm almost ready to just install it on my internal harddrive if I can't find out how to boot from the external drive soon :(

---

### Post by SuperSizeMe on 2005-11-02
> (2) During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning... Which sets up an ext2 or ext3 partition and a swap partition for you.)

NOTE: Look for the line during the partitioning phase that might say...
erase entire disk SCSI (0,0,0) (sda)

BE VERY CAREFUL on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!

Once again... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!

I notice that during the install process Ubuntu formats the external drive, is there any way around this as I have important information in this drive that I can't afford to delete.

I have an external USB MAXtor 250GB drive, of which 135 GB are used.  Any ideas??

SSMe

---

### Post by moonlord on 2005-11-02
you could resize the partition of your external drive with partition magic and add one ext3 partition for ubuntu and one swap partition. then you won't have
to format the drive at all

---

### Post by bluemerle27 on 2005-11-03
I folllowed the procedure you outlined and it worked very well and now installed sucsessfully onto an external hard drive so thank you very much.
A question, my motherboard allows for booting from usb drive but if I take this external hard drive on the road and plug it into a computer that does not allow booting from an USB hard drive - would it be possible to create a floppy disk or a boot cd that would enable you to access the external hard drive and my installation of ubuntu from a computer that has no ability to boot from USB.

the Second part of this question is that might it be possible to use original install disk and the rescue mode to access USB drive. Unfortunatly I have no way to test this as my motherboard supports USB booting very well.

Any advice, help would be apreciated.

Thanks

---

### Post by blixa on 2005-11-04
moonlord - I had the same problem - only booting up and stopping at the grub prompt.

I decided to try to type in the grub commands one at a time (ie. the ones listed in menu.lst for the ubuntu entry) manually to see what would happen.  I eventually got an error messgae saying something like "USB volume too large for BIOS".  I have a 30G USB drive and it is all partitioned for ubuntu.  I don't know if it's right, but I think my BIOS can't handle booting partitions of a certain size or crossing a certain boundary in the drive.

So I repartitioned the drive - putting a 10G ext3, followed by a small swap, and then with a FAT32 for the rest.  I reinstalled - and it works.  I might have also worked if I kept the drive all ext3 and had a small /boot partition at the start of the disk.

I don't know if this will help you out.  But I thought I'd let you know how I got it to work.

blixa

---

### Post by moonlord on 2005-11-05
thanks blixa,
i`ll try reformatting my drive tomorrow. because it is an 80 gig harddrive it could actually mean that you're right.
just gotta go to bed now after this night of partying ;)
need to be sober when fiddeling around with linux...

---

### Post by RyanGT on 2005-11-07
Does anyone running Ubuntu off a USB harddrive have hibernation working?  I would really like to be able to hibernate.

Ryan

---

### Post by DaBruGo on 2005-11-11
[QUOTE=RyanGT]Does anyone running Ubuntu off a USB harddrive have hibernation working?  I would really like to be able to hibernate.

Ryan[/QUOTE]

Ryan,

I don't know if this helps, but here is a link ...

[http://ubuntuforums.org/showthread.php?t=75443&highlight=hibernate](http://ubuntuforums.org/showthread.php?t=75443&highlight=hibernate)



DAVE

---

### Post by DaBruGo on 2005-11-11
[QUOTE=moonlord]thanks blixa,
i`ll try reformatting my drive tomorrow. because it is an 80 gig harddrive it could actually mean that you're right.
just gotta go to bed now after this night of partying ;)
need to be sober when fiddeling around with linux...[/QUOTE]

moonlord,

Did you get your hard drive issue resolved?



DAVE

---

### Post by DaBruGo on 2005-11-11
[QUOTE=SuperSizeMe]I notice that during the install process Ubuntu formats the external drive, is there any way around this as I have important information in this drive that I can't afford to delete.

I have an external USB MAXtor 250GB drive, of which 135 GB are used.  Any ideas??

SSMe[/QUOTE]

super,

I don't know if this helps, but here is a link ...

[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)



DAVE

---

### Post by Matze on 2005-11-12
Hi Dave and all others here,

first of all:
Hi @ all here, because i'm new in this forum!

Second my problem ;-)
I've the same problem as moonlord, the only thing what happens on boot is GRUB stands on the screen and nothing happens anymore :-(

I've done exact what you've written before (at least i think so...)

Here are my edited files:

/boot/grub/menu.lst

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
```

/etc/mkinitramfs/modules

```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod

```

/etc/mkinitramfs/initramfs.conf

```
WAIT=12
#
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#
MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  The command line will override this setting.

RESUME=/dev/sda5


```

Thanks for any help and greetings from germany,

Matze

---

### Post by DaBruGo on 2005-11-13
matze,

I noticed something in your grub file that is different from mine.
My kernel number doesn't end with -686 like yours.
Mine is ... 2.6.12-9-386 (and not -686)

If you can get to a terminal window, this command will tell you what your kernel version number is ...

ls /lib/modules


Check that and if it is different, you may want to boot into rescue mode and recompile your kernel (with the mkinitramfs command) using the correct kernel number. Then make sure the kernel number is also correct in your grub config file.

Maybe that is the problem that you and moonlord are having.


DAVE

---

### Post by Matze on 2005-11-14
Hi,

no, that isn't the problem...i tried it with the -386 also...:(
-686 is for my laptop with an Intel Cenrino in it...

Greets!

---

### Post by TheChad on 2005-11-14
Can you move that drive from one comp to another, like a live cd?

---

### Post by DaBruGo on 2005-11-14
[QUOTE=TheChad]Can you move that drive from one comp to another, like a live cd?[/QUOTE]

chad,


If you have an external USB hard drive, you could connect it to another PC.

But ... you would have to run a number of setup files again to detect the hardware on every other PC you connect it to (at least that is what I had to do for xserver video settings).

Plus ... I don't believe it remembers each PC's hardware settings (or auto-detects it like the Live CD does) ... but I could be wrong on that.



DAVE

---

### Post by carlosatbcn on 2005-11-15
Hi!
great procedure. I found some similar and it works for me.
I have breezy installed in an external 30GB HD
The first start was ok.

But I found a problem!

The USB devices have to be conected in the same order. If I add an usb device or I change the ports where the devices are connected, then linux asigns  devices sda sdb... etc in a different way compared to the assignations existing during the installation.

If I install in sda, and I connecta another drive, maybe the new drive will be sda... or in the worst case it depends on the order of the BIOS to find the usb devices.

Any idea to have always the same sd* for each device?

Thanks

---

### Post by Zerocool10482 on 2005-11-15
I'm thinking of doing that with my Ipod. I'm like the gtkpod. It's alittle better to work with than Itunes.

---

### Post by daibak on 2005-11-16
Dave and other successful Breezy installers on this forum,

Am impressed how many folks here got Ubuntu 5.10 up and running dual-boot.

Question is about my mostly-docked notebook's external 160 GB Seagate drive ST316002 using on-board notebook Firewire port -- USB 2.0 possible through my PCMCIA Cardbus but that will screw up my WinXP setup. The external, second disk always shows up in [!!] Partition Disks phase as SCSI3 (0,0,0) (sda) but I've never managed to boot to Ubuntu. Running a Live CD session shows /media/ieee1394disk/...(path) and all looks good but no boot loader works as none installed. LILO never takes during Breezy install, only GRUB to new Ubuntu partition. Tried GAG 4.5d floppy too but it doesn't see any partitions on the external Seagate, only on the Windows IDE /dev/hda.

I've tried, believe me. First attempt was a disaster and had to HP Factory Software re-install Windows XP HE. At least now I know not to let GRUB loader install on the Windows C: root drive MBR after re-partitioning!

Will Dave's how-to below work for this Firewire-connected Seagate, or only USB? If yes, I'll wipe the Seagate clean and try again with this step by step.

[QUOTE=DaBruGo]Hi Folks,

Since my first post on this topic a few days ago, I have learned quite a bunch about the UBUNTU install process ... and managed to successfully load UBUNTU a number of times on my external USB drive. (Call me crazy, but I wanted to run the install a few times to make sure that what I was doing would work every time.)

I would like to share my updated outline with others who may also be struggling with this process.

BACKGROUND: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a Seagate 40GB Portable External Hard Drive that was purchased at Walmart for around $120

Here is what I now do to successfully load UBUNTU v5.10 on this EXTERNAL USB DRIVE ...

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

NOTE: I used vim to edit the files. It is weird to use at first until you learn what a few keys do in it ... The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ...  And hitting : x (colon x) saves the file and exits out of vim.

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

WAIT=12  (in all caps here, not sure if necessary though)

Be sure to save the file changes (using : x)

NOTE: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.

(10) Recompile (recreate) the initrd.img file to include USB support from these edited files ...

mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386

(11) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst

Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 

NOTE: You may want to change the root line for the Windows XP section to (hd1,0)  just in case you want to boot XP from this menu.

Be sure to save the file changes (using : x)

(12) Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.

BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS

(13) After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU


That's the process I've successfully used to install UBUNTU v5.10 on an external USB drive. I hope this helps anyone whose been wrestling with this process. Let me know if it works out for you.

DAVE[/QUOTE]

---

### Post by DaBruGo on 2005-11-16
[QUOTE=daibak]Dave and other successful Breezy installers on this forum,

Am impressed how many folks here got Ubuntu 5.10 up and running dual-boot.

Question is about my mostly-docked notebook's external 160 GB Seagate drive ST316002 using on-board notebook Firewire port -- USB 2.0 possible through my PCMCIA Cardbus but that will screw up my WinXP setup. The external, second disk always shows up in [!!] Partition Disks phase as SCSI3 (0,0,0) (sda) but I've never managed to boot to Ubuntu. Running a Live CD session shows /media/ieee1394disk/...(path) and all looks good but no boot loader works as none installed. LILO never takes during Breezy install, only GRUB to new Ubuntu partition. Tried GAG 4.5d floppy too but it doesn't see any partitions on the external Seagate, only on the Windows IDE /dev/hda.

I've tried, believe me. First attempt was a disaster and had to HP Factory Software re-install Windows XP HE. At least now I know not to let GRUB loader install on the Windows C: root drive MBR after re-partitioning!

Will Dave's how-to below work for this Firewire-connected Seagate, or only USB? If yes, I'll wipe the Seagate clean and try again with this step by step.[/QUOTE]


daibak,

In theory ... all you should need to do is find out what firewire modules you need to add to Step ( 8 ) and then maybe increase the WAIT time in Step ( 9 ) then be sure to do Step ( 10 ) to add the module support to the kernel.

Also, I believe there is a linux command that will tell you what modules are loaded. Maybe you can run it on a Live CD session to see what firewire modules it is autoloading.

I hope it works for you. Maybe some of the other folks in here can add some of their firewire experiences.



DAVE

---

### Post by joess on 2005-11-17
I am also trying to install UBUNTU v5.10 on a USB external HD. But need some additional help. I can install 5.10 and the GRUB to the USB drive OK. I tried following your instructions but when the system reboots I cannot type in the command "rescue" (unknown command). My USB drive is listed as "sdb" & the internal HD as "sda" I have the USB drive set to 1st boot in the BIOS.

I am just a little confused as to the commands in steps 4-13. I understand why you are doing this. What is "vim"? Just a little more precise help for a layman would be helpful.

Thanks

---

### Post by DaBruGo on 2005-11-17
[QUOTE=joess]I am also trying to install UBUNTU v5.10 on a USB external HD. But need some additional help. I can install 5.10 and the GRUB to the USB drive OK. I tried following your instructions but when the system reboots I cannot type in the command "rescue" (unknown command). My USB drive is listed as "sdb" & the internal HD as "sda" I have the USB drive set to 1st boot in the BIOS.

I am just a little confused as to the commands in steps 4-13. I understand why you are doing this. What is "vim"? Just a little more precise help for a layman would be helpful.

Thanks[/QUOTE]

hi joess,

When you are at step ( 4 ) are you leaving the INSTALL CD in the cdrom drive? We do this because we have to run UBUNTU in rescue mode from the INSTALL CD (and not from the USB drive) to do our file edits.

Also, you need to set your bios to boot from the CDROM before the USB (at least until you are finished with the entire installation).

By the way, thanks for the posting on this. I will update the guide to reflect my lack of information. Sorry :D
 
VIM is ... well ... what I would consider a weird text editor program. But after reading a few posts on it, I was able to give the basic usage of it in my guide. You should be able to use any other text editor available on the INSTALL CD to accomplish the edits, if you are not comfortable using VIM.

If this helps resolve your problem, please post back for my (and others) benefit.



DAVE

---

### Post by joess on 2005-11-17
[QUOTE=DaBruGo]hi joess,

When you are at step ( 4 ) are you leaving the INSTALL CD in the cdrom drive? We do this because we have to run UBUNTU in rescue mode from the INSTALL CD (and not from the USB drive) to do our file edits.

Yes

Also, you need to set your bios to boot from the CDROM before the USB (at least until you are finished with the entire installation).

OK I did though. I still could not type in the rescue command?

By the way, thanks for the posting on this. I will update the guide to reflect my lack of information. Sorry :D
 
VIM is ... well ... what I would consider a weird text editor program. But after reading a few posts on it, I was able to give the basic usage of it in my guide. You should be able to use any other text editor available on the INSTALL CD to accomplish the edits, if you are not comfortable using VIM.

If this helps resolve your problem, please post back for my (and others) benefit.



DAVE[/QUOTE]

Thanks for the quick replay

---

### Post by daibak on 2005-11-17
Thanks, Dave.

Found a post (edited) Re: Ubuntu on firewire drive thread mentioning Firewire

[QUOTE=earobinson]I am to understand that ubuntu will run on a usb hd, so as long as the firewire is bootable then I dont see why not. If you could run windows off the firewire hd then I dont see why not with ubuntu.
...
I will say that firewire has had some bugs in the 2.6 kernel and this may cause a problem.[/QUOTE]

Judging from number of posts earobinson has as a Dapper Drake user I'll heed his red flag about 2.6 kernel problems with Firewire before possibly detonating my WinXP setup for the second time in two weeks.

Let me try and dig some more, hopefully finding someone who says they've actually installed a Firewire external disk drive with Breezy. I'll report back if and when I do get anything up and running in 5.10 and how I did it.

Bit off topic but ref. interminable debate, which is faster Firewire or USB 2.0. From hands-on experience, USB 2.0 is rated faster but in day-to-day use on this particular WinXP HE SP2 notebook the Firewire external drive performance outclasses that of USB 2.0's.  Believe it has to do with the system architecture, Firewire doesn't demand the big system overhead USB 2.0 does.

---

### Post by Nrbelex on 2005-11-17
Hi, I followed your guide and got up to the booting for a second time after installing GRUB but at that point it fails with the message, "ALERT! /dev/sda1 does not exist." I made a new thread with much more detail at [http://www.ubuntuforums.org/showthread.php?t=91186](http://www.ubuntuforums.org/showthread.php?t=91186) but feel free to respond here or there. Thanks!!!

~ Brett

---

### Post by DaBruGo on 2005-11-17
[QUOTE=Nrbelex]Hi, I followed your guide and got up to the booting for a second time after installing GRUB but at that point it fails with the message, "ALERT! /dev/sda1 does not exist." I made a new thread with much more detail at [http://www.ubuntuforums.org/showthread.php?t=91186](http://www.ubuntuforums.org/showthread.php?t=91186) but feel free to respond here or there. Thanks!!!

~ Brett[/QUOTE]

Brett,

I'm not sure if this is the right direction to go in ... but ... could you post your grub.conf file for me to see. The problem may be located in it.



DAVE

---

### Post by joess on 2005-11-17
DaBruGo:

Thanks for the info!! I made it to step #8 but can't seem to save the file using the :X keystroke. What am I missing?

---

### Post by DaBruGo on 2005-11-17
[QUOTE=joess]DaBruGo:

Thanks for the info!! I made it to step #8 but can't seem to save the file using the :X keystroke. What am I missing?[/QUOTE]

joess,

VIM commands seem to be case-sensitive.

Make sure you are using a lowercase x.

An uppercase X will NOT work.

Also, make sure you are hitting ESC when done editing, before typing : x (with NO SPACE between the colon and the lowercase x)

Thanks for your post. I have edited the section dealing with vim usage in the guide.



DAVE

---

### Post by joess on 2005-11-17
DaBruGo:
Again thanks for the help. I figured out the save command, it seemed to ask for my password the 1st time I saved in step #8. Now on to another problem i'm having in step #11 that file seems empty?? There is nothing but the tide key, nothing like mentioned below??
 
"Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector"

PS: is..... vim /boot/grub/menu.lst .lst or .1st?

Thanks

---

### Post by DaBruGo on 2005-11-17
a[QUOTE=joess]DaBruGo:
Again thanks for the help. I figured out the save command, it seemed to ask for my password the 1st time I saved in step #8. Now on to another problem i'm having in step #11 that file seems empty?? There is nothing but the tide key, nothing like mentioned below??
 
"Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector"

Thanks[/QUOTE]

You may want to be sure you have entered the command in step 11 correctly (that's vim /boot/grub/menu.lst in all lowercase letters) to edit the grub menu list file.

Linux is case sensitive on everything, including filenames AND directories.

One misplaced uppercase or lowercase letter and you have a completely different file or directory, according to Linux. You may have accidentally created another file with a case-sensitivity error.

Let me know if that fixes your problem. (You're almost there!)



DAVE

---

### Post by Nrbelex on 2005-11-17
Dave -

First off - thanks for this guide - it's the only good one I've found of it's type. (Hint to admins - make it sticky) :KS 

Secondly - I'm very new to Linux so is the grub.conf file the one edited to make hd1 hd0? If so, how do I copy the whole thing here without manually copying it over by writing it down and then typing it here? At another forum I was aksed for Fdisk output so I'll post it here in case it helps:

Disk /dev/sda: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 499 4008186 83 Linux
/dev/sda2 500 525 208845 5 Extended
/dev/sda5 500 525 208813+ 82 Linux swap / Solaris

Then stuff about my internal HD

In case it matters, I'm using a Adaptec ACS-100 enclosure for a former internal HD but, from what I've seen, it should act like any other external HD.

Oh - also, since I didn't feel like permanently screwing around with my BIOS, I just hit F12 whenever I want to fool around during booting. I am able to boot to whatever I want so will this be a problem with revised step #4?

Thanks!

~ Brett

P.S. I get to the point in booting where the Ubuntu logo comes up, a loading bar comes up and it says something about loading modules when it leaves that screen and says unpacking Linux kernel or something like that then gives the Alert! error and "drops to a shell".

---

### Post by DaBruGo on 2005-11-17
[QUOTE=Nrbelex]Dave -

First off - thanks for this guide - it's the only good one I've found of it's type. (Hint to admins - make it sticky) :KS 

Secondly - I'm very new to Linux so is the grub.conf file the one edited to make hd1 hd0? If so, how do I copy the whole thing here without manually copying it over by writing it down and then typing it here? At another forum I was aksed for Fdisk output so I'll post it here in case it helps:

Disk /dev/sda: 4320 MB, 4320862208 bytes
255 heads, 63 sectors/track, 525 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 499 4008186 83 Linux
/dev/sda2 500 525 208845 5 Extended
/dev/sda5 500 525 208813+ 82 Linux swap / Solaris

Then stuff about my internal HD

In case it matters, I'm using a Adaptec ACS-100 enclosure for a former internal HD but, from what I've seen, it should act like any other external HD.

Oh - also, since I didn't feel like permanently screwing around with my BIOS, I just hit F12 whenever I want to fool around during booting. I am able to boot to whatever I want so will this be a problem with revised step #4?

Thanks!

~ Brett

P.S. I get to the point in booting where the Ubuntu logo comes up, a loading bar comes up and it says something about loading modules when it leaves that screen and says unpacking Linux kernel or something like that then gives the Alert! error and "drops to a shell".[/QUOTE]

brett,

I don't think that GRUB looks at hard drives as sda. I could be wrong, but I believe it just attaches a designation as hd0, or hd1, or hd2 etc.

As an example ... my external USB hard drive ( which should be labeled as sda for all practical purposes ) shows up as hd0 in my GRUB config file (menu.lst). It is labeled as hd0 because the GRUB bootloader was loaded on it - and NOT loaded my internal hard drive that has XP on it ( which shows up ad hd1 ).

Wherever the GRUB bootloader is installed ... that drive is considered to be hd0 by GRUB (even if it shows up as an sda drive when running fdisk).

I really believe your problem lies in the GRUB menu.lst file somewhere.

I'm in XP right now, but I will switch to Ubuntu in a bit and try to post my grub menu.lst file for you to review.



DAVE

---

### Post by Nrbelex on 2005-11-17
I understand the whole GRUB hd0 concept and I thought I had fixed that (earlier I hadn't swtiched from hd1 and was getting error 17 so I read your guide and changed it to hd0). I just posted the fdisk stuff for you to see because somebody else trying to help me said it might be important so I thought you might like to see it. I think I know how to see the grub.conf file but how do you post it without retyping it? It's rather long.

~ Brett

---

### Post by DaBruGo on 2005-11-17
brett,

Here is my menu.lst file ...

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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu (5.10, 2.6.12-9-386) 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu (memtest86+)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		OTHER OPERATING SYSTEMS:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map (hd1) (hd0)
chainloader	+1
savedefault

```



DAVE

---

### Post by Nrbelex on 2005-11-17
I *think* that's what mine looked like. I have to boot up Ubuntu from the install CD to check so it's hard for me to copy it here. I'll tell you if anything is different.

~ Brett

---

### Post by Nrbelex on 2005-11-17
Ok - the only differences between yours and mine are...

where yours says:
You can specify 'saved' instead of a number...
default        saved

- mine says 10 where yours says saved


where yours says right below:
timeout                5

- mine says 10 where yours says 5

where yours says much further below in the section I edited per your instructions:
title		Ubuntu (5.10, 2.6.12-9-386)

- mine says 
Ubuntu, kernel 2.6.12-9-386

where yours says right below:
title		Ubuntu (recovery mode)

- mine says
Ubuntu, kernel 2.6.12-9-386 (recovery mode)

and where yours says:
title		Ubuntu (memtest86+)

- mine says 
Ubuntu memtest86+




That's it - thanks!

~ Brett

---

### Post by Nrbelex on 2005-11-17
Dave, when was the last time somebody told you that you're godly? :smile: 

Frustrated and convinced I had made some errors along the way, I tried your guide from step 1 and it's now installing in stage two - I'll post again once I'm in (fingers crossed).

~ Brett

---

### Post by Nrbelex on 2005-11-17
\\:D/ Dave - =D> 

THANK YOU! (posted from Ubuntu)

~ Brett

---

### Post by DaBruGo on 2005-11-18
[QUOTE=Nrbelex]Dave, when was the last time somebody told you that you're godly? :smile: 

~ Brett[/QUOTE]

Brett,

Thanks for the compliment.

Someone ( Psalms 82:6 , John 10:34 ) already mentioned that to me. :)



DAVE

---

### Post by DaBruGo on 2005-11-18
Brett,

You might want to post anything out of the ordinary ( different from the outline ) that you did during the install process.

There might be others who can benefit from your experience with this.

Plus, it never hurts to have a good set of notes when playing with Linux.



DAVE

---

### Post by Nrbelex on 2005-11-18
I would have posted anything out of the odinary if there was anything, but the beauty of it is... there wasn't. I just followed your directions from start to finish. The only minor difference was in picking where to go from the BIOS because I wanted to pick what to boot from manually instead of automatically going into the CD or USB but that was just a choice - not different from your guide. Thanks!

~ Brett

---

### Post by daibak on 2005-11-18
Untiring Christian and spririt-of-Ubuntu zeal Dave shows helping others lick this USB2 challenge inspired me to keep searching how to solve my boot-off external Firewire disk. Surprise, surprise - everybody from PowerPC to Wintel Linux tinkerers reveals Firewire is a complex, iffy proposition. Meaning this may mean no more than a cable change on external Seagate ST316002 (model allows Firewire/USB 2.0) and then follow Dave's how-to step by step.

[QUOTE=daibak]Thanks, Dave.

Found a post (edited) Re: Ubuntu on firewire drive thread mentioning Firewire

Judging from number of posts earobinson has as a Dapper Drake user I'll heed his red flag about 2.6 kernel problems with Firewire before possibly detonating my WinXP setup for the second time in two weeks.

Let me try and dig some more, hopefully finding someone who says they've actually installed a Firewire external disk drive with Breezy. I'll report back if and when I do get anything up and running in 5.10 and how I did it.

Bit off topic but ref. interminable debate, which is faster Firewire or USB 2.0. From hands-on experience, USB 2.0 is rated faster but in day-to-day use on this particular WinXP HE SP2 notebook the Firewire external drive performance outclasses that of USB 2.0's.  Believe it has to do with the system architecture, Firewire doesn't demand the big system overhead USB 2.0 does.[/QUOTE]

Hope have time over weekend to test what was till now an external Firewire disk as a Breezy install on an external USB 2.0 disk. Will post back afterwards.

---

### Post by DaBruGo on 2005-11-18
daibak,

I hope it works for you ... that would be awesome.



DAVE

---

### Post by hardclip on 2005-11-18
Hi Dave,

I already have Breezy installed on an internal hd that I now want to convert to an external drive with a USB case...

Can I simply make the same changes in VIM in Recovery Mode to add USB support or is it too late?? 

Also, I did not have my XP Drive connected at installation time, so as far as Grub is concerned, Ubuntu is all it sees..can I manually add Windows to Grub or am I looking at a clean install?

---

### Post by DaBruGo on 2005-11-19
[quote=hardclip]Hi Dave,

I already have Breezy installed on an internal hd that I now want to convert to an external drive with a USB case...

Can I simply make the same changes in VIM in Recovery Mode to add USB support or is it too late?? 

Also, I did not have my XP Drive connected at installation time, so as far as Grub is concerned, Ubuntu is all it sees..can I manually add Windows to Grub or am I looking at a clean install?[/quote] 

hardclip,

In theory, if you add the vim changes to the files and then recompile/recreate the kernel, I don't see any reason why it wouldn't work. Even if you made the changes and never removed the drive, I don't see how it would effect Ubuntu booting up. You are just adding some module support to the kernel is all.

I would just make sure that you do the vim changes right before you remove the drive to put it in an external enclosure. Also, if recovery mode will not let you do the edits, then try using the install cd in rescue mode.

My home PC is setup similar to what you want. I have Ubuntu on an external drive and XP is on my internal drive. I posted my grub config file ( menu.lst ) a few posts back (#44) if you want to see how mine is setup. My settings to boot XP is at the bottom of the menu.lst file.

Hope that helps. Let me know how it all works out.



DAVE

---

### Post by Arktis on 2005-11-19
Why hasn't this been moved over to the howto section?  C'mon, man! :p

---

### Post by koichirose on 2005-11-19
ok i followed your tutorial, everything goes ok, but when i reboot with no cd inserted it, ubuntu starts but says "Block I/O error device sdb1".
Note that i installed to sdd, not sdb, so it has to be something else.

However the initialization goes on, it should finish the installation, but it stucks at 0% on that screen...how can i solve it?

---

### Post by hardclip on 2005-11-19
Will do!! Ordering the enclosure right now so I'll know in a few days...


Thanks for help...this forum really is a wonderful place..zero elitism factor!!

---

### Post by joess on 2005-11-19
Posting from FF\ubuntu. Finally got it sorted out. I was making two errors. On step #2, Instead of using the option "erase entire disk SCSI (0,0,0) sdb" (sdb is my external usb drive), I was using "erase entire disk and use lvm" (something like that). 2nd mistake was on step#3 grub loader I was using the command /dev/sdb1, instead of /dev/sdb. That explains why I was getting the "new file" when I got to step#11 vim /boot/grub/menu.lst.

Anyway it work, I like it, i'm happy:razz:. Thanks to DaBruGo. I like the fact that I did not give up, and being 55+ makes it all more sweet.

---

### Post by daibak on 2005-11-22
Had hoped to be back to the thread by now with Breezy up and running off external FireWire (IEEE 1394a) Seagate drive but 'fraid not there yet. Or maybe I'm just chasing own tail as don't know how to boot into Ubuntu as have run the re-partition and install many times, adding eight dependency modules for SCSI and USB (just to play safe):
sd_mod
scsi_mod
ehci-hcd
usb-storage
sbp2
ieee1394
ohci1394
raw1394

All looks good on external 160 GB disk when investigate with Breezy Live CD and every single piece of hardware works flawlessly with Live CD (whether FireWire disk, Plextor DVD Recorder USB 2.0 thru Belkin USB 2.0 PCMCIA Cardbus hi-speed notebook card, or Mitsumi USB 1.1 3/1/2" floppy drive).

Having said NO to GRUB boot loader install on MBR as WinXP C: drive uses root partition /dev/hda2 - thus merely typed /dev/sda for disk volume with no partition number (it's sda1) -  /boot/grub is only on external Seagate Linux root. Stuck, can only boot or re-boot into Windows when Install CD finishes.

[QUOTE=DaBruGo]daibak,
I hope it works for you ... that would be awesome.
DAVE[/QUOTE]

Saved FDISK, GRUB menu.lst, /etc/fstab, lspci, SCSI connections shell info if anybody cares to have a look or has any tips how I can try to boot into Breezy 5.10   For example, is there an Ubuntu Install CD or Live CD cheat code as I believe Knoppix 4.0.2 has?

TIA, guys.

---

### Post by RyanGT on 2005-11-22
One thing you could try.  My laptop is funny about the boot order and resets the internal harddrive ahead of my USB harddrive if the USB drive is unplugged even once and not reset.  When you boot, go into your BIOS and make sure that your firewire drive is listed first or move it up.

Ryan

---

### Post by DaBruGo on 2005-11-22
[QUOTE=daibak]Had hoped to be back to the thread by now with Breezy up and running off external FireWire (IEEE 1394a) Seagate drive but 'fraid not there yet. Or maybe I'm just chasing own tail as don't know how to boot into Ubuntu as have run the re-partition and install many times, adding eight dependency modules for SCSI and USB (just to play safe):
sd_mod
scsi_mod
ehci-hcd
usb-storage
sbp2
ieee1394
ohci1394
raw1394

All looks good on external 160 GB disk when investigate with Breezy Live CD and every single piece of hardware works flawlessly with Live CD (whether FireWire disk, Plextor DVD Recorder USB 2.0 thru Belkin USB 2.0 PCMCIA Cardbus hi-speed notebook card, or Mitsumi USB 1.1 3/1/2" floppy drive).

Having said NO to GRUB boot loader install on MBR as WinXP C: drive uses root partition /dev/hda2 - thus merely typed /dev/sda for disk volume with no partition number (it's sda1) -  /boot/grub is only on external Seagate Linux root. Stuck, can only boot or re-boot into Windows when Install CD finishes.



Saved FDISK, GRUB menu.lst, /etc/fstab, lspci, SCSI connections shell info if anybody cares to have a look or has any tips how I can try to boot into Breezy 5.10   For example, is there an Ubuntu Install CD or Live CD cheat code as I believe Knoppix 4.0.2 has?

TIA, guys.[/QUOTE]

daibak,

I don't know if this matters, but I am wondering if you have to bump up the setting for WAIT time since all those extra modules are being loaded?

Just a thought.



DAVE

---

### Post by daibak on 2005-11-23
For Dave and RyanGT,

Thanks for your replies.

Dave, problem no. 1 is can't get beyond step (12). No GRUB loader is being saved to /dev/sda1 or GRUB-speak (hd0,0) as I can never get to finish install. Running grub> prompt confirms no stage1 file exists at (hd0,0) or elsewhere and any attempts to dual-boot using WinXP ntldr just hangs at Linux option (that's observing rules copying first 512 bytes of root Linux partition into shareable vfat/FAT32 partition then copying linux.bin to C: /dev/hda2 NTFS).

RyanGT's makes me feel dumb. Of course I should have checked before starting out what BIOS detects at startup and never did (see note)!
This is a 2002 HP Pavilion P4-M notebook, HP never updated BIOS, which allows selecting boot sequence for Diskette A, CD-ROM/DVD, Hard Disk or Internal LAN but not FireWire. FireWire (if on-board port is connected) detected fine *after *Windows login and any other OS like Linux will face same problem. FW seems to have its own, separate controller architecture on motherboard.

So problem no.2 is Linux on an external FireWire disk drive sounds like a real Catch-22 until you read IBMer Martyn Honeyford's 2004 solution, 
[Boot > Linux from a FireWire device - Installing Linux on removable drives]("http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html?") 

Problem is still in diapers and Honeyford says that in order to use this method you need to create two things, a kernel and an initrd image. That's way too adult if unable conclude Dave's step (13) with a simple reboot into Ubuntu to finish Breezy's installation.

Cheers all.


(Note) For the heck of it attempted install Fedora Core 4 today. Red Hat's Anaconda installer doesn't see the external Firewire Seagate drive with its partitioner, Disk Druid. Another reason am so keen to use UBUNTU as its disk partitioner seems to handle this Seagate drive just fine as a SCSI /dev/sda during Ubuntu Install CD (inconclusive) session.

---

### Post by RyanGT on 2005-11-23
daibak,

I haven't tried this, but it might work: you could put your boot partition on your internal harddrive.  It would only need to take up a few hundred megs.  I think you could make everything work from there.  You would still want firewire related modules built into your initrd, but you have to do that same kind of stuff to boot from a USB drive.

This may not be possible if you don't have a way to create a small partition on your internal drive.  Assuming the drive is NTFS, you would need something like partition magic to do this.

Ryan

---

### Post by daibak on 2005-11-23
Ryan,

Will probably wind up trying PM 8.01 with an ext3 or FAT32 logical partition to test what you suggest on internal 30GB IDE HD. Hold overrated view different OSes ideally inhabit different planets. Tried hard but there are practical limits.

[QUOTE=RyanGT][SIZE="3"]daibak,

I haven't tried this, but it might work: you could put your boot partition on your internal harddrive.  It would only need to take up a few hundred megs.  I think you could make everything work from there.  You would still want firewire related modules built into your initrd, but you have to do that same kind of stuff to boot from a USB drive.

This may not be possible if you don't have a way to create a small partition on your internal drive.  Assuming the drive is NTFS, you would need something like partition magic to do this.

Ryan[/SIZE][/QUOTE]

Thanks!

---

### Post by RyanGT on 2005-11-23
I understand why you want to keep them seperate.  I would like to hear how things turn out and let me know if I can help in any way.  I should actually do what I am suggesting you do sometime soon.  Right now I have Windows and Fedora on my internal harddrive and ubuntu on the USB.  I never boot into Fedora, but because I didn't want to go into the bios each time to boot into ubuntu, I installed grub on my MBR of hda.  I actually use the grub of fedora on the internal harddrive because otherwise my computer won't even boot into windows without the usb harddrive attached.  Kind of a mess.

So, if you are successful, I may try it to!

Ryan

---

### Post by earobinson on 2005-11-25
I dont normaly do this and feal kinda like a whore but ....*BUMP*

Great how to (Mods should move this thread to the how tos)

---

### Post by lonevvolf on 2005-11-27
Thanks for the great posting, but unforunately, I have a problem at the moment.  I have installed Ubuntu exactly as described on a USB stick, but when I start from the USB drive, I get:

GRUB GRUB Loading stage1.5

Over and over in an endless loop.  Can anyone help?

---

### Post by daibak on 2005-11-28
Dave, Ryan and friends

Learned a lot but still have far to go - e.g. 137 GB disk bounday challenges some distros and bootloaders. Anyway, finally did get GRUB stage2 loaded, only not certain to exactly where. This HP Windows notebook really doesn't seem ready to share its roof with anybody else so I took the plunge. Pls read on below.

[QUOTE=RyanGT]I understand why you want to keep them seperate.  I would like to hear how things turn out and let me know if I can help in any way.  I should actually do what I am suggesting you do sometime soon.  Right now I have Windows and Fedora ...

So, if you are successful, I may try it to!

Ryan[/QUOTE]

Will live on the wild side in Linuxland for a week or so to see what life's like with a Linux box. Once again running grub> root hd(1,0) then setup (hd0,1) clobbered dual-boot loader and Windows MBR irrecoverably. Perhaps should have tried setup (hd0,0) first but re-booting with Ubuntu Live CD time after time is a hassle and got dreaded missing hal.dll screen that killed that. Rather than reinstall WinXP all over again, a lot of work - only have four HP Pavilion factory Recovery CDs, no separate OEM WinXP CDs to be able to enter Recovery Console and try and repair MBR, just ploughed on and installed Ubuntu 5.10 on both internal IDE and external Firewire 160.0 GB Seagate disks.
To my joy, back on the Internet all in order in under an hour with Breezy Badger. Perhaps now I really will learn some Linux commands!

Below is dialogue GRUB spewed out this morning

grub> root (hd1,0)
Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,1)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0,1)"... failed (this is not fatal)
Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
Running "install /boot/grub/stage1 d (hd0,1) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.

grub> quit

Thanks for your help.

---

### Post by RyanGT on 2005-11-28
So are you saying you are up and running or is there a question in your grub post?

I know what you mean about the 4 OEM cd's - my compaq is the same way.  If you didn't completely overwrite your windows install, I think there are MBR repair tools on the internet.  But if you did, good for you.  It's like Cortez burning the ships - or something.

Ryan

---

### Post by daibak on 2005-11-28
Ryan,

Since I've still got 4 HP Rescue CDs in desk drawer can't honestly say I've burnt all my bridges but, yes, I'm flying high on this Linux Ubuntu 5.10 box with nary a bit of Microsoft. Wiped both disks clean and started over, Linux only for this week anyway. We'll see, feels like first day at kindergarten and am bit lost but can get things done.
Of course this isn't a work machine. May be pretty dumb but not yet that so!

Believe that informing all about our experiences responsibly requires telling all the facts, not just the success stories. My success was it taught me a a lot although I didn't ever succeed dual-booting this HP Pavilion notebook as originally intended. There are a lot of people out there who, frankly, don't have any Windows technical expertise to recover from a messed-up MBR and other such situations and they shouldn't be fooling around with GRUB/LILO; they should buy a cheapo Linux box.

Cheers.

---

### Post by TLimits on 2005-11-30
Great Work Thanks....

Followed the original post exactly and it works no problem.

Have managed to get a full load on my USB disk, as well as a base load on my Cruzer 1GB stick. Seem to be running out of space on the stick if I try a full load. Last night got my WLan (Broadcom) working so life is good.

Same problem as others with my Compaq R3000 notebook it can't seem to remember that I want to boot off the USB device.

Currently partitioning my USB disk to try and get Ubuntu, Dyne:Bolic (another great distro) and Bart's PE all on the same disk.

Thanks again DaBruGo

---

### Post by Nrbelex on 2005-12-01
Ok so I got an alert to update my kernel and did so... now when I go into Grub, I get the message that it's trying to boot from the wrong drive. I changed it back to 0,0 and it works but it doesn't stick. Now that everything's set up, is there any easy way to keep it at 0,0 without manually changing it every time?? Thanks!

~ Brett

P.S. I've been using Ubuntu for a while now because of *this* thread so THANKS! :)

---

### Post by TLimits on 2005-12-01
Brett,

If you edit the grub bootloader(remembering to save ":x") it should stick..

See DaBruGo's original post

>>(11) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst <<

Cheers.... Dave

---

### Post by Nrbelex on 2005-12-01
I remembered his method via the install CD in rescue mode but is there any other way? That's sorta time consuming and always get's me a little worried... :rolleyes: - If not, no problem and thanks!

~ Brett

P.S. - oh wait - now that it's installed, can I just boot up Ubuntu and the the prompt and do it from there?

---

### Post by Nrbelex on 2005-12-01
> P.S. - oh wait - now that it's installed, can I just boot up Ubuntu and the the prompt and do it from there?

Hmmm - that doesn't seem to work - the terminal cuts me off before I can start doing anything - 

```
brett@brettslaptopubuntu:~$ sudo mount -tproc proc /target/proc
mount: mount point /target/proc does not exist
brett@brettslaptopubuntu:~$ chroot /target
chroot: cannot change root directory to /target: No such file or directory

```

- through the install CD then? Thanks!

~ Brett

---

### Post by lonevvolf on 2005-12-02
TLimits...how did you do a "base load"?  I am also trying to get this running on a 1GB stick, and it just doesn't want to boot up.

---

### Post by the_person0 on 2005-12-02
I was wondering if this could possibly work the other way around, i would like to boot a windows system off my external hard drive.  Windows will not install to the mobile hard drive by default, however it would possibly work to install it on another sytem then put it in the external hdd shell and then do this. If anybody has any ideas on weather or not this would work it would be much appreciated.

---

### Post by TLimits on 2005-12-03
lonevvwolf.... Base load is installed by typing "server" at the install prompt when booting the install CD. Unfortunately you get no GUI. I'm trying to see if I can strip out as much as possible and still get a GUI.... no success yet.

Booting XP from USB is a problem. Also if you could get it to work moving the USB drive from system to system would cause many issues. XP does not like changes in hardware. It's one thing to change say a graphics card, you can boot up the machine in safe mode, change the driver and life should be good. However if everything has changed windows will probably not even boot (BSOD). I have seen this many times at work were we use Ghost images for configuring development PC's if we get the wrong image it's dead in the water.

If you are serious about getting XP to boot off a USB drive for 1 machine I would play about with Embedded XP.

Enjoy

---

### Post by the_person0 on 2005-12-05
xp has no problems going between systems, i threw my laptop hard drive in my desktop and it worked just fine (using a hdd adaptor of corse).  what i don't know is if it will run off usb or not.

---

### Post by xeno on 2005-12-05
This topic should really be sticky or something. After finding it yesterday and figuring out my problem, I came back today and there are at least three postings asking how to do this.

Fabulous instructions.

---

### Post by Nrbelex on 2005-12-06
[QUOTE=Nrbelex]Ok so I got an alert to update my kernel and did so... now when I go into Grub, I get the message that it's trying to boot from the wrong drive. I changed it back to 0,0 and it works but it doesn't stick. Now that everything's set up, is there any easy way to keep it at 0,0 without manually changing it every time?? Thanks!

~ Brett

P.S. I've been using Ubuntu for a while now because of *this* thread so THANKS! :)[/QUOTE]

OK - fixed it- 

If you update the kernel, you'll probably need to use the Ubuntu install CD from "rescue" mode and follow the given instructions on how to change the Grub menus. Not too big a deal. Good luck!

~ Brett

P.S. - *THIS SHOULD BE STICKY OR IN THE HOW-TO*

---

### Post by Draaku on 2005-12-06
Great guide....followed and installed to a 20GB USB2.0 external drive. rebooted, but now i get this error.

```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18
``` 
I am not dual booting, just trying to install ubuntu on the external drive. Any suggestions?

EDIT: Well I tried a different USB port in my computer and I am now able to boot...so I'm progressing...

---

### Post by Nrbelex on 2005-12-06
[QUOTE=the_person0]I was wondering if this could possibly work the other way around, i would like to boot a windows system off my external hard drive.  Windows will not install to the mobile hard drive by default, however it would possibly work to install it on another sytem then put it in the external hdd shell and then do this. If anybody has any ideas on weather or not this would work it would be much appreciated.[/QUOTE]

the_person0 - You definitely will want to check [this]("http://www.tomshardware.com/howto/20050909/index.html") out. :smile: 

~ Brett

---

### Post by Olle on 2005-12-08
Hi

I am triying installing Ubuntu 5.10 on my external usb HD. The problem I have is that as long as i am rebooting ubuntu from external usb hd, booting is succesfuly but if I power off and then power On, I get "Alert! /dev/sda1 does not exist" - message.   

I have search and read about everything on internet on this subject including DaBruGo:s excellent instruction. I have rechecked initramfs.conf, modules and menu.lst and everything is ok.

I boot from the CDrom in resue mode, then reboot with external usb hd connected and it boots from external usb hd succesfully. I can reboot with no problems, everything works fine. But... if I power off and then power on it starts to boot from ext usb Hd and then comes ALERT! /dev/sda1 does not exist.
Once or twice It has booted succesfuly from power on, can it be a timing problem? Anyone has any ideas?

I have tested WAIT in /etc/mkinitramfs/initramfs.conf with various settings. I tried WAIT=50 but couldnt see any differens in boot time. (in previous ubuntu version there was a DELAY instruction). Is WAIT realy working or am i doing something wrong? 

Any help appreciated  :p

---

### Post by kch_86 on 2005-12-08
Hi, I would like to say thanks for the HowTo. But I have a problem. I followed the tutorial step by step, but when I reboot after step 12, I get an error from the bios that says boot failed. Any ideas?

---

### Post by Nrbelex on 2005-12-09
[QUOTE=Olle]Hi

I am triying installing Ubuntu 5.10 on my external usb HD. The problem I have is that as long as i am rebooting ubuntu from external usb hd, booting is succesfuly but if I power off and then power On, I get "Alert! /dev/sda1 does not exist" - message.   

I have search and read about everything on internet on this subject including DaBruGo:s excellent instruction. I have rechecked initramfs.conf, modules and menu.lst and everything is ok.

I boot from the CDrom in resue mode, then reboot with external usb hd connected and it boots from external usb hd succesfully. I can reboot with no problems, everything works fine. But... if I power off and then power on it starts to boot from ext usb Hd and then comes ALERT! /dev/sda1 does not exist.
Once or twice It has booted succesfuly from power on, can it be a timing problem? Anyone has any ideas?

I have tested WAIT in /etc/mkinitramfs/initramfs.conf with various settings. I tried WAIT=50 but couldnt see any differens in boot time. (in previous ubuntu version there was a DELAY instruction). Is WAIT realy working or am i doing something wrong? 

Any help appreciated  :p[/QUOTE]


If you can sometimes get it to work, you may have an issue I occasionally have. I find that flipping the switch on the HD *just* as you load up the BIOS usually gets the two in sync. If not, the drive may not show up in the BIOS or may get messed up while loading. Good luck!

~ Brett

---

### Post by Nrbelex on 2005-12-09
[QUOTE=kch_86]Hi, I would like to say thanks for the HowTo. But I have a problem. I followed the tutorial step by step, but when I reboot after step 12, I get an error from the bios that says boot failed. Any ideas?[/QUOTE]

Make sure vim /boot/grub/menu.lst has been edited the way described in the guide. If it's perfect, start over making sure you follow EVERY direction. I initially had this problem too but after starting from scratch and following every direction to the letter, I got it working without a problem. Good luck!

~ Brett

---

### Post by kch_86 on 2005-12-09
I'll do it again but i have tried it 3 times, and I checked and rechecked what i edited.

---

### Post by Baptiste on 2005-12-09
Good evening

your solution is quite good. However it is very slow. I have to wait a lot of time at starting grub (on my usb hd) and at starting ubuntu (that is to say before the apparition of usplash).

Is there a way to speed up the boot?

Thanks!

---

### Post by MMorbidfaithMM@gmail.com on 2005-12-09
Hello, I have read the instructions at the front of this Thread, I was just wondering if there is anything different that I would have to do on a Mac.  I am still installing Ubuntu on my external but I believe that the boot loader is called Yaboot instead of Grub?  I am very new to this so I might be mistaken.  Please tell me what steps to do differently if any.  Thanks.

---

### Post by kch_86 on 2005-12-09
Alright, so I tried installing ubuntu again. Boot failed again. One thing i should say is that I have Unbuntu installed on an internal hard drive already, and grub was installed to the mbr. Would this be my problem?

---

### Post by silver_arrow on 2005-12-09
Hi,

Nice to meet you guys! :) 
I am trying to setup a development workstation in Linux with all these nice open source software. So far so good, I installed Kubuntu without any problem but I get the same type of error as many of you... in my case I get the infamous: **Error 17** on Grub.

I followed Dave's guide exactly but still doesn't work for me.
I am wondering what could be the issue here? :rolleyes: 

I have an external drive on USB Maxtor Personal Storage 3100.
My partition is 21 GB on applications side and 1 GB Swap.
Not to forget on my external HD I have 3 partitions:
1. Windows NTFS
2. Swap
3. / (root) partition

The Kubuntu installer sees my / partition as: hd0,2 --> /dev/sda3
My question is:
- Is hd0,2 correct?
- Should I install the boot loader on External's drive MBR?

Thanks a lot for your time,
Alex

---

### Post by joess on 2005-12-09
[QUOTE=silver_arrow]Hi,

Nice to meet you guys! :) 
I am trying to setup a development workstation in Linux with all these nice open source software. So far so good, I installed Kubuntu without any problem but I get the same type of error as many of you... in my case I get the infamous: **Error 17** on Grub.

I followed Dave's guide exactly but still doesn't work for me.
I am wondering what could be the issue here? :rolleyes: 

I have an external drive on USB Maxtor Personal Storage 3100.
My partition is 21 GB on applications side and 1 GB Swap.
Not to forget on my external HD I have 3 partitions:
1. Windows NTFS
2. Swap
3. / (root) partition

The Kubuntu installer sees my / partition as: hd0,2 --> /dev/sda3
My question is:
- Is hd0,2 correct?
- Should I install the boot loader on External's drive MBR?

Thanks a lot for your time,
Alex[/QUOTE]

Make sure you follow Dave's insructions to the letter,i.e #3 grub to **/dev/sda**
#5 if your drive is not the same  **(Mine was mount /dev/discs/disc1/part1)**
then you may have a issue. Of course this is assuming that you have one internal HD  (hda) and on external (sda)?

---

### Post by silver_arrow on 2005-12-10
Joess,

I have an internal HD and the external HD.
While installing Kubuntu the system was installed in /dev/sda3. I also remember when the partition was created I was setting up the boot flag for it. Based on that I installed the boot loader on /dev/sda3. 

According with the device names on my external HD things are getting counted like this:
1. Windows NTFS --> /dev/sda1
2. Swap             --> /dev/sda2
3. /                   --> /dev/sda3

You suggest that the boot loader should be installed on /dev/sda ?
If so, why not installing it in /dev/sda MBR anyway?

Thanks a lot,
Alex

---

### Post by utterlyjaded on 2005-12-10
Well finally I was able to get Ubuntu running off my exturnal hd, I also tried it on a 2 gig stick, with small some tweaks I was able to get it to work, haha, now I can load Ubuntu onto my school computers.  Great Stuff!

---

### Post by joess on 2005-12-10
silver arrow
If you have 2 hd then your internal is a sata? (sda) if so then you external should be listed as sdb? In any case all you need is the root /ext3 & a swap, do not turn the boot flag on the /ext3 partition because it will move from your windows partition to the linux partition (the lighting bolt symbol) and you will not be able to boot into windows without the grub. The boot loader (grub) needs to go on the hd that has the new linux partition on it ,i.e /dev/sdb if that is what you external hd is called. In my case I had a sata internal (sda) and a usb external (sdb) also make sure that when in the rescue mode that you can only mount /dev/discs/disc1/part1)
 the others will not mount if you set things up right...got it? If you did screw up and moved the boot flag from windows to linux, it ca be fixed my booting into windows with the grub, then go into disk manager and right click on the windows partition and choose (make active) ignore the warning pop up, you will see it listed as (boot) before you make it active and then change to (system) like it should be.

---

### Post by Nrbelex on 2005-12-10
[QUOTE=kch_86]Alright, so I tried installing ubuntu again. Boot failed again. One thing i should say is that I have Unbuntu installed on an internal hard drive already, and grub was installed to the mbr. Would this be my problem?[/QUOTE]

If you're trying to boot from a GRUB copy on the external I don't think it would be a problem but if you're trying to boot from the internal, change the GRUB boot list back to what it was before the guide. If it still doesn't work, post the output of that file and the other one edited in the guide.

~ Brett

---

### Post by chromguy on 2005-12-10
Just wanted to comment that this worked GREAT. Thanks for the details. My only problem is getting the winmodem working on my D610 Regards, Chromguy.:p

---

### Post by chromguy on 2005-12-11
As an interesting datapoint, I did an md5sum on a 100M file on my notebook Dell D610 with an installation of Breezy running from the internal HD and and external usb drive. I was amazed with the results (using the time function). Both clocked in at 1.1 sec each.

---

### Post by Olle on 2005-12-11
Is there any differens between a reboot and a boot from power-on? 

I have installed ubuntu on external usb drive, grub on external as well, and as long as i reboot it works fine. When i power off and power on it boots from external as i should but stops at ALERT /dev/sda1 does not exist.

Is there anyway to catch bootcommands (in a file) so that i can compare reboot and boot starts?

---

### Post by ezkcdude on 2005-12-12
Great tutorial! I've been wanting to do this for a long time (with Linux in general, but not Ubuntu), but could never figure out how. I followed the tutorial exactly as is, and it worked perfectly. Thanks, DaBruGo!

---

### Post by obe1kenobi on 2005-12-14
This is a great tutorial. 

I got it to work on the install, but after upgrading to the 2.6.12-10-386 kernel it will no longer work.  Please help.

Thanks again.

---

### Post by joess on 2005-12-15
[QUOTE=obe1kenobi]This is a great tutorial. 

I got it to work on the install, but after upgrading to the 2.6.12-10-386 kernel it will no longer work.  Please help.

Thanks again.[/QUOTE]

You need to update the menu.lst file to see the new kernel...
>sudo gedit /boot/grub/menu.lst< then change it like this...
Change the kernel from 2.6.12-9-386 to 2.6.12-10-386. Thats it. My menu.lst will look different from yours because I now have Breezy installed on my internal HD and when you update the kernel it does it automatically. Where as when its installed on a external HD, you have to edit the menu.lst by hand.


## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

---

### Post by xyglose on 2005-12-15
Quick question.  I followed the installation instructions given in the "Success - Breezy loaded on external USB drive" (10-23-2005); however, when I reboot with the CDROM still in the hard drive it takes me through the install process again.  The initial install was a snap up to this point.  How do I get to where I am asked which partition to mount?

I am installing ver. 5.04, seeing as how this is the only version I have available.

---

### Post by obe1kenobi on 2005-12-16
You have to type rescue in instead of hitting enter for the normal install (after the reboot with the CD in).

---

### Post by xyglose on 2005-12-17
Ok, I will try it again.  At the login screen I did type "rescue"; however, it took me to the start of the installation process again.  I'll give it another shot.

Thanks for the reply.

---

### Post by obe1kenobi on 2005-12-18
look at this tutorial

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

---

### Post by Nrbelex on 2005-12-19
[QUOTE=obe1kenobi]look at this tutorial

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)[/QUOTE]

Also known as the start to **this very thread!** :p 

~ Brett

---

### Post by obe1kenobi on 2005-12-19
Sorry, forgot which thread I was looking at. #-o

---

### Post by dfme on 2005-12-21
thanks DaBruGo for the detailed instructions!
ubuntu is working very well from my usb hd
the only thing that isn't working is suspend to disk and suspend to ram...
is this working with anyone?
and if yes...
how did you get it to work?

---

### Post by DaBruGo on 2005-12-21
Hi folks,
 
Just wanted to give a heads up to everybody for a potential upgrade problem I encountered the other night. The fix is simple but I wanted to make you all aware of it.
 
Last night, using the automatic update program that runs from the desktop, I had Ubuntu upgrade my kernel to a newer version. Everything went fine until I rebooted. When that happened, my PC wouldn't start up in Ubuntu and it gave me a GRUB ERROR 17 message.
 
What happened was that Ubuntu correctly updated the GRUB info (in /boot/grub/menu.lst) for the new kernel (which looked fine) BUT IT ALSO CHANGED THE ROOT LINES in my menu.lst file from (hd0,0) to (hd1,0) for all my Ubuntu entries.
 
My fix was this ...
 
When GRUB furballed on me, I got back to the GRUB menu screen (I believe by hitting ESC) and navigated to my first menu choice and then hit the E key to temporarily edit it's root line entries from (hd1,0) back to my original (hd0,0).
 
NOTE: this is only a temporary change as GRUB does not save any edits from the startup menu (at least it doesn't for me)
 
When I hit the letter option (I believe it was B) to boot that choice, it then successfully started up Ubuntu.
 
Once the desktop came up, I then edited the /boot/grub/menu.lst file from a terminal window (sudo vim /boot/grub/menu.lst) and changed all my root line entries to match what they are supposed to be ... (hd0,0).
 
That seemed to fix everything back to normal ... and I didn't even need a CD in rescue mode for the fix!
 
 
Hope this helps anyone who has had a similar problem.
 
DAVE
 
 
*** UPDATED (02-26-2006): Please see the information in [message #249]("http://ubuntuforums.org/showpost.php?p=772873&postcount=249") for a fix to this issue

---

### Post by CrunchyDoodle on 2005-12-21
I had a similar kernel update experience and fixed it pretty much as you did. I was a little surprised it did what it did, since you'd think the updating script would have looked at and retained what was obviously working and needed for the system to boot correctly. But no, it ignored what was working.

I do realize that loading up an external USB drive with ubuntu is a bit unusual. And that it does present some unusual drive mappings with the internal drive being ancillary and the external drive logically being the main boot drive. However, it's not that wierd.    :smile: 

Maybe next time it will be right.     ;) 

Bye.     :cool:

---

### Post by bloodylip on 2005-12-24
I've been trying to load Ubuntu on my IDE hard drive, while booting it from a USB flash stick (my main HDD is a SATA RAID that grub can't see, and I don't feel like changing the BIOS settings on every reboot), but I'm running into some troubles. I've followed this guide almost exactly. The only thing I changed was keeping my grub root as (hd4,0), since that's what the grub map refers to my USB stick as (I've also tried the other (hd?,0) values).

So I go through all this, then when it comes time to reboot, one of two things can happen to me:

1. If I'm booting to USB-FDD, I just get "GRUB" and it sits there forever.
2. If I'm booting to USB-ZIP, I can either get the first message, or "GRUB GRUB GRUB Hard Disk Error". 

And to save anybody the time of looking up the "Hard Disk Error" message, here it is:
> The stage2 or stage1.5 is being read from a hard disk, and the attempt to determine the size and geometry of the hard disk failed.

Thanks in advance.

---

### Post by Roland Bouman on 2005-12-28
Hi, and thanks alot!

I have been struggling with this issue and have been kindly redirected to this thread. I ran through the procedure and now I'm posting this from the freshly installed Mozilla that ships with ubuntu. 

Thanks ever so much, I could not have done it without this!

There's is one little issue that I encountered during the procedure. It might help someone else so I'll inlcude it here.

Apart from an external USB hard-drive, I also had a USB hub/"6 in 1" cardreader/dvd combi connected to my PC. I think that led me to choose the wrong disk in step 5. I restarted the procedure this time without the cardreader and that worked for me. 

The funny thing is, that the first time (cardreader connected) during the partitioning phase (your step 2), my ext. harddrive was recognized and written too (I could tell, it made ticking sounds and the led showed activity) but it was labeled sde. (yup, sde!) Apart from the ext. harddrive, only my builtin harddrive was shown there.

In the mount step (your step 5) it showed me a whole bunch of discs the first time (when the cardreader was still connected).

The second time (cardreader disconnected) the external harddrive was labelled sda, like in your procedure. THen, everything went very smoothly. 

Props to you dude! I Really admire that work of yours.

---

### Post by tylerKiwi24 on 2005-12-28
ok, so can someone give me steps on how to INSTALL ubuntu FROM a USB stick? I have a 1gb stick and want to install it on my laptop. My CD-ROM has died and I have no floppy - so USB is my only hope, right?

PLEASE help me!!
thanks

---

### Post by ilmw on 2005-12-29
[QUOTE=tylerKiwi24]ok, so can someone give me steps on how to INSTALL ubuntu FROM a USB stick? I have a 1gb stick and want to install it on my laptop. My CD-ROM has died and I have no floppy - so USB is my only hope, right?

PLEASE help me!!
thanks[/QUOTE]

maybe this will help? [link]("https://wiki.ubuntu.com/Installation/FromUSBStick")

---

### Post by peekpt on 2005-12-29
After 2 days of getting error 17 and error 18 I did it!! :rolleyes:

Solution for bigger disks:

Create a small /boot partition like 200 megas in the beggining of disk to make sure your stages aren't writed on higher cylinders  than the bios is capable to read of.

that's how I did in my 250G disk:

M.point    type
/boot.....ext3.......0.2G.......sda1
............ FAT32....200G.......sda2
.............swap.....1G..........sda3
/...........ext3......48G..........sda4


don't forget to specify the mounting point /boot on the first partition on your ubuntu installation.

NOTE:  When go on rescue cd and then got the root prompt You have also to mount boot:

> mount /dev/sda1 /boot

---

### Post by Roland Bouman on 2005-12-29
Wow, it's just such a thrill to have this OS sitting here on a portable drive!!

I just hooked my external drive to the IBM Thinkpad laptop I use for my job. 

True, for some reason, I had to install the drive first under Windows XP (I'd expected the BIOS to pick it up right away, but it didnt), but after that, I could boot Ubuntu right away, just like I did on my desktop upstairs. 

So, Ubuntu has awoken in this strange new body. From there, I used the graphical "networking" tool to set up my wireless adapter  (built-in in my thinkpad, my desktop  uses and old fashioned ubilical chord)  and lo-and-behold: here I am, sitting in the living with my laptop posting this :cool: .

Thanks again Dave, I really, really am so much obliged to you for posting this solution!!

---

### Post by etabeta on 2005-12-30
Hi,
Great topic.

I'd like to install ubuntu on my usb key but I have 1 question: my motherboard doesn't allows for booting from usb drive, is possible to create (and how to?) a floppy disk or boot cd in order to access my usb key?

thanks,

---

### Post by yekibud on 2005-12-31
I think DaBruGo should be elevated to diety status - I have been trying to do this for - years?  I gave up on external USB HDDs last year and lived on Slackware since then, since it was the only thing I could get running on my Cruizer whatchamacallit 256MB thumbdrive.  But the goal was always to go "big drive".  I was about to buy into this LaCie-Mandriva crap, thinking it was beyond joe-users to get a bootable USB drive working, and then I found DaBruGo's simple, clear how-to.  

It failed once because of the 'cant find sda1' panic that Brett mentioned earlier in the thread, but then I re-did it and it worked.  I think the only thing I changed was to write my vim files with : x (I was using :wq).  But it seems silly if that was a factor.  Anyway, it's working now, I'm pleased as can be and typing this from my my favorite browser (Firefox) on my new favorite Linux distro (Ubuntu) running from my external Seagate 80GB drive (in enclosure).

Again, much thanks to DaBruGo - people like you make this community work.

---

### Post by psanta on 2006-01-06
Kudos DaBruGo!

Great HOWTO!

It worked. I was looking for this information for the couple months. Now I have got my UBUNTU working and booting from my external USB Drive!

Thanks a lot for the effort of writing this down.

---

### Post by evandevo on 2006-01-06
Hi,

thanks a lot for this info on fixing the problems after the kernel update.

I changed the entries in /boot/grub/menu.lst.  I also see there that the older entries are still in place.  But the indication of root hd(0,0) was also changed to hd(1,0).  I fixed these also.  My question is,: Is the old kernel still working ?  or can I safely remove these lines ?

Sorry, perhaps this seems a stupid question, but I'm a newbie to ubuntu and linux in general.  Thanks to this fantastic thread I was able to install the ubuntu breezy to an external usb disk to try and learn.  In general thanks a lot for the very detailed info generally given in theze forums.  It helped me a lot to get up this new system.

---

### Post by thegreatnorth on 2006-01-07
I've tried about 8 times now to get it to work with no luck. The same error every time. After I finish (rescue mode) editing GRUB and remove cd to boot, everything looks like its booting fine, it jumps to a GUI and says loading "modules" then it jumps back to this screen.

I've gone over everything with a fine-tooth comb and can't figure it out.

ASUS A7N8X-E Deluxe
Maxtor 120GB SATA (Internal) (Windows XP) SCSI3 (0,0,0) sda
Western Digital 45GB IDE (External USB) (Ubuntu) SCSI3 (0,0,0) sdb
Plextor PX-716A IDE (Internal)

---

### Post by thegreatnorth on 2006-01-08
I've just tried my USB drive with another system that has no internal drive and I get the same error.

SCSI(0,0,0) sda

This time Ubuntu goes ahead and installs grub and everything on its own without asking because it knows I only have one drive. So after it failed I went through and used the guide to make sure everything looked good. All seemed ok but still fails.

---

### Post by xot on 2006-01-09
Hi,

This is my first post.This was a lovely howto unfortunately...after all the steps my setup doesnt resume after I reboot.It just boots back into windows xp instead of going into Ubuntu setup on my usb drive.
I have an external 40 gb seagate and i made sure it boots from cd rom first then  external device and then hdd.Should i go ack and try installing again?
Thanks!!

---

### Post by thegreatnorth on 2006-01-09
[QUOTE=xot]Hi,

This is my first post.This was a lovely howto unfortunately...after all the steps my setup doesnt resume after I reboot.It just boots back into windows xp instead of going into Ubuntu setup on my usb drive.
I have an external 40 gb seagate and i made sure it boots from cd rom first then  external device and then hdd.Should i go ack and try installing again?
Thanks!![/QUOTE]

In your bios I would disable booting to your internal hard drive until you are finished setting up Ubuntu.

first = cdrom
second = usb-hdd

---

### Post by Nrbelex on 2006-01-09
[QUOTE=xot]Hi,

This is my first post.This was a lovely howto unfortunately...after all the steps my setup doesnt resume after I reboot.It just boots back into windows xp instead of going into Ubuntu setup on my usb drive.
I have an external 40 gb seagate and i made sure it boots from cd rom first then  external device and then hdd.Should i go ack and try installing again?
Thanks!![/QUOTE]

If you're confident you did everything right, try hitting F2 or F12 as your BIOS boots and manually selecting the external drive (probably labelled as USB) from the list. Good luck!

~ Brett

---

### Post by Nrbelex on 2006-01-09
Hmmm - when I edited grub as detailed in repy #112 because of the new kernel, it asked me for something about encryption then double-checked it. What should be done at that point? Thanks

~ Brett

---

### Post by chaumurky on 2006-01-09
I am really frustrated! In the past I have successfully booted Damn Small Linux from a USB key so I know my ASUS P4SP-MX BIOS supports USB ZIP/FLASH boot. I thought I'd have a go with a spare WD 40GB drive in an external case and all goes well but it seems the BIOS doesn't see my drive when I try booting from it. My other BIOS boot option of USB FDD doesn't work either. I made sure I had the latest firmware and that the boot settings were correct - I even unplugged my internal HDD's but I get a 'non system disk' error. Are there any tools I can use to analyze the drives boot sector/mbr? I will have a go in another PC at work to see if it's just a limitation of my MB but apart from that I'm stumped!

---

### Post by Nrbelex on 2006-01-09
[QUOTE=chaumurky]I am really frustrated! In the past I have successfully booted Damn Small Linux from a USB key so I know my ASUS P4SP-MX BIOS supports USB ZIP/FLASH boot. I thought I'd have a go with a spare WD 40GB drive in an external case and all goes well but it seems the BIOS doesn't see my drive when I try booting from it. My other BIOS boot option of USB FDD doesn't work either. I made sure I had the latest firmware and that the boot settings were correct - I even unplugged my internal HDD's but I get a 'non system disk' error. Are there any tools I can use to analyze the drives boot sector/mbr? I will have a go in another PC at work to see if it's just a limitation of my MB but apart from that I'm stumped![/QUOTE]

Sometimes my Dell just won't see my external drive either but oftentimes just flicking the power switch in the back and reloading the BIOS allows it to be seen. Sometimes I feel it's more effective to flick the switch on the drive and restart the BIOS simultaneously, though I doubt it.

~ Brett

---

### Post by diverge on 2006-01-10
For many people unable to complete the installation process after following DaBruGo's steps, you may have the same problem as me:  Your BIOS is unable to boot to your USB device.

This may be because it either (a) lacks the ability to boot from USB or (b) can't detect your particular device.  For example, I have a Compaq computer whose BIOS says it allows USB booting, but Compaq's tech support admitted that it really wasn't able to boot from USB (meaning they didn't bother to give it the capabilities of actually recognizing USB devices).

From my own research, there are pre-existing special boot disks specificly to address this issue; just not for Ubuntu.  With this problem in mind I've started a thread with the goal of [Building the Supreme Ubuntu Bootdisk for USB/FireWire Externals]("http://www.ubuntuforums.org/showthread.php?t=115164").  I've included a bunch of resources, so hopefully it will prove useful in addressing many problems posted to this thread and, with any luck, inspire some of you reading this to step up and help make Ubuntu competitive in the realm of portability!

---

### Post by xot on 2006-01-10
Pardon my ignorance, I am very new at this.But is it possible that we install the bootloader(GRUB or LILO) on the internal hardrive's MBR and then it forcefully redirects to the USB drive??
I dont know how it would work.

---

### Post by flaccidspatula on 2006-01-10
I've been trying to instal ubuntu onto my 120 gig external.  Everything goes smoothly like you describe until I go to the vim and try to work with the plug and play code.  Seems to me like it isn't finding any file to edit, but I've tried to instal the grub into several different places, in case I had it wrong, and I get the same thing every time...
any advice?

---

### Post by Nrbelex on 2006-01-10
[QUOTE=flaccidspatula]I've been trying to instal ubuntu onto my 120 gig external.  Everything goes smoothly like you describe until I go to the vim and try to work with the plug and play code.  Seems to me like it isn't finding any file to edit, but I've tried to instal the grub into several different places, in case I had it wrong, and I get the same thing every time...
any advice?[/QUOTE]

I'm sure you've tried it but since I had a similar problem, I can't help but re-suggest that you triple check the file name you're trying to edit and make sure you're looking in the right place. My problem was solved by starting the guide anew and making sure to pay attention to every period. Where/when do you get the message in the process and what does it say?

~ Brett

---

### Post by Nate607 on 2006-01-10
I have gone through all of the steps and the onething i had to do difrent is change sda to sdb now when ubuntu loads up it does not finish installing and does not go to the desktop. Does any one have any ideas??

---

### Post by encompass on 2006-01-10
[QUOTE=xot]Pardon my ignorance, I am very new at this.But is it possible that we install the bootloader(GRUB or LILO) on the internal hardrive's MBR and then it forcefully redirects to the USB drive??
I dont know how it would work.[/QUOTE]
The great advantage of doing the grub and an install on a usb drive is the fact that you can 'take your computer' where every you go... for instance... I use a bootable linux drive to take to schooo and home, I just plug it into any computer that can boot off of use, that any new one, and I have my computer right in front of me, just as if I was at home.  Don't even need internet... have you ever seen windows do that?  I highly doubt it.

---

### Post by xot on 2006-01-12
[QUOTE=Nate607]I have gone through all of the steps and the onething i had to do difrent is change sda to sdb now when ubuntu loads up it does not finish installing and does not go to the desktop. Does any one have any ideas??[/QUOTE]
Hi,
Where exactly did you use sdb instead of sda??I'll give it a try.thanks!

---

### Post by jpinzonc on 2006-01-17
Hi. 
I have beentrying to install UBUNTU 5.10 in my external HDD. I spend the whoel weekend trying and trying and so far I have not been able to do it. It seems that the WAIT command does not work, because after the error message (ALERT! /dev/sda1 does not exist), the next line in the screen is that the USB drive have been recognized. 
Anyone have an idea of how can I past through this. 
Be advice that I am nex and I may need details...... SORRY about this
Thanks
Jpinzon

---

### Post by manthano on 2006-01-17
Worked flawlessly!  Thanks so much!  The only thing that might make it better would be to indicate what screens will come inbetween the different steps, and approx. how long some of that will take.

**System Specs:**
Thinkpad R40 (2723)
Pentium M (Centrino) 1.3 MHz 
256MB RAM
ATI Radeon 7500 
Dual booting Window$ XP Pro (internal 40GB hd) and **Ubuntu 5.10 Breezy** (external Western Digital 80GB USB hd)

---

### Post by Sephatine on 2006-01-19
Okay.. this is my first post that is actually not a question.  yay for me!

I would highly reccomend that this gets added to the first post, seeing as it will save a lot of time for a group of people.  This specifically addresses those that are having the /dev/sda does not exist error.

Tip1
Boot into grub. On the second line where it says 'root=/dev/sda1'  you need to do a bit of play.  If you have a single sata drive in your system, the usb drive is actually sda2 now.  In any case play with changing that end number that will be different based on the number of drives and partitions  I've had it range between  sda1 - 3 based on the system i was booting.

Tip2
If you leave your internal drive disconnected during the install, you can install grub without having to specify a location for it.  It will also default the grub menu to hda0 rather than hda1.

If anyone has any questions let me know.

~Marc~

---

### Post by 504harry on 2006-01-19
[QUOTE=Kyral]I'm curious, whats the performance like?

At any rate, ***very*** good job.[/QUOTE]

DaBruGo,
Great Post, could I ask the following:
As it's external, presumably any OS can be internal?
How small a HDD will 5.10 work with (within reason)?
(presumably any large working fils can be on another USB drive?)
Where did you find Vim? - on my 5.10 Gedit is there; no Vim.
Well done, that others have taken the same route means it really, really works. Perhaps Umbuntu should ship it, as a ReadMe, before that Partition-tool loads!

---

### Post by 504harry on 2006-01-19
[QUOTE=Kyral]I'm curious, whats the performance like?

At any rate, ***very*** good job.[/QUOTE]

DaBruGo,
Great Post, could I ask the following:..........

As it's external, presumably any OS can be internal?
How small a HDD will 5.10 work with (within reason)?
(presumably any large working files can be on another USB HDD?)
Where did you find Vim? - on my 5.10 Gedit is there; no Vim.

Well done, that others have taken the same route means it really, really works. Perhaps Ubuntu should ship it, as a ReadMe, before that Partition-tool loads!

---

### Post by stoner on 2006-01-19
hi im fairly new to linux and this is my first time installing linux so iam sorry if my problem is trivial, but im havin real difficulties

im trying to follow to the guide posted on the first page so i can load ubuntu onto my external usb drive but im havin a few problems.

my problem is at step 5

the system doesn't ask me to pick a partition to mount, which could be the source of the problem im havin in step 7:
in step 7 i type in mount -tproc proc /target/proc
and the terminal prints:Mounting <some other text> failed to mount invalid file or folder

does any1 know what im doing wrong?

---

### Post by cpro on 2006-01-19
I have just install Ubuntu onto a 30GB external hard drive.  

Thanks for the tips DAVE you are truly an asset to the linux community.

---

### Post by Sephatine on 2006-01-19
stoner,

I recieved this message once during my numerous attempts at playing around with this.  Be sure that your usb drive is being recognized in the bios prior to running the resuce steps.

Also if you want to avoid the headache on this account, try disconnecting your internal drive during the installation process.

~Marc~

---

### Post by stoner on 2006-01-20
cheers for the advice marc. the bios definatly recognises the usb drive and ive setup the same way dave says. but there is 1 thing that might be messing things up. the bios calls the usb a floppy drive i expand a tab and it shows the name of the hard drive and has (usb) next to it. so i think i can boot from usb. but im still not sure why im not prompted to mount the partition in step5

---

### Post by scotty boy on 2006-01-21
[QUOTE=jpinzonc]Hi. 
I have beentrying to install UBUNTU 5.10 in my external HDD. I spend the whoel weekend trying and trying and so far I have not been able to do it. It seems that the WAIT command does not work, because after the error message (ALERT! /dev/sda1 does not exist), the next line in the screen is that the USB drive have been recognized. 
Anyone have an idea of how can I past through this. 
Be advice that I am nex and I may need details...... SORRY about this
Thanks
Jpinzon[/QUOTE]

Im having the exact same problem. The usb support loads fine but the boot fails because the drive hasnt been recognised in time. After crashing to the shell, the drive is recognised within seconds. No amount of playing with the "WAIT" command has changed this, im not even sure it does anything, as when i put it to 120, the system definately does not pause for 2 minutes.

Any help would be really appreciated.

--- Marty

---

### Post by crsd36 on 2006-01-24
Hi all-Im super new to Linux and am having problems.  I was doing okay--I think--until step 10.  Sorry if this is a repost...I dont have time to flip through all of the pages for I am in between classes

> (10) Recompile (recreate) the initrd.img file to include USB support from these edited files ...

mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386

NOTE: Be sure to use the most current initrd.img file version numbers when using this command (they may be using a version higher than the 2.6.12-9-386 version that was available when I originally created this help guide)

I thought I did this correctly but got an error message that said

      touch:  cannot touch '/boot/inititrd.img/img-2.6.12-9-386/lib/modules/2.6.12-9-386': No such file or directory

Is there something I am doing wrong?

Thanks for the help!

---

### Post by s5GbJReJ on 2006-01-24
[QUOTE=javier.blazquez]I followed your directions and was finally able to install Ubuntu 5.10 Server on a 512MB USB stick plugged into a VIA EPIA MII motherboard.

Thank you very much.[/QUOTE]

I will be trying a USB install of Ubuntu 5.10 Server on my VIA EPIA 5000 as soon as it ships in - will tell you how it goes!

:p

---

### Post by Vangelis on 2006-01-24
Fantastic procedure! I followed it and it worked like a charm. Only thing is now that I have changed computers and so my set of devices has changed. X won't start up and who knows what other drivers are not correct. Is there a way of telling Ubuntu to redetect all devices and reload new drivers as required? I don't want to have to reinstall although that will be my last option.

Thanks in advance for any help!

Vangelis

---

### Post by supercarrera on 2006-01-25
Great tutorial.  I was able to load to my 1 gig usb flash drive and boot from it.  Everything was going good on the initial boot up until it ran out of space on my flash drive and stopped while it was loading all the modules and stuff.  How can load only the essential modules on the initial boot so that I don't run out of space?  Is this even possible?  I'm an newbie so any help would be appreciated.  Thanks!

---

### Post by supercarrera on 2006-01-25
Oh, uh never mind.  I just saw the threads on Ubuntu server, lite, etc..

---

### Post by Nrbelex on 2006-01-26
Ok - so I updated my kernel and tried to update the GRUB list as I had in the past but when I followed the steps in post #112, I am given the following instead of the list which we changed before:

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours

```

Thanks!

~ Brett

---

### Post by gecko46 on 2006-01-26
After changing the BIOS as suggested, i tried the method, but it failed at the end of Step 3.  /dev/sda was obviously not correct for my system.  Trouble is, i'm left with a system that will only operate with the Live disk because i had loaded GRUB onto my internal hard drive as Ubuntu said to do at the beginning.  When i try to boot up, the system stops dead at the point that GRUB is supposed to run.   i enter a command line after it to get in to remove the GRUB line in my config.sys file so i can access XP... :( :( :(  Trouble is, my normal computer guy knows nothing about Linux and is suggesting a complete reformat of my hard disk which would destroy some very important files i can't afford to lose.Can someone help?  A reply to gecko46 at swissinfo.org would be MOST appreciated.

---

### Post by gecko46 on 2006-01-26
i *can't* enter a DOS command line (see above for details of my problem -- should have changed the title on it as well.)

---

### Post by Nrbelex on 2006-01-27
Well the good news is that you can use the live cd to salvage the important files if worst comes to worst. How did you change your BIOS? Can you use the live cd in rescue mode to try to redo GRUB until you get it right? 

~ Brett

---

### Post by mickola on 2006-01-27
hi there,

i successfully installed ubuntu on my external drive.
the problem is when i boot my computer, i got this message:

GRUB Stage 1.5
error 2

anybody?

---

### Post by DaBruGo on 2006-01-27
[QUOTE=mickola]hi there,

i successfully installed ubuntu on my external drive.
the problem is when i boot my computer, i got this message:

GRUB Stage 1.5
error 2

anybody?[/QUOTE]

mickola,

In the first post of this thread (at the bottom) I have a link to GRUB error codes. 

Look in section 14.3 of that web page and it may give you a hint on what your problem may be.

Hope that helps,


DAVE

---

### Post by DaBruGo on 2006-01-27
[QUOTE=Vangelis]Fantastic procedure! I followed it and it worked like a charm. Only thing is now that I have changed computers and so my set of devices has changed. X won't start up and who knows what other drivers are not correct. Is there a way of telling Ubuntu to redetect all devices and reload new drivers as required? I don't want to have to reinstall although that will be my last option.

Thanks in advance for any help!

Vangelis[/QUOTE]

Vangelis,

I don't know if this will help, but azz posted a reply in another thread that may help you. He is a very knowledgeable guy.

[http://www.ubuntuforums.org/showpost.php?p=395865&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=395865&postcount=3")

I know from personal experience that X doesn't act real well with PCs that have the video integrated onto the motherboard (like most DELL Optiplex PCs). It usually requires some fiddling around to get it working right.


DAVE

---

### Post by DaBruGo on 2006-01-28
[QUOTE=CrunchyDoodle]I had a similar kernel update experience and fixed it pretty much as you did. I was a little surprised it did what it did, since you'd think the updating script would have looked at and retained what was obviously working and needed for the system to boot correctly. But no, it ignored what was working.

I do realize that loading up an external USB drive with ubuntu is a bit unusual. And that it does present some unusual drive mappings with the internal drive being ancillary and the external drive logically being the main boot drive. However, it's not that wierd.    :smile: 

Maybe next time it will be right.     ;) 

Bye.     :cool:[/QUOTE]

CrunchyDoodle,

I think I may have found what the problem was for us.

There was a line in my GRUB menu.lst file that read ...
# groot=(hd1,0)

I changed it recently to read ...
# groot=(hd0,0)

And, when I used the desktop auto-update feature tonight to update the linux-image file, everything worked without the menu.lst file getting goofed up.

I believe what happened was that (when I originally installed Ubuntu to the external drive) GRUB created that groot line, but it was somewhat incorrect. 

Because, during the install process, my external drive would have originally showed up as (hd1,0) because my internal drive (with XP on it) was currently (hd0,0).

But after installation (according to GRUB) my external drive was really (hd0,0) because that was where I had loaded GRUB to. 

So, by changing the groot line to read (hd0,0) that made things right because (after installation) my external drive would really be (hd0,0)


I hope that made some sense,
DAVE

---

### Post by chammi on 2006-01-28
I'm guessing, based on the description and other posts that you're on your own if you decide to take your USB HD to another computer--esp. it can't boot to a USB device, huh?

It's too bad there's no way you can use a Live CD to scan for the hardware profile and load the USB drivers before booting the HD. 

Ideally, you could even tell the CD to re-scan the computer or use a preset on the HD (like your "home" computer) to save time.  If I knew more about how Live CDs and Kernels worked, I might be able to write something myself. Maybe someone else will. If Klaus Knopper can invent a Live CD that recognizes USB devices, certainly someoen can figure this one out.

---

### Post by bradhawk08 on 2006-01-28
Hey so everything worked ok (this has been the only way that it has installed on the hard drive thus far) until i exited rescue mode and it restarted and it couldn't find the the boot record or something.

So I took the hard drive out of my external enclosure and put it internally as the master drive.  It goes into the Ubuntu load up screen, but then it exits saying ALERT! /dev/sda1 not found 
it says something about exiting to the shell

Help! I'm so close but yet so far.  Thanks for the suggestion of putting on via usb drive.

---

### Post by pomalin on 2006-01-29
Here there is a solution to put a live cd on usb hdd, and boot from it.
Juste download the split files and recompose it with "cat" extract to your usb hdd, download USBootout.iso and burn it on a mini cd.
Boot from the cd, it will mount your usbhdd as a cdrom on every computer with internal ide hdd.

[http://usbuntu.info](http://usbuntu.info)

---

### Post by benz240 on 2006-01-29
OK newbie here so forgive my idiocy:

I am attempting to install 5.10 on an external, USB 2.0 hard drive, which is connected to my Thinkpad T42p laptop.  I run windows on an unpartitioned internal HD, which I would like to keep completely untouched.  So I followed the procedure outlined here and another site ([http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#secondhdd)](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html#secondhdd)).

No problems booting from the install CD, and when the installation program asked to setup the partitions, I selected the option for making a second and third partition on the USB drive (resized the existing single partition which had some music on it) for ext3 and swap.  It did this without a problem, and then proceeded to install all of the system files.

However, after that, I attempted to setup GRUB on the USB drive (I don't want it on my internal HD, as I'd like only invoke GRUB when I select the USB drive on the device list at bootup).  I was getting errors when I manually set it to install at /dev/hdc1, as instructed in the website above, so I tried /dev/sda5 as suggested in the install screen.  Still I got errors.  So I eventually tried /dev/sdc1 and it worked, and completed installation.  However, if I select the USB drive from the device list at startup I get "Missing operating system".

Is there any way to get back to that part of the installation of Ubuntu and try a different part of the USB drive?  I think it needs to be on the MBR of the external drive, but I'm not sure how to go about this.

Thanks for the help!

---

### Post by daibak on 2006-01-29
Some months back DaBruGo and this thread, in a very roundabout way, encouraged me to persist to break away from WinXP with an external FireWire 160GB disk drive. Even though I never succeeded in booting from the external drive as this thread explains so well for USB 2.0 drives I've been a happy dual-booter with Ubuntu 5.10 for the past two months, nowadays rarely booting Windows at all. Ubuntu is all most heavy users will ever need!

So how did I get there? Mercifully this 2002-purchase, HP Pavilion notebook PC came with a factory freebie: USB 1.1 Mitsumi floppy disk drive. The secret was to grab GAG in current version 4.5d and choose at boot which OS I want,  and I've never looked back.  After all the terror scenarios I tried and tested for two months I'll never consider installing a dual-boot scenario ever again without a GAG floppy or 'El Torito' CD at hand to circumvent the inescapable GRUB error messages you'll get when you first try to load Linux.

Here's a link to the free dual-boot [GAG]("http://www.majorgeeks.com/download2588.html") boot-loading manager I use, it's great!

---

### Post by scotty boy on 2006-01-29
[QUOTE=bradhawk08]So I took the hard drive out of my external enclosure and put it internally as the master drive.  It goes into the Ubuntu load up screen, but then it exits saying ALERT! /dev/sda1 not found 
it says something about exiting to the shell.[/QUOTE]

This problem has been troubling me for the last 2 weeks and I finally solved it tonight. I am currently posting from Ubuntu.

The problem occurs because there isnt enough time between when the usb support is loaded and when ubuntu looks for the usb drive. After much time looking at the boot image I came up with this fix.

Do this before step 10 (in rescue mode):

Create a new script file that will tell the system to wait, giving it time to recognise the external drive.

vim /etc/mkinitramfs/scripts/init-premount/acpid

which will create a new file. To this file add :

```
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

```

Save with : x

After doing this continue with step 10 :D

Let me know if this solves this problem for other people - it did with me :)

--- Marty

---

### Post by bradhawk08 on 2006-01-29
so if i screwed up and installed the GRUB to the master boot record is there a way to undo that?  can i use fdisk /mbr? will that erase my entire hard drive or just clean the master boot record? what effects will fdisk /mbr do? 
please help...

forget about this... i figured it out... using fdisk /mbr will clean the master boot record and restore proper booting.

---

### Post by bradhawk08 on 2006-01-29
Okay so everything loaded up fine EXCEPT after making all the changes to the files through RESCUE setup I restart my computer, the computer won't boot into Ubuntu.  The cd has been pulled out and I tell my computer to boot from the USB Hard Drive.  My BIOS start up order is 
1st: CDROM
2nd: USB HDD
3rd: Disabled
Yet, after all of this the computer boots up to Windows XP regardless of whatever boot instructions I give it.

I need help so that I can finish the installation and use Ubuntu.

---

### Post by scotty boy on 2006-01-30
If you cleared the MBR on your external hard drive it is likely grub is no longer installed there. Try the install procedure again, and dont forget the extra step I included if you were getting the "ALERT! /dev/sda1 does not exist" error.

--- Marty

---

### Post by mickola on 2006-01-30
[QUOTE=DaBruGo]mickola,

In the first post of this thread (at the bottom) I have a link to GRUB error codes. 

Look in section 14.3 of that web page and it may give you a hint on what your problem may be.

Hope that helps,


DAVE[/QUOTE]

hi dave,

thanks! problem solved! i gotta change the hd(0,0) to hd(0,1).

for noobies like me, try this out: [EXT2 IFS for Windows]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm"). it allows you to read & write linux partition from windows. i used it to edit GRUB's menu.lst from windows using my favourite text editor, NOTEPAD2... :)

---

### Post by DaBruGo on 2006-01-30
[QUOTE=mickola]hi dave,

thanks! problem solved! i gotta change the hd(0,0) to hd(0,1).

for noobies like me, try this out: [EXT2 IFS for Windows]("http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm"). it allows you to read & write linux partition from windows. i used it to edit GRUB's menu.lst from windows using my favourite text editor, NOTEPAD2... :)[/QUOTE]

mickola,

Thanks for posting your success. I'm glad you got it going! (Did you originally load GRUB to sda1 or just sda?)

By the way that's a great software tip too!

I may add that to post #1 :) 


DAVE

---

### Post by bradhawk08 on 2006-01-31
Where do I install grub? the instructions say to install it to the external hard drive. is that hard drive suppose to be in the list of drives that comes up when you manually tell it where to install the grub? or is it the /dev/<the name that you started with, such as sda or sdb>? i think this is probably the reason that my computer won't boot is because it's no finding grub on the right partition or something of the external. please help. i've been trying since thursday night to install. thanks.

---

### Post by h0bbe on 2006-02-02
Does anyone had any success on installing a bootable Ubuntu on a USB stick yet?

---

### Post by brotorious on 2006-02-03
This tutorial is GREAT!  Problem is, I discovered it a little too late, and now, no matter what I do, whenever I try and load Ubuntu from the GRUB loader, the splash will come for a few seconds before disappearing and informing me that

"ALERT! /dev/sdb1 does not exist. Dropping to a shell!"

Here's my tale of woe:

Wanting to install Ubuntu on a portable drive, I found a tutorial that was fairly cryptic in nature, and not nearly as thorough as this one.  The author said nothing about not installing GRUB on the MBR, and it was right after I did this that I discovered THIS (the good) tutorial.

I followed this tutorial from step 5 onward, but even after 6 hours of messing with settings, the end result is always the same:  Grub loader will boot to Windows just fine, but it will not boot Ubuntu.

Keep in mind a couple things that may make my case unique: I'm trying to install this on a Dell Inspiron 6000 laptop, and (I believe that) because I have an Intel Centrino chip, the kernel ends in -686, not -386.  Additionally, my system hard drive is labeled as sda, and my external drive became sdb.  

Something odd I'm noticing about booting up:

One of the things I've tweaked in startup is increasing the wait time from 12 seconds to 30, and no matter what, bootup halts after around 8 seconds: it will say it loads the kernel file (then gives a memory address), it will load initrd file we created (again, gives a memory address below that), it will display the splash for a few seconds, and then will drop back to text, displaying it's signature "/dev/sdb1 does not exist."  

I've run fdisk and I'm sure it's the right linux partition.  I've also tried appending mptbase and mptscsih to /etc/mkinitramfs/modules and recompiling, same error.  Changes I make to /boot/grub/menu.lst (for example, renaming the initrd file) will show up during bootup, but the same error occurs.

Oh yes!  I believe it's important to note that I left my primary hard drive ahead of my usb drive in the boot sequence, because that's where the GRUB loader is loaded, and it wouldn't load the other way.  Also, in the menu.lst file, my windows boot was (0,1), and my linux drive was (1,0).  I tried changing my external drive to (1,1), but to no avail.  

So, after 6 hours of fiddling with this, I decided that I must be getting these errors because I installed the GRUB loader on the wrong drive, and decided to completely reinstall, this time doing it EXACTLY as stated in this tutorial.  

After this, I got the EXACT SAME error when trying to load Ubuntu (/dev/sdb1 does not exist), and windows wouldn't load at all.  I reinstalled Ubuntu a third time, this time installing grub to the MBR again, and now windows will load but Ubuntu gives me the same error.  

So here I am, back with a clean slate and a machine that boots to Windows but not to Ubuntu.  I find it odd that changing the wait doesn't affect anything at startup... it's almost as though the changes I make aren't showing up, but I know that's not true because I can change the names in menu.lst to match a file i compiled with a different name, and it will show up in the text right before the error /dev/sdb1 message with a happy memory address.  

Any advice you can give would be more than welcome!  Please help me solve this problem!  I'll be happy to answer any questions you have, forgive me if I was vague in my setup, but it's safe to assume that I've followed instruction word for word the 2nd and 3rd time installing, except that I've replaced the -386 with -686 in the Kernel-related stuff because that's what's loaded on my system.  Also, I'm not sure if it matters, but i'm loading off the dual live/install DVD, not the install CD, but rescue mode still works great.  

Thank you in advance for your help, I'll be sure to keep everybody up to date on my situation if it changes, and on any improvements that come about from suggestions here!

~Andrew

---

### Post by Muggz on 2006-02-03
Sounds difficult to install and easy to screw up your PC.  I might wait for Linux to mature.

---

### Post by brotorious on 2006-02-03
To follow up: I went ahead and restored the Master Boot Record on my main hard drive, and reinstalled everything EXACTLY, and I get the exact same error.  I guess installing GRUB to the internal drive was not the problem.

---

### Post by koinonia on 2006-02-04
Hi,

I'm new to ubuntu and trying to install it unto a USB hard drive. I've followed to your instructions to the _**detail **_ but am not able to get past step 5 - the prompt of which partition to mount. It always takes me back to the installation phase. There are a couple of people with this problem in this thread but it seems like no one has posted any solutions to it. 

To summarise my problem, I've ensured the boot disk is in the cdrom drive, the bios can detect the USB drive and also entered 'rescue' when ubuntu is re-started. Would appreciate very much if someone can help me with this.

Thanks a lot in advance!!

---

### Post by daibak on 2006-02-04
[QUOTE=brotorious]To follow up: I went ahead and restored the Master Boot Record on my main hard drive, and reinstalled everything EXACTLY, and I get the exact same error.  I guess installing GRUB to the internal drive was not the problem.[/QUOTE]

I tell everybody about the free GAG 4.5d multi-bootloader manager on floppy disc or bootable CD mentioned in my last post #166 because it's such a simple solution. I'd installed Ubuntu 5.10 just fine but could never get GRUB to load it. Then it dawned on me, let GAG 4.5d bootloader try and find any operating system and give me the choice to load whichever I want at startup. Bingo, I can choose Breezy with GRUB or Windows.
You don't need to lug a floppy drive device around - if I'm going to take this HP notebook out of its dock/port replicator, I'm careful to shut down in Windows. That way PC remembers the last MBR written and re-boots (without floppy) normally into Windows. If I need to boot Linux, I connect floppy drive and it steps me through GRUB perfectly to load Breezy in a blink.
Puzzled why brotorius~andrew and so many others seem to ignore GAG tip - it certainly put an end to my two months of grief uselessly trying to get GRUB to work alone with Breezy as this thread teaches others so well.

---

### Post by scotty boy on 2006-02-04
[QUOTE=scotty boy]Do this before step 10 (in rescue mode):

Create a new script file that will tell the system to wait, giving it time to recognise the external drive.

vim /etc/mkinitramfs/scripts/init-premount/acpid

which will create a new file. To this file add :

```
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

```

Save with : x
[/QUOTE]

This is what worked for me to get rid of the dreaded ALERT!

--- Marty

---

### Post by brotorious on 2006-02-04
Thanks for the feedback, guys!  I'm running Linux now from my external drive, and the thing that got it working was modifying /etc/mkinitramfs/modules by adding a couple lines and **Making sure they were in this order:**

ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod

Looks like all of modules needed to read my external drive were not loading in the order necessary during startup.  I hope this helps somebody down the road!:D

---

### Post by DaBruGo on 2006-02-04
[QUOTE=brotorious]Thanks for the feedback, guys!  I'm running Linux now from my external drive, and the thing that got it working was modifying /etc/mkinitramfs/modules by adding a couple lines and **Making sure they were in this order:**

ehci-hcd
uhci-hcd
usb-stroage
usbcore
usbhid
scsi_mod
sd_mod

Looks like all of modules needed to read my external drive were not loading in the order necessary during startup.  I hope this helps somebody down the road!:D[/QUOTE]

brotorious,

Thanks for your post! I may add your comments as a note to that section in my first post. It may help others using similar hardware. 


good job,
DAVE

---

### Post by chammi on 2006-02-04
[QUOTE=pomalin]Here there is a solution to put a live cd on usb hdd, and boot from it.
Juste download the split files and recompose it with "cat" extract to your usb hdd, download USBootout.iso and burn it on a mini cd.
Boot from the cd, it will mount your usbhdd as a cdrom on every computer with internal ide hdd.

[http://usbuntu.info](http://usbuntu.info)[/QUOTE]


Good thing I can read French, huh?  Merci pour ce lien.  ;)

---

### Post by foresto on 2006-02-04
To begin with, thanks so much for the very helpful guide!  Except for the small problem I'll describe below, it worked perfectly using initrd.img-2.6.12-9-amd64-default (instead of initrd.img-2.6.12-9-386) in step 10.

[QUOTE=kch_86]Hi, I would like to say thanks for the HowTo. But I have a problem. I followed the tutorial step by step, but when I reboot after step 12, I get an error from the bios that says boot failed. Any ideas?[/QUOTE]

The first time I tried to reboot after step 12, I got this message from GRUB:

```
GRUB Loading stage1.5
GRUB loading, please wait...
Error 18
```

On a lucky hunch, I found that it was caused by the boot order in my computer's BIOS.  While installing Ubuntu, I used this order:

[INDENT]Removable Drives:  Floppy
CD-ROM Drives:  CD-RW drive,  DVD-RW drive
Hard Drives:  External USB (my Ubuntu target),  RAID (my internal drives)
[/INDENT]
That worked fine for installing, but in order to make GRUB happy after the step 12 reboot, I had to use this boot order:

[INDENT]Removable Drives:  Floppy
Hard Drives:  External USB (my Ubuntu target),  RAID (my internal drives)
CD-ROM Drives:  CD-RW drive,  DVD-RW drive
[/INDENT]

Even with nothing in my CD/DVD drives, placing them before my hard drives interfered with the boot process.  For the record, this was an ABIT AN8 Ultra motherboard.

---

### Post by scrondle on 2006-02-05
I wish I had found your article on Friday night instead of Sunday afternoon. You rock. My internal hard disk died and this will give me a great alternative until the internal one comes back. Thank you.

Kjel

---

### Post by mättu on 2006-02-05
Tanks, Dave!
:-)
Easy install, very good instructions, everything went fine.

There was a short moment of panic, though: 
In the moment the installer started to write the files, the LED showing activity on my internal (winXP) HD went on. I already planned a long night session to get all "live-important" functions back up, but in the end nothing was written on the internal HD.
Now I'm far too excited to go to bed, so let's grab a perfectly chilled beverage and enjoy.. (know that one?) ;-)

Thanx again, very much appreciated!
:m)

By the way, anybody know how to build partitions on the external disk larger than 32GB using FAT(32) readable both to Windows XP & linux? (win's internal disk-tool seems to be unable to do so, partitions by linux-gparted are unreadable to win, but when purchased the disk contained one big 160GB-Fat-anything-partition clearly write-and-readable to both systems.)

edit: solved with qtparted

---

### Post by srirampcl on 2006-02-06
I tried this instructions in my **Dell Inspiron 600m** with Windows XP professional. It worked great. Thanks for the info. You really rock!!!

I followed instructions as per [post#2]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") for getting Windows XP through GRUB.
If I set root as (hd1,0) (See [post#2]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2")), it starts the Dell diagnostic utility. I changed the root to (hd1,1). It worked!!!

Here is the /boot/grub/menu.lst entry for Windows XP in **Dell 600m**.

```
title Windows XP Professional
root (hd1,1)
map (hd1) (hd0)
chainloader +1
```

Hope this is useful. 
Was any one able to get the system(under Ubuntu) to hibernate ?

---

### Post by DaBruGo on 2006-02-08
[QUOTE=mättu]

By the way, anybody know how to build partitions on the external disk larger than 32GB using FAT(32) readable both to Windows XP & linux? (win's internal disk-tool seems to be unable to do so, partitions by linux-gparted are unreadable to win, but when purchased the disk contained one big 160GB-Fat-anything-partition clearly write-and-readable to both systems.)

edit: solved with qtparted[/QUOTE]

mattu,

There is another way to format partitions greater than 32GB as FAT32. 

If you have a windows 98 boot disk handy with fdisk and format on it, it can be done without having to purchase a partitioning program.

XP by default always formats a drive larger than 32GB as NTFS. But if you boot with the 98 boot disk and use it's version of fdisk to partition the drive (choosing (Y)es for the large hard drive support option) and then reboot with the 98 boot disk and format it, then XP should be able to use the partition with no problem (when you reboot again without the 98 boot disk).

You may also be able to copy the 98 versions of fdisk and format (either off a cd or boot disk) and place them into a special folder (that you create) in Windows XP for these types of issues. (Just be sure NOT to overwrite the XP versions of these!) I have not tried this personally though, but it should work.

Just wanted to share that for anyone else with similar problems.


DAVE

---

### Post by easy on 2006-02-08
Hi all.

Dave thanks for documenting your hard work.
i would love to get this going.
I am having the same issue as some others that I have seen posts for but none have recieved any replies. So this is sort of a "bump" and a recap.
My bios does suport booting from a USB device.
The boot order is CDrom then USB drive.
Installation of ubuntu goes fine following Daves instructions carefully and step by step.
when I reboot with ubuntu still in the drive I get the ubuntu prompt. I enter "rescue"
It then goes into the installation process but this time with "rescue" in the top left of the screen.

Thank you in advance for your help
cheers
e.

---

### Post by DaBruGo on 2006-02-10
[QUOTE=easy]Hi all.

Dave thanks for documenting your hard work.
i would love to get this going.
I am having the same issue as some others that I have seen posts for but none have recieved any replies. So this is sort of a "bump" and a recap.
My bios does suport booting from a USB device.
The boot order is CDrom then USB drive.
Installation of ubuntu goes fine following Daves instructions carefully and step by step.
when I reboot with ubuntu still in the drive I get the ubuntu prompt. I enter "rescue"
It then goes into the installation process but this time with "rescue" in the top left of the screen.

Thank you in advance for your help
cheers
e.[/QUOTE]

easy,

You may want to try the approach that daibak used in [post #179]("http://www.ubuntuforums.org/showpost.php?p=705347&postcount=179") just to see if it would work for you since you don't have boot support for USB. Give that a try and let us know if it works for you.

You might also want to take a look at [post #181]("http://www.ubuntuforums.org/showpost.php?p=705797&postcount=181") to see if maybe you need one of the items listed to be able to boot from USB. You never know, it just might work by adding all those items listed to the modules file in step 8.


DAVE

---

### Post by CousCous on 2006-02-10
This thread is full of excellent information.

I'm totally new to Linux. I've been fooling with it here and there from Live CD's for a while now though. This thread really got me interested in installing it.

So interested that I went out and bought a USB 2.0 PCI card so I could run my external drive with that instead of Firewire.

I'd like to jump right in with the install cd, but I have some questions about this whole thing.

I have Windows XP Home installed on my internal hard drive. The external drive I want to use has a lot of data on it that I don't want to lose stored using NTFS.

I used PartitionMagic on the external drive and created a 10 GB Linux ext2 partition and a 1 GB Linux swap partition. I expected that would help, but after reading the tutorial here again I'm not so sure. Can I install Ubuntu to that partition and skip the auto-partitioning during the install process?

My computer is also pretty old. It's BIOS doesn't have a boot from USB option. I've had BootMagic installed on my internal disk for a while now though. I notice that in Windows BootMagic detects my external drive and the Linux partition. Will it be possible to use that to boot Ubuntu?

I've searched this thread many times. A lot of my questions have been touched on, but I'm having a hard time making head or tails of it all.

Any help would be great. I hope this is all possible because I love Ubuntu.

Thanks,
Matt

---

### Post by RyanGT on 2006-02-10
The partitioning should be pretty straight forward and yes just choose the manual option instead of the auto-partioning.  One problem you may have though is that a boot partition has a maximum size (it might be 2GB), so it is probably best to create a third partition using partition magic.  My boot partition is something like 300 megs.  I think you can also choose autopartitioning and tell it too keep all non-linux partitions (though I may be remembering that from Fedora).

I think you will need to install first and then try BootMagic and see what happens, unless you can find someone who has it working with Ubuntu on an external harddrive.

---

### Post by CousCous on 2006-02-10
Thanks Ryan!

I'm glad the partition I made won't go to waste. I figured there was an option in the installer for something like that. I'm just kind of nervous about trying it out.

Is the boot partition size limit unique to Linux or is it a BootMagic thing? I hadn't heard of that before.

I think you're right about trying to install it. That's the only way I'll know if BootMagic detects it. I'm pretty sure I have to install Grub or LILO on the Linux partition too. I don't think BootMagic does it all by itself.

At least that's what I read in the BootMagic FAQ.

I hope someone who dual boots Ubuntu with BootMagic can help me clear it up. Either way I'm gonna try to install Ubuntu before the day's over.

Thanks,
Matt

---

### Post by RyanGT on 2006-02-10
I don't know where the limit comes from and I don't even remember what it is, I just remember letting the auto-parition thing do the partitioning for one of my installs and it likes to make one root partition and one home parition.  The boot partition is part of the root partition and that puts a size limit on the root partition that I didn't like.  I much prefer a small, seperate boot partition and root and home on one other large parition.

Just be careful to specify something like grub hd1 to make sure you don't overwrite the MBR of your internal hard drive (which should be hd0).  Your external may be more than hd1 if your internal is partitioned at all.  If you do accidentally overwrite the MBR of hd0, don't panic.  I think almost anyone who has tinkered with Linux and try to make a computer dual boot has screwed up their MBR at one point.  It can be recovered - you haven't screwed up windows at all - you just can't boot into it right now.  Too that end, you may won't to have a bootable CD around with an MBR fixing program.  I think microsoft may even have a downloadable one for free ("Look at us, we will help save you from nasty linux.")

---

### Post by RyanGT on 2006-02-10
Hey Matt,

FYI, I had started a very similar thread a while back and it details everything I did to get Breezy installed on my USB HD:
[http://ubuntuforums.org/showthread.php?t=75439](http://ubuntuforums.org/showthread.php?t=75439)

There may be some information there that isn't in this thread (and there may not).

Ryan

---

### Post by CousCous on 2006-02-10
Thanks Ryan. This is all extremely helpful.

I think my internal drive has two partitions. One 50 or so MB FAT32 partition for BootMagic and then the rest of the disk is NTFS for XP.

The external drive I want to put Ubuntu on has three partitions. The first being an NTFS partition, the second being my Linux ext2 partition, and the third being the 1 GB Linux swap. I'm kind of confused about how the Ubuntu installer labels disk drives and partitions.

Would that make hd0 my BootManager partition and hd1 my Windows partition? If that's the case then I'm guessing my Linux partition would be hd3.. or higher.

The Ubuntu Disks Manager from the live cd tells me that my internal drive's Windows partition is located at /dev/hde1 and my BootMagic partition is at /dev/hde5. My external drive's Linux partition is located at /dev/sda5. The NTFS partition on the external drive is /dev/sda1 and the Linux swap partition is /dev/sda6.

It's different in the installer though, right?

I'm starting to get a little confused. I wish I were more confident about all of this. I'm printing out your thread right now since I'll need it when I install.

Does the installer give you a list of choices when choosing these drives and partitions or do you have to type them in? If they all have to be entered by hand then I'm going to have a hard time. I need to learn more about how Linux structures everything I guess.

Thanks,
Matt

---

### Post by RyanGT on 2006-02-10
I may be making this more confusing than it really is.  The problem is that there are two different naming conventions: one for Linux in general and one for grub.  Linux will call your internal partitions hda1, hda2, hda3,... and if you actually had a seperate, physical internal harddrive (like a slave-IDE drive) it would be hdb and have partitions hdb1, hdb2,...  Linux will call your USB drive sda and its partitions sda1, sda2, ...

Grub doesn't use the letters and starts numbering at zero.  So, your internal hard drive is hd0 and its partitions are referred to as (hd0,0), (hd0,1),... And your USB harddrive is probably hd1 with partitions (hd1,0), (hd1,1),...

I think the only thing you need to know to do the install is that you probably want to install GRUB on hd1 (it goes on the MBR and therefore doesn't need a specific partition).  

Ryan

---

### Post by CousCous on 2006-02-10
That makes a lot more sense than what I was thinking.

So other than skipping the auto-partitioning I should follow DaBruGo's step by step to the letter. The only thing holding me back now is the thing about the boot partition. Should I go ahead and reboot into Windows and make one real quick with PartitionMagic?

That's the only thing I'm still confused about. I hope I'm not being too much trouble with all of this. I want to be safe though.

How does the installer and loader know which are which. Does it give me a choice or something? I could easily spare another 300 - 500 MB on my disk to create a boot partition if it's really necessary.

Matt

---

### Post by RyanGT on 2006-02-10
You could try it without creating another partition.  If the manual partitioning dialog won't let you create one 10 gig partition that includes the /boot partition, then go back and create it with partition magic.  I think the partitioning is fairly early in the install process, so it isn't too painful to go back and do it again if you need to.

Ryan

---

### Post by CousCous on 2006-02-10
I guess I did something wrong. My external drive is unreadable now by both Windows and Ubuntu. I don't know what happened.

Windows doesn't know what to do with the drive. It asks me if I want to format it when I try to access it. PartitionMagic still shows all of the partitions, but the drive label is messed up.

The drive is reading as RAW now.

Matt



*Update:*

Everything's fine now.. I'm still not running Ubuntu, but I think it's installed at least. The boot sector of the primary NTFS partition was corrupted on my external drive. I think I did something wrong when I was installing Grub.

I fixed it with some software I found though.

I had to sleep on it. I'd been awake for around 24 full hours when I messed it up last night. I was pretty upset, but when I woke up I knew exactly what to do. I fixed it before I even got my coffee.

I'm still eager to get Ubuntu installed and bootable. This didn't deter me at all. I think the fact that my disk was so easy to fix actually encourages me to try again.

Thanks,
Matt

---

### Post by easy on 2006-02-11
[QUOTE=DaBruGo]easy,

You may want to try the approach that daibak used in [post #179]("http://www.ubuntuforums.org/showpost.php?p=705347&postcount=179") just to see if it would work for you since you don't have boot support for USB. Give that a try and let us know if it works for you.

You might also want to take a look at [post #181]("http://www.ubuntuforums.org/showpost.php?p=705797&postcount=181") to see if maybe you need one of the items listed to be able to boot from USB. You never know, it just might work by adding all those items listed to the modules file in step 8.


DAVE[/QUOTE]

After many hours of trial and error and following every link I could find I couldn't make it go. Maybe my mobo doesn't suport usb boot even though it is supose to and it allows you to pick usb devices in the bios.
In the end I just wanted to run ubuntu. So I bit the bullet, did some partitioning and installed to my C: drive.

---

### Post by DaBruGo on 2006-02-11
[QUOTE=chammi]Good thing I can read French, huh?  Merci pour ce lien.  ;)[/QUOTE]


chammi,

If you need to translate info from a foreign language site, you can go to [http://babelfish.altavista.com/]("http://babelfish.altavista.com/") and enter the URL in their "Translate a Web Page" box to convert the text into almost any major language.


DAVE

---

### Post by DaBruGo on 2006-02-11
[QUOTE=srirampcl]I tried this instructions in my **Dell Inspiron 600m** with Windows XP professional. It worked great. Thanks for the info. You really rock!!!

I followed instructions as per [post#2]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") for getting Windows XP through GRUB.
If I set root as (hd1,0) (See [post#2]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2")), it starts the Dell diagnostic utility. I changed the root to (hd1,1). It worked!!!

Here is the /boot/grub/menu.lst entry for Windows XP in **Dell 600m**.

```
title Windows XP Professional
root (hd1,1)
map (hd1) (hd0)
chainloader +1
```

Hope this is useful. 
Was any one able to get the system(under Ubuntu) to hibernate ?[/QUOTE]

srirampcl,

Thanks for posting your experience. You probably had to choose (hd1,1) instead of (hd1,0) as the root partition because DELL (and I believe COMPAQ) places a special partition on the hard drive as part of their installation process at the factory.

I may add that to message #2.

Thanks for sharing. 


DAVE

---

### Post by RyanGT on 2006-02-11
I am glad to hear you fixed it.  That scared me a little.

I have read some threads that talk about how to use the install CD's to just install GRUB.  I don't think you have to redo everything.

Ryan

---

### Post by RyanGT on 2006-02-11
Here is one such thread:

[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub)

---

### Post by CousCous on 2006-02-11
Wow that's good stuff. There's even a post mentioning BootMagic. That's what I need to do, I think.

I need to install Grub onto the root partition I made for Ubuntu. Thanks for finding that thread. You've been really, really helpful. I feel right at home here because of you.

I haven't ever gotten good help like this for any Windows problems before.

I'm still not totally clear on the way Grub handles disks and partitions. I noticed during the install last night that I had the option of using /dev/sda5 instead of the hdx,x format. I might use the /dev/sda method this time if I have a choice.

I'm about to re-read the posts you made yesterday and then I'll probably try and get Grub onto my root partition. I think I'll use the Install CD method.

Thanks Ryan,
Matt

---

### Post by DaBruGo on 2006-02-11
Hi folks,

I found a [web link]("http://www.linqi.org/linux/lomd.html") to creating a bootable GRUB CD that may help those out without USB boot support. It's a little sketchy on some of the details but may help those willing to give it a try.

Maybe someone has a better link they would like to share that details this approach?

Hope it helps.


DAVE

---

### Post by RyanGT on 2006-02-11
Hey Matt,

Glad to help.  The post above about a bootable GRUB cd may get you started without getting GRUB on your HD.  Another trick to be aware of is that you will need to have your BIOS set to boot from the USB drive before the internal harddrive.  My BIOS resets the order whenever the USB drive is unplugged.  Having GRUB on the USB MBR doesn't do any good if the BIOS is booting from the internal HD first (it will never even check the USB MBR).  I don't know if BootMagic gets you around that.  The GRUB CD may also solve any problems you have with not being able to boot from the USB because of an older system.

I really love Ubuntu and think it is worth the pain of getting through some of this stuff.  I would say its only weakness is that the forums aren't quite as quick to get responses as some of the Fedora ones.  So, I am doing my part to try and improve that.

Ryan

---

### Post by CousCous on 2006-02-11
I'm starting to think that maybe my BIOS is going to be a problem.

I followed the steps in the thread you linked to about re-installing Grub. I got Grub onto the right partition this time. When I tried booting into Windows however the computer froze while detecting my USB drive.

I turned off the drive and rebooted. Then Windows loaded normally. Once Windows started I turned the drive back on and Windows is reading it just fine. I'm not sure why that's happening now.

So with the USB drive turned on I opened BootMagic. It detected that I had Linux installed on my external drive. I added it to my list of operating systems so I could choose it during my next boot.

I rebooted the computer. When BootMagic appeared it had a list with "Windows NT/2000/XP" as the only selectable choice. Under that it had "X Unavailable" where Ubuntu should have been.

I'm thinking that BootMagic doesn't load any USB drivers. The function isn't built into my BIOS either. So I'm kind of stuck at the moment.

I think the next thing I'll do is try DaBruGo's suggestion and Daibak's suggestion to use GAG. I'm starting to worry that this might just not be possible with my system though. It's pretty old. I think I got it in 1999.

That's the biggest reason I want to run Linux on it too though. It's old, but it runs much better with Ubuntu's Live CD than it does Windows. I've even got some hardware that works under Ubuntu, but XP won't touch.

I really appreciate all of your help. I'm not giving up on this until I know for sure that it's impossible. If you're shooting for quick and helpful responses then you're hitting the bullseye. Without your help I wouldn't have gotten this far without breaking something.

Thanks,
Matt

---

### Post by RyanGT on 2006-02-11
I assume from your post about buying a PCI card that this is a desktop and not a laptop computer.  Is your USB drive simply an enclosure around a normal IDE hard drive or did you buy it as a seperate enclosed HD that you should open?  I was just wondering if as a trouble shooting method there was any way to hook up the external drive as an internal drive and see if it boots.  If that works well for you for a while, maybe you could get some cheap 20gig hard drive and do this all internally.

If you are having BIOS problems, I think the GRUB on a CD thing is your best approach.

Ryan

---

### Post by CousCous on 2006-02-11
I just typed up a big response, but then I hit refresh and lost it.. I'll try to type what I remember.

This is a desktop, but I'm not too familiar with installing hard drives internally. The external drive is just an enclosure with a 3.5" disk drive inside. I *think* I have at least one empty internal 3.5" drive bay inside this computer. I'm not sure if there's a spot for me to hook it up in there though.

I'll read up on installing hard drives and see if it's viable. It probably is, but I just don't have the experience to say so now. It would sure make a lot of things easier.

I was just reading the link that DaBruGo posted earlier about putting Grub on a CD. It looks like it has to be done from inside Linux. Would that work from the Live CD?

For some reason I don't think Ubuntu detects my CD-R drive. I wouldn't be able to burn it from there, but maybe I could write the iso to a FAT32 partition. Then load up Windows and burn it with Nero.

I'll read up on installing that hard drive internally. I'll have a look around inside my computer too and see if I've got everything I need in there.

Thanks,
Matt

---

### Post by RyanGT on 2006-02-11
Basically all you need to connect it internally is enough IDE connections, a power connection, and proper setting of the master/slave jumper.  Most mother boards support 4 total IDE drives: a master and a slave for the primary and secondary connections.  So, if you only have one internal harddrive and one or two CD-roms/writers, you most likely have at least one connection.  Basically open the case and look at the ribbon cables connected to the CD drives and the harddrive.  If there is an unused 50pin connection on either of the two ribbons, then that is what you need to use.  Two drives will share the same cable, so just make sure that one o them is jumpered to master and the other is jumpered to slave.  There should be stickers or a little sketch somewhere on each drive telling how to set up the jumpers to make it the master or slave.  It shouldn't really matter which is master and which is slave, but you may have to mess with BIOS settings to change the boot order.  

For a quick test you could even just unplug the current harddrive and plug your other one in and see if it boots.  The only reason it wouldn't is if GRUB or BootMagic is not on the (currently external) harddrive.  

I think I have even seen GRUB on a floppy.  I think I actually have a Fedora rescue floppy that might work as a boot disk.  You could search for one in google.

I don't see why you couldn't make the GRUB CD from the live CD, except that you would need a way to burn it to disk.  Maybe someone has an iso you can download from somewhere.  It also be possible to create the iso from the live CD, save it somewhere and burn it from windows.

---

### Post by RyanGT on 2006-02-11
here is a link from googling grub boot disk:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RESCUE](http://www.yolinux.com/TUTORIALS/LinuxTutorialRecoveryAndBootDisk.html#RESCUE)

---

### Post by RyanGT on 2006-02-11
Another option that is slightly more complicated and risky is to put GRUB and your 300meg boot partition on your internal harddrive.  GRUB would then always start up every time you boot your computer and you would choose Ubuntu or Windows.  The kernel that would be stored in this boot partition would contain the drivers for USB and would boot the USB drive from there.

The trick with this is that you are formatting a portion of your internal harddrive and so there is some risk to damaging that drive.  You would have to create the partition with Partion Magic or something like it that has the ability to shrink your existing NTFS partition.

---

### Post by CousCous on 2006-02-11
I'll definitely try some of these suggestions. I've got a few things that I need to get finished first though. I'll probably check out the cables inside my computer tonight when I get a chance.

I'll post back.

Matt

---

### Post by DarthOverlord on 2006-02-14
Can the USB drive be attached to different computers and boot the same version of Ubuntu if the chipsets are the same (ie. 386)?

I installed Breezy onto a USB hd and am running it off my gaming machine.  Works great.  

I was curious if I can plug my laptop into the usb and get ubuntu running with the same settings.

---

### Post by LivnLarge on 2006-02-14
its funny that installing an os on an ext harddrive is such a big topic since I guess its hard to do.  When it should be relatively easy, as the process mentioned to do so it logical.  What bothers me is getting a BIOS to recognize the USB harddrive.  Now how is that done?

Thanks in advance fellow linux nerds.

---

### Post by DarthOverlord on 2006-02-14
On my motherboard, the USB was listed as a hard drive in the bios, so if you put it first in the boot sequence you should be good.

---

### Post by jdpipe on 2006-02-14
Hi all,

First post for me. Trying to install linux on my new USB drive, thought ubuntu probably looked like the easiest option.

I tried carefully to follow the instruction from this thread (I read it all!) and to install Ubuntu on my external USB drive. After making the suggested changes to the grub menu.lst, I get a GRUB "error 16" after booting. Apparently this means "inconsistent filesystem structure".

During the 'rescue' boot, I selected my device from a list, and it was "/dev/discs/disc2/part1". I was able to mount it in rescue mode just fine, but it doesn't boot.

I tried editing the menu.lst to hd0,0 as well as hd2,0 (a wild guess, given the 'disc2' above)

But neither of these work. Under Fedora Core 4, I am able to plug in the USB drive and view the files, so obviously the filesystem structure is fine. It is simply a question of settings.

I also tried adding extra modules to initrd, as follows:
ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod
This didnt make any difference though.

What's the next thing I should try?

I am thinking the 'usbuntu' boot ISO... Or FC5...

RE post #218, I also moved my USB drive to be the first HDD in the boot ordering.

---

### Post by jdpipe on 2006-02-14
**Fixing your Windows Master Boot Record (MBR)**

I know it's probably evil to publish a windows how-to here, however like one or two others in this thread, I managed to overwrite my windows MBR during my attempt to install ubuntu on my USB hard drive. These instructions apply to Windows 2000, hopefully the process is similar on XP and others.

For fix this, you need to get your original windows CD and boot from that CD. You need to enter the 'repair' mode, then go to the 'recovery console'. Select your "C:\WINNT" installation (whatever/whereever it is). Then at the console, type

fixmbr
then,
fixboot

Then you can type 'exit' and reboot (take out the CD first). Windows should be running OK again now.

There are some caveats about this that would be worth reading up on carefully before you jump in head-first though. Be careful. For example, read here:

[http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/prork/prcb_dis_dgya.asp](http://www.microsoft.com/resources/documentation/Windows/2000/server/reskit/en-us/Default.asp?url=/resources/documentation/Windows/2000/server/reskit/en-us/prork/prcb_dis_dgya.asp)

---

### Post by DaBruGo on 2006-02-16
[QUOTE=jdpipe]Hi all,

During the 'rescue' boot, I selected my device from a list, and it was "/dev/discs/disc2/part1". I was able to mount it in rescue mode just fine, but it doesn't boot.

I tried editing the menu.lst to hd0,0 as well as hd2,0 (a wild guess, given the 'disc2' above)

[/QUOTE]

jdpipe,

If this is the second drive in your system, then your discs command should read as follows ...

"/dev/discs/disc1/part1"

And, the menu.lst file should read (hd0,0) if you installed GRUB to the external drive like I did and set it to be the first drive in the boot sequence in your BIOS.

Hope that helps,
DAVE



*** FYI: SECTION 5 OF POST #1 ...
 
(5) When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your external drive from the list.
(Mine was mount /dev/discs/disc1/part1 ... but yours may be different depending on the number and/or types of drives in your system)

COMMENT: /dev/discs mount points start with disc0 (with 0 meaning the first drive in a system). So, my mount point of /dev/discs/disc1/part1 was really the second disk (the sda drive we are working with) and the first partition on that disk.

*** FYI: SECTION 11 OF POST #1 ...

(11) Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...

vim /boot/grub/menu.lst

Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).

There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 

INSTALL NOTE: You may want to change the root line for the Windows XP section in this file to (hd1,0) just in case you have XP loaded on an internal drive and want the option to boot into XP from the GRUB menu. (See post #2 for more info.)

Be sure to save the file changes (using : x)

COMMENT: Feel more comfortable editing this file in Windows? See post #171 for a program that will let you edit files on linux partitions from within Windows. (Kudos to "mickola" for the suggestion.)

---

### Post by archis on 2006-02-18
DaBruGo, I followed your tutorial right down to the last step 13 without problems -- but when it's time for the BIOS to do its thing and load from the USB drive it just switches back to the internal HD no matter how I change the first boot device setting. If someone here can post a success story with an Asustek motherboard (Asus N7N8X-X, Award BIOS rev. 1009) and a USB hard drive, I would certainly like to hear it. Anyway, I decided to make room on the internal and go through a normal installation routine there. The resulting Grub installation on the MBR noticed my root partition on the USB drive as well and I should have a perfectly functional triple-boot system.

However, when I select the USB boot partition, grub returns an error 21 - 'Selected device (hd1,1) does not exist'. I need a little advice in pinning this down, so please correct any of the following if I'm in error:

I have two separate menu.lst files, one on each drive, but only the one on the internal drive matters cause I'm not booting from USB. So any of the changes I made to the menu.lst file on the USB in accordance with DaBruGo's tutorial (i.e. changing the device mappings because grub handles them 'relative' to its own location) are irrelevant. (Hopefully, I can get it to work anyway!). Now, the menu.lst file on the internal drive was generated by the grub install process as part of my second installation of Ubuntu and should be accurate (right?). It gives me /dev/sda2 as the alternative boot partition and that sounds right to me (I've got a large FAT32 partition at the beginning, then the boot partition, then a home partition and finally a swap partition on the USB drive). Thus, the 'second' partition on the 'second' drive (hd1,1)..

So right now I am thinking it's probably not a wrong device specification in the menu.lst file but it might be. Is there something else I need to take into account? -- Could this be about lacking USB support during bootup, i.e. do I need to amend the /etc/mkinitramfs/modules file for the internal ? But if that's the case, then why am I already successfully calling a swap partition on the USB drive while booting from the internal drive (both installations share a swap partition located on the USB drive)?

P.S. One thing I'm going to try later on is to go into the grub command line and just tab through the device entries, just to double check on the available devices. Or better, go invoke the grub shell and type **find /boot/grub/stage1**, which should hand me my two stage1s - unless there is a problem and grub actually can't see the USB drive...




Any comments appreciated.

---

### Post by archis on 2006-02-18
The actual error message is **Error 21: Selected disk not not exist** which "is returned.. if the device, part of a device-, or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system." Furthermore, the grub command line hands me only fd0 and hd0 as available devices - no hd1. So is this really a BIOS problem, not a grub problem? But again, how does this square with the fact that I am using the USB drive for a swap file without problems?

---

### Post by archis on 2006-02-18
I want to think aloud for a moment - please help me get this straight. 

IBM's Martyn Honeyford [writes the following about booting from Firewire or USB](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html):




[INDENT][FONT="Lucida Console"]Before I discuss booting up your new drive, a little boot loader theory is required.

Boot loaders are usually installed in the MBR of the first hard disk in the machine. When the boot loader is invoked (the BIOS automatically executes the code in the MBR), it usually displays a menu of possible OSes to boot. Selecting a given OS causes it to boot up.

Two things should be noted about this scenario:

    * The menu of OS choices is (usually) loaded from disk
    * To boot the relevant OS, the bootloader needs to read the relevant kernel from disk

As the above takes place before the OS has been loaded, it means that all of the disk reading must take place by way of BIOS calls. This has a very serious implication: namely, that in order to boot the disk directly, your BIOS must support disks connected via FireWire or USB.[/FONT][/INDENT]



If I understand correctly, this means that *direct* booting from USB depends on the ability of the BIOS to use it as boot drive (to 'wait' for the USB drive to initialize etc.) and *not* on the ability of the kernel to deal with USB drives, be it patched with modules via initrd (Martyn's **two-phase boot**) or recompiled (**one-phase boot**).



[INDENT][FONT="Lucida Console"]This can typically be seen as a BIOS option to boot from these types of disk. FireWire BIOS support is currently very rare indeed, but USB support is becoming reasonably common. Therefore, if you are using USB on a relatively recent machine, it should be possible to boot the drive into Linux directly.

After installing GRUB in the MBR of the external drive, I was able to boot it directly when connected via USB. Simply enter the BIOS setup utility while booting with the disk connected. The external disk will appear as a regular hard drive: move it so it is before the internal drive in the boot order.

I was also able to install a boot loader in the MBR of the internal drive and use that to boot the USB drive (where it appeared as hd1 in GRUB).[/FONT][/INDENT]



The first scenario Martyn describes is the one Dave has laid out. The second one is the one I have on my system right now - a boot loader on the internal drive that would boot the USB. Because no there's no OS running when you are looking at the Grub menu, both of these methods rely on the BIOS. And this is where Dave's module patching or Martyn's two-phase boot come into the picture: even though a compliant BIOS will allow you to start up the kernel from the USB, you still don't have a file system to mount and thus the need for the initRAM disk until the 'real' root is up. Dave's method involves adding a WAIT routine to initramfs.conf while Martyn [has a linuxrc script that he folds into the initrd.img](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html) that 'waits' for the USB or Firewire drive to come up.

The kernel patching or recompiling also comes into play when you're using a secondary device or partition (for example a floppy, a [boot CD](http://www.bootdisk.com/) or a separate boot partition on your internal drive) in order to get your USB-installed OS off the ground.

In this scenario, the kernel cannot be on the USB drive because the BIOS isn't capable of booting from it. It has to be in a place the BIOS *can* use. There, it mounts the initrd and switches to the real root once the USB drive is initialized. 

So the most convenient solutions involve either getting the BIOS to boot from USB or [using a boot CD](http://ubuntuforums.org/showpost.php?p=690569&postcount=166) such as [GAG boot loader](http://gag.sourceforge.net/).

Am I getting this right?

---

### Post by Cth on 2006-02-18
I understand that someone was getting ALERT! /dev/sda1 does not exist.
I have the same problem. What was the fix?
Chris..

---

### Post by cdsboy on 2006-02-19
I did all of the steps that are asked for. Then when i boot my computer it does grub and then instead of starting ubuntu i get a terminal-ish screen that says grub > and i have no idea what to do...

---

### Post by archis on 2006-02-19
OK, I've figured it out now and it works exactly as I want it to. I've got a triple-boot system now, with Windows and Ubuntu dual boot on the internal drive and an additional install on the external USB. I have two boot loaders, one in the MBR (Master Boot Record) of the internal drive and one on the USB drive ([COLOR="Olive"]/dev/sda[/COLOR]) on my machine. [COLOR="Olive"](Note: I'm not sure whether the second boot loader's location is actually /sda or /sda2, i.e. at the beginning of the drive or at the beginning of my boot partition. This is being determined during the grub installation, see [step 3 of Dave's tutorial](http://ubuntuforums.org/showpost.php?p=436420&postcount=1)).[/COLOR]

I can bring up the different boot loaders ('grub menus') according to the boot order set in the BIOS. My BIOS boot order is either [FONT="Lucida Console"][COLOR="Olive"]CD-ROM > HHD-0 > USB-HDD[/COLOR][/FONT] or [FONT="Lucida Console"][COLOR="Olive"]CD-ROM > USB-HDD > HDD-0[/COLOR][/FONT]. I just flip around the second and third entries to boot up from either drive (the USB drive is connected most of the time).


[INDENT][FONT="Lucida Console"][COLOR="Olive"]Here's a sketch of my setup[/COLOR][/FONT]
[INDENT][ATTACH]6255[/ATTACH][/INDENT][/INDENT]


The key part for me was to kick the BIOS into shape and allow me to boot from the USB drive. 

The grub menu is just a file, menu.lst, read from the disk. As such, it is only as good as the last human or machine that edited it. All activities at this stage of the boot process take place via BIOS calls. This means the BIOS has to be able to see the USB drive, otherwise the boot will fail. Initially, I could only get into the Grub menu on the internal drive ([COLOR="DarkSlateBlue"]Grub on /dev/hda[/COLOR] in my sketch) because the BIOS didn't allow me to boot from the USB. I could then choose the kernels located on the USB drive in the grub menu (because grub had found them when the system was fully booted) but would receive 'error 21: disk does not exist'. You can press Ctrl-Alt-Delete to reboot. Back in the grub menu, you can get a grub command line by pressing 'c'. By the way, [you can use the grub command line to do your research for you.](http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You) For instance, you could type 

[FONT="Lucida Console"][COLOR="Olive"]find /boot/grub/stage1[/COLOR][/FONT]

Instead of getting back two locations as I would have liked to see - [FONT="Lucida Console"][COLOR="Olive"](hd0,3) (hd1,1)[/COLOR][/FONT] I only got one - [FONT="Lucida Console"][COLOR="Olive"](hd0,3)[/COLOR][/FONT]. Again, confirmation that the problem was not with a wrong entry in menu.lst but with the BIOS. 

In fact, my BIOS problem resolved itself very easily -- I simply had to enable USB keyboard support in order for the drive to boot. Even though that's rather quirky and far from obvious, it has been mentioned before here on this thread and elsewhere. All I can say is - be methodical when you try to get your BIOS to work with USB.

Next, the USB drive finally boots up and finishes the Ubuntu installation that had been stalled at stage 13 of the tutorial. On the desktop, you'll probably receive a notice of further upgrades and a new kernel waiting for you to download. On reboot, I am again greeted by a grub error message, this time it's 

[FONT="Lucida Console"][COLOR="Olive"]root (hd1,1)
Filesystem type unknown, partition type of 0xf
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash
Error 17=cannot mount selected partition
[/COLOR][/FONT]

What's going on? Looks like the menu.lst got changed - root (hd1,1) is a dead giveaway, since I had specifically changed my kernel roots from (hd1,1) to (hd0,1) (tutorial step 11). Apparently what happens is quite simply this: [FONT="Lucida Console"][COLOR="Olive"]update-grub[/COLOR][/FONT] runs after each kernel update and adjusts the list of available linux kernels in the menu.lst file. More precisely, it updates the lists of kernels between the lines 

### BEGIN AUTOMAGIC KERNELS LIST

and

### END DEBIAN AUTOMAGIC KERNELS LIST

[More here](http://www.ubuntuforums.org/showthread.php?t=57858&highlight=grub-update). 

update-grub uses certain default parameters that are contained within that same section of menu.lst, commented out with a single #. One of the parameters is 

[FONT="Lucida Console"][COLOR="Olive"]## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)
[/COLOR][/FONT]

This value should correspond to the location of the root partition on the USB drive **relative to the location of the grub boot loader**. To take my setup as an example, groot should be set to (hd0,3) (the 'fourth' partition on the 'first' volume) for the MBR grub and to (hd0,1) (the 'second' partition on the 'first' volume) for the USB grub respectively. 

[INDENT][ATTACH]6255[/ATTACH][/INDENT]

AFAIK, if it isn't set properly, [FONT="Lucida Console"][COLOR="Olive"]update-grub[/COLOR][/FONT] will change the root to incorrect locations in the menu.lst file every time it runs (or every time you invoke it on the command line) and you'd have to go in and change them back again. So, I'd propose to add the changing of the groot value to step 11) of the tutorial... 


I hope this helps!

---

### Post by Cth on 2006-02-19
Looking for help!! or someone to work with.

I read  line by line how to install on a USB Hard drive. I get Alert! /dev/sda1 does not exist. I see someone had this problem, but I did not see what the fix was.****

Chris..

---

### Post by erakepio on 2006-02-19
I too had the same problem and followed the guide line for line.

for some reason..once i installed the operating system, mine kept referring the location of my drive to /media/sda1

i tried different combinations in menu.lst in the /boot/grub/menu.lst but it didnt seem to have an effect no matter what I did.

I dont know whehter it differes for USB devices and USB HDD..perhaps it differes for each manufacturer (i imagine it wouldnt)  but I've tried installing it to USB about 6 or 7 times now..following line for line but cant seem to get any success.

The USB was the only drive connected to the system at the time as I was a little wary of overwriting the WinXP part of the system.

would like a solution if possible.  Thanks

Erakepio

---

### Post by Cth on 2006-02-19
I have been playing it safe and doing this with a old p3 500mhz computer with the USB drive as the only drive.I can install ubuntu to it and work with the files.

The USB drive is for my IBM laptop that will boot up ok. It  can see the USB HDD ok.
It is tough not knowing linux!!!!

Chris.

---

### Post by erakepio on 2006-02-19
ok it would seem that it's auto mounting my USB drive to the /media/sda1  position so i need to turn off auto mounting within linux.

Any ideas suggestions or even ways around this?

---

### Post by Cth on 2006-02-20
GOT this to WORK !!\\:D/

---

### Post by erakepio on 2006-02-20
Cth - how did you get this to work? im still having problekms with mine

---

### Post by Saxegaard on 2006-02-20
Hi exeryone,

First of all, I would like to thank DaBruGo for this incredibly clear and well-explained how-to.

I have successfully reach the step 10, but I'm now facing a problem : whenI type the command :

```
mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
```

I have the message :

```
Cannot find /lib/modules/2.6.12-9-386
```

I didn't have any problems, so I don't understand why it is buging now.

Thank for your help.

---

### Post by Saxegaard on 2006-02-20
Okay, I have found what was wrong.

I had to type : 2.6.12-9.686 instead of 2.6.12-9.386.

I used the command :

```
ls /lib/modules
```

I think it could be good to add this tip in the first post.

---

### Post by yager on 2006-02-21
[QUOTE=blixa]moonlord - I had the same problem - only booting up and stopping at the grub prompt.

So I repartitioned the drive - putting a 10G ext3, followed by a small swap, and then with a FAT32 for the rest.  I reinstalled - and it works.  I might have also worked if I kept the drive all ext3 and had a small /boot partition at the start of the disk.
blixa[/QUOTE]

I too had the same issue with an 80GB Seagate.  According to the Grub docs, the Error 18 I was getting was due to the size being bigger than my BIOS could handle.  During the install I went with a manual partitioning of the external drive and set the primary at less that 8GB.  I then set a swap the same size as the auto routine and then set the remaining portion of the drive as EXT3 just as the primary.  Everything worked fine and the system mounted both partitions with no problems.

Later, I did some searching and found that I did not have the latest version of my BIOS so I upgraded the BIOS and re-installed again a fresh copy.  This time I followed the exact instuctions with no issues at all.  

While I felt clever overcoming the small problem of the GRUB error, I felt kind of foolish when all I needed to do was maintain the updates on my BIOS.

---

### Post by yager on 2006-02-21
[QUOTE=archis]when it's time for the BIOS to do its thing and load from the USB drive it just switches back to the internal HD no matter how I change the first boot device setting. [/QUOTE]

While I don't have your motherboard, I had a similar problem with my Gateway Essex class motherboard.  

Even though my BIOS said is supported booting from the USB and I set it up to boot in the order of CD, Floppy, External, HD, it always went to the first hard drive.

I started to poke around in my BIOS settings and noticed that if I had the external plugged in during reboot, it showed up as an available hard drive and not as a USB device.  I had to change the boot order of the hard drives in the BIOS hard drive sub-menu.  Once I saved the changes and rebooted, no problems, booted to Grub and everything ran fine.

As a note, if I rebooted later without the external drive plugged in, the BIOS would remove the drive from the list and I would need to change the order again on the next startup.  The aggravating thing is that it always puts it at the bottom of the list so you need to edit the BIOS every time you restart after removing the USB cable.

---

### Post by archis on 2006-02-21
Thanks for this, yager. I have now solved my BIOS problem as well ([see this post]("http://www.ubuntuforums.org/showpost.php?p=749354&postcount=227")). It was trivial: I only had to enable 'USB keyboard support' in the BIOS settings and it would recognize the USB drive. Apparently, the BIOS wouldn't check for drives attached to USB ports unless you enabled the keyboard support setting. Easy to do, but certainly not obvious. I had tried various combinations of boot devices (USB-HDD, USB-FDD, USB-ZIP) and boot orders before that but no joy.

My current boot order is CD-ROM, USB-HDD and then HDD-0. This way, I boot up from the USB drive. I can change boot devices in two ways now: I simply switch off or unplug the USB drive or I change the second boot order entry to read HDD-0 in the BIOS. I haven't actually tried booting with the drive unplugged, but  switching it off doesn't remove it from my BIOS boot order - the BIOS just skips down to the next choice, HDD-0.

---

### Post by erakepio on 2006-02-21
for some reasoni dont have a USB-HDD in the boot list as an option although It's recognised as a bootable device.  bearing in mind NO OTHER HDD where on the system at that point

---

### Post by jdpipe on 2006-02-21
[QUOTE=DaBruGo]If this is the second drive in your system, then your discs command should read as follows ...

"/dev/discs/disc1/part1"

And, the menu.lst file should read (hd0,0) if you installed GRUB to the external drive like I did and set it to be the first drive in the boot sequence in your BIOS.[/QUOTE]

Hi Dave,

My system has two internal HDDs (first one has FC4 on a LVM partition, second one has XP on first partition and storage on second partition) and one external USB drive. I used /dev/discs/disc2/part1 to access my main partition on the USB drive, that worked fine.

But when I select (hd0,0) in the grub menu file, my bootup proceeds until an error message:

```
GRUB Loading stage1.5

GRUB loading, please wait... apparently.
Error 16
_
```

Just in case the GRUB loader was thinking that USB was (hd2,0) i tried that as well, but it didn't help. FYI, my USB drive is partitioned into ext3 (68GB), then FAT32 (10GB) then swap (1.5GB).

The USB drive's LED is flashing after boot, and the GRUB thing seems to have loaded off it. Is it possible that the WAIT=12 isn't long enough perhaps?

Any other ideas what could be causing this error? It's a filesystem error ("16 : Inconsistent filesystem structure") apparently.

JP

(PS: Interestingly, FC4 fails to boot if I have the USB drive connected. It falls over just after doing something with swap space, so I presume it's having trouble accessing the swap space on the USB drive as well. I connect the drive after booting and it automounts just fine)

---

### Post by DaBruGo on 2006-02-22
[QUOTE=jdpipe]Hi Dave,

My system has two internal HDDs (first one has FC4 on a LVM partition, second one has XP on first partition and storage on second partition) and one external USB drive. I used /dev/discs/disc2/part1 to access my main partition on the USB drive, that worked fine.

But when I select (hd0,0) in the grub menu file, my bootup proceeds until an error message:

```
GRUB Loading stage1.5

GRUB loading, please wait... apparently.
Error 16
_
```

Just in case the GRUB loader was thinking that USB was (hd2,0) i tried that as well, but it didn't help. FYI, my USB drive is partitioned into ext3 (68GB), then FAT32 (10GB) then swap (1.5GB).

The USB drive's LED is flashing after boot, and the GRUB thing seems to have loaded off it. Is it possible that the WAIT=12 isn't long enough perhaps?

Any other ideas what could be causing this error? It's a filesystem error ("16 : Inconsistent filesystem structure") apparently.

JP

(PS: Interestingly, FC4 fails to boot if I have the USB drive connected. It falls over just after doing something with swap space, so I presume it's having trouble accessing the swap space on the USB drive as well. I connect the drive after booting and it automounts just fine)[/QUOTE]

jdpipe,

I am not completely sure on this, but I thought I had to completely shutdown my PC whenever I edited the menu.lst file for changes to actually be recognized by GRUB. I could be wrong, but for some reason, I remember that doing a warm reboot wouldn't let the changes be recognized for me.

Are you doing a warm reboot or are you completely shutting down the PC and then bringing it back up?


Just a thought,
DAVE

---

### Post by jdpipe on 2006-02-22
Ok, I'll try that.

By the way, I notice that there's a file in /boot/grub/ called 'device.map'. After finishing the ubuntu installer, and your instructions, mine said:

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda

What does that mean to you? Should I be tweaking this to put /dev/sda at the start of the list?

---

### Post by primetime on 2006-02-23
Hmm..  Can I use a USB flash drive?  What's the minimum size for an installation with gnome?

---

### Post by DaBruGo on 2006-02-23
[QUOTE=primetime]Hmm..  Can I use a USB flash drive?  What's the minimum size for an installation with gnome?[/QUOTE]

primetime,

Yes, you can use a USB flash drive or memory stick. The only limitation is on how much space your type of install requires. For example, there are others who have loaded a very basic server install on a 1GB memory stick.

One company offers Ubuntu on a USB flash drive (the Ubuntu H2 from Pertec i believe) that is only 3 or 4 GB in size.


Hope that helps,
DAVE

---

### Post by archis on 2006-02-23
Dave had the idea of providing a menu.lst file for cross-referencing purposes. So I thought I can help by putting this up. Perhaps this helps people sorting out some of the difficulties they might be having. I've interspersed some comments along the way (see the [grub manual]("http://www.gnu.org/software/grub/manual/grub.html") for 'proper' documentation) and will add to these if needed. ;-)

-------------------------


[INDENT][FONT="Lucida Console"][COLOR="Olive"]
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
default		saved
[/COLOR][/FONT]
[INDENT][COLOR="DarkRed"]If you use 'saved' instead of a number beginning with 0, grub sets the last selected entry as the default for the next boot. Note: Only entries with the 'savedefault' option added to them will be 'remembered' at the next boot. Add 'savedefault' to any manually created entries in order to have grub 'remember' them.[/COLOR][/INDENT]


[FONT="Lucida Console"][COLOR="Olive"]## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10[/COLOR][/FONT]

[INDENT][COLOR="DarkRed"]Just make sure you don't set this to zero - if your default is set to boot a non-Linux system and you've set the timeout to zero, you will have to edit your menu.lst file before you can boot into Linux again. Instead, use the [FONT="Lucida Console"]hiddenmenu[/FONT] option to hide the grub menu and boot into your default OS.[/COLOR][/INDENT]


[FONT="Lucida Console"][COLOR="Olive"]## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu[/COLOR][/FONT]

[INDENT][COLOR="DarkRed"]Don't display the grub menu. If the command is used, no menu will be displayed on the control terminal, and the default entry will be booted after the timeout expired. The user can still request the menu to be displayed by pressing <ESC> before the timeout expires.
[/COLOR][/INDENT]

[FONT="Lucida Console"][COLOR="Olive"]# Pretty colours
#color cyan/blue white/blue[/COLOR][/FONT]

[INDENT][COLOR="DarkRed"]There are two ways to spruce up your boot menu a little: you can define a foreground / background colour scheme for the menu entries or you can add a background image to the boot menu. 

The grub manual [has a section explaining]("http://www.gnu.org/software/grub/manual/grub.html#color") the colour scheme options. [This page]("http://ruslug.rutgers.edu/%7Emcgrof/grub-images/") has all the details about creating and using a background image for grub.[/COLOR][/INDENT]


[FONT="Lucida Console"][COLOR="Olive"]## password ['--md5'] passwd
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
#[/COLOR][/FONT]

[FONT="Lucida Console"][COLOR="Olive"]#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs[/COLOR][/FONT]

[COLOR="DarkRed"][INDENT]This seems a little counterintuitive at first. You might expect any settings behind a single # to be 'commented out' and thus without effect on grub's behaviour. But interestingly they do (but only in this section of the file) -- the 'real comments' in this section are commented out twice.. ;-) That's because they are actually being used by update-grub (the script that generates the list that grub then uses) and not grub itself. See [this post](http://www.ubuntuforums.org/showpost.php?p=307133&postcount=3) for a **very** short explanation on why these settings need to be commented out with a single #.

The command-line tool [FONT="Lucida Console"][COLOR="Olive"]update-grub[/COLOR][/FONT] manages the grub menu entries between the lines [FONT="Lucida Console"][COLOR="Olive"]### BEGIN AUTOMAGIC KERNELS LIST[/COLOR][/FONT] and [FONT="Lucida Console"][COLOR="Olive"]### END DEBIAN AUTOMAGIC KERNELS LIST[/COLOR][/FONT]. This means that any changes you make to the list of kernels between these two lines will be overwritten by update-grub each time it runs (after each kernel update, for example. You can also invoke it from command line with [FONT="Lucida Console"][COLOR="Olive"]sudo update-grub[/COLOR][/FONT]) You can add more kernels or other operating systems underneath this section, where they will show up under the header [FONT="Lucida Console"][COLOR="Olive"]Other operating systems:[/COLOR][/FONT] 

update-grub uses the settings in the following section (from [FONT="Lucida Console"][COLOR="Olive"]## ## Start Default Options ##[/COLOR][/FONT] down to the line [FONT="Lucida Console"][COLOR="Olive"]## ## End Default Options ##[/COLOR][/FONT]) as default settings for the kernels it adds to its 'automagic kernels list'. For example, you can set a maximum number of kernels it adds to the grub menu (the grub menu can become quite unwieldy if you have a lot of kernels to boot from). You can set the boot options update-grub should add to each of the kernels it finds, and whether to add the memtest entry for example. [/INDENT][/COLOR]

[FONT="Lucida Console"][COLOR="Olive"]## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda2 ro
[/COLOR][/FONT]
[INDENT][COLOR="DarkRed"]These are the kernel options that [FONT="Lucida Console"]update-grub[/FONT] writes to every kernel entry in the list below. Make sure the root option points to the correct OS device containing the root partition.

Some people might be interested in setting the screen resolution for the framebuffer console (i.e. the boot messages and / or boot splash screen that you see between the grub menu and the login screen). You can add an option such as vga=791 to your default kernel options.

Here is a table you can use so it can help you decide what resolution you want to use:

```
#	colour		depth	| 640x480  800x600  1024x768 1280x1024
#	256		(8bit)	|  769      771       773      775
#	32000		(15bit)	|  784      787       790      793
#	65000		(16bit)	|  785      788       791      794
#	16.7 Mill.	(24bit)	|  786      789       792      795
```

This [might or might not work]("http://ubuntuforums.org/showthread.php?t=83201") with your particular setup (works with mine). You can try setting it as a boot option by temporarily adding it to a specific entry (press 'e' with the menu entry selected). 
[/COLOR][/INDENT]


[FONT="Lucida Console"][COLOR="Olive"]## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)[/COLOR][/FONT]

[COLOR="DarkRed"][INDENT]This is where the physical device containting root is specified in grub's device syntax. In this example, it is set to ('the second partition on the first device')  In this case, the grub boot loader is located on a drive with the OS device name [FONT="Lucida Console"][COLOR="Olive"]/dev/sda[/COLOR][/FONT]. The root partition on this drive is the second partition on the volume ([FONT="Lucida Console"][COLOR="Olive"]/dev/sda2[/COLOR][/FONT]). Thus, groot should be set to (hd0,1). [FONT="Lucida Console"][COLOR="Olive"]update-grub[/COLOR][/FONT] writes this setting to every kernel it lists below.[/INDENT][/COLOR]


[FONT="Lucida Console"][COLOR="Olive"]## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true[/COLOR][/FONT]
[FONT="Lucida Console"][COLOR="Olive"]## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false
[/COLOR][/FONT]

[FONT="Lucida Console"][COLOR="Olive"]## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single[/COLOR][/FONT]

[FONT="Lucida Console"][COLOR="Olive"]## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash[/COLOR][/FONT]

[FONT="Lucida Console"][COLOR="Olive"]## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all[/COLOR][/FONT]

[FONT="Lucida Console"][COLOR="Olive"]## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##[/COLOR][/FONT]

[INDENT][COLOR="DarkRed"]Here's the list of kernels, maintained by [FONT="Lucida Console"][COLOR="Olive"]update-grub[/COLOR][/FONT], that appear at the top of your grub menu:[/COLOR][/INDENT]


[FONT="Lucida Console"][COLOR="Olive"]
title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
[/COLOR][/FONT]

[INDENT][COLOR="DarkRed"]Here you can add more operating systems, such as a Windows OS or other OS in different locations etc.[/COLOR][/INDENT]



[FONT="Lucida Console"][COLOR="Olive"]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title	           Microsoft Windows XP Home Edition
root	          (hd1,0)
map              (hd0) (hd1)
map              (hd1) (hd0)
savedefault
makeactive
chainloader	+1[/INDENT][/COLOR][/FONT]
[INDENT][COLOR="DarkRed"]Note: This Windows entry swaps the device map for grub because grub itself is located on the 'other' drive in this example. Add this option in order to chain-load a Windows OS from a different drive. 

If you are dual-booting from the same drive your grub boot loader resides on, the entry should probably look like this (assuming that the Windows partition is the first partition, hd0,0):

[FONT="Lucida Console"]title	           Microsoft Windows XP Home Edition
root	          (hd0,0)
savedefault
makeactive
chainloader	+1[/FONT][/COLOR][/INDENT]

---

### Post by TD-Linux on 2006-02-23
I installed this and followed the instructions, and all was well (except X11 didn't start, but I have the solution to that and was in the middle of fixing it).

But... for some reason after I boot XP Pro (with the drive turned off) and then try to boot Linux again, it breaks. The startup goes fine until it gets to 'Checking battery state... [ ok ]'. At that point, the pretty kubuntu logo dissapears and it goes to a text mode, still displaying all the startup messages. And then it just sits there, doing nothing. If I press the power button, it does a fairly normal shutdown, but with an absence of the normal shutdown messages. A reinstall of Kubuntu temporarily fixed this.

EDIT: [Here]("http://ubuntuforums.org/showthread.php?t=77588") I found the actual cause of this... I had told x11  to use the ati driver instead of 'nv'. I was going to install the ati driver on next reboot. Strangely, the other time this happened, I hadn't messed with the drivers at all. Oh well, not the fault of the USB drive after all... in fact, I don't even notice I'm using the drive, except when apt-get decides to install the latest kernel, of course ;)

---

### Post by Killeroid on 2006-02-25
Hi,i was just wondering if it was possible to do the install without installing grub and if it was possible,what would be the effects.


Dumb question,please ignore me  because i am a newbie. Oh,and i successfully installed ubunut on my 60 gig hard drive with Xp on my internal drive.I would like to add this suggestion for edititng the grub menu.lst , when you reach the entry for XP and you edit it,dont forget to delete the line *#make default* or else a grub error will result when you start to boot it.

---

### Post by Cth on 2006-02-26
Will this need to be done over if you update Kernel each time?

Chris..

---

### Post by DaBruGo on 2006-02-26
[QUOTE=Cth]Will this need to be done over if you update Kernel each time?

Chris..[/QUOTE]

Chris,

Are you asking about changes to the GRUB menu.lst file?
If you are, here is what I learned about that.

There is a line in the menu.lst file that starts with ...
# groot=

As long as you have that set to the correct drive that GRUB should boot Ubuntu from, then you shouldn't have any problems (which in my case was hd0,0 because GRUB thought my external USB drive was the first drive in my system since I loaded GRUB to it's bootsector).

NOTE: whenever you update your kernel with the update application, it will change all the root lines in your menu.lst file to equal this groot value.

Since I have corrected this groot line in my menu.lst file, I have had no problems with the kernel update app.

Hope that helps,
DAVE

---

### Post by Cth on 2006-02-26
Thank you Dave,
It took me 3 days to get all of this working.Because I an very new to linux. I have a sprint AirCard that Ubuntu is working well on. I had to change the ppp/options with the help of a friend to get this to work.

So If I can keep up with the updates without it re-doing what I have done, this will be great.

Ubuntu is very nice and you guys on the forms are great.

Chris..

---

### Post by DaBruGo on 2006-02-26
[QUOTE=Cth]Thank you Dave,
It took me 3 days to get all of this working.Because I an very new to linux. I have a sprint AirCard that Ubuntu is working well on. I had to change the ppp/options with the help of a friend to get this to work.

So If I can keep up with the updates without it re-doing what I have done, this will be great.

Ubuntu is very nice and you guys on the forms are great.

Chris..[/QUOTE]


Chris,

Just remember that if you ever have startup problems in the future with the kernel update app, you can use the steps in [message #112]("http://ubuntuforums.org/showpost.php?p=593793&postcount=112") to get up and running again without having to use any recovery CDs.


DAVE

---

### Post by DaBruGo on 2006-02-26
[QUOTE=CousCous]I just typed up a big response, but then I hit refresh and lost it.. I'll try to type what I remember.[/QUOTE]

Matt,

In the future, if that happens to you (like it has to me when posting sometimes) all you have to do is hit the back button on your browser and then highlight and copy what you had just entered.

Then you can choose to post/reply again and paste what you had just copied into your message area. 


DAVE

---

### Post by brucetan on 2006-03-02
Hi Dave,

My fault for reading the complete threads of this.  I read only your first page of the installation and went ahead to install ubuntu onto my external USB HD and with the same intention to keep my existing internal HD (WinXP Home) intacted.

Unfortunately, things gone bad at the step where it asked for where to write the GRUB loader.  I said no to MBR and specific /dev/sda.

When I came the step to edit the /boot/grub/menu.lst file, it showed me a new file.  This was where I found something wrong in the installation.  When I look into /boot dir, there was empty!

I exit the vim and to reboot.  It couldn't boot from the USB and gave panic msgs.

When I disconnect the USB HD and rebooted it, it showed GRUB loading error 21 and stopped at there.

When I connected USB HD back, it showed me a list of OS choices to boot from:
(1) ubuntu ...
(2) ubuntu recovery ...
(3) other OS
(4) Window XP home

all the 1 to 3 gave me errors except 4.

From the above, I knew my internal HD had been modified by the installation process.

Initially, I thought the installation modified the MBR of the internal HD.  I tried to fix with FIXMBR but no help. Only with FIXBOOT, I managed to normalized the internal HD.

Dave, from the above, something must be wrong in my installation.  Can you advise:

(1) Is an updated installation process for ubuntu on external USB without touching my internal XP HD?

(2) Won't be simple if I just disconnect my internal HD, only with the external USB HD connected and install ubuntu?  Once it is working on external USB HD without the internal HD attached, I then reconnect the internal HD back.  I then use the BIOS' booting sequence to control with OS to boot from first.  Would this work?

Best regards,

Bruce

---

### Post by Killeroid on 2006-03-02
[QUOTE=brucetan]Hi Dave,

My fault for reading the complete threads of this.  I read only your first page of the installation and went ahead to install ubuntu onto my external USB HD and with the same intention to keep my existing internal HD (WinXP Home) intacted.

Unfortunately, things gone bad at the step where it asked for where to write the GRUB loader.  I said no to MBR and specific /dev/sda.

When I came the step to edit the /boot/grub/menu.lst file, it showed me a new file.  This was where I found something wrong in the installation.  When I look into /boot dir, there was empty!

I exit the vim and to reboot.  It couldn't boot from the USB and gave panic msgs.

When I disconnect the USB HD and rebooted it, it showed GRUB loading error 21 and stopped at there.

When I connected USB HD back, it showed me a list of OS choices to boot from:
(1) ubuntu ...
(2) ubuntu recovery ...
(3) other OS
(4) Window XP home

all the 1 to 3 gave me errors except 4.

From the above, I knew my internal HD had been modified by the installation process.

Initially, I thought the installation modified the MBR of the internal HD.  I tried to fix with FIXMBR but no help. Only with FIXBOOT, I managed to normalized the internal HD.

Dave, from the above, something must be wrong in my installation.  Can you advise:

(1) Is an updated installation process for ubuntu on external USB without touching my internal XP HD?

(2) Won't be simple if I just disconnect my internal HD, only with the external USB HD connected and install ubuntu?  Once it is working on external USB HD without the internal HD attached, I then reconnect the internal HD back.  I then use the BIOS' booting sequence to control with OS to boot from first.  Would this work?

Best regards,

Bruce[/QUOTE]
Bruce,I am also a newbie at this and i encounted the same problem you did during my first try to install ubunut on my portable hard drive. I found out that,if you had a SATA internal drive,then install grub in /dev/sda2/
Also,you could note the name and path of the drive which you partitioned and then input that line for where to write the grub loader.

---

### Post by brucetan on 2006-03-02
> I found out that,if you had a SATA internal drive,then install grub in /dev/sda2/
Also,you could note the name and path of the drive which you partitioned and then input that line for where to write the grub loader.
The internal HD is an IDE ATA.  I did try to use the name and path from the partition.  But it did not help.

I think it may be to do the Dell's way of partition the internal hd. Actually, I found out the internal HD has 3 partitions, (1) 50MB unknown (2) 90GB (windowxp) (3) 3GB for Dell's SW Recovery. 

I did try to take out the internal HD and leaving the DVDRW and the Ext USB IDE and setting boot sequence to CD, USB, Int HD.  For some reason, ubuntu installation just would not go and keep asking me for floppy and CDROM driver..

---

### Post by brucetan on 2006-03-02
Hi there,
Does any know where I get a documentation on ubuntu's 'naming' structure for the hard disk whether it is internal IDE/SCSI/SATA or external USB disk?

---

### Post by RyanGT on 2006-03-02
Internal harddrives will be named hda, hdb, hdc,... with partitions nubering from 1: hda1, hda2,...

USB drives should be sda, sdb, ....

If you need to check things out, you could boot from a live CD, without your USB drive attached and at a command prompt type:
sudo fdisk -l

This will list your drives and partitions.  You could then plug your USB drive in and re-run the command to see what changed and you would know for sure what the computer is calling your drives.

---

### Post by thexaspect on 2006-03-02
Does anyone know how I can access the drive when I haven't booted from it? I had Kubuntu 5.10 installed on an internal hard drive, that i decided to make external, and then put Kubuntu 5.10 also on the the new internal hard drive. When I try to load the external in kde it gives me an error saying:

 An error occurred while loading media:/sda1:
The file or folder media:/sda1 does not exist.

three different ones, all (i'm assuming) for the different partitions on the disk. they show up as sda1, 2, and 5 in the errors. Anybody have a clue? The drive has some important files that I would like to get off without having to completely rearrange my desk again to do it. Thanks

---

### Post by RyanGT on 2006-03-02
If you have booted from your internal drive, you should be able to just plug in the USB drive and Ubuntu will recognize it and mount it for you.

If that doesn't work, try sudo fdisk -l and if the drives are listed, try mounting them manually.  But my guess is if they didn't mount automatically when you plug in the drive, there are some errors with it.  If you create a folder called externalhd (or whatever) some where on your file system (usually in /media for convention), then typing something like sudo mount /dev/sda1 externalhd should mount the drive.

---

### Post by DaBruGo on 2006-03-02
[QUOTE=RyanGT]Internal harddrives will be named hda, hdb, hdc,... with partitions nubering from 1: hda1, hda2,...

USB drives should be sda, sdb, ....

If you need to check things out, you could boot from a live CD, without your USB drive attached and at a command prompt type:
sudo fdisk -l

This will list your drives and partitions.  You could then plug your USB drive in and re-run the command to see what changed and you would know for sure what the computer is calling your drives.[/QUOTE]

RyanGT,

Are internal SCSI drives also listed as sd* drives?

I thought someone had mentioned that in a thread somewhere , but I am not 100% sure on this because I don't have any SCSI drives in my system. I was just curious if you could confirm this for everyone's benefit.

I appreciate the time you take to help others out in here. :KS


Thanks,
DAVE

---

### Post by RyanGT on 2006-03-02
I honestly don't know and don't have any SCSI drives to check this on.

---

### Post by jdpipe on 2006-03-02
[QUOTE=DaBruGo]jdpipe,

I am not completely sure on this, but I thought I had to completely shutdown my PC whenever I edited the menu.lst file for changes to actually be recognized by GRUB. I could be wrong, but for some reason, I remember that doing a warm reboot wouldn't let the changes be recognized for me.

Are you doing a warm reboot or are you completely shutting down the PC and then bringing it back up?


Just a thought,
DAVE[/QUOTE]

Hi again,

RECAP: I installed using the above instructions, but got a "GRUB Error 16" at "stage 1.5" of the boot process.

I had access to a newer computer recently and I tried doing the installation again, according to your instructions. Using the same USB drive as before, the ubuntu installation worked fine. So now it looks like I have to work why this is failing on the older computers, and what this 'error 16' means, and how to make it go away.

These older computers have USB boot support in the BIOS but give these errors, GRUB error 15 (stage 1.5). (An aside: Fedora Core 4 doesn't even detect the USB drive on these systems using the installer.) The older system has an Intel Desktop Board D850EMD2.

I saw that some users suggested using different kernel modules on certain systems. How can I work out which ones I am likely to need? If my GRUB boot loader is failing at stage 1.5, doesn't that mean that it's not even getting to the stage of loading the kernel modules?

If I decide to give up on booting from USB, what are the minimum steps to create a boot CD with the same kernel version as I have on my USB drive?

---

### Post by Killeroid on 2006-03-02
[QUOTE=DaBruGo]RyanGT,

Are internal SCSI drives also listed as sd* drives?

I thought someone had mentioned that in a thread somewhere , but I am not 100% sure on this because I don't have any SCSI drives in my system. I was just curious if you could confirm this for everyone's benefit.

I appreciate the time you take to help others out in here. :KS


Thanks,
DAVE[/QUOTE]
Yes,my internal hard drive is listed as sda and my external hardrive which i boot ubuntu off is listed as sdb

---

### Post by brucetan on 2006-03-03
> nternal harddrives will be named hda, hdb, hdc,... with partitions nubering from 1: hda1, hda2,...

USB drives should be sda, sdb, ....

If you need to check things out, you could boot from a live CD, without your USB drive attached and at a command prompt type:
sudo fdisk -l

This will list your drives and partitions. You could then plug your USB drive in and re-run the command to see what changed and you would know for sure what the computer is calling your drives.

Thanks RynGT.

I think the suggestion to run Live Ubuntu first to check the HDs organization of your system before installation is absolutely vital if you are not familiar with Linux like me.  It shows you the correct /dev/... for each harddisk your system able to see in ubuntu and you can note it down.

In my case after running Live CD, it reported that my internal HD as /dev/sda and my external USB HD as /dev/sdb!  Which explains why the installation write the GRUB loader to my internal HD!

Also, if you find "sudo fdisk -l" hard to understand, there is a GUI disk manager on the [System] --> [Administration] --> [Disks] that would show you just like in WindowXP's.

With this experience, I would suggest this Live CD HD checking step to be included in Dave's HowTo guide.  Hope this is ok with Dave.

Thanks everyone.

---

### Post by brucetan on 2006-03-03
Hi Dave,

I reran the installation as per the first page of this thread.  When I came to step 5, it listed the following for me to select:
 /dev/discs/disc0/part1
 /dev/discs/disc0/part2
 /dev/discs/disc0/part3
 /dev/discs/disc1/part1
 /dev/discs/disc1/part2
 /dev/discs/disc1/part5
/dev/ubuntu/root
/dev/ubuntu/

I selected /dev/discs/disc1/part1, since in my Dell Inspiron 6000 notebook has 1 internal hard disk and 1 ext USB hd.

But the system showed me the following msg:
> 
[COLOR="Blue"]No shell found in /target[/COLOR]
No usable shell was found on your root file system (/dev/discs/disc1/part1).

You will now be given a shell in the installer environment instead. Your root file system is mounted on /target.

When you exit this shell, the system will reboot.

<Go Back>                                <Continue>


What should I do?

When I hit <Continue>, it shows me a blue empty screen with a white band at the bottom of the screen.  In the white band, it showed me:
> BusyBox v1.00-pre10 (Debian 2004062-1ubuntu22) Built-in shell (ash)
Enter 'Help' for a list of built-in commands.

~ #
 

The "rescue mode" didnot show on the left top corner of the screen!

When I hit [alt-F2], it showed me a black screen with white text.  The text are insmod msgs and fatal msgs.  The last line was "umount: /target: Invalid argument"

Can anyone help?

---

### Post by brucetan on 2006-03-03
hi, I just reran the installation as per the 1st pg of this thread.  Except in step 3, this time, i selected <erase entire disk SCSI3 (0,0,0) (sdb)>.  Before, I was selecting <erase entire disk on SCSI3 (0,0,0) (sdb) and partition with LVM >.  It works!\\:D/ 

Just a question and also for the others, why the installation does not work with LVM partition USB disk?

---

### Post by Killeroid on 2006-03-03
[QUOTE=brucetan]hi, I just reran the installation as per the 1st pg of this thread.  Except in step 3, this time, i selected <erase entire disk SCSI3 (0,0,0) (sdb)>.  Before, I was selecting <erase entire disk on SCSI3 (0,0,0) (sdb) and partition with LVM >.  It works!\\:D/ [/QUOTE]
Good for you.Congratulations.

---

### Post by brucetan on 2006-03-03
anyone know why ubuntu installation doesnot work with LVM partitioned USB Hd?

If this is the case, I would suggest this to be noted in step 3 of this wonderful guide.  So that the other would fall into the same mistake I did which caused me couple days to install it.  Also, it would be useful to ask the installer to run Live CD to check the system's disk definition (i.e., whether it is /dev/sda or /dev/sdb, etc) Do you agree?

---

### Post by brucetan on 2006-03-03
By the way, has anyone successfully installed ubuntu onto a SD/MMd memory?

I have inserted a 1GB SD Memory into my DELL inspiron 6000 and booted from my external USB ubuntu HD.  When I ran the [System]->[Adminstrator]->[Disks}, it can't be detected! 

Anyone has encountered this?

I am very keen to see if I can install ubuntu onto this SD memory.

---

### Post by Jonathan.Martin on 2006-03-03
Hi All.

Firstly i am a complete newbie and this is the first time I have posted. This is what I tried to achieve following this post. I had an old 2.5" laptop drive which I connected to my main machines IDE1 using an adapter and installed ubuntu following additional steps per this post. I then took the drive and popped it into a USB caddie to see if I could load from it, and adjusted the bios settings accordingly. The problem I get when I boot is:

/bin/sh: can't access tty; job control turned off

I think this may be because it was initially installed via an IDE connection, but I could be well off the mark.

If anyone can point me in the right direction I would be very happy.

Cheers,

Jonathan.

---

### Post by Viper_0 on 2006-03-03
Hi

I have done all the steps...but when I reboot, it goes to windows, doesn't appear the GRUB Menu. 
Why???

Thank You

---

### Post by DaBruGo on 2006-03-03
[QUOTE=Viper_0]Hi

I have done all the steps...but when I reboot, it goes to windows, doesn't appear the GRUB Menu. 
Why???

Thank You[/QUOTE]

Viper_0,

Is your bios setup to boot the drive you loaded Ubuntu onto as the first boot drive?


DAVE

---

### Post by brucetan on 2006-03-03
> Firstly i am a complete newbie and this is the first time I have posted. This is what I tried to achieve following this post. I had an old 2.5" laptop drive which I connected to my main machines IDE1 using an adapter and installed ubuntu following additional steps per this post. I then took the drive and popped it into a USB caddie to see if I could load from it, and adjusted the bios settings accordingly. The problem I get when I boot is:

/bin/sh: can't access tty; job control turned off

I think this may be because it was initially installed via an IDE connection, but I could be well off the mark.

If anyone can point me in the right direction I would be very happy.

Cheers,

Jonathan.

I suspect when you built your ubuntu onto the old 2.5" disk using IDE would not be compatible for it to run using USB interface.

If you can, I would suggest to connect the old disk as USB and reinstall ubuntu as per the guide again. But just watch out for a couple things (i) the correct disk path name in the step 3 and (ii) donot use LVM and  (iii) read the rest of the guide carefully.  It should work and don't give up.

---

### Post by DaBruGo on 2006-03-04
Hi folks,
 
 Some sections of post #1 have been improved with the addition of INSTALL NOTES ... based on suggestions offered by others to improve this guide.
 
If you haven't read post #1 lately, it may be of benefit for you to go back over it again. This guide keeps improving because of your comments and suggestions.
  
 Thanks for helping others find SUCCESS in installing Ubuntu on their external USB drives.
 
 
 DAVE

---

### Post by Jonathan.Martin on 2006-03-04
[QUOTE=brucetan]I suspect when you built your ubuntu onto the old 2.5" disk using IDE would not be compatible for it to run using USB interface.

If you can, I would suggest to connect the old disk as USB and reinstall ubuntu as per the guide again. But just watch out for a couple things (i) the correct disk path name in the step 3 and (ii) donot use LVM and  (iii) read the rest of the guide carefully.  It should work and don't give up.[/QUOTE]


Cheers Bruce,

I thought this might be the case and am thankful for the confirmation.  

The reason I didnt install directly onto usb is that when I select 'format the usb device and use' which is shown as a scsi in the partitioner I just get the folllowing error.

/dev/scsi/host2/bus0/target0/lin0/disk - No such file or directory

which I think could be an issue with the caddie itself (icybox). I used another usb caddie which I borrowed from a friend and this problem never arose, but after selecting to partition the drive and after 99% of formating to ext3 I got an error which stated something like 'The partition could not be formatted' - Hmm very strange.

If anyone could save me some time on this feel free to do so.

Thanks again,

Jonathan.

P.S. I never give up ;)

---

### Post by macrogeo on 2006-03-04
Hi,

I bought an internal Seagate 250GB hard drive and installed on an eStar 3.5" USB enclosure.  Windows XP Home on my Compaq 2568CL laptop "found new device" but the drive does not show up in "My Computer".  I went ahead and install Ubuntu by following DaBruGo's steps listed in "SUCCESS - Breezy loaded on external USB drive!".  Everything was going fine until I get to STEP 12:  I exit out of the terminal window by typing exit<enter> BUT DID NOT KEEP TYPING IT UNTIL THE SCREEN ACTUALLY SAYS TO PRESS ENTER.  I held down Ctrl-Alt-F1 tp get back to rescue mode terminal window and type exit<enter> to reboot the system by first removing the Ubuntu install CD.  When the laptop reboot there is no GRUB and it reboots to Windows XP Home (even though Legacy USB Support is enabled and USB (removable drives)'s boot order is before the hard drive in Setup).  The USB hard drive does not show up in "My Computer" still.

I should I do next?  So I reinstall Ubuntu from scratch?  I already turn off the USB hard drive as of now.  Thanks!

---

### Post by brucetan on 2006-03-04
Jonathan,

If you don't mind to try, I find it easy to confirm the disk configure is to run ubuntu Live CD with the intended USB disk attached. 

Once you are in, you go thru  menu [Administrator]->[Disks] and see what are the disks available to the system and their correct naming structure.

---

### Post by brucetan on 2006-03-04
MacroGeo,

Have you checked your BIOS boot sequence?  It should be USB, then Internal HD and then CD, etc Hope this is the case.

---

### Post by macrogeo on 2006-03-04
I tried brucetan's suggestion by having USB being first in the boot order but it did not help.  The USB drive shows up in Windows XP Device Manager with no error but cannot be seen in My Computer; could it be because it is not a Windows drive/partition?

---

### Post by snaik on 2006-03-05
Hi All,

my experience installing Ubuntu on External USB HDD was not very good. Got the Ubuntu installed with no problems. Changed the /etc/mkinitramfs/modules, and initramfs.conf files. Recompiled. Changed /boot/grub/menu.lst for correct drive parameters (hd0,0). Got the Ubuntu to load thru GRUB installed on /dev/sda. No problem.

But the problem starts :( the moment I try to boot the WinXP residing on /dev/hda. First due to some problem in Chain Loader, Grub is unable to boot WinXP;)  . Now if I try to boot Ubuntu once again, this time GRUB fails with Error 17 :evil: , and now GRUB will not boot either Ubuntu or WinXP :confused: .

My machine is Dell Inspiron 510m Laptop with 40GB Internal IDE HDD, BIOS can boot from Internal HDD, USB Device, CDROM, PCMCIA, NETWORK. The External HDD is USB 2.0 Toshiba 40GB.

Anyone faced this problem ?

---

### Post by jdpipe on 2006-03-05
Hi snaik

This sounds a bit similar to the problem I experienced. I concluded that just because your BIOS says it supports USB booting doesn't mean that it will work. On two older computers that I have tried usb ubuntu installation with, it failed (Error 16 at GRUB stage 1.5). I insert the same USB HDD on a newer machine and it boots fine.

Did you try adding the extra kernel modules?

I am inclined to believe that a boot CD is required on these older machines to load up the USB drivers etc, then run ubuntu off the USB HDD. Haven't worked out yet how to make one though.

Regarding booting windows, I just unplug my USB drive in that case... so much easier than solving the real problem... (I assume you didn't accidentally alter your /dev/hda MBR?)

Cheers
JP

---

### Post by Jonathan.Martin on 2006-03-06
[QUOTE=brucetan]Jonathan,

If you don't mind to try, I find it easy to confirm the disk configure is to run ubuntu Live CD with the intended USB disk attached. 

Once you are in, you go thru  menu [Administrator]->[Disks] and see what are the disks available to the system and their correct naming structure.[/QUOTE]

Brucetan,

Appologies for being a pain ;-). I already have ubuntu installed on a different machine so I booted this with the USB device attached. When checking the disk configuration for the drive it stated the device was attached (Appologies for the poor terminology) to /dev/sda with an access path to /media/usbdisk - Is it the access path which is incorrect ? If so what should it be ? I might have a play round with this to see what happens.

Cheers,

Jonathan.

---

### Post by brucetan on 2006-03-06
Jonathan,

I think it may be safer to run the Live CD first on the machine that you intended to install ubuntu onto the USB HD to see the actual access path would be.

For example, in my Dell inspiron 6000, I only found out through Live CD that my internal hd is /dev/sda and the ext USB HD is /dev/sdb....

---

### Post by DaBruGo on 2006-03-10
Hi Folks,
 
Has anybody had any luck on getting a basic server install on a USB memory stick by using this Setup Guide?
 
I have a 1GB memory stick that has been finicky on letting me install the "server" option onto it.
 
I am wondering if there are some tips/tricks that need to be done when installing Ubuntu on these specific types of storage devices.
 
 
 
Thanks in advance,
DAVE

---

### Post by biker44442005 on 2006-03-10
3 installs later, im still getting the same error. got it all installed, configured, followed all steps. grub loads, kernel starts loading, splash screen for loading comes up, then an error always occurs

"ALART! /dev/sda1 does not exist. dropping to a shell!
[83.238131] sda: assuming drive cache: write through
[83.249111] sda: assuming drive cache; write through"

with the system hanging there. 

any ideas?

windows died and i decided this was a good time to get ubuntu installed in something besdies vmware. luckily my mac is working fine as usual. 

installing onto a hp pavillion ze5185 laptop with external usb seagate harddrive in a metal gear hd enclosure.

---

### Post by sheilnaik on 2006-03-10
I just want to thank you so much for those incredibly detailed and easy to follow instructions.  Complicated things like these were the reasons I've been shying away from Linux for so long, but I recently realized that all I have to do is follow directions from expert Linux users like yourself and it's not too hard to get up and running.

Thanks again so much!

---

### Post by DaBruGo on 2006-03-10
[quote=sheilnaik]I just want to thank you so much for those incredibly detailed and easy to follow instructions. Complicated things like these were the reasons I've been shying away from Linux for so long, but I recently realized that all I have to do is follow directions from expert Linux users like yourself and it's not too hard to get up and running.

Thanks again so much![/quote] 

sheilnaik,

Thanks for the kind words, but I am by no means a Ubuntu expert. 

Much of the credit for the success of this thread comes from others who have offered their comments and suggestions from personal experience (usually involving high levels of frustration) to help inprove this setup guide. 

"People helping people" is what has made this thread one of the highest viewed topics in the installation section of the forums. That is awesome.

( I'm starting to feel all warm and fuzzy inside ... :p )
 

  DAVE

---

### Post by dps on 2006-03-12
Hi!
I'm new to Ubuntu and now I've finally installed Ubuntu Breezy 5.10 and I can say I wouldn't have made it without this extremely good instructions.:D 
I was determined to do it all the way on my external USB disk and it worked fine (almost).

As a newcomer to this OS you have to get some help, this one was really great.
The only thing I had to do in a different way was the order of "hd1,0" "hd0,0" in grub.

Again thank you Dave!

---

### Post by derjames on 2006-03-14
Hey Dave, thanks for this wonderful detailed instructions, I managed to install Ubuntu in my external hard drive (USB Maxtor 250 GB), it works now extremely well, all devices were recognised immediately, sound, video, ethernet, etc, etc... It is quite fast, There is truly a significant improvement in system performance compared vs Win XP...

My Laptop is
Twinhead Model D212A
AMD Athlon XP 1500LV
Memory 640 MB
Video VIA S3 Prosavage  32 MB shared
Windows XP SP2 and now Ubuntu Linux 5.1 Breezy Badger

Every device works fine, also all the externals (HD, of course, External sound card from Trust, 7 in 1 card reader from Bytestor, External USB Keyboard, USB mouse, USB hub. 

My External hard drive had a lot of media files, however I did not delete them, I just did use the Ubuntu partitioning tool to adjust the size of the new Linux partition, a very simple process indeed. The grub is configured in the following way If the external hard drive is not attached then the laptop enters WinXP, if the hard drive is attached Grub loads from the external HD and ask what OS have to be run...this is pretty amazing

* * * * * * Now the questions* * * * * * * * * * 

If a new kernel version  is released; apart from the changes needed to /boot/grub/menu.lst that i pretty understand :cool: 

Is it necesary to recompile initrd.img? (THis is not very clear to me)
suppose you get the kernel update. What would be the procedure?

is this correct???
1. Update the Kernel
2. modify menu.lst to change GRUB's drive notation (if any)
3. recompile initrd.img. <---this I am not sure????
4. reboot

Thanks everybody!!! 

derjames

---

### Post by KoloRahl on 2006-03-15
Hi everyone, I'm having a slight problem when trying to finish off the Ubuntu installation. I have a 120GB Western Digital external USB hard drive that I'm trying to load Ubuntu on, and I have followed every step as outlined in the directions in post #1. However, for step 13, where you reboot to your external and finish the ubuntu installation and can login for the first time, I can never get to the GRUB loader or ubuntu.

I've made sure to have my usb drive (called "rem drive", or what I assume means "removeable drive" by my computer) as the first thing to boot, and have even brought up a boot selection menu to manually select the external drive first, but nothing seems to be working. I go to a blank screen for a couple seconds and then straight to the Windows XP loading screen. As I said, no grub loader screen, no nothing. I don't even get error messages.

And since I have the files open right now I figure I may as well post my menu.lst, initramfs.conf, and modules files.

menu.lst:
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map (hd1) (hd0)
chainloader	+1
savedefault
```

initramfs.conf:
```
WAIT=12

#
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#
MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  The command line will override this setting.

RESUME=/dev/sda5
```

Finally, modules:
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod

ehci-hcd
usb-storage
scsi_mod
sd_mod
```

Any bit of help would be greatly appreciated, thanks!

---

### Post by jdpipe on 2006-03-15
I think that you might have gone wrong on setting 'rem drive' as your boot device. On most of the systems I have seen, you should set the hard drive or internal drive as the first boot priority, then there will be another BIOS option related to hard disk priority. You should open that up and you will see your USB drive along with whatever internal drives are on your system. Choose your USB drive as the first-priority amongst the hard drives.

Does that help?

---

### Post by KoloRahl on 2006-03-15
When I first went to configure the boot priority I thought this would be the case, but I haven't found a way of looking at multiple hard drives on my BIOS menu. I made sure my external was plugged in and powered up but I still only hadthe one option for hard drive, with no sub-options. My bios screen for boot priority is something like this:

1st:  ATAPI CD-ROM
2nd:  Removable Dev. (what I think is my usb drive, but seems like it isn't)
3rd:  Hard Drive
4th:  Realtek Agent Bootloader (this seems to be some weird boot agent for my internet card)

Even after I set the hard drive to the first priority I can only scroll up/down between the four using the <up/down> arrow keys, change their order by hitting <enter> or using the <+/-> keys. I tried using the <left/right> arrows keys but nothing happened. No additional bios menus or anything pop up when hard drive is in the first priority slot.

---

### Post by DaBruGo on 2006-03-15
[QUOTE=KoloRahl]Hi everyone, I'm having a slight problem when trying to finish off the Ubuntu installation. I have a 120GB Western Digital external USB hard drive that I'm trying to load Ubuntu on, and I have followed every step as outlined in the directions in post #1. However, for step 13, where you reboot to your external and finish the ubuntu installation and can login for the first time, I can never get to the GRUB loader or ubuntu.

I've made sure to have my usb drive (called "rem drive", or what I assume means "removeable drive" by my computer) as the first thing to boot, and have even brought up a boot selection menu to manually select the external drive first, but nothing seems to be working. I go to a blank screen for a couple seconds and then straight to the Windows XP loading screen. As I said, no grub loader screen, no nothing. I don't even get error messages.

And since I have the files open right now I figure I may as well post my menu.lst, initramfs.conf, and modules files.

menu.lst:
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd1,0)
map (hd1) (hd0)
chainloader	+1
savedefault
```

initramfs.conf:
```
WAIT=12

#
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#
MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  The command line will override this setting.

RESUME=/dev/sda5
```

Finally, modules:
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod

ehci-hcd
usb-storage
scsi_mod
sd_mod
```

Any bit of help would be greatly appreciated, thanks![/QUOTE]

KoloRahl,

Everything looks OK in your menu.list file. But, I would make a few changes to ward off potential future problems.

Find this line in your menu.lst file ...
# groot=(hd1,0)

Change it to ...
# groot=(hd0,0)

If you don't do this, whenever Ubuntu does a kernel update, it will change all your root lines in menu.lst to (hd1,0) for all the Ubuntu entries. (You did load GRUB to the external drive (sda) bootsector, didn't you?) 

I would also take out the savedefault line in the bootup config area for Windows XP so the grub menu always defaults to your first entry (which should be Ubuntu).

Also, remember to always do a complete shutdown (not a reboot) after editing menu.lst so that you kill anything floating around in memory that may cause hiccups.



I really believe the problem you are having with XP booting up every time  (without your PC seeing a GRUB menu) has to do with the external drive not being setup as the first bootup device. If your internal drive is seen first, the PC will just boot XP. (If you have an older PC, you may need to use the more comprehensive list of modules mentioned in the install note for that STEP.) Also, are you sure you are saving your settings in bios before exiting out? 

Just a thought.


DAVE

---

### Post by KoloRahl on 2006-03-15
Ok, I tried running my external on my friend's laptop and it booted up just fine and was able to log onto Ubuntu (couldn't get internet unfortunately). I then called my computer provider and asked them about the boot options, and they said if I don't have any boot device marked with "USB" then removable device should work, but obviously it's not working. I think I may look into updating my BIOS if I still can't get it to boot properly.

But all-in-all, the instructions worked and ubuntu loaded up nicely onto my external =D Now to get my darn boot options working correctly >_<

Thanks for all the help everyone!

---

### Post by Ruskie on 2006-03-18
What a weird story: I followed the "original" instructions (i.e. only first post, no addendum necessary) of DaBruGo to install kubuntu in my external HD on a IBM T42, and everything worked like a charm. I only had to change sda partition, 'cause it was mapped like this:

sda1: ntfs
sda5: ext3
sda6: swap

(sda5/6 because they're on an extended partition).

Everything PERFECT, I booted up and my ubuntu is original 5.10, not having had opportunity to upgrade it (only wep wireless, still not very good support in Breezy).
Here's what's weird: if I plug my drive, turn drive on, then turn the laptop on and try to boot from USB HDD it DOES find the disk, because GRUB starts (and it's on sda mbr), but when I choose to boot linux it shows the kubuntu splash and then, after the 2nd/3rd "loading" line it goes kernel panic because it does not find /dev/sda5!!! 
No matter how much time I give to the disk to spin up. /dev/sda5 is never found (though it undoubtely loads initrd from there!!!).
I can reboot dozen of times, still same result.
BUT, if I reboot, load windows (hda1), plug the USB HDD (and choose to visualize it in explorer), and then reboot, without turning the external off... then linux load!

What is it due to? Some hdd buffer issue perhaps? My HDD is a Maxtor DiamondMax 200GB... Any idea???

Thank you
Marco

---

### Post by RyanGT on 2006-03-18
My guess is that something weird is happening with the partition numbering.  It doesn't make sense that there is an sda1 and no 2,3, or 4.  I would try booting off a live CD, but following the procedure that would otherwise cause you to fail.  Then go to a terminal and type fdisk -l (or maybe sudo fdisk -l)  and see what partitions it shows on sda.

---

### Post by Ruskie on 2006-03-18
Oh no, it does make sense, instead.
For historycal/technical reasons that I do not exactly know (but I know they exists), an hard disk can only have 4 PRIMARY partitions. Therefore, they are for example hda1, hda2, hda3, hda4. If you want to have more than four partition, you can create an EXTENDED (or LOGICAL) partition, that are like empty boxes into which you can create as many partitions as you like.
Which I usually do when I decide to partition a disk for it to be hybrid between linux and windows.

So, I think to distinguish partitions created into EXTENDED partitions, they always start with 5, 6, 7 etc. etc. This way you know they are not primary ones.

Moreover, if that was the problem I wouldn't understand why it works if I boot windows, enter the ntfs partition in the external disk and then turn off Windows... I think it has rather something to do with the hdd buffer, but I don't know how and why...

---

### Post by david.won on 2006-03-18
[QUOTE=DaBruGo]Hi Folks,
 
Since my first post on this topic, I have learned quite a bunch about the UBUNTU install process ... and managed to successfully load UBUNTU a number of times on my external USB drive. (Call me crazy, but I wanted to run the install a few times to make sure that what I was doing would work every time.)
 
I would like to share my updated outline with others who may also be struggling with this process.
 
**BACKGROUND**: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a Seagate 40GB Portable External Hard Drive that was purchased at Walmart for around $120
 
**REQUIREMENTS**: Make sure you have your bios set to boot the CDROM first and then the USB device, or you will have problems down in step 4. (Kudos to "joess" for pointing out my omission!)
 
*pre-install tip*: If you feel comfortable performing one of the suggestions in [post #141]("http://www.ubuntuforums.org/showpost.php?p=669047&postcount=141") then it should make the installation to the external drive (especially tip 2) run smoother. (Kudos to "Sephatine" for suggesting this.)
 
**IMPORTANT**: Don't forget that Linux is case sensitive on everything, including file and directory names. (There is a difference between an uppercase and a lowercase letter.) *Example*: According to Linux, a file named "DaBruGo" and a file named "dabrugo" are considered two completely different files.
 
 
 
**Here is what I do to successfully load UBUNTU v5.10 on my EXTERNAL USB DRIVE ...**
 
 
**( STEP 1 )** Instead of using "expert" mode to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).
 
*INSTALL NOTE*: The installation process will ask you for some information when it starts up ...
 
first it will ask for your language,
then your (language) location,
then your keyboard type,
then it will detect your cdrom(s),
then it will attempt to detect your network configuration,
then it will ask you to give your PC a name (hostname),
then it detects hardware and starts up the partition phase of the install.
 
*INSTALL NOTE*: When you get to STEP 2 (the partition phase), there is a simple way to determine how the install program assigns device names to your hard drive(s). Before starting any partitioning activity in STEP 2, choose the GO BACK option in the lower left corner of this screen and then choose EXECUTE A SHELL farther down in the Ubuntu installer menu that appears. Choose CONTINUE at the next prompt. In the shell window that appears, type in fdisk -l (that is FDISK -L in all lowercase). This will give you a list of all the storage devices the installer program sees. Make a note of the device names (/dev/hd? or /dev/sd?) and then type in exit to return to the partition phase (STEP 2) of the install. (Kudos to "RyanGT" for suggesting this in post #257.)
 
**( STEP 2 )** During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning ... which sets up an ext2 or ext3 partition and a swap partition for you.)
 
*INSTALL NOTE*: Look for the line during the partitioning phase that might say ... erase entire disk SCSI (0,0,0) (sda). Be careful here as some people have had problems when choosing any partitioning options that include the text "and use LVM" (Kudos to "brucetan" for sharing this in post #268.)
 
Feel like learning about LVM anyway? Check this [link]("http://www.ubuntuforums.org/showthread.php?t=141900") out. (Kudos to "SD-Plissken" for sharing this info.)
 
*BE VERY CAREFUL* on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!
 
Once again ... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!
 
**( STEP 3 )** When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.
 
The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the SDA (external USB) drive where we want to install the GRUB bootloader.
(Mine was /dev/sda [NOT sda1] ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: I loaded GRUB to sda (the bootsector of the external drive) and NOT to sda1 (which would be the first partition on the external drive). 
 
*INSTALL NOTE*: at this point, the install program loads some stuff and ejects the CD ... wanting you to do a reboot.
 
**( STEP 4 )** BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode) ( Review REQUIREMENTS at the beginning of this guide! )
 
Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.
 
**( STEP 5 )** When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your external drive from the list.
(Mine was mount /dev/discs/disc1/part1 ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: /dev/discs mount points start with disc0 (with 0 meaning the first drive in a system). So, my mount point of /dev/discs/disc1/part1 was really the second disk [disc1] (the sda drive we are working with) and the first partition [part1] on that disk. 
 
**( STEP 6 )** When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.
 
**( STEP 7 )** Type in these lines before we start editing out files ...
 
mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>
 
*INSTALL NOTE*: I used vim to edit the files. It is weird to use at first until you learn what a few keys do in it ... The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ... And hitting : x <enter> saves the file and exits out of vim. (IMPORTANT TIP ... that's a colon and a lowercase x with NO SPACE between the colon and the x) 
 
**( STEP 8 )** Run vim to edit the modules file to make sure USB support is added/loaded during UBUNTU startup ...
 
vim /etc/mkinitramfs/modules <enter>
 
Right below the last line of text, enter these lines ...
 
ehci-hcd
usb-storage
scsi_mod
sd_mod
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Some PCs may need a more comprehensive list added here. Please take a look at [post #181]("http://ubuntuforums.org/showpost.php?p=705797&postcount=181") if you are having startup issues after these edits. (Kudos to "brotorious" for his efforts on this.)
 
**( STEP 9 )** Run vim to edit the initramfs.conf file to make sure enough time elapses for USB support to load before UBUNTU gets running ...
 
vim /etc/mkinitramfs/initramfs.conf
 
At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up ...
 
WAIT=12 (in all caps here, not sure if necessary though)
 
Be sure to save the file changes (using : x)
 
*INSTALL NOTE*: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.
 
**( STEP 10 )** Recompile (recreate) the initrd.img file to include USB support from these edited files ...
 
mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
 
*INSTALL NOTE*: When you are done with the previous step #9 (and before performing this step), you can run the "ls /lib/modules" command (without the quote marks) from a terminal window to see what kernel version number you should use for this install step. They may be using a kernel version higher than 2.6.12-9-386 that was available when I originally created this help guide. (Kudos to "Saxegaard" for bringing this to my attention in [post #235.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=754862&postcount=235"))
 
**( STEP 11 )** Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...
 
vim /boot/grub/menu.lst
 
Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).
 
There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 
 
*INSTALL NOTE*: You will also want to change a "# groot" line in a section of your menu.lst file that may look something like this ...
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) <<< CHANGE THIS LINE TO READ # groot=(hd0,0)
(Kudos to "archis" for his excellent documentation of this farther down in [post #227.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=749354&postcount=227"))
 
*INSTALL NOTE*: You may want to change the root line for the Windows XP section in this file to (hd1,0) just in case you have XP loaded on an internal drive and want the option to boot into XP from the GRUB menu. (See post #2 for more info.) You may have to edit this section whenever you update your kernel version. If you have problems pulling up XP after a kernel update, check this section of your menu.lst file to see if you need to edit it again.
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Feel more comfortable editing this file in Windows? See [post #171]("http://ubuntuforums.org/showpost.php?p=692413&postcount=171") for a program that will let you edit files on linux partitions from within Windows. (Kudos to "mickola" for the suggestion.)
 
**( STEP 12 )** Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.
 
BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS
 
**( STEP 13 )** After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU
 
 
That's the process I've successfully used to install UBUNTU v5.10 on an external USB drive. I hope this helps anyone whose been wrestling with this process. Let me know if it works out for you.
 
DAVE
 
 
 
**OTHER PROBLEMS AND POTENTIAL FIXES** ...
 
* Booting Ubuntu from Windows XP without loading GRUB to the MBR ...
[http://www.ubuntuforums.org/showthread.php?t=56723]("http://www.ubuntuforums.org/showthread.php?t=56723")
(Kudos to "celticmonkey" for documenting this.)
 
* Problems booting XP from an internal drive ...
[( message #2 )]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") + [( message #203 )]("http://ubuntuforums.org/showpost.php?p=723454&postcount=203")
 
* Problems starting UBUNTU after a kernel update using Ubuntu's automatic update app ...
[( message #112 )]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112") + [( message #161 )]("http://www.ubuntuforums.org/showpost.php?p=686867&postcount=161")
 
* Using Windows XP to format drives larger than 32GB AS FAT32 ...
[( message #188 )]("http://www.ubuntuforums.org/showpost.php?p=715722&postcount=188")
 
* Re-installing GRUB in a relatively painless manner ...
[( message #205 )]("http://ubuntuforums.org/showpost.php?p=723618&postcount=205") (Kudos to "RyanGT" for hunting this down.)
 
* Creating a bootable GRUB CD (sketchy details but seems to make sense) ...
[( message #207 )]("http://ubuntuforums.org/showpost.php?p=723735&postcount=207") + [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html")
 
**REFERENCE MATERIALS** ...
 
* GRUB Manual (section 14.3 shows what error codes mean)
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")[/QUOTE]
i have installed succeed
but,used in another computer it didn't work anymore
any idea?

---

### Post by Killeroid on 2006-03-19
[QUOTE=Ruskie]What a weird story: I followed the "original" instructions (i.e. only first post, no addendum necessary) of DaBruGo to install kubuntu in my external HD on a IBM T42, and everything worked like a charm. I only had to change sda partition, 'cause it was mapped like this:

sda1: ntfs
sda5: ext3
sda6: swap

(sda5/6 because they're on an extended partition).

Everything PERFECT, I booted up and my ubuntu is original 5.10, not having had opportunity to upgrade it (only wep wireless, still not very good support in Breezy).
Here's what's weird: if I plug my drive, turn drive on, then turn the laptop on and try to boot from USB HDD it DOES find the disk, because GRUB starts (and it's on sda mbr), but when I choose to boot linux it shows the kubuntu splash and then, after the 2nd/3rd "loading" line it goes kernel panic because it does not find /dev/sda5!!! 
No matter how much time I give to the disk to spin up. /dev/sda5 is never found (though it undoubtely loads initrd from there!!!).
I can reboot dozen of times, still same result.
BUT, if I reboot, load windows (hda1), plug the USB HDD (and choose to visualize it in explorer), and then reboot, without turning the external off... then linux load!

What is it due to? Some hdd buffer issue perhaps? My HDD is a Maxtor DiamondMax 200GB... Any idea???

Thank you
Marco[/QUOTE]

Yeah,this also happens to me sometimes.When it starts booting,after the second step,i am told kernel panic,/dev/sda1 not found
sometimes,it happens after i restart my pc after using winxp and the pc tries to boot from the usb,sometimes it happens when i just start up the pc with the usb drive connected.

---

### Post by Ruskie on 2006-03-20
[QUOTE=Killeroid]Yeah,this also happens to me sometimes.When it starts booting,after the second step,i am told kernel panic,/dev/sda1 not found
sometimes,it happens after i restart my pc after using winxp and the pc tries to boot from the usb,sometimes it happens when i just start up the pc with the usb drive connected.[/QUOTE]

Seems slightly different than my case then... Unless... are you absolutely sure that the kernel panics after you reboot from using windows? Because in my experience, it has never happened when rebooting from windows ***provided that  accessed the drive in Win (of course, an NTFS partition on that drive)***.
In your case, being the partition sda1, I suppose you only have ext3 (plus swap) on there, therefore no reason to access it from windows. In that case, that you rebooted from win or powered up from scratch makes no difference. If you feel like playing, I'd suggest you to creare a little ntfs partition on the external usb, then try to display it in windows and then reboot: see if the kernel panics when you do that. If not, we're experiencing exactly the same.

Bye

---

### Post by Ruskie on 2006-03-20
[QUOTE=david.won]i have installed succeed
but,used in another computer it didn't work anymore
any idea?[/QUOTE]

Using the SAME disk on another computer?
That would be just right: different computer = different hardware. You can't expect an OS tailored on a specific pc works with a different one...

---

### Post by Killeroid on 2006-03-20
[QUOTE=Ruskie]Seems slightly different than my case then... Unless... are you absolutely sure that the kernel panics after you reboot from using windows? Because in my experience, it has never happened when rebooting from windows ***provided that  accessed the drive in Win (of course, an NTFS partition on that drive)***.
In your case, being the partition sda1, I suppose you only have ext3 (plus swap) on there, therefore no reason to access it from windows. In that case, that you rebooted from win or powered up from scratch makes no difference. If you feel like playing, I'd suggest you to creare a little ntfs partition on the external usb, then try to display it in windows and then reboot: see if the kernel panics when you do that. If not, we're experiencing exactly the same.

Bye[/QUOTE]
Thanks Ruskie,I will try that.

---

### Post by Killeroid on 2006-03-21
Hi DaBruGo,I just noticed that you updated the tutorial and removed the warnings about this procedure being for only Breezy(I saw the warning the last time,I was here). So I was just wondering if the procedure could be used for Dapper Drake? If not then will you please put the warning back there :) before someone as dumb as I am tries this for the Dapper Flight CD 5.

---

### Post by DaBruGo on 2006-03-21
[QUOTE=Killeroid]Hi DaBruGo,I just noticed that you updated the tutorial and removed the warnings about this procedure being for only Breezy(I saw the warning the last time,I was here). So I was just wondering if the procedure could be used for Dapper Drake? If not then will you please put the warning back there :) before someone as dumb as I am tries this for the Dapper Flight CD 5.[/QUOTE]

Killeroid,

What warning are you talking about ???


DAVE

---

### Post by DaBruGo on 2006-03-21
Hi folks,

Has anyone had any luck using either LABEL or UUID on the kernel line (root=LABEL=mylabel or root=UUID=11223344 etc) in the menu.lst file for GRUB?

I am trying to figure this out so I don't have to worry about what drive letter will be assigned (sda or sdb) when I plug my external drive into my PC, since I am also using usb flash memory sticks on the computer as well.

Supposedly, GRUB will look for the LABEL or UUID of the drive and try to get the rest of the bootup info from there. I have googled and searched to no avail on this. It would be great if someone could help me out.

Anyone run across a good howto or tutorial on this?


DAVE

---

### Post by Killeroid on 2006-03-21
Hi DabruGo,I must have been mistaked about the warning.Sorry for bothering but my question still stands. Can you use this procedure for dapper drake?

---

### Post by DaBruGo on 2006-03-21
[QUOTE=Killeroid]Hi DabruGo,I must have been mistaked about the warning.Sorry for bothering but my question still stands. Can you use this procedure for dapper drake?[/QUOTE]

Killeroid,

It's no bother (questions are a good thing), but my honest answer is "I don't know yet". I haven't had a chance to download Dapper to see what they either have, or have not, changed. 

My next project will be to see if I can get a LIVE DAPPER on a memory stick. I had some luck with this for BREEZY in another thread, but haven't played with it much lately.


DAVE

---

### Post by edoardo on 2006-03-21
[QUOTE=Killeroid]Hi DabruGo,I must have been mistaked about the warning.Sorry for bothering but my question still stands. Can you use this procedure for dapper drake?[/QUOTE]
I did not read this post but just installed dapper flight5 on the 6GB primary partition of my usbpowered drive, and have another instance of dapper installed within a vmware image on another partition of that drive. 
so I can boot from the usb disk and the run vmware player and load my 'portable' dapper,
or I can boot from the interanlHD into windows and again using vmware player running the virtualized dapper.

what I am missing yet is a "live" dapper with vmware that i can boot from.

---

### Post by scratched on 2006-03-21
I just finished installing ubuntu on my external hard drive. I got through all of the steps up to the last one, took my CD out of the drive, restarted, chose ubuntu from GRUB, and tried loading ubuntu. It got to the graphical ubuntu loading screen, and then went back to black and white and displayed this message
```
ALERT! /dev/sda2 does not exist. Dropping to a shell!
```

What does that mean? Anyone have any ideas what I did wrong?

[COLOR="Silver"]When I was installing, on the rescue disk, when it asked what partition it should mount, I tried selecting /dev/discs/disc0/part2 When I did this, a screen came up saying:
```
[COLOR="Silver"]An error occured while mounting the device you entered 
for your root file system () on /target

Please check the error log on the third console 
or /var/log/messages for more information[/COLOR]
```

when I try selecting part1 or 3, it gives me something to the effect of "No usable root found on partition. A shell is being created in the installation environment" I'm guessing that this is somehow connected to my problem. Does anyone know why this is happening or what I might have done wrong?[/COLOR]

I don't know what I did, but something I did caused the list of partitions to mount the USB partitions. I was able to pick the correct partition for my drive and everything seems like it went fine there. I still have that original error message though....

---

### Post by elfois on 2006-03-22
Hi to everybody, i'm new here and i read all around before try to install ubuntu 5.10...
I would like to install breezy badger on USB HD so i got through all of the steps of  DaBruGo's guide, but i've a problem, when i reboot the system (after the manipulation of the grub file) and also when i restart, always boot WXP and not ubuntu... i don't see any grub!!!
Here is```
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root	        (hd1,0)
map (hd1) (hd0)
makeactive
chainloader	+1
boot
savedefault

```
```

WAIT=12
#
# initramfs.conf
#

# BUSYBOX: [ y | n ]
#
# Use busybox if available.  You MUST use the -static version
#

BUSYBOX=y

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# MODULES: [ most | dep | list ]
#
# most - Add all framebuffer, acpi, filesystem, and harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# list - Only include modules from the 'additional modules' list
#
MODULES=most

#
# NFS Section of the config.
#

#
# DEVICE: ...
#
# Specify the network device, like eth0
#

DEVICE=eth0

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

# Hardcode partition to resume from so it doesn't have to be specified
# on the command line.  The command line will override this setting.

RESUME=/dev/sda5

```
```
# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
#
# This might be good choices:
#
# raid1
# sd_mod
ehci-hcd
usb-storage
scsi_mod
sd_mod

```
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
What's wrong in me?
Thanx in advace for your help

---

### Post by Ruskie on 2006-03-22
[QUOTE=scratched]I just finished installing ubuntu on my external hard drive. I got through all of the steps up to the last one, took my CD out of the drive, restarted, chose ubuntu from GRUB, and tried loading ubuntu. It got to the graphical ubuntu loading screen, and then went back to black and white and displayed this message
```
ALERT! /dev/sda2 does not exist. Dropping to a shell!
```

What does that mean? Anyone have any ideas what I did wrong?

**EDIT:** When I was installing, on the rescue disk, when it asked what partition it should mount, I tried selecting /dev/discs/disc0/part2 When I did this, a screen came up saying:
```
An error occured while mounting the device you entered 
for your root file system () on /target

Please check the error log on the third console 
or /var/log/messages for more information
```

when I try selecting part1 or 3, it gives me something to the effect of "No usable root found on partition. A shell is being created in the installation environment" I'm guessing that has something to do with why ubuntu will not boot. Does anyone know why this is happening or what I might have done wrong?[/QUOTE]

Hello,
I guess the two things are only slightly related...
About the second part: trivially, if the /dev/discs/disc0/part2 was the only one you could use, then it HAS to be the right one. ;)
More specifically, you're selecting here the partition in which the operating system has been installed, and that's because the rescue disc uses it to... well, to rescue the system. And you want it to be chosen, because you have to modify some files as explained in the guide.
Now, from your "I tried selecting /part1 and /part3" I can guess that in this disk you have:

sda1: NTFS
sda2: EXT2/3
sda3: SWAP

So, as you can see, part2 (sda2) IS the partition into which you boot the rescue disk, and the one where you correctly installed Ubuntu.

Now, back to the main error message: it says that the partition /dev/sda2 does not exists. But, you know it DOES exist! If you read some message back, that is the exact problem I am experiencing: seems like we've found some kind of a bug, because the kernel can not find our partitions. This can not be because they're incorrectly mounted, perhaps there's a fix for which we have to wait for more experienced people (DaBruGo, where are you?).
Meanwhile if you don't mind, I'll ask you too to make this test: since you have an ntfs partition on the disk, try to boot windows, connect the external disk, enter the ntfs partition (i.e.: f:<enter> dir <enter>), then, *without powering the usb disk off*, to reboot the pc and entering grub with the usual way you use and that now gives error.
Does the error persist even if you access the drive from windows first?
Please let me know, I've noticed on my box that this way it works.
Don't know why... ](*,)

---

### Post by Ruskie on 2006-03-22
[QUOTE=elfois]
What's wrong in me?
Thanx in advace for your help[/QUOTE]

When you reboot your pc, choose in the BIOS options to boot from the external usb disk: if you followed the manual, grub has been installed there and only shows up if you choose that disk as primary boot disk.

---

### Post by Zerlinna on 2006-03-22
I wanted to follow the HowTo posted here, too.
But unfortunately I can't set "boot from external usb disk" in my bios (I only have: boot from HD C, boot from CD and boot from floppy) - does this mean that it's impossible for me to run a second system on my external usb disk? (I wanted to try out dapper with it...)

Z.

---

### Post by scratched on 2006-03-22
[QUOTE=elfois]What's wrong in me?
Thanx in advace for your help[/QUOTE]

I had a similar problem yesterday with this. Did you change the USB drive to boot first in the BIOS? If you did that and it still isn't working, what I did to fix my problem is turn off my computer, then turn off my external hard drive. Then I turned the hard drive back on, before I started up my computer, then I started my computer. This seemed to work for me, I don't know why but it worked for me and I do that every time I want to boot to ubuntu (Even though I'm still having some other problems with booting:-? )

---

### Post by Ruskie on 2006-03-22
[QUOTE=Zerlinna]I wanted to follow the HowTo posted here, too.
But unfortunately I can't set "boot from external usb disk" in my bios (I only have: boot from HD C, boot from CD and boot from floppy) - does this mean that it's impossible for me to run a second system on my external usb disk? (I wanted to try out dapper with it...)

Z.[/QUOTE]
Maybe stupid question mine but... did you have your usb disk plug in? Because in my IBM T42 the option to boot from external HD does not show unless you have an external usb connected.
Also check that in your BIOS the boot option is enabled (usually there is a menu dedicated to boot options).

---

### Post by scratched on 2006-03-22
I figured out my own problem ([post #309]("http://ubuntuforums.org/showpost.php?p=847764&postcount=309")). I had to add a few more lines to /etc/mkinitramfs/modules

brotorious has the list of files to add at [post #181]("http://ubuntuforums.org/showpost.php?p=705797&postcount=181"). DaBruGo actually linked to this in his guide but it didn't click that I needed that at first.

This should fix both my problem and Ruskie who apparently had [the same problem]("http://ubuntuforums.org/showpost.php?p=849547&postcount=311").

---

### Post by Zerlinna on 2006-03-22
[QUOTE=Ruskie]Maybe stupid question mine but... did you have your usb disk plug in? [/QUOTE]

I wasn't sure so I tested it again. Even when my external HD is plugged in and running, Bios won't give me the option "boot from external USB drive" or so. 
There's only one option concerning USB: "USB Emulation" there 'USB Port' is enabled, also the option 'USB Keyboard' and 'USB FDD'. 

[QUOTE=Ruskie]
Also check that in your BIOS the boot option is enabled (usually there is a menu dedicated to boot options).[/QUOTE]
There is such a menu, but as I mentioned I have only the choice between boot from HD C, from CD or from floppy (which is funny because I don't have a floppy).

I use a PackardBell Easynote K5305 Bios Version 1.06 -- [Here]("http://support.packardbell.com/de/mypc/?PibItemNr=instr_bios_kigem&PibItemParent=P920400503#show") is how my Bios looks like.

I tried the HowTo anyway, but when rebooting at the end of the process, it takes the old grub (I have Breezy on my first hd). I tried to add the second system to grub 

> 
title		Ubuntu, kernel 2.6.15-18-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-18-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-18-386
savedefault
boot


hd1,1 because Dapper is on the second partition of my external USB-drive (I use the first for my backups). 

But it didn't work. 
When I try to boot it Grub just says:
"Error 21. Selected disk does not exist"

Any ideas or do I have to forget about it? 

Z.

---

### Post by Ruskie on 2006-03-23
[QUOTE=Zerlinna]
But it didn't work. 
When I try to boot it Grub just says:
"Error 21. Selected disk does not exist"

Any ideas or do I have to forget about it? 

Z.[/QUOTE]
This goes beyond my own knowledges... I would have suggested you the same (installing the boot loader on main hd), and changing some of the settings because of course in that case the order the disk are recognized which would have changed... but you just did what I would have done so... I'm sorry, no idea.

---

### Post by Ruskie on 2006-03-23
[QUOTE=scratched]I figured out my own problem ([post #309]("http://ubuntuforums.org/showpost.php?p=847764&postcount=309")). I had to add a few more lines to /etc/mkinitramfs/modules

brotorious has the list of files to add at [post #181]("http://ubuntuforums.org/showpost.php?p=705797&postcount=181"). DaBruGo actually linked to this in his guide but it didn't click that I needed that at first.

This should fix both my problem and Ruskie who apparently had [the same problem]("http://ubuntuforums.org/showpost.php?p=849547&postcount=311").[/QUOTE]
Hi scratched, thanks for the info.
Meanwhile, I found a "solution" as well. I changed the HD case for a cooled one, and had to set my external hard disk to MASTER. For some reason it wasn't set so but it it was set to "CS enabled" (Maxtor, I don't know the meaning of this setting), so to make it work with the new case I discovered it wasn't master. Since I changed this setting, I have no problems booting from there.
Maybe something worth adding to the guide, if confirmed...

---

### Post by Zerlinna on 2006-03-23
[QUOTE=Ruskie]This goes beyond my own knowledges... but you just did what I would have done so... I'm sorry, no idea.[/QUOTE]

Never mind, and thank you for taking the time to try to help me!
So I'll just keep the hd for backups or maybe a /home partition (if that works ;) ) and install the 2nd system on my internal hd... 

Z.

---

### Post by Zerlinna on 2006-03-23
Yooohoooo! :-D 

Kubuntu Dapper is now running on my external HD though my bios does not support boot from external usb drive.
I asked in the #kubuntu-de IRC channel and was helped by comm[A|n]der and TheDemonInsed (thank you guys!). 

Creating a bootable CD did the trick. To do so follow this HowTo.[http://ubuntuforums.org/archive/index.php/t-19428.html]("http://ubuntuforums.org/archive/index.php/t-19428.html")

Ok, it's not a real dual boot, because whenever you want to run the system on the USB-Drive you need to start from CD. But at least it's possible to run it :mrgreen: 

Z.

---

### Post by elfois on 2006-03-24
[QUOTE=Zerlinna]Yooohoooo! :-D 

Kubuntu Dapper is now running on my external HD though my bios does not support boot from external usb drive.
I asked in the #kubuntu-de IRC channel and was helped by comm[A|n]der and TheDemonInsed (thank you guys!). 

Creating a bootable CD did the trick. To do so follow this HowTo.[http://ubuntuforums.org/archive/index.php/t-19428.html]("http://ubuntuforums.org/archive/index.php/t-19428.html")

Ok, it's not a real dual boot, because whenever you want to run the system on the USB-Drive you need to start from CD. But at least it's possible to run it :mrgreen: 

Z.[/QUOTE]

Nice to know that you win your battle with grub&BIOS... I think i have the same problem, in BIOS setup exists the option "boot from ext device" but it doesn't do nothing...
Now, i read the link you suggest, but i need obviuosly help ;)
I can see the HD usb only if I boot with a Live CD, in fact i'm only at half installation, so, (i'm so new in linux, sigh sigh) what must i do to create this Boot cd?
thanks a lot for your help

---

### Post by StefanoCole on 2006-03-24
Hello elfois, I read the Howto Make an Ubuntu Boot-CD, I think that in step 6 for <your-root-dev> you have to specify something like: /dev/sda1

For the rest, what's the matter with the creation of the boot CD?

Stefano

---

### Post by elfois on 2006-03-24
[QUOTE=StefanoCole]Hello elfois, I read the Howto Make an Ubuntu Boot-CD, I think that in step 6 for <your-root-dev> you have to specify something like: /dev/sda1

For the rest, what's the matter with the creation of the boot CD?

Stefano[/QUOTE]

Hello Stefano, that's also my name ;) , my doubt is what is the complete procedure...

I try to explain my situation better:
I install Ubuntu Breezy on USB device, first partion primary ext3 (/dev/sda1), swap partion logical (/dev/sda5), and the partion fat32 primary (/dev/sda3), i put the grub on MBR of sda (when i reboot in rescue mode i choose /dev/discs/disc1/part1), i do all the modification in /etc/mkinitramfs/modules, in /etc/mkinitramfs/initramfs.conf and in /boot/grub/menu.lst like DaBruGo says, then i get out the CD before restart... 
But my BIOS, even if tells me that i can boot from external device, boot win xp from /dev/hda...
So, the only thing i can do is boot from a live CD (ubuntu or knoppix). 
Now, and then?
If i boot from a live CD my CD-RW is busy... how can i do? 
Can i install syslinux on a live session? 
If yes, how can i do if the syslinux_2.11.orig.tar.gz is on the desktop? 
And then, if i success doing step 1 to 7, how can i burn the CD? Can i put what i should burn on a pen drive and then burn it in Win XP?

Sorry for all this question, i'm really new and i'd like understand and learn what i'm doing! 

Thanks to you and to other people who try to help me

OT: Obviously everything should be simplier (for me) if we can write in our language, but probably someone like me but from other country could find this topic useful!!!

---

### Post by Zerlinna on 2006-03-24
[QUOTE=elfois]
I can see the HD usb only if I boot with a Live CD, in fact i'm only at half installation, so, (i'm so new in linux, sigh sigh) what must i do to create this Boot cd?
thanks a lot for your help[/QUOTE]

Hey elfois,

Firstly you need two things: a first system installed on your internal HD which is able to access your usb drive, and the second system installed on your usb Drive. 
Maybe it would also work with a LiveCd, but you need to burn a cd (while the livecd is running...), that's kinda difficult ;-)

The boot CD works like a boot floppy (I just made a boot CD because I don't have floppy) - this means that the CD loads the kernel first, then the computer is able to recognize the usb drive and can load the system therefrom.

Why is the first system (on internal hd) important?  Because you need to access your second system (on the usb partition) and copy its kernel (step 4) and its initrd.img (step 5) into a folder named bootcd (which you have to create, see step 2). 

Stefano is right about step 6. 
You need to create isolinux.cfg yourself (just open kate or gedit and save the file as isolinux.cfg). All you need to type into the file is:
DEFAULT linux initrd=initrd.img ro root=<your-root-dev> while your-root-dev is the partition where you second system is installed. In my case that was: 
DEFAULT linux initrd=initrd.img ro root=/dev/sda2
(sda ist my usb drive and the system is on the second partition).

I hope it's a bit clearer now :-)
If you still have questions, please try to be a bit more precise then it's easier to give you a answer which might help you.

Z.

---

### Post by elfois on 2006-03-24
[QUOTE=Zerlinna]If you still have questions, please try to be a bit more precise then it's easier to give you a answer which might help you.[/QUOTE]

Tanx Zerlinna for your explanation, but if you read the previous post i think there are more questions unanswered... Be patienced with me

---

### Post by Zerlinna on 2006-03-24
You're too fast, guy...(while I was writing you already posted something new) :-)

As I can see from here you have two possibilities: 
You can try to install grub to the MBR of your internal HD and make sure that you have something like that in your grub: 

> title Ubuntu, kernel 2.6.xx-xx-xxx
root (hd1,0)
kernel /boot/vmlinuz-2.6.xx-xx-xxx root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.xx-xx-xxx
savedefault
boot

Of course 2.6.xx-xx-xxx has to be replaced with your kernel of breezy.

Try out if it works. Maybe your Windows won't boot, but this is nothing to be scared of, you just have to add it to grub, too. 

Second solution (with the bootCd)
I know that with knoppix it's possible to remove and install programms (you can save your personalized image on usb stick so that even when you restart the livecd your settings stay the same). So that is not a problem. Maybe you can even install syslinux with a program like synpactic, apt-get or... (not sure what knoppix uses). 
Create the folder and everything and put the iso on your usb stick (the iso you will create is not very big, about 7MB). 
Reboot in Windows an burn the iso. 

[QUOTE=elfois]
Sorry for all this question, i'm really new and i'd like understand and learn what i'm doing! [/QUOTE]

You don't have to be sorry... the forum is made for people having questions :-)

---

### Post by StefanoCole on 2006-03-24
Yes, as Zerlinna says, with the live CD and Synaptic you could install syslinux package (this will be put in RAM, as the live OS you are running). Then create the bootcd dir and the other required files in the USB stick and build the iso file in the USB stick. Then, from Windows burn to CD the iso file.
You can use an USB stick or the FAT32 partition on your USB external disc to build the iso.
If you have problems to install syslinux with Synaptic you can download it from the repository (even from Windows) the link is: [http://packages.ubuntu.com/breezy/utils/syslinux]("http://packages.ubuntu.com/breezy/utils/syslinux")

then, put it on the USB stick and install it from terminal with the command:
sudo dpkg -i syslinux_2.11-0.1ubuntu4_i386.deb

Stefano

---

### Post by Zerlinna on 2006-03-24
[QUOTE=StefanoCole]Yes, as Zerlinna says, with the live CD and Synaptic you could install syslinux package [/QUOTE]
With Knoppix there is even no need to install syslinux, because it's already there.

Z.

---

### Post by h0meb0y25 on 2006-03-25
hi Dave,

First of all a big thanx for expalining the installation steps in details.

I followed ur step by step guide and was able to install Ubuntu on my USB Extenal HDD succesfully.

But after installation when i rebooted my system after STEP 12) in ur procedure system went to Windows XP logo and windows started successfully and didnt boot from External HDD.

I have sony VAIO desktop
with 2 internal hard drives (80gig, 200gig) and I installed linux on usb external hdd (160 gig).

I have made all the changes as suggested by u in  --

/etc/mkinitramfs/modules
/etc/mkinitramfs/initramfs.conf
copiled using --  mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
vim /boot/grub/menu.lst

I have made my menu.lst exactly look likes urs posted in post [#44]("http://www.ubuntuforums.org/showthread.php?t=80811&page=5")

BOOT setup on BIOS is --
1. Other Boot Device = SCSI BOOT Drive
2. ATAPI CD-ROM = CD-Rom
3. Removal Device = USB FDD
4. IDE Hard Drive = 80 gig drive


Please advice what I can do to resolve this issue.

Appreciate all ur help.

---

### Post by yager on 2006-03-25
[quote=h0meb0y25]
But after installation when i rebooted my system after STEP 12) in ur procedure system went to Windows XP logo and windows started successfully and didnt boot from External HDD.
[/quote] 
For what it is worth, I had a similar situation.  I solved it by setting the boot order of the hard drives in the Hard Drive submenu of my BIOS.  While I had the Hard drives as the 3rd boot priority, the internal drive was the first in the list that it checked for a Master Boot Record and that was the one that took the computer to my Windows XP startup.  When I put the external hard drive as the first hard drive in that submenu, when the BIOS gets to the hard drives looking for the boot, it finds the external drive with GRUB and boots from it instead.

In your post, you show that the BIOS is pointing to an 80GB drive.  The only 80 listed is your internal drive.  You definitely need to change the Hard Drive submenu so that it is pointing the 160GB external drive.

---

### Post by h0meb0y25 on 2006-03-26
In your post, you show that the BIOS is pointing to an 80GB drive.  The only 80 listed is your internal drive.  You definitely need to change the Hard Drive submenu so that it is pointing the 160GB external drive.[/QUOTE]

Thnx for reply .. 
But i have 2 internal HDD. 80gig and 200 gig, 80 gig is primary that why i mentioned "4. IDE Hard Drive = 80 gig drive" which has windows Xp installed on it. 

160gig is external HDD on which Ubuntu is installed and which i m not able to boot from.

thanx for ur inputs.

---

### Post by h0meb0y25 on 2006-03-26
Ok Guys, 

here is quick update .. 

I have installed ubuntu on my external USB hdd but from another system which supports booting from USB HDD.

Seems like the bios of the system on which I was connecting external usb hdd donest support booting from extrenal hdd. 

Is there a way to boot from external USB or external firewire device, even if system BIOS doesnt support that.

I have read this link "http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html" but being a newbie could not understand the details mentioned there. 

If some has done this earlier please help.

thnx

---

### Post by Zerlinna on 2006-03-27
[QUOTE=h0meb0y25]Ok Guys, 
Is there a way to boot from external USB or external firewire device, even if system BIOS doesnt support that.

I have read this link "http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html" but being a newbie could not understand the details mentioned there. 

If some has done this earlier please help.

thnx[/QUOTE]

Hey Hb, 

as I mentioned above you can make a startupCD to boot from your external HD. I put all the information together to a little HowTo located here: [http://zerlinna.blogspot.com/2006/03/dual-boot-on-external-usb-drive-with.html](http://zerlinna.blogspot.com/2006/03/dual-boot-on-external-usb-drive-with.html)

Z.

---

### Post by DaBruGo on 2006-03-27
[quote=h0meb0y25]Ok Guys, 
 
Seems like the bios of the system on which I was connecting external usb hdd donest support booting from extrenal hdd. 
 
Is there a way to boot from external USB or external firewire device, even if system BIOS doesnt support that.
 
If some has done this earlier please help.
 
thnx[/quote]
 
h0meb0y25,
 
You might want to double check your other settings in your BIOS because sometimes there is a separate option in another menu that allows you to turn on (enable/disable) the booting of USB devices.
 
The BIOS on my motherboard is setup that way so that I not only have to place the USB device at the top of the boot list but I have to also make sure USB booting is enabled as well. (DELL Optiplex PCs have a similar setting in their BIOS as well.)
 
Check and see if you have that option in your BIOS.
 
 
DAVE

---

### Post by yager on 2006-03-27
Master DaBruGo speaks the truth.  

I reviewed your referenced web page: [http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)
and found the following.
> As the above takes place before the OS has been loaded, it means that all of the disk reading must take place by way of BIOS calls. This has a very serious implication: namely, that [COLOR="Blue"]in order to boot the disk directly, your BIOS must support disks connected via FireWire or USB. This can typically be seen as a BIOS option to boot from these types of disk.[/COLOR] FireWire BIOS support is currently very rare indeed, but USB support is becoming reasonably common. Therefore, if you are using USB on a relatively recent machine, it should be possible to boot the drive into Linux directly.

After installing GRUB in the MBR of the external drive, I was able to boot it directly when connected via USB. [COLOR="Blue"]Simply enter the BIOS setup utility while booting with the disk connected. The external disk will appear as a regular hard drive: move it so it is before the internal drive in the boot order.[/COLOR] 

In my case, I am using a 4 year old Gateway 500XL and it has the option in the BIOS to boot from a USB device.  When I bought this system, it was top of the line but I would not say it was on the cutting edge of technology back then.  I would suspect that any decent system that is newer than this would have that option available.  You may also want to check for a BIOS update as your manufacturer may have added some additional features to your BIOS.  I upgraded my BIOS and it corrected a 8GB max partition size problem during boot up.

---

### Post by h0meb0y25 on 2006-03-28
[QUOTE=DaBruGo]h0meb0y25,
 
You might want to double check your other settings in your BIOS because sometimes there is a separate option in another menu that allows you to turn on (enable/disable) the booting of USB devices.
 
The BIOS on my motherboard is setup that way so that I not only have to place the USB device at the top of the boot list but I have to also make sure USB booting is enabled as well. (DELL Optiplex PCs have a similar setting in their BIOS as well.)
 
Check and see if you have that option in your BIOS.
 
 
DAVE[/QUOTE]


Dave,

I have checked the BIOS again and couldnt find any option which will allow to boot from USB hdd. The only option i see is "USB FDD" i think which means Floppy disk drive. anyways I have tried selecting this option and no success. :( .

---

### Post by h0meb0y25 on 2006-03-28
[QUOTE=yager]Master DaBruGo speaks the truth.  

I reviewed your referenced web page: [http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html](http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html)
and found the following.


In my case, I am using a 4 year old Gateway 500XL and it has the option in the BIOS to boot from a USB device.  When I bought this system, it was top of the line but I would not say it was on the cutting edge of technology back then.  I would suspect that any decent system that is newer than this would have that option available.  You may also want to check for a BIOS update as your manufacturer may have added some additional features to your BIOS.  I upgraded my BIOS and it corrected a 8GB max partition size problem during boot up.[/QUOTE]


Thxn Yager,

Will check if updates for my SONY system BIOS is available. I bought it in 2003. This thing has boot option from USB FDD .. but not USB HDD .. surprising :).

---

### Post by elfois on 2006-03-31
Hi to everyone, even if I do what Zerlinna says I continue to have problems...
I success to create the boot Cd but after a bit appears the following ALERT

"Not find /dev/sda1"     the mbr of external HD...

What is the error?
What can I do to launch Grub?
Is it possible to install Grub on a CD?

Thanks to everyone

---

### Post by Zerlinna on 2006-03-31
[QUOTE=elfois]
"Not find /dev/sda1"     the mbr of external HD...
What is the error?
[/QUOTE]

Hey Elfois,

if you have the boot cd you don't need to start Grub, because the CD will boot the kernel and then directly the system. So if you want to start another system than the one your USB-Device, remove the CD before booting - if you want to boot the system on your USB-Device, make sure that in your BIOS "boot from CD" is enbabled as first option, and just put in the CD before booting. If you've done all that, the only explanation I have is that the root system on the external drive is not on /dev/sda1 but somewhere else.

Z.

---

### Post by elfois on 2006-03-31
Ok, i try to explain:
Win Xp is on hda (internal HD)
Ubuntu is on sda (usb HD)

my **/etc/fstab** is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

So? where is the error? i can't understand...
I'll wait for your help
bye

---

### Post by DaBruGo on 2006-03-31
[QUOTE=elfois]Hi to everyone, even if I do what Zerlinna says I continue to have problems...
I success to create the boot Cd but after a bit appears the following ALERT

"Not find /dev/sda1"     the mbr of external HD...

What is the error?
What can I do to launch Grub?
Is it possible to install Grub on a CD?

Thanks to everyone[/QUOTE]

elfois,


In STEP 3, did you install GRUb to /dev/sda1 or /dev/sda?

It should have been installed to /dev/sda (the bootsector of the drive) and NOT to /dev/sda1 (the first partition of the drive).

Do you remember where you installed it in STEP 3?


DAVE

---

### Post by Zerlinna on 2006-03-31
[QUOTE=DaBruGo]elfois,
In STEP 3, did you install GRUb to /dev/sda1 or /dev/sda?
It should have been installed to /dev/sda (the bootsector of the drive) and NOT to /dev/sda1 (the first partition of the drive).
DAVE[/QUOTE]

I think it doesn't matter where he installed Grub if he uses the bootCD. 

Elfois: you're right, with your fstab, /dev/sda1 should be the right one.. This is really weird.
Can you paste what's happening before the error? Is your computer really booting from CD? 

Z.

---

### Post by h0meb0y25 on 2006-03-31
[QUOTE=Zerlinna]Hey Hb, 

as I mentioned above you can make a startupCD to boot from your external HD. I put all the information together to a little HowTo located here: [http://zerlinna.blogspot.com/2006/03/dual-boot-on-external-usb-drive-with.html](http://zerlinna.blogspot.com/2006/03/dual-boot-on-external-usb-drive-with.html)

Z.[/QUOTE]

Hi Zerlinna,

I tried to create bootcd as mentioned in the giveurl but i m getting following error when try to run mkisofs command. Can u help me out.

Many thnx

root@ubuntu:/bootcd# mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - bootcd/

I have following in the /bootcd dir.

root@ubuntu:/bootcd# ls -altr
drwxr-xr-x  23 root root    4096 2006-03-31 14:11 ..
-rw-r--r--   1 root root      50 2006-03-31 14:18 isolinux.cfg
-rw-r--r--   1 root root   12720 2006-03-31 14:28 isolinux.bin
-rw-r--r--   1 root root 1207036 2006-03-31 14:38 linux
-rw-r--r--   1 root root 5288213 2006-03-31 14:39 initrd.img

---

### Post by robio376 on 2006-03-31
Hello feller Ubunters...yeah! I have an HP pc with a 250gb internal SATA HD and also have a External USB 250gb HD. The problem is that I have followed the guide word for word then followed it some other ways because I can't get it to work. The problem I see is that my external enclosure is also a SATA drive. It's a kingwin USB2.0 external enclosure for 3.5 SATA hard disk. No matter where I try to put Grub, it will write it to every partition. My bios does support booting from a usb device. Luckily I have been able to restore my MBR with HP recovery dvd and haven't demolished my Windows installation. List of partions are shown below...

/dev/sda1  (internal Hp recovery partition)
/dev/sda2  (internal Windows installation)
/dev/sdb1  (external usb drive)

---

### Post by Zerlinna on 2006-04-01
[QUOTE=h0meb0y25]
I tried to create bootcd as mentioned in the giveurl but i m getting following error when try to run mkisofs command. Can u help me out.[/QUOTE]

I think in this case I can :mrgreen: 

[QUOTE=h0meb0y25]
root@ubuntu:/bootcd# mkisofs -o bootcd.iso -b isolinux.bin -c boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -J -hide-rr-moved -R bootcd/
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
mkisofs: No such file or directory. Invalid node - bootcd/[/QUOTE]

Watch step VI in the howto:* "Cd into the directory above bootcd"* - you need to be one directory *above* the folder bootcd (you ran the command when you were IN bootcd: root@ubuntu:/bootcd#)

Z.

---

### Post by rolazp on 2006-04-01
Hi,

I just followed the guide and was able to install UBUNTU on a Barracuda external USB drive connected to my compaq Presario turion 64 laptop.

I mean, I got it installed. GRUB shows up and I am able to choose it.

The problems starts as soon as the UBUNTU screen loads and starts mounting the root file. The screen disappears and I get:

"Uncompressing Linux...OK. Booting the Kernel
loading, please wait..."

After that it pauses for approx. 20 seconds and I get buffer I/O errors on device /dev/sda1

Then It cannot open /dev/sda/, it says that such device does not exist and I am taken out to the prompt.

I can see the file in /dev/sda.

Any clues?

Thanks

rolazp

---

### Post by h0meb0y25 on 2006-04-01
[QUOTE=Zerlinna]I think in this case I can :mrgreen: 



Watch step VI in the howto:* "Cd into the directory above bootcd"* - you need to be one directory *above* the folder bootcd (you ran the command when you were IN bootcd: root@ubuntu:/bootcd#)

Z.[/QUOTE]

Thnx Thnx Thnx so much ... I was able to Boot from from my external USB HDD successfully.

But here is the another problem now .. 

I m getting X Server error. "The X server is now disabled. Restart FDM when it is configured correctly."

seems like /home need to be set as u mentioned in ur how-to. 

Do u know any alternate to this .. or do i have to install UBUNTU again considering the above ?

thnx again for all ur help.
much appreciated. :)

---

### Post by unar on 2006-04-01
Hi to all!
I'm a new Ubuntu user and I'm trying to install it on my usb external hd!
I followed up the wonderful guide given in this forum but, when I've done all, while loading Linux I get the following error message:

[...]
Decrompressing Linux...done
Booting the kernel.
Loading, please wait...
FATAL: Module unknown not found.
mount: Mounting /dev/sdb1 on /root failed: No such device
mount: Mounting /root/dec on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busybox ...

/bin/sh: can't access tty; job control turned off

](*,) 

Anyone could help me?!
Thank you very much!

regards, Andrea

---

### Post by Zerlinna on 2006-04-02
[QUOTE=h0meb0y25]Thnx Thnx Thnx so much ... I was able to Boot from from my external USB HDD successfully.[/QUOTE]
I'm really glad I could help you so far :-D 

[QUOTE=h0meb0y25]
I m getting X Server error. "The X server is now disabled. Restart FDM when it is configured correctly."[/QUOTE]

I think you mean GDM not FDM, right?
Hmmm, I don't think this has really to do something with your home...the X-server is not in your /home directory (e.g. the folder .kde is just created when you login the first time, but Xorg is in /etc/X11/ - not in home). 
I googled around a bit and I found two things. Just try to run: 
> sudo dpkg-reconfig xserver-xorg  - "that should run you through setting up X again (make sure you have your monitor and video card detaisl to hand - you'll need to know (specially type and manufactrer of your card, and vertical and horizontal sync rates of your monitor)" I took this advice from [here.]("http://www.ubuntuforums.org/archive/index.php/t-36498.html")
 
Other possibility: download the CD again and burn it very carefully (maybe it was damaged), install again. But I'd really try the other one first (less of work!).

Z.

---

### Post by h0meb0y25 on 2006-04-02
[QUOTE=Zerlinna]I'm really glad I could help you so far :-D 



I think you mean GDM not FDM, right?
Hmmm, I don't think this has really to do something with your home...the X-server is not in your /home directory (e.g. the folder .kde is just created when you login the first time, but Xorg is in /etc/X11/ - not in home). 
I googled around a bit and I found two things. Just try to run: 
  - "that should run you through setting up X again (make sure you have your monitor and video card detaisl to hand - you'll need to know (specially type and manufactrer of your card, and vertical and horizontal sync rates of your monitor)" I took this advice from [here.]("http://www.ubuntuforums.org/archive/index.php/t-36498.html")
 
Other possibility: download the CD again and burn it very carefully (maybe it was damaged), install again. But I'd really try the other one first (less of work!).

Z.[/QUOTE]

Dude, u know what .. You are Geniusssssssssssss ... :) (trust me .. not kidddin .. :))

just ran that command, it walked me thru some steps....  and here i m replying to ur post from Mozilla firefox in UBUNTU..

Thnx a lot man and keep up ur good work.

cheers,

---

### Post by Zerlinna on 2006-04-02
> **h0meb0y25]Dude, u know what .. You are Geniusssssssssssss ... :) (trust me .. not kidddin .. :))[/QUOTE]

Is there no /me blushing-smiley???  said:**
> 
 and here i m replying to ur post from Mozilla firefox in UBUNTU..

is working now :D 

[QUOTE=h0meb0y25]
Thnx a lot man and keep up ur good work.
[/QUOTE]

I'm glad you're on ubuntu :mrgreen: 

Z.

---

### Post by A. J. Rimmer on 2006-04-02
Dave and everyone else: Thank you for this excellent post! :) 

A week ago I couldn't even spell Linux, and now I are one. :mrgreen: 

Really!  Last Sunday I ordered a bunch of distros on CD (including Ubuntu live and install) and on Wednesday I bought the Linux for Dummies book.  Thursday the CDs arrived and within two hours I had "Damn Small Linux" running on a USB thumb drive.  Yesterday I resized the partitions on my 80GB external USB drive (65GB for ntfs and 15GB for ext2) using Windows XP Disk Manager and Gparted from the live CD and this afternoon (Sunday) I installed Ubuntu and got it working on the second try.

I followed your directions to the letter and they were perfect.  Well, it wouldn't boot on the first try, but I immediately reallized the problem, as I had used "hd0,0" in step 11 when I should have used "hd0,1" since I had put Ubuntu on the second partition.  

Again, thanks to all who contributed to writing these excellent guidelines.  I'm looking forward to many hours of experimentation and learning! :rolleyes:

---

### Post by confused2 on 2006-04-02
Been fighting with different versions of Linux for 2 weeks just trying to get one to run. Finaly tried Ubuntu on a USB, installed smooth. But. I get to Step 7 and thats it. I type in mount -tproc proc /targetproc/proc and the comand prompt doesn't change. I type in chroot /target and the command prompt changes to sbin. Input su and it says invalid command. Cannot open VIM in any form on any command line. Tried multiple variations of commands and lines. Nothing. About to give up on Linux. I've tried 3 different Linux OS's on the same HDD as my Windows and none boot. Tried seperate boot partitions and every trick in the book, nothing. My laptop doesn't support booting a USB drive so I am trying to boot it with a floppy. I have BootIt and tried to boot it with it but it will not add the boot partition to the boot list. Says the partition is bootable but it won't let me add it. But if I can't tell Grub where the drive is I can't boot on a floppy with Grub on it. I'm new to Linux completely and alot of the command stuff is extremely confusing especially when I don't know what it is supposed to do. I'm guessing that when I input the first command of step 7 the command line should have changed? It doesn't. Ran the Live DVD so I could run the commands and see what was supposed to happen and they work Live. But nothing that works Live works otherwise.

---

### Post by elfois on 2006-04-03
[QUOTE=DaBruGo]elfois,


In STEP 3, did you install GRUb to /dev/sda1 or /dev/sda?

It should have been installed to /dev/sda (the bootsector of the drive) and NOT to /dev/sda1 (the first partition of the drive).

Do you remember where you installed it in STEP 3?


DAVE[/QUOTE]

@ DAVE: I'm sure that I installed  Grub to /dev/sda and when I try  STEP 5 I must choose /dev/discs/disc1/part1 

[QUOTE=Zerlinna]I think it doesn't matter where he installed Grub if he uses the bootCD. 

Elfois: you're right, with your fstab, /dev/sda1 should be the right one.. This is really weird.
Can you paste what's happening before the error? Is your computer really booting from CD? 

Z.[/QUOTE]

@ Zerlinna: I try with bootCD both with configuration from STEP 8 to STEP 12 and with  "default" configuration (GRUB on mbr of usb HD and  no manipulation of /etc/mkinitramfs/modules, /etc/mkinitramfs/initramfs.conf and /boot/grub/menu.lst) but in both case the error is that it can find /dev/sda1...

I try also thi method [http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/]("http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/") but i have another BIG problem: I can format the share partition either in FAT32 nor in FAT16, so Ifailed the STEP 8


OK, I hope that my problems are more clear and that someone could understand where is/are the error/errors... I want to use linux, expecially ubuntu, but I'm so demoralized

---

### Post by confused2 on 2006-04-03
Tried to install Grub to /dev/sdb2. Which is the USB drive. Also tried it /dev/sdb1 which is my floppy. Neither worked. Am going to try a install one more time and see if anything changes. How do I get Grub installed without running a complete install? Can I put Grub on a floppy and try to get it to find the USB or does the fstab have to be connected to Grub from the start? I don't understand how this works still.

---

### Post by elfois on 2006-04-05
nobody has ideas?

---

### Post by DaBruGo on 2006-04-07
[QUOTE=elfois]nobody has ideas?[/QUOTE]

elfois,

This is just a guess ... but there may be something not correct in your GRUB menu.lst file (/boot/grub/menu.lst). Are you able to post it's contents? I am thinking that may be the problem from one of your [previous posts]("http://www.ubuntuforums.org/showpost.php?p=878362&postcount=339").

Also, most people don't know that you can run the GRUB install more than once when you are originally installing Ubuntu. If you load it the first time to the external drive MBR, you can then hit ESC (backing out to the installer menu options) and scroll down to the GRUB loading option again ... and then load it to the floppy as well.


DAVE

---

### Post by Zerlinna on 2006-04-07
Hi elfois,

sorry for my late answer to your post.

[QUOTE=elfois]
@ Zerlinna: I try with bootCD both with configuration from STEP 8 to STEP 12 and with  "default" configuration (GRUB on mbr of usb HD and  no manipulation of /etc/mkinitramfs/modules, /etc/mkinitramfs/initramfs.conf and /boot/grub/menu.lst) but in both case the error is that it can find /dev/sda1...[/QUOTE]

Maybe I didn't make it clear enough: if you made the bootCD it doesn't matter where you installed grub and what you wrote on menu.lst because your computer will boot from CD and not from grub. 
In an older post you said that the error while booting from CD would be "can't find /dev/sda1" and my answer to that was: [QUOTE=Zerlinna]Can you paste what's happening before the error? Is your computer really booting from CD?[/QUOTE]

If you answer those questions I could probably help you :-)

So talking about booting from CD there are 2 possible main problems:

1. your computer is NOT booting from the CD you created at all. What could be the reason? 
It could be because you didn't set bios to boot from cd first OR because you didn't make the CD bootable when you burned it.

2. your computer IS booting from cd, BUT it fails. Reason?
You told the CD to boot from the wrong device (but if you set the boot cd to boot from /dev/sda1 and your new root system IS on /dev/sda1 it should work) OR something went wrong when you created the bootCD.

Maybe there are more possibilities but I can only think of those as probable.

So my question is: Are you sure that your computer is booting from CD? If grub shows up, it doesn't! 

If it does boot from CD but gives you an error check again the settings you made for you boot CD. If you aren't able to find an error, you can send me your bootcd folder (and your iso if you want to) -- if that's ok with your internet connection (both are about 7,5 MB I think) - so I could check if the CD you created works. To get my email just send me a PM - I could check your CD on monday.

[QUOTE=elfois]
OK, I hope that my problems are more clear and that someone could understand where is/are the error/errors... I want to use linux, expecially ubuntu, but I'm so demoralized[/QUOTE]

Keep it up, I'm sure you'll get it working!

Z.

---

### Post by A. J. Rimmer on 2006-04-10
Dave (or anyone who can address this issue) --

On rereading your original post, I noticed that you said you were using a WD portable drive.  Is this a USB-powered device?  My reason for asking is this:

I now have Ubuntu running on my laptop using an 80GB USB2.0 drive with external power supply.  I start the external drive first, then start the computer.  I would like to switch to a more portable setup with a USB-powered drive, but am concerned that, since the drive would not get power until the laptop is turned on, the USB drive might not spin up soon enough to support booting.

Just wondering if this will really be a problem, or if my concerns are unfounded.  I guess I could always boot into Windows, plug in the drive, spin it up, then reboot, but that would be a hassle as well as burning up valuable minutes of battery time, which is a limited resource on my 2.8GHz P4 laptop!

Thanks for any thoughts anyone might have on this.

(This is turning out to be a fun project.  I now have my modem working, and hope to go to the library today with my setup to try out WiFi and get into the Universe repository -- thus the motivation for something more portable for the long term.)

---

### Post by DaBruGo on 2006-04-10
[QUOTE=A. J. Rimmer]Dave (or anyone who can address this issue) --

On rereading your original post, I noticed that you said you were using a WD portable drive.  Is this a USB-powered device?  My reason for asking is this:

I now have Ubuntu running on my laptop using an 80GB USB2.0 drive with external power supply.  I start the external drive first, then start the computer.  I would like to switch to a more portable setup with a USB-powered drive, but am concerned that, since the drive would not get power until the laptop is turned on, the USB drive might not spin up soon enough to support booting.

Just wondering if this will really be a problem, or if my concerns are unfounded.  I guess I could always boot into Windows, plug in the drive, spin it up, then reboot, but that would be a hassle as well as burning up valuable minutes of battery time, which is a limited resource on my 2.8GHz P4 laptop!

Thanks for any thoughts anyone might have on this.

(This is turning out to be a fun project.  I now have my modem working, and hope to go to the library today with my setup to try out WiFi and get into the Universe repository -- thus the motivation for something more portable for the long term.)[/QUOTE]

A. J.


It is a USB-powered external Seagate drive (just one cable connecting the drive to the USB port on the PC). No power adaptor comes with it.

It is powered from the USB port. The drive light comes on as soon as I turn on my PC. So, you shouldn't have to worry about spin-up time.

Here is a [link]("http://www.walmart.com/catalog/product.do?product_id=3910242") for more information.

(My INTERNAL drive is a WD drive.)

Hope that helps,
DAVE

---

### Post by A. J. Rimmer on 2006-04-10
Dave --

Super!  And thanks so much for the fast response! :p 

Right now I am sitting at the library in their "study room" with everything plugged in to the wall, downloading stuff from the Universe repository via WiFi.  Good ol' Ubuntu detected and connected without my so much as having to lift a finger (other than to log in to Gnome).  Tomorrow it's off to the stores to pick up a portable USB drive; just hope I can duplicate my install success a second time.

Wow, is this fun!  :D

---

### Post by Rafinator on 2006-04-12
I've been trying to find a guide like this.  I'm just not sure I can understand it :P i'm new to linux.  I've been wanting to try it, but I did not want the commitment of installing it to my hd.  I'll keep on trying to figure this out.

---

### Post by DaBruGo on 2006-04-13
[QUOTE=Rafinator]I've been trying to find a guide like this.  I'm just not sure I can understand it :P i'm new to linux.  I've been wanting to try it, but I did not want the commitment of installing it to my hd.  I'll keep on trying to figure this out.[/QUOTE]


Rafinator,


I am sure you can get Ubuntu up and running. I tried to make the guide as simple (yet detailed) as possible. You basically answer some setup questions and edit a few text files that Ubuntu uses for it's configuration ... with a few little command line entries thrown in for good measure!

Are there certain installation STEPs that you aren't sure about? There are a lot of good people that check out this thread regularly that could help you figure it out. (They are what made this guide as good as it is!)


DAVE

---

### Post by HJB on 2006-04-13
Ok I did it. If someone else did it before me shoot me. I only read up to page 22/37 (at this time) and couldn't find a suitable answer

**I now Boot from CD and start USB **on my one machine and boot straight from USB on the other.

Wasted 7 cd's in the process but struck gold at last!

I will spend some time later and explain how to do it  (step by step) - again if someone else hasn't already explained this.

Briefly, make a directory iso
In there make sub directory boot and in boot another subdirectory grub
iso --> boot --> grub

Copy the file stage2_eltorito to grub> 

_cp /lib/grub/i386-pc/stage2_eltorito iso/boot/grub_
Thanx to [this page]("http://www.linqi.org/linux/lomd.html")

use nano (or whatever) and create new file 'menu.lst', also in grub subdirectory.

In the boot directory, copy the file I have attached [ATTACH]8292[/ATTACH] and rename to 'initrd.img-2.6.12-9-386' (had to ad gz to be able to attache here)
search for this file on your computer and also copy to the boot directory '_vmlinuz-2.6.12-9-386_'

My menu.lst looks like this:
> default		0
timeout		3
hiddenmenu
color cyan/blue white/blue

### Use gunzip to uncompress miniroot.gz and then mount it (mount -o loop miniroot /mnt). 
### Open linuxrc with your editor.

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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 1_0_initrd-in-root
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 0_0_initrd-in-root
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 1_0_initrd-in-bootdir
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 0_0_initrd-in-bootdir
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


I need someone to tell me why initrd.img sometimes needs to load from /boot and other times not? (still trying to figure this one out)

Thats all you need. Now just run the command from your root directory
_mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o bootcd2usb.iso iso_
and burn the image (I used nero) to your cd
Bootup and if it complains about initrd choose option3
Enjoy

---

### Post by Rafinator on 2006-04-13
Once I install to an external hard drive, can I move it around from computer to computer?  Assuming that their BIOS are configured corectly.

---

### Post by DaBruGo on 2006-04-14
[quote=Rafinator]Once I install to an external hard drive, can I move it around from computer to computer? Assuming that their BIOS are configured corectly.[/quote] 
Rafinator.

You can move it from PC to PC, but you may have to reconfigure the xserver app (and maybe other apps) everytime it is connected to another PC ... just to make sure the video setup is correct for the current PC. (X can be real picky sometimes.)

Maybe some of the others in the forum can elaborate on this a little more.


DAVE

---

### Post by DaBruGo on 2006-04-14
[quote=HJB]Ok I did it. If someone else did it before me shoot me. I only read up to page 22/37 (at this time) and couldn't find a suitable answer

**I now Boot from CD and start USB **on my one machine and boot straight from USB on the other.

Wasted 7 cd's in the process but struck gold at last!

I will spend some time later and explain how to do it  (step by step) - again if someone else hasn't already explained this.

Briefly, make a directory iso
In there make sub directory boot and in boot another subdirectory grub
iso --> boot --> grub

Copy the file stage2_eltorito to grub

_cp /lib/grub/i386-pc/stage2_eltorito iso/boot/grub_
Thanx to [this page]("http://www.linqi.org/linux/lomd.html")

use nano (or whatever) and create new file 'menu.lst', also in grub subdirectory.

In the boot directory, copy the file I have attached [ATTACH]8292[/ATTACH] and rename to 'initrd.img-2.6.12-9-386' (had to ad gz to be able to attache here)
search for this file on your computer and also copy to the boot directory '_vmlinuz-2.6.12-9-386_'

My menu.lst looks like this:


I need someone to tell me why initrd.img sometimes needs to load from /boot and other times not? (still trying to figure this one out)

Thats all you need. Now just run the command from your root directory
_mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o bootcd2usb.iso iso_
and burn the image (I used nero) to your cd
Bootup and if it complains about initrd choose option3
Enjoy[/quote] 
HJB,

That sounds really simple to do. I'm gonna give this a try on my PC to see if it works for me. Thanks for posting it.


DAVE

---

### Post by gholaleto on 2006-04-19
Hey,
   I am having problems when ubuntu goes to load.  GRUB loads and then goes to mount the root filesystem.  I get a flash screen and the progress bar of the OS loading. It says 

mounting root file system...

then

waiting for root file system...

then it just hangs and eventually goes to a Bash prompt
Any idea why this might be?

here is my grub menu config
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
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
#groot=(hd0,0)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-19-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-19-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-19-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-19-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-19-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1


```

Any help would be appreciated, thx.

---

### Post by HJB on 2006-04-20
Hi, this might be wrong but you are using vmlinuz-2.6.15-19-386 and everything is based on vmlinuz-2.6.12-9-386. Just make sure which kernel you have installed.

---

### Post by Killeroid on 2006-04-21
Hmm,I was just wondering,can I update to dapper without getting any problems? I have breezy on a usb drive and used Dabrugo's process. SO if I update to dapper,will it mess up?

---

### Post by skendale on 2006-04-21
So I am receiving the following error message:

Decrompressing Linux...done
Booting the kernel.
Loading, please wait...
FATAL: Module unknown not found.
mount: Mounting /dev/sdb2 on /root failed: No such device
mount: Mounting /root/dec on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init

Busybox ...

/bin/sh: can't access tty; job control turned off


My setup is a little tricky, so I may have done something wrong. I have an internal SATA running xp (ntfs), an internal IDE with just data (ntfs), and an external ide in a usb enclosure with three partitions:

1) win2k (ntfs)
2) ext3
3) swap

I reconfigured my menu.lst to account for all this. It seems like others have had this problem before, but no one seems to know exactly what to do? I tried a couple of reinstalls as well but get the same errors.

Does annnnnnnnnnyone have any thoughtses?

Thanks.

---

### Post by DaBruGo on 2006-04-22
[quote=skendale]So I am receiving the following error message:
 
Decrompressing Linux...done
Booting the kernel.
Loading, please wait...
FATAL: Module unknown not found.
mount: Mounting /dev/sdb2 on /root failed: No such device
mount: Mounting /root/dec on /dev/.static/dev failed: No such file or directory
mount: Mounting /dev on /root/dev failed: No such file or directory
Target filesystem doesn't have /sbin/init
 
Busybox ...
 
/bin/sh: can't access tty; job control turned off
 
 
My setup is a little tricky, so I may have done something wrong. I have an internal SATA running xp (ntfs), an internal IDE with just data (ntfs), and an external ide in a usb enclosure with three partitions:
 
1) win2k (ntfs)
2) ext3
3) swap
 
I reconfigured my menu.lst to account for all this. It seems like others have had this problem before, but no one seems to know exactly what to do? I tried a couple of reinstalls as well but get the same errors.
 
Does annnnnnnnnnyone have any thoughtses?
 
Thanks.[/quote]
 
skendale,
 
 
Have you tried the COMMENT in STEP 8 yet (post #181)?
 
 
DAVE

---

### Post by skendale on 2006-04-22
[QUOTE=DaBruGo]skendale,
 
 
Have you tried the COMMENT in STEP 8 yet (post #181)?
 
 
DAVE[/QUOTE]

yeaahh...i tried that and still no luck sadly...any other ideas?

btw thanks for the instructions...the ubuntu community is ill..

---

### Post by JohanHagelback on 2006-04-23
Hi,

I have problems in Step 8 and 9.
When I boot from CD in rescue mode and selects the correct disk as root the problems start.
En /etc/ there are not folder called mkinitramfs. The system does not recognize mkinitramfs command either so I cannot create a new image file. Anyone know what the problem might be?

Regards,
Johan

---

### Post by DaBruGo on 2006-04-24
[QUOTE=skendale]yeaahh...i tried that and still no luck sadly...any other ideas?

btw thanks for the instructions...the ubuntu community is ill..[/QUOTE]

Try setting the WAIT delay in step 9 up a little higher ... maybe 15 or 20 and see if that gets you any farther along.

Also, if you can, try to post your menu.lst file so we can take a look at it.

DAVE

---

### Post by DaBruGo on 2006-04-24
[QUOTE=JohanHagelback]Hi,

I have problems in Step 8 and 9.
When I boot from CD in rescue mode and selects the correct disk as root the problems start.
En /etc/ there are not folder called mkinitramfs. The system does not recognize mkinitramfs command either so I cannot create a new image file. Anyone know what the problem might be?

Regards,
Johan[/QUOTE]

Hi Johan,

Did you have any problems in previous steps? Are you sure you typed in the commands in STEP 7 exactly as they were posted?


DAVE

---

### Post by DaBruGo on 2006-04-24
[QUOTE=Killeroid]Hmm,I was just wondering,can I update to dapper without getting any problems? I have breezy on a usb drive and used Dabrugo's process. SO if I update to dapper,will it mess up?[/QUOTE]

Killeroid,

I had someone in another thread say they used this guide to install Dapper without any problems. But as far as UPGRADING to Dapper .. I don't have an answer for you yet.


DAVE

---

### Post by JohanHagelback on 2006-04-25
[QUOTE=DaBruGo]Hi Johan,

Did you have any problems in previous steps? Are you sure you typed in the commands in STEP 7 exactly as they were posted?


DAVE[/QUOTE]

No, the command didn't work exactly (I read in another page found at Google that these steps weren't necessary. Obviously they are...). This is what I type:
mount -tproc proc /target /proc
No error returned
chroot /target
Error: chroot: cannot execute /bin/sh: No such file or directory
ch
Error: /bin/sh: su: not found

/Johan

---

### Post by Killeroid on 2006-04-25
[QUOTE=DaBruGo]Killeroid,

I had someone in another thread say they used this guide to install Dapper without any problems. But as far as UPGRADING to Dapper .. I don't have an answer for you yet.


DAVE[/QUOTE]

Ok,thanks for the reply. I guess it is back to the install board. Time to burn the cd

---

### Post by DaBruGo on 2006-04-28
[QUOTE=JohanHagelback]No, the command didn't work exactly (I read in another page found at Google that these steps weren't necessary. Obviously they are...). This is what I type:
mount -tproc proc /target /proc
No error returned
chroot /target
Error: chroot: cannot execute /bin/sh: No such file or directory
ch
Error: /bin/sh: su: not found

/Johan[/QUOTE]


Johan,


There is no space between /target and /proc (/target/proc) in the first command line for that STEP. It looks like you added a space from your post above. 

Try running in rescue mode again and typing this in for the STEP ...
( where <space> = insert a space )

mount [COLOR="Red"]<space>[/COLOR] -tproc [COLOR="#ff0000"]<space>[/COLOR] proc [COLOR="#ff0000"]<space>[/COLOR] /target/proc [COLOR="Red"]<enter>[/COLOR]
chroot [COLOR="Red"]<space>[/COLOR] /target [COLOR="#ff0000"]<enter>[/COLOR]
su [COLOR="#ff0000"]<enter>[/COLOR]

That might get it going if you had mis-typed the command. I hope it works for you.


DAVE

---

### Post by Ilove2023 on 2006-04-29
Hello!

I've a weird problem with my ubuntu's installation.
I tried to install ubuntu on a external usb udd (Western Digital 320 GB with AC power), following this topic. Everythings was fine!


But i wan't to install ubuntu on a hdd usb-powered (philipps 2.5", 80 GB), because it's more easy with my laptop ;) . I followed this topics, like with the WD disk so, but i got a "ALERT! /dev/sda1 not found " error !!
and a few moment later, the two lines appear on the shell :
[xxxxxx.xxxx] sda : assuming drive cache : write through
[xxxxxx.xxxx] sda : assuming drive cache : write through
(where "x" are numbers)
I tried to put other values int the WAIT statement of the initramfs.conf file, I put others modules et the "modules" file...
I tried the "sleep" scripts of scotty_boy too, i got the same error but in a longer time ;)

I don't know what to do, but i guess it's a matter of time between the access of my hdd and its initiatlisation...

Anybody can help me ?
Thanks!

[sorry for my poor english)

---

### Post by Killeroid on 2006-04-30
[QUOTE=Killeroid]Hmm,I was just wondering,can I update to dapper without getting any problems? I have breezy on a usb drive and used Dabrugo's process. SO if I update to dapper,will it mess up?[/QUOTE]

[QUOTE=DaBruGo]Killeroid,

I had someone in another thread say they used this guide to install Dapper without any problems. But as far as UPGRADING to Dapper .. I don't have an answer for you yet.


DAVE[/QUOTE]

Dave/DaBruGo, I successfully updated to Dapper Beta 2 yesterday. During the update, I was asked whether I wanted my mkinitramfs file to be updated and I specified no and so retained all my settings without having to reconfigure ubuntu again.

So,yes,users of this method can update to dapper,just click on keep to keep your old mkinintramfs file when prompted.

---

### Post by Ilove2023 on 2006-04-30
Does someone try to install ubuntu on a selfpowered usb hdd? 
the installation on a AC-powered disk was fine, but the installation on my usb-powered disk crach on the first reboot with "ALERT! /dev/sda1 does not exists" !!
Please, help me !

---

### Post by briancof on 2006-05-02
Hey all,

I've been trying to run Breezy on my Dell D610 and install it on a USB external. I followed the guide exactly (as nearly as I can tell), but when I get to the part where I exit rescue mode and remove the CD before the BIOS loads, it goes into XP.

I have the Boot order set as: 

1. CD/DVD  2. USB Storage  3. Internal HDD

so I'm guessing the BIOS just isn't recognizing the external for some reason. Could the WAIT time be too short?

Possible explanation: In (STEP 11) of the guide, there is an INSTALL NOTE: that says *"you may want to change the root line for the... to (hd1,0) just in case..."*

I did that, so I don't know if that may have caused the problem. I'm brand new to linux, and certainly don't know as much about computers in general as most here probably do. If you have any ideas, suggestions, or theories, I'm all for trying them.

Thanks!

Brian

---

### Post by DaBruGo on 2006-05-02
[quote=Killeroid]Dave/DaBruGo, I successfully updated to Dapper Beta 2 yesterday. During the update, I was asked whether I wanted my mkinitramfs file to be updated and I specified no and so retained all my settings without having to reconfigure ubuntu again.
 
So,yes,users of this method can update to dapper,just click on keep to keep your old mkinintramfs file when prompted.[/quote]
 
 
Killeroid,
 
 
Thats awesome! Thanks for posting the info. When I get a chance I will add that to the appropriate STEP in the first post so others will know how to upgrade to Dapper without messing up their settings.
 
Thanks for posting!
 
 
DAVE

---

### Post by DaBruGo on 2006-05-02
[quote=briancof]Hey all,
 
I've been trying to run Breezy on my Dell D610 and install it on a USB external. I followed the guide exactly (as nearly as I can tell), but when I get to the part where I exit rescue mode and remove the CD before the BIOS loads, it goes into XP.
 
I have the Boot order set as: 
 
1. CD/DVD 2. USB Storage 3. Internal HDD
 
so I'm guessing the BIOS just isn't recognizing the external for some reason. Could the WAIT time be too short?
 
Possible explanation: In (STEP 11) of the guide, there is an INSTALL NOTE: that says *"you may want to change the root line for the... to (hd1,0) just in case..."*
 
I did that, so I don't know if that may have caused the problem. I'm brand new to linux, and certainly don't know as much about computers in general as most here probably do. If you have any ideas, suggestions, or theories, I'm all for trying them.
 
Thanks!
 
Brian[/quote]
 
Brian,
 
That (hd1,0) root command (mentioned in STEP 11) is ONLY USED for the Windowx XP boot section in your GRUB menu.lst file ... and only if you want the option to boot into windows via the GRUB menu.
 
The three other sections in menu.lst that have Ubuntu mentioned (normal, rescue, and memtest) should all be (hd0,0) because you loaded GRUB to the bootsector of the external drive.
 
If you get things setup correctly (and working) for Ubuntu and then have problems booting into the Windows XP option on the GRUB menu then change the root line for ONLY the Windows XP section in your menu.lst file to (hd1,1). The reason for this is that DELL PCs sometimes have two partitions setup on them from the factory. (One for installation purposes and one for the XP partition.)
 
Let me know if this fixes your problem.
 
 
DAVE

---

### Post by DaBruGo on 2006-05-02
[quote=Ilove2023]Does someone try to install ubuntu on a selfpowered usb hdd? 
the installation on a AC-powered disk was fine, but the installation on my usb-powered disk crach on the first reboot with "ALERT! /dev/sda1 does not exists" !!
Please, help me ![/quote]
 
 
Ilove2023,
 
 
That is exactly how I installed Ubuntu (on a self-powered drive) when I started this setup guide. Is it possible for you to post your menu.lst file for us to look at?
 
 
DAVE

---

### Post by DaBruGo on 2006-05-02
[quote=Ilove2023]Hello!
 
I tried to put other values int the WAIT statement of the initramfs.conf file, I put others modules et the "modules" file...
I tried the "sleep" scripts of scotty_boy too, i got the same error but in a longer time ;)
 
I don't know what to do, but i guess it's a matter of time between the access of my hdd and its initiatlisation...
 
Anybody can help me ?
Thanks!
 
[sorry for my poor english)[/quote]
 
 
Ilove2023,
 
 
If you make any changes to STEP 8 and/or STEP 9, don't forget that you have to do STEP 10 again (recompile the initial ramdisk) for them to work when you startup Ubuntu.
 
So, if you made any changes, startup in RESCUE mode again and run STEP 10 for your changes to be active.
 
 
DAVE

---

### Post by briancof on 2006-05-02
Dave,

Thanks for your response. The problem isn't that I have a GRUB menu and don't want it, it's that I don't have one and want it. I haven't been able to boot off the external hd at all. I've tried the root command both ways (hd1,0) and (hd0,0) and neither seems to make a difference. I'd like to avoid putting a GRUB in my internal MBR (this screwed everything up last time), but am willing do put anything in the external boot sector to make it load.

Thanks,

Brian

---

### Post by e-sabbath on 2006-05-03
(Deleted)

---

### Post by Olle on 2006-05-05
[QUOTE=Ilove2023]Does someone try to install ubuntu on a selfpowered usb hdd? 
the installation on a AC-powered disk was fine, but the installation on my usb-powered disk crach on the first reboot with "ALERT! /dev/sda1 does not exists" !!
Please, help me ![/QUOTE]

I have the same problem. Try this: When booting, just after kernel and initrd is loaded and initrd is uncompressed, unplug the usb device and plug it in again. This works for me. It's a problem with coldplugging, kernel, hal, udev is having problem detecting the partition table on disc.

---

### Post by theorem_hunter on 2006-05-07
success is near for me:)

thank you for the great guide

i have two hard drives, the first is a western digital 250gig WDC WD2500JS-40MVB1, which has two partitions. the first is for windows xp, the second is were is dump all my music, movies, stuff. both are ntfs.

the second hard drive i have is a samsung 120gig SAMSUNG SP1203N, which has four (4) partitions.
the first is a 8mb unpartitioned space. the second is a ntfs, the third is my swap, the fourth is ext2

i have my bios setup to boot form the samsund first then the western digital.

i installed grub onto /dev/sdb
swap is @ /dev/sdb6
ext2 is @ /dev/sdb7

my menu.lst looks something like this 

.
#groot=(hd0,0)
.

& the ubuntu parts were the same (hd0,0)

when i boot up, i get a grub error 17

so i tried fiddling with the #groot=(hd0,0) & the ubuntu:
 title        Ubuntu, kernel 2.6.12-9-386 
root        (hd0,0)

so i changed the (hd0,0) a few times with different combinations. 
(hd1,0)
(hd0,1)
(hd0,6)
(hd1,6) which is what is originaly was
(hd1,1)

im getting close but if you know a way that they could be setup correctly that would help a lot. thanks again

-=-

ok so i played around with some of the combinations, and had a bit of success.
i set:
#groot=(hd0,0)

title        Ubuntu, kernel 2.6.12-9-386 
root        (hd0,6)

for all 3 of those.

then when i boot i still get the grub error 17, but if i use the bois boot manager & chose the samsung hard drive to boot to it pops up with grub and it works like normal.

so my question now becomes how can i make it boot to grub normaly
the bios was set to boot to the samsung first & then the WD

any thoughts?

---

### Post by ncappel1 on 2006-05-08
I tried the guide, but it seems that the place I go wrong is with my BIOS settings. How do I change them to allow usb booting?

I have tried to press "esc" at the blue boot "HP" screen at my computer. I get into the pheonix Bios configuration thing. When I navigate to the boot order process, I don't see any options for the usb drive. I have only options for internal harddrives, removeable drives, atapi drives (cd drive?) and floppy. 

can anyone help me with this one?

---

### Post by scratched on 2006-05-13
[QUOTE=ncappel1]I tried the guide, but it seems that the place I go wrong is with my BIOS settings. How do I change them to allow usb booting?

I have tried to press "esc" at the blue boot "HP" screen at my computer. I get into the pheonix Bios configuration thing. When I navigate to the boot order process, I don't see any options for the usb drive. I have only options for internal harddrives, removeable drives, atapi drives (cd drive?) and floppy. 

can anyone help me with this one?[/QUOTE]

It looks like your computer's BIOS don't let you boot to a USB device. I don't remember how to do it, but there is a way to create a boot disk (either CD or floppy) that would allow you to boot to a USB drive. You'd have to do some research to find out how to do that. Maybe someone else on these forums knows the answer to that.

You could also try looking for updates for your computers BIOS on HP's website.

---

### Post by Lobut on 2006-05-13
I followed the steps here and received the good old: 'alert /dev/sda1 does not exist'.

There were a few steps in here that said it would help like increasing the time and creating the acpid file.

Eventually I was able to get in. After celebrating 5am last night, I woke up 2pm and now it's giving me the same alert problem. Other than a cold boot I didn't do anything last night.

---

### Post by vekron on 2006-05-14
Hi,

Like many people here, I am getting the error [COLOR="Red"]ALERT! /dev/sda1 does not exist. Dropping to a shell![/COLOR], which is quickly followed by, as described in post [#382]("http://www.ubuntuforums.org/showpost.php?p=969220&postcount=382"), 
[QUOTE=Ilove2023]
[COLOR="Red"][xxxxxx.xxxx] sda : assuming drive cache : write through
[xxxxxx.xxxx] sda : assuming drive cache : write through[/COLOR]
(where "x" are numbers)
I tried to put other values int the WAIT statement of the initramfs.conf file, I put others modules et the "modules" file...
I tried the "sleep" scripts of scotty_boy too, i got the same error but in a longer time ;)
[/QUOTE]
The same exact thing is happening to me: unlike some people, I don't get a message recognizing the existence of the external hard drive a few seconds later.

Besides increasing the WAIT parameter to 20 and trying [scotty_boy's acpid script]("http://www.ubuntuforums.org/showpost.php?p=690695&postcount=167"), I've tried adding extra parameters to the /etc/mkinitramfs/modules file (from the posts [here]("http://www.ubuntuforums.org/showpost.php?p=705797&postcount=181") and [here]("http://www.ubuntuforums.org/showthread.php?t=57741")) and messing with the 'root' parameter in GRUB (also from one of the posts in this thread). All that was in addition to doing three (!) clean installs.

My /boot/grub/menu.lst file seems to be close to the ones posted here as examples, but I can try posting it here if you think that might help.

Now, I'm pretty much out of ideas, especially since I have little Linux experience. Help! ](*,) 

The install CD I'm using is actually Kubuntu, but (I think) that doesn't matter at this stage of the boot process, especially since I'm getting errors identical (even in timing) to the ones others get.

---

### Post by Rob_ on 2006-05-16
Thanks a ton DaBruGo, and all others who offered up info on this.  I've been wanting to do something like this for awhile now, as I wanted to install Linux, but not overwrite WinXP.

Being completely new to Linux, I've got to say, I only ended up getting nervous during one point (the /dev/discs/disc1/part1 deal).  I wasn't sure which was which :P  But other than that, everything went exactly as you said it would.  Now I can finally learn more about Linux without a Live CD.  Thanks tons!!!

---

### Post by HJB on 2006-05-17
[QUOTE=ncappel1]I tried the guide, but it seems that the place I go wrong is with my BIOS settings. How do I change them to allow usb booting?

I have tried to press "esc" at the blue boot "HP" screen at my computer. I get into the pheonix Bios configuration thing. When I navigate to the boot order process, I don't see any options for the usb drive. I have only options for internal harddrives, removeable drives, atapi drives (cd drive?) and floppy. 

can anyone help me with this one?[/QUOTE]

Hi there, have a look here:
[http://www.ubuntuforums.org/showpost.php?p=919274&postcount=365](http://www.ubuntuforums.org/showpost.php?p=919274&postcount=365)

---

### Post by tertullian01 on 2006-05-22
I went all of the way through the tutorial and had little to no troubles.  I didn't see any error message and everything happened as explained.  However, after the 12th step I pull out the cd and let it reboot.  It gets to a black screen with a blinking cursor.  It waits there for 5-10 seconds and then continues to boot from the hard drive.  If I don't plug in the external hard drive there is no black screen with blinking cursor.  So it seems to find the hard drive and think about booting from it.  But for whatever reason it never does.  Any thoughts?

---

### Post by jmb365 on 2006-05-25
Hello All,

I am not sure if this is the right thread to post in, but I am trying to get a WD 1600C032 Ext USB Hard Drive to be recognized by Ubuntu Breezy (2.6.12-9-386).  I am NOT trying to load/boot Breezy from this Ext USB HD, but just trying to mount it.

It is factory preformatted as FAT32 I believe.  I have tried loading many modules and methods in Breezy.  The only time I am able to see /dev/sda & /dev/sda1 for a brief moment is if I power down the Ext USB HD and power it up again while the Breezy is running.

A "fdisk -l" just hangs there if the USB drive is connected.

less /var/log/messages
localhost kernel: [4296385.744000] SCSI subsystem initialized
localhost kernel: [4296385.780000] Initializing USB Mass Storage driver...
localhost kernel: [4296385.800000] usbcore: registered new driver usb-storage
localhost kernel: [4296385.800000] USB Mass Storage support registered.
localhost kernel: [4296973.922000] usb 1-1: new full speed USB device using uhci_hcd and address 6
localhost kernel: [4296982.422000] usb 1-1: new full speed USB device using uhci_hcd and address 7
localhost kernel: [4296982.529000] scsi0 : SCSI emulation for USB Mass Storage devices
localhost usb.agent[6731]:      usb-storage: already loaded
localhost kernel: [4296987.538000]   Vendor: WD        Model: 1600JS External   Rev: 101a
localhost kernel: [4296987.538000]   Type:   Direct-Access                      ANSI SCSI revision: 04
localhost kernel: [4296987.551000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
localhost kernel: [4296987.561000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
localhost kernel: [4296987.561000]  /dev/scsi/host0/bus0/target0/lun0: p1
localhost kernel: [4296987.579000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
localhost scsi.agent[6778]:      sd_mod: loaded sucessfully (for disk)
localhost kernel: [4297063.652000] usb 1-1: reset full speed USB device using uhci_hcd and address 7
localhost kernel: [4297082.046000] usb 1-1: reset full speed USB device using uhci_hcd and address 7
localhost kernel: [4297100.440000] usb 1-1: reset full speed USB device using uhci_hcd and address 7
localhost kernel: [4297110.731000] usb 1-1: reset full speed USB device using uhci_hcd and address 7
localhost kernel: [4297120.959000] scsi: Device offlined - not ready after error recovery: host 0 channel 0 id 0 lun 0
localhost kernel: [4297120.959000] usb 1-1: USB disconnect, address 7
localhost kernel: [4297121.087000] usb 1-1: new full speed USB device using uhci_hcd and address 8
localhost kernel: [4297139.481000] usb 1-1: new full speed USB device using uhci_hcd and address 9
localhost kernel: [4297157.875000] usb 1-1: new full speed USB device using uhci_hcd and address 10
localhost kernel: [4297168.165000] usb 1-1: new full speed USB device using uhci_hcd and address 11

I have not been able to figure out why the drive is being offlined after being recognized.  It is a new drive that works in a WinXP PC.  I have tried 3 different Breezy PC's with no luck.

Modules loaded are:
# ohci-hcd       # Autoloaded
modprobe ehci_hcd
# uhci_hcd	# Autoloaded
modprobe usb_storage
# usbcore       # Autoloaded
modprobe usbhid
modprobe scsi_mod
modprobe sd_mod

Any help would be appreciated!  My apologies if this is not the right thread.  I could not find any other thread that seemed relevant.  Thanks.

-JBM

---

### Post by jerseyboy91 on 2006-05-30
OK, before I tell you my problem, I want to say thank you for this great tutorial! I've gotten to Step 12, but when I restart, the GRUB boot loader (Stage 1.5) starts up, then it says Error 2 and stops. It may be because I did something wrong in editing the menu.lst file, but I'm not sure. Right now, I'm looking at some of the threads and at Google for help, but if anyone can help me here, it would be greatly appreciated.

Edit: OK, here's the menu.lst file. Seeing how you've fixed most everyone else's problems, maybe you could help mine. ;) 

# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
[B]# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1[/B]
#
[B]# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro[/B]
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro acpi=off
[B]
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)[/B]

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-9-386 
**root		[B](hd0,0)**[/B]
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro acpi=off quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
**root		[B](hd0,0)**[/B]
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro acpi=off single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
**root		(hd0,0)**
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
[B]title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
chainloader	+1
[/B]

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
[B]title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1[/B]

______________________________
I spaced the 8's at the beginning so the smileys wouldn't show up and I bolded the areas I edited.

---

### Post by keri_ubu on 2006-06-04
Dapper 6.06 installation on external USB HD

Thank you! Following this tutorial for Breezy I succeeded to install Dapper 6.06 on my external USB drive. I had read that on Dapper 6.06 the installation on external HD is supported, so I gave it a try.
For this I used the 64-bit PC (AMD64) alternate install CD (not the desktop/live CD) and I had to enable USB HD booting in the BIOS of the laptop before starting. 
I followed the tutorial and skipped steps 7 to 10 of the since I expected that in Dapper this should not be needed anymore (which is correct). 
After reboot after step 12 however, the changes in "menu.lst" seemed not to be taken into account right away. I had first to do "reinstall grub" in rescue mode on " /dev/sda " (using again the install CD as in step 4&5), and then after a new reboot, the root (hd0,1) had effectively changed into root (hd0,0) during the grub bootmenu.

So now I can boot from the external HD and run Dapper from it without any change to my internal HD. If I don't connect the USB drive, it just boots the internal HD as before. Great!

(my configuration: Packard Bell Easynote (AMD Turion 64) laptop, and Maxtor 300Gb USB drive)

---

### Post by Jonathan.Martin on 2006-06-05
Hi all,

I attempted an install on my usb drive a while ago on Breezy which was a bit unsuccessful. Now Im on the case with dapper and feel as if Im nearly there apart from an error Im getting. The problem is:

mounting /dev/sdb1 on root failed - No Such Device

Which Im assumming, hopefully correctly that this is due to the usb device not being initialised. I have set the /etc/mkinitramfs/modules as per the tutorial and set the WAIT time to 20 rather than 12 in the initramfs.conf

If anyone could suggest anything to fastrack my efforts it would be greatley appreciated.

Living in Hope,

Jonathan.

---

### Post by sagan on 2006-06-06
Hi all,
I am new to linux and would like to share my experience in the installation process.

I tried to install Breezy on an external USB drive by following the steps prescribed by DaBruGo. Everything went well until I got : 'alert /dev/sdb1 does not exist.Dropping to a shell!'.

After hours of trials and errors, I chanced upon a workaround and successfully boot up.

Here's the steps of the workaround:
1) When GRUB menu appears during booting, edit entry 'Ubuntu, kernel 2.6.12-9-386'
2) Edit line 'kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro quiet splash' to become 'kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/sdb1 ro single'. 
2) Add a dummy line with invalid command (e.g. test) before line 'boot'.
3) Press 'b' to boot. Error 27 will appear due to the invalid command.
4) Then reboot again. When GRUB menu appears, delete the dummy line and then press 'b' to boot. Ubuntu will boot successfully to the desktop

I have no idea why the above steps work. Would appreaciate if someone could advise on the real counter measure. Thanks.

---

### Post by Jonathan.Martin on 2006-06-06
[QUOTE=Jonathan.Martin]Hi all,

I attempted an install on my usb drive a while ago on Breezy which was a bit unsuccessful. Now Im on the case with dapper and feel as if Im nearly there apart from an error Im getting. The problem is:

mounting /dev/sdb1 on root failed - No Such Device

Which Im assumming, hopefully correctly that this is due to the usb device not being initialised. I have set the /etc/mkinitramfs/modules as per the tutorial and set the WAIT time to 20 rather than 12 in the initramfs.conf

If anyone could suggest anything to fastrack my efforts it would be greatley appreciated.

Living in Hope,

Jonathan.[/QUOTE]

Hi All,

Managed to get it working ... IDEAL.
The problem was the ordering of the USB module loading in
/etc/mkinitramfs/modules

This is the order I had to make it work:

usb-storage
usbcore
usbhid
ehci-hcd
uhci-hcd
scsi_mod
sd_mod


Now I have some problems with the Xserver configuration, due to the support of lack of it on my mobility X700 card, but thats a different story.(Ive simply changed the driver from ati to fglrx in the meantime).

Good Luck,

Jonathan.

---

### Post by maltje on 2006-06-07
sorry for the double post,but here it is a better place to ask I think.
I like to instal Dapper on my laptop but have a broken cdrom-drive.
I have an externel cdrom with usb,but I can't install ubuntu this way??
Isn't there a good solution for it?

---

### Post by Dropknee on 2006-06-13
Maybe this is a Stupid question, but I want to be sure....

 In Ubuntu Dapper 6.06 Alternate CD I got this opcion in boot up
Text Install
Oem Install 
Server Install

My question is..... OEM install is the same as Expert installation??? 

 I reallly want to clear my doubt about this, I do this installation in breezy with success, but in dapper the boot opcion change, so pls someone clear my mind about this

Thx

---

### Post by keri_ubu on 2006-06-13
[QUOTE=Dropknee]Maybe this is a Stupid question, but I want to be sure....

 In Ubuntu Dapper 6.06 Alternate CD I got this opcion in boot up
Text Install
Oem Install 
Server Install

My question is..... OEM install is the same as Expert installation??? 

 I reallly want to clear my doubt about this, I do this installation in breezy with success, but in dapper the boot opcion change, so pls someone clear my mind about this

Thx[/QUOTE]

Text mode can be considered as expert mode. End users will not need OEM install mode, see below explanations (from [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm)) Good luck!

**Text mode install**. The text mode install is the popular choice for most good professional or home users. 

**Install in 'OEM' mode**. The (Original Equipment Manufacturer) installation is for computers that are being set up in a factory or a store with Ubuntu pre-installed.  During the OEM installation, you set an OEM password. You then log in with the username 'oem' and the password that you set. After you shut down, it will be set up to allow the new owner to set up their own new user account on boot-up.

---

### Post by Jonathan.Martin on 2006-06-16
OK Chaps and Chapesses,

Surely someone can solve this problem and at the same time help find my temper.

After a lot of effor I successfully installed ubuntu on an 2.5" laptop drive via usb sitting externally. Though to have any success with this I had to install using the alternative installer via text mode. (Oh I forgot to mention Im new to all of this so you may have to bear with it :-) ).

I did this as the machine im using is a laptop used for development and felt it would make the transition from windows to ubuntu easier if I did it this way keeping total seperation between the two operating systems.

I spent a long time getting my ubuntu dev environment configured and have been quite happy for a couple of days until this morning.

I accidentaly forgot - and I know this is really my fault - to check what was being updated by the updater, and on clicking install watched the new non alternative kernel image 2.6.15-15-25 being installed. Now every time I attempt to boot either images from the grub installer I get the following error:

File System Type Unknown - Partition Type 0x7
Kernel /boot/umlinuz-2.6.15-25-386 root=/dev/sdb1
Error 17 Cannot Mount Selected Partition

Now this has led me to having a couple of questions:

Firstly does anyone know how I can easily fix this as If I have to reinstall I'll probably just go back to windows where my dev environment is already setup.

If I hadnt installed the new kernel version - What exactly would I have been missing out on.

If I hadnt installed the new kernel version, can I stop the updater looking for new kernel versions and stopping the notify.


Appologies for the long winded post, im just pretty cheesed off at the moment.


Cheers,

Jonathan.

---

### Post by scratched on 2006-06-16
Your problem happens to just about everyone I think. I had the same problem. All that happened is somehow GRUB got pointed to the wrong drive. You just need to change one text file. 

To boot into Ubuntu directly from the boot loader so you can fix the problem, highlight Ubuntu from the GRUB menu and press 'e'. Now you can edit the details of that choice. Change the part that says "root=/dev/sdb1" to say "root=/dev/sdb0" and then boot up.

This will not fix the problem permanently, only for that one time. To fix it permanently, open the terminal and type ```
sudo gedit /boot/grub/menu.lst
```

In the menu.lst file, scroll down towards the bottom of the file and find the line that says
```
Kernel /boot/umlinuz-2.6.15-25-386 root=/dev/sdb1
```
and change the part that says "sdb1" to say "sdb0" and save it.

That should fix the problem. I don't know the exact changes added with the new kernel, but my guess is that it is mostly stability improvements. Check [Kernel.org]("http://kernel.org") for the list of changes.

---

### Post by Jonathan.Martin on 2006-06-16
[QUOTE=scratched]Your problem happens to just about everyone I think. I had the same problem. All that happened is somehow GRUB got pointed to the wrong drive. You just need to change one text file. 

To boot into Ubuntu directly from the boot loader so you can fix the problem, highlight Ubuntu from the GRUB menu and press 'e'. Now you can edit the details of that choice. Change the part that says "root=/dev/sdb1" to say "root=/dev/sdb0" and then boot up.

This will not fix the problem permanently, only for that one time. To fix it permanently, open the terminal and type ```
sudo gedit /boot/grub/menu.lst
```

In the menu.lst file, scroll down towards the bottom of the file and find the line that says
```
Kernel /boot/umlinuz-2.6.15-25-386 root=/dev/sdb1
```
and change the part that says "sdb1" to say "sdb0" and save it.

That should fix the problem. I don't know the exact changes added with the new kernel, but my guess is that it is mostly stability improvements. Check [Kernel.org]("http://kernel.org") for the list of changes.[/QUOTE]

Hi Scratched,

I changed the parameter in the grub menu to "root=/dev/sdb0" from "sdb1" as suggested, but still got the same error.  Im wondering if my drive is seen differently ie "/dev/sda0". Im going to have a play round with it but any other suggestions would definitley be appreciated.

- New Update
I realised that it was the grub loader itself had the drive incorrect ie had gone back to (hd1,0) instead of (hd0,0) on changing grub onload I could see the UBUNTU loading screen. But at the point of mounting the root file system it crashed, whith  the same symptoms i had when incorrect usb mounting modules in /etc/mkinitramfs/modules.  Though I have re-compiled the kernel to be the same as the previous version (23-386).  As im pretty new to this I dont understand why the new kernal needs different or a re-ordering of modules, and I can now boot into the old kernel. Aany advice would be appreciated.


******* FIXED *******
After trying everything apart from getting my dog to lick the monitor I eventually got it to work.  I had previously been running the mkinitramfs command by booting through the 'Rescue Mode' of the installation CD. Instead of doing this I booted into the old kernel and ran the command there (not forgetting to run under sudo). When I attempted to boot into the new kernal it worked. As Ive always stated Im new to this and am not sure why this made any difference. If someone could comment on this im sure people will find it useful.

Thanks for Reading.


Cheers,

Jonathan.

---

### Post by bamarob on 2006-06-21
Jonathan.Martin,

I'm having a similar issue.  I have Ubuntu 6.06 LTS installed on an external 40 GB USB HD that I partitioned to have ~10 GB for "/", ~28 GB for "/home", and the rest in swap.  The installation went fine.  Booting from the CD, I can mount the partitions and see that everything appears to have installed (including my home folder in the "/home" partition).  When I try booting from the USB drive, it hangs waiting for the root filesystem.  So, I follow the instructions here to the letter, but I can't boot from the drive.  I can run fine from the drive when I chroot over to it.  Just can't get it to boot.  And, the problem is related to the loading of the USB modules, I'm sure.  When it hangs, I can CTRL-ALT-F1 and see:

[code]udevd-event[1888]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6.4/1-6.4:1.0/host0/target0:0:0/0:0:0:0/bus' failed

The modules have have in /etc/mkinitramfs/modules are:

ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod

Any suggestions would be greatly appreciated.

BamaRob

---

### Post by bamarob on 2006-06-22
OK.  Obviously, nobody's reading this.  Probably because it's under the Breezy forum.  Anyhow, for anyone that might read it, I found that when it's stuck at the 'Waiting for root file system...', I can unplug/replug the USB drive and it picks back up and boots.  I'm posting from Ubuntu running on the USB drive now. :D

I may try posting this query in the Dapper forums to see if I get any response.  I posted here because my problem seemed very similar to those discussed in this thread.

Thanks,

BR

---

### Post by Jonathan.Martin on 2006-06-22
Hi,

Dont forget there are many people round the word who are in bed when you post :-) 

Unfortunately I may not be a great deal of help here. It may be worth trying to alter the loading sequence of your modules Ie. putting the usbcore stuff first like in my previous thread and increase the waiting time to 30 rather than 12.
If your 2.5" drive is in a caddie it may be the caddie thats the problem. I have three different caddies and only one of them has had any success in doing this. One doesnt even get recognised by the partitioner at load time, the other hangs at the mounting root parition and simply stops.

A quick tip which may be a red herring, is that when my bios boots, the caddie is seen a s a generic usb drive, this one works.  The others which dont work show the name of the drive ie Toshiba 80gb drive, it may be worth checking how your bios sees the caddie.

I know this doesnt help alot - But keep trying.

Good luck,

Jonathan.

---

### Post by bamarob on 2006-06-22
[QUOTE=Jonathan.Martin]Hi,

Dont forget there are many people round the word who are in bed when you post :-) 
[/quote]

I figured 22 hours was long enough.  I guess some people sleep more than I do. :D

[QUOTE=Jonathan.Martin]Unfortunately I may not be a great deal of help here. It may be worth trying to alter the loading sequence of your modules Ie. putting the usbcore stuff first like in my previous thread and increase the waiting time to 30 rather than 12.[/quote]

Thanks.  I'll try those tips.

[QUOTE=Jonathan.Martin]If your 2.5" drive is in a caddie it may be the caddie thats the problem. I have three different caddies and only one of them has had any success in doing this. One doesnt even get recognised by the partitioner at load time, the other hangs at the mounting root parition and simply stops.

A quick tip which may be a red herring, is that when my bios boots, the caddie is seen a s a generic usb drive, this one works.  The others which dont work show the name of the drive ie Toshiba 80gb drive, it may be worth checking how your bios sees the caddie.
[/quote]

My drive is actually just a spare 2.5" laptop drive (identical to the one in my laptop) housed in a USB caddy.  I'll definitely have to look into this and see how the BIOS lists the drive.

Thanks for replying.  I'll reply to this post with results.

BR

---

### Post by bamarob on 2006-06-27
I just booted my laptop from the USB drive (having to disconnect/reconnect the drive), connected to my home network, and ran synaptic to update the box.  In doing so, a new kernel was installed.  After the reboot, I no longer have to disconnect/reconnect the drive during boot.  I'm not sure what fixed it, but it works.  I'm not complaining.  My /etc/mkinitramfs/modules file hasn't changed.  Perhaps the new kernel (2.6.15-25-386) just handles USB better????

BamaRob

---

### Post by jdpipe on 2006-06-30
Hi Jerseyboy

I had the same problem. My conclusion was that some BIOSes claim to support USB booting but actually don't. I took it up with the GRUB mailing list, and I posted on this thread as well, several times. Nobody had any useful suggestions, far as I could tell. I followed the instructions on a newer system and it all 'just worked'. The only suggestion I have is that you could buy the 'ubuntusb' product from [www.pertec.com](www.pertec.com), and try that. It gives you a CD that you can use to boot your USB drive in the cases where booting direct off USB doesn't work.

[QUOTE=jerseyboy91]OK, before I tell you my problem, I want to say thank you for this great tutorial! I've gotten to Step 12, but when I restart, the GRUB boot loader (Stage 1.5) starts up, then it says Error 2 and stops. It may be because I did something wrong in editing the menu.lst file, but I'm not sure. Right now, I'm looking at some of the threads and at Google for help, but if anyone can help me here, it would be greatly appreciated.
[/QUOTE]

---

### Post by Zerlinna on 2006-06-30
You don't have to buy a boot CD - you can just make it yourself very easy, see here: [http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html](http://zerlinna.blogweb.de/archives/52-Dual-boot-on-external-USB-Drive-with-a-BootCD-with-Bios-not-supporting-boot-from-external-device.html)

Z.

---

### Post by nolongerlivecd on 2006-07-03
I just installed on my external Hard Disk 40GB Seagate 2.5", using the Dapper pressed CD, the free ones ordered from ShipIt.

The install was smooth, but I did not monitor it, only a quick glance now and then.

I installed it on sda3, as my hard disk currently is:

Size     mount type    usage
5GB     /          ext3    Ubuntu
0.5GB  /swap  swap   Swap
4.5GB  ?         FAT32  Programs
30GB   ?         FAT32  Data

I didn't see GRUB get installed, and I can't access rescue mode on either 6.06 or 5.10 live and install CDs.
I can't boot from the hard disk either, even though my motherboard is supposed to support it (Intel 865PERL).
What should I do?

---

### Post by gobbluth on 2006-07-12
Hello,
Firstly, kudos for this stellar howto, and secondly I'd like to apologize in advance if this has already been answered. I've googled, and I have searched these boards, but alas, have found nothing yet.

Using this guide (with a modification or two when editing the modules file) I was able to smoothly install Dapper on my 100GB Maxtor external usb drive about a month ago. It worked perfectly for a week and I loved it. Strangely, it stopped being able to boot, it would simply come up with a screen that said something to this effect when I booted my laptop:

GRUB Loading Stage 1.5

Error 17

and hangs.

I have reinstalled using the exact same process about 4 times and each time I am able to boot into Ubuntu the first time fresh off the install and then no more. When I reboot again, I get the same error. I realize there really are no clues in this story as to what is wrong, but the main thing I'm trying to fix, which I think might be a clue in itself, and is the single thing that has me pulling hair out with each reinstall is this: vim does not work. Each re-install I have had to use ed because when I type vim or vi for any file, or even with no arguments I get this error message:

E558: Terminal entry not found in terminfo
'bterm' not known. Available builtin terminals are:
builtin_riscos
builtin_amiga
builtin_beos-ansi
builtin_ansi
builtin_pcansi
builtin_win32
builtin_vt320
builtin_vt52
builtin_xterm
builtin_iris_ansi
builtin_debug
builtin_dumb
defaulting to 'ansi'

This screen appears for one second, and then the file I was attempting to open in VIM opens, except I cannot move the cursor or do any commands except, of course the exit w/o saving command. Hopefully this is a clue, and any help whatsoever is appreciated! Thanks in advance!

---

### Post by rebelfallen on 2006-07-12
DAPPER nightmare :(
Okay so when I get GRUB on my USB device loaded up (1st in bios boot) I e my kernel. I get to kernel line and press e again. root=/dev/sda1
Right well it doesn't work, it won't mount and it goes to busybox. 

I change that /dev/sda1 to 0,1,2,3,4,5 and none work. For some reason it doesn't read any partitions.

Here's the WHACKY part.
At home on my machine I run Fedora Core 5. I simply change my bios and the external boots perfectly. 
I am at work, and using WindowsXP and the external will not boot. Maybe Windows has something to do with it?

---

### Post by rebelfallen on 2006-07-12
Okay, no worries. I figured out that this machine is labelling the drive differently. /dev/sda = /dev/sdb

So I can boot into Ubuntu now. However.... GDM won't load!!!
I guess the hardware isn't configured right so it goes whacky and sends me to command line. X = warped.

Any suggestions?

---

### Post by niksonuk on 2006-07-26
Great How to.

I had just finished setting up 5.10 when I stumbled on to the Ubuntu web site and discovered a much easier method.

Basically download the 6.06 Dapper alternative install cd iso from the site.

Make a cd.

Remove the internal hd from your pc, connect your usb HD to the pc and boot from the CD and run the install.

This will automatically install the grub loader on the USB HD. 

Once the install has finished set your bios to boot from the USB HD first and away you go :D 

Had a slight glitch when I swapped machines the HD was not recognised but this was a BIO setting on the new PC (basically legacy USB support had to be activated in the BIOS).

Hope this helps :-)

Off to test my Pen drive now :-)

---

### Post by shoggoth on 2006-07-26
hello.

i'm following the directions from the first post and everything was just like you instructed but on Step 4 when you leave the cd in the drive after installing everything including grub to the external usb hard drive what are you then booting from on the reboot?

i reboot and while my computer is checking memory i press f11 to choose what to boot from. if i choose the usb hard drive it instead directs me to a boot windows xp normally screen. if i choose the cd do i tell it to begin a rescue?

im using the alternative install of dapper drake.

thanks for any help.

---

### Post by niksonuk on 2006-07-26
Once dapper has installed on the USB hard drive you need to be booting from the USB Hard Drive.

As your PC booted to windows I'm guessing that it has windows on the PC hard drive.

It might be easier if you disable the boot options for all other devices except the usb HD.

I know with the second and 3rd PCs I tested my drive on I had to turn on legacy USB support in one of the advanced bios options before the PC would boot.

I can't remember where the settings were in my bios but I wil look for you at work tomorrow.

---

### Post by Zgrund on 2006-08-05
Absolutely fantastic guide.=D>  I used it to install Dapper on my external drive with no problems encountered whatsoever. The only thing to nag about is the lengthy time needed for GRUB to boot linux. It takes quite longer than "MS Door$" which makes me avoid it when I'm in a hurry. Isn't there a way to speed the process up? An answer would be very appreciated. Even a "Not in a million years" is better than ignorance, so thanks in advance to anyone who spares some of his time to help a first time Linux user.

P.S:I searched with queries "long" and "time" in this thread for an answer already to no avail.(Just a simmiliar question left unanswered.)Apologies if I missed anything.

---

### Post by nolongerlivecd on 2006-08-05
I don't know about you, but when I did it, I did not face any time problems, mainly because it takes only ~30-40 seconds to fully boot for me.

---

### Post by raintheory on 2006-08-05
Thanks for the tips, however I am stuck as well...

Installed everything fine, but when I boot from the external USB it gets to a screen that just says GRUB with a flashing cursor...  I can't type or do anything at this point, and the system never goes anywhere from here...

Any suggestions?  I'm trying to get Dapper installed on an external drive for use with my laptop.  

Let me know if there is any information I can post that might help.  I've double-checked all of the relevant info, and have gone through the full installation 4 times now from scratch, each time I'm stuck with the same thing.

Thanks in advance!

-Aaron

---

### Post by nolongerlivecd on 2006-08-05
Does it actually say loading GRUB 1.5? If so, you may need to edit your /boot/grub/menu.lst

---

### Post by raintheory on 2006-08-06
> **nolongerlivecd said:**
> Does it actually say loading GRUB 1.5? If so, you may need to edit your /boot/grub/menu.lst

Nope, just says "GRUB".  Nothing else, no "loading" or "1.5"...

-a

---

### Post by insub2 on 2006-08-08
coulda' got that* externaldrive cheaper on newegg
[http://www.newegg.com/Product/Product.asp?Item=N82E16822154406]("http://www.newegg.com/Product/Product.asp?Item=N82E16822154406")


*that: this may be a different one...i don't know.  but it IS cheaper.

---

### Post by sandor.dornbush on 2006-08-24
I would like to follow these instructions on a machine with no cd drive.  I have gotten the network install of ubuntu started.  However I have not been able to resize a partition that I am not willing to format.  So can I start the network install as outlined in:
[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

Then when the istall chooses a disk to install choose the usb drive.  I have a different Kubuntu machine that I can use to modify the usb drive.  Anybody know if I can sort of do this:
1. Start the network install.
2. Install onto usb drive.
3. Shutdown.
4. Modify usb drive with other kubuntu machine.
5. Continue install on original machine.

Many thanks

---

### Post by one_man_down on 2006-08-27
Just got hibernation working on my usb install!!!

had to edit /etc/acpi/prepare.sh and /usr/default/acpi-support in order to get it working.

here's how i got it done.

open /etc/acpi/prepare.sh in a text editor.

find the line that says 

[COLOR="Sienna"]# Now do something similar for USB[/COLOR]

coment out the lines below it like this

[COLOR="Sienna"]# Now do something similar for USB
#for x in /sys/class/usb_host/*; do
#    if [ -e $x/device/driver ]
#	then
	MODULES="$MODULES $(basename $(readlink $x/device/driver) | tr [:upper:] [:lower:])"
#    fi
#done[/COLOR]

close the file, saving changes.


open /usr/default/acpi-support in a text editor.

look for 

[COLOR="Sienna"]
MODULES_WHITELIST=""[/COLOR]

change that to


[COLOR="Sienna"]
MODULES_WHITELIST="usbcore ehci-hcd uhci-hcd usb-storage usbhid scsi_mod sd_mod"[/COLOR]

close the file, saving changes

restart ubuntu, and your hibernation should work.

hope this helps!

---

### Post by gdumont on 2006-08-29
> **tertullian01 said:**
> I went all of the way through the tutorial and had little to no troubles.  I didn't see any error message and everything happened as explained.  However, after the 12th step I pull out the cd and let it reboot.  It gets to a black screen with a blinking cursor.  It waits there for 5-10 seconds and then continues to boot from the hard drive.  If I don't plug in the external hard drive there is no black screen with blinking cursor.  So it seems to find the hard drive and think about booting from it.  But for whatever reason it never does.  Any thoughts? 

I installed Drapper Drake 6.06 on my Acomdata Photon 80 Gb USB drive and Iget exactly the same problem. Whenever I try to boot from the USB drive, the machine waits for few seconds then boots the CD if there's one in the drive or boots Windows. 

So I tried to do what was mentionned in DraBuGo's post to```

``` configure USB properly but it didn't help. Anyway, someone mentionned that it wasn't necessary anymore in Drapper Drake. 

So I said to myself, that it has to be grub that isn't configured correctly . But the menu.lst had already the line
```
root            (hd0,0)
```
I tried to change it to (hd0,1) but it didn't work. However, I am able to get in graphical mode by following DraBuGo's post
```

mount -tproc proc /target/proc
chroot /target
su

```
and then 
```

startx

```
Any ideas how I could fix this issue? I don't want to have to go through the rescue process every single time I wan't to but in ubuntu.

Thanks in advance

---

### Post by CELI-Nux on 2006-08-30
Hi there,

How about sharing your new FSTAB and MTAB for comparison? I'm trying to share some of my internal folders (from some of my internal drives) from your configuration without any great success (everything seems to belongs to "root").

Regards.

**** FSTAB ****

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
#/dev/sda3      /media/CELI-NUX vfat    defautls        0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
#
# HDA definition for COMPAQ nc8000
#
/dev/hda1       /media/winxp    vfat    defaults        0       0
/dev/hda5       /media/dos      vfat    defaults        0       0
/dev/hda6       /media/dos2     vfat    defaults        0       0

**** MTAB ****

/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
/dev/hda1 /media/winxp vfat rw 0 0
/dev/hda5 /media/dos vfat rw 0 0
/dev/hda6 /media/dos2 vfat rw 0 0
/dev/sda3 /media/CELI-NUX vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

---

### Post by werdnav on 2006-08-30
Can anyone help with the following: Re: ALERT! /dev/sda does not exist.
Follow Alice and the Rabbit to 
[http://ubuntuforums.org/showthread.php?t=91186&highlight=usb+hdd+install](http://ubuntuforums.org/showthread.php?t=91186&highlight=usb+hdd+install)

---

### Post by forrie on 2006-09-05
Great tutorial, I have Breezy running on my 5gig usb drive :) 

How would I go about making the usb drive "Live", so I could use it on any computer I choose and not just the pc I installed it on?

---

### Post by willersj on 2006-09-06
Are the steps from 4) onward the same with Dapper?
Thanks.

---

### Post by superprad on 2006-09-10
> **moonlord said:**
> you could resize the partition of your external drive with partition magic and add one ext3 partition for ubuntu and one swap partition. then you won't have
to format the drive at all

Hi: I'm having a similar issue. I have a 250G external HDD and I formated about 60G for installing ubuntu and some swap. For some reason it was'nt able to create ext3 filesystem..it was erroring. So i created ext2 and linux swap(i assume this should still be ok to install ubuntu). 


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7600    61046968+  83  Linux
/dev/sda2            7601        7858     2072385   82  Linux swap / Solaris

Now when i reach the partitioning phase in the installer. I choose 
- manually edit the partition table.
- then i select /dev/sda and it shows the above and another line with free space(which i'm planning to format later for tons of data i need for storage).
- at this point it came to a next page where 

there is a table for pointing the /dev/'s to different mounts

which one do I point to as root partition at this point? i mean ('/') . At the bottom it says it needs atleadt 2G or something. 

By default /dev/sda1(60G) is pointing to some /media/usbdrive or something and /dev/sda2 is pointing to 'swap' and '/' is pointed from /dev/hda1(which is the boot partition for my internal. 

Should I continue with defaults or what do i have to do now?
oh and I'm running drapper..

any help is greatly appreciated asap.

Thanks much.

---

### Post by superprad on 2006-09-11
anyone? can anyone help me with my problem stated in the above post? how do i continue the install process without formatting the already formatted sda..its slightly confusing when the defaults say '/' is mounted to/dev/hda1.. if i continue will it effect my current grub on my internal.

---

### Post by the_duce on 2006-09-13
Hi, I tried this, but I couldn't get this to work. Ok on the Grub menu.lst I have everything right, but it doesn't work. The Warning Says dropping the Shell or something like that. P.S I'm using Western Digital External HD.

---

### Post by river2884 on 2006-09-23
everything worked, but password won't take.  What is password? Please?

---

### Post by mullur2358 on 2006-09-25
Thanks to your HowTo, I got Dapper installed on my Western Digital USB drive. As someone before me said, Steps 7-10 are not needed if you are installing Dapper, as it claims to have support for installation on USB drives. So you only need to modify the grub menu.lst file before the first boot.

This seems to work only with the text install mode of the "Alternate Installation" CD of Dapper.

I use a IBM Thinkpad T43.

---

### Post by MPEGON on 2006-09-28
Brilliant post.

thanks for the help

mp:D

---

### Post by MousePotato on 2006-09-28
Hi there,

I've had some success installing Dapper to an external drive but the method I used has left me with a problem. I wanted to be sure that nothing would happen to the laptop, which is my work laptop and can't be messed with, so I removed the hard drive during the install. The installer installed to the external fine, and without the internal drive it boots and work perfectly. However, if I put the internal drive back in then the number of the drive is altered and although grub finds the kernel, root does not mount. By altering the 'device.map' and 'menu.lst' files (sda1 changed to sdb1) in the Grub folder I have got root to mount, however the rest of the file system does not mount. Does anyone know a way to repair the file system? 

Many thanks if you can help me. I'm a newbie with linux but I'm happy using the terminal if guided.

Cheers.

---

### Post by MousePotato on 2006-09-29
I've managed to sort my problem by editing the /etc/fstab file. Seems to be the file that tells the installation where to look for things.

So, an external hard drive install with no risk to your main hard drive can be achieved thus:

1. Download and burn an ubuntu installation cd
2. Power down
3. Detach your main hard drive
3. Power up - press F12/F2 whatever to enter bios settings
4. Switch boot order to cd/usb/internal drive
5. Put your Ubuntu cd in
6. Boot
7. Do the install
8. Power down - leave the cd in
9. Put your main drive back in
10. Reboot from the live cd
11. Launch a terminal
12. sudo nautilus
13. Edit boot/grub/device.map and boot/grub/menu.lst replacing all sda(s)  with sdb(s) (or whatever your external hard drive is, you can use System/Administration/Disks to check this)
14. Edit /etc/fstab in the same way
15. Save and reboot without the live cd

Should be working nicely.

---

### Post by river2884 on 2006-10-04
figured out my password problem, I was on beer when I configured the external drive.
booted to rescue, typed "ls /home", it told me my misspelled user name.  Then password worked.

Duh.

---

### Post by b.treu on 2006-10-14
You don't need to go through all of this.[-X  You can do the install SIMPLY and completely through the GUI. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.\\:D/ 

Best to all!

---

### Post by aroland on 2006-10-18
hello all,
I am getting the  "ALERT! /dev/sda1 does not exist" error.  I have read ALL the posts and it still happens.  My ubuntu desktop mounts the drive and see's the install and gparted see's the partitions.

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

and thats it.:evil: 

Thanks for reading my post and any help would be great.  

Adam

---

### Post by pudland on 2006-10-21
Lacie 80GB USB HD w/ pavilion ze5170 laptop

I junked brezzy install and tried dapper alternate install..... i selected oem install and it installed with-out a hitch.

---

### Post by zmat on 2006-10-27
just like to add to this very good thread.

I installed ubuntu edgy successfully on my 320gb external hdd.

Basically my external hdd is partitioned as follows:

primary -> /dev/sdb1 - ntfs (just some stuff from windows)

logical -> /dev/sdb5 - swap
           /dev/sdb6 - ext3 (mounted "/")

Install went perfect but i stuffed up the grub install, i installed it to the ext3 partition instead of the external hdd MBR! however i also remembered making the ext3 partition flagged "boot", so i guess that saved me... either way when i rebooted it went into grub as normal and the only thing i had to do was change "root(1,5)" to "root(0,5)" and it loaded perfectly.

I remember earlier in this thread someone talked about changing "groot(1,5)" to "groot(0,0)" or something but i never did that and it still booted fine.

And it didn't touch my internal hdd and the installed windows xp which is great! If i wanted to boot to windows xp i'd just turn off my external hdd when starting up my laptop, so that the bios would bypass it.

Anyway, hope that helps someone wanting to do something similar :)

---

### Post by anders.ostling on 2006-10-28
Good morning all Ubuntu'ers out there.

I have managed to install 6.10 on an external 60G usb disk, but I still have a boot problem. Right now I am running the installer CD, and here is the disk layout (internal 100G SATA disk, external 60G usb disk). Ubuntu is installed w/o any problems to the 60G disk, and I have exec'ed the "mkinitramfs" trick to load usb disk drivers according to the HOWTO that started this thread. So booting seems to work, I select USB boot from the BIOS boot menu, I get the Grub menu and booting starts. I removed the "quiet" option and I could see that the kernel detected the USB disk as 

sda1 sda2 sda3 <sda5> which is correct since the kernel treats the external disk as the first one. This is also what I have in the grub config (see below)

I little later on the kernel dropped me to a busybox shell complaining that sdb5 does not exist, which is true. But why on earth did the kernel look for sdb5 suddenly? 

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14       12161    97578810    7  HPFS/NTFS

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      104391   83  Linux
/dev/sdb2              14         136      987997+  82  Linux swap / Solaris
/dev/sdb3             137        1110     7823655    5  Extended
/dev/sdb5             137        1110     7823623+  83  Linux

The relevant part of my grub menu.lst looks like this. Note that the initrd is the one that I created after the installation (contains the usb disk drivers)

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic-usb
quiet
savedefault
boot

And the device.map has these lines

root@ubuntu:/boot/grub# cat /boot/grub/device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb

Any clues? It would be great to be able to have my 2.5" disk with a full linux in my back pocket :)

Later
Anders

---

### Post by shakyone on 2006-10-29
b.treu you are exactly correct, this is the easiest method.  One change though, at the last step before it executes the installation procedure, if gives a summary.  In there is a button for install GRUB to (hd0).  Press this button and replace the text with

/dev/sda

and it works like a charm.

If you want the quick jump to the method posted by b.treu

[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by anders.ostling on 2006-10-29
> **anders.ostling said:**
> 

sda1 sda2 sda3 <sda5> which is correct since the kernel treats the external disk as the first one. This is also what I have in the grub config (see below)


Let me answer this myself. I changed boot order in BIOS to try USB before the internal drive, and that did the trick! At the same time, device names changed from sda to sdb, so I just had to modify the grub menu.lst file.

Anyone care to explain why the kernel changes to sdb when the drive is first in the list, and sda when it's second. Should it not be the other way around to be logical?

---

### Post by oryaaaaa on 2006-10-31
I did success ubuntu6.10 Japanese DesktopCD Edition.

HGST&#12288;HTS541040G9AT00 5400rpm ATA/IDE
LANTEC NexStar-3 (USB Interface, IDE to USB2.0)
PC nForce430 USB2.0 enable
AMD Athlon64 X2 2.6GHz
PC3200 2GB

dmesg & fdisk

/dev/sdc 40GB
partition table ms-dos
1 2GB ext2 /boot
2 2GB linux-swap 
3 20GB ext2 /

Last Installation Questions, Grub?
no input (hd0), you have to input sdc1 (/dev/sdc1)

Caution (hd0)
If your NTFS RAID is /dev/sda, Run install Grub rewrite /dev/sda.
you cant WindowsXP FIXMBR, and RAID CRUSH.

mount /dev/sdc1 /mnt (/boot)
edit menu.lst & device.map

reboot
once remove USB-cabel, and connect USB-cable (HDD OFF/ON)

Ubunto Orange Display... bar stop (HDD LED Flash) (*1
once remove USB-cabel, and connect USB-cable (HDD OFF/ON)

launch ubuntu6.10

I have one question.
How to solve (*1 problems, Please teach me.:confused: 

Thanks.

---

### Post by anders.ostling on 2006-10-31
In GRUB, edit the boot command and remove the last 2 options (quiet and something more). Then boot and you will se exactly where the boot stops

---

### Post by noktekniq on 2006-11-03
thanks for this. it help me install ubuntu on my external drive without going through that rough installation in the first page. i appreciate it. now i can test ubuntu like crazy.

got erro15

---

### Post by oryaaaaa on 2006-11-04
Thanks, its kernel process.

dmesg Logs (ubuntu forum japan)
[URL="http://forum.ubuntulinux.jp/viewtopic.php?id=13"]http://forum.ubuntulinux.jp/viewtopic.php?id=13
[/URL]

I write installation Guide
[URL="http://www.purebasic.fr/english/viewtopic.php?p=169048"]PureBasic :: Linux trial environment Guide (USB-HDD)
[/URL](Links free)

---

### Post by carrie.peary on 2006-11-04
It won't changed my root directory, any ideas why?

I found the right disc, and was able to get a terminal up, I think. I typed in mount -tproc proc /target/proc and that comes up with a list of what mount is, fine by me. Then I type chroot /target and it says that it can't. 

Another question too though, I might be doing something wrong....I hite "Rescue from damaged disk" and clicked a mount point. THen it asked about Rescue Configuration options, I choose Open Shell on Discblah which brought up a blue window with a whiteish line at the bottom..clicking Ctrl-Alt-F2 before this only caused it to bring up a black/white window.

Which do I want? And might all this stop it from working? Thanks!

---

### Post by Sir Action on 2006-11-06
> So,yes,users of this method can update to dapper,just click on keep to keep your old mkinintramfs file when prompted.

Well I tried to upgrade directly to Edgy (using apt-get) and it's giving me troubles. there is a conflict between volumeid and udev and now the Package Manager reports initramfs-tools as broken.

how can I put it "on hold"?

---

### Post by wsouders on 2006-11-09
> **DaBruGo said:**
> **[COLOR=red]Newsflash[/COLOR]** ... [COLOR=seagreen]UPGRADING from a BREEZY USB install to DAPPER is possible[/COLOR] !!!
( Kudos to "Killeroid" for sharing his success in [this post]("http://www.ubuntuforums.org/showpost.php?p=971692&postcount=383"). )
 
 
Hi Folks,
 
Since my first post on this topic, I have learned quite a bunch about the UBUNTU install process ... and managed to successfully load UBUNTU a number of times on my external USB drive. (Call me crazy, but I wanted to run the install a few times to make sure that what I was doing would work every time.)
 
I would like to share my updated outline with others who may also be struggling with this process.
 
**BACKGROUND**: I have an internal hard drive (western digital) already in my system with Windows XP Pro installed (which shows up initially as drive HDA in the UBUNTU partitioning phase of the install). My external USB drive is a [Seagate 40GB Portable External Hard Drive]("http://www.walmart.com/catalog/product.do?product_id=3910242") that was purchased at Walmart for around $120
 
**REQUIREMENTS**: Make sure you have your bios set to boot the CDROM first and then the USB device, or you will have problems down in step 4. (Kudos to "joess" for pointing out my omission!)
 
*pre-install tip*: If you feel comfortable performing one of the suggestions in [post #141]("http://www.ubuntuforums.org/showpost.php?p=669047&postcount=141") then it should make the installation to the external drive (especially tip 2) run smoother. (Kudos to "Sephatine" for suggesting this.)
 
**IMPORTANT**: Don't forget that Linux is case sensitive on everything, including file and directory names. (There is a difference between an uppercase and a lowercase letter.) *Example*: According to Linux, a file named "DaBruGo" and a file named "dabrugo" are considered two completely different files.
 
 
 
**Here is what I do to successfully load UBUNTU v5.10 on my EXTERNAL USB DRIVE ...**
 
 
**( STEP 1 )** Instead of using "expert" mode to install, I just hit enter to start the install process (using the install CD ... NOT the live CD).
 
*INSTALL NOTE*: The installation process will ask you for some information when it starts up ...
 
first it will ask for your language,
then your (language) location,
then your keyboard type,
then it will detect your cdrom(s),
then it will attempt to detect your network configuration,
then it will ask you to give your PC a name (hostname),
then it detects hardware and starts up the partition phase of the install.
 
*INSTALL NOTE*: When you get to STEP 2 (the partition phase), there is a simple way to determine how the install program assigns device names to your hard drive(s). Before starting any partitioning activity in STEP 2, choose the GO BACK option in the lower left corner of this screen and then choose EXECUTE A SHELL farther down in the Ubuntu installer menu that appears. Choose CONTINUE at the next prompt. In the shell window that appears, type in fdisk -l (that is FDISK -L in all lowercase). This will give you a list of all the storage devices the installer program sees. Make a note of the device names (/dev/hd? or /dev/sd?) and then type in exit to return to the partition phase (STEP 2) of the install. (Kudos to "RyanGT" for suggesting this in post #257.)
 
**( STEP 2 )** During the partitioning phase, I let the install program format my external USB drive. (I believe UBUNTU calls this a guided partitioning ... which sets up an ext2 or ext3 partition and a swap partition for you.)
 
*INSTALL NOTE*: Look for the line during the partitioning phase that might say ... erase entire disk SCSI (0,0,0) (sda). Be careful here as some people have had problems when choosing any partitioning options that include the text "and use LVM" (Kudos to "brucetan" for sharing this in post #268.)
 
Feel like learning about LVM anyway? Check this [link]("http://www.ubuntuforums.org/showthread.php?t=141900") out. (Kudos to "SD-Plissken" for sharing this info.)
 
*BE VERY CAREFUL* on these screens to choose the correct SDA drive and NOT an HDA drive or you may unintentionally format another drive in your system. There is no undo button for this!
 
Once again ... BE 100% SURE OF THE DRIVE YOU WANT TO FORMAT!
 
**( STEP 3 )** When the install gets to loading the GRUB bootloader ... DO NOT LET IT LOAD TO ANY OTHER DRIVE BUT THE EXTERNAL USB drive we are working with here.
 
The install program will ask to load GRUB to the master boot record (MBR) of your internal hard drive (HDA). Say NO to this, and on the next screen, type in the correct path to the SDA (external USB) drive where we want to install the GRUB bootloader.
(Mine was /dev/sda [NOT sda1] ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: I loaded GRUB to sda (the bootsector of the external drive) and NOT to sda1 (which would be the first partition on the external drive). 
 
*INSTALL NOTE*: at this point, the install program loads some stuff and ejects the CD ... wanting you to do a reboot.
 
**( STEP 4 )** BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode) ( Review REQUIREMENTS at the beginning of this guide! )
 
Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.
 
**( STEP 5 )** When the system comes back up it will ask for a partition to mount. Pick the correct mount point for your external drive from the list.
(Mine was mount /dev/discs/disc1/part1 ... but yours may be different depending on the number and/or types of drives in your system)
 
*COMMENT*: /dev/discs mount points start with disc0 (with 0 meaning the first drive in a system). So, my mount point of /dev/discs/disc1/part1 was really the second disk [disc1] (the sda drive we are working with) and the first partition [part1] on that disk. 
 
**( STEP 6 )** When it comes up to a terminal window (with RESCUE MODE in the upper left corner) and just sits there, hold down Ctrl-Alt-F2 to open another terminal window for us to do our edits in.
 
**( STEP 7 )** Type in these lines before we start editing out files ...
 
mount -tproc proc /target/proc <enter>
chroot /target <enter>
su <enter>
 
*INSTALL NOTE*: I used vim to edit the files. (There is a great [vim cheatsheet]("http://www.tjl2.com/sysadmin/vim_cheatsheet.pdf") in pdf format available from "TimL".) It is weird to use at first until you learn what a few keys do in it. The INSERT key allows you to actually enter text where you place the cursor ... The ESC key takes you out of INSERT mode ... And hitting : x <enter> saves the file and exits out of vim. (IMPORTANT TIP ... that's a colon and a lowercase x with NO SPACE between the colon and the x) 
 
**( STEP 8 )** Run vim to edit the modules file to make sure USB support is added/loaded during UBUNTU startup ...
 
vim /etc/mkinitramfs/modules <enter>
 
Right below the last line of text, enter these lines ...
 
ehci-hcd
usb-storage
scsi_mod
sd_mod
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Some PCs may need a more comprehensive list added here. Please take a look at [post #181]("http://ubuntuforums.org/showpost.php?p=705797&postcount=181") or [post #406]("http://www.ubuntuforums.org/showpost.php?p=1100888&postcount=406") if you are having startup issues after these edits. (Kudos to "brotorious" for his efforts on this, and to "Jonathan.Martin" for posting his successful resolution to the problem as well.)
 
**( STEP 9 )** Run vim to edit the initramfs.conf file to make sure enough time elapses for USB support to load before UBUNTU gets running ...
 
vim /etc/mkinitramfs/initramfs.conf
 
At the very top of this file, add this line which tells UBUNTU to pause for 12 seconds before starting up ...
 
WAIT=12 (in all caps here, not sure if necessary though)
 
Be sure to save the file changes (using : x)
 
*INSTALL NOTE*: Editing these two files loads the necessary commands to get USB support going so UBUNTU will recognize the external USB drive. But we still need to recompile (or recreate) the initrd.img that UBUNTU uses at startup ... so that these edits actually work.
 
**( STEP 10 )** Recompile (recreate) the initrd.img file to include USB support from these edited files ...
 
mkinitramfs -o /boot/initrd.img-2.6.12-9-386 /lib/modules/2.6.12-9-386
 
*INSTALL NOTE*: When you are done with the previous step #9 (and before performing this step), you can run the "ls /lib/modules" command (without the quote marks) from a terminal window to see what kernel version number you should use for this install step. They may be using a kernel version higher than 2.6.12-9-386 that was available when I originally created this help guide. (Kudos to "Saxegaard" for bringing this to my attention in [post #235.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=754862&postcount=235"))
 
**( STEP 11 )** Edit the GRUB bootloader menu file to correct a small error that looks at the wrong drive to boot from ...
 
vim /boot/grub/menu.lst
 
Navigate down this file until you get to a section where there is a menu list (not commented out ... no #s) that has Ubuntu mentioned three times (and possibly an area mentioning Windows XP down below it, if you have XP installed on an internal drive of yours).
 
There is a line in these three Ubuntu menu choices that has root listed on it and probably has (hd1,0) to the right of it. We need to change this to (hd0,0) on all three of these menu choices. Why? Because according to GRUB, the external USB drive will be our first drive (hd0,0) and not our second drive (hd1,0) because we loaded GRUB on it's bootsector. 
 
*INSTALL NOTE*: You will also want to change a "# groot" line in a section of your menu.lst file that may look something like this ...
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) <<< CHANGE THIS LINE TO READ # groot=(hd0,0)
(Kudos to "archis" for his excellent documentation of this farther down in [post #227.]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=749354&postcount=227"))
 
*INSTALL NOTE*: You may want to change the root line for the Windows XP section in this file to (hd1,0) just in case you have XP loaded on an internal drive and want the option to boot into XP from the GRUB menu. (See post #2 for more info.) You may have to edit this section whenever you update your kernel version. If you have problems pulling up XP after a kernel update, check this section of your menu.lst file to see if you need to edit it again.
 
Be sure to save the file changes (using : x)
 
*COMMENT*: Feel more comfortable editing this file in Windows? See [post #171]("http://ubuntuforums.org/showpost.php?p=692413&postcount=171") for a program that will let you edit files on linux partitions from within Windows. (Kudos to "mickola" for the suggestion.)
 
**( STEP 12 )** Exit out of this terminal window (keep typing exit <enter> until the screen actually says to press enter). Hold down Ctrl-Alt-F1 to get back to the RESCUE MODE terminal window and type exit<enter> to reboot the system.
 
BE 100% SURE TO GET THE CD OUT OF THE DRIVE BEFORE UBUNTU RESTARTS
 
**( STEP 13 )** After rebooting, UBUNTU continues to run it's install process and comes to the desktop. Use the username and password you setup earlier in the install process to get into UBUNTU
 
 
That's the process I've successfully used to install UBUNTU v5.10 on an external USB drive. I hope this helps anyone whose been wrestling with this process. Let me know if it works out for you.
 
DAVE
 
 
 
**OTHER PROBLEMS AND POTENTIAL FIXES** ...
 
* Booting Ubuntu from Windows XP without loading GRUB to the MBR ...
[http://www.ubuntuforums.org/showthread.php?t=56723]("http://www.ubuntuforums.org/showthread.php?t=56723")
(Kudos to "celticmonkey" for documenting this.)
 
* Problems booting XP from an internal drive ...
[( message #2 )]("http://www.ubuntuforums.org/showpost.php?p=441318&postcount=2") + [( message #203 )]("http://ubuntuforums.org/showpost.php?p=723454&postcount=203")
 
* Problems starting UBUNTU after a kernel update using Ubuntu's automatic update app ...
[( message #112 )]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112") + [( message #161 )]("http://www.ubuntuforums.org/showpost.php?p=686867&postcount=161")
 
* Using Windows XP to format drives larger than 32GB AS FAT32 ...
[( message #188 )]("http://www.ubuntuforums.org/showpost.php?p=715722&postcount=188")
 
* Re-installing GRUB in a relatively painless manner ...
[( message #205 )]("http://ubuntuforums.org/showpost.php?p=723618&postcount=205") (Kudos to "RyanGT" for hunting this down.)
 
* Creating a bootable GRUB CD (sketchy details but seems to make sense) ...
[( message #207 )]("http://ubuntuforums.org/showpost.php?p=723735&postcount=207") + [http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html")
 
**REFERENCE MATERIALS** ...
 
* GRUB Manual (section 14.3 shows what error codes mean)
[http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")

i get to step 7 and can't get any farther, mount: mounting/proc on /target/proc failed: no such file or directory. maybe being a windows user i made a mistake. any help to get past this would be appreciated. thanks in advance.

---

### Post by yanqui on 2006-11-14
> **daibak said:**
> Some months back DaBruGo and this thread, in a very roundabout way, encouraged me to persist to break away from WinXP with an external FireWire 160GB disk drive. Even though I never succeeded in booting from the external drive as this thread explains so well for USB 2.0 drives I've been a happy dual-booter with Ubuntu 5.10 for the past two months, nowadays rarely booting Windows at all. Ubuntu is all most heavy users will ever need!

So how did I get there? Mercifully this 2002-purchase, HP Pavilion notebook PC came with a factory freebie: USB 1.1 Mitsumi floppy disk drive. The secret was to grab GAG in current version 4.5d and choose at boot which OS I want,  and I've never looked back.  After all the terror scenarios I tried and tested for two months I'll never consider installing a dual-boot scenario ever again without a GAG floppy or 'El Torito' CD at hand to circumvent the inescapable GRUB error messages you'll get when you first try to load Linux.

Here's a link to the free dual-boot [GAG]("http://www.majorgeeks.com/download2588.html") boot-loading manager I use, it's great!


Okay---I got it downloaded in a zip file.   When I open the zip file, I see a bunch of files but NOTHING that tells how to actually use it.  A lot on what it does, but nothing that says :step 1, double click on this file.

Little light on documentation.

---

### Post by dracule on 2006-11-14
I got to step 8 and now i am stuck.

I am trying to install edgy, but i have no idea were to go next.

I am guessing when step 4 says Rescue mode it means "rescue a broken system"
I then mounted the correct partition (in my case /dev/sdb1 (the same one that i wrote the mbr to)
But when i hit Ctrl-Alt-F2, and typed in the following:
mount -tproc proc /target/proc
chroot /target
su

all goes well

but when i type this in:

nano /etc/mkinitramfs/modules

it doesnt find the file...

so how do i do this?

---

### Post by MrGrey1 on 2006-12-09
WAIT or DELAY doesn't seem to make a difference. When I did this tutorial I kept getting stage 1.5 error 2. Tried all sorts of things. Eventually turned out that I had to change the boot order back so that cd booted second, hd/usb booted first and everything worked. Beat my brains out trying to figure out why this was so hopefully it will save others the trouble.

---

### Post by MrGrey1 on 2006-12-09
I had to change my boot order back to hd/usb boot first, cd second, before the install would complete. Kept getting grub boot error 2.

---

### Post by Bobtheknight on 2006-12-12
Dave, thanks for the guide

In my bios I have the option of booting from USB-FDD or USB-ZIP.  I tried both but none of them seem to work, they just boot right into my hard drive.

Also, in step 8 and 9 you said to edit the modlues and initramfs files.  They don't exist, in fact mkinitramfs didn't exist.  I had to create them to put the lines you want for them.  Is that a problem?

Thanks

---

### Post by bartgrefte on 2006-12-22
Hi!
i haven't read the intire topic yet, but i'd like some help choosing a external harddrive which i want to install ubuntu on...
The laptop i'm using is a toshiba satellite a100-683 wich can boot from usb if i'm not mistaking, dont know if it can boot from firewire.

---

### Post by infocomm on 2006-12-26
Great!

Following this guide, I have successfully loaded Ubuntu 6.0.6 on my USB drive (Buffalo 250GB).

My laptop do not support booting from USB, but there is no problem. I just have to create a grub bootable cd and boot my laptop from CD Drive, then load Ubuntu from USB drive at booting time.

In summary, to install Ubuntu on an external USB drive where your old BIOS do not support booting from USB, following the steps:

1. Boot your laptop with UbuntuLiveCD.
2. Install Ubuntu into your USB external hard disk (e.g. /dev/sdb1 for root file system / and /dev/sdb2 for swap). Remember to write grub into the master boot record (MBR) of USB drive.
3. Boot again with LiveCD. [Follow DaBruGo's guide]("http://ubuntuforums.org/showthread.php?t=80811") to create a new image file including some modules that support USB drive. (Remember that your USB drive will be mount somewhere in /media/usbdisk).
4. [Create a grub bootable cd]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html"). Please include the /boot/grub menu.lst file. When booting from CD, USB drive will be recognized as hd1, (hd0 for internal hard disk). Thus your menu.lst file will looks like that:

[SIZE="2"][SIZE="1"]
title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot
[/SIZE][/SIZE]
5. OK, now you can boot your lap top from cd to load Ubuntu from external USB drive, without modifying your internal hard disks.

Good luck,

---

### Post by samji on 2006-12-30
Sorry for the totally n00bish question, infocomm. But how do you specify where to install GRUB when installing from the install wizard?
I've tried installing with the wizard in Dapper and it always seems to fail - I tried Edgey and the system always crashes or the mouse just freezes.

I guess I'm saying did you just use the install wizard or the command line for this?

I kind of managed an install once, but GRUB was installed to the computer's MBR of the internal hard drive and although the system loaded - the mouse cursor was not responsive
even on several restarts. Do I need three partitions, one for the boot sector and one for the system and a swap of course on my external drive?

I have a Dell Inspiron C521 and have been trying to install to a 160GB Seagate external HDD (USB 2.0, 2MB Cache, 7200 RPM). Thanks in advance.

---

### Post by Shin_Gouki2501 on 2007-01-02
Hello there people of this thread!
Im quite new to Linux! over the chrismas days i tried installing ubuntu 6.10 on a USB-Harddisk...
But it didn't work :/

I know i "could" try to digg thourgh the above depicted guide but.. sure u could call me lazy but...
couldn't we adress this partly towards the ubuntu devs?
So now my questions are:

How much effort for the ubuntudevs would it be to implement a "STANDARD" Method to install ubuntu from the Live CD onto a USB Device?

Is there a Launchpad entry for this?(if so plz link)

Do u think its reasonable to get an USB install Ability right away?

thx for coming replays ;)

wbr Shin Gouki and a happy new year to every one :)

---

### Post by manthano on 2007-01-03
> **Killeroid said:**
> Dave/DaBruGo, I successfully updated to Dapper Beta 2 yesterday. During the update, I was asked whether I wanted my mkinitramfs file to be updated and I specified no and so retained all my settings without having to reconfigure ubuntu again.

So,yes,users of this method can update to dapper,just click on keep to keep your old mkinintramfs file when prompted.

I also successfully upgraded to Dapper using this method.  However, I as it was awhile ago that I initially installed Ubuntu, I had not seen the following install note.... 

> INSTALL NOTE: You will also want to change a "# groot" line in a section of your menu.lst file that may look something like this ...
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3) <<< CHANGE THIS LINE TO READ # groot=(hd0,0)
(Kudos to "archis" for his excellent documentation of this farther down in post #227.)

...or what was mentioned in [posts 227]("http://www.webdwelling.com/cgi-bin/nph-browse.pl/000110A/http/www.ubuntuforums.org/showpost.php?p=749354&postcount=227"), [112]("http://www.ubuntuforums.org/showpost.php?p=593793&postcount=112"), or [161]("http://www.ubuntuforums.org/showpost.php?p=686867&postcount=161") I had to do the steps there to get back in to change menu.lst.  Thanks for adding that information! Everything is working great now.

DaBruGo, perhaps you could add a note to see that information in with your note about upgrading at the top of your tutorial.  Thanks!

---

### Post by Moosey on 2007-01-04
Hi there! Just want to express my thanks at DaBruGo and everyone who has contributed to this thread. Following the tutorial posted by DaBruGo (albeit a few changes, seeing as I was using a newer kernel version) I was able to sucessfully install and run Xubuntu 6.10 on a Seagate USB Harddrive. After a bit of trouble it's now working like a charm but I couldn't have done it without all your ideas in this thread!

Thanks again!

-Moosey

---

### Post by Moosey on 2007-01-05
Ok, well it seems that not all is as well as I hoped. Despite being able to boot successfully into Xubuntu most of the time, sometimes it will just hang for about a minute at the splash screen and then throw up loads of I/O errors, including this one: "usb1-9, device not accepting address 3, error -110"

Normally a restart fixes it and I can boot into Xubuntu again, but just now I spent about 30 minutes restarting again and again to no avail before it finally booted again. I doubt that it's a hardware issue as when I'm in Windows, the NTFS partition on the hard-disk (also, I don't think the partition is corrupted either, as it DOES boot up fine occasionally), and also the boot loader runs off the disk without any problems. It's only when the Xubuntu splash screen comes out that problems start occurring. 

The thing that confuses me the most is the fact that only sometimes the error occurs and other times it works fine. I could understand it more if the error occurred all the time, but it seems to be happen completely at random. Any ideas as to what could be causing this? Naturally, I would like to have a system that actually loads reliably, so any help would be greatly appreciated.

On a somewhat related note, my USB wireless keyboard and mouse were not working when I first installed Xubuntu, but now for some strange and just as random reason as with the hard disk (I did not tinker with anything that could have affected it), they now both work...

Once again, thanks for any help you can give me,

-Moosey

EDIT: The hard drive in question is a Seagate 320GB External USB Hard Drive

Also, forgive me for double posting, but I felt it to be appropriate, considering that my last post was over a day ago, and this post has a different theme to the previous one. If I have somehow breached any rules of etiquette by doing so, I apologize.

---

### Post by stguitar@gmail.com on 2007-01-13
> **infocomm said:**
> Great!

Following this guide, I have successfully loaded Ubuntu 6.0.6 on my USB drive (Buffalo 250GB).

My laptop do not support booting from USB, but there is no problem. I just have to create a grub bootable cd and boot my laptop from CD Drive, then load Ubuntu from USB drive at booting time.

In summary, to install Ubuntu on an external USB drive where your old BIOS do not support booting from USB, following the steps:

1. Boot your laptop with UbuntuLiveCD.
2. Install Ubuntu into your USB external hard disk (e.g. /dev/sdb1 for root file system / and /dev/sdb2 for swap). Remember to write grub into the master boot record (MBR) of USB drive.
3. Boot again with LiveCD. [Follow DaBruGo's guide]("http://ubuntuforums.org/showthread.php?t=80811") to create a new image file including some modules that support USB drive. (Remember that your USB drive will be mount somewhere in /media/usbdisk).
4. [Create a grub bootable cd]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html"). Please include the /boot/grub menu.lst file. When booting from CD, USB drive will be recognized as hd1, (hd0 for internal hard disk). Thus your menu.lst file will looks like that:

[SIZE="2"][SIZE="1"]
title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
boot
[/SIZE][/SIZE]
5. OK, now you can boot your lap top from cd to load Ubuntu from external USB drive, without modifying your internal hard disks.

Good luck,

hello, when i try to do this i get 

root (hd0,0)
Filesystem type unknown, partition type 0x44
kernel /vmlinuz root=/dev/sda1 ro quiet splash

Error 17: Cannot mount selected partition

any ideas?

im booting this on an old gateway that does not have usb boot up stuff in the bios. i know the ubuntu(breezy) is installed and working as i can boot my desktop that has usb bootup bios ability just fine... i just need this on the laptop.

ultimately, my goal is to load this linux, from the external drive on my mac book pro. when i try i have to use rEFIt and i get stuck on the loading grub screen with no error, but just a blinking cursor.

i was hoping to use either the mac or the gateway for my laptop needs...

---

### Post by bradhawk08 on 2007-01-17
My friend and I are trying to install Ubuntu 5.10 on his brand new external USB 160 GB hard drive.  We've followed all of the steps in the tutorial.  We've used the extra script.  We've added the extra modules as described in previous posts.  When we try booting up into Ubuntu, the grub bootloader loads up and then splash screen shows up and says Loading Modules and says ok, but when it tries to mount the drive.  It gives the same error that's been described in other replies on this thread.  "ALERT: /dev/sda1 does not exist! Dropping to a shell"  


Any suggestions?

---

### Post by stguitar@gmail.com on 2007-01-17
i would check your GRUB command. when you get to the grub screen where you can pick what you are booting up, you can hit 'e' to edit the command.

if i remember, i saw this when i was playing around that and i think i had the wrong path for the hd0,0 or the sda1 thing... you can edit it, hit return, and hit 'b' to reboot with that command. you can edit until it works...

otherwise you can load up off a live cd, and manually edit the grub file as mentioned in the tutorial.

ofcourse, you would also need to know if it was infact sd1 that you installed ubuntu on and not something like sdb or something else...

---

### Post by bradhawk08 on 2007-01-17
So, we weren't able to make Ubuntu 5.10 load up onto the USB hard drive correctly, but we were able to, after making the partitions obviously with the 5.10 cd, install 6.06 onto the external hard drive and it works fine.  don't really understand why it works but it does.

---

### Post by ashwin_murali on 2007-01-29
Hi all guys,

First off... I'm a n00b in Linux.  Other than Vim and grep, i pretty much am not very heavily used to linux.  But yea, i've been working on linux for sometime now... And the doubt I have is as follows:

[LIST]
[*]I want to install Ubuntu 6.06 on my external USB HDD (Seagate 40GB IDE Disk).
[*]I dont want it tinkering with my windows XP installation in any way.  I'm a Symbian developer by profession, and sadly to say, Nokia doesnt give tools that run on linux... So, the need for windows...:D
[*]If my understanding of Dave's installation procedure is right:
Can I say that during boot, If i plug in my USB HDD, i get the boot menu (GRUB here) where I can choose Windows / Ubuntu... and If I dont plug in my USB drive during boot, the laptop silently loads up Windows XP???
[*]I'm going to install Ubuntu onto my USB HDD.  Is there going to be any, if at all, ANY effect on my internal HDD???
[/LIST]

Please clarify me on these points before I actually proceed with the setup / install.

---

### Post by craigwsee on 2007-02-03
A few things I learned from an Edgy (6.10) install on an external hard drive:

1. Go into System...Preferences...Removable Drives and Media and DISABLE 'Mount removable drives when hot plugged.'  Ubuntu installer will get an error if you don't do this, presumably because it will mount the drive mid-install.

2. Don't try to set up your partitions beforehand.  Doing this only caused an error for me.  Instead, use the 'Manually edit partition tables' option during the installation (if you don't want the whole drive to be formatted in ext3, for example)

I am going to have to use a GRUB cd to boot my USB because my BIOS does not allow it.  I will repost with anything I learn from that.

---

### Post by leobaby on 2007-02-10
Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.

---

### Post by Robert A. Morin on 2007-02-18
I was able to configure things correctly (I hope).  I just installed Ubuntu Dapper Drake on my Seagate 160 GB External HDD, and set the BIOS to load the Seagate drive first, before going to my internal drive, which has, sorry to say, Vista Ultimate installed on it.  However, Dapper Drake seems to make it easier to do this kind of dual-boot, if you set the installation to do the right thing.  I believe that I had the whole Ubuntu CD install on the external drive, and things worked out right.  I turned off my external HDD to see what happens, and it boots right into Windows, like it should.  However, when I reboot and turn on my external HDD, it SHOULD give me the GRUB menu, and should allow me the choice from the ESC menu.  Let's hope that I configured things correctly for this to happen.

---

### Post by Oen386 on 2007-02-26
I had so many errors.

[http://ubuntuforums.org/showpost.php?p=2212087&postcount=1](http://ubuntuforums.org/showpost.php?p=2212087&postcount=1)

---

### Post by scott_b on 2007-03-10
> **leobaby said:**
> Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.


leobaby, 

I have an acomodata 2.5" drive.  I seem to be able to get it to boot on some computers, but not others.  Do you know if that's a power issue?   Can you boot off your 2.5" disc on any computer that will boot a USB?

-scott

---

### Post by leobaby on 2007-03-10
I've had more than one of these external 2.5" drives and power was an issue with all of them. On the laptop I did this install, if I turn on the computer with the drive plugged in it will spin up but not boot or even get recognized by windows. I have a boot prompt on the internal drive, so I plug it in when I see that and  press ctl-alt-delete and then choose to boot from from the usb. Oddly enough I had the same issue with an external firewire 2.5" drive; and hear other complain about this usb problem too.

On my desktop I have usb in my monitor, keyboard and a hub. The drive will spin up in all three but not work.

> **scott_b said:**
> leobaby, 

I have an acomodata 2.5" drive.  I seem to be able to get it to boot on some computers, but not others.  Do you know if that's a power issue?   Can you boot off your 2.5" disc on any computer that will boot a USB?

-scott

---

### Post by degsyw on 2007-03-12
> **leobaby said:**
> Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 


worked for me, though got grub confusionalong with all the others! caught me out as well until i remembered and woke just in time to stop it from installing to internal hd  :)

thx

d

---

### Post by jasjason on 2007-03-21
hi can anyone help as i try to install drapper into my 20gb external harddisk during the installation i encounter error. The error message is unable to configure Openssh. Sometimes when try to do reinstallation i always get different error may i know what is happen and i have also follow the instruction too. pls advise me. thanks in advance

---

### Post by ocho on 2007-04-04
Thanks a lot for the tutorial. Is it possible to format the drive as fat32 instead of ext3? I would like to be able to still use the data in Windows and I don't want to have more than one partition holding data.

---

### Post by gordon1992 on 2007-04-07
followed instructions perfectly for 5.10

but on boot-up i get an error like tty job control turned off.

any ideas?

---

### Post by dfarce on 2007-04-08
How hard is it doing an instalation on an external drive compared to a normal installation? I am totally n00b to linux of any kind. Also, I want to keep pulling the drive from computer to computer, so would this be able to handle this? I've been told that I need a live USB.

---

### Post by m34joey on 2007-04-10
Wireless Everyone????????    How is it possible to configure wireless when ubuntu boots from an external drive?  Any help would be great.  I am running Ubuntu Edgy.

---

### Post by ninocass on 2007-04-20
Hey All

I think i have this nearly working, i can see the grub form my external blink up for a split second and then the grub on my internal drive takes over

any ideas?

Thanks

Nino

---

### Post by leobaby on 2007-04-20
during install it may think your external is drive is hd1, but when booting from it, ubuntu thinks the external is hd0.
Maybe you need to change the grub on external.

from [http://ubuntuforums.org/showthread.php?t=407212](http://ubuntuforums.org/showthread.php?t=407212)
    * After rebooting, I choose to boot from the external usb drive. Since I am booting from the drive it now appears as hd0 instead of hd1.
    * Grub loads, so it is booting off the correct drive, but Error 17: Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot
    * and success. Once at the desktop, terminal sudo gedit /boot/grub/menu.lst
      and copied the first group of options to the very top and did the same changing (hd1,0) to (hd0,0)


If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

---

### Post by luqsim on 2007-04-21
I did follow instructions perfectly. After the Install it worked for a while and then I turned off my computer. But on the 2. day I couldn't boot up. It shows me the following error message! Could somebody help me to figure out what the problem is? Thx
[IMG]http://luqsim.googlepages.com/Error.JPG[/IMG]

---

### Post by micfreedom on 2007-04-26
> **h0meb0y25 said:**
> Ok Guys, 

here is quick update .. 

I have installed ubuntu on my external USB hdd but from another system which supports booting from USB HDD.

Seems like the bios of the system on which I was connecting external usb hdd donest support booting from extrenal hdd. 

Is there a way to boot from external USB or external firewire device, even if system BIOS doesnt support that.

I have read this link "http://www-128.ibm.com/developerworks/linux/library/l-fireboot.html" but being a newbie could not understand the details mentioned there. 

If some has done this earlier please help.

thnx


Hi guys, 
I have WD My Book. I found first that windows XP would not recognize my devise. WD Digital has lots of support                          [http://support.wdc.com/](http://support.wdc.com/)
regarding their external drive. They have also a download program called Data Lifeguard Tools 11.2 for Windows. This program will make sure that your USB External drive is recognized by Windows AND you have the opetion between choosing the USB external hard drive *as you booting device* or simply as an external hard drive.
Caution, I have only noticed that you could choose this as a booting device, but i have not used this in this way, so i don't know whether this will invalidate any booting practice from your PC. But it may be interesting to explore WD as they produce reliable external hard drive.
Sorry, I am not a techie myself, but I struggled to have my USB external drive recognized and SEEN amongst the devices that I use and it is nice tohave problem resolved. I hope this helps.

---

### Post by leobaby on 2007-04-26
can you let it put grub on the internal drive during installation?

---

### Post by micfreedom on 2007-04-30
I had another problem with GRUB. When I reboot with the Linux rescue CD, it loads and reaches Grub. Then it says    Grub Error 21.
I had a look at [http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)    and found some answer to by pass this. I am grateful frothis answwer and i copy it here:
Re: GRUB error '21' problem *solved*

--------------------------------------------------------------------------------
From:  tom 
Subject:  Re: GRUB error '21' problem *solved* 
Date:  Thu, 27 Feb 2003 10:37:15 -0000 

--------------------------------------------------------------------------------

GRUB Error 21 problem solved 



(w00t)



thanks to David Balazic for pointing me in the right direction!

 

i changed the CMOS settings to detect the HD's in my system...

 

this is what i did:

 

entered Standard CMOS Setup

 

set the Primary Master to:

    Type = User,  Mode = LBA

by scrolling through the options

 

then set the Primary Slave to:

    Type = Auto, Mode = Auto

 

hope this helps someone in a similar predicament

 

cheers again to David

 

tom

 

~ everything was beautiful, and nothing ever hurt ~

 

[www.purpletemple.co.uk/forum](www.purpletemple.co.uk/forum)

Hope this haleps too.

---

### Post by micfreedom on 2007-04-30
I have WD External Drive 500 GB. 
I have by passed the Grub part, but now it takes ages to load. I have a balck screen which I don't dare do anything with!

---

### Post by kgriffin on 2007-05-01
Anyone done this with feisty?

---

### Post by Jeff van Hees on 2007-05-02
**Dear Ubuntu users,**

I follow the whole tutorial that the topic starter wrote, but I got a problem.

While the Ubuntu starts (loading screen), I see "Loading modules..." (No 'ok' at the end) and my external usb harddisk turns off and on again. Then there is a error that /dev/sda2 is not found.

> 
Booting 'Ubuntu 5.10'

root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vml... bla bla

...
...

Uncompressing Linux... Ok, booting the kernel.
Loadin, please wait...
Alert! /dev/sda2 does not exists. Dropping to a shell!

BusyBox v1.00-pre10 (debian.......
...
...

/bin/sh: can't access tty; job control turnet off
#_

What can I do to fix this?

Thanks a lot from the Netherlands!

Jeff

---

### Post by Jeff van Hees on 2007-05-03
Sorry for the early kick, but I just want to know it soon...

---

### Post by el_dorado on 2007-05-24
Just tried the above steps with Ubuntu Feisty Fawn ( 7.04)  alternate cd ( not LIVE CD ) , it worked liked a charm on my 40G seagate external usb drive. The installation was pretty smooth. 

Most of the steps you mentioned earlier still work 

(STEP 1-4)  Still the same  , i used the text based install .. everything is the same till you install grub to your usb drive and let it reboot in rescue mode . 

(STEP 5)  In rescue mode i was asked to choose the root partition to rescue ;  i was given the choices in the form of  

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sdb1
/dev/sdb2
/dev/sdb3 

Instead of anything like /dev/discs/disc1/part1  , so choose your root partition accordingly.

(STEP 6)  No Change  

(STEP 7) If you chose the  correct partition on STEP 5 you wont need to mount anything . The installer will mount the drive for you , all you need to do is su - to get a root shell prompt. 

(STEP 8 )  No Change , location modules file has changed to /etc/initramfs-tools/modules.

(STEP 9)  No Change , location of conf file has changed to /etc/initramfs-tools/initramfs.conf 

(STEP 10)  No change , just choose your version of initrd.img from /boot and the kernel in /lib/modules/ 

(STEP 11)  Edit the /boot/grub/menu.lst . Search for groot , change it to groot(hd0,0) .
Also just after the comment "End Default Options" change the root to (hd0,0) , repeat the same for rescue and memtest entries . Also change the entry for Windows incase you have a dual boot with windows , for this change root to (hd1,0) 

Finally do a reboot  , Make sure you have enabled boot from usb drive in the bios. 
Not much has changed except a few steps ever since this tutorial was written and  it has worked for me both time ( breezy & feisty ) ; it should work for everyone else too  :D. 

My Sincere thanks to the original writer of this tutorial

---

### Post by noobie123 on 2007-05-26
I had attempted to install feisty on bus powered 2.5" hdd but the install did not boot at all, probably due to insufficient power but on** using a powered usb hdd, the install works fine!**
 
> **leobaby said:**
> Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.

---

### Post by leobaby on 2007-05-26
I used a bus powered 2.5" drive as well and had two issues. First, the drive does not spin up unless plugged in after turning on the computer, sometimes requiring a reboot to avoid booting into windows. Second, the installer called the drive hd1 but when booting from it ubuntu thinks its running on hd0.

> **noobie123 said:**
> I had attempted to install feisty on bus powered 2.5" hdd but the install did not boot at all, probably due to insufficient power but on** using a powered usb hdd, the install works fine!**

---

### Post by Mrs Harris on 2007-05-27
Hey all,

Read through most of this but am still having no luck with this on my Sony Vaio Desktop RC-202 with a 320gb WD MyBook.

Firstly I tried as per the original instructions but I now find that although the "boot from USB" option is in my BIOS the Sony Vaios do not actually support this.  I then created a grub boot CD from the instructions in the link on page 48 of this thread.  I now have a really silly question (sorry for being a thicko but all this relatively new to me)... what do I do once I get to the GRUB prompt?

Thanks in advance,
Mrs H

---

### Post by ManojMistry on 2007-07-02
Well I tried installation process many times..line by line..Installation goes fine on my external WD 120 GB HD. It is during boot process it fails in grub 1.5 stage with error 2( first time it was error 5). I did partition as follow. "/ as /dev/sdb1" and "swap as /sdb2". My internal HD is recognised as sda. 

Will it help to install /boot on separate partion?

Can it be power problem to extrnal HD as i am using singal cable to USB device?

Please Help!

---

### Post by siblog on 2007-07-03
Successfully loaded Feisty Fawn (7.04) onto my WD 160GB with the directions from el_dorado and DaBruGo. I am still having a few issues with my laptop booting to my USB and grub correctly but I think a grub boot cd or Super Grub Disk ([http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)) might do the trick. Thanks guys! :D

---

### Post by siblog on 2007-07-03
> **ManojMistry said:**
> Well I tried installation process many times..line by line..Installation goes fine on my external WD 120 GB HD. It is during boot process it fails in grub 1.5 stage with error 2( first time it was error 5). I did partition as follow. "/ as /dev/sdb1" and "swap as /sdb2". My internal HD is recognised as sda. 

Will it help to install /boot on separate partion?

Can it be power problem to extrnal HD as i am using singal cable to USB device?

Please Help!

First off I am by no means a Linux-guru but since I just went through the install myself maybe I can help. What version of Ubuntu are you trying to install? Are you manually creating your partitions or using the "guided partitioning" technique? 

I don't think it is because of the single cable USB device.

The grub manual might help...
"2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 
5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign."

---

### Post by leobaby on 2007-07-04
It very well could be a power problem, or just as likely something else maybe grub.

My usb drive has a cable with a single usb connector that plugs into the drive and two usb that plug into the computer. One only carries power.

Even then, I have an issue where I have to plug in the drive after I turn on the computer, just like a few seconds after I power up the laptop.  You should be able to hear it not spinning though, if you listen close you might hear it just clicking or something.

I've had this issue on other computers and with firewire drives as well.

Good luck.

I will say this. Since I wrote my instruction post many pages back I have since dedicated a good bit of space on the internal drive, boot into ubuntu by default and haven't looked back. This version of ubuntu 7/4 is by far the best and most usable yet. I rarely boot windows on my laptop anymore. I did use a separate utility to shrink my windows partition first, then let ubuntu just use all available free space automatic. Take the plunge, you probably won't regret it.

---

### Post by Chronos6 on 2007-07-06
Hy!
I have a problem, and didnt found a soultion. I'm working with an old pc, and want to work with ubuntu, and have a 40gig external hdd. I tried to make a grub cd, but it did not recognise in time the hdd. the usb scsi etc. modules are loaded. Can anybody help??? If somebody could make a boot cd for me i would be grateful. sda1 is where is should be. 
I had problems with a tutorial, on the live cd the chroot woul not work. Any help will be appreiciated. Thanks, Bya

---

### Post by zenit123 on 2007-07-25
[QUOTE=el_dorado;2710934]Just tried the above steps with Ubuntu Feisty Fawn ( 7.04)  alternate cd ( not LIVE CD ) , it worked liked a charm on my 40G seagate external usb drive. The installation was pretty smooth. 


I have tried all the steps mentioned in your tutorial without luck. I am trying to boot Ubuntu 7.04 using a usb external hard drive (250GB) partitioned into 4 partitions (2 ext3 and 2 fat 32).

I have also changed the settings to boot from external removable drive but when I restart the computer, the bios checks the usb hard drive but does not boot. It continues to windows which is on the internal hard drive and is last in boot priority.

Anybody - any help. Should I try booting from a GRUB cd?

thanks ahead

---

### Post by zenit123 on 2007-07-27
> **zenit123 said:**
> [QUOTE=el_dorado;2710934]Just tried the above steps with Ubuntu Feisty Fawn ( 7.04)  alternate cd ( not LIVE CD ) , it worked liked a charm on my 40G seagate external usb drive. The installation was pretty smooth. 



Ok guys, I need your help to crack this. I have been working on this further and here is the scenario

1. I can install and boot from the USB Hard drive if the windows internal hard drive is physically removed. The installation is done by removing the windows internal hard drive, booting from live cd and installing to the USB external drive. I can then boot and use Ubuntu from the USB hard drive. I do make use of all steps given in the first post and the post by el dorado. Ubuntu works like a charm and no issues.
2. If I however plug back internal hard drive, it only boots from the windows internal hard drive, even though my boot bios priority is 1. removable disk 2. CDROM and 3. Hard drive.
3. Another point to note is if I plug in a bootable ubuntu USB flash drive (there is a post in these forums on how to create it), it boots from the flash drive even when all drives including the USB hard drive and windows internal drive are connected. While booting it does show USB hard drive found but then boots from the USB flash drive.

Any ideas?

Thanks

---

### Post by corbypete on 2007-07-27
Dont have to do all that for fiesty do we?

Just unplug the internal hard drive, and do an install to the external usb, then put the old hard drive back in and set boot usb as first option in the bios

yeh?

---

### Post by zenit123 on 2007-07-27
> **corbypete said:**
> Dont have to do all that for fiesty do we?

Just unplug the internal hard drive, and do an install to the external usb, then put the old hard drive back in and set boot usb as first option in the bios

yeh?

Precisely my problem, since it does not boot from external usb even after setting the bios to boot from usb when the internal hard drive is plugged in. It works fine when the internal hard drive is unplugged

Any further ideas?

---

### Post by leobaby on 2007-07-27
maybe the boot sector of the external drive is telling the computer to boot to the first drive?

when it boots windows, do you see anything before it starts booting windows?

did you edit menu.lst?

---

### Post by leobaby on 2007-07-27
Maybe you can try putting grub on the internal drive.

Maybe a boot selector is what you need. I've used acronis and it works magic on a system with multiple operating systems but it costs money.
[http://www.acronis.com/homecomputing/products/diskdirector/multibooting.html](http://www.acronis.com/homecomputing/products/diskdirector/multibooting.html)
I've heard about but have no experience whatsoever with [http://osloader.com/](http://osloader.com/)

---

### Post by zenit123 on 2007-07-28
> **leobaby said:**
> maybe the boot sector of the external drive is telling the computer to boot to the first drive?

when it boots windows, do you see anything before it starts booting windows?

did you edit menu.lst?

No I dont see anything before windows boot up, maybe couple of seconds delay. I have edited the menu.lst and changed all the hd1 to hd0 for ubuntu and hd0 to hd1 for windows.

any ideas?

---

### Post by zenit123 on 2007-08-01
> **zenit123 said:**
> No I dont see anything before windows boot up, maybe couple of seconds delay. I have edited the menu.lst and changed all the hd1 to hd0 for ubuntu and hd0 to hd1 for windows.

any ideas?

Finally got round to use Ubuntu on the usb external hard drive by booting from a Grub boot CD. The bios seem to be a problem. This is a Amilo M7405 laptop. Anybody else trying on this machine please note that the root and boot partition has to be less than 8Gb size and you need to make the necessary modifications to the menu.lst to boot from the CD.

I am able to dual boot to both Ubuntu and Windows Xp from the Grub boot CD.

Cheers

---

### Post by yashkhaitan on 2007-08-06
Hello!

well i installed ubuntu 7.04 yesterday on my external HDD yesterday. I assured tht no file enters my internal HDD but alas it didnt happen!!!!

my boot files in the internal HDD have got corrupted due to which I'm able to boot to windows or Ubuntu only when my external HDD is plugged in. The internal HDD uses the grub files to boot but wen its nt able to find them (when the external HDD is plugged out) it shows Error 21, and nothing happens after tht at all.

I was suggested by someone to boot my laptop with the windows cd in the drive nd then go on to the recovery console to repair the Master Boot records. (FIX MBR). However, im really scared to do anythin now! i hav loads of data on my laptop which i cant give up nd linux has created a partition on my external HDD so i cant use tht as well. moreover, the external HDD does not even show on my "my computer" icon in windows anymore!!!

pl suggest me wat to do?

Eagerly waiting for your reply.

Thanks alot,

Yashraj Khaitan

---

### Post by leobaby on 2007-08-06
I'll try to help but hopefully someone else will provide a second opinion.

I was able to specify to put grub on the external, but I think you might have missed that choice somewhere. No big deal.

First off, if you want to feel some reassurance boot into windows and backup your data, at the very least entire "c:\documents and settings". Then it doesn't matter if you mess up your windows install. I use acronis true image, and am not ashamed to plug that product; it has saved my hide more than once and I trust the backups I make with it.

The suggestion to fix mbr is correct, maybe in addition to fix boot. I've had to do this in the past and it is relatively trivial. But I seem to remember having to do an fdisk /mbr, which is what the grub faq suggests [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q12)


Here's a few more links that may help.
[http://www.compatdb.org/ubbthreads.php/ubb/showflat/Number/143448/page/1/fpart/2](http://www.compatdb.org/ubbthreads.php/ubb/showflat/Number/143448/page/1/fpart/2)
[http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD](http://www.wikihow.com/Uninstall-the-Grub-Bootloader-from-a-Dual-Boot-XP-System-With-an-XP-CD)

---

### Post by leobaby on 2007-08-06
Also this thread explains why the error 21. [http://www.linuxquestions.org/questions/showthread.php?p=2756026#post2756026](http://www.linuxquestions.org/questions/showthread.php?p=2756026#post2756026)

Essentially if you reinstall ubuntu and are sure to put grub on the external drive, these problems will not happen. I think the option to do this is behind a button labeled  'advanced'  at the very beginning of the install process for ubuntu. 

Good Luck.

---

### Post by yashkhaitan on 2007-08-07
Hey!

Thanks for your reply. Well something magical happened today. I sourced a Win XP cd from somewhere and just boot my pc with the CD. The CD automatically loaded some files and gave me an option to overwrite Windows XP Professional on my Home Edition. When I denied that and quit the setup, Windows started functioning as it was before!!!! 

Well now that the boot problem is solved, all I need to know is how do I make the external HDD completely independant. What I want is that whenver I want to boot Linux, I should just boot it with my external HDD and start it without it even touching my internal HDD. Is there a solution to this?

Please let me know!

Thanks.

Yashraj Khaitan

---

### Post by zenit123 on 2007-08-14
> **yashkhaitan said:**
> Hey!

Thanks for your reply. Well something magical happened today. I sourced a Win XP cd from somewhere and just boot my pc with the CD. The CD automatically loaded some files and gave me an option to overwrite Windows XP Professional on my Home Edition. When I denied that and quit the setup, Windows started functioning as it was before!!!! 

Well now that the boot problem is solved, all I need to know is how do I make the external HDD completely independant. What I want is that whenver I want to boot Linux, I should just boot it with my external HDD and start it without it even touching my internal HDD. Is there a solution to this?

Please let me know!

Thanks.

Yashraj Khaitan

When you have done selecting the hard disk and the partitions in the Ubuntu install screen, there is an advance button at the bottom above the ok button. Make sure you click that and change it from Hd0 to Hd1. This make the install program to write to the external HDD and not the internal HDD which was the mistake you made in the first place. Then your Ubuntu hdd is independent and should boot up into Ubuntu if you have made the bios changes to boot from the external drive!! If it now boots from the external HDD and indicates Error 21, or 15 , Editing your Grub Menu.lst and make sure the default Ubuntu boot is hd0 as given in the starting of this post.  

Cheers

---

### Post by yanqui on 2007-08-15
I had successfully gotten dapper on a usbhdd, but was not satisfied with some things that kept happening, like network dropping completely, no winmodem support.  Following the instructions for feisty, I have feisty installed on the usbhdd, but after that I'm stuck.

Step 8 says to use vim to edit files.  that doesn't seem to work.  Something called Busy Box comes up, and it won't recognize the commands.

if I can't get beyond that, I don't know how to proceed.

---

### Post by leobaby on 2007-08-15
if you're at a desktop then instead of vim you can just
sudo gedit

here's my post on the subject (page 49 of this thread)
[http://ubuntuforums.org/showpost.php?p=2132418&postcount=481](http://ubuntuforums.org/showpost.php?p=2132418&postcount=481)

---

### Post by yanqui on 2007-08-16
that might work.... I'll try it when I get a chance.

---

### Post by fulanito on 2007-08-20
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Sorry.
I just erased the text in the "modules" from step 8 and entered the new text:
ehci-hcd
usb-storage
scsi_mod
sd_mod

overwriting the original text. can some one send me the original text to add it again to the start of this document please!!!!!!
Thanx

---

### Post by tubaybb321 on 2007-08-22
I'm trying to install Ubuntu 7.04 on an external hard drive, but have hit a fairly embarassing stumbling block.

How Do I Boot Into Rescue Mode? 

Everything I've read seems to say just type "rescue" after the "boot:" prompt, but when I boot up off the CD, I don't see this prompt. The disk loads and then I get a screen with the Ubuntu logo and several install options. But, no "boot:" prompt.

If I type F6, an label reading "Boot Options" appears followed by an edit box with the string:

"file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --"

I've tried replacing the entire string with the word 'rescue'; I've tried replacing the substring "boot=casper" with "boot=rescue" and I've tried just concatenating 'rescue' after the '--'.

Nothing seems to work. I'd really appreciate it if someone could tell me what I should do.

Thanks.

---

### Post by spm42 on 2007-08-26
I'm a newbie and trying to load the alternate disk onto a 300GB.  I've set up "/" on sda5 and when I try Step 7 and run "mount -tproc proc /target/proc", I get a "Mounting proc on /target/proc failed: Device or resource busy".  Any ideas why this is occuring, I've tried everything I can think of (which isn't much, I'm afraid). Thanks.

---

### Post by Dezed on 2007-09-15
Ok so i have tried desperately to get my Zonbu to boot Ubuntu from external HD with no luck.

I followed these instruction to the letter with building a initrd in rescue mode and modified initramfs.conf, menu.lst etc.

However the machine won't load the kernel whatever i do. when i reboot after the installation it says

Grub loading stage 1.5

then it drops into grub prompt [ Minimal BASH-like .....

fd0 is the only thing shown when i do a root (<tab>

It's like GRUB doesn't recognizes /dev/sda drive at all ? which is very strange

Any suggestions would be immensely  great as i have been battling this for days now.

---

### Post by hikeb on 2007-09-25
Thanx DaBruGo for your input on how to get xp going from the grub boot up. I was having problems with it and as soon as i tried your suggestions it worked fine. Thanx a lot once more.

---

### Post by franzpv on 2007-09-27
HELP ! I´ve tried almost every guide, followed the indications step by step and.....no succes for me.
I've installed Ubuntu 7.04 using the alternate cd (with special attention when installing GRUB). Then modified the modules on initramfs-tools and updated the initrd.img. But still.....I'm always getting an error 2 when loading GRUB. 

But not everything isn't working. When I disable the IDE on the bios, GRUB launches smoothly and I get a functional Linux running from the Usb Disk.

(PC configuration:
 IDE1 Master: Internal Hard Disk
 IDE1 Slave: Dvd-burner
 with disabled IDE2 on the bios to speed up loading process)

---

### Post by leobaby on 2007-09-27
I think my guide might help. It's buried deep on p51 of this thread, a glaring testament to a forums lack of knowledge building ability. 

[http://ubuntuforums.org/showpost.php?p=2132418&postcount=481](http://ubuntuforums.org/showpost.php?p=2132418&postcount=481)

---

### Post by franzpv on 2007-09-28
All ready changed (hd1,0) to (hd0,0) and still no success

---

### Post by mattg89 on 2007-09-28
> **leobaby said:**
> Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.

This WORKS with Gutsy beta. Just be careful though, the place to select where GRUB is installed is hidden under and "Advanced..." button on the "Ready to Install" dialog. Thanks for the guide leobaby.

---

### Post by Stoodle on 2007-09-29
:confused:

I got lost at the GRUB part. Sorry, maybe I should read the (54 page) thread some more, but I can't get GRUB installed on the external hard drive. I tried installing it on the first partition (which according to fdisk, is bootable) but it gave me a fatal error. I'm using LVM, too, so that I can change partition sizes on the fly but I don't know what to do! There is an LVM partition for pretty much everything, a bootable partition, and a partition which I think is swap.

---

### Post by marenzu on 2007-09-30
HELP!!!

I've tried with Feisty Fawn (7.04). It's all ok until step 5. In rescue mode I was asked to choose the partition to use but the external disk partitions /dev/sdb1 and /dev/sdb2 aren't listed.

---

### Post by Stoodle on 2007-09-30
Okay, I got GRUB installed but when I put the CD back in, there isn't any place for me to type rescue, so I just chose rescue a broken system. Then, I chose the boot partition for it to boot from and then I think I had a shell, I couldn't get it to mount anything from step 7. Not sure what to do...

---

### Post by Nouba on 2007-10-23
I suggest, that you go into a grub commandline and try a [FONT="Courier"]**find --set-root /vmlinuz**[/font] to search for the right location of your root device. Some BIOSes handle external drives during boot up as a floppy disk like they do with a cdrom - i. e. [FONT="Courier"]**root (fd0)**[/FONT].

hth Nouba

---

### Post by Hero_boy on 2007-10-24
Hi I have a question regarding installing Ubuntu (v7.10 Gutsy Gibbon) to a USB 2.5" HDD.

I disconnected my other hard drives, plugged in the USB hard drive and booted off the CD in to Ubuntu. I tried installing as per normal to the hard drive with an ext3 & swap partitions but after boot it would just hang at the Ubuntu loading screen. I tried the same thing with the Ubuntu Alternate CD text installtion but it did the same thing.

So I tried the alternate CD again however created an ext2 + swap partition instead of a ext3 partition and it worked great! 

- Why does it only work with the older ext2 file system? Why can't I use ext3?
-  Are there any other changes I should make because it is a USB drive install?

---

### Post by Hero_boy on 2007-10-24
Also is there a 'best' way to run Ubuntu on a USB hard drive?

1- Installing it to the hard drive the same as a normal hard drive means all files are extracted and arn't being unzipped at boot time & it also would obviously save any changes I make as if the HDD was internal

2- Using methods like here: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) take up less HDD space but must extract the files at run-time. Is this method better though if jumping on/off many different PC's (such as AMD/Intel ATi/nVidia) as it uses its live-cd auto detect features to boot?

Sorry if these are n00b style questions :)

---

### Post by Zaphael on 2007-10-25
> **leobaby said:**
> Here is how I performed an **install of 6.10-desktop to an external usb hard drive (2.5")** and the issues I faced. Whether it's too detailed or not enough it should help someone. 

The computer is a dell laptop. I do not want to modify the internal drive at all; and I am able to choose to boot from another drive.

Before boot, my computer allows me to F12 and select boot device, usb is in the list.
If this is not possible, you might need to create a grub boot cd, or possibly in your bios you need to choose which usb drive when usb is selected. 

Small issue, my 2.5" external disk does not spin up when plugged in before turning on the computer.

**The install**:

[LIST]
[*]**prepared the target drive**. Ubuntu is unhappy to install when theres stuff on this drive it wants to mount, so I deleted all the partitions in windows Disk Management.
[*]**booted from the Ubuntu CD**.
[*]Once at the desktop, I did not see usbdisk icon on the desktop. Good for me.
[*]**started the install** and proceded with the **usual options**.
[*]At the ***Select a disk***  I chose the second drive, my usb drive, sdb.
[*]At the ***Prepare disk space***  I chose 'Manually edit partition table'. 
[*]At the ***Prepare partitions***  I made sure to choose the empty drive and created pri 16384MiB ext3, and ext 2048MiB swap.
[*]At the ***Ready to install*** dialog, I changed the 'GRUB will be installed to' option to (hd1), putting grub on the external usb. This is important, also I did not want to modify my internal drive with a boot sector. 
[*]After rebooting, I choose to **boot from the external usb drive**. Since I am booting from the drive it now appears as hd0 instead of hd1.
[*]Grub loads, so it is booting off the correct drive, but **Error 17:** Cannot mount selected partition. Press something, then presented with the grub boot menu, choose e to edit the first option, then e to edit line root (hd1,0) and changed to root (hd0,0). Then pressed b to boot 
[*]and **success**. Once at the desktop, terminal sudo **gedit /boot/grub/menu.lst**
and copied the first group of options to the very top and did the same changing **(hd1,0) to (hd0,0)**
[/LIST]
 
If you can't boot and need to edit your menu.lst, you can boot with the 6.10 disc, which will mount the usb disk, and from terminal
sudo gedit /media/usbdisk/boot/grub/menu.lst

This is much better than the days of mkinitramfs, but not quite perfect.

I know this is a lil weird.  I've got a 7.04 disc and i followed this guide for installation.  

Problem: Ubuntu doesn't boot.  Instead, Vista boots back.

Following the installation, GRUB for ubuntu has been installed on the external drive. Boot sequence has been set that USB external drive has higher priority over the Internal HDD. I'm unable to see the [Error 17:].  

The first time i booted, I saw GRUB, for a few seconds, but then disappears and vista takes over. 

The next few times, my boot went into a loop, and nothing loads. Only after removing my external HDD, will I boot into vista again.

I tried to use the Ubuntu CD to boot, and hopefully Gedit menu.lst, hoping that would fix the problem, however, the Live CD environment disallows me from logging in as root, hence I'm unable to edit menu.lst

What else can I do?

---

### Post by Zaphael on 2007-10-25
Managed to sudo Gedit /media/disk/boot/grub/menu.lst via the LiveCD

Edited 3 lines from (hd1,0), to (hd0,0)

Rebooted.  Still no success.

I see GRBLDR, but nothing after that, instead Vista loads up. 

An interesting point I noticed.  When I hit F12 to boot via USB Storage device, nothing happens.  I don't even see GRBLDR trying to load up.  But when I hit Boot via Internal HDD, I see the GRBLDR for a few secs and then vista loads up. So somehow, my bios thinks that the External HDD is an internal HDD?

I tried using EasyBCD 1.7 to add ubuntu from my USB drive into Vista's boot loader.  Was unsure whether to check the "Grub isn't installed to the bootsector" option.  When I did, and selected Ubuntu(named it myself) at vista's boot loader, i enter Grub's command line.  

Never used Grub COmmand line before, so, I have no idea how to proceed from there. 


Need help!!

---

### Post by Zaphael on 2007-10-25
F6 - "rescue" doesnt work.

Opted to boot through Live CD and carry out step 8-11 via Sudo Gedit /media/disk/--respective-- folders.
Configurations set, rebooted with USB Storage, still nothing. Rebooted with Internal HDD, see GRLDR start up, but Vista Loader suddenly supercedes it, and im back to vista! 

Any clues?? Any one???

---

### Post by Zaphael on 2007-10-26
I explored more into the problem of mine.  Made a little progress but still haven't managed to boot into my external hard drive.

Installed GRUB4DOS in the C: and created a menu.lst so that I can select which OS I want to boot to.  Windows Vista boots up fine, but Ubuntu still aint moving.

Whenever I select ubuntu, it tries to look for root (hd1,0) and finds nothing. Gives the error, "Partition Table invalid or corrupt."  Can't be, I just reinstalled 7.04 on ext2 this time.  

It leaves me to believe that my BIOS is the problem. 

Firstly, it doesn't detect the USB Storage as bootable, despite being able to boot from USB Storage.  And whenever it looks into (hd1,0), I see/hear my external hd click, but nothing happens.  Partition Invalid or Corrupt.  Is there anyway to check how my BIOS maps the devices?  Or any find --set-root /path that I can use to try to boot up?

FYI:  I tried     find --set-root /boot  <-- no joy =(

---

### Post by confused57 on 2007-10-26
Have you tried using the live cd to install grub to the root partition?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You would need to use "setup (hd1,0)", without quotes, to install to your root partition, using the instructions from the tutorial.

This might enable you to boot Ubuntu from Vista, using EasyBCD.

---

### Post by Zaphael on 2007-10-26
> **confused57 said:**
> Have you tried using the live cd to install grub to the root partition?:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You would need to use "setup (hd1,0)", without quotes, to install to your root partition, using the instructions from the tutorial.

This might enable you to boot Ubuntu from Vista, using EasyBCD.

Okay, that was just bad.  Now I can't boot up anything. 

Grub tries to run but encounters Error Code 5.  When I remove my USB External Hard Drive, I get error Code 21. 

I can't load anything.  Is there anyway to UNDO the setup (hd0)??  I need to get my GRUB4DOS back?  Anyway to remove GRUB install?

My vista was booting up via GRUB4DOS on its root partition.  I shouldn't have followed the above step since I was already using a boot loader.

---

### Post by Zaphael on 2007-10-26
I tried popping in the Vista Disk, but still grub pops up.  It refuses to go away. Its not letting me boot via CD or anything.  This is frustrating the hell out of me.

Now I have 2 un-useable OS....

---

### Post by audiofreq on 2007-10-26
Woo hoo!!

I got 7.10 loading from my external hard drive.

The problmes i had to overcome:

1 - Grub Error 18 - kernel was installed on sector the bios couldn't read...
**FIX**

During installation i created a sector /boot at the start that's 150 meg ext3
Created main ext3 "/"
Created swap

On last page changed grub install location to /dev/sda (i think...can't remember exactly)

2 - Grub Error 15 - basically since root and kernel are on different partitions you need to tweak your conf to :
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          (hd0,0)/vmlinuz-2.6.22-14-generic root=UUID=aa6385e9-b9dc-4c91-$
initrd          (hd0,0)/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          (hd0,0)/vmlinuz-2.6.22-14-generic root=UUID=aa6385e9-b9dc-4c91-$
initrd          (hd0,0)/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          (hd0,0)/memtest86+.bin
quiet

```

ROOT is where you filesystem is...not the kernel...so for me...first partition
Then just append everything else to suit...so instead of just having /vmlinuz add the partition path at the start...so it becomes (hd0,0)/vmlinuz

After saving and rebooting it takes a while for things to happen (compared to when i had the same system installed via IDE) but eventually the kernel loads and the OS starts up...

I have an XP drive in this comp too (curse me!!) and wanted to keep the mobility of my USB drive, keep XP untouched and let grub do the work if the USB drive is in and on...so if the usb is off...XP loads as if nothing happens...

I did all this install without XP drive plugged in so next step is to configure grub to have an option for XP...i imagine it will be similar. There is a file called device.map which i will add (hd1) /dev/hd0 or whatever it is...

I'm still really new to linux and although figuring this out took a bit of time i'm happy i finally got it working.

If i have been to vague then i can make a full write up...

I wasn't sure if anyone had done this with gutsy (this thread is too big!!)...

---

### Post by confused57 on 2007-10-26
> **Zaphael said:**
> Okay, that was just bad.  Now I can't boot up anything. 

Grub tries to run but encounters Error Code 5.  When I remove my USB External Hard Drive, I get error Code 21. 

I can't load anything.  Is there anyway to UNDO the setup (hd0)??  I need to get my GRUB4DOS back?  Anyway to remove GRUB install?

My vista was booting up via GRUB4DOS on its root partition.  I shouldn't have followed the above step since I was already using a boot loader.
If you used "setup (hd0)", this would have installed grub to the internal drive's mbr, however "setup (hd1,0)" should have installed grub to the Ubuntu root partition.

I would recommend downloading & burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's a very small download(5-7 Mb) and might be able to boot Vista and Ubuntu...you would need access to another pc in order to do this.

If you still have root as (hd0,0), you could try mounting your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
then change root back to (hd1,0).

Your Vista install DVD should still boot, regardless of what's on your internal hard drive's mbr...if you can get it to boot, you can use the bootrec.exe utility to restore Vista's IPL to the mbr:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by Zaphael on 2007-10-27
Thanks for the help.  

I used Super Grub Disk to fix the mbr, and it set it straight like magic.

I suspect the problem is related to my laptop's bios.  It seems that it doesn't like to boot up external usbs, and treats the external usb as an internal usb.  Even so, it could be that the bios is mapping out the devices differently, which is why root (hd1,0) returns a partition invalid or corrupt.  I don't know why.

I've switched over to my desktop to try to install ubuntu on the external hard disk.  If everything works smoothly, I can legitimately blame my bios, or for this problem.  

I did notice some funny configuration pop up during the booting of GRLDR.  Something get_diskinfo(80) n blah blah.  It might be caused by that.  

I guess i'll have to verify that with my desktop installation.

---

### Post by Zaphael on 2007-10-27
Sigh..

Trying to boot ubuntu off my external hard drive off my desktop didn't work too.

Again, might be a BIOS issue.  I don't see an option in my Bios that allows me to boot USB HDDs.  USB-ZIP, USB-FDDs, USB-CDRoms yes, but nothing for external USB drives.

Bios:  AWARDBios Revision 1010.  Yes, its an old desktop that I built in 2004 I think. 

Anymore ideas?  (Preferably without GRUB) :lolflag:

---

### Post by confused57 on 2007-10-27
> **Zaphael said:**
> Sigh..

Trying to boot ubuntu off my external hard drive off my desktop didn't work too.

Again, might be a BIOS issue.  I don't see an option in my Bios that allows me to boot USB HDDs.  USB-ZIP, USB-FDDs, USB-CDRoms yes, but nothing for external USB drives.

Bios:  AWARDBios Revision 1010.  Yes, its an old desktop that I built in 2004 I think. 

Anymore ideas?  (Preferably without GRUB) :lolflag:
Glad SGD worked, it's a pretty amazing utility.

Your problem might be with your external hard drive...could be modules have to be loaded before trying to boot:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)
I think the above instructions are for the alternate install cd, however you can designate where to install grub with the live cd by pressing the "Advanced" button and typing in your external hard drive's mbr, e.g. "/dev/sdb", without quotes(or however your external drive is recognized by the installer).

Here's the Ubuntu Documentation for installing on a USB device:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by leobaby on 2007-10-27
> **Zaphael said:**
> Sigh..

Anymore ideas?  (Preferably without GRUB) :lolflag:


Acronis

---

### Post by Zaphael on 2007-10-27
> **confused57 said:**
> Glad SGD worked, it's a pretty amazing utility.

Your problem might be with your external hard drive...could be modules have to be loaded before trying to boot:
[http://ubuntuforums.org/showpost.php?p=2982257&postcount=2](http://ubuntuforums.org/showpost.php?p=2982257&postcount=2)
I think the above instructions are for the alternate install cd, however you can designate where to install grub with the live cd by pressing the "Advanced" button and typing in your external hard drive's mbr, e.g. "/dev/sdb", without quotes(or however your external drive is recognized by the installer).

Here's the Ubuntu Documentation for installing on a USB device:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

Managed to boot up ubuntu on my desktop now.  Despite the BIOS not being able to do so.
Went back to the good old boot disk.  Or rather boot cd.

Will attempt another reinstallation on my laptop once im finished exploring the xgl n compiz features.  

A few question about running on external drive.

1.  I noticed that before I shut down last nite, i set some desktop effects, like the cube etc. When I rebooted, those effects were gone.  Does running ubuntu on external drive have some kind of non-persistency for configurations? ( don't know what to call it)

2.  Is it possible for me to run this current installation (which was done on my desktop) off my laptop with completely different hardware by just creating a new bootcd?

3.  How do I check my hardware device n whether appropriate drivers have been loaded?  Something like the equivalent of System / Device Manager.

---

### Post by traderpats on 2007-10-30
I tracked my usb hdd boot issue to the bios.  Before you read all of this post check that usb legacy support is enabled in the bios if you're trying to boot from a usb hdd.

I had read the threads and unmounted the drive and unchecked the three items in System/Preferences/Removable Drives and Media before installing.  Then installed Gutys as usual ie /, /home, swap, etc. A straight forward installation.   When installing the grub, (I had my internal eide HD's disconnected), I changed the install location from    (hdo)   to    /dev/sda  just how it's written.  This is all obtained from the threads.

If I booted without having my internal drives connected bios wouldn't find the usb hdd and would ask for a boot disk.  If I did have my internal drives connected it would boot right to xp.  My usb hdd simply was not being found.  

I went into bios and changed a lot of settings and rebooted.  The usb hdd was found and it booted right into Gutsy.  Cooool!

I went back into bios and changed everything back (I think) and it was as before - Not finding the usb hdd at boot.  Went back in again and enable usb legacy support and all is good.  I don't know why that was the case.  I had usb1&usb2 support enabled already.  Now I may have changed the "Reset configuration date" from disable to enabled also.  I don't recall.  

I shut down and reattached my internal drives.  (Paranoid I guess)  Rebooted and there were no issues.  Anyway it's as I wanted it now.  If I have my usb hdd on at boot I go into Gutsy.  If not it boots into xp.  Hope this helps.

---

### Post by thechristelegacy on 2007-10-31
Just an update to anyone reading this, I installed the newest Ubuntu release 7.10 using the modified directions for 7.04. Works great and I'm loving it! Thanks for all the help guys!

---

### Post by karishbhr on 2007-12-05
I installed 7.10 perfectly on my external last night and was using it throughout yesterday... but when I went to turn it on today my computer gets all the way to the ubuntu startup screen (so grub loads) and then my external HD turns off.

This did not happen before and I cannot remember changing anything other than running the normal updates ubuntu asks me to make.  Any ideas why this is happening?

When I load up the live cd, the external drive shows up and works... so its not a faulty drive

---

### Post by audiofreq on 2007-12-19
Hi,

After grub i get the blinking cursor for about 3 minutes.

My splash screen is fine...i've tried with and without. I've tried the 2 different methods for boot time modules...yet still the 3 minute wait before it starts booting.

I'm using 7.10...any information you need i'll supply!

This problem is driving me insane!

---

### Post by colecampbell666 on 2008-01-03
Hi!

First of all let me say; Ubuntu is amazing! The graphics are better than anything I've ever seen, the load times are superior, and best of all - it's free!

Now for a few small problems:

I downloaded Ubuntu (7.10) last night, and burned the live CD. I downloaded it to try it out, but more importantly to get past the security at my school, by having it on my portable HDD. As my USB HDD (WD Passport 250 Gb) locks up my desktop on bootup, I decided that I'd have to use my mom's laptop to install it. I put in the live CD, and on the desktop clicked install. I followed the instructions and selected my USB drive, deciding to format 200 Gb and leave 50 NTFS, as I had some important files on it. Everything seemed to go off without a hitch, and Linux works perfectly on her laptop, doing _most_ of the things I tell it to. I can't seem to install any programs from the Add/Remove window. When I click on a program, no matter which one, it says:

[IMG]http://i18.tinypic.com/8bxyz3q.png[/IMG]

This is not the least of my problems, when I remove my HDD and try to boot XP, the GRUB1.5 screen appears with an "Error 21". I'm certain that I installed Ubuntu to my USB HDD.

The main reason that I'm posting: It doesn't work at school. The majority of school PCs are Dell Optiplex gx620s, with some HPs, (not sure which model) and on the Dells Linux doesn't load. I select "USB device" in the utterly crap BIOS, and it refuses to load. I've heard of a GRUB bootdisk, is this what I need?

Thanks in advance for any replies!

[color=red]EDIT: OK. As I've now learned GRUB apparently gets loaded onto the main HDD a.k.a my mom's laptop. I don't know how to remove the GRUB partition. I didn't understand the directions for installing GRUB to the root (presumably Ubuntu) directory. If I do this, it should make Ubuntu auto-load on any PC if the BIOS is set, correct?

Another thing - Firefox now loads, but closes the second it loads a page.[/color]

[color=darkred]EDIT2: I am re-installing Ubuntu, and set the boot-loader to be installed on hd1 in the advanced options.[/color]

---

### Post by colecampbell666 on 2008-01-03
BUMP.

I really need help.

---

### Post by Acps on 2008-01-03
Ok on to my problem. I am stuck at Set 7 on the post.
mount -tproc proc /target/proc
yields an erros saying that "failed: device or resource busy"

not sure where to go from here. any help would be greatly appreciated.

---

### Post by Kegir on 2008-01-14
> **spm42 said:**
> I'm a newbie and trying to load the alternate disk onto a 300GB.  I've set up "/" on sda5 and when I try Step 7 and run "mount -tproc proc /target/proc", I get a "Mounting proc on /target/proc failed: Device or resource busy".  Any ideas why this is occuring, I've tried everything I can think of (which isn't much, I'm afraid). Thanks.


I'm having this same problem anyone have any idea?

---

### Post by ad0 on 2008-02-14
Hello,

i followed all the rules from this tutorial (installing 7.10) and my Hardware is:

HP Laptop Compaq nx9420
Internal disk 80GB

External USB Disk: WD Passport ( [WD Passport]("http://www.amazon.de/exec/obidos/ASIN/B000JRSMM2/100006612-21/?m=A3JWKAKR8XB7XF") ) ...

I created 4 Partitions on the USB disk ... that is:

/dev/sdb1 ( 80 GB ... NTFS Partition to use in Windows)
/dev/sdb2 ( 2,5 GB ... swap)
/dev/sdb3 ( 20 GB ... /home .... ext3)
/dev/sdb4 ( 50 GB ... / ........... ext3)

Now everything is fine ... except when the GRUB is trying to load, it says ...

Grub error 18:

And it stops ... i tried to change settings in BIOS (for the USB Disk) but there are no options in BIOS to set the USB drive as LBA ... help?

---

### Post by ad0 on 2008-02-14
> **Kegir said:**
> I'm having this same problem anyone have any idea?

What hapens if u do "ls -la /target" ? <- without the "

---

### Post by ZachGardner on 2008-02-19
I just got Ubuntu up and running on my laptop via a USB drive. Thanks to many people in this thread.

One problem that I ran into was the GRUB error 17 message. My BIOS, for whatever reason, wouldn't show me the order that it detects my drives. I did a little reading on GRUB and found some really good stuff. Using the [GRUB Command Line Interface](http://users.bigpond.net.au/hermanzone/p15.htm#cli), I was able to determine how BIOS was detecting my drives. I have a total of 3 drives on my system. I used the geometry command to see how big the sizes of the drives were. This narrowed it down pretty well. (Especially since my Linux drive is the only one with an ext3 partition on it.) I changed some things in GRUB using the steps described in the first post and it seems to do the trick.

I hope that experience during a day and a half of confusion might help someone out. Thanks again.

By the way, I'm using a HP dv9700z. I didn't have to make any changes to get it working other than the ones in this thread. Getting the wireless card, from what I've read, is going to take a small amount of work.

---

### Post by ajbkfloit on 2008-04-11
I tried to get 7.10 to work off the live CD, but no luck...couldn't start the GDM to even install it...have it running in a vm on Window$ Vi$ta though...
I'm running a HP Pavilion dv6451us notebook with 2 gbs of ram, a AMD Turion64 x2 TL-56 processor (1.8 GHz), 160 GB HDD, external HDD is a Fantom Drives 500 GB partitioned into two 232.94 GB & 116.46 GB NTFS partitions along with a 116.35 gb unallocated partition on the drive...my primary OS currently is Micro$oft Window$ Vi$ta Ultimate 64-bit....my bios says it supports USB boot....

Any help would be GREATLY appreciated! I love the effects I've seen on others who successfully installed 7.10....

---

### Post by Hellbourne on 2008-04-11
Anyone having problems with 8.04? I put the latest beta on my USB stick and booted it. When it started the debian-installer, the partitioner doesn't detect my hard drive. Could it be because both try to use /dev/sda and since I boot from USB it gets precedence over the hard drive?

Any suggestions?

Hellbourne.

---

### Post by ~Chimera~ on 2008-06-15
Just got Hardy 8.04 working off of an external USB Drive using a live CD.  I had to get a little creative in altering the appropriate files since there isn't a recovery mode on the live CD but I got it working in no time.  And (to the best of my knowledge)I didn't have to rebuild GRUB.  
Thanks to everyone who posted.  I've been wanting to do this for a while.  
Later,
Chimera

---

