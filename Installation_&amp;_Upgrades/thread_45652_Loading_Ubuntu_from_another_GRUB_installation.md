---
title: "Loading Ubuntu from another GRUB installation"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by lance_delacroix on 2005-07-01
Hi,

Before I ask my question, I'd like to say that the help I have received here has been top-notch!  Thanks to all.

I had Kubuntu installed and booting, but then I changed the partition from primary to extended and lost GRUB functionality.  All I get now is the legend "GRUB" on a blank screen.

I am booting from BootItNG (a bootloader/partition manager) on a dedicated partition.  BootItNg chain-loads whatever bootloaders (ntldr, GRUB, etc.) I select.  It cannot boot Linux directly.  

I have Windoze and SimplyMepis installed.  I can get to Mepis from BootItNg by selecting GRUB on the Mepis root partition, from which I can go to either Mepis or Windoze.  Or, I can get to Windoze by selecting ntldr in BootItNg.

I want to add Kubuntu to my Mepis-root GRUB menu.  I know what partition Kubuntu is on, but I don't know the command(s) to give GRUB.  Can anyone tell me?

I assume that this will allow me to bypass GRUB on the Kubuntu-root menu entirely.  Right?

Please be explicit.  I ain't real smart.

Many thanks.

---

### Post by Lunde on 2005-07-01
Try to make a bootdisk so you can enter your Ubuntu:
[http://www.openbg.net/sto/os/xml/grub.html](http://www.openbg.net/sto/os/xml/grub.html)

Then this is what I did from inside Ubuntu
$ sudo grub-install 

In my case this was the command that located my systems:
$ sudo grub-install /dev/hda

---

### Post by lance_delacroix on 2005-07-01
I got into Kubuntu by making the root partition primary again and installing GRUB to the root from Ultimate Boot Disk.

Inside GRUB, I found what I need to boot Kubuntu from my Mepis-root GRUB, and in my Mepis-root GRUB I found what I need to boot Mepis from my Kubuntu-root GRUB.

Using the command line, I can boot either OS from the other's root using the copy of GRUB that is installed on that root.

Now, can anybody tell me how to make a new menu entry in a GRUB menu? 

Thanks very much!

---

### Post by Lunde on 2005-07-01
[QUOTE=lance_delacroix]I got into Kubuntu by making the root partition primary again and installing GRUB to the root from Ultimate Boot Disk.

Inside GRUB, I found what I need to boot Kubuntu from my Mepis-root GRUB, and in my Mepis-root GRUB I found what I need to boot Mepis from my Kubuntu-root GRUB.

Using the command line, I can boot either OS from the other's root using the copy of GRUB that is installed on that root.

Now, can anybody tell me how to make a new menu entry in a GRUB menu? 

Thanks very much![/QUOTE]
 I'm pretty sure you just add the startup lines in: /boot/grub/menu.lst

Add the lines to your menu.lst Like this: 

> 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.10-5-386 (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel 2.6.10-5-386 (recovery mode) (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hdb1 ro single 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb1.
title		Ubuntu, kernel memtest86+ (on /dev/hdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


I did the same when I upgraded my kernel. I have 2 linux systems, 1 simple installation for backup and recovery and my Ubuntu. 

Note: If you upgrade your kernel on the system that is not hosting the grub configuration, you have to manually edit the menu.lst to boot the right kernel.

---

### Post by lance_delacroix on 2005-07-01
[QUOTE=Lunde]I'm pretty sure you just add the startup lines in: /boot/grub/menu.lst[/QUOTE]

Okay, thanks! I'll give it a try.

---

### Post by mingus on 2005-07-01
[QUOTE=lance_delacroix]
I assume that this will allow me to bypass GRUB on the Kubuntu-root menu entirely.  Right?[/QUOTE]

Yes.  Lunde's method explicitly calls the kernel from the MEPIS boot loader.  The only way the Kubuntu grub would run is if it were chain-loaded.  You do not need grub installed in Kubuntu at all.

---

