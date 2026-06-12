---
title: "Windows won't boot with GRUB"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by Curlydave on 2005-05-21
If I select winXP from GRUB, it shows some text on screen, but won't do load. What's up?

---

### Post by Xian on 2005-05-21
Provide a few things to start:

1. The output of this terminal command: 
$ sudo fdisk -l

2. The contents of your /boot/grub/menul.lst file.

---

### Post by Curlydave on 2005-05-21
1. That terminal command appears to do nothing- I get no output. However, if I leave out the -|, it gives me a list of my drives etc.

2. That file is kinda long, so I'll wait until I can figure out how to get my PPPoE internet set up so I can copy+ paste. (If you know how to set up PPPoE, I'd love to know! I know how to do it in Knoppix, but Ubuntu only lets me to DHCP.)

Here's the output of what happens when I try to boot into windows wiht grub:

Booting "Microsoft Windows XP Pro"

root (hd1,0)
filesystem type unknown, parition type 0x7
savedefault
make active
chainloader +1

---

### Post by Xian on 2005-05-21
[QUOTE=Curlydave]1. That terminal command appears to do nothing- I get no output.[/QUOTE]
Okay, that's a "-l" [small letter 'L'] , not a -|.

Basically, we should be able to compare your partition scheme with your menu.lst and determine what needs to be altered to get you into your windows install. That's why those two things are generally needed to proceed.

---

### Post by Curlydave on 2005-05-21
K, I got online and did it with an "L", here they are!

1:
sudo: unable to lookup amd64 via gethostbyname()

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4665    37471581   83  Linux
/dev/hda2            4666        4866     1614532+   5  Extended
/dev/hda5            4666        4866     1614501   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9732    78172258+   7  HPFS/NTFS
david@amd64:~$
david@amd64:~$


2:
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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro console=tty0

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default 
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic Default (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz root=/dev/hda1 ro console=tty0 single
initrd		/boot/initrd.img
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda1 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-amd64-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-amd64-generic root=/dev/hda1 ro console=tty0 single
initrd		/boot/initrd.img-2.6.10-5-amd64-generic
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

---

### Post by Curlydave on 2005-05-22
Bumpsicles!

---

### Post by jrasith on 2005-05-29
You have the same issue that I have, did you find a solution?

Peace;
-Joshua

---

### Post by myoda on 2005-05-29
I have the same problem. I've done heaps googleing and i've tried a few changed to my menu.lst file under the "windows xp.." section but to no avail.

I get "Error 29: cannot mount drive" or a similar message when I try to boot into windows xp, ubuntu boots fine.

Could someone post a working menu.lst file. And please let us know if you have to change something in your bios to get it to work.

Thanks
Abhi

---

### Post by myoda on 2005-05-29
ok, to get windows booting again,

you have to put in the cd, let it load.

and hit "R" when asked if u want to install windows again, or recovery or quit.

this will take you to the recovery console which is just "C:\" and type in..... "fixboot"?? i think it fixboot.

That should fix your windows boot.

However, now I find that I have no GRUB... and am having  a lot of difficulty installing it.!!!!

GRRR

I might just install mandriva, which i'll cut down to size, as a third distros, at least I don't have to deal with grub... I get Lilo.

---

### Post by jsuen on 2005-06-12
[QUOTE=myoda]ok, to get windows booting again,

you have to put in the cd, let it load.

and hit "R" when asked if u want to install windows again, or recovery or quit.

this will take you to the recovery console which is just "C:\" and type in..... "fixboot"?? i think it fixboot.

That should fix your windows boot.

However, now I find that I have no GRUB... and am having  a lot of difficulty installing it.!!!!

GRRR

I might just install mandriva, which i'll cut down to size, as a third distros, at least I don't have to deal with grub... I get Lilo.[/QUOTE]
 using the windows recovery console (R off booting with an XP cd) and typing fixboot (? something to that effect) would reset your MBR, where installing ubuntu on your hd would've added grub to the MBR.

to re-add grub to the MBR, you can try this:
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)
given that, i can't say that you won't arrive at the problem you've had before myoda (that XP won't boot again..)

i've managed to get winXP & 98 bootable through grub off a slave hd (win 98 was my master drive, xp and hoary on my slave), along with ubuntu - i'll post my menu.lst in here soon (someone pls pm me if i forget)

---

### Post by daenney on 2005-06-14
Thats weird.
I dualboot WinXPPro and Ubuntu 5.04 without a glitch. 
I do notice one differenc...
My menu.list to boot Windows XP Pro is hd0,0 and not hd0,1 maybe you need to give that a try...

