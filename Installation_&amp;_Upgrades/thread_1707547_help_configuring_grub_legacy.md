---
title: "help configuring grub legacy"
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by boarder428 on 2011-03-15
I need help configuring grub!  After I installed Ubuntu I get th following error when trying to load Win Xp. "Windows could not start because the following file is missing or corrupt: <windows root>\system32\hal.dll. Please re-install a copy of the above file."

I made the mistake of not installing windows on the first partition.  When creating/deleting partitions with windows cd I did not want to delete my data partition so when I deleted my other partitions the partitioner re-named my data partition as C and I did not catch this until after installing windows.  I cannot figure out how to correctly map/swap the partitions if somebody could give me some advice?
[IMG]http://img37.picoodle.com/i53f/cjb428/1719_d8f_u7am.png[/IMG]
```
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
# kopt=root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=366e7827-bfde-42f9-b853-d7808616253b

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
title		Ubuntu 9.04, kernel 2.6.28-19-generic
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=366e7827-bfde-42f9-b853-d7808616253b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		366e7827-bfde-42f9-b853-d7808616253b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by mörgæs on 2011-03-16
I can't help with the Windows questions, but your Ubuntu (9.04) is unsupported and therefore a security threat. Best is to get rid of that and install 10.04 or 10.10.

---

### Post by coffeecat on 2011-03-16
Your Windows issue is that you have Windows on a logical partition and Windows cannot boot from a logical partition. Your grub menu is trying to boot Windows from sda1 which you say is your data partition, but if you look at your Gparted screenshot, you'll see the boot flag is set on sda1.

Windows would be able to work in the logical partition sda5 if it had boot files on a primary partition. So the Windows boot files must either be in your sda1 data partition, or were on the first physical partition (which is now, confusingly, sda4) before you installed Ubuntu to it.

To get a better idea of what is going on and where the Windows boot files are, if they are anywhere, boot up Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the contents of the RESULTS.txt file in code tags.

---

### Post by boarder428 on 2011-03-16
Yeah coffecat, you are correct, I figured that out after browsing thru the data partition I found the windows bootfiles there.  I don't exactly know how they got there unless grub moved them or changed the partition type when installing ubuntu because windows booted before the ubuntu install.  I ended up just re-partitioning and re-installing the os's to correct the problem.  

Thanks for the advice mörgæs, I know 9.04 is unsupported, this pc has a problem running any kernels past Jaunty, which I have never been able to come up with a rerason for so I just stick with what works.  Same reason it has win xp on it instead of 7, I use what's "know good" with this particular pc.  I'm not worried about security, windows itself throws security out the door! LOL!

It performs best with these 2 os's!;)

---

