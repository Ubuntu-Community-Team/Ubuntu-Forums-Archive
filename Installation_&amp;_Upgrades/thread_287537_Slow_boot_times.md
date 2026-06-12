---
title: "Slow boot times"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by ryan on 2006-10-28
I was able to do the upgrade from Dapper fine and everything works fine but it really takes a long time for it to boot up in fact slower than with Dapper There is no verbose mode by default I think so I can't see what is going on. Shutdown is slow to. I am wondering if there is a misconfigured conf file some place. Anyone have any ideas ? tks

---

### Post by mad0master on 2006-10-29
Hola, I've got the same problem! :???: 

[http://ubuntuforums.org/showthread.php?t=285920](http://ubuntuforums.org/showthread.php?t=285920)

Show us your bootchart. The first tip is to configure network by /dev/hands :rolleyes:  Well - 15 secs ;)

---

### Post by khedron on 2006-10-29
I'm suffering from a slow boot time as well. Grub takes ages to load, so I think it might be a filesystem problem.

---

### Post by Tempurite on 2006-10-29
Same here...](*,)

---

### Post by ryan on 2006-11-01
Tks for the information I installed bootchart (see attachements) #1 was a normal boot seems like usplash is causing some delays 1:10 secs. I can't remember where I read this but someone said that if you hit Cltr-Alt-F1 on the boot things go faster. #2 40 seconds. I am not sure what that means. Also I have attached my boot log seems like there are some things not loading right. Again I am not sure what these things mean. The following seemed to stand out.

Oct 31 18:57:31 localhost kernel: No module symbols loaded - kernel modules not enabled. 

Oct 31 18:57:32 localhost kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"

Oct 31 18:57:32 localhost kernel: [17179572.892000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Oct 31 18:57:32 localhost kernel: [17179572.892000] Please report the result to linux-kernel to fix this permanently
Oct 31 18:57:32 localhost kernel: [17179572.892000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Oct 31 18:57:32 localhost kernel: [17179572.892000] Please report the result to linux-kernel to fix this permanently


I assume that "Please report the result to linux-kernel to fix this permanently" mean to report this to the linux-kernel dev team. Anyone know if this is what this means and if so how to do that ? 

Here is copy of menu.lst

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro

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
# defoptions=quiet splash elevator=cfq

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

title        Ubuntu, kernel 2.6.17-10-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.17-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.17-10-386
boot

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, kernel 2.6.15-22-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-22-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-22-386
boot

title        Ubuntu, kernel 2.6.15-21-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-21-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-21-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-21-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-21-386
boot

title        Ubuntu, kernel 2.6.15-20-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-20-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-20-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-20-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-20-386
boot

title        Ubuntu, kernel 2.6.15-19-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-19-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-19-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-19-386
boot

title        Ubuntu, kernel 2.6.15-18-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-18-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-18-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-18-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-18-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-18-386
boot

title        Ubuntu, kernel 2.6.12-10-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.12-10-386
boot

title        Ubuntu, kernel 2.6.12-9-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by ryan on 2006-11-16
> **ryan said:**
> Tks for the information I installed bootchart (see attachements) #1 was a normal boot seems like usplash is causing some delays 1:10 secs. I can't remember where I read this but someone said that if you hit Cltr-Alt-F1 on the boot things go faster. #2 40 seconds. I am not sure what that means. Also I have attached my boot log seems like there are some things not loading right. Again I am not sure what these things mean. The following seemed to stand out.

Oct 31 18:57:31 localhost kernel: No module symbols loaded - kernel modules not enabled. 

Oct 31 18:57:32 localhost kernel: [17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"

Oct 31 18:57:32 localhost kernel: [17179572.892000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Oct 31 18:57:32 localhost kernel: [17179572.892000] Please report the result to linux-kernel to fix this permanently
Oct 31 18:57:32 localhost kernel: [17179572.892000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
Oct 31 18:57:32 localhost kernel: [17179572.892000] Please report the result to linux-kernel to fix this permanently


I assume that "Please report the result to linux-kernel to fix this permanently" mean to report this to the linux-kernel dev team. Anyone know if this is what this means and if so how to do that ? 

Here is copy of menu.lst

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro

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
# defoptions=quiet splash elevator=cfq

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

title        Ubuntu, kernel 2.6.17-10-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.17-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.17-10-386
boot

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, kernel 2.6.15-25-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-25-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-25-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-25-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, kernel 2.6.15-22-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-22-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-22-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-22-386
boot

title        Ubuntu, kernel 2.6.15-21-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-21-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-21-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-21-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-21-386
boot

title        Ubuntu, kernel 2.6.15-20-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-20-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-20-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-20-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-20-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-20-386
boot

title        Ubuntu, kernel 2.6.15-19-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-19-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-19-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-19-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-19-386
boot

title        Ubuntu, kernel 2.6.15-18-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-18-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.15-18-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-18-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.15-18-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.15-18-386
boot

title        Ubuntu, kernel 2.6.12-10-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.12-10-386
boot

title        Ubuntu, kernel 2.6.12-9-386
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro quiet splash elevator=cfq
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=UUID=11ec7aa5-27f7-47c8-a66d-4df3c38441ea ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


I found out that I was booting the wrong kernel when I started to boot the generic one everything worked fine and things speed up a great deal.

---

### Post by linuxfreak003 on 2008-02-05
if you are looking for an answer here and didn't happen to be booting the wrong kernel this might help. [http://ubuntuforums.org/showthread.php?p=4274379#post4274379](http://ubuntuforums.org/showthread.php?p=4274379#post4274379)

---

