---
title: "Setting GRUB to boot Windows by default"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by saxsux on 2006-12-18
Hi :-)
I share a computer with my brother and he absolutely HATES Ubuntu. Seriously. I've tried and I've tried to talk to him about it seriously, but he wont listen. 
But, he says he wont mind me installing Ubuntu on there, as long as I keep Windows, and make it boot by default. I can easily partition the disk during installation, and leave a partition for Windows, but how do I make it boot by default?
GRUB always boots Ubuntu as default, with Windows being another option on the list. How would I change it to boot Windows instead?

Thanks :)

---

### Post by JamesWP on 2006-12-18
```
gksu gedit /boot/grub/menu.lst

```

Then scroll to the bottom, and move the windows entry above the ubuntu entry, then simply save and exit. :)

---

### Post by groggyboy on 2006-12-18
another way to set windows to boot first is to edit the grub menu like the previous poster said.  instead of moving the entry for windows before ubuntu, try this: the first entry in GRUB should read```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

```

the last line there, "default  0", is the line you are concerned about.  At bootup, you should have four entries if you haven't edited GRUB (Ubuntu..., Ubuntu...Recovery Mode, Memtest86, & Windows).  Change the number after "default" to the GRUB entry you want automatically selected at startup - the first entry is 0, the second is 1, etc.  Thus, windows would be 3.

Hope that works.

---

### Post by Ecthelion on 2006-12-18
I just wanted to add that the divider

> ### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


Counts as an entry too...
So when you are counting to see which entry windows is you should add 1

---

### Post by groggyboy on 2006-12-18
right!  forgot about that, but it is important!

---

### Post by louieb on 2006-12-18
> **JamesWP said:**
> 
Then scroll to the bottom, and move the windows entry above the Ubuntu entry, then simply save and exit. :)
And you will make you brother real happy when it disappears after the first kernel update.
The XP entry  needs to be above the line that reads ```
### BEGIN AUTOMAGIC KERNELS LIST
```

---

### Post by saxsux on 2006-12-20
That's brilliant.
Thanks everyone :-)

---

### Post by fatty_chris on 2006-12-23
Can somebody post their GRUB list with Windows as the first boot operating system, please.  That may help to clarify things for some of us noobs.  Thanks.

---

### Post by Greevous on 2006-12-23
Fatty_chris, 

Here's *my* menu.lst. However, I just moved my XP entry above the "Automagic Kernels" and haven't tried it. Normally I just copy the XP entry and paste it above the others, and when a new kernel is present I move it again.
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

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
# kopt=root=UUID=3caaefa2-fb52-4873-9ba4-8f8ac95ecd2b ro
# kopt_2_6=root=/dev/hda6 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet
boot

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


```

Edit>> I just rebooted and it worked for me; simply copy/cut and paste above the line "### BEGIN AUTOMAGIC KERNELS LIST" and you should be good to go. ;)

---

### Post by Felix17 on 2007-01-07
Thanks for the instructions guys. However I have a total newb question for you after googling my way to these forums. When I access the menu.lst file and make those changes I get an error mesage when I try to save the file saying that I don't have the necessary access privileges. 

Do I have to log in as an adminstrator or something? The only username I created during the installation process was the one that I was using during that failed file edit attempt so I'm not aware of any other usernames or passwords. I accessed the menu.lst file through the "find files / folders" tool if that makes any difference. I'm afraid my linux knowledge is embarassingly poor but I'm trying to learn.

Help!

Cheers

Felix

---

### Post by bulldog on 2007-01-07
Use a terminal and enter the command```
gksudo gedit /boot/grub/menu.lst
```
Alter it and save it.

---

### Post by Felix17 on 2007-01-08
Thanks Bulldog but that didn't work. Sorry I should've declared I'm using Kubuntu 6.10. After spending a few hours trawling through the online Kubuntu documentation I also tried typing this in as a run command:

> kdesu kedit /boot/grub/menu.lst

After which the OS prompted for a password which I correctly supplied but it came back saying it did not understand the command 'kedit /boot/grub/menu.lst'. I also tried sudo instead of kdesu and kdedit instead of kedit and various combos thereof and still no good.

Now what? I feel I'm close to getting past this hurdle I'm probably just missing one piece of the puzzle.

Thanks in advance

Felix

---

### Post by pmcchapman on 2007-01-08
hey,

just installed kubuntu. i have tried linux (suse and fedora) before, but am still new at this. however, this should work (!), however the terminal does spout out some errors which i do not understand... this is possibly because ubuntu (or maybe it is a debian thing, i'm not sure) seems to handle su/root differently to what i have used before... nonetheless:

open a terminal:

          sudo kate /boot/grub/menu.lst

it will ask you for your password, and then open up the menu file in kate (kde text editor, gedit is a gnome text editor and not installed by default in kubuntu, that is why it did not understand your command). 

you seem to have the standard windows convert options: i.e. ubuntu(0), ubuntu safe(1), mem test(2), divider(3), windows(4). the options are counted from 0, therefore, windows is option 4. 

therefore, edit it as follows; uncomment "default num" command so that it looks for the default, and change the default to 4:

default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		4


save the file and close kate, exit the terminal (type "exit"), then restart.

hope that helps

ps. you can also follow the same method to reduce the time before grub boots windows (thereby annoy your brother less). Uncomment the timeout line, and change time out to (for example) 3 seconds rather than 10...

---

### Post by Felix17 on 2007-01-09
That did the trick totally pmcchapman. Thanks heaps...you're a legend! :KS 

Windows now boots as default with just a 3 second wait. Thanks again also to Bulldog for his post.

Much appreciated

Felix

---

### Post by rafalr on 2007-01-11
Hi Felix,

Yes, you need the admin rights to edit this file.

In Deb based Os you basically do not create a separate admin account but aquire an admin privilidge for a time you need to execute specific command/activities.

You aquire the admin rights by "sudo" command written before the actual command you want to use, then whatever is done untill you exit from the terinal is done by admin.

Example:
sudo gedit /boot/grub/menu.lst

If you want to use admin right with a graphical interface/GUI, you should use gksu (or gksudo) instead of sudo.

That is it.
rafal

---

### Post by dave.goodfellow on 2007-01-14
> **Felix17 said:**
> Thanks for the instructions guys. However I have a total newb question for you after googling my way to these forums. When I access the menu.lst file and make those changes I get an error mesage when I try to save the file saying that I don't have the necessary access privileges. 

Do I have to log in as an adminstrator or something? The only username I created during the installation process was the one that I was using during that failed file edit attempt so I'm not aware of any other usernames or passwords. I accessed the menu.lst file through the "find files / folders" tool if that makes any difference. I'm afraid my linux knowledge is embarassingly poor but I'm trying to learn.

Help!

Cheers

Felix

In a terminal window type

sudo gedit /boot/grub/menu.lst

put in you password and you're good to go

---

### Post by Felix17 on 2007-01-15
Yeah thanks for all your help everyone.

That boot configuration problem is now well sorted. The only other issue I'm having is that whilst my Netgear wireless PCI card (WG311v2) apears to be recognised by Kubuntu 6.10 it doesn't appear to support WPA only WEP or no encryption which sucks. I'm sure as heck not going to downgrade my entire wireless network security to WEP just because Kubuntu can't handle WPA PSK. Perhaps if I got a more Linux friendly wireless card that might solve the problem. But I should probably post this issue in the wireless networking section of the forums.

Cheers

Felix

---

