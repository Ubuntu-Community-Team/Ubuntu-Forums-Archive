---
title: "Grub2 update in 2 OS"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by PedroGomes on 2012-04-18
Hi 

I just put to work a double installation setup for a remote cluster where I have 2 versions of Ubuntu for now. Since I saw several threads against the use of a single /boot partition, that I tried and it only give me problems, I have a each system manage its own /boot partition. 

The problem is that only one system controls grub as far as I know, in this case the 2nd OS. 
So, I install the OS1, the bootdev in sda, and then install OS2 that takes control of grub but in the rest all works fine. 
When I want to change OS, i edit etc/default/grub and update grub and on reboot I change to OS1. When I'm one OS1, as far as I tried, the only way to change to OS2 is to mount it and directly change /boot/grub/grub.cgf

I'm I doing something wrong here? Is there another option? 
Remember that this was to be as automated as possible so no graphical tools please like boot-repair or grub-customizer.

---

### Post by dino99 on 2012-04-18
dont tweak  /boot/grub/grub.cgf

simply set grub in the /dev/sda mbr for both OS then:    sudo update-grub

---

### Post by PedroGomes on 2012-04-18
> **dino99 said:**
> dont tweak  /boot/grub/grub.cgf

simply set grub in the /dev/sda mbr for both OS then:    sudo update-grub



I thought I did it already. In my installation, on the first OS i use in the preseed:

```

d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
#install on /dev/sda
d-i grub-installer/bootdev string (hd0)

```

In the second instalation:

```

d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean false
d-i grub-installer/bootdev string (hd0)

```

I'm installing to the /dev/sda no? What I'm I doing wrong? :confused:
And I ran "update-grub" when changing to change to the other OS... update-grub2 more precisely (dunno if there is a difference), so...

---

### Post by darkod on 2012-04-18
If you didn't touch any of the grub2 config, the ubuntu on top is your install which installed the grub2 on the MBR, and on the bottom the other one.

So, if you second install, OS2 as you call it, was the one that installed the current (and latest) grub2 to the MBR, when you get the grub2 boot menu on boot, the top ubuntu is OS2, and the bottom ubuntu is OS1.

For the bottom it will also state on which partition it's found.

You can boot either from your boot menu.

Does it work like that or not? If it does, what actually are you trying to achieve?

If it doesn't, what exactly happens when you select the top ubuntu, and the bottom ubuntu?

---

### Post by oldfred on 2012-04-18
Only one install can be in the MBR. dino99's commands will get you booting both from either one that is in MBR. Not sure what you are doing.

You should just have whichever system you boot the most in the MBR and let sudo update-grub add the other to your menu.

You can directly install grub to the MBR from a working install that is not currently in the MBR.

sudo grub-install /dev/sda

Grub does have an entry on where to reinstall if you have major updates. So if you installed your other install to the MBR and it gets a major update to grub2, it may reinstall itself to sda.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you do not want it to reinstall anywhere you can unselect everything. Or you can force an install to the partition which is not recommended, but if you do not use it, then it does not matter. You use grub from your primary install to boot both systems.

sudo update-grub2 just calls sudo update-grub which actually calls:

#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

---

### Post by PedroGomes on 2012-04-18
> **oldfred said:**
> 
Only one install can be in the MBR. dino99's commands will get you booting both from either one that is in MBR. Not sure what you are doing.

You should just have whichever system you boot the most in the MBR and let sudo update-grub add the other to your menu.

You can directly install grub to the MBR from a working install that is not currently in the MBR.

sudo grub-install /dev/sda

Grub does have an entry on where to reinstall if you have major updates. So if you installed your other install to the MBR and it gets a major update to grub2, it may reinstall itself to sda.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you do not want it to reinstall anywhere you can unselect everything. Or you can force an install to the partition which is not recommended, but if you do not use it, then it does not matter. You use grub from your primary install to boot both systems.

sudo update-grub2 just calls sudo update-grub which actually calls:

#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"


But I don't have a system that I boot the most, and so I think the real question here can be summarized to: 

