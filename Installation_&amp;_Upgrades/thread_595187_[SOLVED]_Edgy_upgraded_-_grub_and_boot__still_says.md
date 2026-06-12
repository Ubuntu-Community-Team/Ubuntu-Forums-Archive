---
title: "[SOLVED] Edgy upgraded - grub and boot  still says dapper"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Klarsin on 2007-10-28
I upgraded from dapper to edgy using my install CD. All went good except I lost my speedcrunch calc which was reinstalled OK. But why does GRUB not change to edgy - it still says dapper with the dapper version. Also the boot diologue says dapper. Once booted everything looks like edgy. 

Also, where do I check to see if my Ubuntu version is truly edgy?

---

### Post by mlind on 2007-10-28
does *cat /etc/lsb-release* say that codename is edgy?

---

### Post by Klarsin on 2007-10-28
> **mlind said:**
> does *cat /etc/lsb-release* say that codename is edgy?

Yeah, it's edgy.  Bu it's still unclear why grub still says dapper. I guess I can go in and change it manually.

 Is this the only way I can tell my version. You usually find it in the 'about' menu of other OSs.

---

### Post by zvacet on 2007-10-28
Did you change your sources.list from Dapper to Edgy?If you didn´t

```
 sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

After that 

```
sudo aptitude update
```

---

### Post by Klarsin on 2007-10-28
> **zvacet said:**
> Did you change your sources.list from Dapper to Edgy?If you didn´t

```
 sudo sed -e 's/\sdapper/ edgy/g' -i /etc/apt/sources.list 
