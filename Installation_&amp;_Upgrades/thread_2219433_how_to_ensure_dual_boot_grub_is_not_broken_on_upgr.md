---
title: "how to ensure dual boot grub is not broken on upgrade to 14.04?"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by darrenrmoss on 2014-04-24
Hi!  I'm about to upgrade to 14.04. I have dual boot with windows 8.1. I can't use the standard upgrade tool because my internet connection is too unreliable and the tool crashes out every time the connection is lost - I keep getting errors and having to start again. So I'm using Transmission to torrent the ISO file. 

My question is, how do I upgrade from an ISO on my harddrive, making sure grub dual boot isn't damaged? Last time I upgraded I lost windows boot option and had to use boot repair to get it back. This was easy and worked well but I'd prefer to get it right first time!

I've hunted for information but most posts seem to be related to fixing grub after upgrade, rather than getting it right in the first place - but point me to the correct posts please if you know of any!

Step-by-step-for-blithering-idiot instructions, please :)

Thanks!

---

### Post by oldfred on 2014-04-24
Is this a BIOS/MBR install where you installed or upgraded Windows yourself or a UEFI/gpt install that was pre-installed?

If you have existing Linux partitions and what to reuse them, you should then use Something Else. There have been some issues with some auto installs and Windows 8, where the installer says overwrite Ubuntu (does not mention Windows) and then erases entire drive.
Best to make sure the fast boot or always on hibernation is off in Windows.

If you have not made a Windows backup best to do that. If your own install, back up your data. But a full image backup may still be better as reconfiguring Windows can be a hassle.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

How you install with BIOS or UEFI if using something else should be the same. You choose existing / (root) as new / and existing /home as new /home but DO NOT reformat.
If you do not have separate /home you need to back that up.
And best to make a list of installed applications so you can reinstall easily.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
But when doing a new install, I install to a new 25GB / partition, so I can still boot old install and find something I forgot.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by darrenrmoss on 2014-04-25
Thanks for taking the time for all that, Oldfred!  I'll have to spend some time checking your links out.
 In answer to your question, Windows 8 was already installed when I got the computer -it's UEFI. I added Ubuntu myself onto a new partition. I upgraded to windows 8.1 just using the standard windows automatic upgrade method and afterwards only windows booted - I fixed it using a live usb key. Later I upgraded ubuntu, which also broke grub, afterwards only ubuntu booted. I fixed that too using boot repair.  I'd prefer not to reinstall anything, really - what would be nice would be if the Ubuntu upgrade tool (and the windows one too!) just sorted all this out itself instead of blindly overwriting everything! I'll have a go, anyway. Thanks again for your help!

---

### Post by oldfred on 2014-04-25
As I understand it just about any maintenance or upgrade in Windows will auto reset it to be first in UEFI boot order. It does not know about other systems, nor want to.

But updating Ubuntu should not have caused grub issues. And sometimes a update loses the Windows entry in grub menu and a sudo update-grub fixes that.

---

