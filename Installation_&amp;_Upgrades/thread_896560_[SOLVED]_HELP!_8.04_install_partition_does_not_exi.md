---
title: "[SOLVED] HELP! 8.04 install partition does not exist"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Bandolin on 2008-08-21
I have a P4 standard desktop with Win XP and Ubuntu 7.10. When I boot I get the choice of booting up in Ubuntu or Windows. I wanted to upgrade to 8.04, so I choose the 10 Gb Ubuntu partition that had 7.10 installed on it. Everything seemed to go well. But now when I reboot I get the message:
Error 22: No such partition

I can't get into Linux or Windows! It won't recognize any partition.

I desperately need help. Please tell me there's a solution to this which involves getting my Windows XP back.

---

### Post by coffeecat on 2008-08-21
Hopefully, your Windows partition is still there, and there's been a mixup when the installer installed grub. First step is to see what's on the hard disc. Boot up with the live cd and go to Applications > Accessories > Terminal. Post the output of:

```
sudo fdisk -l
```

That's a lower-case L, not one.

---

### Post by Bandolin on 2008-08-21
I get the following. Keep in mind I'm on my laptop so I'm actually retyping everything I see in the terminal window.

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24421 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eb87eb8

   Device Boot     Start       End     Blocks    Id   System
/dev/dsa1    *        2      24321   195350400    5  Extended
/dev/sda5             2       1942    15591051    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 Bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

   Device Boot     Start       End     Blocks    Id   System
/dev/dsa1    *        1       7012   56323858+    7  HPFS/NTFS
/dev/sda2          7013       8228    9767520    83  Linux
/dev/sda3          8229       8352     996030    82  Linux swap /Solaris
/dev/sda4          8353       9729  11060752+    83  Linux
ubuntu@ubuntu:~$

---

### Post by Bandolin on 2008-08-21
With the Live CD when I go to Places I can see my Win XP drive. Everything seems to be there. So, I didn't lose the data. How can I get the boot to work again?

---

### Post by coffeecat on 2008-08-21
> **Bandolin said:**
> Keep in mind I'm on my laptop so I'm actually retyping everything I see in the terminal window.

My apologies; I should have pointed out that if you were able to connect to the internet in the live environment you would have been able to copy and paste from the terminal. Anyway, I'm slightly perplexed about the partition layout. let me give you my thoughts and then take it from there.

> **Bandolin said:**
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24421 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eb87eb8

   Device Boot     Start       End     Blocks    Id   System
/dev/dsa1    *        2      24321   195350400    5  Extended
/dev/sda5             2       1942    15591051    7  HPFS/NTFS

This is the first disc. What is odd is that the NTFS partition is on a logical partition (sda5). Is that your Windows C: partition? Because that's very odd. Normally, Windows can't boot from a logical partition and you have to do some clever hacking to get it to do so. If that is your Windows C: partition, it would have been more straightforward to have sda1 as an ordinary primary partition. Also, the numbers for sda1 and sda5 don't seem to fit. sda1, as an extended partition, is the 'container' for sda5.

> Disk /dev/sdb: 80.0 GB, 80026361856 Bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

   Device Boot     Start       End     Blocks    Id   System
/dev/dsa1    *        1       7012   56323858+    7  HPFS/NTFS
/dev/sda2          7013       8228    9767520    83  Linux
/dev/sda3          8229       8352     996030    82  Linux swap /Solaris
/dev/sda4          8353       9729  11060752+    83  LinuxI think you've mistranscribed sda for sdb in the second block. I'm guessing that's all the second disc - sdb. What's interesting is that you've got two ext3 Linux partitions. Did you have a separate /home? If not, it's possible you've ended up with two Ubuntu installations, 7.10 and 8.04.

> With the Live CD when I go to Places I can see my Win XP drive. Everything seems to be there. So, I didn't lose the data. How can I get the boot to work again?You'll have to give me time. I'm also trying to help a neighbour who's been taken ill.

Question: are you able to connect to the internet with the live CD? The reason I ask is that I think this is a simple grub repair job, but to get the information needed it might be easier to post a couple of screenshots from the GUI. I'll tell you what when you answer that.

---

### Post by redester on 2008-08-21
****

