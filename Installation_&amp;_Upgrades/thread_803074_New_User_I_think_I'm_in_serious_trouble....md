---
title: "New User: I think I'm in serious trouble..."
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by SirBritt on 2008-05-22
Okay, Imma make this quick because I need it fixed- fast. 

I got sick of Vista so I decided to try out Ubuntu. I made a CD, popped it in, installed it, ran it, and now I can't boot back into Vista. It won't give me the option to do so when I press ESC during bootup.

I know I'm a new user and all, but I'd just like someone to assure me that my files are all still on the machine. I cannot imagine why installing an OS like Ubuntu would wipe all the contents of a HDD, so if I could just find my files I would feel infinitely better.

In case you hadn't guessed, this situation is EXTREMELY URGENT and could potentially ruin my entire summer.

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Okay, Imma make this quick because I need it fixed- fast. 

I got sick of Vista so I decided to try out Ubuntu. I made a CD, popped it in, installed it, ran it, and now I can't boot back into Vista. It won't give me the option to do so when I press ESC during bootup.

I know I'm a new user and all, but I'd just like someone to assure me that my files are all still on the machine. I cannot imagine why installing an OS like Ubuntu would wipe all the contents of a HDD, so if I could just find my files I would feel infinitely better.

This could potentially ruin my entire summer.

If you could boot on your Ubuntu, Open your terminal and issue this command:

fdisk -l

(that's small L)

 and post whatever it displays.

You could also boot your liveCD and open terminal and try issuing the command above.


*Maybe you used the incorrect method/way of partitioning your drive.

---

### Post by SirBritt on 2008-05-22
> **iaculallad said:**
> 
*Maybe you used the incorrect method/way of partitioning your drive.

Does that mean I'm ******?

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Does that mean I'm ******?

I still don't know it yet, but you could still try issuing the command I posted above you we could double check.

---

### Post by SirBritt on 2008-05-22
It doesn't say anything, unless I'm doing it wrong.

Btw, the wireless isn't yet configured on my laptop, the one that Ubuntu is on, so I'm using another one.

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> It doesn't say anything, unless I'm doing it wrong.

Btw, the wireless isn't yet configured on my laptop, the one that Ubuntu is on, so I'm using another one.

We don't need the wireless connectivity in here, what we're trying to find out is if your NTFS partition is still present. So, we try to use the command fdisk -l first on your terminal.

Why don't you try it first before solving other problems.

---

### Post by SirBritt on 2008-05-22
Gah, sorry if I'm being hasty. It's just the idea of losing ALL of my work has put me on edge.

This is my first time using any Linux based OS, mind telling me how to do this first terminal business?

For anyone that has AIM and can help I'll be online for a while after this. I'd really appreciate it if you helped me out.

My sn is Sir Brittanicvs.

---

### Post by mlissner on 2008-05-22
SirBritt, so you know, that command is going to tell us what your partitioning scheme is currently like on your computer. It's indeed possible you overwrote your vista installation when you installed. It's also possible you didn't. That command will inform us all one way or another.

My fingers are crossed for you.

---

### Post by SirBritt on 2008-05-22
Okay, here it is:
[img]http://img80.imageshack.us/img80/3355/imgp0794mt4.jpg[/img]

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Okay, here it is:
[img]http://img80.imageshack.us/img80/3355/imgp0794mt4.jpg[/img]

Sorry to say, you did mess up your partition. NTFS drive/s does not show up on your fdisk -l.

---

### Post by SirBritt on 2008-05-22
And let me guess...

I'm screwed.

---

### Post by prshah on 2008-05-22
> **SirBritt said:**
> 
This is my first time using any Linux based OS, mind telling me how to do this first terminal business?


[s]Boot off the live CD, and when you get to the main screen, click on Applications-Accessories-Terminal.

Then give the command as mentioned earlier, eg```
sudo fdisk -l
``` and note what it says (exactly!) and post here; or take a snap with a digital camera and post the snap here.[/s]

EDIT: OK, Boom, pointless. I really have to realize that others are typing as well when I'm typing.

---

### Post by Living2007 on 2008-05-22
Is the entire partition ext2/3 or is their a NTFS Drive?

If so, then GRUB needs to be edited.

---

### Post by vibinlakshman on 2008-05-22
Dont panic buddy , after entering ubuntu , get a terminal , type gedit /boot/grub/menu.lists .. If u can find the Vista in that grub list , surely it wud be there if u install ... If u find the Vista below Ubuntu , copy and paste the whole content , on the top of ubuntu menu , Then send me what happens ... We r always here 2 help

---

### Post by SirBritt on 2008-05-22
Thanks for all your help guys. :D

My laptop (with Ubuntu) is not connected to the internet, so I'm using a desktop.

I tried the gedit /boot/grub/menu.lists .. command and it opened up a text document with nothing in it. >_>

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Thanks for all your help guys. :D

My laptop (with Ubuntu) is not connected to the internet, so I'm using a desktop.

I tried the gedit /boot/grub/menu.lists .. command and it opened up a text document with nothing in it. >_>

That should be:

sudo gedit /boot/grub/menu.lst

---

### Post by SirBritt on 2008-05-22
Still got an empty gedit window.

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Still got an empty gedit window.

From what mode are you issuing this command? From the "LiveCD bootup" terminal or from the installed Ubuntu terminal on your system?

---

### Post by SirBritt on 2008-05-22
From the installed Ubuntu terminal on the system.

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> From the installed Ubuntu terminal on the system.

If this is what you did: 

ian@gutsy-gibbon:~$ sudo gedit /boot/grub/menu.lst
[sudo] password for ian:

and still it provided an empty window, I guess you messed up already.

Try clicking to:

Places->Computer

can you see any vista drive in there?

---

### Post by R_T_H on 2008-05-22
I kniw this is a bit ahead of the game, but if you go to Synaptics and search for Data Recovery, you should be able to get a program that will be able to pull *some* of the files back. I'm sorry I can't remember what it's called, and it's a lot of work, and it'll probably restore every file ever deleted, but it's worth a try :)

