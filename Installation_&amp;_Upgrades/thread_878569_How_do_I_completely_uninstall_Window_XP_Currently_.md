---
title: "How do I completely uninstall Window XP? Currently Dual OS."
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by jalal0 on 2008-08-03
[FONT="Arial"][COLOR="Blue"]I am using both Ubuntu and XP, as dual OS on my PC. I recently had some problem with XP (dont know what), and can no longer gain access to my XP account. The screen freezes at the start-up phase (when asked to press Alt+Ctrl+Del, nothing happens when I press these combination keys).

I initially though of troubleshooting it, but feel since I seldom use XP, I be better off, completely uninstalling it from my PC. And therefore have all the hard disk allocated for Ubuntu.

Now the issue is:

-I want to uninstall XP, but strictly dont want to lose any application I installed on Ubuntu. I have certain very valuable applications running on Ubuntu, which I use for my work-related purpose. And there is simply no way, I want to lose them and re-install those application again.

-I can not log in to XP.

-I want that, after uninstalling XP, I should have all hard disk space allocated to Ubuntu.

Given this scenario, whats the safe way of uninstalling XP?

Thanks[/COLOR][/FONT]

---

### Post by tamoneya on 2008-08-03
the way you uninstall an OS is by formatting its partiton.  Just open up gparted: alt-F2 ```
gksudo gparted
```
Find the NTFS partition where XP is installed and delete it.  If you want to be really safe you just turn the new space into a new partition. The simplest method is with ext3.  Then mount it to you filesystem.  If however you want to simply increase the size of ubuntu and not have spare partitions you have to use the liveCD.  Follow the same steps with the liveCD installed but this time tell gparted to also expand the ubuntu (most likely ext3) partition.  If you do the second method I would recommend backing your vital data up.  While the process itself isnt dangerous if you hit the wrong buttons by mistake or something you can seriously wipe out some data.  Just be careful though and you should be fine.

---

### Post by Sef on 2008-08-03
> -I want to uninstall XP, but strictly dont want to lose any application I installed on Ubuntu. I have certain very valuable applications running on Ubuntu, which I use for my work-related purpose. And there is simply no way, I want to lose them and re-install those application again.


Back up your data.  There is no way to guarantee 100% success.

---

### Post by meindian523 on 2008-08-03
Are you sure you have a dual boot and not Ubuntu under Windows using WUBI?Quite a few people have the misconception that these two terms mean the same.I ask because:
> **jalal0 said:**
> [FONT="Arial"]
-I want to uninstall XP, but **strictly dont want to lose any application I installed on Ubuntu.** I have certain very valuable applications running on Ubuntu, which I use for my work-related purpose. And there is simply no way, I want to lose them and re-install those application again.
[/FONT]
Loss of applications installed on Ubuntu will only happen if you installed Ubuntu under Windows and then remove Windows.That is removal of Windows automatically implies removal of Ubuntu IF you have installed Ubuntu using WUBI.

---

### Post by wpshooter on 2008-08-03
> **meindian523 said:**
> Are you sure you have a dual boot and not Ubuntu under Windows using WUBI?Quite a few people have the misconception that these two terms mean the same.I ask because:

Loss of applications installed on Ubuntu will only happen if you installed Ubuntu under Windows and then remove Windows.That is removal of Windows automatically implies removal of Ubuntu IF you have installed Ubuntu using WUBI.

To me this is just another reason why people should not be using different O/Ss on the same computer.  

And additionally, to me it is an insult to Ubuntu to be installed inside of windows, especially when you consider that that (IMO) Ubuntu is the better O/S.

---

### Post by crhylove on 2008-08-03
> **wpshooter said:**
> To me this is just another reason why people should not be using different O/Ss on the same computer.  

And additionally, to me it is an insult to Ubuntu to be installed inside of windows, especially when you consider that that (IMO) Ubuntu is the better O/S.

What?!?  Are you crazy?  I can boot into 5 different OSes on this machine, and also have tons of VM machines installed in several of them.  More OSes on a box THE BETTER, if you know what you're doing. :)

---

### Post by jalal0 on 2008-08-03
[FONT="Arial"][COLOR="Blue"]Dear all,

You got to appreciate that not all people are geeks and come from the same background. Nor is it necessary that I have the same hardware performance as your to run 5 OS on my PC.

And yeh, I am very sure. I have Ubuntu installed as a dual OS on my PC, along with XP.

I feel, I will take the advice of tamoneya. Given the significance of the applications I have on Ubunutu, I would be as nervous a bomb-disposal team, to defuse a bomb (uninstall XP). Because as tamoneya mention, one wrong key, and its all gone.

