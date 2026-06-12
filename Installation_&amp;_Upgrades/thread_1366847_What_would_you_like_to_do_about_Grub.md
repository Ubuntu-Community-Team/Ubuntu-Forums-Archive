---
title: "What would you like to do about Grub?"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by adam22 on 2009-12-28
Hi guys. I was previously using Vista with Ubuntu via Wubi. However, I recently installed Windows 7 64 Bit Home Premium and Karnic Koala with a standard hard drive partition.

The problem is after I installed Karmic and updated it, I was presented with this screen (click to enlarge):

_[[IMG]http://img9.imageshack.us/img9/2061/screenshotge.th.png[/IMG]](http://img9.imageshack.us/i/screenshotge.png/)_

I had the Windows Bootloader when I was using Wubi, so I was surprised to see GRUB2...that just shows you my level of knowledge in this area.

System Specs are:
AMD Athlon Dual Core X2 2.1 Ghz
ATI Radeon 3200
Ubuntu 9.10 64 Bit

What option would you recommend?

---

### Post by x33a on 2009-12-28
you should just keep the current version, if everything is working fine, i.e., you can boot into both OSes.

---

### Post by adam22 on 2009-12-28
I don't think so. I read a lot of threads saying that will screw things up. If anything I believe it will keep the current kernel listed in GRUB, which will be a problem if I'm updating the kernel. I can't find a whole lot of information about this though.

---

### Post by x33a on 2009-12-28
do a 2 way compare and see the differences.

if possible, post the output here.

and yes, if the kernel is being updated, then keeping the old version won't add entries for the newer kernel. though, it won't break anything, and you can even manually create entries for the newer kernel.

though, i am using grub legacy, so i am not sure, how easy it is to change stuff with grub2.

---

### Post by presence1960 on 2009-12-28
If you don't use the package maintainer's version there always seems to be problems, one of which is the newly installed kernel does not appear in GRUB menu. Why would you update and then use the old version?

---

### Post by adam22 on 2009-12-28
> **presence1960 said:**
> If you don't use the package maintainer's version there always seems to be problems, one of which is the newly installed kernel does not appear in GRUB menu. Why would you update and then use the old version?

Thank you for the reply. It would seem that I should select the 'Install the package maintainer's version' option? This will update the GRUB listings with the newly installed kernel, correct? Is there anything that has to be done afterwards?

---

### Post by drs305 on 2009-12-28
> **adam22 said:**
> Thank you for the reply. It would seem that I should select the 'Install the package maintainer's version' option? This will update the GRUB listings with the newly installed kernel, correct? Is there anything that has to be done afterwards?

Choosing to update to the maintainer's version is usually a good idea, since it will incorporate any improvements the developers have made and which Ubuntu has adopted. Unless you have made manual changes to the Grub 2 files you shouldn't notice much difference.

If have already modified the default kernel selection, timeout, etc, you may have to go into /etc/default/grub and set them again.

After install, running "sudo update-grub" won't hurt. It should be done during the upgrade but it won't harm anything to run it again just to make sure it has tried to find all your system's OS's.

---

### Post by adam22 on 2009-12-28
Thanks for the replies. Any other opinions?

I've never messed with GRUB before at all (no editing for anything) since it's not used with the Wubi installation. This is my first time installing to the hard drive and I don't have anything custom set. I just remember seing some recovery for Windows and Windows 7 as well as I think 3 Linux options listed in the boot menu. I just don't want to mess anything up.

That command, 'sudo update-grub'...what exactly does that do?

Thank you.

---

### Post by drs305 on 2009-12-28
> **adam22 said:**
> That command, 'sudo update-grub'...what exactly does that do?

It runs a series of scripts, mostly found in /etc/grub.d/ which look for linux kernels and other operating systems. It also looks at the settings in the /etc/default/grub file and incorporates what it finds into the GRUB 2 menu which is displayed on boot. And to be precise, it's actually a stub (think shortcut) for the command "grub-mkconfig -o /boot/grub/grub.cfg".

To learn more about Grub 2, take a look at the GRUB2 link in my signature line, which is a link to the Ubuntu community doc on Grub 2. The G2-Basics link is to the original thread on this forum regarding Grub 2. The "G2-Basics" tells you how to set up the most commonly-changed items in the Grub 2 menu, such as timeout and default kernel selection.  The "G2-Basics" linked post also contains some links to others who have written excellent posts on the new Grub 2 bootloader.

---

### Post by adam22 on 2009-12-28
Thank you for the help! Everything is working fine, and as expected the old kernel is listed, but will leave for now. 

Cheers.

---

### Post by geoffree on 2009-12-29
I have/had a dual boot system with suse 11.2 and ubuntu.  Last night/this am I upgraded from 9.04 to 9.10. Toward the end of the process I got a message regarding menu.lst and if I wanted to leave it as is. I did. After finishing 3 hours of download and upgrade I re-booted and found that menu.lst was (surprise, surprise) still listing ubuntu 9.04. The menu screen comes up after startup and displays suse, suse failsafe and ubuntu.  Selecting ubuntu first gives an error message including the phrase (EE) Intel (0) .... more that slipped away, and then that it was starting up in Low Graphics mode.  Had a choice of either one time use of low or re-configuring or etc.  (I am hoping these terms may be familiar) (but not as it is to me now which is not pleasant).  I vainly tried apt-get update, upgrade and update-grub which scrolled many pkg names but not much else.  Question: How do I change the menu.lst in Suse,  the menu in Ubuntu, and be able to boot Ubuntu normally with a higher resolution than 640x480?  I hope this is somewhat clear - I've been up a long time and getting frustrated and woozy.  

If I've not been clear I will supply whatever info can help you help me, and presumably others who have confronted this problem.

Geoffree  (zeno@empire.net)

---

### Post by presence1960 on 2009-12-29
> **geoffree said:**
> I have/had a dual boot system with suse 11.2 and ubuntu.  Last night/this am I upgraded from 9.04 to 9.10. Toward the end of the process I got a message regarding menu.lst and if I wanted to leave it as is. I did. After finishing 3 hours of download and upgrade I re-booted and found that menu.lst was (surprise, surprise) still listing ubuntu 9.04. The menu screen comes up after startup and displays suse, suse failsafe and ubuntu.  Selecting ubuntu first gives an error message including the phrase (EE) Intel (0) .... more that slipped away, and then that it was starting up in Low Graphics mode.  Had a choice of either one time use of low or re-configuring or etc.  (I am hoping these terms may be familiar) (but not as it is to me now which is not pleasant).  I vainly tried apt-get update, upgrade and update-grub which scrolled many pkg names but not much else.  Question: How do I change the menu.lst in Suse,  the menu in Ubuntu, and be able to boot Ubuntu normally with a higher resolution than 640x480?  I hope this is somewhat clear - I've been up a long time and getting frustrated and woozy.  

If I've not been clear I will supply whatever info can help you help me, and presumably others who have confronted this problem.

Geoffree  (zeno@empire.net)

If you didn't install the package maintainer's version then your 9.10 kernel is not listed in menu.lst. That means you are booting from a Jaunty 9.04 kernel. But to be sure look at the kernel in menu.lst. karmic's kernel should be 2.6.31-x. If it is not listed you can try manually adding the 9.10 kernel stanza to menu.lst

In the future when you update kernels always choose use the package maintainer's version to keep everything in sync.

---

### Post by geoffree on 2009-12-29
> **presence1960 said:**
> If you didn't install the package maintainer's version then your 9.10 kernel is not listed in menu.lst. That means you are booting from a Jaunty 9.04 kernel. But to be sure look at the kernel in menu.lst. karmic's kernel should be 2.6.31-x. If it is not listed you can try manually adding the 9.10 kernel stanza to menu.lst

In the future when you update kernels always choose use the package maintainer's version to keep everything in sync.
Thank you for your quick reply. I did check menu.lst after doing "update-grub" and it still is listing 9.04, although the 2.6.31-17 kernel is in the /boot dir. 
How do I manually install the kernel stanza and also how to do a similar change in the suse menu.lst which is the boot loader and also lists Ubuntu 9.04.

I will stand by, appreciatively,

Geoffree

---

### Post by presence1960 on 2009-12-29
> **geoffree said:**
> Thank you for your quick reply. I did check menu.lst after doing "update-grub" and it still is listing 9.04, although the 2.6.31-17 kernel is in the /boot dir. 
How do I manually install the kernel stanza and also how to do a similar change in the suse menu.lst which is the boot loader and also lists Ubuntu 9.04.

I will stand by, appreciatively,

Geoffree

I don't use GRUB 0.97 anylonger and as such do not have a menu.lst
If you could post the contents of your menu.lst I can help you with that. Off the top of my head I don't remember exactly the kernel stanzas.

---

### Post by geoffree on 2009-12-29
Once again, thank you for replying.

Below is the whole gruesome menu.lst as it now exists in Ubuntu 9.10.  ((Happy faces replaced (8) for some horrible reason.))

Following I have placed the menu.lst from SuSE 11.2

Geoffree


root@zenotopia:/home/zeno# cat /boot/grub/menu.lst
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
timeout	10

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
# kopt=root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dd299f57-f3fb-45db-b551-bb46087909a2

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

title		Ubuntu 9.04, kernel 2.6.28-16-generic
uuid		dd299f57-f3fb-45db-b551-bb46087909a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid		dd299f57-f3fb-45db-b551-bb46087909a2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		dd299f57-f3fb-45db-b551-bb46087909a2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		dd299f57-f3fb-45db-b551-bb46087909a2
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

## title		Ubuntu 9.04, kernel 2.6.28-14-generic
## uuid		dd299f57-f3fb-45db-b551-bb46087909a2
## kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.28-14-generic
## quiet

## title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
## uuid		dd299f57-f3fb-45db-b551-bb46087909a2
## kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro  single
## initrd		/boot/initrd.img-2.6.28-14-generic

## title		Ubuntu 9.04, kernel 2.6.28-11-generic
## uuid		dd299f57-f3fb-45db-b551-bb46087909a2
## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash 
## initrd		/boot/initrd.img-2.6.28-11-generic
## quiet

## title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
## uuid		dd299f57-f3fb-45db-b551-bb46087909a2
## kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro  single
## initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		dd299f57-f3fb-45db-b551-bb46087909a2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

******************************************************


...AND HERE IS THE SUSE MENU.LST THAT INITIATES THE BOOT PROCESS:


root@zenotopia:/# cat media/disk/boot/grub/menu.lst
# Modified by YaST2. Last modification on Sat Dec 19 09:06:05 EST 2009
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,4)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2
    root (hd0,4)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-ST380013AS_3JVCLFRX-part5 resume=/dev/disk/by-id/ata-ST380013AS_3JVCLFRX-part3 splash=silent quiet showopts vga=0x314
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)###
title Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2
    root (hd0,4)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-ST380013AS_3JVCLFRX-part5 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x314
    initrd /boot/initrd