The same happened to me with 8.04!  Two weeks of angst!!!

Running with the Live CD I was able to edit GRUB's Menu.lst and noted the references were to HD1.. Changed them to HD0 and voila!!  Happy again.

This *might* be your problem.... ?


Ray

---

### Post by Bandolin on 2008-08-21
If this is my problem how do I fix it. I'm a complete noob.

---

### Post by Bandolin on 2008-08-21
The first disk listed is my 200 Gb HD and not the Windows: C drive.

The second disk is my 80 Gb HD and yes that is my Windows: C drive.

I did mistranscribe sda for sdb.

I can connect to the internet from the Live CD. It took me a couple of hours but I finally figured it out.

---

### Post by maybeway36 on 2008-08-21
There is a quick way to get Windows back, but it won't let you boot Linux for the time being:
```
sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
```
Keep in mind if you mistype it it could very well wreck your data, so be careful.
The DOS command
```
FDISK /MBR
```
will do the same thing.

First, though, to get into the menu.lst from the live CD, mount the partition you installed Ubuntu to (Places menu), then find boot/grub/menu.lst and edit it as root. You might need to press Alt+F2 and run "gksu gedit", then use File>Open.

---

### Post by Bandolin on 2008-08-21
So, if I type the code: sudo dd if=/dev/zero of=/dev/sda bs=446 count=1 (how do you get that niffty box around the code quote).

I'll get my windows back but not Linux.

You also state FDISK /MBR is a DOS command and will do the same thing. But if I can't get windows up how can I enter the DOS command?

I don't understand what you mean by edit the boot/grub/menu.lst as root. I found the file and just double clicked on it and it opened in a text file, but I don't know what I'm editing and what will it do? Must I do this before I perform the code you listed above?

---

### Post by coffeecat on 2008-08-21
If you've managed to find the menu.lst file, could you post it please? Also, we need to know whether your Ubuntu root partition is on sdb2 or sdb4 so we know whether or not menu.lst needs editing and, if so, what to change.

Also, we may need to reinstall grub stage 1 to the mbr and for that we also need to know what partition your Ubuntu root is on. As you've managed to find menu.lst, have you been able to work out which partition that is?

Personally, I wouldn't do the sudo dd.. bit. In fact, I can't see what maybeway36 is trying to achieve with that code. It looks as though you have a perfectly good Windows C: partition on sdb1, and we just need to make sure you can get into a working grub menu.lst to be able to boot from it.

And FDISK /MBR from MSDOS won't work (I think) because you've got Windows on the second disc. And even if it did work, you'd lose the ability to boot into Ubuntu, so please everyone, let's concentrate on getting grub up and running so that the OP can boot into both Ubuntu and Windows.

---

### Post by Bandolin on 2008-08-21
I'm pretty sure Ubuntu is on sdb2. Here is the dump from my menu.lst

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Microsoft Windows XP Professional
root		(hd0,5)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


---

### Post by Bandolin on 2008-08-21
So, as far as I can gather from the various posts I must somehow edit my GRUB =Grand Unified Boot loader.

from GNU.org

> Briefly, boot loader is the first software program that runs when a computer starts. It is responsible for loading and transferring control to the operating system kernel software (such as the Hurd or the Linux). The kernel, in turn, initializes the rest of the operating system (e.g. GNU). 

from grub.enbug.org

> GRUB 2

GRUB 2 is the next generation of GNU GRUB. GRUB 2 is a complete rewrite and is at a developmental phase. The most important goal is to make GNU GRUB cleaner, safer, more robust, more portable and more powerful. 

I don't understand if GRUB is meant for Linux, why is it affecting my Win XP OS?

---

### Post by coffeecat on 2008-08-21
If Ubuntu is on sdb2, and that's what that menu.lst says, then that menu.lst looks fine and all you need do is reinstall grub stage 1 to the mbr, as below.

I'm puzzled by the two Windows entries. the second is for sdb1 and looks fine. But why an entry for sda6 when you don't have a sda6? I don't understand. (hd0,5), by the way is grub-speak for sda6.

Anyway - boot up from the live CD again and go to Applications > Accessories > Terminal. Type:

