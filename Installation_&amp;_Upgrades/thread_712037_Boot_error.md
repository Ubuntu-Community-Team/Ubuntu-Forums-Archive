---
title: "Boot error"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by baggya99 on 2008-03-01
I successfully installed ubuntu using wubi and rebooted my computer.
The final installation and loading of ubuntu worked when I selected to run the ubuntu OS instead of Windows XP. However after loading the screen went blank and remained unchanged after a half hour. I rebooted the computer and attempted to run ubuntu again: the ubuntu logo appeared with loading bar, however after it loaded the same blank black screen appeared and again after being left for a period, nothing would load. In order to try and resolve this I forced the computer to shutdown and left it for approx 9hrs before attempting to boot again. However, this time the screen would only load showing the message:-
"We apologize for the inconvenience, but Windows did not start successfully. A recent hardware or software change might have caused this.

If your computer stopped responding, restarted unexpectedly, or was automatically shut down to protect files and folders, choose Last Known Good Configuration to revert to the most recent settings that worked.

If a previous startup attempt was interrupted due to a power failure or because the Power or Reset button was pressed, or if ou aren't sure what caused the problem, choose Start Windows Normally.

 <options as follows>

         Safe Mode
         Safe Mode with Networking
         Safe Mode with Command Prompt

         Last Known Good Configuration (your most recent settings that worked)

         Start Windows Normally

Use the up and down arrow keys to move the highlight to your choice"

The problem being that no matter which option I select, the system attempts to boot, a blue screen with writing appears then disappears before I have chance to read it, and the system reboots againloading the same message.


Any and all advice on how to fix this would be welcome as I am at a loss as to A) What is going on; and B) what on earth to do about it


Many thanks

Mikey W O:)

---

### Post by prshah on 2008-03-06
Press F8 while Windows is starting up (BEFORE windows splash screen). In the following menu screen, choose the option "disable automatic restart on error". That will let you see the error (eg blue screen will stay put and not disappear).

Report the exact error here.

Or you can try booting into Safe Mode and running system restore, choosing a date before the installation of wubi.

Cheers,
PRShah

---

### Post by woodbrick on 2008-06-15
.........Or you can try booting into Safe Mode and running system restore, choosing a date before the installation of wubi.....

Hi. I have the same error when trying to boot into windows. I had a perfectly working dual boot system, and all I can think that has done it is I installed a couple of packages: wine and gammu. 

My menu.lst looks "normal":

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=6cfb60b3-f4ec-47c2-b357-b3efabd04334 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=6cfb60b3-f4ec-47c2-b357-b3efabd04334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=6cfb60b3-f4ec-47c2-b357-b3efabd04334 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6cfb60b3-f4ec-47c2-b357-b3efabd04334 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=6cfb60b3-f4ec-47c2-b357-b3efabd04334 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

this is the second time I have managed to destroy my windows OS with ubuntu. Can anyone help me avaoid another clean install??? Appreciate any help... Cheers

---

### Post by woodbrick on 2008-06-15
I think I have discovered the problem. I didn't just install wine, I thought that the idea was to 'point' wine's C drive to my windows folders. I think a clean install may be in order, as according tho this post: 

[http://www.linuxforums.org/forum/wine/119917-can-wine-create-problems-windows.html](http://www.linuxforums.org/forum/wine/119917-can-wine-create-problems-windows.html)

the windows registery will have been corrupted..

---