Anyway, any one else got more suggestions in the meantime?[/COLOR][/FONT]

---

### Post by wpshooter on 2008-08-03
> **crhylove said:**
> What?!?  Are you crazy?  I can boot into 5 different OSes on this machine, and also have tons of VM machines installed in several of them.  More OSes on a box THE BETTER, if you know what you're doing. :)

You may know what you are doing, but the real question is, do each of these O/Ss **always** know what the others are/might be doing ?  I doubt that M/S, Linux & whatever other O/S are getting together each night to make sure that they don't cause each other any problems.

I think you are living dangerously.  But if that is what you like, that's fine, go for it.

---

### Post by meindian523 on 2008-08-03
> **wpshooter said:**
> To me this is just another reason why people should not be using different O/Ss on the same computer.  

And additionally, to me it is an insult to Ubuntu to be installed inside of windows, especially when you consider that that (IMO) Ubuntu is the better O/S.
I beg to differ.Sometimes you can't avoid doing this,and sometimes,it's how you learn stuff about OS's.I have a triple boot,XP for family who haven't migrated yet,8.04 for my main distro,and openSUSE 11.0 to try out-cum-backup distro-cum launchpad for Qt development.But,I agree that Ubuntu(for that matter any *nix) being installed under Windows is an insult to the *nix.

---

### Post by tamoneya on 2008-08-03
> **jalal0 said:**
> [FONT="Arial"][COLOR="Blue"]Dear all,

You got to appreciate that not all people are geeks and come from the same background. Nor is it necessary that I have the same hardware performance as your to run 5 OS on my PC.

And yeh, I am very sure. I have Ubuntu installed as a dual OS on my PC, along with XP.

I feel, I will take the advice of tamoneya. Given the significance of the applications I have on Ubunutu, I would be as nervous a bomb-disposal team, to defuse a bomb (uninstall XP). Because as tamoneya mention, one wrong key, and its all gone.

Anyway, any one else got more suggestions in the meantime?[/COLOR][/FONT]

What is your reason behind wanting to remove it?  Is it that you dont want to see the boot prompt for it or that you need more space?

---

### Post by jalal0 on 2008-08-04
[FONT="Arial"][SIZE="2"][COLOR="Blue"]The reason, why I want it be removed is because I need more memory. 

In the meantime, I was offered this solution by one of my friend, I think, what this solution does is just remove XP option from the option list at the selection of OS boot option

_**[QUOTE START]**_

Ok now you need to rewrite this file over the old menu.lst

First download the menu.lst, and move it to your /home folder

You will need to use the sudo command

Assuming, the new menu.lst file is in the dir /home, just type this on the command prompt

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.old

sudo cp /home/menu.lst /boot/grub/menu.lst

And then restart the system. You should find that the option for windows xp would have gone.

Fahad

THE NEW menu.lst looks like this: _**[FILE STARTS]**_

# menu.lst - See: grub(8.), info grub, update-grub(8.)
#            grub-install(8.), grub-floppy(8.),
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
# kopt=root=UUID=736fd484-20c3-45f3-8830-19c4e0fe63b5 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title		Ubuntu 7.10, kernel 2.6.22-15-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=736fd484-20c3-45f3-8830-19c4e0fe63b5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=736fd484-20c3-45f3-8830-19c4e0fe63b5 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=736fd484-20c3-45f3-8830-19c4e0fe63b5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=736fd484-20c3-45f3-8830-19c4e0fe63b5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

[U][B][FILE ENDS]
[QUOTE ENDS][/B][/U][/COLOR][/SIZE][/FONT]

---

### Post by tamoneya on 2008-08-04
Thats why I was asking what your reasons are.  If you simply dont want to see the boot prompt I would suggest what your friend has just suggested which should work fine.  However this will not free up any of your harddrive space.  You either have to get an additional internal or external harddrive or you need to do some reformatting.

---

### Post by JarekG on 2008-08-04
Hi all,

I'm kind of in the same boat as jalal0.
I had XP and it was doing some funny stuff, since I was thinking about switching to *nix before i thought why not install Ubuntu and see if this is something that i can use for every day usage.
I have been using Ubuntu for the last 2 weeks and i do like it and since i can use VMWare to install XP (I still need it to use for work....mostly VS2005 and ASP.net).

I used GParted to format the XP partition to ext3 and now i have 50 Gigs partition that is free. I can access it using Nautilus but now I'm not able to put any files on it. I want to put my VMWare image there mostly.

