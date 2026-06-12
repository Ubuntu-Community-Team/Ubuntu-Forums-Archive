---
title: "/boot/grub/menu.list"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by 16sinker on 2009-04-08
My /boot/grub/menu.list does not contain the latest kernel for Jaunty beta. That is linux generic 2.6.28-11. How do I update menu.list to contain this latest kernel which I took in an update this morning. I overlooked a prompt about menu.list during the update by selecting forward instead of other option which would probably taken care of it. Any help is appreciated.

---

### Post by SuperSonic4 on 2009-04-08
I believe the kernel is in /boot and is vmlinuz-2.6.28-11 root=UUID <your uuid>
My one for kubuntu jaunty beta is below

```

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
uuid		916c7587-aee8-4444-a84f-f7124d72d300
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=916c7587-aee8-4444-a84f-f7124d72d300 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
```

to find out your UUID type ```
ls -lF /dev/disk/by-uuid/
```

---

### Post by 16sinker on 2009-04-08
I ran the command ls -lF /dev/disk/by-uuid/ and this is the output.

bofus66@ubuntudell:~$ ls -lF /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2009-04-08 09:31 8010ebc6-ff8a-4aff-986a-ce821319d703 -> ../../sda1
lrwxrwxrwx 1 root root 10 2009-04-08 09:31 cc054c0b-f483-406a-9466-981fdfee53b0 -> ../../sda5
bofus66@ubuntudell:~$ WTF?

---

### Post by SuperSonic4 on 2009-04-08
That command tells you what the UUID of each disk is so you can put it up in the kernel line on the menu. If /dev/sda1 is root then you'd put ```
/boot/vmlinuz-2.6.28-11-generic root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro quiet splash
```

It'd be wise to back up your menu list too ```
sudo cp -v /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

---

### Post by 16sinker on 2009-04-08
Thanks for your help Supersonic. Ibacked up as you advised but when I ran the boot/vmlinux code I got permission denied. I'm going to have to get back on this later. Thanks again.

---

### Post by SuperSonic4 on 2009-04-08
You need to be root to edit the grub menu ```
gksu gedit /boot/grub/menu.lst
``` should open it with root permissions in ubuntu

---

### Post by 16sinker on 2009-04-08
> **SuperSonic4 said:**
> You need to be root to edit the grub menu ```
gksu gedit /boot/grub/menu.lst
``` should open it with root permissions in ubuntu

Thanks again. I'll have to work on it this evening.

---

### Post by 16sinker on 2009-04-08
I know how to access the boot/grub/menu.list with alt=f2 and the command:
gksu gedit /boot/grub/menu.lst, but I don't know how to add the new kernel linux generic 2.6.28-11. The kernel,headers and such are in synaptic and are installed there. I need to know the proper command to edit (add this kernel) to my menu.list or should I uninstall everything relative 2.6.28-11 and then reinstall in synaptic. Any help would be appreciated.

---

### Post by plucky on 2009-04-08
From a terminal, try ```
sudo update-grub
``` which should look at your /boot directory and create menu.lst entries for eack kernel it finds.

Checkout ```
man update-grub
``` for what the command does.

Please make a copy of your menu.lst file that you can use restore from in case it goes wrong.

Good luck

---

### Post by 16sinker on 2009-04-08
This is the output of sudo update-grub:
bofus66@ubuntudell:~$ sudo update-grub
[sudo] password for bofus66: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Which looks like what I need.Does the command "man update-grub" add this output to my menu.list or will I have to do it manually?

---

### Post by lisati on 2009-04-08
<aside>It's > /boot/grub/menu.**lst** NOT > /boot/grub/menu.**list**
</aside>

---

### Post by 16sinker on 2009-04-08
Thank you for pointing that out. My bad. If I had copied and pasted the command in terminal I think I would have used menu.lst. Thanks again.

---

### Post by fdisk-o on 2009-04-08
> **16sinker said:**
> This is the output of sudo update-grub:
bofus66@ubuntudell:~$ sudo update-grub
<snip>
...
</snip>
Found kernel: /boot/vmlinuz-2.6.27-14-generic
<snip>