```

After that 

```
sudo aptitude update
```

I used the above code and the source list below says edgy, but grub still says dapper.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by zvacet on 2007-10-29
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

to 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

```
sudo aptitude update
```

Before you do this chek if you have all repos open 

system>administration>software sources

If all this give no joy try in synaptic find linux-image with higher number then it is one you use now.Install it.I hope this will help.

---

### Post by mlind on 2007-10-29
Did you tried to run 'sudo update-grub' yet?

---

### Post by Klarsin on 2007-10-29
If this code is supposed to change, well all looks the same here:

# Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by zvacet on 2007-10-29
```
gksudo gedit /etc/apt/sources.list
```

and than remove # sign in front of lines.Save and close.

---

### Post by Klarsin on 2007-10-29
> **mlind said:**
> Did you tried to run 'sudo update-grub' yet?
Yeah. It did nothing. So I guess maybe Zvacet is on the right track where there is something wrong with the update source.

---

### Post by Klarsin on 2007-10-29
> **zvacet said:**
> ```
gksudo gedit /etc/apt/sources.list
```

and than remove # sign in front of lines.Save and close.

OK I did that but It put the # back in after I deleted it and saved - below is what is looks like. Also, you said go to synaptic and dowload new image. What do you mean by image? Like what is the file name?


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by meierfra on 2007-10-29
Please post the output of 

```
cat /boot/grub/menu.lst        (l is a lower case L)
```

so that we can see what your grub menu looks like.

---

### Post by Klarsin on 2007-10-30
> **zvacet said:**
> ```
gksudo gedit /etc/apt/sources.list
```

and than remove # sign in front of lines.Save and close.
This is the way it looks right now:

ect/apt/sources.list

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

-------------------------------
Below, the 2.6.17-12 is another Edgy on another drive hd5.  We are concerned with 2.6.15 on the hd1 drive that is now Edgy showing dapper I.D.

~$ sudo update-grub
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-12-386 ------------------     *hda5  Edgy (it shows -10 not -12)
Found kernel: /boot/vmlinuz-2.6.15-29-386 -------------------    *hda1  Edgy is installed but grub shows only Dapper -27)
Found kernel: /boot/vmlinuz-2.6.15-28-386  ----------------------       "  
Found kernel: /boot/vmlinuz-2.6.15-27-386  -----------------------     "    
Found kernel: /boot/vmlinuz-2.6.15-26-386  -------------------    *hda2  Mepis shown
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

----------------
According to my synaptic the linux image 2.6.17-12.41  for 386 was installed, but I reinstalled it. Then updated grub again. 

Note: I just remembered way back when I was setting up my partitions that grub was edited because hd1 was not the primary loader. If that is of any consequence I might have to edit it by hand, but that still might not fix the update problem.

---

### Post by mlind on 2007-10-30
I reckon you have grub in two(?) different hdd's MBR and you're booting using the 'old' one. I would probably reinstall grub using "sudo grub-install /dev/hda" and change that drive as first in bios boot order.

(.. or maybe not. could you attach your /boot/grub/menu.lst ?)

Are you using shared /boot partition for kernel's?

---

### Post by Klarsin on 2007-10-30
> **mlind said:**
> I reckon you have grub in two(?) different hdd's MBR and you're booting using the 'old' one. I would probably reinstall grub using "sudo grub-install /dev/hda" and change that drive as first in bios boot order.

(.. or maybe not. could you attach your /boot/grub/menu.lst ?)

Are you using shared /boot partition for kernel's?

I think I added the words Edgy and Dapper  so I could quickly distinguish the difference. They originally just said Ubuntu.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4

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
# kopt=root=UUID=49380a4b-5a11-4edc-b768-82ebdb1874a3 ro
# kopt_2_6=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

## ## End Default Options ##

title		Ubuntu Edgy, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu Edgy, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu Edgy, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu Dapper, kernel 2.6.15-27-386 (on /dev/hda1) 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu Dapper, kernel 2.6.15-27-386 (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title		Ubuntu Dapper, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		MEPIS at hda2, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 nomce quiet vga=791 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		MEMTEST (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by meierfra on 2007-10-31
Edit :Ignore this post, wrong diagnosis.

Mystery solved:

You must have edited you dapper menu.lst and moved  the Dapper items outside the automatic update area, that  is the area between

### BEGIN AUTOMAGIC KERNELS LIST 
and 
### END DEBIAN AUTOMAGIC KERNELS LIST

Every outside that area is left untouched during updates and upgrades.  You can just  remove everything below  "### END DEBIAN AUTOMAGIC KERNELS LIST".

---

### Post by Klarsin on 2007-10-31
> **meierfra said:**
> Mystery solved:

You must have edited you dapper menu.lst and moved  the Dapper items outside the automatic update area, that  is the area between

### BEGIN AUTOMAGIC KERNELS LIST 
and 
### END DEBIAN AUTOMAGIC KERNELS LIST

Every outside that area is left untouched during updates and upgrades.  You can just  remove everything below  "### END DEBIAN AUTOMAGIC KERNELS LIST".

But if I do that I'll be losing hda1 and mepis, won't I? Shouldn't I just move the '### END DEBIAN AUTOMAGIC KERNELS LIST' down to the bottom?

---

### Post by meierfra on 2007-10-31
Oops, I didn' t notice mepis. But  memtest is also in the automatic update area.

---

### Post by meierfra on 2007-10-31
I had another look at you menu.lst and it looks like that you did not upgrade dapper  but installed edgy on a separate partition. So you have dapper on one partition and edgy on another. Is that what you want?  
 If I'm right then using  the edgy and dapper item in the grub menu should  get you to different parts of your computer.

Use "sudo fdisk -l" to list all the partitions.

---

### Post by Klarsin on 2007-10-31
> **meierfra said:**
> I had another look at you menu.lst and it looks like that you did not upgrade dapper  but installed edgy on a separate partition. So you have dapper on one partition and edgy on another. Is that what you want?  
 If I'm right then using  the edgy and dapper item in the grub menu should  get you to different parts of your computer.

Use "sudo fdisk -l" to list all the partitions.
 
I installed edgy on hda5 about 6mo. ago to use as a backup and a trial for future upgrades.  I upgraded dapper (which is the primary that I work in every day) to edgy on hda1 just the other day. This is what I want, except that the new edgy (hda1) grub still says dapper. I want to keep edgy on hda1 but change the grub menu to reflect the new upgrade to edgy. Get it!


~$ sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       12197    97972371   83  Linux
/dev/hda2           12198       14660    19784047+  83  Linux
/dev/hda3           14661       14749      714892+  82  Linux swap / Solaris
/dev/hda4           14750       19457    37817010    5  Extended


/dev/hda5   *       14750       19262    36250641   83  Linux
/dev/hda6           19263       19457     1566306   82  Linux swap / Solaris

---

### Post by meierfra on 2007-10-31
The menu.lst  you posted is  the menu.lst from hda5. You need to reinstall grub  to use the hda1 menu.lst:

sudo grub

and then at the grub prompt:

root (hd0,0)

setup (hd0)

quit


After reboot you should get the hda1 menu.lst.

---

### Post by Klarsin on 2007-10-31
> **meierfra said:**
> The menu.lst  you posted is  the menu.lst from hda5. You need to reinstall grub  to use the hda1 menu.lst:

sudo grub

and then at the grub prompt:

root (hd0,0)

setup (hd0)

quit


After reboot you should get the hda1 menu.lst.

OK now I get auto boot for hd0 which is actually hda1 that boots, and have to press esc to get the menu which shows all drives as hd0. So now in order to change to the other drives, I must I.D. the drive?  Menu list now looks like this.

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.17-12-386
boot

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by meierfra on 2007-10-31
What a mess. I would do the following:

1) Change  "#howmany=all" to "#howmany=2"  in menu.lst on sda1. This determines how many different kernels you want to be listed in the "automatic update area"

2) type "sudo update-grub" in a terminal. This regenerated "menu.lst" and you will have only two sets kernels in your menu.lst.

3) Change "hiddenmenu" in menu.lst  to "#hiddenmenu". Then you won't have to press "Esc" during boot up.

4) Maybe change "timeout 3" to "timeout  10" (or some other number) so that you have more times before  grub boots automatically.

5)     Add this at the  end of file:

title Edgy on sda5
root (hd0,4)
configfile /boot/grub/menu.lst

Selecting  this item at boot-up will bring up the grub menu from sda5,
I like this method because you won't have to manual change your menu.lst on sda1 whenever there is a kernel upgrade for your edgy on sda5. You won't even have to change your menu.lst, if you  install feisty or gutsy on sda5.
To make this work nicely  you could  set "timeout=0" on menu.lst in sda5. Then you won't even notice the second menu.

6)  Copy and paste the mepis and windows items from your menu.lst on sda5 to the  end of menu.lst on sda1. (And if you don't like my method in 5) do  the same with the edgy items  on sda5.)

---

### Post by mlind on 2007-11-01
You need to add **kopt** entries for other Ubuntu kernels. It's better to put Mepis kernel after 'automagic kernel list'.


For exaple, this is what I have for Gutsy, Feisty and Edgy in my menu.lst
```