Now the question is: with out any formatting is there a way that i can make this to accessible from with in Ubuntu and mostly be mounted when the OS starts.

If I'm not mistaken this is what jalal0 want to do as well.
I'm OK with the menu in GRUB, not planning to restart this computer too often so i will not see it ;).

Don't mean to hijack this thread but it looks like this is the same "problem" as jalal0.

Thanks in advance.
--Jarek

---

### Post by meindian523 on 2008-08-05
You need to create a mount point for your 50Gig partition and edit your /etc/fstab to make it automountable,just follow the format already available in the fstab file,making sure to use the appropriate filesystem,in your case ext3.

---

### Post by JarekG on 2008-08-05
Thanks meindian523

After little more search on the net I found this article which was really easy to follow (even for new *nix user as me).

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

> **meindian523 said:**
> You need to create a mount point for your 50Gig partition and edit your /etc/fstab to make it automountable,just follow the format already available in the fstab file,making sure to use the appropriate filesystem,in your case ext3.

---

### Post by meindian523 on 2008-08-06
You found the holy grail of the ubuntuforums!NOOO,let go!:-P :D

---

### Post by jalal0 on 2008-08-07
[FONT="Arial"][COLOR="Blue"]Okay, so far.....

First install Partition Editor using this command:

```
sudo apt-get install gparted
```

If you get any error message, then, download the package and get it installed:

[http://packages.ubuntu.com/search?keywords=gparted]("http://packages.ubuntu.com/search?keywords=gparted")

Once thats done:

System> Administrator> Partition Editor

XP will be in the NTFS partition, right click it, and then UNMOUNT it. Dont worry its safe. Once unmounted. You can safely delete it by right clicking it again and selecting Delete. I just did that, and had no problem. Trust me on this.

Once thats done. You can then increase the partition size of your Ubuntu (ext3). This is something I have yet not done. But as per information given from, [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")
 this can be done using a Ubuntu LiveCD.

So the next step for me it to download the .iso image, burn it on a CD and attempt to increase the partition space of my current Ubuntu partition.

So far so good. Anyone got any suggestion or ideas for increasing the partition space using LiveCD. 
I would make this daring attempt, once I gather more information and am sure that I know all the steps, and everything is safe and sound to attempt. But surely, I would update you folks once I achieve something out from it.
[/COLOR][/FONT]

---

### Post by meindian523 on 2008-08-07
Please stop using blue.GParted is available on the LiveCD under System>>Administration>>Partition Editor.

---

### Post by jalal0 on 2008-08-08
[FONT="Arial"][COLOR="Blue"]_THE SOLUTION (TESTED):_

Get a Live CD. Reboot your system, with the CD inside, and select, boot from CD.

You will then see a startup screen.

Select:

"Start Ubuntu in safe graphics mode"

It will then take around 2-3 min to load.

System> Administration> Partition Editor.

Right click and delete off your XP partition. And then click Apply (Top right).

Once thats done. Select your Ubuntu partition. And Select Resize/Move, increase the partition size as much as your system allow

Click Apply.

And its all, ready steady go.

This is how simple it is. And yeh, contrary to earlier post no need to worry about the data loss myth. Nevertheless, I would still advice you to do backup. Dont blame me.

I just did it, deleted XP partition, increased my Ubuntu partition, and all works fine.
Assuming you got LiveCD, the whole procedure can be done in 10-15 mins.


_USING THE SAME APPROACH TO UNINSTALL UBUNTU:_
Okay, the same approach can also be used to uninstall Ubuntu from a PC having dual OS. Just delete the Ubuntu partition, click Apply, and increase your XP partition, click Apply.

I just tried it. And works fine. However, on restart, you get GRUB error 22. Which can basically be troubleshooted with a XP CD. I got to get XP CD, before I go on to give my verdict on this. But I tried uninstalling Ubuntu as well on my laptop, and till the GRUB error 22 point, all works fine.[/COLOR][/FONT]

---

### Post by Yudraciell on 2008-08-18
well if windows don't run doesn't that mean ubuntu wont run if its wubi???

---

### Post by mike1234 on 2008-08-18
I don't mean to insult anyone but I have a hard time understanding why anyone fears installing an operating system. Maybe because after 18+ years of experience, I've done it thousands of times. Windows, Linux, Unix. Sometimes just for experimentation. The rewards have been tremendous. I got in the habit from my early Windows days because doing clean installs is the only way to fix all those corrupted files that you get from using Microsoft. I recommend it. I keep all my valuable data on cd, dvd and usb flash drives anyways. Just do away with Windows. It is really a joke comparing it to Linux. 

M.

---

