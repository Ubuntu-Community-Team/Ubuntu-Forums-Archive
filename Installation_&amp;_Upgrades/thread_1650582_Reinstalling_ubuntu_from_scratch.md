---
title: "Reinstalling ubuntu from scratch"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by charmedncursed on 2010-12-21
I am a noob
I tried to upgrade ubuntu 8.10 to 9.04 but interrupted the process as it was taking alot of time..It cost my updating my ubuntu..But I found a solution and then upgraded to ubuntu 9.04, again I interrupted ubuntu upgrade to 9.10 and now I am not able to get into the desktop display.
It keeps saying that: 1 not fully installed or removed...and then fails to remove 2.6.27-17-generic : no such file or directory

Anyways I have lost all hope it repair my laptop...All I can do is get the terminal and high speed net.I want to reinstall ubuntu but the disk drive is not booting itself....Can somebody guide me how to do that?

---

### Post by Quackers on 2010-12-21
Welcome to UF.
It is never a good idea to interrupt a computer that is accessing its hard drive. The drive can be damaged that way.
In order to boot from the live cd it is necessary to change the boot priority in the bios so that the cd drive is the first boot device.
Have you done that?

---

### Post by garvinrick4 on 2010-12-21
put in install cd and use try ubuntu when opens get internet working.
sudo fdisk -l (lower case L)
find your ubuntu install #. Like sda1 or sda2 or sda5 whichever it is.
I will use sda1 for this: Copy and paste these one at a time to try and fix your install.
Sorry I forgot to code tag them before entering (to lazy to do all the tags now)
sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
dpkg --configure -a
apt-get update && apt-get upgrade
dpkg --configure -a
update-grub
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt
sudo reboot

---

### Post by charmedncursed on 2010-12-21
thanks for the quick response!:p
Will check if that works
[IMG]http://ubuntuforums.org/showthread.php?t=1006656[/IMG]
[IMG]http://img254.imageshack.us/i/83790325.jpg/[/IMG]

---

### Post by charmedncursed on 2010-12-21
I reached to apt-get update && apt-get upgrade but it shows the following error
[[IMG]http://img149.imageshack.us/img149/2364/40572099.jpg[/IMG]]("http://img149.imageshack.us/i/40572099.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Sorry about the inverted image...just a bit frustrated

---

### Post by garvinrick4 on 2010-12-21
if you are still in root run:
```
dpkg --configure -a
```
```
apt-get -f install
```

Can anyone read the errors in screenshot?

---

### Post by garvinrick4 on 2010-12-22
Do you get to grub menu to use recovery or even a different kernel?

---

### Post by charmedncursed on 2010-12-22
Sorry:

Removing linux-restricted-modules-2.6.27-17-generic ...
rmdir: failed to remove '/lib/modules/2.6.27-17-generic/volatile/': No such file or directory
FATAL: Could not ope '/boot/System.map-2.6.27-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-17-generic
cpio: ./sbin/udevadm: Cannot stat: No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.27-17-generic
dpkg: error processing linux-restricted-modules-2.6.27-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-restricted-modules-2.6.27-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by garvinrick4 on 2010-12-22
Is there another kernel to boot with? Does it get to the grub menu to choose which
kernel to boot with? Is there like a 2.6.27-16 or a 2.6.27-15 that shows up in menu choice.

---

### Post by charmedncursed on 2010-12-22
I tried but the above error persists
After apt-get -f install, is says-

The following packages will be REMOVED:
  linux-restricted-modules-2.6.27-17-generic
0 upgraded, 0 newly installed, 1 to remove and 1063 not upgraded
1 not fully installed or removed
After this operation, 2433kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 121449 files and directories currently installed.)


And then same as above post

---

### Post by charmedncursed on 2010-12-22
I only have kernel 2.6.28-19-generic

Edit: I just figured out how get to the grub>

---

### Post by garvinrick4 on 2010-12-22
where are you now?

---

### Post by charmedncursed on 2010-12-22
At
grub>

---

### Post by garvinrick4 on 2010-12-22
So if you reboot it will go to grub>
and when it says 1063 to upgrade and
2.6.37-17 to remove you say yes to that
and it does what is on the screen shot?

---

### Post by charmedncursed on 2010-12-22
ok I am there

---

### Post by garvinrick4 on 2010-12-22
> **charmedncursed said:**
> ok I am there
Where rebooted and it went to grub>?

---

### Post by charmedncursed on 2010-12-22
Ok here is the thing...to get to the terminal I go to 2.6.28-19-generic (recovery)
from there to recovery menu  and then netroot

