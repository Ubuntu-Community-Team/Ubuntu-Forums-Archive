---
title: "Help Install 2 SATA HD"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by sandman3838 on 2008-07-21
Hello:confused:
Is there anyone out there who can shed some light on getting Ubuntu 804 installed new on a system that has Winxp Pro already installed.  I would like to get a dual boot going!  However I must point out that these “is not” two operating systems sharing the same Hard Drive that has been partitioned or IDE drives!  I’m trying to get Ubuntu running on my other SATA II drive?
So far I have already checked out these sites:

My system is an ABIT AN9-32X (up 2 date) BIOS setup before installing Ubuntu looked like this:
1	CH3	M	WDC WD2500KS-00MJB0	SATAII	(winxp)
2	CH6	M	WDC WD2500KS-00MJB0	SATAII	(files)
3	CH8	M	WDC WD1600JS-22NCB1	SATAII	(target HD 4 Ubuntu)
4	CH1	S	MAXTOR 6X200PO		IDE	(files)

Now for safety reasons I unplugged both:
2	CH6	M	WDC WD2500KS-00MJB0	SATAII	(files)
4	CH1	S	MAXTOR 6X200PO		IDE	(files)

With just these two HD Winxp still boots up!  Now we install Ubuntu!

1	CH3	M	WDC WD2500KS-00MJB0	SATAII	(winxp)
2	CH8	M	WDC WD1600JS-22NCB1	SATAII	(target HD 4 Ubuntu)

Next I installed Ubuntu.
1.  Reboot with the Ubuntu CD in the CD Drive.
2.  It Boots and I selected Install Ubuntu.
3.  I install it to WDC WD1600JS-22NCB1 giving it the whole drive.
4.  Ubuntu finishes installing and asks for a restart and it does.
5.  However Ubuntu is no where?  I just reboot right back into Winxp.
6.  As suggested from this site and others I switch the Boot Priority to:

1	CH8	M	WDC WD1600JS-22NCB1	SATAII	(target HD 4 Ubuntu)
2	CH3	M	WDC WD2500KS-00MJB0	SATAII	(winxp)

7. Still nothing however now with my boot up I get “Operating System not found” naturally because I switched the HD order.

After switching the HD order back to the original setting and reentering Winxp I used WD HD utility to wipe out the WDC WD1600JS-22NCB1 to start fresh.  

Now someplace I read an install guide where they “didn’t” reboot when asked and instead selected the INSTALL ICON that popped up after they canceled the restart.  I did this.  I was on the Ubuntu desktop on the top left corner.  It just seemed to be installing as before and I did select the full HD for WDC WD1600JS-22NCB1?  However this time around it did ask what Profiles I would like to migrate to Ubuntu.  I thought great, success!  Wrong!  On the Boot up I received, “GRUB 1.5  error 17”.  Grub menu can’t find the Ubuntu location obviously?  

The fix was to return to the original HD setup and boot to the Winxp CD and use FIXMBR in the recovery option.

Ladies and gentleman I have Ubuntu on my older system and I love it and I have used Dual Booting before with other OS’s.  This shouldn’t be this hard or weird?  What am I missing here?  
Oh there was mentioned a program called GUTSY has any one had any luck with it?  
:confused::confused:

---

### Post by logos34 on 2008-07-21
Set the ubuntu drive back to first place in the Bios hard disk boot order.

Follow [this guide]("http://ubuntuforums.org/showthread.php?t=224351") to reinstall grub to the mbr of the ubuntu disk.  Except for 'setup'  use whatever the root is, e.g.:

if it says root is

(hd**0**,?)

then do

setup (hd**0**)

If it shows root as (hd**1**,?), use setup (hd**1**).  This will ensure it goes on the ubuntu disk, pointing to the correct bios location of root.  If the latter, you will probably get an error when you actually try to boot the ubuntu kernel--simply press 'e' to edit root line to (hd**0**,?).  (Because the menu.lst will probably be wrong, since the OS installer appears to not be seeing the drives in the correct order)

---

### Post by sandman3838 on 2008-07-24
Hello

I did put out another issue on this out here in this forum.  It didn't work “at all” and I needed some time to play around with it again.  Well I did and I now have the Grub menu up and running and I'm able to access Winxp on it's HD as well.  However there is a NEW problem!

