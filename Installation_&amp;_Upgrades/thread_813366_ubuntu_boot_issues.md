---
title: "ubuntu boot issues"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by sprightlyone on 2008-05-30
hi 
  i`m reposting as i can`t get a resolution in previous posts 
i`ve installed the alternate cd as it is the only d/load i seem to be able to get to work  i have dual boot set-up &can boot to windows but when i sel ubuntu it starts loads splash screen the orange bar does its thing up until about 3/4 bar then stops 
 i tried most suggestions ended up at various prompts don`t know which command to use @which prompt to getany info from system to see if errors / info posted can help someone give me resolution 
  can someone help me extract some info from my install 
 thanks lyle

---

### Post by Pumalite on 2008-05-30
Edit menu.lst and remove 'quiet splash'. That will allow you to see where it gets stuck.

---

### Post by sprightlyone on 2008-05-30
hi
  forgive my newness but which of the prompts do i access the boot menu list at??? &which command ??
  thanks lyle

---

### Post by Pumalite on 2008-05-30
Back it up first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst
Make the changes. Save, exit and reboot.

---

### Post by sprightlyone on 2008-05-30
hi
 i  triedthe command prompt @the dual-boot screen it is "grub>cursor "is this the right one ?????
 if it is i couldn`t get to command line to work

i am puzzled:confused:
lyle

---

### Post by Pumalite on 2008-05-30
Applications>Accessories>Terminal
Copy and paste the commands one at the time.

---

### Post by sprightlyone on 2008-05-30
hi
  i think you have misunderstood me
 i can`t get past the dual boot selector screen &any prompts accessable from there 
 lyle

---

### Post by Pumalite on 2008-05-30
Can you get into Recovery Mode?

---

### Post by sprightlyone on 2008-05-30
> **Pumalite said:**
> Can you get into Recovery Mode?
 yes i can access all the options in the recovery mode console just don`t know what to do when i`m there :confused:
 lyle

---

### Post by Pumalite on 2008-05-30
Try post # 4

---

### Post by sprightlyone on 2008-05-30
hi 
  i go to recovery mode &get 3 options 1 normal boot 2root shell prompt 
 3 x-fix server 
 i choose the prompt option
  ist cmd in post#4 error does not recognise command
  2nd cmd gives error"(gksudo:4774):GTK=WARNING**cannotdisplay:
 prompr in recovery mode is ROOT@ubuntubrutus :/# cursor 
lyle

---

### Post by meierfra. on 2008-05-31
At the grub menu at boot up (you might have to press "Esc" to get to the grub menu) select ubuntu, but do not press "enter", press "e" instead. At the new screen  select the second line. Press "e" again. Edit the line. Press "enter" and then "b" to boot.



You can also do  the changes in the recovery  mode, but you have to use

```
nano /boot/grub/menu.lst
```

(you don't need "sudo" or "gksudo" since you are already logged in as root. Also "gedit" is a graphical editor which does not work in a terminal)

---

### Post by sprightlyone on 2008-05-31
hi 
 just tried something from another post &am finally getting info i don`t fully understand 
 so here it is :  if i start @tis prompt "grub> cursor " with this cmd i get (hd0,4)
 this cmd "setup (hd0)
 i get checking if "/boot/grub/stage1 exists......yes
       checking if "/boot/grub/stage2 exists......yes
      checking if "/boot/grub/e2fsstage1_5(hd0) 16 sectors embedded
  succeeded 
running"install/boot/grub/stage1(hd0)#16p(hd0,4)/boot/grub//menu.lst" succeded 
 done   
 who can decipher this for me &point me to the next stage of resolution 
  thanks lyle

---

### Post by sprightlyone on 2008-05-31
> **Pumalite said:**
> Edit menu.lst and remove 'quiet splash'. That will allow you to see where it gets stuck.
 i removed as suggested &discovered that the page stalled on starting acpi so back in &turn of acpi
then finish on this "check root=bootarg cat/proc/cmdlineor misswing modules,devices:cat/proc/modules  ls/dev
alert! /dev/disk/by-uuid/b222d775-se17-481b-8fe3-4728f49627d2 does not exist "
busybox v1.1.3(debian 1:1.1.3-5ubuntu12)built in shell (ash)
enter help for commands 
initramfs cursor 
 where to now ???or what does this say in plain english???:confused::confused:
thanks lyle

---

### Post by Pumalite on 2008-05-31
I can only suggest to you to burn a new CD after doing md5sum, at 4x or less in good quality CD-R

---

### Post by sprightlyone on 2008-05-31
hi
  the disc also has a rescu8e mode option  it has a lot of options but which one /s would get me running if any ???
 thanks lyle

---

### Post by Pumalite on 2008-05-31
You should use it the regular way. We are assuming you had a bad burn.
[https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6](https://help.ubuntu.com/community/Installation#head-194b248381c71c37f7b187c6b814bbe7e31d91d6)

---

### Post by sprightlyone on 2008-05-31
hi 
  thanks to pumalite for his help i am now logged in i went back over ubuntu community documents checked my windows install discovered my system was in fact an AMD 64 system  rebooted to recovery mode edited kernel with suggestion &it loaded to log-in screen  i looged in &now am sending this post from ubuntu 
  all that i need to do now is edit the  grub/boot/menu.lst in a terminal window 
  what is the command ??
which line do i edit in menu list???
thanks lyle:)

---

### Post by Pumalite on 2008-05-31
Backup first:
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst

---

### Post by sprightlyone on 2008-05-31
hi below is my menu.lst words in red are what i added i still have to boot via recovery-mode with these added in it won`t boot normally 
 have i put them in the wrong place ??????
move them if you think they should go somewhere else &i will edit list again 
thanks lyle 

[SIZE="1"]# menu.lst - See: grub, info grub, update-grub
#            grub-install, grub-floppy,
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
# kopt=root=UUID=b222d775-5e17-481b-8fe3-4728f49627d2 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic[SIZE="1"][/SIZE]
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b222d775-5e17-481b-8fe3-4728f49627d2 [COLOR="Red"]irqpoll pci=noacpi nolapic acpi=off[/COLOR]
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b222d775-5e17-481b-8fe3-4728f49627d2 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:[SIZE="1"][/SIZE]
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/SIZE]

---

### Post by Pumalite on 2008-05-31
If it works; stick to it.

---

### Post by sprightlyone on 2008-05-31
hi
  i was a bit premature with my last post late at night 
 when i rebooted this morning it loaded straight up no hiccups 
 thanks to the forum community the help is there if you keep looking &writing &asking  ´where there`s a will there`s away´  
  i have now learned something &that is what counts 
lyle

---

