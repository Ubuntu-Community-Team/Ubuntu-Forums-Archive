---
title: "PANIC: CPU too old for this kernal"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Imoen_tw on 2007-12-08
The Computer Specs
Model is a Compaq 7478 with the following specs:
• 533 MHz AMD K-6(r)
• 97 MHz system bus
• 512 MB 100 MHz SyncDRAM - 8 MB dedicated for video memory
• 30.0 GB 1 UltraDMA hard drive
• DVD-ROM Drive1
• CD-RW Drive2
• 512KB L2 Pipeline Burst Cache
• Trident Graphics Integrated in the ViaChipset.
• ESS Allegro PCI Audio

I finally figured out why it just kept restarting on install so I fixed that. Then found that I can't boot from CD drive on the computer, so I took the hard drive out, put it in another computer and installed ubuntu 7.10 server. When finished I put it back in the computer, load it up and get PANIC: CPU too old for this kernal.

I believe I read the system requirements and there was nothing that said the cpu was too old. How is this fixed?

---

### Post by Whiffle on 2007-12-08
I *think* the problem is that the ubuntu server kernel is built for i686 architecture, which isn't what your 533 MHz AMD is.  I ran into the same issue when setting up my old compaq amd 450mhz laptop as a server.  I solved it by installing the 386 kernel, works fine now.

---

### Post by Imoen_tw on 2007-12-08
Could you tell me where I can get that and information to install it? This is my first try using non-Windows so installing isn't something I'm good at yet. Thanks for your help.

---

### Post by PmDematagoda on 2007-12-08
Try using Synpatic to install the i386 kernel, it can be usually found with the word "linux" in front of it.

---

### Post by Imoen_tw on 2007-12-09
I'm not following how I get this to work.

Since I only have the option to boot from the floppy or hard drive is there a way that I can boot ubuntu from the floppy? It seems that according to [http://ubuntuforums.org/archive/index.php/t-4452.html](http://ubuntuforums.org/archive/index.php/t-4452.html) if I do that and install ubuntu on the hard drive from the computer that will run it the correct kernal will be installed.

---

### Post by PmDematagoda on 2007-12-09
I actually meant that you could install the proper kernel by using Ubuntu on the previous PC then use it on your old PC.

---

### Post by Imoen_tw on 2007-12-09
That's not an option. That pc isn't mine it's my boyfriends and it's built for gaming... way too much money put into it to become a server for forums.

---

### Post by PmDematagoda on 2007-12-09
No, no, you mistook my idea, use Ubuntu on your boyfriend's PC to install the i386 kernel, then use it on your PC.

---

### Post by Imoen_tw on 2007-12-09
OK sorry. How do I do that?

---

### Post by PmDematagoda on 2007-12-09
Do:-
```

sudo apt-get install linux-386

```

To install the kernel, that should do it.

---

### Post by Imoen_tw on 2007-12-09
it's asking me for the ubuntu-server 7.10 i386 cd. I put in the cd I installed ubuntu with and it tells me the same thing. Is there another cd I need to make and if so where do I find it?

---

### Post by PmDematagoda on 2007-12-09
Hmm, you will have to use vim or nano to edit the sources.list file, a question, have you used vim or nano before?

---

### Post by Imoen_tw on 2007-12-09
I haven't used anything but windows and red hat before, and I didn't really use red hat because I couldn't figure it out.

---

### Post by PmDematagoda on 2007-12-09
Well, if you know how to use vim or nano, open the sources.list file for editing using(I'm using vim as an example):-

```
sudo vim /etc/apt/sources.list
```

Then comment out the CD-ROM repository by typing # in front of it, then save the file and then do:-

```
sudo apt-get update
```

Then try installing the kernel again.

If you want to know how to use vim, you can refer to this [page]("http://www.vim.org/htmldoc/help.html"), if you want to know how to use nano, then you can refer to this [page]("http://www.tqnyc.org/tutorial/nano/").

---

### Post by Rhubarb on 2007-12-09
To stop gutsy server from trying to access the gutsy installer CD when ever you try to download a package:
```
sudo nano /etc/apt/sources.list
```
Find this line (it should be up the top somewhere):
"deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted"
and put a "#" infront of it so it looks like this:
```
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```
Press Ctrl + O, enter, to save the changes
Press Ctrl + X to exit out of the nano text editor

Then run:
```
sudo aptitude update
sudo aptitude install linux-generic
```
This will enable your old AMD PC to boot up without getting a Kernel Panic.
To boot up now select the generic linux kernel when booting up ubuntu server.
To make ubuntu server use the generic linux kernel to boot up as default (a very good idea to do):
```
sudo nano /boot/grub/menu.lst
```
Scroll right down to the bottom of the page, after you see "## ## End Default Options ##" delete the 1st two blocks that say something about booting linux-server, so you are left with a menu.lst that contains only the generic kernels.

It should look something similar to this:
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
# kopt=root=UUID=bd13603a-5467-4a55-a83e-1e4f49a80028 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd13603a-5467-4a55-a83e-1e4f49a80028 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bd13603a-5467-4a55-a83e-1e4f49a80028 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Press Ctrl + O, enter, to save the changes
Press Ctrl + X to exit out of the nano text editor

Then you are free to put the hard drive back into your old AMD box and ubuntu server will boot up nicely for you (I did exactly this for my old PC yesterday to get ubuntu server running on it).

---

### Post by Imoen_tw on 2007-12-10
You guys are great. It now loads on my old computer. Thank you very much for the help and great directions for someone as clueless as me.

---

### Post by PmDematagoda on 2007-12-10
No problem, we are glad to help:).

And a lot of credit to Rhubarb for providing a lot of the necessary information and help which very much simplified the process, nice going Rhubarb:lolflag:.

---

### Post by zany on 2007-12-14
i cannot boot into ubuntu. i loads and goes to the PANIC: CPU too old for the kernel.  Is there another way I can install ubuntu with a different kernel?

Thanks

---

