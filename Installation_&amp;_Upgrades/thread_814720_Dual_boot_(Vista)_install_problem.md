---
title: "Dual boot (Vista) install problem"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by dps77 on 2008-06-01
Hello,

I just attempted to complete a dual boot install on my laptop.  The laptop already had Vista and I installed Ubuntu 8.04 using instructions at [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm).

Everything went according to the instructions except that nothing appeared under the Migration Assistant portion of the "Ready to install" screen.  Perhaps (in retrospect) unwisely, I went ahead with the install after selecting the Windows Longhorn/Vista loader under the advanced options.  Now when I boot the laptop, it has the Vista option, but nothing happens when I select that option (it just returns to the OS selection menu).  Does this mean my Vista OS is gone?  Or is there any way to fix this (get the dual boot option) without a complete reinstall of both OS's?  Any help/advice would be greatly appreciated.

1st time Linux user

---

### Post by Pioneer5000 on 2008-06-01
Hi, i don't so but i'm not so sure im no linux pro but i do have Ubuntu 8.04 and Windows Vista running together on my laptop.

This is what i did but I'm not sure if this will be what you want to do. I reformatted Vista using the Vista disc and then created partition when installing Vista. So pretty much:

1. I just put in Vista disc that came with laptop and rebooted. Formatted current partition(s) and then deleted it. 

2. Then created new partition i just choose size 58000 (guess this will depend on how big your HDD is and how much you want to dedicate to Windows) for partition and installed Windows onto it. 

3. After doing that and having Windows fully installed, restarted computer now with Ubuntu disc in, choose the install Ubuntu option. 

4. When it came up to the partition part of the installation i just simply choose " Use largest contiguous free space" (not sure if it says free or empty) And since i had used half for windows the other half was free. Installed Ubuntu onto that and then i was done.

Now when i boot up comp it has both Ubuntu and Windows options and both working.

Not sure if this will help as you may not want to reformat HDD.

Edit:
Whoops, sorry didn't fully read your post before writing this as you stated you don't want to reformat.

---

### Post by meierfra. on 2008-06-01
> Does this mean my Vista OS is gone? 

Since Vista appears on the Grub Menu, I'm almost certain that  Visa is  still intact. But let's see what is going on:

Boot into Ubuntu, open a terminal (Applications->Accessories->Terminal)

Type

```
sudo fdisk -l
```
and

```
gksudo gedit /boot/grub/menu.lst
```
(both l are lowercase L)

Post the output here.

You  might also have a look at  your files on the Vista partition:
Go to Places->Computer. Double click the icon for  you  Vista partition. Just browse to see whether everything looks o.k

---

### Post by dps77 on 2008-06-01
Meierfra, I posted the info you specified below. thanks,  dps

> **meierfra. said:**
> Since Vista appears on the Grub Menu, I'm almost certain that  Visa is  still intact. But let's see what is going on:

Boot into Ubuntu, open a terminal (Applications->Accessories->Terminal)

Type

```
sudo fdisk -l
```
and

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313        7132    46742528    7  HPFS/NTFS
/dev/sda4            7133        9730    20861811+   f  W95 Ext'd (LBA)
/dev/sda5            9469        9730     2096128   dd  Unknown
/dev/sda6            7133        9365    17936541   83  Linux
/dev/sda7            9366        9468      827316   82  Linux swap / Solaris


```
gksudo gedit /boot/grub/menu.lst
```
(both l are lowercase L)

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
# kopt=root=UUID=81dd9f1c-cbee-4be5-adb2-0f88f1a3c590 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=81dd9f1c-cbee-4be5-adb2-0f88f1a3c590 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=81dd9f1c-cbee-4be5-adb2-0f88f1a3c590 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Dell Utility Partition
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
chainloader	+1


Post the output here.

You  might also have a look at  your files on the Vista partition:
Go to Places->Computer. Double click the icon for  you  Vista partition. Just browse to see whether everything looks o.k

***I looked here, but I did not see anything labeled as "Vista partition"

thanks!

---

### Post by meierfra. on 2008-06-01
Open "menu.lst" again via

