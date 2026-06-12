---
title: "dual boot help"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by maddoggschank on 2008-09-19
Dont know what to do. Just installed vista fine,it worked well (as good as a ms os works) then installed ubuntu after giving it its own partition but at the restart i do not get the option to boot from eather vista or 8.04, it goes straight to ubuntu. I am not at all smart when it comes to computers, esp. command line, but i can cut and past.  vista is formated to a NTSF partition but i dont think ubuntu is, could this cause the problem? 
this might be a dumb question but dont the 2 OSs' need their own partition? or can they be installed on the same partition?
It is a self built home desktop, i installed the two systems on a 250 gb ata hdd, i have a 150 sata that i wanted to intall them on but i did somthing and jacked that drive all up i can only boot the pc on that drive from a live cd, i can find out the nitty gritty if needed.
Any help is greatly appreciated!

---

### Post by daniel.hodge on 2008-09-19
I'm no expert when it comes to computers either. I had the same problem with a dual boot. I had a lot of headaches getting dual boot to work. I'll list the steps I took, hopefully it will help.

Install Windows, letting it rewrite what it needs to. Once installed, go into the partition editor (control panel - search for "partition edit" or such in the search box). Once in the editor, you should see that Windows has taken over the partition. If you right click on that you should be able to "shrink" the volume. Shrink it by whatever you want. Once that completes, pop in the Ubuntu live cd and restart, making sure your pc boots from cd.
Once in the live cd, click to install. When the window to select partitions comes up, select "Manual". Find the "shrink" volume you created in Windows (it will either be unallocated or formatted as ntfs or whatever you chose to format is as when you shrunk it). Choose that partition, making sure the mount point is set to " /", and click to install. 
When linux finishes its install, it should restart for you. If all goes well, you should have a screen that will allow you to choose between Ubuntu or Windows (Longhorn Loader). 

I hope this helped.

---

### Post by nvance on 2008-09-19
Daniel did a great job of summing up the dual boot!!  When I have done a dual boot from Hardy 8.04.1 I let Ubuntu do the partitioning for me.  When that part comes up during the install it found the Windows partition and I was able to grab the slider bar to resize the partition to what I wanted for Windows and the rest was left for good ole Ubuntu.  Once the install is complete Grub will initiate and give you the option for Ubuntu or Windows (as Daniel stated).  

Good Luck and enjoy.

---

### Post by caljohnsmith on 2008-09-19
> **maddoggschank said:**
> ...but at the restart i do not get the option to boot from eather vista or 8.04, it goes straight to ubuntu.
I think that most likely means that the "hiddenmenu" option is turned on in your Grub menu, so that you don't see the Grub menu at start up and instead boot directly into Ubuntu. Next time you start up, press "ESC" repeatedly and you will get the Grub menu if that is your case. You definitely don't need to do a full reinstall to fix that problem.

---

### Post by maddoggschank on 2008-09-19
I pressed esc and it did take me to the boot menu, but vista was not an option just ubuntu 8.04 and the safe mode, I am confused do i need to re-install ubuntu on the same partition as vista in order for grub to see them both? Is that even possable? if not then how can i get both to be recognized on startup?
 you guys are answering questions thanks!

---

### Post by Bucky Ball on 2008-09-19
Yes, they do need separate partitions. Windows can be installed on NTFS or FAT (not sure if Vista uses FAT though). Linux (Ubuntu) installs on an EXT3 partition.

You are looking pretty good to go and you might try this for now:

**[www.supergrubdisk.org]("http://www.supergrubdisk.org")**

Download, burn and reboot from the cd. Should find both operating systems and set up their boot for you. Then you can learn a bit more about how the Grub works, but this should get you up for now with a choice at the boot. :)

* Update: [quote=maddoggschank]do i need to re-install ubuntu on the same partition as vista in order for grub to see them both?[/quote]

Definitely not. Caljohnsmith's post looks like a good option.

---

### Post by caljohnsmith on 2008-09-19
> **maddoggschank said:**
> I pressed esc and it did take me to the boot menu, but vista was not an option just ubuntu 8.04 and the safe mode, I am confused do i need to re-install ubuntu on the same partition as vista in order for grub to see them both? Is that even possable? if not then how can i get both to be recognized on startup?
 you guys are answering questions thanks!
OK, that's great news, just boot into Ubuntu like you did before, go to the menu Applications > Accessories > Terminal to get a terminal, and do the following:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```
Post the output of the above commands. And no, I definitely would not reinstall Ubuntu at this point since I don't think it is necessary; once you give the above commands, we can tell you how to boot Vista.

---

### Post by maddoggschank on 2008-09-19
Ok thanks ill try that and let you know.

---

### Post by maddoggschank on 2008-09-19
here it is.....

abe@abe-desktop:~$ sudo fdisk -lu
[sudo] password for abe: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7aa21749

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   482335559   241167748+  83  Linux
/dev/sda2       482335560   488392064     3028252+   5  Extended
/dev/sda5       482335623   488392064     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x100f59dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   228412169   114206053+  83  Linux
/dev/sdb2       228412170   234436544     3012187+   5  Extended
/dev/sdb5       228412233   234436544     3012156   82  Linux swap / Solaris
abe@abe-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=9009bcca-4def-45d6-851f-516aa7ee0c33 ro

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9009bcca-4def-45d6-851f-516aa7ee0c33 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=9009bcca-4def-45d6-851f-516aa7ee0c33 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
abe@abe-desktop:~$

---

### Post by caljohnsmith on 2008-09-19
I really hate to be the bearer of bad news, maddoggschank, but both of your HDDs only have Linux partitions; it looks like you overwrote your Vista partition. :( I hope you didn't have any documents or files in Vista that were too valuable, because there's probably not a lot of hope recovering them since you mistakenly overwrote the Vista partition with Linux.

---

### Post by maddoggschank on 2008-09-19
no prob. i did this to learn, i had just installed vista.

i could have swore that i installed 8.04 on a different partition

so can i install vista with ubuntu already installed or should i start over wipe everything out and start with vista?

---

### Post by caljohnsmith on 2008-09-19
> **maddoggschank said:**
> no prob. i did this to learn, i had just installed vista.

i could have swore that i installed 8.04 on a different partition

so can i install vista with ubuntu already installed or should i start over wipe everything out and start with vista?
Both your HDDs have Linux partitions; do you know which HDD you are booting from? I suppose if I were you, I would partition one of your HDDs so that you have both Vista and Ubuntu on the same HDD (they each need their own partitions), and then I would keep your other HDD entirely for storage and all your files. And since everything is newly installed anyway, I would go ahead and wipe the HDD clean and just start over: make three partitions, one for Vista, one for Ubuntu, and one for swap space. Then install Vista first, after that install Ubuntu. Does that sound like what you would want to do?

---

### Post by maddoggschank on 2008-09-19
ya that is what i was originally trying to set up, but i have learned a lot thus far. Thanks again! I will try and post how it all goes.

---

