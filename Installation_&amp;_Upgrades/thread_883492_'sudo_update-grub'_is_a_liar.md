---
title: "'sudo update-grub' is a liar"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by phil the dill on 2008-08-08
Hi,

Following advice on a Linux audio forum, I used synaptic to install parts of UbuntuStudio, specifically the audio part. 

In doing that, synaptic installed a realtime kernel, which I hadn't realised was going to happen. During the install process, a dialog popped up asking me what I wanted to do with the grub menu. Not knowing what the options involved, I stuck with the default to keep the current grub menu. 

I can now see in synaptic that the realtime kernel is installed, and the file 'initrd.img-2.6.24-19-rt' is in the /boot directory, but it doesn't show in the grub menu.

I saw elsewhere on this forum a solution to this problem: run 'sudo update-grub'. I did this, and this is the output:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-rt
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

The problem is that menu.lst *is not* updated - only the generic kernels are present in the boot menu after this 'update'. Why is 'sudo update-grub' saying the menu.lst file has been updated when it hasn't? And how do I get the realtime kernel to show in the grub menu?

Thanks.

---

### Post by cariboo on 2008-08-08
When you run update-grub it only updates the mbr, you usually run update-grub after modifying menu.lst. The easy way to modify menu.lst and change boot options is to install startupmanager. It is available in the repositories you can use Add/Remove Programs, Synaptic Package Manager or the command line to install it.

Jim

---

### Post by phil the dill on 2008-08-08
cariboo907:

Thanks for the quick response, but I'm afraid it's only left me more confused.

You said "When you run update-grub it only updates the mbr" but the output when I ran update-grub clearly said 'Updating /boot/grub/menu.lst' and it didn't say anything about the mbr - are you sure it's 'update-grub' you're referring to?

And I have StartUp-Manager installed, but it only gives the option of changing the default operating system in the grub menu. It doesn't give any option to add a new item to the grub menu.

---

### Post by sisco311 on 2008-08-08
post the content of the /boot/grub/menu.lst file

---

### Post by tropdoug on 2008-08-08
Hi Phil

I am a relative newbie so don't have a lot of knowledge, but I seem to recall a few others mentioning the problem you have with update-grub not working. 

If its any help I had to add in the relevant lines to dual boot when I reinstalled windows  (only for a short while lol) this is what I did

Boot the system from a live disc, then open a terminal and type 

```
sudo gedit /media/whichever dev your root files are on/boot/grub/menu.lst
``````
sudo cp /media/dev.../boot/grub/menubackup.lst
```Use whatever editor is your preferred one if gedit is not yours. Then simply add the lines pointing to your new kernel. The old ones will be there, so if you need another entry in the menu list copy the old one, paste it in as a new section and alter the img numbers to suit. below is my entry for 7.10 yours should be similar. The new entry should be the same except the img and version numbers

title        Ubuntu 7.10, kernel 2.6.22-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.22-15-generic root=UUID=b3b727c5-b145-4494-aa31-aa986f715b52 ro
initrd        /boot/initrd.img-2.6.22-15-generic    
quiet        splash


Hope that makes sense to you , and works. (PS I am not sure if you can boot into your system or not from your original post. If you can then just use your editor without booting from the live cd) 

Doug
 
</div>

---

### Post by phil the dill on 2008-08-08
Thanks for the response.

Ok, here's the 'menu.lst' file contents:

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,2)

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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I just noticed something in the /boot directory - the 'vmlinuz-2.6.24-19-generic' and 'vmlinuz-2.6.24-16-generic' each have a corresponding 'abi-' file ie. 'abi-2.6.24-19-generic' and 'abi-2.6.24-16-generic', but there is no corresponding 'abi-' file for the file 'vmlinuz-2.6.24-19-rt'. Is that significant?

---

### Post by sisco311 on 2008-08-08
add the following entry to the file:

>  title        Ubuntu 8.04.1, kernel 2.6.24-19-rt
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-rt root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-rt
quietto edit the menu.lst press Alt+F2 and run:
```
gksu gedit /boot/grub/menu.lst
```save it and try to boot with the new kernel.

---

### Post by phil the dill on 2008-08-08
tropdoug: yes I can boot into Ubuntu ok with the other kernels, it's just that the newly installed kernel doesn't show up in the grub boot menu.

sisco311: ok I added the lines you suggested to 'menu.lst' and rebooted, and I can get Ubuntu to start up using the realtime kernel. There was a lot of text output during the boot process, including some stuff relating to the VirtualBox installation and something about installing modules. The problem now is that the graphics drivers don't load in the realtime kernel operating system. 

If I install new graphics drivers after I've booted with the realtime kernel, will it overwrite the drivers I currently use for the generic kernel? I'm using the Envy-NG drivers for an Nvidia 6800GT card with dual monitors, plus a Wacom graphics tablet, and it took me about 3 weeks to get all the xorg stuff working, so I don't want to mess it up.

Maybe I should just uninstall the realtime kernel and forget about using the UbuntuStudio programs. I thought I was just installing a few apps, I didn't realise it was going to turn into such a fundamental change to the operating system.

---

### Post by Herman on 2008-08-08
```
## default grub root device
## e.g. groot=(hd0,0)
# groot=[COLOR=Red]**(hd2,2)**[/COLOR]
```

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
**root		(hd0,2)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=074b342f-dc8e-0368-5f23-87c66225c033 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

```
## default grub root device
 ## e.g. groot=(hd0,0)
 # groot=[COLOR=Sienna]**(hd0,2)**[/COLOR]
```

Probably the reason why your update-grub script isn't working is because your Debian Automagic Kernels List has the wrong hard disk number listed for grub's default root device.
If you fix that then your grub-install script will probably start working okay. :)

---

### Post by phil the dill on 2008-08-08
Herman: The hard disk number is correct for my setup, although during installation I did discover an inconsistency in the way Ubuntu recognises hard drives. I have two other hard drives in a RAID-0 configuration that I use for data storage. I found that they were recognised as drives 0 and 1 by whatever it is that creates the initial grub menu, making the OS drive '2'. But the boot loader itself does NOT see the raid drives, so Ubuntu failed to boot until I manually edited the grub menu to make it boot from drive 0.

Anyway, since the initial installation of Ubuntu, I've upgraded the kernel from 2.6.24.16 to 2.6.24.19, and that worked without a problem and without having to edit the grub menu, so I would expect that installation of the realtime kernel would follow the same pattern - but that's just a guess on my part.

---

### Post by Herman on 2008-08-08
> I have two other hard drives in a RAID-0 configuration  Oh, okay, sorry.
I don't know anything about RAID.  I guess your update-grub script doesn't either. Sorry for any inconvenience then.
> Anyway, since the initial installation of Ubuntu, I've upgraded the kernel from 2.6.24.16 to 2.6.24.19, and that worked without a problem and without having to edit the grub menu, so I would expect that installation of the realtime kernel would follow the same pattern - but that's just a guess on my part. Oh, I would expect so too then. I don't know now, maybe someone else can help?

---