> gksudo gedit /boot/grub/menu.lst



Add this to the end

title Windows Vista
root (hd0,1)
makeactive
savedefault
chainloader +1

Save the file. Reboot and see whether the new item on the Grub Menu works.

---

### Post by chex_m8 on 2008-06-01
I noticed that the vista partition (hd0,2) is the boot partition but you've installed grub on the linux partition (hd0,5). I would try making the linux partition the boot partition and see what happens.

---

### Post by RobHK on 2008-06-01
> **dps77 said:**
> Meierfra, I posted the info you specified below. thanks,  dps



***I looked here, but I did not see anything labeled as "Vista partition"

thanks!

It will probably just be labelled "Disk" but if you open it you will see the usual Windows directories like "Programme files" and "Windows".

Have you tried Super Grub? If not Google it. A boot disk that will find and boot Windows and Linux installations.

---

### Post by dps77 on 2008-06-01
> **meierfra. said:**
> Open "menu.lst" again via

Add this to the end

title Windows Vista
root (hd0,1)
makeactive
savedefault
chainloader +1

Save the file. Reboot and see whether the new item on the Grub Menu works.

********************

Hi,

I did as instructed above and got the following:

Starting up...
BOOTMGR is missing
Press Ctrl-Alt-Del to restart

When I hit Ctrl-Alt-Del, it just loops back to the message immediately above.  Now I can't get any OS to boot.

---

### Post by meierfra. on 2008-06-01
>  Now I can't get any OS to boot.

Turn the computer off with power button. Turn it back on and  see whether you  get to the grub menu and can boot into ubuntu.


