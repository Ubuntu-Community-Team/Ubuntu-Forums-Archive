---
title: "Setting bootloader options"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-04-13
Dear Ubuntufolk

I just installed Ubuntu 6.10 beside Windows XP, using the space that contained Fedora Core 4.  Under Fedora Core 4 I had the GRUB default set to Windows XP.  Now I see that the default is set automatically to Ubuntu.  I would like to set the default to Windows XP again.  I fiddled a little with the settings on GRUB without knowing what I was doing and although I probably didn't do any serious damage (since I can boot), I probably need a complete list of commands for the main Ubuntu option and the Windows XP option on GRUB, in such a way that Windows is the default.  In a pinch I can reinstall Ubuntu, but I would still need to know how to make Windows the default.

Thanks.

Whatawonderfulday

---

### Post by bulldog on 2007-04-13
Count the entry's in your menu.lst```
cat /boot/grub/menu.lst
``` starting with zero,one,two.....
The number of your windows entry you should enter here ,instead of the zero listed.
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0  **<------ windows entry number**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```

To edit the menu.lst```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Whatawonderfulday on 2007-04-13
Thanks, Bulldog.

Others should note that the line 'other operating systems' counts as one entry.  When I counted just operating systems I was 1 off and GRUB tried to load that line.  When I added 1 to account for that line, everything went okay.

There are other options explained that make life easier, for example silent loading of the default operating system unless you press ESC; the time delay before booting.

Whatawonderfulday

---

### Post by falkenheart on 2007-05-04
Is there any way to run Grub using a mouse?

---

### Post by kevin tough on 2007-05-22
Just got a ubuntu 7.04 Feisty Fawn DVD and started the install.  I chose my install partitions and found the advanced button to select a location for the boot loader. I do not wish to install a boot loader!  I have enough versions of Linux mixed with Windows XP I almost forget where they all are. I certainly do not wish to overwrite anything. Can I install 7.04 without a boatloader and not write into any existing MBR.  My install ended at this point with cancel. Help would be greatly appreciated as until I clear this up Feisty Fawn can continue to play in the woods.

Namaste,

Kevin Tough

---

### Post by Whatawonderfulday on 2007-05-24
To Kevin Tough:

This is a little beyond my technical expertise, but let me pose some questions:

Are you trying to set up a dual boot without a bootloader?  As far as I know this is impossible.  In the transition from BIOS to OS boot, BIOS has to go somewhere to get the address of the OS; it's set up to go to an address on the MBR, which gives it the start address of the OS.  But if you have two OS's, how are you going to be able to boot one or the other OS without inserting an interface at the OS address on the MBR to point to the OS you want to boot?  That's what I understand a bootloader to be doing.  At the standard location on the MBR, BIOS finds the address not of the OS but of the bootloader.  The bootloader then handles the selection of the OS to boot, providing the subsequent address of the correct OS to boot either by default or through your selection.   I am not an expert on these matters, but I don't see how you're going to have a dual boot without a bootloader.

Do you want to set up a bootloader that's not on the MBR?  This is possible, but you will have to search a little to see how it's done.  There is an option on the bootloader (advanced options at bootloader set up time during install) whereby you can have the bootloader placed on /boot (or I suppose elsewhere).  But as far as I know, the BIOS > MBR address > bootloader sequence remains identical.

Are you just trying to make a copy of the installation disk?  Obviously not, that's trivial.

Are you trying to install Ubuntu as the sole OS on a computer?  I don't know whether you need a bootloader in such cases (the install will probably decide), but in such a case there's no problem since there's only one OS: there should be no reason for the setup not to work even if there is a bootloader.  But since you have problems with your MBR this doesn't seem to be what you have in mind.

Sorry I don't know enough to help more.

Whatawonderfulday

---

### Post by kevin tough on 2007-05-25
Hi WhatAWonderfulDay,

I have roughly 8 distros installed on my computer. Therefore my  /etc/grub.conf is already quite customised. Once I have installed the new fawn I will include an entry to find its /boot/vmlinz... and /boot/initrd... files. This is easy but if I rewrite the MBR then I have to use grub from its command prompt to relocate everything. With many other linux installers a person has the option to not install the bootloader.  I just wanted to know if Ubuntu allows this.

Namaste,

Kevin Tough

---

### Post by bernied on 2007-05-25
Kevin

Perhaps the easiest way to deal with this is to tell the installer to put grub on the partition where you are installing, not on the MBR. That way the installer can add the kernel options that it likes in it's own customised menu.lst and when you get kernel updgrades the grub configuration will be updated automatically without interfering with any of your other OSes.

To boot to this, just have an entry like this in your master grub config file:
```
title ubuntu
configfile (hdx,y)/boot/grub/menu.lst
```(where (hdx,y) is wherever you have installed your ubuntu.
This will load ubuntu's grub menu, and you're away.

---

### Post by Whatawonderfulday on 2007-05-25
To Kevin Tough:

Well you must know what you are doing if you have 8 distros on your machine (not to mention a big machine!).  I really don't understand what you mean about having the install CD not install the bootloader, unless you mean re-install, since you already have a bootloader.  Of course I may just be demonstrating my ignorance.

In any event, it seems that berneid knows a lot more than me and that his advice is sound.

Whatawonderfulday

---

### Post by rillip on 2007-05-25
I think it'd be easiest just to make a backup of the grub menu.lst, let it reinstall, then copy the menu list back.  I'm sure you can do it without this step, but frankly, it'd be a lot of research and work, and this seems trivial since you're already using grub.

---

### Post by kevin tough on 2007-06-01
Hi bernied,

Way too cool for school!  Hey, its been a lot of years since that saying fell off the tongue. Configfile is a super command for us with multiple installs. Ja, the Ubuntu installer messed up the mapping and erased my master boot. With 3 bootable drives I thought I might be safe, but oh well.  With configfile a person can set-up a master grub file and straighten all root commands and such to reflect only one bios boot order. Is it however useful to leave  a distro that would boot from another boot order setting in the computer's BIOS? Then that one distro would have to be setup for that new BIOS boot order and its entry in the master grub manually updated as I had been doing for all distros.
My fedora_64_Rescue_CD or Puppy Linux rescues me every time so far but I was just wondering how the professionals set up a multi-distro computer in which  a person can change the boot order in BIOS?  I have two satas and one IDE.

Namaste,

Kevin Tough :)

---