Thank you,  Geoffree

---

### Post by presence1960 on 2009-12-29
```
title Ubuntu 9.04, kernel 2.6.28-16-generic
uuid dd299f57-f3fb-45db-b551-bb46087909a2
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash
initrd /boot/initrd.img-2.6.28-16-generic
quiet

title Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid dd299f57-f3fb-45db-b551-bb46087909a2
kernel /boot/vmlinuz-2.6.28-16-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro single
initrd /boot/initrd.img-2.6.28-16-generic
```

I only pasted the top two kernel stanzas. If you need more will depend on how many 9.10 kernels you have in your /boot directory. Change these two to:

```
title Ubuntu 9.10, kernel 2.6.31-17-generic
uuid dd299f57-f3fb-45db-b551-bb46087909a2
kernel /boot/vmlinuz-2.6.31-17-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro quiet splash
initrd /boot/initrd.img-2.6.31-17-generic
quiet

title Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid dd299f57-f3fb-45db-b551-bb46087909a2
kernel /boot/vmlinuz-2.6.31-17-generic root=UUID=dd299f57-f3fb-45db-b551-bb46087909a2 ro single
initrd /boot/initrd.img-2.6.31-17-generic
```

Click Save on toolbar and close file. Reboot try booting into the 9.10 kernel. If successful then try booting into recovery mode. If all works then reboot and edit your Ubuntu menu.lst by removing the remaining jaunty kernels stanzas.