** Is there a way of changing the grub default entry from both systems?**

That is all I need, because my need is to have a way of changing from one OS to the other when having no physical access to the machine. 
In the moment I can do it, simply by changing the /boot/grub/grub.cfg directly on the controlling system, but I don't know if this has repercussions.

---

### Post by darkod on 2012-04-18
What you could do, is change the GRUB_DEFAULT entry in /etc/default/grub. After that running update-grub will recreate new grub.cfg file, and upon reboot the default OS will be different.

Just make sure you don't make a mistake when counting the position in the boot menu. And that a new kernel installation doesn't move the bottom OS position.

When counting it goes top to bottom, and starts from 0. So, the first line in the menu is 0, the next 1, etc.

In any case, I think you are doing this in a very complicated manner. First the machine is remote, on top of that you want two separate OSs, and on top of that to change the default OS back and forth. You're looking for trouble.

But that's your choice. :)

PS EDIT: I don't know what are you doing with this machine, but maybe you can consider having them as virtual machines. That way there is only one OS per machine, on top of that you can have both machines online at the same time while in dual boot you can only have one OS booted at the same time.

---

### Post by PedroGomes on 2012-04-18
> **darkod said:**
> What you could do, is change the GRUB_DEFAULT entry in /etc/default/grub. After that running update-grub will recreate new grub.cfg file, and upon reboot the default OS will be different.

Just make sure you don't make a mistake when counting the position in the boot menu. And that a new kernel installation doesn't move the bottom OS position.

When counting it goes top to bottom, and starts from 0. So, the first line in the menu is 0, the next 1, etc.

In any case, I think you are doing this in a very complicated manner. First the machine is remote, on top of that you want two separate OSs, and on top of that to change the default OS back and forth. You're looking for trouble.

But that's your choice. :)

PS EDIT: I don't know what are you doing with this machine, but maybe you can consider having them as virtual machines. That way there is only one OS per machine, on top of that you can have both machines online at the same time while in dual boot you can only have one OS booted at the same time.

If you read my first post you will see that this is what I do, but it only works in the system that installed, (or last installed) grub. When on the other OS, running update-grub has no effect.

---

### Post by oldfred on 2012-04-18
You can only run the sudo update-grub on the other system if you chroot into your other system.

You can set default on reboot:
[http://ubuntuforums.org/showthread.php?t=1310463](http://ubuntuforums.org/showthread.php?t=1310463)

A couple of others alternatives which I can think of but do not know if they would work. I think my old install of OS/2 used to do something like a dd of the MBR and in Windows you specified if you wanted to boot OS/2 it copied(dd) the OS/2 boot loader into the MBR. If in OS/2 you could then copy the Windows boot loader in the MBR.

You can write a couple of scripts for each system and save mbr.bin for each system can dd one or the other into the MBR depending on which you want to boot.
Backup the MBR e.g. 
sudo dd if=/dev/sda of=mbr.bin bs=446 count=1



Or you can create a script to edit grub.cfg to change boot order, but as Darko suggested you may have to keep track of boot order. 

grub.cfg is read only and should not normally be edited:
sudo chattr -i /boot/grub/grub.cfg
gksu gedit +28 /boot/grub/grub.cfg

But instead of using number you can use name. This was a Windows example but it can be any name:
If grub 1.99 with submenus it is a bit different - drs305
[http://ubuntuforums.org/showthread.php?p=10720316](http://ubuntuforums.org/showthread.php?p=10720316)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by darkod on 2012-04-18
> **PedroGomes said:**
> If you read my first post you will see that this is what I do, but it only works in the system that installed, (or last installed) grub. When on the other OS, running update-grub has no effect.

Like oldfred said, you will need to chroot.

Directly editing will have effect only in the OS that is controlling grub2 on the MBR, in other words OS2. When you boot OS1 the way you want it, which you say it's working, you make OS2 default again you will need to chroot into OS2 root partition, edit /etc/default/grub, and run update-grub. All of that from within the chroot.

Making changes in OS1 grub config makes no difference.

---

