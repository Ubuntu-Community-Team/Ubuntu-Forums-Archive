---
title: "How to install Ubuntu and Kubuntu on 2 different partitions"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by tralogik on 2007-09-13
Hi,

How can I have both Ubuntu and Kubuntu on the same drive but on different partitions.

I want to try both and the best way to the find the one I prefer is to use them independently. I know that there is a thing called Kubuntu-desktop which allows to have both OS on the same partition, but I don't really like it since all functions are mixed together.

Do I need to have 2 swaps? And 2 roots (/)? 

I am new with Linux and would love to have both OS on my machine (with XP also).

Thanks!!

JS

---

### Post by rfruth on 2007-09-13
On Ubuntu CD is the gparted utility, use it to make room for Kubuntu install - what you want to do is smart & very doable :)

---

### Post by tralogik on 2007-09-13
Hi rfruth,

Thanks for that quick answer and those encouraging comments!

Is this operation easy to do? As I mentioned, I am a newbie on Linux and I don't want to destroy everything.

Thanks!
JS

---

### Post by rfruth on 2007-09-13
Gparted is easy, not many options and menu driven but may need to edit menu.lst file afterwords, Id'e start with a dual boot (XP & Ubuntu) - do the live CD thing with Kubuntu (unless you have lots of free hard disk space and must have a triple boot system (if dual boot is too easy can add 3rd OS later))

---

### Post by tralogik on 2007-09-14
Hi rfruth,

I am at the point where both Ubuntu and Kubuntu are installed on my HD (with Win XP).

My partitions are as follows:

HD = 40 GB
hda1 - fat32 - 20003 MB
hda5 - swap (**Ubuntu**) - 1003 MB
hda6 - / (**Ubuntu**) - 6999 MB
hda7 - /home (**Ubuntu**) - 5000 MB
hda8 - / (**Kubuntu**) - 7007 MB

Of course I can change the size of these partitions if I need to set a swap and a "/home" folder for Kubuntu.

When I start my computer, the "triple-boot"(??) list contains:
-[I] Ubuntu, kernel 2.6.20-16-generic
- Ubuntu, kernel 2.6.20-16-generic (recovery mode)
- Ubuntu, kernel 2.6.20-15-generic
- Ubuntu, kernel 2.6.20-15-generic (recovery mode)[/I]
- memtest 86+
Other operating systems
Microsoft Windows XP Professional
- Ubuntu, kernel 2.6.20-16-generic
- Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda6)

The strange thing is that the first 4 options (in italics in this post) will load **Kubuntu** and not Ubuntu. I tried to change the name in Kubuntu's menu.lst but I am not authorized to do so. And I can't change the name of those 4 options in Ubuntu's menu.lst because they don't appear in the list. (I hope I am clear - English is not my first language).

I tried to create a swap for Kubuntu but I had an error called something like (grub error 15).

I have to tell you that I have another 120 GB HD (with about 30GB free). Would it be easier to install Kubuntu on that disk and leaving XP and Ubuntu on the first HD? And by doing so, would it be possible to have the "triple-boot option"?

I really appreciate the time you take to help me and I am sure we (you) are about to find a solution :)

---

### Post by forestpixie on 2007-09-14
can you open a terminal, do these and post the ouptuts, close the menu.lst after

```
gedit /boot/grub/menu.lst
```

```
sudo fdisk -l
```

---

### Post by tralogik on 2007-09-14
Hi forestpixie,

Should I do it in Ubuntu or in Kubuntu?

---

### Post by tralogik on 2007-09-14
Hi forestpixie,

Here is my menu.lst in Ubuntu. The F-disk list follows (I am sorry my system is in French).

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
# kopt=root=UUID=2e97a40e-1043-4f12-9e87-7ef0883a8cdc ro

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

## ## End Default Options ##

title		Kubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e97a40e-1043-4f12-9e87-7ef0883a8cdc ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=2e97a40e-1043-4f12-9e87-7ef0883a8cdc ro single
initrd		/boot/initrd.img-2.6.20-16-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


**AND THE F-DISK:**

Disque /dev/sda: 40.0 Go, 40020664320 octets
255 têtes, 63 secteurs/piste, 4865 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1        2432    19535008+   c  W95 FAT32 (LBA)
/dev/sda2            2433        4865    19543072+   5  Extended
/dev/sda5            2433        2554      979933+  82  Linux swap / Solaris
/dev/sda6            2555        3405     6835626   83  Linux
/dev/sda7            3406        4013     4883728+  83  Linux
/dev/sda8            4014        4865     6843658+  83  Linux

Disque /dev/sdb: 120.0 Go, 120034123776 octets
255 têtes, 63 secteurs/piste, 14593 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdb1               1       12303    98823816    7  HPFS/NTFS



Thanks!!

---

### Post by Pumalite on 2007-09-14
Something is wrong in your menu.lst. You cannot have Ubuntu and Xubuntu in the same partition (hd0,5). Figure out which is which and change the line 'root (hdx,y) in each one accordingly. If you installed Xubuntu in sda8 (as an example), then 'root' for Xubuntu in menu.lst should be (hd0,7).etc.