I think you know how to edit menu.lst
But just in case run in terminal ```
gksu gedit /boot/grub/menu.lst
```
 If your Ubuntu GRUB is in MBR and takes over when you boot I recommend chainloading Suse's GRUB from Ubuntu's GRUB. But let's get Ubuntu up first.

---

### Post by presence1960 on 2009-12-29
If you are using Suse's GRUB to boot your machine then you need to edit the chainload entry for Ubuntu in Suse's GRUB also. Change this:

```
###Don't change this comment - YaST2 identifier: Original name: Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)###
title Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)
rootnoverify (hd0,0)
chainloader +1
```

To:

```
###Don't change this comment - YaST2 identifier: Original name: Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)###
title Ubuntu 9.10 (/dev/sda1)
rootnoverify (hd0,0)
chainloader +1
```

When you select Ubuntu from Suse you should get Ubuntu's GRUB menu with the entries you edited earlier.

---

### Post by geoffree on 2009-12-29
Great!  Thanks.  I will try these now (using emacs) and get back to you.

Geoffree

---

### Post by presence1960 on 2009-12-29
> **geoffree said:**
> Great!  Thanks.  I will try these now (using emacs) and get back to you.

Geoffree

I would make a copy of both menu.lsts just in case!

---

### Post by geoffree on 2009-12-29
A million thanks.  It works like a charm and I now even have a large selection of video resolutions.  You responded in the true Linux spirit, which is why I love this argghh system.  I've seen you're reply to others and you seem to be there consistently.
Three cheers.  This has been a very rough morning but alls well that ends (temp) well.
Now...can I just remove everything else besides those two stanzas?  As for SuSE, the boot menu still comes up with Ubuntu listed as 9.04, though when I clic on it, it goes to the Ubuntu menu which I added the 'mem' stanza.  Should I do a similar paste/replace in the SuSE menu.lst of the Ubuntu stanzas?  Or?

Geoffree

And how do I post an acknowledgement of your service?

---

### Post by presence1960 on 2009-12-29
> **geoffree said:**
> A million thanks.  It works like a charm and I now even have a large selection of video resolutions.  You responded in the true Linux spirit, which is why I love this argghh system.  I've seen you're reply to others and you seem to be there consistently.
Three cheers.  This has been a very rough morning but alls well that ends (temp) well.
Now...can I just remove everything else besides those two stanzas?  As for SuSE, the boot menu still comes up with Ubuntu listed as 9.04, though when I clic on it, it goes to the Ubuntu menu which I added the 'mem' stanza.  Should I do a similar paste/replace in the SuSE menu.lst of the Ubuntu stanzas?  Or?

Geoffree

And how do I post an acknowledgement of your service?

In the Ubuntu menu.lst you can remove all other kernel stanzas that are not 9.10.

In the Suse menu.lst I was leary of editing that first line ```
###Don't change this comment - YaST2 identifier: Original name: Ubuntu 9.04, kernel 2.6.28-16-generic (/dev/sda1)###
```
 because it said not to do so. If you want to try it make sure you have a backup in case of disaster that way you can edit that line back to the way it was.

Glad you got it working. Enjoy!

---

