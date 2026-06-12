---
title: "Super Grub won't load.."
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2007-08-08
In an attempt to put Ubuntu on my main PC (the last to run windows), I continue to run into problems. See my posts at:

[http://ubuntuforums.org/showthread.php?t=518071](http://ubuntuforums.org/showthread.php?t=518071)

and 

[http://ubuntuforums.org/showthread.php?t=519296](http://ubuntuforums.org/showthread.php?t=519296)

I've been directed to Super Grub which sounds like it might work. I ran into a problem because my windows partition has been overwritten. I went to a neighbor's house to burn Super Grub and got the errors referred in the threads above. I stole my kid's machine which runs on XP, and still am unable to burn the image as I consistently get errors no matter which software I use to burn the image (Nero was a flop, InfraRecorder worked to burn the ISO for feisty, and IsoRecorder seems to want to work, but wont. 

Once again, I open a thread and appeal to the Ubuntu Gods~~ Any ideas or do you see something I'm missing?

---

### Post by adrian15 on 2007-08-08
Your previous threads are very strange. I have never heard nothing about this problem.

1) If your windows partition has been overwritten I suspect that SGD cannot do nothing about it.
However if what has been overwritten is the windows partition boot record it might help (although I am not very sure with Advanced -> Windows (Advanced) -> Fix Windows Partition Boot .

2) You can try to make yourself a floppy or try to make an SGD usb.

3) Use Firefox internet browser to download the ISO with the Save Link as option and then burn it with whatever burning program you have with the "Write Image to Disk" or similar option. I mean when you burn the disk you do not have to see the .iso image INSIDE it.

I have heard that some Internet Explorer version have a bug that makes some binaries downloads corrupt. So that's might be your case. Is it?

adrian15

---

### Post by sp0nge on 2007-08-08
THanks for the input, I Use firefox on my windows machines as well. 

I tried to boot back into windows simply because I couldn't burn the iso correctly, I knew deep down that it was gone because I had seen the Error 21 popping up as ubuntu tried to load from the successful install. 

I have tried to make the sgd boot disk, but the troubled machine has no floppy drive, only an optical superdrive. In attempting to burn the ISO is where I'm getting the errors. I will attempt to re-download the image and burn in case there was a corrupt download. I think this is highly unlikely as it has happened from 2 machines now. 

In reading more, I understand there is some signifigance in the menu.lst file, so here is what I found: 

<code>
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
# kopt=root=UUID=81dfa119-60ae-4dd0-a195-d6fb7f27b2f3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=81dfa119-60ae-4dd0-a195-d6fb7f27b2f3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=81dfa119-60ae-4dd0-a195-d6fb7f27b2f3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
</code>

I'll post again after I retry the sgd as you suggest.

---

### Post by sp0nge on 2007-08-08
"Operation has failed. Reason: A generic error has occurred. "

---

### Post by adrian15 on 2007-08-08
> **sp0nge said:**
> THanks for the input, I Use firefox on my windows machines as well. 


So that's not the problem.
> **sp0nge said:**
> 
I tried to boot back into windows simply because I couldn't burn the iso correctly, I knew deep down that it was gone because I had seen the Error 21 popping up as ubuntu tried to load from the successful install. 

Error 21 seems that grub is installed to check for files in disk #2 meanwhile files are in #1. Maybe you have an incorrect device.map. 

If you try to correct device.map then you have to rerun grub-install again.
> **sp0nge said:**
> 
I have tried to make the sgd boot disk, but the troubled machine has no floppy drive, only an optical superdrive.


If your Linux handles your optical superdrive you can boot it with Super Grub Disk (Linux -> Boot Linux). Once booted you can try:

Untar the usb version of SGD into the optical superdrive so that when you open it you see the boot folder.

Open a terminal an type

sudo grub
grub> device (hd3) /dev/sd0 #where /dev/sd0 is device that matchs your optical superdrive.
grub> root (hd3,0)
grub> setup (hd3,0)
grub> quit

