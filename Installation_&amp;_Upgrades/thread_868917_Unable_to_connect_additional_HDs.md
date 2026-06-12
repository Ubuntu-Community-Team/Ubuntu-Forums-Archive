---
title: "Unable to connect additional HDs"
date: 2008-07-24
forum: Installation &amp; Upgrades
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

### Post by confused57 on 2008-07-24
With multiple hard drives, it's probably easier to set the Ubuntu drive as the first hard drive booted in bios.  While you only have 2 hard drives connected, boot the live cd & install grub's IPL to the Ubuntu drive's mbr:
```
sudo grub
find /boot/grub/stage1
```
if it still returns (hd1,0):
```
root (hd1,0)
setup (hd1)
quit
```

Then set your bios to boot first to the Ubuntu drive, you should get a grub boot menu, highlight the first Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.  This change is temporary, but it can be made permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
make sure to also change the line with groot to (hd0,0).

Then you can add an entry to boot Windows, similar to what's used in this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Set your Windows drive 2nd in the hard drive boot order.

If for some reason Windows doesn't boot with (hd1,0) after you reconnect all your drives, you could try:
```
title  Windows
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

or (hd3,0), changing the map lines accordingly.

---

### Post by sandman3838 on 2008-07-25
Got it working!  Ya!

Ok first I figure that possibly Ubuntu just didn't like relying on the HD boot order utility in the BIOS.  Originally my SATA wire connections from the HD to the Motherboard where:

SATA1  WINXP
SATA4  FILES
SATA6  (target HD 4 Ubuntu)
IDE1 S  FILES

So I physically moved the wires to the HD and Motherboard to:

SATA1  WINXP
SATA2  (target HD 4 Ubuntu)
SATA4  FILES
IDE1 S  FILES

Next I installed Ubuntu and there were no issues as before and I was able to reboot and go back into Ubuntu through the Grub menu!  However WINXP failed!

AS YOU SUGGESTED I DID THE FOLLOWINIG:

Code:
sudo grub
find /boot/grub/stage1
if it still returns (hd1,0):

Code:
root (hd1,0)
setup (hd1)
quit

Then set your bios to boot first to the Ubuntu drive, you should get a grub boot menu, highlight the first Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot. This change is temporary, but it can be made permanent in your menu.lst:

Code:
gksudo gedit /boot/grub/menu.lst

make sure to also change the line with groot to (hd0,0).

Then you can add an entry to boot Windows, similar to what's used in this thread:
[http://ubuntuforums.org/showthread.p...light=dualboot](http://ubuntuforums.org/showthread.p...light=dualboot)

Set your Windows drive 2nd in the hard drive boot order.

If for some reason Windows doesn't boot with (hd1,0) after you reconnect all your drives, you could try:

Code:
title  Windows
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

or (hd3,0), changing the map lines accordingly.

*** What I did was I added Three alternatives to the bottom of the menu.lst file.  I figured while I'm in there?  That way I wouldn't have to keep popping in and out changing it.  Later when I found the one that worked I just re-edited the menu.lst file and removed the TWO that failed.

FAILED
title  MS Windows XP Professional
root (hd0,0)
makeactive
map (hd0) (hd0)
map (hd0) (hd0)
chainloader +1

FAILED
title  Windows XP Professional
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

WORKED!  WE HAVE A WINNER!   YES IT WAS THE THIRD ONE!

title  Windows XP Pro
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


Thank you so much confused57 for your help!  You where great!

---

### Post by confused57 on 2008-07-25
Glad to help...good job on your part getting it working.

---