---

### Post by tralogik on 2007-09-14
Hi Pumalite,

I think I will restart the installation from scratch. I don't mind, I have nothing important on Ubuntu and Kubuntu.

What if I go this way:

hda1 - fat32 (for Win XP) 20000 MB
hda5 - swap (for Ubuntu) - 1000 MB
hda6 - / (for Ubuntu) - 5000 MB
hda7 - /home (for Ubuntu) - 4000 MB

And for Kubuntu, do I need to have another swap and another /root??

hda8 - swap (for Kubuntu) - 1000 MB
hda9 - / (for Kubuntu) - 5000 MB
hda10 - /home (for Kubuntu) -  4000 MB

BTW, I don't know anything about things like hd0,5 and hd0,7.

Many thanks!!

---

### Post by Pumalite on 2007-09-14
First of all, you don't need more than one swap (it's hardly used at all)
Second it looked to me last time I checked, that you had both systems installed and that you only had to edit your menu.lst: in Terminal:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst

This was your menu.lst last time I checked:

title Kubuntu, kernel 2.6.20-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2e97a40e-1043-4f12-9e87-7ef0883a8cdc ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=2e97a40e-1043-4f12-9e87-7ef0883a8cdc ro single
initrd /boot/initrd.img-2.6.20-16-generic

Here:

title Kubuntu, kernel 2.6.20-16-generic
root (hd0,5)

You have to change (hd0,5) to (hd0,7)
That's it
Save, exit, reboot.

---

### Post by tralogik on 2007-09-14
I have to leave for a few hours.

Can't wait to do what you told me!!!

Thanks!!!

---

### Post by tralogik on 2007-09-14
Do you think I need to have 2 "/home" (1 for each OS)?

---

### Post by Pumalite on 2007-09-14
Yes. Also post: blkid
We'll need it to change UUID's

---

### Post by santy_kushwaha on 2007-09-14
i didnt knew that we will get so much of the greve for downloadingt two operating system in the same box . i install two different version of linux on same tower one was suse and other was ubuntu on the 20GB hard drive never got the problem and i just went to do settings of the hard drive during instalation and thats all and i good to go then   
     might u try again might help

---

### Post by tralogik on 2007-09-14
Pumalite, I am unable to change the menu in Kubuntu anymore. Is it through sudo gedit /boot/grub/menu.lst? If so, it did not work. Therefore, I can't not change the hd0,5 and hd0,7. Is there another way to do it? And do I have to make those changes under Ubuntu or Kubuntu?

Thanks again!!!

santy_kushwaha: I don't think I got your point. Good for you if you did not have any issues with the installation of 2 OS! Things don't seem to be as easy here. I tried many things before I came here and fortunately there are great people on this forum to help us!

---

### Post by Pumalite on 2007-09-14
The menu.lst that you posted was not right. Was pointing to the wrong partitions according to your fdisk. So we need to change that or your system will not boot. What is the problem with: sudo gedit /boot/grub/menu.lst?

---

### Post by tralogik on 2007-09-15
Hi,

I know that the menu posted yesterday (Friday) was not right, but I cannot access the menu.lst in Kubuntu anymore to change the settings you told me to change (hd0,5 and hd0,7). I get the following message : 
sudo: gedit: command not found

I have to tell you that both systems start normally (from what I can see). I can choose the 3 OS when I launch my computer.

The problem this morning is that I just can't access that menu.lst to do what you told me.

Thanks!!

---

### Post by Pumalite on 2007-09-15
Forget about it then. You have a working system!

---

### Post by tralogik on 2007-09-15
Yes it is great, but there must be a way to get the menu.lst in Kubuntu...

Aren't Ubuntu and Kubuntu supposed to speak the same language?

---

### Post by Pumalite on 2007-09-15
You might need a different editor (gedit is my personal favorite); you can use 'vi', 'vim'. 'nano'

---

### Post by tralogik on 2007-09-15
This is my menu.lst in Ubuntu. Kubuntu is not there anymore... I wonder what happened to my PC while I was sleeping. I must have "sleepwalked"!



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
timeout		30

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
# kopt=root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro single
initrd		/boot/initrd.img-2.6.20-16-generic


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by tralogik on 2007-09-15
I think those changes occurred when I created a /home for Kubuntu, as you told me to. Is it possible :confused:

---

### Post by Pumalite on 2007-09-15
Do you have a choice of all three and are you able to boot all three OS's?.

---

### Post by tralogik on 2007-09-15
Yes I have the choice of the all three when I boot, but the menu has changed and is back to what it was when I first posted my message:

[I]- Ubuntu, kernel 2.6.20-16-generic
- Ubuntu, kernel 2.6.20-16-generic (recovery mode)
- Ubuntu, kernel 2.6.20-15-generic
- Ubuntu, kernel 2.6.20-15-generic (recovery mode)[/I]
- memtest 86+
Other operating systems
Microsoft Windows XP Professional
- Ubuntu, kernel 2.6.20-16-generic
- Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda6)

