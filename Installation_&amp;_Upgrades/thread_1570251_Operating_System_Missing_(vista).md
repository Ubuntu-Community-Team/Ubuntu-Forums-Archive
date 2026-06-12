---
title: "Operating System Missing (vista)"
date: 2010-09-07
forum: Installation &amp; Upgrades
---

### Post by okanagansage on 2010-09-07
Hey, I had created a LiveUsb from a LiveCd using Startup Disk Creator and then later formatted the usb drive and installed Ubuntu 10.04 onto it again. On the last install, instead of using the Startup Disk Creator, I installed using the desktop icon (from within a LiveCd session) and found the usb during the manual partition.

Now when I try to load straight into Vista (without the usb drive plugged in), I get a black screen with two lines of text:
error: no such device:   ...(followed by about thirty letters and numbers)
grub rescue> _

When I load straight into vista (with the usb drive plugged in), I get a normal grub menu. This is like you get with a normal dual-boot. On the last install, I'm guessing I should have left out the grub and then I wouldn't have to have the usb plugged in all the time. Assuming that I should just remove grub, my question is: how do I do that? 

When I load into Ubuntu by pressing 'escape' to access my boot menu (BIOS?), after choosing to boot the usb and just before the grub menu appears there is a message saying that an operating system is missing. I don't know if I should worry about that right now. I'm thinking that will be resolved if I remove grub. 

I'm using a hp pavillion media center pc (model: m8532f)
     Intel Core 2 Quad (Q6700)

Please let me know if you need any more information and where/how I can find that info (if it involves config. files, etc).

Also please let me know if I'm way off base with my evaluation of what the problem is and how I should deal with it. 

Thanks.

---

### Post by garvinrick4 on 2010-09-07
Do you just have Vista on the internal hard drive?
You can boot into ubuntu on pen drive?
Gives you option to boot into Vista on pen drive?
You cannot boot into Vista when no USB pen drive installed?

Is that all correct?

---

### Post by okanagansage on 2010-09-07
That's right.

---

### Post by okanagansage on 2010-09-07
For some reason this thread is not showing as read (bold lettering) but I have read and responded to my first replier. Any suggestions in regards to my original post?

---

### Post by confused57 on 2010-09-07
Here's one way to repair your system:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

An alternate method:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you follow the 2nd method & don't have a Vista installation DVD, you can download a Vista Recovery cd:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by garvinrick4 on 2010-09-07
Do you have your Vista Recovery disk or install disk.
                    from:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7  installation disk, you can get the same effect with a Vista recovery  disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").
When you get to the Regional settings, select your Location/Keyboard  setting then click next. On the next page you must click on "Repair your  computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the following : One at a time:

bootrec.exe /fixboot

bootrec.exe /fixmbr

Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

If you do not have a Vista disk then you have to have a Ubuntu disk and their is another way to do this.

---

### Post by okanagansage on 2010-09-07
Thanks for the replies! I have previously downloaded a 'vista recovery' iso because my computer didn't come with an installation disk. 

I'll give that a try.  Thanks again.

---

