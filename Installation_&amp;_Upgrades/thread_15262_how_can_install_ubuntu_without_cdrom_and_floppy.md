---
title: "how can install ubuntu without cdrom and floppy?"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by Kyson on 2005-02-13
there are XP and  debian on my hd and no free space
i want to replace my debian with  ubuntu
but i have no cdrom and  floppy
 
here's my computer's information

P4 1.6A
256M
40G (5G for linux)
windowsXP & Debian

i tries unzip the iso and copy the initrd.gz and vmlinuz out, use loadin to run the install kernel, but it still ask for cdrom.

i wonder if there's a initrd for HD-install like debian.

regards,
kyson

---

### Post by Rerven on 2005-02-13
yeah ... Ive got the same problem ,  ive just downloaded an iso image ... Whether  it can be installed with hd image but not with cdrom or floppy... Anyone got ideas ? 
Thanx !!!

---

### Post by moufranica on 2005-02-13
[QUOTE=Rerven]yeah ... Ive got the same problem ,  ive just downloaded an iso image ... Whether  it can be installed with hd image but not with cdrom or floppy... Anyone got ideas ? 
Thanx !!![/QUOTE]

Same problem here. I have the iso file downloaded. But no CDs :(
I have VcdControlTool, and have extracted the files inside the iso image onto my hard drive. How do I procede from here? Thanks.

---

### Post by az on 2005-02-13
"i want to replace my debian with ubuntu"

You can apt-get dist-upgrade from Woody to Warty.


Warty's installer is thrown off when it is not on a cd.  Perhaps Hoary's will work.  If not, you can always install Woody that way and then dist-upgrade to Warty.

---

### Post by Kyson on 2005-02-14
i add the two address in source.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

and then 
#apt-get update
#apt-get dist-upgrade
 i just get some packages that need update

is this the way to update from woody to ubuntu?

---

### Post by az on 2005-02-14
Do not forget about main:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

I would just start with that first line, and then add Universe and security updates afterwards.  Check to see if packages are going to be removed.  Is your debian system Woody or Sarge and Sid?  If so, you may have a few glitches.  You should still be able to do it, though.  Especially if you do not care about the system that you already have.

---

### Post by Kyson on 2005-02-14
thx ... i'm doing the dist-upgrading now.
there are 191 pakages to upgrade, 6 new pakages to install, 1 to uninstall, and  .... 1 not to upgrade?
the speed is not too bad ...

and after the upgrade, what should i do ?
will it run a install program? or just reboot, and the ubuntu coms into my computer?

anyway, after all done, i will write a summary about this

thx azz again

---

### Post by az on 2005-02-14
If it does not give you the Ubuntu desktop:

apt-get install ubuntu-desktop.

---

### Post by Kyson on 2005-02-14
hmmm, after i finished the upgrade, it has some changes, now some of the icons in the packeges have  ubuntu icon and it reffers to a ubuntu start page when i open the firefox

but, i cannot install the ubuntu-desktop

#apt-get install ubuntu-desktop
it said the packeges i want to install is depends on some other packeges but they wont be installed, and some other packeges have the same problem ...

and ... now i can still use the root account to login and havet use sudo yet ... o_O

is that because i used a customed debian(like knoppix but not)?

should i try to install a sarge base system and do the dist-upgrade again?

regards,
Kyson

---

### Post by az on 2005-02-14
Okay.  Woody should work, but not Sarge.  Try removing whatever package is preventing you from installing Ubuntu-desktop.

apt-get remove --purge kdelibs4 arts libgnome2-0
apt-get install ubuntu-base ubuntu-desktop

---

### Post by Kyson on 2005-02-14
well, can i use the woody net-install mini cd to install a pure ubuntu ?

---

### Post by Kyson on 2005-02-15
i did it. well there are still some small problems but ... they were just small problems i think  :---) 

i downloaded woody cd1 (minimal cd)  and ubuntu iso files

**[COLOR=Blue]first[/COLOR]**, i extracted them into two folders in a FAT32 drive /linux/woody and /linux/ubuntu

**[COLOR=Blue]second[/COLOR]**, boot to DOS, run the boot.bat in the /woody/install/boot.bat

[COLOR=Green]//it should be diaplayed a menu to let you to choose a install kernel, but it just jumped to the first one,  somebody told me it's a bug of loadlin, i dunno. but i cannot use the 2.4 kernel (bf2.4), so i installed the old 2.2 ... and it causes problems when i installing ubuntu ...[/COLOR]

doing the install, choose the file from hardrive, it will  install the base system

[COLOR=Green]//why woody format my ext3 into ext2 !?[/COLOR]  :| 

after the base-system install, it installed lilo to MBR ( i prefer grub ....)

REBOOT ....

**[COLOR=Blue]third[/COLOR]** , login as root, do these commands:

#mkdir /mnt/ubuntu
#mount /dev/[COLOR=Red]hdc7[/COLOR] /mnt/ubuntu          // change the red text yourself
#nano /etc/apt/sources.list                 //  i dunno how to use vim :P

add this line

deb file:///mnt/ubuntu/[COLOR=Red]linux/ubuntu/[/COLOR] warty main restricted    [COLOR=Red]// change the red text yourself[/COLOR][COLOR=Red] !!! DO NOT ADD THE COMMENT !!![/COLOR]

#apt-get update
[COLOR=Green]//i'm not sure of the right apt-get turns below[/COLOR]
#apt-get dist-upgrade
#apt-get install ubuntu-base
#apt get install ubuntu-desktop
.....
......
.....
#reboot

....

Ubuntu 4.10 "Warty Warthog" Ifrit tty1    //Ifrit's my computer  :grin: 
login:

......

all done .... i think :P


and the known problems, because of the old kernel, many modules cannot be load, and i cant enter the X, when i do startx. maybe it also caused by the kernel.

maybe i can try to install the base-system with sarge ?

but *_azz_* said that it cannot update from sarge to warty ... why ... :| 

regards,
Kyson

---