Take a look at your current(newly created) boot list by doing the following:
cat /boot/grub/menu.lst

Look for a menu option with 2.6.27-14-generic in it. If it's there, you do indeed have what you need. You should look at how it's structured to see that you will boot to the latest kernel. The default image to boot is in the "default    <somenumber>" line and if the <somenumber> is 0 then that corresponds to the information directly following the first "title" line. 

use "man grub" to see further how grub works.

---

### Post by 16sinker on 2009-04-08
Should I uninstall Jaunty beta and then reinstall, making sure that I get the updates including linux generic 2.6.28-11 and following the prompt to add to my menu.lst, which is my problem to begin with. I overlooked the menu.lst prompt by choosing the highlighted option "forward" instead of "add." The generic kernel 2.6.28-11 and the headers are installed in synaptic, but I don't know how to update my menu.lst. In terminal I ran sudo update-grub and see the new kernel, but am confused as to how to edit menu.lst. I'm still booting from the Intrepid kernel 2.6.27-14. Please advise.

---

### Post by 16sinker on 2009-04-08
> **fdisk-o said:**
> Take a look at your current(newly created) boot list by doing the following:
cat /boot/grub/menu.lst

Look for a menu option with 2.6.27-14-generic in it. If it's there, you do indeed have what you need. You should look at how it's structured to see that you will boot to the latest kernel. The default image to boot is in the "default    <somenumber>" line and if the <somenumber> is 0 then that corresponds to the information directly following the first "title" line. 

use "man grub" to see further how grub works.

I do indeed see 2.6.27-14 generic and 2.6.27-11 generic, however I don't see a reference to the 2.6.28-11 generic which I am wanting to add to this menu.lst. I have my terminal open on my other work space with the output of command: cat /boot/grub/menu.lst. How do I add the new Jaunty kernal to this menu.lst?

---

### Post by 16sinker on 2009-04-08
This is the out put of: cat /boot/grub/menu.lst.

bofus66@ubuntudell:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8010ebc6-ff8a-4aff-986a-ce821319d703

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		8010ebc6-ff8a-4aff-986a-ce821319d703
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		8010ebc6-ff8a-4aff-986a-ce821319d703
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		8010ebc6-ff8a-4aff-986a-ce821319d703
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		8010ebc6-ff8a-4aff-986a-ce821319d703
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=8010ebc6-ff8a-4aff-986a-ce821319d703 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic



title		Ubuntu 8.10, memtest86+
uuid		8010ebc6-ff8a-4aff-986a-ce821319d703
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
bofus66@ubuntudell:~$ 

I see the default number is 0, but have no idea how to make linux kernel 2,6.28-11 my default boot kernel.

---

### Post by meierfra. on 2009-04-08
This should generate a new menu.lst containing your new kernel:

```

cd /boot/grub
sudo mv menu.lst menu.lst.backup
sudo update-grub
```

---

### Post by 16sinker on 2009-04-08
> **meierfra. said:**
> This should generate a new menu.lst containing your new kernel:

```

cd /boot/grub
sudo mb menu.lst menu.lst.backup
sudo update-grub
```

This is the output of that command:
bofus66@ubuntudell:~$ cd /boot/grub
bofus66@ubuntudell:/boot/grub$ sudo mb menu.lst menu.lst.backup
sudo: mb: command not found
bofus66@ubuntudell:/boot/grub$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

I have restarted and clicked esc. to get to bootloader. 2.6.28-11 doesen't appear.

---

### Post by meierfra. on 2009-04-08
Sorry, typo.. It needs to be "mv" not "mb" (I fixed my orginal post)

---

### Post by 16sinker on 2009-04-08
> **meierfra. said:**
> Sorry, typo.. It needs to be "mv" not "mb" (I fixed my orginal post)
Don't worry about the typo-I do it all the time. I ran the corrected code and guess what? SUCCESS!!! I am now booting with the new Jaunty kernel 2.6.28-11. That is the code I've needed all day. Thank you, thank you, thank you Meierfra. I'm so relieved I'm going to bed now. Solved!!!

---