(Edit: I don't think this will work)

---

### Post by meierfra. on 2008-06-01
Actually that probably  will not work.  But I think I know what happened (and also how to fix it)

Is it true that  you installed grub to the vista partition (using the advanced button in step 7 of the  Ubuntu installation)?

---

### Post by athaki on 2008-06-01
You'd probably save a lot of trouble if you just reformatted at this point.  Pioneer5000's post on how to do that would work the best.

---

### Post by RobHK on 2008-06-01
> **dps77 said:**
> ********************

Hi,

I did as instructed above and got the following:

Starting up...
BOOTMGR is missing
Press Ctrl-Alt-Del to restart

When I hit Ctrl-Alt-Del, it just loops back to the message immediately above.  Now I can't get any OS to boot.
Try the Super Grub disk I recommended above.

You could try FIXMBR to restore your Vista boot (from the Vista installation disk). You'll lose your Linux boot but you can get it back with SuperGrub. See:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by meierfra. on 2008-06-01
> You'd probably save a lot of trouble if you just reformatted at this point

 If my previous post is correct, it is easily fixed. Just give me a second, to write up instructions how to fix it.

---

### Post by chex_m8 on 2008-06-01
I still think your boot loader is looking in the wrong place for the boot files.

---

### Post by meierfra. on 2008-06-01
Try this

Boot from a Vista CD/DVD
click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type:

Bootrec /FixMBR
Bootrec /FixBoot
exit

This  should get you into vista. (if not you  will also have to  the set the boot flag to the Vista's partition. Come back here for help)

---

### Post by dps77 on 2008-06-01
> **meierfra. said:**
> Actually that probably  will not work.  But I think I know what happened (and also how to fix it)

Is it true that  you installed grub to the vista partition (using the advanced button in step 7 of the  Ubuntu installation)?

*************

Um... on the "Ready to install" screen, I opened the "Advanced" tab and chose Longhorn/Vista loader.  Otherwise I exactly followed the instructions at: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

I don't remember anything about grub mentioned in those instructions.  I never heard about grub until now.

---

### Post by meierfra. on 2008-06-01
Just a sort explanation what happened. The OP had installed Grub to the boot sector of  the Vistas partition (hd0,2).  This overwrites the Vista boot sector, making it unbootable. The MBR still  was intact and is just trying to boot  the active partition.  The active partition was (hd0,2) , the location of Grub. So the OP was able to get to  the grub menu. But choosing Vista   just tells grub to look for boot information on (hd0,2).  So it goes back to grub.

I  told the OP to use "root (hd0,1), makeactive". This turned (hd0,1) into the active partition.  So now the MBR is looking for boot information on (hd0,1), but (hd0,1) does not contain any boot information giving "BOOTMGR is missing".

"FixBoot" will restore the boot sector of the Windows partition. I'm not sure whether "fixmbr" will automatically set the boot flag to the MBR, but I think it will. (If not this can easily be done with the Ubuntu liveCD)

---

### Post by meierfra. on 2008-06-01
> m... on the "Ready to install" screen, I opened the "Advanced" tab and chose Longhorn/Vista loader

O.K then my diagnosis is  right. And my fix should work. Just start with "FixMBR" and "FixBoot" from the VistaCD (see post 15)

---

### Post by meierfra. on 2008-06-01
After "FixBoot' and "FixMBR" you will have to reinstall grub.

Was there a particular reason you choose Vista on the advanced tab? Did you want the  keep the MBR intact?  If this is true, I recommend using EasyBCD (see my signature)

If not this will install Grub to the MBR  and let you boot into Vista and  Ubuntu. (Grub is just the Bootloader, Ubuntu uses)



Boot from the Ubuntu LiveCD. Open a terminal and type

```

sudo grub
```
and at the grub prompt:


```
root (hd0,5)
setup (hd0)
quit
```

Reboot. For vista choose  " Windows Vista/Longhorn (loader) from the Grub Menu.

Also the next time  you boot into ubuntu,  delete the "Windows Vista" item from menu.lst which I had told you to add.

---

### Post by dps77 on 2008-06-01
> **meierfra. said:**
> Try this

Boot from a Vista CD/DVD
click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type:

Bootrec /FixMBR
Bootrec /FixBoot
exit

This  should get you into vista. (if not you  will also have to  the set the boot flag to the Vista's partition. Come back here for help)

**************************

Ok, I followed the instructions as best as I could.
-I clicked on ""Repair your Computer"
-No OS was listed (it said to load hard disc drivers in this case, but I just clicked on next anyway)
-I opened command prompt and entered specified commands (each said it was successful)
-I restarted, but Vista did not boot
[also: I ran the "Startup repair" option and its report said: "Boot manager is missing or corrupt.  File repair failed."

So perhaps I need to set the boot flag as you mentioned?  Can you explain how to do that?  Or do I need to reinstall each OS from scratch?  

BTW- thanks for providing so much help with this!

---

### Post by meierfra. on 2008-06-01
I'm not sure the  boot flag will  make a difference, but it is worth a try:

Boot  with the Ubuntu LiveCD. Open a terminal  and type

```
sudo cfdisk /dev/sda 
```

Select your Vista partion (/dev/sda3)  and use the "boot" tab on the bottom to set a boot flag to the Vista Partition. Next select /dev/sda2 and use "boot"  to remove the boot flag. Then use the "write" to save the settings.
(Use the left and right arrow keys to select a "tab" and "enter" to execute a tab)

---

### Post by meierfra. on 2008-06-01
If changing the boot flag did not make a difference, get EasyBcd (see my signature) EasyBCD is a nice boot loader for Vista and  also has the ability to  fix the boot sector:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD")

Using EasyBCD it is fairly easy to add Ubuntu to the Vista's Boot menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by dps77 on 2008-06-02
> **meierfra. said:**
> If changing the boot flag did not make a difference, get EasyBcd (see my signature) EasyBCD is a nice boot loader for Vista and  also has the ability to  fix the boot sector:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD")

Using EasyBCD it is fairly easy to add Ubuntu to the Vista's Boot menu:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

***************************

meierfra,

Thanks for all your help!  At this point, I am just going to reinstall Ubuntu without the dual boot option.  I'll try out Linux and see how I like it.  I can always go back to Vista later.

thanks again!

---

### Post by meierfra. on 2008-06-02
If you follow my post #19 you will be back in ubuntu within fives minutes. I'm  at least 99.9 % sure that it work.

---

