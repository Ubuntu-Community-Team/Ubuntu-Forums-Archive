---
title: "Grub2 Help"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2011-02-19
Complete newby questions on GRUB2, since i am not a linux guy. 
 
I have been trying to get familiar with Grub2 since it looks that i may need it to boot from the network with PXE. I figured the best way for me to familiarize myself was to install Ubuntu  in vmware  ands  start configuring a floppy disk and get to know grub2.   Unbuntu 10.1O installs grub 1.98. 
 
every information i have found on the net is really quit confusing since nothing really works on creating floopy Grub2 disk.  from using grub-install to grub-mkrescue.  Nothing i have tried works for me. 
 
 I have spent few days looking and i think i have covered many of the tutotials that are out there.  One tutorial ([http://www.gossamer-threads.com/lists/gentoo/user/224979](http://www.gossamer-threads.com/lists/gentoo/user/224979)) says to skip version 1.98 and go to 1.99. I donwloaed the lasted version and tried to upgrade but received  "./autogen.sh: line 5: autogen: command not found" error.   Since i have no experience in compiling  this is a problem .  if anyone can point me in the righ direction, either with this error or a tutorial that works for ubuntu it would be greatful.  thanks in advance.

---

### Post by oldfred on 2011-02-20
Welcome to the forums.

Herman has some info on floppy.
Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

But most now use USB flash drives to boot:

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