The strange thing is that the first 4 options (in italics in this post) will load Kubuntu and not Ubuntu. And I can't change the name of those 4 options in Ubuntu's menu.lst because they don't appear in the list as you could see in a earlier post.

It seems that all changes done to the menu.lst are not saved. I have modified the number of seconds for showing the choice of OS (i.e. from 10 to 30 secs) and when I boot, it is back to 10 secs.

Is there anything with the menu I've just posted?

---

### Post by forestpixie on 2007-09-15
just to let you know tralogik - if you're in kubuntu you need to use kate instead of gedit

---

### Post by Pumalite on 2007-09-15
It seems that Ubuntu is lost somewhere. What partition is it in?.
Post: sudo fdisk -lu (copy and paste)

---

### Post by tralogik on 2007-09-15
Thanks for the information, forestpixie. It will help me.

Pumalite, here is what you wanted. Sorry, it is all in French, please tell me if you need help... The text in bold says something like the partition table inputs(?) are not in the disk's order.


sudo fdisk -lu
j-sebastien@j-sebastien-desktop:~$ sudo fdisk -lu
Password:

Disque /dev/hda: 40.0 Go, 40020664320 octets
255 têtes, 63 secteurs/piste, 4865 cylindres, total 78165360 secteurs
Unités = secteurs de 1 * 512 = 512 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hda1   *          63    39070079    19535008+   c  W95 FAT32 (LBA)
/dev/hda2        39070080    78156224    19543072+   5  Extended
/dev/hda5        39070143    41030009      979933+  82  Linux swap / Solaris
/dev/hda6        41030073    50797529     4883728+  83  Linux
/dev/hda7        50797593    58605119     3903763+  83  Linux
/dev/hda8        68388768    78156224     4883728+  83  Linux
/dev/hda9        60581178    68388704     3903763+  83  Linux

**Les entrées de la table de partitions ne sont pas dans l'ordre du disque**

Disque /dev/hdb: 120.0 Go, 120034123776 octets
255 têtes, 63 secteurs/piste, 14593 cylindres, total 234441648 secteurs
Unités = secteurs de 1 * 512 = 512 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdb1              63   197647694    98823816    7  HPFS/NTFS

---

### Post by Pumalite on 2007-09-15
You have 4 Linux partitions: 6 to 9. Which is which here?. Do you remember where you put Ubuntu and where you put Kubuntu?

---

### Post by tralogik on 2007-09-15
If it can help you, here is what I get when I do sudo kate /boot/grub/menu.lst (in Kubuntu):

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
DCOP aborting call from 'anonymous-5362' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

---

### Post by tralogik on 2007-09-15
Ok, I have just discovered something. I can make (and apply) all the changes in Kubuntu's menu. Here is what I get when I enter sudo kate /boot/grub/menu.lst.

As you can see, the values are now (hd0,7) for Kubuntu and (hd0,5) for Ubuntu. Is it okay this way? Do you still want me to post the blkid to change the UUID's (It looks Chinese for me!) ? If so, in Ubuntu or in Kubuntu???


____________________
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
# kopt=root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=52aa2dc1-c807-487e-a9be-909fe4c0436b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-16-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro single 
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/hda6)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e50f28ae-b8f9-4221-a11d-ab437613880f ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda6.
title		Ubuntu, memtest86+ (on /dev/hda6)
root		(hd0,5)
kernel		/boot/memtest86+.bin  
savedefault
boot

---

### Post by Pumalite on 2007-09-15
Look; you have to remember where you put what, I would change the Title according to that and I would change the enty for 'root' according to that. AS an example: how did you know you were in Kubuntu? I don't see the name Kubuntu anywhere.

---

### Post by tralogik on 2007-09-15
No problem. I know it is Kubuntu or Ubuntu because I tried every option and I saw the opening screen of the OS. Therefore, I am positive that the first four options (with hd0,7) are for Kubuntu and the other four (with hd0,5) are for Ubuntu. Regarding memtest86+, I did not try them.

Regarding the absence of Kubuntu's name, this is strange. I can change it though in the menu (using sudo kate...) but it did not do it because I did not want to do things that I was not "allowed" to. Do you want me to change that menu and post it after?

---

### Post by Pumalite on 2007-09-15
Then; if you have a working system and you can boot in either Ubuntu or Kubuntu; stay put. You don't need anything else.

---

### Post by tralogik on 2007-09-15
Well, I guess it is done!

One last thing: I want to thank Pumalite, forestpixie and rfruth. You guys are the best =D>. Whenever you come to Montreal (Canada), drop by, I owe you a couple of beers (or coffees)!

Merci beaucoup!! (Thank you very much!!)

JS

---

### Post by Pumalite on 2007-09-15
I've been in Montreal. It's great. I'm happy you are happy with your system.

---

### Post by tralogik on 2007-09-15
I am more than happy!

Sorry Mr. Gates, but I found something else!!!!

---

