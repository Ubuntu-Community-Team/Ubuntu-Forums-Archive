---
title: "Edit  Grub to set other OS (Vista)  first?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by oserdavid on 2008-06-09
This is what my Grub menu.list file looks like:

[SIZE="1"]title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9737ff12-0a2b-418e-8651-6661bda623bd ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-18-generic
quiet
title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=9737ff12-0a2b-418e-8651-6661bda623bd ro single
initrd		/boot/initrd.img-2.6.24-18-generic
title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1[/SIZE]

How do I edit it to put Windows Vista/Longhorn ahead of Ubuntu, so that unless I intervene to select Ubuntu, it is Windows which loads first? I've looked at the documentation, but I'm confused, and, naturally, very worried about making an error.

Also, I would guess that after editing it as user, it won't save - so I guess it needs to be edited as root, and I'm not sure how to do that.

Detailed hand-holding help would be much appreciated!
David

---

### Post by sisco311 on 2008-06-09
> 
[B][SIZE=1]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1[/SIZE][/B]

[SIZE=1]title        Ubuntu 8.04, kernel 2.6.24-18-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=9737ff12-0a2b-418e-8651-6661bda623bd ro quiet splash xforcevesa
initrd        /boot/initrd.img-2.6.24-18-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.24-18-generic root=UUID=9737ff12-0a2b-418e-8651-6661bda623bd ro single
initrd        /boot/initrd.img-2.6.24-18-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,4)
kernel        /boot/memtest86+.bin
quiet
[/SIZE][SIZE=1]

or set the 
```
default    0
```option to 
```
default    4
```To edit the file open a terminal:
```
gksu gedit /boot/grub/menu.lst
```Before you edit the file create a backup:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```[/SIZE]

---

### Post by oserdavid on 2008-06-09
Blimey (London/Cockney-English slang expression of surprise) sisco311, that was fast! Many thanks for that. 

I'll just wait a day or so, in case someone picks up that you may have made a minor speed-induced syntax error (no offense intended! but in my ignorance, it pays to be double-cautious) and then apply your solution and let you know it was successful.
Best
David

---

### Post by Joeb454 on 2008-06-09
Changing the "default 0" to "default 4" should work just fine, it will change the default selected system to your Vista entry :)

---

### Post by oserdavid on 2008-06-09
Thanks Joeb454 - but it occurs to me that as Ubuntu is updated with new kernels, these are added to the list from the top, and unless you remember to manually delete the old ones, this will play havoc with the default 0, default 4, etc type solution. 

And I suspect it may also cause problems with sisco311's original solution.

Am I right, and is here a simple way of overcoming this issue?
David

---

### Post by dstew on 2008-06-09
> but it occurs to me that as Ubuntu is updated with new kernels, these are added to the list from the topYes, that usually changes the default. To prevent updates from changing the default OS, edit the line in menu.lst that says```
# updatedefaultentry=false
```to```
# updatedefaultentry=true
```That way, when new items are added to the menu, the update-grub program will change the default entry number so that the Windows menu item will always be the default.

---

### Post by oserdavid on 2008-06-09
Brilliant dstew. Thank you. When I get a moment, over the next few days, I shall take my life into my hands and get down to editing my grub menu.lst file.

Many many thanks to you all for your help.
David

---

### Post by Vivaldi Gloria on 2008-06-09
It should be

```
updatedefaultentry=true
```

rather than

```
# updatedefaultentry=true
```

Grub does not look at lines which start with a "#" sign.


Edit: What I wrote is wrong. Read dstew's comments below.

---

### Post by dstew on 2008-06-09
Vivaldi, you are right that **grub** does not look at lines that start with a #, but **update-grub** does. The top of the grub menu.lst has the parameters that update-grub uses. They are *supposed* to be ignored by grub, so these parameters start with a single #. The comments in this section begin with ##. Again, you are supposed to leave the single # in front of each of the update-grub parameters, so that they will be ignored by grub. See the [man page for update-grub]("http://pwet.fr/man/linux/administration_systeme/update_grub").

---

### Post by Vivaldi Gloria on 2008-06-09
> **dstew said:**
> Vivaldi, you are right that **grub** does not look at lines that start with a #, but **update-grub** does. The top of the grub menu.lst has the parameters that update-grub uses. They are *supposed* to be ignored by grub, so these parameters start with a single #. The comments in this section begin with ##. Again, you are supposed to leave the single # in front of each of the update-grub parameters, so that they will be ignored by grub. See the [man page for update-grub]("http://pwet.fr/man/linux/administration_systeme/update_grub").

Hmm. I didn't know that. Thanks for letting me know.

---

### Post by oserdavid on 2008-06-09
Learning more and more... Thanks guys.
D

---

### Post by oserdavid on 2008-06-10
Sorry - need help again: I've succeeded in backing up my menu.list file but to edit the original how do I get to it in terminal? After entering my password, typing gksu mousepad /boot/grub/menu.lst just leaves me with the standard prompt - what am I supposed to put into it to bring up the file I want to edit? Doing cd /boot then cd /grub won't get me any further, it seems - because it then tells me there is no such directory as /grub

Of course - getting to it via 'places' and editing it left me with 'you do not have the necessary permissions' to save it, again.

Really, the easiest thing for me would be to become 'superuser' and then simply click on 'places' and go from there. But I don't know enough to be able to do that, either. Grrr... Linux is a pretty steep learning curve after Windows!

---

### Post by sisco311 on 2008-06-10
> **oserdavid said:**
> Sorry - need help again: I've succeeded in backing up my menu.list file but to edit the original how do I get to it in terminal? After entering my password, typing gksu mousepad /boot/grub/menu.lst just leaves me with the standard prompt - what am I supposed to put into it to bring up the file I want to edit? Doing cd /boot then cd /grub won't get me any further, it seems - because it then tells me there is no such directory as /grub

Of course - getting to it via 'places' and editing it left me with 'you do not have the necessary permissions' to save it, again.

Really, the easiest thing for me would be to become 'superuser' and then simply click on 'places' and go from there. But I don't know enough to be able to do that, either. Grrr... Linux is a pretty steep learning curve after Windows!

Sorry, the default text editor in gnome is gedit:
```
gksu gedit /boot/grub/menu.lst
```I'm using xubuntu. Sorry again.

EDIT:
You can run the file browser(nautilus) as super user:
```
gksu nautilus
```
but is very dangerous. As super user you are allowed to do anything with the system files. 
One bad click and you need a reinstall. So be real careful.

---

### Post by oserdavid on 2008-06-10
Success!! Many, many thanks to all of you. I did it via gedit rather than tinker with nautilus, as you advised sisco311.

One final question to dstew, before I make that recommended change... Is that foolproof, or is it possible that some update or another could leave me booting into memtest or something, if I'm not careful?

Apologies for being such a nag...
David

Edit - FYI the change I made was to change default 0 to default 4

---

### Post by dstew on 2008-06-10
I would say its foolproof. It is always possible to mess something up when you edit a file, but if you make a backup first you have no worries. Even if you completely destroyed menu.lst and the backup you could always make a new one, using the grub-install program I think.

By the way, the best way to edit a file with administrative privleges in my opinion is to press alt-F2 (gets you a quick command line without opening Terminal) and using```
gksudo gedit /boot/grub/menu.lst
```That little box will also save that command in a  drop-down list.

---

### Post by oserdavid on 2008-06-10
Thanks dstew - I'll use that for editing "# updatedefaultentry"

Now my wife can switch on my computer to use Skypeout with our Cordless Dualphone (no software for Linux, and Wine won't cut it either) and not be faced with the Ubuntu login...

---

### Post by th3gh05t on 2008-06-10
Hi,

I am also trying to get XP to boot up first. Here is what my menu.lst looks like:

```

