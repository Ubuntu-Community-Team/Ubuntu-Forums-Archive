---
title: "After Upgrade its failed to bootup"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by mayi on 2009-11-17
Hi,

I upgraded my Ubuntu 8.10 version to 9.10 version through upgrade.
It asked for restart and stucked there for 1 hr. Keyboard and Mouse are not working so  I did hard reset to my system. When I restarted it, it failed during boot up. I am using windows also. It's not going to choose that option. It's failed at BOOTUP only. I had some sensitive data on that which I don't want to loose.
Please help me on how to recover that.

Thanks in Adv
Mayi

---

### Post by mayi on 2009-11-17
Please Help !

How do I get back to my previous bootup option which has windows XP.

The message which its showing was :-

[B][I]****** Warning: System BOOT Fail ******
Your system last BOOT fail or POST interrupted
Please enter setup to load default and reboot again
[/I][/B]

Please Please help me

---

### Post by raymondh on 2009-11-17
Mayi,

Do you have a/any liveCD available (probably the old 8.10)?  If yes, boot into it and go live session (aka TRY UBUNTU WITHOUT ANY CHANGES).  Once in live session, go to PLACES (top left of the desktop) and access your "sensitive" files from there.  Copy/paste/drag them to a thumb drive.

About your boot problem ... did you/have you entered SET-UP and loaded the defaults as mentioned by the error message?


Regards,

---

### Post by mayi on 2009-11-17
Thanks Raymond for the inputs.

To my badluck, I lost the live CD of Ubuntu and also the windows XP setup disk too. 

I entered in to the setup, but I did loading the defaults but that doesn't worked. 
And also I had both the OS on the same Hard disk only :(

I am having Important data on windows xp :( how to recover that!!
And also I installed Ubuntu 8.10 through Windows


Please help on how to resolve this. 


Thanks
Mayi

---

### Post by raymondh on 2009-11-18
> **mayi said:**
> 

I am having Important data on windows xp :( how to recover that!!
And also I installed Ubuntu 8.10 through Windows


Please help on how to resolve this. 


Thanks
Mayi


Mayi,

I know little about 9.10's GRUB2 to be able to identify boot problems .... 'specially involving a wubi-install (ubuntu-inside-windows) which is what I presume  you have had since 8.10.  As a side note, 8.10 - 9.04 had GRUB legacy whilst 9.10 uses GRUB2 which is a "whole new set-up".  Also, a quick google search shows challenges with karmic vis-a-vis WUBI.

This may be limiting but perhaps you could ask a friend/borrow a computer to:

1.  Download and burn a liveCD.  I suggest (at this stage) a 9.04 Jaunty iso.  As mentioned, you can use that to access your files and save them elsewhere.

*   You can use the same liveCD to install ubuntu in its' own partition.  That will likewise install GRUB legacy which will overwrite the existing MBR .... in hopes of giving you access to XP (it should).  Once in XP,  you could then remove the wubi-ubuntu through the add/remove function of windows.  Note, should you do this, you also have to manually edit (in windows) the boot.ini file to remove the wubi-related line (ONLY THE WUBI-RELATED LINE).  You can do this later once you have recovered your files.

2.  In my signature is Hiren's CD which you can also download and burn.  Use that to access boot applications and access a command prompt.  Once in command prompt, you can 'fixmbr' (no quotes) to fix the boot-loading process of windows.

3.  This is [supergrubdisk]("http://www.supergrubdisk.org/") which you can also download and use to give you access to your windows install.

4.  You can bring your computer to a repair shop to either have them fix the bootloader (FixMbr and FixBoot) or, recover your files or, both.

I'm sorry this may be limiting.  Wait around, someone may be able to provide more/better support than what I can think of.  You can also join and access launchpad (where there are more dev's than the forum) and either file a bug report or search for a similar case with solutions.

Regards,

---