So when I type exit, it takes me back to the recovery menu....

and when I rebooted  and reached the grub> it says nothing ( what command I have to enter here?)
I am a mech student and so haven't been in this area for long...

---

### Post by theasprint on 2010-12-22
Hi,

If you are quite sure you don't want to settle the problem in your PC, then just reformat it and start over.

Just boot from the LiveCD, Try Ubuntu without any changes, and then use the Disk Utility to reformat your whole hard drive!

The link below also has a user who is unable to access his HDD.
[http://ubuntuforums.org/showthread.php?t=1650248](http://ubuntuforums.org/showthread.php?t=1650248)

* I know that this is not solving anything, but it does get rid of all your hassles! 
(Unless you have stuff in your PC you urgently need)

Good Luck :D

---

### Post by garvinrick4 on 2010-12-22
And when you go to 2.6.28-19 not in recovery it does what now?

---

### Post by charmedncursed on 2010-12-22
@theasprint: In order to boot the disk which device should be prioritised?
and I don't know how to use disk utility...
(removed everything from the destop so formatting will be fine

---

### Post by charmedncursed on 2010-12-22
> **garvinrick4 said:**
> And when you go to 2.6.28-19 not in recovery it does what now?
It goes to ubuntu startup which increases to 100%
after that it shows a number of checks with astericks....like
[[IMG]http://img692.imageshack.us/img692/5084/53776409.jpg[/IMG]]("http://img692.imageshack.us/i/53776409.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")

Again sorry for the inverted pic

After that everything goes and a black screen is all I get

---

### Post by theasprint on 2010-12-22
Hi,

Aha wise choice. There's no need to waste effort if you are sure that everything you need is with you.

The device to be prioritized is the CD drive of course. CD Drive first then the rest is up to you. 

Er, while approaching disk utility (which is under System>Administration I think, I'm not on ubuntu) then you can get to reformat your whole drive (there's an option for that).

Reformat your HDD to NTFS type first, just in case you want Windows 7.
You can also refer to the link I gave you earlier.

With your empty HDD, just go and install some OS.
Here is a guide on how to dual-boot Windows and Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

---

### Post by charmedncursed on 2010-12-22
> **theasprint said:**
> Hi,

Aha wise choice. There's no need to waste effort if you are sure that everything you need is with you.

The device to be prioritized is the CD drive of course. CD Drive first then the rest is up to you. 

Er, while approaching disk utility (which is under System>Administration I think, I'm not on ubuntu) then you can get to reformat your whole drive (there's an option for that).

Reformat your HDD to NTFS type first, just in case you want Windows 7.
You can also refer to the link I gave you earlier.

With your empty HDD, just go and install some OS.
Here is a guide on how to dual-boot Windows and Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

Sorry but I am not dual-user....Ubuntu is the only OS in the laptop

---

### Post by theasprint on 2010-12-22
Hi,

Then go ahead and install Ubuntu after you've reformatted it!

*Er, for quoting, to save space, just quote the important words then its enough. No need to quote the whole reply.

Enjoy your Ubuntu :D

---

### Post by charmedncursed on 2010-12-22
I decided to upgrade grub to grub2 as the installation said(if I undestood it correctly)
that leads me to lilo configuration and I got the following message:

it  seems to be your 1st lilo installation.it is absolutely necessary to run liloconfig(8 ) when you complete
and execute /sbin/lilo after this

lilo wont work if you don't do this


What should I give as command to accomplish this?

---

### Post by theasprint on 2010-12-22
Did the guide said that? I don't see it. 

Btw, I thought you wanted to reformat your HDD and start over?
I mean that there's no need bothering about updating or editing anything in your PC if you want to reformat. Because its gonna be cleaned off anyway.

About the grub2 upgrade and Lilo stuff, I'm not sure how to do it.
Will need to wait for someone to shed some light over this.

But still, you want to update your grub? Or it is really compulsory?
What I told you to do is to boot from LiveCD and format the whole HDD with the Disk Utility.

---

### Post by charmedncursed on 2010-12-22
Ok I am reinstalling ubuntu 8.10 and will upgrade it...(and wont interrupt it ever again):)

Thanks for your help and time

---

### Post by theasprint on 2010-12-23
Hi,

A better way is to just download the Ubuntu 10.10 / 10.04 .iso file.

This actually enables you to find your compatibility problems with 10.10/10.04 much faster.
It also reduces the chances of causing problems during upgrading from 8.10 to 10.10/10.04.

But its ok if you've done it.
Start a new thread if you have problems with 10.10/10.04

---