# kopt=root=/dev/mapper/Ubuntu-rootGutsy ro
# kopt_2_6_20=root=/dev/mapper/Ubuntu-rootFeisty ro
# kopt_2_6_17=root=/dev/mapper/Ubuntu-rootEdgy ro

```

You need to use **vol_id** to get the UUID for each kopt entry as you're using UUID's.

---

### Post by Klarsin on 2007-11-01
> **meierfra said:**
> What a mess. I would do the following:

1) Change  "#howmany=all" to "#howmany=2"  in menu.lst on sda1. This determines how many different kernels you want to be listed in the "automatic update area"

2) type "sudo update-grub" in a terminal. This regenerated "menu.lst" and you will have only two sets kernels in your menu.lst.

3) Change "hiddenmenu" in menu.lst  to "#hiddenmenu". Then you won't have to press "Esc" during boot up.

4) Maybe change "timeout 3" to "timeout  10" (or some other number) so that you have more times before  grub boots automatically.

5)     Add this at the  end of file:

title Edgy on sda5
root (hd0,4)
configfile /boot/grub/menu.lst

Selecting  this item at boot-up will bring up the grub menu from sda5,
I like this method because you won't have to manual change your menu.lst on sda1 whenever there is a kernel upgrade for your edgy on sda5. You won't even have to change your menu.lst, if you  install feisty or gutsy on sda5.
To make this work nicely  you could  set "timeout=0" on menu.lst in sda5. Then you won't even notice the second menu.

6)  Copy and paste the mepis and windows items from your menu.lst on sda5 to the  end of menu.lst on sda1. (And if you don't like my method in 5) do  the same with the edgy items  on sda5.)

I'm finding this all very confusing, and don't have much more time to spend on this. But I do have Edgy showing in grub for hda1 now, which was missing before. My question now is, looking at the below menu.lst, why is dapper and all its updates still appearing on hda1 when Edgy has replaced it. Can't I now just delete the dapper entries, or will this screw up grub. I noticed that the following does not appear on the grub for Edgy had1:(At the very bottom of this file)

title Edgy on hda5
root (hd0,4)
configfile /boot/grub/menu.lst

--------
Here is the current grub menu lst after the changes you suggested:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# howmany=2

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.17-12-386
boot

title		Ubuntu, kernel 2.6.15-29-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-29-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-29-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-29-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-29-386
boot

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Edgy on hda5
root (hd0,4)
configfile /boot/grub/menu.lst

---

### Post by meierfra on 2007-11-01
Just delete the dapper items. They no longer serve any purpose.

---

### Post by meierfra on 2007-11-02
> My question now is, looking at the below menu.lst, why is dapper and all its updates still appearing on hda1 when Edgy has replaced it. Can't I now just delete the dapper entries, or will this screw up grub. I noticed that the following does not appear on the grub for Edgy 

I'm confused:

Did you run "sudo update-grub" to shorten the list of items in your menu.lst?


Does "Ubuntu Dapper, kernel .... "  appear on your grub menu at boot-up?  Or  just a  long list of various   "Ubuntu, kernel  .......  " ?

---

### Post by Klarsin on 2007-11-02
> **meierfra said:**
> 

Did you run "sudo update-grub" to shorten the list of items in your menu.lst?
Does "Ubuntu Dapper, kernel .... "  appear on your grub menu at boot-up?  Or  just a  long list of various   "Ubuntu, kernel  .......  " ?

OK, I'm unconfused. I deleted the long list of U kernels on both hda1 and hda5 and moved mepis from hda5 to hda1 then "sudo update-grub". I havn't moved U on hda1 to list on hda5 though (yet). I guess that shouldn't be a problem. 

Did you say that when I update Edgy hda1 that Edgy on hda5 will simultaneously update too. 

This is what hda1 looks like now:

# ## End Default Options ##

title		Ubuntu, kernel 2.6.17-12-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-386 root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c ro single
initrd		/boot/initrd.img-2.6.17-12-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title Edgy on hda5
root (hd0,4)
configfile /boot/grub/menu.lst

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		MEPIS at hda2, kernel 2.6.15-26-386 (on /dev/hda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 nomce quiet vga=791 
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title		MEMTEST (on /dev/hda2)
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Klarsin on 2007-11-02
> **mlind said:**
> You need to add **kopt** entries for other Ubuntu kernels. It's better to put Mepis kernel after 'automagic kernel list'.


For exaple, this is what I have for Gutsy, Feisty and Edgy in my menu.lst
```