NEVER EVER EVER use Windows Recovery console to fixmbr bnecause then you'll lose Grub and the easiest way to get it back is to reinstall ubuntu from scratch.
before doing something stupid like fixmbr you might actually bother to check what it exactly does.

---

### Post by pietro_spina on 2005-06-14
[QUOTE=Curlydave]title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1[/QUOTE]

My experience, getting windows to boot when it was not the first operating system installed on the first primary partition was a similar failure.  To get it to work and it is working wight now...

I use the [map](http://www.gnu.org/software/grub/manual/html_node/map.html)  commands in grub...

So my windows entry looks something like this... (this from memory, not at my linux box right now.)

```
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0
root		(hd1,0)
makeactive
chainloader	+1
```

I'm not sure if the map comands come before or after the "root" command. I'll check tonight or maybe not...  :-) 

[edit] oh and you might have to say
root (hd0,0)  or something...

and stay away from the windows tools the fix is through Linux...[/edit]

cheers,
p

---

### Post by wake-kitty on 2005-06-14
when i messed up with my grub, i just poped in the kubuntu cd (thats what i use) then go through the set up process without formatting the partitions up to the point where it will install grub. im new to linux so im not really familiar with linux commands.

---

### Post by alastair lewis on 2005-06-14
[QUOTE=wake-kitty]when i messed up with my grub, i just poped in the kubuntu cd (thats what i use) then go through the set up process without formatting the partitions up to the point where it will install grub. im new to linux so im not really familiar with linux commands.[/QUOTE]

Did this work? I just scrubbed winXP booting by trying to get the splashscreen working. All I did was add, then remove the approiate path to spalshimage in /boot/grub/menu.lst.
I have no idea what has happened as the rest of the file is unchanged. I don't need the XP partition for much, but I do need it badly (My surgeons logbook does not have a linux alternative).
I have spent a lot of effort configuring Wifi and network printing for Hoary and I don't want to lose it.

---

### Post by manicka on 2005-06-14
[QUOTE=myoda]ok, to get windows booting again,
this will take you to the recovery console which is just "C:\" and type in..... "fixboot"?? i think it fixboot.
.[/QUOTE]
it's fixmbr

---

### Post by pietro_spina on 2005-06-14
OK, this is my setup. It will work for windows dual boot ifwindows is installed on a separate hard drive and that hard drive is set as slave...

```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1
boot
```

[COLOR=Magenta]alastair lewis[/COLOR]- I think this thread is discussing something a bit diferent than your problem.  I'd suggest editing/deleting your post here and starting a new thread. (Youmight get more help that way. This thread is kinda old and tired... hehehe)  You should probably post your menu.lst as well.

-p

---

### Post by linuxNewb on 2005-12-02
In another thread, someone with the same --original-- problem claims it was a "bios protection" issue. He said he turned off the "bios protection" and windows booted fine. 

I am having the same problem, but I don't know what the h*** "bios protection" means.

---

### Post by al7kz on 2005-12-06
the map commands come after the root (or rootnoverify) commands

---

### Post by BLTicklemonster on 2005-12-06
If you are using two hard drives, and ubuntu is on the master and windows is on the slave (you installed it like that, I mean), then the following works. I had the same problem. Just boot into kubuntu/ubuntu and in the terminal 

sudo gedit /boot/grub/menu.lst

then make the changes listed below.


[QUOTE=pietro_spina]OK, this is my setup. It will work for windows dual boot ifwindows is installed on a separate hard drive and that hard drive is set as slave...

```
title Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
chainloader +1
boot
```

[COLOR=Magenta]alastair lewis[/COLOR]- I think this thread is discussing something a bit diferent than your problem.  I'd suggest editing/deleting your post here and starting a new thread. (Youmight get more help that way. This thread is kinda old and tired... hehehe)  You should probably post your menu.lst as well.

-p[/QUOTE]
Also, I hate the way it has several ubuntus with kernels listed at the top, and windows at the bottom when it loads, so I changed mine to this:

```
## ## End Default Options ##

title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title           Now back to other linux versions
root 

[COLOR="Red"](pick up where it left off here....)[/COLOR]

```

So now it shows ubuntu then windows. I need to remove that part about other operating systems, that's silly to leave that in there now that I know what's going on...

Anyway, try that.

(okay, I lied, I originally had windows as the master, and ubuntu as slave, had problems, switched the drives, jumpered them to master and slave, not cs, set the drives as lba, not auto in bios with the grub menu list already edited, and it booted up fine)

---