title Ubuntu hardy (development branch), kernel 2.6.24-12-rt
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-12-rt root=UUID=50f899d8-39d0-4271-a014-54386e05368b ro quiet splash
initrd /boot/initrd.img-2.6.24-12-rt
quiet

title Ubuntu hardy (development branch), kernel 2.6.24-12-rt (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-12-rt root=UUID=50f899d8-39d0-4271-a014-54386e05368b ro single
initrd /boot/initrd.img-2.6.24-12-rt

title Ubuntu hardy (development branch), memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

```

Can I still change the "default 0" to "default 4" and it will work?

---

### Post by dstew on 2008-06-10
I think in your case it would be **default 3**, since grub starts counting from 0, and you only have 4 menu items total.

---

### Post by oserdavid on 2008-06-22
@sisco311, @dstew
Just thought I'd let you know that the simplified solution, proposed as second by sisco311 and endorsed by dstew worked fine through the linux-image updates and also survived my removal of the penultimate (18) kernel version, after kernel version 19 was installed and found acceptable. Thanks once again.
David

Edit: Cool smiley unintended - meant to read 'eight-close-bracket' - but serendipitous I suppose! (How do you stop a smiley inserting when you mean 8-close-bracket?!!)

---

### Post by bertles86 on 2008-07-23
Sorry chaps I'm trying to do this too, where is the 'default 0' to edit in the menu.lst file..I can't find it!? Is it right near the top about line 14 (in mine!)?

```
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
# kopt=root=UUID=996930ee-eaf8-410f-88ef-15d5fe0ca61f ro

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
# defoptions=quiet splash all_generic_ide

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=996930ee-eaf8-410f-88ef-15d5fe0ca61f ro quiet splash all_generic_ide
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=996930ee-eaf8-410f-88ef-15d5fe0ca61f ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
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

```

I've opened menu.lst and backed it up so far, just want XP as first choice then *nix after. Thanks!

---

### Post by bertles86 on 2008-07-25
Any help would be grand guys, cheers.

---

### Post by bertles86 on 2008-07-30
bump

---

### Post by sisco311 on 2008-07-30
try:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from
0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default
entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
[B]default         4
[/B]
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the
default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
...


---

