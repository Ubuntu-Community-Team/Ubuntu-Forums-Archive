---
title: "how do I unstall xbuntu??"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by calldrin on 2007-10-06
I have both ubuntu and xbuntu installed in a dual boot xp system.
Ubuntu 7.04 was installed about 2 weeks is running fine. 

Then I installed/added xbuntu xfce  and now I want to go back and just use xp and ubuntu.

Can I just remove xbuntu or do I have to start all over with a new install.

My search has not come up with answers that would apply to this situation.

Please give me complete instructions if possible.

Also I plan on upgrading to the version as soon as it is released.
 
Thanks from a newbie,

Chuck

---

### Post by El Rogueo on 2007-10-06
If you have all three installed, you could just format the partitions that contain xubuntu and leave the ubuntu ones

Unless you're saying you changed from xubuntu to ubuntu?

---

### Post by calldrin on 2007-10-06
> **El Rogueo said:**
> If you have all three installed, you could just format the partitions that contain xubuntu and leave the ubuntu ones

Unless you're saying you changed from xubuntu to ubuntu?
My 1 st install was ubuntu, this was the method that the partitions were set up with.
Then  yesterday, I saw some info about using xbunto/xfce so I followed the instructions and installed it. I have no idea if any more partitions were added :-(
 Since xbuntu is not what I wanted, I would like to go back to using ubuntu and uninstall xbuntu.
Since I'm so new using linux, I have a hard time explaning what is going on ;-(

Chuck

---

### Post by Pumalite on 2007-10-06
Let me know if you are in Ubuntu or Xubuntu. If you can get to Ubuntu, then, from there and from the terminal, post:

cat /boot/grub/menu.lst

Also post:

sudo fdisk -lu

---

### Post by calldrin on 2007-10-06
> **Pumalite said:**
> Let me know if you are in Ubuntu or Xubuntu. If you can get to Ubuntu, then, from there and from the terminal, post:

cat /boot/grub/menu.lst

Also post:

sudo fdisk -lu
Here are the results as requested.

Chuck



chuck@chuck-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fa96bfee-95c4-465d-9f63-1c6988795e0a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=fa96bfee-95c4-465d-9f63-1c6988795e0a ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=fa96bfee-95c4-465d-9f63-1c6988795e0a ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=fa96bfee-95c4-465d-9f63-1c6988795e0a ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=fa96bfee-95c4-465d-9f63-1c6988795e0a ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

chuck@chuck-desktop:~$ 

------------
chuck@chuck-desktop:~$ sudo fdisk -lu
Password:

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    78782759    39391348+   7  HPFS/NTFS
/dev/hdb2       120085875   120101939        8032+  82  Linux swap / Solaris
/dev/hdb3        78782760   120085874    20651557+  83  Linux

Partition table entries are not in disk order
chuck@chuck-desktop:~$

---

### Post by Pumalite on 2007-10-06
Well, you have both in sdb3 and Ubuntu is managing the Grub. So, what exactly do you want to do?
It might all be a matter of:

sudo apt-get remove xubuntu-desktop

---

### Post by calldrin on 2007-10-06
I would like to remove all the xbuntu stuff and return to my original install of ubuntu.
When I boot now, at login/passsword, the title of the "box" says xbuntu. I also have a choice of boot options. This was not there untill I installed xbuntu.
 I'm sorry that I'm such a boob!.. I should have just waited until 7.10 was ready and just updated then... But no!!!.. not me I like to tinker too much and now got my butt spanked ;-)

Chuck

---

### Post by Pumalite on 2007-10-06
The problem id that according to fdisk everything is in one partition. Wait ten days and after saving your data do a clean install of Gutsy.

---

### Post by calldrin on 2007-10-06
> **Pumalite said:**
> The problem id that according to fdisk everything is in one partition. Wait ten days and after saving your data do a clean install of Gutsy.

When I ran the command, It got rid of a lot of files but it tells me to use" apt-get autoremove"  to remove several others.
I tried to save the report to the desktop thinking I could send it to you but it is a .png file and I don't know what to do to send it to you.

I like your suggestion about waiting until the new release is out.

This brings another question. How do I and what files do I  save for my data that I need to transfer to the new system?


/home/chuck/Desktop/Screenshot-chuck@chuck-desktop: ~.png

Thanks again for all your help..You folks are GREAT ;-)

Chuck

---

### Post by Pumalite on 2007-10-06
I would go ahead with apt-get autoremove. You save /home, including 'Hidden Files' Of course your music, movies,etc.

---

### Post by calldrin on 2007-10-06
I feel so dumb... how and where is apt-get ???

chuck

---

### Post by calldrin on 2007-10-06
I found it and it did remove a lot of files.

Thanks again,
Chuck

chat with you again when the new verson is out!!

---

### Post by Pumalite on 2007-10-06
You are welcome. Good luck.

---

### Post by andrewsomething on 2007-10-14
Try:

```
sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce gxine hal-cups-utils libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing3 libchewing3-data libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-common libgoffice-gtk-0-3 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libpulse0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine1 libxvmc1 mousepad mozilla-thunderbird orage python-cups python-exo scim-anthy scim-chewing scim-hangul scim-pinyin system-config-printer thunar thunar-archive-plugin thunar-doc thunar-media-tags-plugin thunar-volman-plugin vim-runtime xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

---

