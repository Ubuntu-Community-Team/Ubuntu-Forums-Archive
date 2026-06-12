---
title: "Sector 32 is already in use by the program `FlexNet'; avoiding it..."
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by xxx6 on 2014-04-01
Hi!

```
Setting up grub-common (2.02~beta2-8) ...
Installing new version of config file /etc/grub.d/05_debian_theme ...
Setting up grub2-common (2.02~beta2-8) ...
Setting up grub-pc-bin (2.02~beta2-8) ...
Setting up grub-pc (2.02~beta2-8) ...
Installing for i386-pc platform.
grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-18-generic

```

do I need to worry bout? some tip(s) to get rid of that winBUG$ sh_t ??

tia!

---

### Post by oldfred on 2014-04-01
You installed some software in Windows that uses DRM with Flexnet (often Adobe but many others). 
It used to be an issue as flexnet would just overwrite grub or vice-versa and create all sorts of issues. Now grub just created a work around to avoid the Flexnet sector.

If you do not need or want the DRM based software in Windows then you would not have flexnet. Not sure how to uninstall that though. Found this in my notes from when we used to see it a lot.

 Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet site:ubuntuforums.org
Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

---

### Post by xxx6 on 2014-04-01
THX a LOT pal!

---

### Post by xxx6 on 2014-04-01
> **oldfred said:**
> 
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

Hi!

don' get this:

> [COLOR=Blue][COLOR=Black]If you want to target one individual sector to erase, then you can erase [COLOR=Blue]Sector 32[COLOR=Black] as follows:[/COLOR][/COLOR]

 	

 	```
sudo dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=[COLOR=Blue]32[/COLOR]
```


After I erased the FlexNet data and re-installed Grub, the PC booted up fine[/COLOR][/COLOR]

How to **_re-install  _**grub?

tia!

---

### Post by oldfred on 2014-04-01
Most find Boot-Repair to be easiest, but you can use a live installer DVD or flash drive.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by xxx6 on 2014-04-04
Weirdest thing I do not have nada of Adobe installed except flash-plugin on win7...in fact  I do not use that malware[win$UCK$] at all!

---

### Post by oldfred on 2014-04-04
You only have to have installed flexnet once even trials of some software that uses it.

You really do not have to worry about sector 32, as grub just does not use that sector and skips it. 

The erasing of it by writing 0 just to sector 32 is so the next time you install grub and it creates core.img that it will then use that sector. The part of grub in the MBR loads core.img which is in the sectors immediately after the MBR or first sector and before the first partition, now usually sector 2048 for compatiblity with SSD and new 4K drives.

---