# kopt=root=/dev/mapper/Ubuntu-rootGutsy ro
# kopt_2_6_20=root=/dev/mapper/Ubuntu-rootFeisty ro
# kopt_2_6_17=root=/dev/mapper/Ubuntu-rootEdgy ro

```

You need to use **vol_id** to get the UUID for each kopt entry as you're using UUID's.

Don't understand this. Needless to say, I need to study the GRUB tutorial some to make sense of this. But real quick, what does kopt do?

---

### Post by mlind on 2007-11-03
> **Klarsin said:**
> Don't understand this. Needless to say, I need to study the GRUB tutorial some to make sense of this. But real quick, what does kopt do?

You have different root partitions for each distribution and grub needs to know what these are if you're using the 'automagic kernel list -feature'. You used to have *root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c* in each kernel definition which would have been incorrect for Dapper and Mepis I guess, because those are in different partitions. This doesn't matter anymore as you seem to have removed Dapper kernels and moved Mepis below the 'automagic kernel list'.

---

### Post by Klarsin on 2007-11-03
> **mlind said:**
> You have different root partitions for each distribution and grub needs to know what these are if you're using the 'automagic kernel list -feature'. You used to have *root=UUID=972af1d0-babe-4e0d-adba-962e1c6bd37c* in each kernel definition which would have been incorrect for Dapper and Mepis I guess, because those are in different partitions. This doesn't matter anymore as you seem to have removed Dapper kernels and moved Mepis below the 'automagic kernel list'.

Thanks for defining it. I guess I'm all set now.

THE PROBLEM IN THIS THREAD HAS BEEN RESOLVED

---

