---
title: "Missing Operating System message off of USB install"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by zmoney2 on 2013-08-30
I'm having a problem that is driving me insane.
I am running Windows XP and am trying to make a bootable live USB drive.  Every time I plug in the USB and in my bios have my laptop boot off of it I'm getting "Missing Operating System".  I'm POSITIVE I'm booting off of the USB in the bios.  Here is what I have done and what I have tried.
[LIST]
[*]I've downloaded and used unetbootin to create the bootable live USB drive.
[*]In unetbootin I've tried using the distribution method and have tried using the ISO image I have downloaded.
[*]I've tried using Ubuntu 13.04 and Mint 15 (again either from the distribution method or downloading the ISO image myself, 32bit versions)
[*]When using Mint 15 I've also verified the ISO image I've downloaded with the md5sum application (the MD5 code matched)
[*]I've verified that the syslinux.cfg and ldlinux.sys files were indeed created on the USB
[*]I've reformatted the USB (although it was FAT32 I reformatted it to FAT32 again just in case)... I'm using XP so I don't know how to check if LBA is on though.
[*]I've run the executable on the USB drive and selected to run the demo and it says I need to reboot off of the USB... Again when I try that I get "Missing Operating System"
[/LIST]
Please remember that unfortunately I'm using XP so linux type of line command solutions aren't available to me.
I'm convinced the iso image is valid and the files created by unetbootin look correct as well... so what is causing this "Missing Operating System"?
Someone please help... What am I missing here.  Why isn't this bootable live USB drive booting???

---

### Post by oldfred on 2013-08-30
That is a BIOS error. 
Some BIOS just check for boot flag, which should be on partition on USB flash drive after you installed. Others do check MBR to see if it has boot code.

Also some installers work with some systems and not others. Usually unetbootin is the preferred choice.
       Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Also some flash drives just have issues.
      
 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

Also how old is system? Are you using 64 bit and it needs 32 bit or even so old that PAE does not work?
      
 PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)


 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by zmoney2 on 2013-08-30
OldFred,
Thanks for the quick reply... I was thinking it was either the USB I was using or unetbootin as those were the only two things that were constant (I was even trying to boot on different pc's).
I was using a Kingston 8Gig.
I'm trying a mystery USB (got at a trade show)... Currently unetbootin is creating the live boot.  
If it doesn't work still I'll try pendrivelinux...
I'll let you know how it goes.

---

### Post by oldfred on 2013-08-30
I have had good luck with older Kingston and MicroCenter's house or OEM brand. 

Microcenter has a store not too far away and every time I am there it is - oh the price is lower or now the USB3 are only a little more than USB2 and cheaper than last time's USB2.

---

### Post by zmoney2 on 2013-08-31
I cannot believe it was the fact that I was using the Kingston 8G USB... Grrrrrrrr...
I downloaded the full 32bit ISO and used unetbootin to create the ubuntu linux OS I'm typing this up on right now. That 1G trade show USB that was just collecting dust in my laptop bag is now going to get alot of exercise. This old laptop that was running XP and was pretty much past it's prime is screaming fast now with linux.  I have an old desktop and another old laptop back home which are going to be getting this install as well.
Thanks again OldFred... it might seem like common sense now looking back on it, but your direction of trying a different USB saved the day and obviously I wasn't thinking of it since I didn't try it.  Maybe you should play the next Batman and not Ben Affleck since you truly saved the day.:p

---

### Post by oldfred on 2013-08-31
Glad you got it working. 
Sometimes it is something simple but until you figure it out it can be very frustrating.

---

