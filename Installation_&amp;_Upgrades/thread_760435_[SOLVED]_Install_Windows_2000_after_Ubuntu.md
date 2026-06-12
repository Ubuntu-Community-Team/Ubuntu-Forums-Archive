---
title: "[SOLVED] Install Windows 2000 after Ubuntu??"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by maconga on 2008-04-20
I have a computer with Xubuntu 7.10 and I want to install Windows 2000 Professional (Original, no sp's) from my CD. I do not want to reformat my hard drive, i want to dual boot. 

How do i set up a Partition? ( never done this before) 
and will i lose my GRUB?, i'v heard that installing windows xp or vista after ubuntu will make you lose your grub... does this affect windows 2000 pro? 
I'm completely lost at this ...

---

### Post by sandysandy on 2008-04-20
post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

if u have a spare partition u can install win 2000 on it.

if u do not have spare partition u can resize existing ubuntu partition with gparted.

u will loose MBR but no problem u can reinstall GRUB after Win 2000 installation is over by going thru this thread on how to re-install grub

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by sandysandy on 2008-04-20
some links to dual boot

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://ubuntuforums.org/showthread.php?t=33778](http://ubuntuforums.org/showthread.php?t=33778)

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://howtoforge.com/dual_boot_wind..._ubuntu_feisty](http://howtoforge.com/dual_boot_wind..._ubuntu_feisty)

[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by maconga on 2008-04-20
jj@jj-desktop:~$ sudo fdisk -lu
[sudo] password for jj:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ce338

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   154818404    77409171   83  Linux
/dev/sda2       154818405   156296384      738990    5  Extended
/dev/sda5       154818468   156296384      738958+  82  Linux swap / Solaris
jj@jj-desktop:~$

---

### Post by maconga on 2008-04-20
thanks for the sites

---

### Post by forestpixie on 2008-04-20
If you don't want to format your hard drive you will not be able to install win2k on it's own.

You could if you wanted - dpending on what you want 2k for - run a virtual machine within buntu and install win2k to that - I had to do the same thing.

---

### Post by maconga on 2008-04-20
Where would i get a  virtual machine?? 
I want to know all the options...

Edit:

also, would it be possible to have Win2000pro on a separate hard drive, and Linux on my primary, and just open BIOS and change the boot order to where the windows will load and if i want to use linux, just restart the computer, and open BIOS and select the Linux drive as primary ?

---

### Post by forestpixie on 2008-04-20
Thhis is as good a start as any - [http://ubuntuforums.org/showthread.php?t=582729](http://ubuntuforums.org/showthread.php?t=582729)

I use virtualbox - mainly because I've nver really looked at the others - but I know that it has the guest additions which enable mouse without the need to capture it inside the virtual machine (you'll know what I mean if you do it).

You can get virtualbox from here - [http://www.virtualbox.org/](http://www.virtualbox.org/)

Have a look and a think. You need to know that generally you won't get 3D inside a vm - so if it's for gaming I'd be looking at dual booting.

---

### Post by maconga on 2008-04-20
I just installed the VM thing, i set it up for windows 2000, and this happened... when it turned it "on" 



The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by the8thstar on 2008-04-20
> **maconga said:**
> I just installed the VM thing, i set it up for windows 2000, and this happened... when it turned it "on" 



The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

This is a typical problem. Go to Administration and Users. Select vboxusers, edit and enter your info there (login and password) and you should be fine.

---

### Post by maconga on 2008-04-20
Solved Thank You All!

---

### Post by maconga on 2008-04-20
well... i got install cd to work... and now i got this SERIOUS question.... will this reformat my hard drive ??!?! 


I do NOT want it to be reformatted....

---

### Post by the8thstar on 2008-04-20
Don't worry it will reformat the VIRTUAL drive only that's within the .vdi, not the whole hard disk.

---

