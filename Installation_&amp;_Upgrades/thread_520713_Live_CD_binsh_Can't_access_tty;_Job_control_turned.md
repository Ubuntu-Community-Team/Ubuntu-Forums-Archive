---
title: "Live CD /bin/sh: Can't access tty; Job control turned off"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by vnkatesh on 2007-08-08
my frnd's comp shows the error while using the live cd
/bin/sh: Can't access tty; Job control turned off

i tried to do a 'modprobe piix'
and then continued.. but still the error occured..

he has a 64 bit comp.amd turion laptop.
i used both 32-bit and 64-bit edition, still the same error occured...

any help will be greatly appreciated.

---

### Post by nilfisk1 on 2007-08-08
I had the same problem yesterday, during my first ever linux install. Do not ask me why, but once you're in the menu of the live cd insert a floppy drive, and then go ahead and hit install. It works, dunno why but it does.

Hope this helped,

Nils

---

### Post by vnkatesh on 2007-08-08
its a laptop, no floppy drive...

---

### Post by Pumalite on 2007-08-08
Here is a mishmash of fixes. See if one applies to you and try it:

when I boot, the screen shows



f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); jStarting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.
ust a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by US41 on 2007-08-08
I received this error trying to run from the liveCD as well. My hardware is not legacy. I have an Abit IP35-e MB and an Intel 6750 core duo 2 chip with 2 gigs of DDR2 800 ram and a sata II HD with 300mb with an 8500GT video card. 

This is more proof to me that linux is not ready for the non-geek desktop.

---

### Post by wilf on 2007-08-09
Had same problem. Tried downloading _6_ times. Giving up. Unreliable. No-one seems to be able or willing to help newbies to overcome this snag.

---

### Post by wilf on 2007-08-09
Just had another try.
Inserted a Windows Me boot floppy and the Ubuntu cd into my computer at the same time and re-booted.
Installation success!!!

_For anyones info._
The 80gb hard drive  was completely blank

_**Why must you have to use a windows floppy to install a linux system?????**_

---

### Post by nilfisk1 on 2007-08-09
It doesn't have to be a windows floppy, any floppy will do.

---

### Post by splintercellguy on 2007-08-09
Did no one try sticking noapic option on boot? And the wonderful flame like 3 or 4 posts back is absolutely unproductive, and he/she probably won't be coming back.

---

### Post by US41 on 2007-12-30
Wrong. I came back. I tried 7.10.

---

### Post by Pumalite on 2007-12-30
Here is a guide and a collection of boot parameters to try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by chopsuwe on 2007-12-30
> **US41 said:**
> Wrong. I came back. I tried 7.10. 
I will be back again. I've been using Linux for 15 years now trying various distros. But I don't believe Ubuntu or any other distro will be an alternative that is useable for current mainstream users until it can be installed reliably. 

I think that is a very productive observation to make about a a product that the entire world is hoping will become user-friendly and reliable enough to supplant the current copyright-hungry monopoly. We are all pulling for you, but you have to be willing to take honest feedback and fix the problems.

This problem is now 4 months old. That's a long time to have people failing during installation. Editing an install routine is not an acceptable workaround in today's industry. It should simply install auto-magically on its own without user intervention.

Well said. I would love to switch to Linux but can't even get it to install.

Can we please have a  solution to this problem?

---

### Post by Pumalite on 2007-12-30
All types of hardware cannot be satisfied in 7.10. That's why the boot parameters.

---

### Post by nitemann on 2007-12-31
Good Evening All ,
Having issues with the fatal Cant access tty: job control tuerned off during live LD Boot:


I have manage to get to the point where I can key in ACPI feature and turned it off but I can't set the  break=top in the additional parms. The default parm in F6 is
:casper initrd=/casper/initrd.gz quiet splash --|  to which I appended livr acpi=no noacpi aclapi.. But I cant resovle the break = top on where to add it , when I do it locks up the machine. I am  currently  runing KNOPPIX-Debain 3.3 on this is a very old machine and it runs well but would like to move to UBUNTU 7.10

 the machine in question is a 1996 Dell 2500 power edge Server 2500 PII 350 MB with DUAL CPU MB (1 processor right now) running 192 megs RAM and a very small onboard agp (2 megs).. I know this may not be enough machine for UBUNTU, but it runs the KNOPPIX just fine.. I really like ubuntu, and would like to run it on this machine. PS.. I hate  MS window!!!!! I have ti run Xp on same Machine for some things I regretably must have for work. This is a RAIDS  Server using 5 SLotted SCSI Drives (only one in use)..
