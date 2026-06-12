---
title: "Save &quot;nomodeset&quot; in GRUB ?? (14.04)"
date: 2014-05-26
forum: Installation &amp; Upgrades
---

### Post by Totolanio on 2014-05-26
Hello,

I tried to follow a guide (old) to save "nomodeset" in the GRUB menu instead of typing it each time (so I can use my old [GPU without any bugs]("http://ubuntuforums.org/showthread.php?t=2223134&p=13018980#post13018980")).

It didn't work at all.

I don't know if it has to do with the fact there is an older lubuntu (zorin lite 6.2) on it in first position and the Lubuntu 14.04 is in sixth position in this GRUb boot menu.
But I'd like to solve this problem, please !

I want to start with Lubuntu 14.04 in "nomodeset" EACH time !


Thank you if you can help.

---

### Post by oldfred on 2014-05-26
Usually nomodeset is a temporary solution until you install the correct proprietary driver. 
What video card/chip do you have?

Which system do you primarily boot? 
With BIOS you can only have one systems's grub boot loader in the MBR, and it will be the first in grub menu. All others then are last in menu.
You can reinstall grub from another install, just by booting into it and issuing this command.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

But grub remembers where to reinstall on major update, so you may want to turn off that update in second choice or it may become first again after an update.

      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Normally grub2's os-prober reads the grub.cfg from your other install. So if you want nomodeset permanently you have to modify that install first to include it, run sudo update-grub to it is in menu, then boot into other install and run sudo update-grub to read the new updated grub menu from second install. I have many installs and it gets too much to do, do I turn off os-prober and just add my own boot stanza to 40_custom.

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

If you really want nomodeset you need to edit /etc/default/grub and then run sudo update-grub. I think recovery mode already has nomodeset as default so you should only need to add after quiet splash.


 gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".

---

### Post by Totolanio on 2014-05-26
[quote="myself"]My pentium 4 with a Nvidia GeFORCE 4 MX 440 (and with 750MB ram) is  having graphical bugs as you might know (icons not showing, some things  really annoying for the eyes).

But I might have one solution :
I accidentally started Lubuntu 14.04 in recovery mode, and NO BUGS at  all, it would help all the people if that's the solution ! So is there a  command to trigger when starting the normal mode ? Or should I let her  use Lubuntu 14.04 in recovery mode all the time ? Are there  inconvenients or risks ?[/quote]

from [http://ubuntuforums.org/showthread.php?t=2223134&p=13018980#post13018980](http://ubuntuforums.org/showthread.php?t=2223134&p=13018980#post13018980)

So I checked the recovery mode settings in GRUB and put nomodeset on normal boot and it worked but didn't save it.

Actually the primary boot is on Zorin Lite 6.2 (which I must remove and replace by Lubuntu 14.04 entirely but with all those bugs I installed it on a tiny partition) and I have to select Lubuntu to start it. 
I'm going to install Lubuntu properly, just want to fix this graphical bug. Do not search about a driver nor anything, I already spent a lot of time, do not waste your. it's not compatible with Xorg >> 1.12


So I guess I'll go with "nomodeset" unless you say it's an horrible idea and **thank you for the instructions, Oldfred, really !**
By the way, I already tried some things you mentionned earlier but it didn't work, maybe that was because Zorin was the primary bootloader so how can I put lubuntu to be the default "normal mode" ? (without erasing zorin yet)

---

### Post by oldfred on 2014-05-26
Its posted above on how to reinstall grub from a working system. Just boot into Ubuntu from Zorin's grub and install Ubuntu's grub to MBR.

You have an older nVidia.

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
It looks like a variety of 440 series use the 96.xx legacy drivers.
 Repository shows 96.xx series driver.
nvidia-graphics-drivers-96-updates

---