My system is an ABIT AN9-32X (up 2 date) BIOS setup before installing Ubuntu looked like this:
1 SATA1 WDC WD2500KS-00MJB0 (winxp)
2 SATA4 WDC WD1600JS-22NCB1 (target HD 4 Ubuntu)
3 SATS6 WDC WD2500KS-00MJB0 SATAII (files)
4 IDE1 S  MAXTOR 6X200PO IDE (files) (slave to the CD Drive)
5 BOOTABLE ADDIN CARD

Now for safety reasons I unplugged both:
3 SATS6 WDC WD2500KS-00MJB0 SATAII (files)
4 IDE1 S  MAXTOR 6X200PO IDE (files) (slave to the CD Drive)

With just these two HD I installed Ubuntu!
1 SATA1 WDC WD2500KS-00MJB0 (winxp)
2 SATA4 WDC WD1600JS-22NCB1 (target HD 4 Ubuntu)

The Ubuntu install went like this:
1. Reboot with the Ubuntu CD in the CD Drive.
2. It Boots and I selected Install Ubuntu.
3. I install it to the second SATA drive SDB WDC WD1600JS-22NCB1 giving it the whole drive and leaving the Winxp Hd alone.
4. Ubuntu finishes installing and asks for a restart and it does.

On the reboot the GRUB menu was there and I'm now able to go into both Winxp and Ubuntu both are working fine!  I even went and took a look at the at GRUB.  By opening the Terminal I - 
sudo grub
find /boot/grub/stage1
This showed the return location to be (HD1,0)

NOW THE PROBLEM, AFTER I SHUT DOWN AND REATTACH THOSE OTHER TWO HD'S!
OOPS!  SO CLOSE BUT NO CIGAR!

Keep in mind that the HD order in the bios for the two OS's is still the same.
1 SATA1 WDC WD2500KS-00MJB0 (winxp)
2 SATA4 WDC WD1600JS-22NCB1 (target HD 4 Ubuntu)
3 SATS6 WDC WD2500KS-00MJB0 SATAII (files)
4 IDE1 S  MAXTOR 6X200PO IDE (files) (slave to the CD Drive)
5 BOOTABLE ADDIN CARD

On the reboot with all of these HD attached I get :
GRUB loading Stage1.5
Grub loading, please wait....
ERROR17

Ok then, from what I have read some folks have fixed this by moving the boot order of  the Ubuntu HD.
I did this:

1 SATA4 WDC WD1600JS-22NCB1 (target HD 4 Ubuntu)
2 SATA1 WDC WD2500KS-00MJB0 (winxp)
3 SATS6 WDC WD2500KS-00MJB0 SATAII (files)
4 IDE1 S  MAXTOR 6X200PO IDE (files) (slave to the CD Drive)
5 BOOTABLE ADDIN CARD

Now on the reboot I get:
ERROR LOADING OS
(There is no mention of GRUB)

Also to check if my problem was one HD or the other I have reboot adding just one of the additional HD at a time.  It still came back with ERROR17!

I have now but the HD order back and I'm running with just the Winxp HD and the Ubuntu HD.
I need to get those other two HD up and running without being unable to get into Winxp.  I still have too much information on there to loose it.  

Is there a way to edit the Grub menu and shutdown and attach all the Hds or perhaps attach all the Hds and use the Ubuntu Cd to edit Grub much like using the Recovery Option from the Winxp CD?  Whichever is the easiest please!  Remember I'm the new guy!

One last note, from the Terminal I did display the Grub.  It looked as if the last part was the meat of the file.  I hope this helps?

Thank you all for your time and help!

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eefecab2-cc0d-4632-8b67-16c25d066a3b ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=eefecab2-cc0d-4632-8b67-16c25d066a3b ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2008-07-24
Sounds like what is happening its that grub is scanning the IDE channels first, before the ubuntu sata disk--when you mix sata and pata drives it throws grub for a loop. 

More about Dual boot on dual drives + sata/pata issues:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

So reconnect the other drives, make sure the Bios hdd boot priority is sda1 (windows) first, ubuntu second.  Reinstall grub to the mbr of sda (see link in my sig).  Hopefully when you reboot the grub menu screen will come up, but you probably won't be able to boot the ubuntu entry.  Press 'e' to edit the ubuntu selection, 'e' again on the 'root' line and try (hd2,0) or (hd3,0). If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

change the root line to match (don;t forget 'groot' line too)

---

