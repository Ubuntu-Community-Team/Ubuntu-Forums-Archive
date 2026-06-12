---
title: "Win7 won't boot after Ubuntu Install"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by njwest on 2010-05-20
I recently installed Ubuntu on my netbook.  I partitioned the drive in Windows with Easeus Partition Manager.  I created a simple partition, ntfs (I know this isn't the correct format for Ubuntu, but I knew Ubuntu would reformat the partition) and rebooted the computer, checking everything was working.  It was.  

So I created an installer for Ubuntu using unetbootin, as it has no CD drive.  So I installed Ubuntu and all was going perfectly, I checked and all my data was on the Windows partition, untouched.  However, when I tried to boot into Windows 7, I got to the splash-screen, then it rebooted.  It briefly flashed a BSOD, but it disappeared far to quickly to read.  I tried videoing it, but my camera is not good enough quality to read what it said.  After that, when I tried to boot into it, I was offered the choice of startup repair or booting normally.  The same thing happens when I try to boot again, and when I go onto startup repair, I get the error: "The boot selection failed because a required device is inaccessible."

The same things happens when I try to boot into Windows Vista partition (I don't have Vista, but I think this is the Recovery partition).  I have checked the grub, and it seems to be correct, but I will post it below.  I am running an HP Pavilion dm1 1020ea which came with Windows 7 Home Premium x86 preinstalled.  I don't have a recovery CD or a copy of Windows with which to reinstall Windows.  

Any help would be greatly appreciated.  I am not a total beginner, but I am equally no veteran of Ubuntu.  
[URL="http://pastie.org/969568"]
/boot/grub/grub.cfg[/URL][FONT=Courier New]

  [/FONT]Thanks in advance.

---

### Post by oldfred on 2010-05-20
If you are getting something from windows, it sounds like windows is starting ok but has problems.

You can post this:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

I am not sure we will be able to see anything if windows at least gives you a repair choice.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I do not know how to put the windows repair CDs on USB. But have this link.
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)

---