```
sudo grub
```.. and the prompt will change to the > grub one. Now type these three commands, each followed by return. You will get feedback from grub after the first two. Post if these are error messages.

```
root (hd1,1)
setup (hd0)
quit
```Now close the terminal, reboot, remove the CD and let's see what happens. We'll still need to do something about that mystery Windows entry in the grub menu, but I want to get you booting into Ubuntu and Windows on sdb1 first.

---

### Post by coffeecat on 2008-08-21
> **Bandolin said:**
> I don't understand if GRUB is meant for Linux, why is it affecting my Win XP OS?

OK. Quick tutorial.

The [COLOR=red]GR[/COLOR]and [COLOR=red]U[/COLOR]nified [COLOR=red]B[/COLOR]ootloader is a bootloader which is commonly (but not exclusively) used in Linux, but which can also boot up Windows. When you install Windows, it puts about 400 bytes of code on the MBR ( [see wikipedia article]("http://en.wikipedia.org/wiki/Master_boot_record") ) which, during the boot process, takes control from the BIOS and then hands control to the boot code in the Windows partition.

Grub works a bit differently. Stage 1 is installed to the MBR and replaces the Windows MBR code. Stage 1.5....... But why not read [wikipedia on Grub]("http://en.wikipedia.org/wiki/GNU_GRUB")? :wink: The important bit is:

> 
When a computer is turned on, the computer's [BIOS]("http://en.wikipedia.org/wiki/BIOS") finds the primary bootable device (usually the computer's hard disk) and loads the initial [bootstrap]("http://en.wikipedia.org/wiki/Bootstrapping_%28computing%29") program from the [master boot record]("http://en.wikipedia.org/wiki/Master_boot_record") (MBR), the first 512 bytes of the hard disk, and then transfers control to this code.
 The MBR contains GRUB stage 1. Given the small size of the MBR, Stage 1 does little more than load the next stage of GRUB (which may reside physically elsewhere on the disk). Stage 1 can either load Stage 2 directly, or it can load stage 1.5: GRUB Stage 1.5 is located in the first 30 kilobytes of hard disk immediately following the MBR. Stage 1.5 loads Stage 2.
 When GRUB Stage 2 receives control, it presents an interface to the user in order to select which operating system to boot. This normally takes the form of a graphical menu, although if this is not available or the user wishes further control, GRUB has its own command prompt, where the user can manually specify the boot parameters. GRUB can also be set to automatically load a particular kernel after a timeout period.
 Once boot options have been selected, GRUB loads the selected kernel into memory and passes control on to the kernel, which then continues to start itself. At this stage GRUB can also pass control of the boot process to another loader, using *chain loading*, for operating systems such as Windows that do not support the Multiboot standard. In this case, copies of the other system's boot programs have been saved by GRUB; instead of a kernel, the other system is loaded as though it had been started from the MBR. This may be yet another boot manager, such as the Microsoft boot menu, allowing further selection of non-Multiboot operating systems. (This behavior is often automatic when modern Linux distributions are installed "on top of" existing Windows systems, allowing the user to retain the original operating system without modification, including systems that contain multiple versions of Windows.)The important thing is that the grub menu - menu.lst - is on the root partition of the Linux installation. If grub stage 1.5 can't find stage 2, you get an error message - just as you did when you started the thread. To reinstall grub stages 1 and 1.5, we need to know the Linux root partition - hence this long process of deduction we've been through on this thread. The "root (hd1,1" 'points' stage 1.5 to sdb1 when we install it. I can only assume that the installation of grub went awry somehow when you installed Ubuntu 8.04, and that's why you got an error.

**Edit:** oh, by the way - forget about grub 2 for now. It's still in development. We're still using grub 0.9something.

---

### Post by Bandolin on 2008-08-21
OK I followed the commands you gave, and the terminal reported succeded.

I've rebooted and still get the same error message. 

I am really nervous now.

So, I tried the commands a second time from the live CD and when I type root (hd1,1) it gives me an error saying the partition does not exist. Funny, it didn't do that the first time I ran through it.

---

### Post by Bandolin on 2008-08-21
I take it (hd1,1) is grub speak for sdb1?

I too am curious as to why there is a MS Win XP on sda6. I do have a partion there of 10 gigs or so, but that's really only for storing temp files.

