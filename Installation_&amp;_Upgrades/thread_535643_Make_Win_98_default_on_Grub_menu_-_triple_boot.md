---
title: "Make Win 98 default on Grub menu - triple boot"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by trishacupra on 2007-08-26
This sounds like a weird request, but it's for my parents.

My Dad wants to try out Ubuntu, because I've been going on and on about it. And after a quick look at the Live CD, he wanted to install it.

Dad's really interested in computer stuff, like me. On the other hand, Mum is stuck waaaaaay in the past, with Win 98 (I know, I know...).

The original set up of the computer is a dual boot with Win 98 and Win XP, and Win 98 is the default choice in the boot menu. So, Mum likes to turn on the computer, walk away, and when she gets back, Win 98 is booted up.

Dad uses Win XP and is trying to get Mum to use that.

Win 98 is on one tiny slave hard drive (Mum's), and Win XP is on Dad's big hard drive.

Dad and I installed Ubuntu on a partition on Dad's hard drive the other night. Grub found all three OS's but now there's a bit of a hitch when it comes to Mum...

Mum is very set in her ways, and will make a big fuss when she finds out that Ubuntu is going to load by default.

The other issue is that for some reason, Grub makes booting Win 98 a two-step process. First you have to select 'Windows' from under the 'Other Operating Systems' heading in the menu. Then it goes to a second menu where you have to select between Win 98 and XP.

This is going to be all too much for Mum to handle, and I don't want her hating Linux from the start because it messed up how she's used to doing things.

Mum takes ages to learn techie stuff, and there's no changing her, so we're stuck with that.

Dad would love to ditch Win 98 altogether and force Mum to use XP, but that's a bit scary for all of us. ;)

So, is there a tutorial out there on how to make Win 98 the default, so it times out on that option and 98 boots automatically if Mum walks off while the computer is turned on?

Can the Super Grub disk do this? I left my copy at home - in another state, and I'm staying with my parents at the moment.

Thanks in advance for any advice...

Trisha

---

### Post by Pumalite on 2007-08-26
You can edit menu list and put win98 first

---

### Post by trishacupra on 2007-08-26
Is it as simple as cutting the Win 98 section and pasting it on top of the Ubuntu entry?

The reason I ask is because Grub has Win 98 on the second menu - you have to select Windows and then Windows 98 on the next screen. I thought that might complicate the process more.

---

### Post by Pumalite on 2007-08-26
Right. Make sure you backup menu.lst first.

---

### Post by trishacupra on 2007-08-26
Ok. I'll give it a go. I think I've stuffed up menu.lst before on my own computer, but restored the backed-up version using the Live CD, so I guess it can't hurt.

---

### Post by trishacupra on 2007-08-26
Doesn't seem to be that easy. The only entry for Windows in the menu.lst is the one that is for both 98 and XP - it's for both, and I'm worried about pasting it first. Here it is:


> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1



---

### Post by weatherman1293 on 2007-08-26
> **Pumalite said:**
> Right. Make sure you backup menu.lst first.

Mum will just love ya if you can't put that back together.

Tell her she IS compromising the computers security by running Win98, and ubuntu would actually be the best thing there.

---

### Post by logos34 on 2007-08-26
An easier way would be to simply change one number on menu.lst--the 'default' line

If it reads 

**default   0**  (-->this boots the first ubuntu kernel)

then change it to '4', or however many '**title**' lines down the windows entry is (start counting at 0 -- i.e. '**0**,1,2,3,4...') 

Another thing: if you paste the windows entry make sure it is above/outside the 'automagic' section, otherwise it will be deleted the next kernel update.

---

### Post by Pumalite on 2007-08-26
Well, if it doesn't work, you can always go back; that's why you have your backup.

---

### Post by trishacupra on 2007-08-26
She doesn't care. She just wants it the way it was. There's no telling some people. All she uses it for is MS Publisher, and that can't run on Ubuntu - unless you use WINE or Crossover, I guess.

---

### Post by trishacupra on 2007-08-26
> **logos34 said:**
> An easier way would be to simply change one number on menu.lst--the 'default' line

If it reads 

**default   0**  (-->this boots the first ubuntu kernel)

then change it to '4', or however many '**title**' lines down the windows entry is (start counting at 0 -- i.e. '**0**,1,2,3,4...') 

Another thing: if you paste the windows entry make sure it is above/outside the 'automagic' section, otherwise it will be deleted the next kernel update.

Okay, that sounds cool, but there isn't a separate entry for Win 98 - both Win versions are lumped together.

So, how do I get the Win 98 entry separated so I can make it default?

---

### Post by Pumalite on 2007-08-26
Follow logos34. He is the Guru for these things.

---

### Post by logos34 on 2007-08-26
it'll be ok...like pumalite says there';s the backup...Grub just chainloads XP, the rest is the same.  But changing default number would be easier

post your whole menu.lst

---

### Post by logos34 on 2007-08-26
> **Pumalite said:**
> Follow logos34. He is the Guru for these things.

We all know Herman's The Man, the Grub Guru...

---

### Post by trishacupra on 2007-08-26
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
# kopt=root=UUID=8ce152d0-f7ca-462d-bfbc-fd92f8b8755e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ce152d0-f7ca-462d-bfbc-fd92f8b8755e ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8ce152d0-f7ca-462d-bfbc-fd92f8b8755e ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by trishacupra on 2007-08-26
I really appreciate the help, by the way.

If I set the Windows one as default, perhaps it will go to the second menu and then hopefully 98 will be on top and time out?

I'd try right now, but have to go out for a bit. I'll check again here as soon as I'm home.

---

### Post by Pumalite on 2007-08-26
Herman is the Guru of the Gurus.

---

### Post by logos34 on 2007-08-26
yep, its 4, so change default lien at top to

**default 4**

---

### Post by logos34 on 2007-08-26
> **Pumalite said:**
> Herman is the Guru of the Gurus.

whoa, THAT high?

---

### Post by logos34 on 2007-08-26
> **trishacupra said:**
> If I set the Windows one as default, perhaps it will go to the second menu and then hopefully 98 will be on top and time out?

Yes.

---

### Post by Pumalite on 2007-08-26
I have a lot of respect for him.

---

### Post by logos34 on 2007-08-26
> **Pumalite said:**
> I have a lot of respect for him.

I do too.  The guy's a walking encyclopedia on dual-booting, bootloaders, and whatnot.  Those web pages of his are amazing.  Can you ever imagine Microsoft with it' huge tech 'support' dept coming up with web pages even half as useful for troubleshooting?

---

### Post by Pumalite on 2007-08-26
Besides being super knowledgeable and helpful whats comes across is a great personality. Don't even talk to me about Microsoft; I think they are the worst, especially after the famous Vista. And help?..Don't make me laugh; my lips are chapped.

---

### Post by trishacupra on 2007-08-27
Good news.

It worked. Just changing the 0 to a 4 did the trick very nicely. Now, the first menu times out with Windows as the default choice, and Win 98 is the default choice on the second screen. That one takes a whole 30 seconds to time out. I have no idea how to change that, though, but it doesn't really matter. It would be nice to know, though. 

And my geeky brain wonders how you'd make Win XP the default, but that isn't relevant anyway. :)