I have two of these servers and would really like to see them run UBUNTU with bare bone GUI Destop. I have been thru the forums and saw some refernces to FIESTY.. But I read dannyboy79 instructions and  machine hang up if I place the break=top in front of special parms.  Any help is most appricaited and welcome.. I dont want to give up on this, These Servers are fast for old PII , with Dual CPU's... They are just good old wrok horses, comes with  PYTHON 4 GIG Tape Backups..



                                               Thanks and Happy New Year!!!!

---

### Post by Partyboi2 on 2008-01-01
> **nitemann said:**
> Good Evening All ,
Having issues with the fatal Cant access tty: job control tuerned off during live LD Boot:


I have manage to get to the point where I can key in ACPI feature and turned it off but I can't set the  break=top in the additional parms. The default parm in F6 is
:casper initrd=/casper/initrd.gz quiet splash --|  to which I appended livr acpi=no noacpi aclapi.. But I cant resovle the break = top on where to add it , when I do it locks up the machine. I am  currently  runing KNOPPIX-Debain 3.3 on this is a very old machine and it runs well but would like to move to UBUNTU 7.10

 the machine in question is a 1996 Dell 2500 power edge Server 2500 PII 350 MB with DUAL CPU MB (1 processor right now) running 192 megs RAM and a very small onboard agp (2 megs).. I know this may not be enough machine for UBUNTU, but it runs the KNOPPIX just fine.. I really like ubuntu, and would like to run it on this machine. PS.. I hate  MS window!!!!! I have ti run Xp on same Machine for some things I regretably must have for work. This is a RAIDS  Server using 5 SLotted SCSI Drives (only one in use)..
I have two of these servers and would really like to see them run UBUNTU with bare bone GUI Destop. I have been thru the forums and saw some refernces to FIESTY.. But I read dannyboy79 instructions and  machine hang up if I place the break=top in front of special parms.  Any help is most appricaited and welcome.. I dont want to give up on this, These Servers are fast for old PII , with Dual CPU's... They are just good old wrok horses, comes with  PYTHON 4 GIG Tape Backups..



                                               Thanks and Happy New Year!!!!
have you tried the alternate cd? 
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by Pumalite on 2008-01-01
Better this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
Lighter in memory usage. Remember you have to feed those integrated graphics.

---

### Post by ceton on 2008-01-01
Regarding [COLOR="Red"]***/bin/sh: Can’t access tty; job control turned off***[/COLOR]

Apparently, there are a bizillion reasons that this error occurs, but in my case, it was because the Ubuntu Live CD couldn't recognize some of the hardware on the machine I was installing to.  (I was able to install it successfully on other machines--it was just one troublesome machine).

Here is what worked for me:
[LIST=1]
[*]When the bootup screen appears, [COLOR="Blue"]***press F6***[/COLOR]
[*][COLOR="blue"]**Type**[/COLOR] the following:  [COLOR="Blue"]***acpi=off irqpoll***[/COLOR]
[*][COLOR="blue"]**Press**[/COLOR] the [COLOR="blue"]***Enter***[/COLOR] key.
[*]View the Live CD and install Ubuntu.
[/LIST]

You have to make sure that this problem is resolved when Ubuntu boots, too.  To do that:

[LIST=1]
[*]Boot your computer so that GRUB is displayed.
[*][COLOR="blue"]**Press**[/COLOR] the "[COLOR="Blue"]***e***[/COLOR]" key to go into edit mode.
[*][COLOR="blue"]**Press**[/COLOR] "[COLOR="Blue"]***o***[/COLOR]" to add a new line to the script.
[*][COLOR="blue"]**Type**[/COLOR] the following:  [COLOR="Blue"]***acpi=off irqpoll***[/COLOR]
[*][COLOR="blue"]**Press**[/COLOR] the [COLOR="blue"]***Escape***[/COLOR] key.
[/LIST]

In the event that acpi=off doesn't work try replacing the entry above with one of the following:
[LIST]
[*]acpi=force irqpoll
[*]nacpitimer irqpoll
[/LIST]

You may have to revisit the second set of steps when you upgrade ubuntu.

I hope this helps.

---