I suppose that your optical super drive is a read and write medium and that you have only one fat partition.

> **sp0nge said:**
> 
 In attempting to burn the ISO is where I'm getting the errors. I will attempt to re-download the image and burn in case there was a corrupt download. I think this is highly unlikely as it has happened from 2 machines now. 

That's strange. I had no complaints about it before. You can try however three different mirrors for downloading which can be found at [Super Grub Disk site]("http://geocities.com/supergrubdisk/"). Please check the links with (DOWNLOAD) on them.


> **sp0nge said:**
> 
In reading more, I understand there is some signifigance in the menu.lst file, so here is what I found: 

<code>
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
...
</code>


One question the error is just before seeing the menu. I mean you do not see any menu, don't you?
> **sp0nge said:**
> 
I'll post again after I retry the sgd as you suggest.

Waiting for your answer as your situation is quite strange.

adrian15

P.S.: I have also one tip if you want. Please try to burn the ISO image in the slowest burning speed that you have. It seems that the slower you burn a cd the better it's burnt. I do not agree with this afirmation but they might be right in your case. :)

---

### Post by sp0nge on 2007-08-08
As I look at device.map, I see: 

(hd0)	/dev/sda

Linux does handle the optical drive rather well, as it runs the Live CD of feisty just fine. I've downloaded the ISO for the supergrub disk as recomended by logos34. In trying to burn the image, I continue to get the error messages which won't let me successfully burn sgd to boot. Are you suggesting I download Untar? I'll go look for it now. 

Upon your suggestion the terminal returns:

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

And to answer your final question- No, I do not see a menu, Upon starting up, the machine goes through post, then requires me to press F1 to access the JMicron portion of the startup which recognizes the HDD. Then is says GRUB loading and then the error. No menu.

---

### Post by sp0nge on 2007-08-08
41 views and no more replys? I'm starting to lose hope. Can it be that I'll really be forced to keep windows on this machine?! SAY IT AINT SO!!!!!!!

:confused:

---

### Post by adrian15 on 2007-08-09
> **sp0nge said:**
> 
Upon your suggestion the terminal returns:

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.


Can you please tell me the full sequence of commands. I told you to use (hd3) and you used (hd0) and I do not know if you have even used the device command with the right device!

> **sp0nge said:**
> 
And to answer your final question- No, I do not see a menu, Upon starting up, the machine goes through post, then requires me to press F1 to access the JMicron portion of the startup which recognizes the HDD. Then is says GRUB loading and then the error. No menu.


Let's see. Once you have put SGD into the optical drive (Which I cannot assure that you have made ok.) you have to setup your bios so that it boots from your optical drive not from your default drive.

Maybe the F8 or the F12 at bios boot time may help or just pressing SUPR, DELETE or F1 as you say to set up the boot order on the bios setup.

adrian15

Don't you have a Linux neighbour which can borrow you an SGD disk?
I might mail you by land mail at last. :)

---

### Post by sp0nge on 2007-08-09
When I ran 

sudo grub
grub> device (hd3) /dev/sd0 #where /dev/sd0 is device that matchs your optical superdrive.
grub> root (hd3,0)
grub> setup (hd3,0)
grub> quit

I replaced (hd3,0) because I had a dumb moment.  Upon reading this post. I input the commands just as you recommended and this was returned: 

```
grub> device (hd3,0) /dev/sd0
Error 15: File not found.
```