Good luck! :)

---

### Post by SirBritt on 2008-05-22
Okay, i got the gedit thing to work finally. Heres what it gave me: 
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
# kopt=root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by iaculallad on 2008-05-22
> **SirBritt said:**
> Okay, i got the gedit thing to work finally. Heres what it gave me: 
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
# kopt=root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=54cb5cc0-697b-4d9e-b603-c424e65852ec ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Does not reflect any NTFS drive either.. sorry :(

---

### Post by Living2007 on 2008-05-22
It seems that Vista has be removed, but that is from th GRUB's Point of View

Try in treminal```
fdisk -l
```that is a lower case L

This should address if your drive still has Vista

---

### Post by SirBritt on 2008-05-22
Well then. It's time for me to get some sleep and time for this laptop to meet the asphalt...okay, well maybe. :p

Thanks again for all your help guys. :)

---

### Post by SirBritt on 2008-05-22
Okay, so now that I'm well rested I'm ready to give it one last try.

And the throws of sleep were infinitely cruel to me last night. I kept dreaming that my Vista worked, and I grabbed the files I needed to tossed the ******* thing.

So before I went to sleep, the nice guy on AIM I was talking with about this situation suggested installing Ubuntu on another hdd and using gddrecovery to get the files I needed. How would I do that?

EDIT: I just had an idea- forgive me if this sounds silly, I don't know much about OSes. But would I be able to get a Vista recovery or installation disc or something and boot up Vista that way to get my files?

---

### Post by kugn on 2008-05-22
See if this helps:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by lewac on 2008-05-22
yes... you've overwritten your primary partition on the 1st drive (vista). and unfortunately you don't have another partition on this drive (prior to the ubuntu install). this is definitely "ugly" because if you don't have your data backed to removable media (CD / DVD) or to a networked machine you've lost something much more important than your OS... your valuable data. thus all any of us can do for you now is advise...

basic computer skills notwithstanding here one should ALWAYS save data to a partition OTHER THAN the OS partition. at least then if you trash your OS more than likely the data will still be there (because it resides on an alternative partition). remember that you can always restore the OS (or somebody else can). but your data is YOUR data! if you value it as much as you obviously do PLEASE in the future take the time to learn how to protect it.

finally when one installs any new OS one should always back the entire partition(s) of relevance to removable media (or to another networked machine if you have one). another choice here is to install a second hard drive and back to that. unfortunately for someone with only basic skills this is not an easy thing.

there are some great tools out there to do this with. first do a search on "mbrtool.exe" (this utility backs your MBR/1st sector on up to 4 physical drives). secondly do a search on "rescueCD". we don't go ANYWHERE without these tools in our "backpack". luck to you...

---

### Post by SirBritt on 2008-05-22
> **kugn said:**
> See if this helps:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Thanks, that looks handy. :)

Well I'm not AS screwed as I thought I was. Fortunately the last backup I made contained enough data to make an okay recovery, as I was planning to format some time this summer but Ubuntu sounded like an easier option.

I still need that Photoshop file though. Most everything else is replaceable...hopefully...

---

### Post by mlissner on 2008-05-22
Well that's good. The real problem isn't that *he* didn't backup. It's that backups aren't a part of computers by default. It's a problem we will definitely overcome soon, because it's obviously becoming more and more ridiculous to set up your own backup solution, test it, use it, etc.

---

### Post by ghindo on 2008-05-23
I know this may seem a bit insensitive, but this is why you should always always *always* back up the important stuff before doing anything major.  

I'm sorry about your loss of data and hope that you will be able to recover it!

---

### Post by Trebaruna on 2008-05-23
I think the "MAKE A BACKUP!" speech has been made enough, now. The fact that SirBritt lost data is likely enough incentive for him to consider a backup strategy, anyway.

Also, parted (from the DataRecovery link) seems like the way to go (or its listed alternatives, perhaps), but keep in mind that due to the format as ext3, there will be "islands" of ext3-related data. These islands will have corrupted (or entirely overwritten) any data previously present there. Do not expect a full recovery. Do not expect large files to have survived 100% intact.

---

