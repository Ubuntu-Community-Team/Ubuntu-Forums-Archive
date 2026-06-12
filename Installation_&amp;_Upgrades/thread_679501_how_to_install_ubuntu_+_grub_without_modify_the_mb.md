---
title: "how to install ubuntu + grub without modify the mbr and boot flag ?"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by kissson on 2008-01-27
now I have xp in hd0,0
i plan to install linux to hd0,1
with grub in /boot/grub but without modify the mbr and boot flag
because I will use the grub4dos later (thats ms-mbr load ntldr then pass to grldr then load grub)

but the alternative cd or livecd dont has such a option, any ways to have it done ?

also, is there any tools to build /boot/grub especially the menu.lst afterwards if i choose not to install grub?

thx

---

### Post by logos34 on 2008-01-27
> **kissson said:**
> but the alternative cd or livecd dont has such a option, any ways to have it done ?

sure they do.  alternate cd: at the end there's a bootloader section where it asks you where to put Grub.  type in **(hd0,1)**  --> this will write it to the bootsector of the ubuntu root partition, not the MBR.

Live cd: >'Ready to install' screen>click '**Advanced**' button lower right>enter **(hd0,1)**

You could also send grub to a floppy with **(fd0)**.

Now you can use grldr or whatever to boot ubuntu from windows

---

### Post by kissson on 2008-01-27
I boot the xubuntu alternate 7.10
then install a command-line system
to the step of "install the grub boot loader on a hard disk"
when i pressed enter, it automated everything.

yes, form the livecd , theres a option in the boot loader advance to let you fill in

I am in normal mode, do I need to in expert mode switched in boot menu F6?
thx

---

### Post by logos34 on 2008-01-27
> **kissson said:**
> I boot the xubuntu alternate 7.10
then install a command-line system
to the step of "install the grub boot loader on a hard disk"
when i pressed enter, it automated everything.

Ok, so you're installing xubuntu, didn't know, but I think it's the same.  If you just pressed enter, then I believe it installed to the default location, (hd0), which is not what you wanted. 

> I am in normal mode, do I need to in expert mode switched in boot menu F6?

not sure what you mean, please clarify

---

### Post by BXA121 on 2008-01-27
during installation of ubuntu at the partition manager section there is an advanced option - it will allow you to not install GRUB during installation. if course youll have to setup your own bootloader. this may help

---

### Post by kissson on 2008-01-27
installed it couples of times, cant find any settings to configure where to install grub in text mode installation, no matter ubuntu 7.10 alternate / xubuntu 7.10 alternate
text mode installation / command-line system installation

but livecd installer doees, yes , it does
:confused::confused::(:(



------------------------------------------------------------------------------------------------------



before:
/sda | ms-mbr
&#12288;/sda1 | ntfs | boot | nt loader
&#12288;/sda2 | ext3
&#12288;/sda3 | swap

one time tried to install grub to sda <---- because no ways to make it sda2
after installation:

/sda | grub
&#12288;/sda1 | ntfs | nt loader
&#12288;/sda2 | ext3 | boot
&#12288;/sda3 | swap

i do this, i want to boot nt loader to boot grub
sudo dd if=/dev/sda of=/dev/sda2 bs=512 count=1
sudo dd if=ms-mbr.bin of=/dev/sda bs=512 count=1

sudo fdisk /dev/sda
a > 1
a > 2 > w

but, the partition of sda2 and sda3 completly gone, and size of sda1 expands, leaving unused space at the end

/sda | grub
&#12288;/sda1 | ntfs | nt loader
&#12288;<space>

my xp still booting ...:KS
:confused::confused::confused:

---

### Post by Pumalite on 2008-01-27
You don't need a /boot partition. Just install Grub to it's own partition, then, modify boot.ini

---

### Post by kissson on 2008-01-28
oh, i realized the problem
because grub fail to detect my win xp
my (hd0,0) only with ntfs+ntldr but no windows xp actually installed
but livecd can override it, no matter xp is detected or not

(hd0,0) should actually has windows xp then command line installer will bring up a menu of where to install grub, otherwise it will still install grub onto hd0 no matter the root is (hd0,1) and is a ntfs on (hd0,0)

hope it can be fixed in 8.04

---

