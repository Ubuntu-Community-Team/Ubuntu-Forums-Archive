---
title: "Grub, MBR??"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by pepperwood on 2008-01-29
Still having some issues with the dual booting linux on dual hdds. I installed ubuntu EMC2 first on the primary HDD and used the Auto partition to set up. Used secondary HDD for BDI 4.51 EMC2, also Auto Partitioning.  Installion completes installing the programs. The next thing before rebooting comes installing the bootloader. This doesn't take place??? Perhaps the boatloader is no longer available or can not be found by BDI As the system just quits, shuts down, freezes up with the message Installing Bootloader. 

At this point I shut off PC & reboot. Upon rebooting Ubuntu EMC2 will boot as it is the only OS listed on the startup screen & it reboots Ubuntu. Nice but not there yet?

Anybody have any suggestions as to the next step to take to get BDI 4.51 EMC installed & rebooted?? Used versa & vise versa. However BDI will not install at all now.  Thought about making a copy of Grub from Ubuntu live CD? and installing to BDI as I believe they both use Grub. BUT how do you do that?  Just a newbie thought??  

Your assistance, as always, would be appreciated. Thank you very much!

Pete

---

### Post by logos34 on 2008-01-29
try [adding a BDI entry]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") to EMC2 grub.cfg/menu.lst.

---

### Post by pepperwood on 2008-01-30
Back to square 1 again, Ubuntu emc installed to hdb1 secondary HDD.
Installed BDI to primary hda HDD. It installed & boot loader was auto
installed to hda. Start up screen showed both BDI & Ubuntu. Ubuntu was
default. Ubuntu would not boot up but BDI booted up.

Upon selecting & trying to boot up Ubuntu. I get the message
map(hd0)(hd1) - map (hd1) (hd0) - rootnoverity (hd1,0), chainloader
+1, error 13: invalid or unsupported executable format. press any key
to continue. Its strange as it lists my hdb as sba, which I think is
USB. Is your sba an USB drive? That may explain part of the error. As
both my drives are internal HDD's? Just a newbie thought?

Presently BDI auto installed my boot loader to hda0 I believe? Not
sure what happened to the Ubuntu Install? Thanks for taking the time
to post your note. According to all the Hippe I thought It might just
take me a couple of tries when I started a month ago. Probably would
of but a fluke of some kind. Thanks again!

Pete

---

### Post by logos34 on 2008-01-30
not sure why it's putting map commands for ubuntu--doesn't need them.  

usb drives are 'sd_'

Better post your 

# fdisk -l

and explain what's what.

You could try [reinstalling Ubuntu grub bootloader]("http://ubuntuforums.org/showthread.php?t=224351") and using the configfile entry format for the others, as I suggested above.

---