Would it be easier to just eliminate the linux partition completely and start from scratch?

At this point I just want my windows back.

Is it also possible to change the boot order so that Windows is the first option? Is it a simple matter of cutting and pasting inside the menu.lst file?

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> I take it (hd1,1) is grub speak for sdb1?

I too am curious as to why there is a MS Win XP on sda6. I do have a partion there of 10 gigs or so, but that's really only for storing temp files.

Would it be easier to just eliminate the linux partition completely and start from scratch?

At this point I just want my windows back.

Is it also possible to change the boot order so that Windows is the first option? Is it a simple matter of cutting and pasting inside the menu.lst file?

Yeah, just paste the windows partition's entries above the others. If you get a kernel update though, it will usually undo that though, so you'll have to do it again.

Or you could just change the number for the default option way up at the top. That would set the default to whichever partition you choose.

---

### Post by coffeecat on 2008-08-21
OK - first thing. If Ubuntu is on sdb2 - and it looks as though it is - and you followed my directions without making a mistake, you should not be getting an error 22. I am quite mystified.

However, there are a few things that don't add up. You have a 200Gb drive - sda - with an extended partition - sda1 - and one logical partition - sda5, but the sector numbers don't correspond. Also you have a menu.lst entry for Windows on sda6, a partition you don't have (seemingly), and you can't have a bootable Windows on sda6 anyway. (Not unless you do some really clever hacking.) So - is there anything else you can tell us about sda? What did you have on there before you installed Ubuntu 8.04?

And now sdb. You have two Linux partitions on that - sdb2 and sdb4. (Ignore the swap partition for now.) You think sdb2 is the Ubuntu root partition. Can you say anthing about sdb4? When you boot into the live CD, you can mount all hard disc partitions from System > Computer and have a look inside using the Nautilus file manager. What does it tell you?

By the way, if the worst comes to the worst, you can reinstall the Windows bootloader using a Windows install disc and the FIXMBR command, but I don't know whether it's possible to boot up Windows from the second disc using the Windows bootloader. I had always believed (but I might be wrong) that Windows C: must be on the 'master' drive, unless you use grub. Have you swapped the discs around at any time?

---

### Post by Bandolin on 2008-08-21
Here's the latest fdisk setup

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/sda2            7013        8228     9767520   83  Linux
/dev/sda3            8229        8352      996030   82  Linux swap / Solaris
/dev/sda4            8353        9729    11060752+  83  Linux
Warning: ignoring extra data in partition table 5

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eb87eb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       24321   195350400    5  Extended
/dev/sdb5               2        1942    15591051    7  HPFS/NTFS


---

### Post by coffeecat on 2008-08-21
> **guywithcable said:**
> Yeah, just paste the windows partition's entries above the others.

Oh dear! **Please** read the thread through before posting. We're having trouble getting grub to install to the mbr, so editing menu.lst at this point is not going to achieve anything. The OP is getting a grub error 22. Grub can't find the partition which menu.lst is on, so editing it won't help yet.

Have you any other suggestions, **guywithcable**? I'm almost out of ideas.

---

