---
title: "clean up menu.lst?"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by useResa on 2006-12-14
I have Ubuntu Edgy running on a Dell Latitude D620.
I have a question about the kernels that are installed on my system.

From what I understand I can best use the generic kernel.
However, my menu list shows various different versions for the kernels that I can start up. Please find below a dump of my menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro

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
# defoptions=quiet splash vga=791

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
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.17-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.17-10-386
boot

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, kernel 2.6.15-27-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-686 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-27-686
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-686 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-686 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.15-27-686
boot

title        Ubuntu, kernel 2.6.15-27-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-27-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-27-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.15-27-386
boot

title        Ubuntu, kernel 2.6.15-26-686
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-686 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-26-686
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-686 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.15-26-686
boot

title        Ubuntu, kernel 2.6.15-26-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-26-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-26-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.15-26-386
boot

title        Ubuntu, kernel 2.6.15-23-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.15-23-386
savedefault
boot

title        Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.15-23-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.15-23-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
My question: Can I safely delete the entries that I believe are obsolete?
And immediately my next question: Should I only have the generic kernel installed and if so, how can I delete the others? Should I use Synaptics or the apt-get remove statement?

Looking forward to your reactions.

---

### Post by bulldog on 2006-12-14
I leave at least two different kernels who are working good for safety,the rest you can delete with synaptic. {with the recovery mode,that make four and your memtest of course]

Make a note from the kernels you want to remove and search for them in synaptic.
If done you can do ```
sudo update-grub
``` to refresh GRUB.

If this update doesn't remove the entry's you can do it manually.

---

### Post by useResa on 2006-12-14
> **bulldog said:**
> I leave at least two different kernels who are working good for safety,the rest you can delete with synaptic. {with the recovery mode,that make four and your memtest of course]

Make a note from the kernels you want to remove and search for them in synaptic.
If done you can do ```
sudo update-grub
``` to refresh GRUB.

If this update doesn't remove the entry's you can do it manually.
Thank you Bulldog, this did the trick!

I have a nice clean menu.lst now again > # menu.lst - See: grub(8), info grub, update-grub(8)
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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

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
# kopt=root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro

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
# defoptions=quiet splash vga=791

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

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-generic root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, kernel 2.6.17-10-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro quiet splash vga=791
initrd        /boot/initrd.img-2.6.17-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.17-10-386 root=UUID=a8f27068-5c25-4aa9-a611-8144e7dd227d ro single
initrd        /boot/initrd.img-2.6.17-10-386
boot

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
 Additionally I have put the generic kernel as first (only needed to recompile my nvidia driver again, but have done that so many times that it was a piece of cake :D)

---

### Post by bulldog on 2006-12-14
GRUb is a nice and configurable application,glad your menu.lst is clean again,I'm not sure about recompiling your nVidia driver,it should make no difference,but if it's nothing to you,why bother :D

---

### Post by useResa on 2006-12-14
> **bulldog said:**
> GRUb is a nice and configurable application,glad your menu.lst is clean again,I'm not sure about recompiling your nVidia driver,it should make no difference,but if it's nothing to you,why bother :D
If I restart with a different kernel (so in case of my new situation) if I switch from generic to 386 or vice versa, I get an error when starting X.
If I recompile the NVidia driver, it is solved.
But this could very well be caused by the fact that I use the latest [beta driver]("http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9742.html") ;)

---

### Post by bulldog on 2006-12-14
No,now I understand,you use a different kernel.
I was thinking you used the same kernel,now it makes sense.:D

---

