---
title: "XP/Ubuntu install - no grub"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by varnerin on 2004-12-16
I have two SATA 200 GB Maxtor drives.  The first drive has XP, and I installed the Ubuntu on the second one.  When I installed Ubuntu, I said yes to install grub on MBR.  When it boots, it goes directly into XP, no grub.

Any suggestions?

Thank you,
Kevin

[http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#](http://www.ubuntuforums.org/newthread.php?do=newthread&f=5#)
Cool

---

### Post by kirsche on 2004-12-17
Sounds like you've installed grub to the MBR of the 2nd HDD.
This MBR wont be read during the startup of the computer (just the one from the master HDD).
So, you should install grub to the MBR of the 1st HDD. (create an image before :) )

---

### Post by varnerin on 2004-12-17
How do I make sure grub is installed on the first hard drive ?  I did not see an option with the Ubuntu installation program.

Thank You,
Kevin

---

### Post by varnerin on 2004-12-17
I now believe the problem is Ubuntu as well as Mepis and Fedora do not support either my motherboards SATA controller (Nvidia Raid MCP) or that they do not support SATA hard drives.  

Can anyone verify this?

Best Regards,
Kevin

---

### Post by tanari on 2004-12-19
I have also problem with GRUB.
I have ubuntu on first partition, and yesterday I have installed WinXP on second parition and of course WinXP deleted GRUB. Now I can load only to WinXP.

How to restore GRUB?

---

### Post by Rhodan on 2004-12-19
[QUOTE=varnerin]I now believe the problem is Ubuntu as well as Mepis and Fedora do not support either my motherboards SATA controller (Nvidia Raid MCP) or that they do not support SATA hard drives.  

Can anyone verify this?

Best Regards,
Kevin[/QUOTE]

I also have a SATA drive on the Nvidia controller, I've been searching around for answers and it seems to be a problem with the kernel supplied with the "Warty" release, basically I'm getting the same problem as posted in here [http://www.ubuntuforums.org/showthread.php?t=8361](http://www.ubuntuforums.org/showthread.php?t=8361) .

We need the 2.6.9 kernel, which should be in the "hoary" release, I'm going to download the latest build and try it, [http://cdimage.ubuntulinux.org/](http://cdimage.ubuntulinux.org/)

---

### Post by fuchetj on 2004-12-20
Sorry fo the OT, but does anyone know how to install the grub in a floppy??? I've tried different paths in the provided line and the outcome is always the same, an error... ](*,) 

Fuche

---

### Post by kirsche on 2004-12-20
one way would be, to boot with a live-cd (gentoo, knoppix, gnoppix...) and start the grub installation manual:

grub
grub> root (hd0,0) (whatever the boot-partition is)
grub> setup (hd0,0) (install grub into the BR of the first partition of HDD0 )
OR
grub> setup (hd0) (install grub into the MBR of HDD0)

see:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing%20GRUB%20natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing%20GRUB%20natively)

also for flopy:
[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy](http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy)

---

### Post by fuchetj on 2004-12-20
[QUOTE=kirsche]one way would be, to boot with a live-cd (gentoo, knoppix, gnoppix...) and start the grub installation manual:

grub
grub> root (hd0,0) (whatever the boot-partition is)
grub> setup (hd0,0) (install grub into the BR of the first partition of HDD0 )
OR
grub> setup (hd0) (install grub into the MBR of HDD0)

see:
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing%20GRUB%20natively](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html#Installing%20GRUB%20natively)

also for flopy:
[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy](http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy)[/QUOTE]

Thanks, I find out the way. [Grub in Floppy](http://www.ubuntuforums.org/showthread.php?t=8555) 

Fuche

---

### Post by tanari on 2004-12-20
I have 3 partitions
/dev/hda1 - ubuntu
swapfile for ubuntu
/dev/hda3 - winXP *boot flag

Must I put 'boot flag' to /dev/hda1 ? Is it safe to do this with partition resizing programm on ubuntu installation CD (it says, it could destroy all data)?

---

### Post by Geizer8414 on 2007-05-15
> **fuchetj said:**
> Sorry fo the OT, but does anyone know how to install the grub in a floppy??? I've tried different paths in the provided line and the outcome is always the same, an error... ](*,) 

Fuche


[baking solar Skin care Eminem music](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