### Post by coffeecat on 2008-08-21
> **Bandolin said:**
> Here's the latest fdisk setup

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ea47d13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7012    56323858+   7  HPFS/NTFS
/dev/sda2            7013        8228     9767520   83  Linux
/dev/sda3            8229        8352      996030   82  Linux swap / Solaris
/dev/sda4            8353        9729    11060752+  83  Linux
Warning: ignoring extra data in partition table 5

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7eb87eb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       24321   195350400    5  Extended
/dev/sdb5               2        1942    15591051    7  HPFS/NTFS                      
```


Aaaaaaaaaaaaaaargggghhhhhhh! You've swapped the discs around. I can't hit a moving target.

---

### Post by tangibleorange on 2008-08-21
er yeah. i've been trying to follow this thread (but having trouble because ubuntuforums so slow) and there seems to be HUGE confusion between /dev/sda and /dev/sdb. i fear it may all be a misunderstanding. is the fdisk listed above actually copied and pasted straight from your liveCD terminal?

---

### Post by Bandolin on 2008-08-21
First of all let me thank you for sticking with me on this coffeecat.

If you look at my previous post you will see something strange. It looks like the sda and sdb entries have switched from the first one I did.

My 200 Gb drive has no bootable OS on it, its just storage.
My 80 Gb drive has Win XP and Ubuntu 8.04.

As for the sda6 entry I don't know enough about this stuff to realize its an anomaly so I'll trust you on that. And believe me any hacking on my part could not possibly be confused with being clever.

Prior to installing 8.04 I had 7.10 and it worked fine until I tried to change the monitor resolution (because I got this niffty new 22" Dell and I wanted to use native 1680 1050) and that totally screw up 7.10. I couldn't see anything, so I decided to upgrade 8.04 over it. Now during the installation process Ubuntu did ask me to make a root directory. So, I chose the partition that 7.10 was (AFAIK to the best of my knowledge). Figuring that 8.04 was intelligent enough to get rid of 7.10 for me and load up 8.04. I thought it strange that I never received a warning saying "Hey, you've already got an older version of Ubuntu, do you really want to replace it with this one?"

So, that's my story.

sda2 & sda4 both have linux on them according to my previous post. I'm wondering if somehow 7.10 is still there causing confusion.

@tangibleorange
It is a direct copy.

@coffeecat
I swear, I have not opened my case and changed anything.

---

### Post by tangibleorange on 2008-08-21
based on previous posts, might i recommend this /boot/grub/menu.lst:

```
#GRUB config file

default 0

timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```

paste exactly that into your /boot/grub/menu.lst, save, and reboot. then try booting XP, and then ubuntu.

EDIT:

if your 200GB drive is storage, is it USB? If so, could you remove it when booting?

---

### Post by guywithcable on 2008-08-21
This should work then, right guys?

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb6
# possibly unnecessary
title		Microsoft Windows XP Professional
root		(hd1,5)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1 
```

It looks like you've switched your hard drives' places, so I switched them in this menu.lst for you.

---

### Post by Bandolin on 2008-08-21
@tangibleorange
The 200 Gb drive is internal. I could remove it but it would be a real pain.

I've been to Edingurgh BTW. Love your town. Would loved to have seen more of it but when I visited apparantly a royal was in town and a lot of the scenic places were blocked off.

---

### Post by guywithcable on 2008-08-21
> **tangibleorange said:**
> based on previous posts, might i recommend this /boot/grub/menu.lst:

```
#GRUB config file

default 0

timeout 10

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```paste exactly that into your /boot/grub/menu.lst, save, and reboot. then try booting XP, and then ubuntu.

EDIT:

if your 200GB drive is storage, is it USB? If so, could you remove it when booting?

You took out the recovery option... and memtest.

---

### Post by tangibleorange on 2008-08-21
> **Bandolin said:**
> @tangibleorange
The 200 Gb drive is internal. I could remove it but it would be a real pain.

I've been to Edingurgh BTW. Love your town. Would loved to have seen more of it but when I visited apparantly a royal was in town and a lot of the scenic places were blocked off.

ah cool you've been to edinburgh!
but did my /boot/grub/menu.lst let you boot :P?

---

### Post by tangibleorange on 2008-08-21
> **guywithcable said:**
> You took out the recovery option... and memtest.

yeah but what is the point in them (temporarily) when he can't even boot normally? if he gets it working, we can add them in :)

---

### Post by Bandolin on 2008-08-21
@tangibleorange
I'm not quite sure where in the grub text file I should paste that.

@guywithcable
Are you sure what you wrote will work? Is it simply a switching thing?

---

### Post by tangibleorange on 2008-08-21
> **Bandolin said:**
> @tangibleorange
I'm not quite sure where in the grub text file I should paste that.

@guywithcable
Are you sure what you wrote will work? Is it simply a switching thing?

delete all the writing in the file and then just paste that. you might think it looks stupidly small, but actually 90% of the /boot/grub/menu.lst in ubuntu in just comments. that is all you need (for now). if it works, you will be able to modify it later with more options :).

---

### Post by Bandolin on 2008-08-21
Crap! It won't let me change it. It says I don't have enough permissions.

---

### Post by tangibleorange on 2008-08-21
> **Bandolin said:**
> Crap! It won't let me change it. It says I don't have enough permissions.

