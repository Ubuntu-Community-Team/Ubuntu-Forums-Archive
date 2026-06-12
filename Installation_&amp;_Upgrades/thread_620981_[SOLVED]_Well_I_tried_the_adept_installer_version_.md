---
title: "[SOLVED] Well I tried the adept installer version for upgrading to gutsy"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by andybleaden on 2007-11-23
Which did not work 100%

So...rather than give up I tried from Shell ( running kubuntu in feisty at the mo)

Which after a while kinda worked finished what adept did not...but I cannot reboot in the last version so I press esc when rebooting and choose an earlier version of 7.1...( sorry do not know how to list that here ( any ideas?)

Runs perfecto now...although I cannot do a straight reboot using the working gutsy ...can I select that it uses this everytime?

Let me know if you would like any system info ( plus the commnads to get them!) if that will help.

First impression is that it looks nice but I cannot be sure until I can get it rebooting everytime ( so my family can use it)

......also I notice I cannot seem to be able to right click and select move or copy for an item with the new gui for system menu...ie dolphin has replaced konqueror

---

### Post by PmDematagoda on 2007-11-23
Could you post the results of:-
```

cat /boot/grub/menu.lst
```

---

### Post by andybleaden on 2007-11-23
thanks for speedy response

that produced this ...



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
timeout         3

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
# kopt=root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.22-14-386

title           Ubuntu 7.10, kernel 2.6.20-16-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.20-16-386

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.20-15-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu 7.10, kernel 2.6.20-15-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.20-15-386

title           Ubuntu 7.10, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, kernel 2.6.17-12-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-386

title           Ubuntu 7.10, kernel 2.6.17-12-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.17-12-386

title           Ubuntu 7.10, kernel 2.6.17-10-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386

title           Ubuntu 7.10, kernel 2.6.17-10-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.17-10-386

title           Ubuntu 7.10, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386

title           Ubuntu 7.10, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.15-28-386

title           Ubuntu 7.10, kernel 2.6.15-27-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386

title           Ubuntu 7.10, kernel 2.6.15-27-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.15-27-386

title           Ubuntu 7.10, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386

title           Ubuntu 7.10, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd          /boot/initrd.img-2.6.15-23-386

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
andy@andy-desktop:~$

---

### Post by PmDematagoda on 2007-11-23
Why on earth do you have so many kernels?

Anyway, before I can tell you the next step, I need the Ubuntu installation that you want to be selected by default to be underlined. After that the next step is solving the problem.

---

### Post by andybleaden on 2007-11-23
that I cannot understand. The one that worked I think is I guess the second one?  ie 

title Ubuntu 7.10, kernel 2.6.20-16-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd /boot/initrd.img-2.6.20-16-386

As to why I have so many ...I am clueless...can I get rid of them?

Is there a way to check which one is running now.

BTW I only installed this today and was on feisty yesterday 

I have run update/upgrade etc and there are no more to do 

Thanks a million for your help

---

### Post by andybleaden on 2007-11-23
Sorry should have let you know I am on msn iM  as [email]andybleaden@hotmail.co.uk[/email] and icq 277487048 if you have any harder questions!

---

### Post by PmDematagoda on 2007-11-23
You can check the version of the kernel you are running using 
```

uname -a
```

Now for your menu.lst file. Open it up for editing using:-

```
sudo gedit /boot/grub/menu.lst
```

Then change the default entry found here:-

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default 0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).

```
to:-

```
default 3
```

If you want to clean the boot-loader list a little, simply delete the entries that you don't want, such as:-
```

title Ubuntu 7.10, kernel 2.6.22-14-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-386
```

But do not delete all the entries, just keep one or two (along with their Recovery Mode entries) so that they could act as backups in case one of your kernels fail.

Once all the changes are done, save the file and see if that solves your problem.

---

### Post by andybleaden on 2007-11-23
Many many thanks

Will give that a quick try now and get back with results

Andy

---

### Post by andybleaden on 2007-11-23
Tried the uname -a

Got this response

Linux andy-desktop 2.6.20-16-386 #2 Sun Sep 23 19:47:10 UTC 2007 i686 GNU/Linux

Tried the sudo gedit /boot/grub/menu.lst

Got this command not found

Do I do kedit instead or gkedit?

---

### Post by andybleaden on 2007-11-23
Sorry I forgot to say I am using kubuntu maybe :confused:

---

### Post by PmDematagoda on 2007-11-23
Oops, my bad, use:-

```
sudo kate /boot/grub/menu.lst
```

Sorry for the mix-up.

---

### Post by andybleaden on 2007-11-23
Right. Thanks 

I have edited and deleted a few versions

Will restart now...see you again in a mo if it works!

Or in an hour if not!:)

---

### Post by PmDematagoda on 2007-11-23
Before you reboot, could you please re-post the menu.lst file again.

---

### Post by andybleaden on 2007-11-23
sorry too late...got the wrong number as I restarted in recovery mode!

Got it working on 2 not 3 fine and dandy 

So now uname a give

Linux andy-desktop 2.6.20-16-386 #2 Sun Sep 23 19:47:10 UTC 2007 i686 GNU/Linux

Here is the now edited kate menu list thing

I might still get rid of a few more kernels

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
default		2

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
# kopt=root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu 7.10, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=cc4f4dfe-5f77-4f45-ae5c-e0ed43958b66 ro single
initrd		/boot/initrd.img-2.6.20-15-386







### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by andybleaden on 2007-11-23
Seems to be working though so thanks very much for your help PmDematagoda matey!

---

### Post by PmDematagoda on 2007-11-23
Glad to see that the problem was solved, and sorry for my error with the default value, I remembered that the value did not apply once the order of the different kernels was changed only after I gave my last post, but it seems that you solved it yourself, good job on your part:).

---

### Post by PmDematagoda on 2007-11-23
> **andybleaden said:**
> Seems to be working though so thanks very much for your help PmDematagoda matey!

Glad I was able to help you:), could you mark the thread as Solved so that it could help other Ubuntu users with your same problem.

---

### Post by andybleaden on 2007-11-23
I make a very risky hacker!

Just thought I would have a go!

BTW can I stop having to log in everytime on my pc now?

---

### Post by PmDematagoda on 2007-11-23
You should be able to use the Automatic Login option, but I do not know how to do that on KDE.

---

### Post by andybleaden on 2007-11-23
Well I found my own answer online which means for others in the same trouble you need to follow this on the kubuntu desktop guide

[http://linux.about.com/od/kubuntu_doc/a/kubudg35t03.htm](http://linux.about.com/od/kubuntu_doc/a/kubudg35t03.htm)

It is possible to login a user automatically when the computer boots. This is not recommended for most computers, as it is not secure and may allow other users access to your information.

    *

      K-Menu->System Setting->Login Manager
    *

      Click on the Administrator Mode... and enter your user password to gain administrator privileges.
    *

      Select the Convenience tab. Check the Enable Autologin and select the user to autologin from the drop down menu and select an appropriate time delay.

---