The machine is set to boot from this optical drive as it's the only drive (aside from the HDD) that is installed. I've been trying to download and burn sgd onto CD from 3 different windows machines now to no avail (and I know I'm doing it correctly because I burned the ISO for feisty and it boots just fine).

As for a linux neighbor, it seems everyone here is stuck in windows. They look at me like I have 2 heads when I start talking about something outside that realm. 

I'd hate to put you out to mail something, but it seems that no one else has any input at this point- I'm open for anything that will help.

---

### Post by adrian15 on 2007-08-10
```
grub> device (hd3,0) /dev/sd0
Error 15: File not found.
```
[/QUOTE]

You should know what's the linux device for your optical drive. Maybe taking a look at /etc/fstab if the optical drive is a permanent drive may help.

I mean maybe your optical drive is called /dev/hdb or /dev/sdb I do not know it myself.

I have another option for you that might sound interesting for you:

[SGD + Gparted Live cd + System rescue cd]("http://sgd.howto-linux.de/download/binaries/sgd_plus_distros/sgd_gparted_system_rescue_001.iso")

It's a 200 MB or 300 MB iso with SGD in it... maybe you can burn this because it's big enough.

Please try it. I suppose you have tried the three mirror on [Super Grub Disk]("http://geocities.com/supergrubdisk/") site already.

Good luck with the big ISO!

adrian15

---

### Post by sp0nge on 2007-08-10
WTH!?!

I was thinking you're on to something, the ISO has burned correctly. Now, I encounter another issue!

Upon booting to the CD, I get:

```
Boot from CD:
GRUB Loading stage 1.5

GRUB Loading, please wait...
Error 21
```


I don't get it. Is this not supposed to be a boot disk?

---

### Post by merlinus on 2007-08-10
Seems to me that you are booting from your hard drive and not from the cd.

-merlin

---

### Post by sp0nge on 2007-08-10
That is what I think as well. I've double checked the BIOS to confirm the machine is booting from the optical drive, it even TRIES to boot (running upon startup, sounds like it's doing work). I can reboot into the Live CD still without issue, but apparently this disk isn't recognized as a boot disk.

I'll try to burn the recommended ISO again, but I don't expect any change.

---

### Post by sp0nge on 2007-08-13
I have now tried to burn the ISO for SGD and for the rescue disk from 3 machines. 2 on my network and one on another network and STILL get the same error messages. To make it more frustrating, I find the disks I used are now unusable. They say they're completely full, but there is no visable data and I have no options to erase the disk (yes, they ARE CD-RW).

If I could find my sledge hammer, I'd fix this thing!

---

### Post by merlinus on 2007-08-13
My best guess is that your downloads are corrupted.  You can possibly do a checksum.  Here are details:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

-merlin

---

### Post by adrian15 on 2007-08-17
As long as I do not have md5 checksums already uploaded he can try to download

a [bz2 file]("http://sgd.howto-linux.de/download/binaries/sgd/cdrom/sgd_0.9598.iso.bz2") and bunzip2 to ensure itself that the ISO is correct.

Another thoughts on this subject:


#1

Are your cdrw disks 2x and 4x speed (ultraspeed) meanwhile the cd
recorders are 8x and above (I do not know the technology name)?

Maybe that's the problem. These cdrws cannot be used in new drives.

#2 Burn the SGD CD from a linux system with a cdrecord at the lowest
speed command.

#3 I have tried SGD 0.9598.iso in my system. I've burned it with k3b and
I've booted as usually and no problem at all. The only thing that I saw
is that the ISO does not check OK the checksum but this does not bother
me too much because I do not build them with an option to save the
checksum into the ISO itself.

#4 Another option is to build myself an stripped-down knoppix with only isolinux boot loader and a SGD floppy image so that you boot it from isolinux. This method might not worked in all the bios because it needs some special interrupt calls.


adrian15

---

### Post by jnorthr on 2007-08-21
here is a link to the grub documentation [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/) for version 0.97 of supergrub. May help. Section 14 has a list of the error codes. '21' is Selected disk does not exist.:-?

---

### Post by sp0nge on 2007-09-30
After taking some much needed time off, I've overcome the urge to throw this thing through the window.. Now that I'm back at it, I find windows fails to recognize the LAN cable so I can't download the BIOS as the guy from J Micron suggested. I Was worried I had done something to fry it but once I Loaded Fiesty on the live CD I can get online just fine. I still can not get GRUB to load when linux is installed. Any input on how to overcome this?

---