open up a root nautilus:

```
gksu nautilus
```

and then find the file and edit/save it.

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> @tangibleorange
I'm not quite sure where in the grub text file I should paste that.

@guywithcable
Are you sure what you wrote will work? Is it simply a switching thing?

It should work as long as grub is installed correctly. Either of our menu.lsts will work. You could also use "gksu gedit" and open it from there.

---

### Post by Bandolin on 2008-08-21
OK the nautilus thing worked.
I can boot in Ubuntu 8.04 but NOT Windows XP. It is still telling me the partition does not exist.

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> OK the nautilus thing worked.
I can boot in Ubuntu 8.04 but NOT Windows XP. It is still telling me the partition does not exist.

Are you using mine, because if you are, you'll have to boot the second of the two Windows entries. I noted in the menu.lst that one of the entries was possibly unnecessary. You should remove that one. It is the first Windows entry. The second one is the correct one.

---

### Post by guywithcable on 2008-08-21
You can try the following two menu.lsts. One of them should allow you to boot into Windows.

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
# kopt=root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
``````
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
# kopt=root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
```

---

### Post by Bandolin on 2008-08-21
sorry to be such a blonde, but which one exactly should I remove?

OK hold on, you're posting faster than I can reply.

---

### Post by Bandolin on 2008-08-21
I'm trying one of your menu.lst but now I can no longer see the linux boot partition. It has disappeared from my list of available Places. :(

Man if its not one thing its another.

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> I'm trying one of your menu.lst but now I can no longer see the linux boot partition. It has disappeared from my list of available Places. :(

Man if its not one thing its another.

Are you in the LiveCD or have you booted into Ubuntu from your hard drive? If you have booted from your hard drive, then it will be called Filesystem, and is available from "Computer" in Places.

---

### Post by Bandolin on 2008-08-21
Ok I managed to mount the sda2 using terminal.

@guywithcable
Just read your last post. Man you must think I'm friggin' stupid. But I'm completely new to Linux. If it helps, just think that you're helping someone with special needs. What they used to call a retard. :)

---

### Post by Bandolin on 2008-08-21
All righty, I tried your first example menu.lst and the same thing. I can boot into Ubuntu but the one Microsoft XP listing simply hangs on:
Starting up...

Now trying your second example.

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> Ok I managed to mount the sda2 using terminal.

@guywithcable
Just read your last post. Man you must think I'm friggin' stupid. But I'm completely new to Linux. If it helps, just think that you're helping someone with special needs. What they used to call a retard. :)

Don't feel bad. Everyone starts out that way. I was searching for the C: drive for a while the first time I ever booted into Linux. :)

Can you boot into Windows yet?

---

### Post by Bandolin on 2008-08-21
@guywithcable
Dude YOU DA MAN! Your second example worked I'm in like Flynn in both Ubuntu & Windoze.

If you're not tired of helping me. I'd like to make Windows the first option on boot. Is it a copy/paste thing in menu.lst? Simply placing the Windows before the Linux?

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> @guywithcable
Dude YOU DA MAN! Your second example worked I'm in like Flynn in both Ubuntu & Windoze.

If you're not tired of helping me. I'd like to make Windows the first option on boot. Is it a copy/paste thing in menu.lst? Simply placing the Windows before the Linux?

Here you go, this will list Windows as the first option. :) If you like, you can give me a thanks. Theres a button with a little star below my post to the right.

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
# kopt=root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1



# This is a divider, added to separate the menu items.
title        Linux operating systems:
root

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=cfc2559b-76cf-4f65-95d3-d5d40668c3db ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by guywithcable on 2008-08-21
You should also back up menu.lst to something like menu.lst.bak in case anything happens in the future and you need to restore it.

---

### Post by Bandolin on 2008-08-21
Oh, yeah. Believe me I've got like ten of these suckers. I'm deleting the one's that didn't work though.

Any you have been thanked.

---

### Post by guywithcable on 2008-08-21
> **Bandolin said:**
> Oh, yeah. Believe me I've got like ten of these suckers. I'm deleting the one's that didn't work though.

Any you have been thanked.

All right. That's my first thanks. :) Glad I could help. Have a good day.

---