So thanks very much for resolving this for me. Mum won't ever know Ubuntu is even installed. (Turns out Dad never even told Mum about it, and now it's fixed she'll never know.) :)

THANKS!!!

---

### Post by logos34 on 2007-08-27
> **trishacupra said:**
> Good news.

It worked. Just changing the 0 to a 4 did the trick very nicely. Now, the first menu times out with Windows as the default choice, and Win 98 is the default choice on the second screen. That one takes a whole 30 seconds to time out. I have no idea how to change that, though, but it doesn't really matter. It would be nice to know, though. 

And my geeky brain wonders how you'd make Win XP the default, but that isn't relevant anyway. :)

So thanks very much for resolving this for me. Mum won't ever know Ubuntu is even installed. (Turns out Dad never even told Mum about it, and now it's fixed she'll never know.) :)

THANKS!!!

To change the time out for windows all you need to do is edit boot.ini file. (it's a hidden file--type 'boot.ini in the explorer file browser address bar, or Start>Run>'msconfig'>boot.ini tab)

Here's mine:

> [boot loader]
**timeout**=4
default=multi(0)disk(0)rdisk(0)partition(**1**)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(**1**)\WINDOWS="Windows XP Professional x64 Edition" /noexecute=optin /fastdetect /usepmtimer
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\GRLDR="Start Grub"

To change the OS to XP, you would just put in the partition (**#**) on the 'default' line. (here x64 is default).  

For menu.lst:

If you don't want to see the grub menu at all just take out the hash ('#') in front of hiddenmenu in menu.lst so it reads

**hiddenmenu**

Or lower the **timeout** to 1 or 0  (ihit ESC key at 'Grub loading...' to halt the timeout and see the menu screen)

Loads [more info here on Grub]("http://users.bigpond.net.au/hermanzone/p15.htm") to satisfy your inner geek.

---

### Post by trishacupra on 2007-08-27
Thanks for satisfying my inner geekiness. :)

Trisha

---

