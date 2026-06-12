---
title: "Ubuntu Install on Imac ppc g5 Help"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by frank18 on 2013-10-14
Hi Guys: I have a PPC Imac g5

Hard Drive Capacity: 500 GB
iMac  
Processor Type: 	
PowerPC G5
Screen Size:20"
Processor Speed: 2.00 GHz
1gbMem Ram

And i have Installed Debian Wheezy 7. and it's running farely good,exept it runs slow.
but before debian wheezy  i also have tried to install  Ubuntu 12.04 PPC,  i installed  it ok till it gets to the Ubuntu Logo and hungs there and goes  nowhere,
after that i installed ubuntu 12.10 and it goes as far as the log in  black screen, where it asks name and password, and from there i don't know how to get the Desktop environment.
the same hapened with  Ubuntu 13.04,all the installation goes smoothly but could never get the desktop of any kind. Any help on getting the commands for the desktop environment of any flavour would be apreciated,
i'd like to try ubuntu cause i don't like Debian Wheezy much . But at least Debian Wheezy installs the Desktop environment right of the box, i wish that Ubuntu would do the same but it doesn't or i don't know how. any help would be apreciated.

---

### Post by Old_Grey_Wolf on 2013-10-14
You might take a look at [Linux MintPPC]("http://www.mintppc.org/about").

---

### Post by tigheron on 2013-11-09
I am not sure what exact iMac G5 revision you have, but I have had some success in installing lubuntu 13.04 on a iMac G5 revC (the one with the iSight camera).

I just downloaded the [lubuntu 13.04 ppc iso]("http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-powerpc.iso") and copied it on a usb stick using dd.
To boot from it just enter OpenFirmware (by pressing alt+command+o+f after powering up the computer) and type some the magic command
>  boot usb0/disk@2:,\\yaboot
This worked for me when the usb stick was inserted in the port just next to the headphone one. If you are not familiar with this process, you can find a lot of tutorials around (for example[ this one]("http://www.debian.org/releases/sarge/powerpc/ch05s01.html.en")).

I found these kernel parameters to be necessary to get openGL working on the Radeon X600
> video=radeonfb:off radeon.modeset=1 video=1440x900-32
followed by a
> sudo X -configure
which generates a xorg.conf file to be copied in /usr/share/X11/xorg.conf.d/01-radeon.conf

Another word of warning is about random kernel locks on boot. I found that [disabling apparmor]("https://help.ubuntu.com/community/AppArmor") solved all my issues.

As far as I can tell, all the hardware is supported. I got openGL working on the Radeon X600, the wifi driver were installed automagically after invoking > sudo apt-get install firmware-b43-installer, and the iSight is working too, although I had to download and compile the [isight firmware tools]("https://launchpad.net/isight-firmware-tools/main/1.6").

Sound does not work out of the box, but you have to manually insert the correct modules, which iny case are > snd-aoa-fabric-layout
 snd-aoa-i2sbus

Please be warned that there are [some openGL issues with lubuntu 13.10]("http://ubuntuforums.org/showthread.php?t=2183771") on the revC iMac G5 (or, at least, I had some issues and reverted to 13.04).

Finally, do not expect a stellar performance. I was able to write this post using firefox on the machine, and - well - it was a good exercise in patience :D

---

