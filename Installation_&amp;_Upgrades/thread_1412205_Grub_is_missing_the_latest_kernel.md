---
title: "Grub is missing the latest kernel"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by bart1452 on 2010-02-20
I'm running Hardy 8.04 LTS 64bit. The Update Manager updated the kernel and then asked if I wanted to use the local version of the grub menu. The boot menu was getting so long I edited it to shorten it. Other options were also offered, like the builder's version, but I chose the local version and since then the new kernel doesn't show up in the boot menu. Sudo update-grub doesn't restore it to the menu.

How do I undo the local version of the boot menu so I can see the newest kernel?

---

### Post by RedSingularity on 2010-02-20
You know how to edit the boot menu?

---

### Post by RedSingularity on 2010-02-20
Its in /boot/grub/menu.lst

Look there and see if your kernel is there.

---

### Post by bart1452 on 2010-02-21
Yes, I know how to edit the menu.lst.  I think that's the reason for the problem. I edited the list to delete the older versions of the kernel to shorten the list. When the kernel was updated the Grub Updater asked me if I wanted to stay with the local version of menu.lst that I created, the builder's version, or one of the other possible versions. I chose the local version that I created. When the Grub menu appeared on reboot, only the kernel version that I left in the menu.lst appeared. The new one was not added.

---

### Post by darkod on 2010-02-21
If you have your own menu.lst then you know how to work with it. Just add the new kernel manually and after next install go with builders version of grub if you want to.

---

### Post by bart1452 on 2010-02-21
What I'd rather do is let the updater detect the new version of the kernel and put it in the menu.lst. I've run update-grub and it doesn't detect the new kernel. Maybe the kernel didn't take? But when I look at the Synaptic Manager it shows the newer kernel having been installed (2.6.24.27.45-65). All I'm seeing is kernel

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=9dae32cf-0428-4081-afc6-68fc235c8d44 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

I should see 2.6.24-27 generic. With the kernel line having some root=(long series of UUID numbers) in there, I don't know what it is for the new kernel and couldn't properly edit the file to put the new kernel in the list.

---

### Post by kansasnoob on 2010-02-21
Post the full output of:

```
cat /boot/grub/menu.lst
```

---

### Post by bart1452 on 2010-02-21
I did it with gedit, and then again in cat. The results were the same so I am leaving the cat results in the next post.

---

### Post by bart1452 on 2010-02-21
I tried to post it from gedit. Here's the cat results:

dave@ubuntuSR1550nx:~$ cat /boot/grub/menu.lst
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
default         0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=9dae32cf-0428-4081-afc6-68fc235c8d44 ro

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
# defoptions=quiet splash vga=773

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
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=9dae32cf-0428-4081-afc6-68fc235c8d44 ro quiet splash vga=773
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=9dae32cf-0428-4081-afc6-68fc235c8d44 ro single
initrd		/boot/initrd.img-2.6.24-26-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf1
title		Windows NT/2000/XP (System Restore - erase everything and start over mode)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by darkod on 2010-02-21
> **bart1452 said:**
> What I'd rather do is let the updater detect the new version of the kernel and put it in the menu.lst.

Well you broke that link when you created your custom file and now told it to use the local version instead of the package maintainers version.
So this once add the new kernel manually, all you need is copy the same entry as the current ones and just change the kernel filename.

And after the next update, select different option when asked.

---

### Post by bart1452 on 2010-02-21
> So this once add the new kernel manually, all you need is copy the same entry as the current ones and just change the kernel filename.

And after the next update, select different option when asked.

I learned about the option.

So the UUID line will not change with the kernel?

---

### Post by bart1452 on 2010-02-21
Thank you for the help, Darkod. I get a little nervous about adding anything to the file. I had also looked into the idea of reinstalling Grub to see if it would refresh everything.

---

### Post by darkod on 2010-02-21
> **bart1452 said:**
> I learned about the option.

So the UUID line will not change with the kernel?

No, it won't. The UUID is for the partition and they are both on the same. It's literary just the filename. You can also see the exact filename in /boot and use that.

---

### Post by oldfred on 2010-02-21
If you want the default to only show 2 kernels, you can edit this in your menu.lst:

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options 
## e.g. howmany=all
##      howmany=7
# howmany=all

change last line [COLOR=Red]all [/COLOR]to [COLOR=Red]2[/COLOR]:
# howmany=[COLOR=Red]2[/COLOR]

---

### Post by kansasnoob on 2010-02-22
Sorry to take so long :(

I don't actually see anything wrong with your menu.lst so exactly why the automagic feature isn't working I'm not sure.

One thing you could do is backup the old menu.lst and let "update-grub" create a new one just to see what happens. You would of course have to add your Windows entries back to the very bottom of the menu.lst.

It would go like this:

```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst_old
```

Then just:

```
sudo update-grub
```

That should ask if you want a menu.lst generated so just say yes (y) and then check the new menu.lst with:

```
cat /boot/grub/menu.lst
```

And see if it found all of your kernels. If so you'll need to add your Windows entries back below this line:

### END DEBIAN AUTOMAGIC KERNELS LIST

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf1
title       Windows NT/2000/XP (System Restore - erase everything and start over mode)
root        (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdf2
title       Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader +1
```

Of course you'll need to use gedit like this:

```
gksudo gedit /boot/grub/menu.lst
```

And be sure to click on Save, then File > Quit.

Actually while you're there you could do what oldfred suggested for limiting the number of kernels or you could install Startup Manager:

```
sudo apt-get install startupmanager
```

It'll then show up in System > Administration and under the Advanced tab you can select how many kernels to show in the menu, and whether or not to display the Memtest option or Recovery Mode options.

**Now, [COLOR="Red"]only if creating a new menu.lst didn't work[/COLOR]**, you can put things back as they were by:

```
sudo rm /boot/grub/menu.lst
```

```
sudo mv /boot/grub/menu.lst_old /boot/grub/menu.lst
```

```
sudo update-grub
```

Clear as mud?

---

