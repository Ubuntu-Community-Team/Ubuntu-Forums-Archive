---
title: "Windows 7 dual boot won't boot!"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Selgar on 2010-10-28
Hi Everyone
 
[FONT=Nimbus Roman No9 L]I am trying to run a dual boot system with Windows 7 and an Ubuntu 9.10 installation from a live CD. I am running this on a Dell Inspiron M5030. Both operating systems have installed fine however whenever I run Windows the computer subsequently fails to run Grub upon rebooting and gives the following error message:
 
Grub loading
the symbol 'ob_bioslgrub?+E?U? Not found
Aborted press any key to exit
 
The unrecognised symbols are different each time. I have also had (' ') and ('ee*??S ')[/FONT] and ('un')[FONT=Nimbus Roman No9 L].[/FONT]
[FONT=Nimbus Roman No9 L] 
I cured this initially by reinstalling Ubuntu but after looking at the support documentation have now found that I can cure it temporarily by simply reinstalling Grub using the command:
 
sudo grub-setup -d /media/dd5d6cd6-cb80-40e0-baf3-13ae1ebe17a4/boot/grub -m /media/dd5d6cd6-cb80-40e0-baf3-13ae1ebe17a4/boot/grub/device.map /dev/sda
 
I can then run Ubuntu fine, however upon running Windows again the problem reoccurs and Grub will not [/FONT]run[FONT=Nimbus Roman No9 L]. Please help me to fix this but please also go as easy as you can on the more technical stuff I am anything but a high-level user - this is my first time using a Linux operating system.
 
Many thanks
selgar
[/FONT]

---

### Post by oldfred on 2010-10-29
Some win7 software writes into the MBR.

If you have 2 drives an advantage of booting grub on the other drive.
Grub team looking for info:
[http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html](http://www.chiark.greenend.org.uk/ucgi/~cjwatson/blosxom/debian/2010-08-28-windows-applications-making-grub2-unbootable.html)
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by Selgar on 2010-10-31
Thanks for your assistance Oldfred - having read the contents of those files I've decided to start by deleting the Dell backup software as this seems to be the simplest and most likely cause of my problems, (apart from Windows itself I've only run Internet Explorer which does not seem to cause this problem).
 
Before I do this I'll wait until I get physical back-up discs sent from Dell - just in case the unexpected happens.
 
Once I've tested this I'll report back to the thread if it help. Thanks again!

---

### Post by oldfred on 2010-10-31
Not sure what partitions Dell has, but most vendors have a Utilities partition which I would just backup. They usually now do not give reinstall CD/DVD but have a partition to create a new install. It is not a true install but just an image of the drive as shipped. I would make the DVD to have, but would never ever use it as I would not want to go back to the original configuration.

And to do repairs of windows:
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I would also have a liveCD or two, Ubuntu, system rescue, Parted Magic etc. I have them all on a grub2 bootable USB flash drive just in case.

---

### Post by ratman1 on 2010-10-31
Try to find a windows 7/vista recovery disk on the internet. Google windows 7 recovery disk. Then when you find one, burn it to a DVD and boot from it. Select your language etc. Select repair computer. Select the partition to repair (the one with windows on it). Select the command prompt option. In cp, type 

'bootrec.exe /fixmbr' Without quotes.

Without the quotes. This command will allow windows to boot but ubuntu will be gone from the boot options. You will just have to reformat the ubuntu partition and reinstall ubuntu.

---

### Post by Selgar on 2010-11-03
Thanks for all your help on this.
 
In the end I took the cowardly option!
 
For any fellow Ubuntu newbies that may have the same problem I got a bootable super grub 2 disc that I downloaded from:
 
[http://www.supergrubdisk.org/category/download/supergrub2diskdownload/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/)
 
I burnt this directly to a DVD using Windows and am now able to access Ubuntu and Windows as long as I boot from the CD directly via the F12 key. I can then jump from this to the existing Grub 2 installation on the hard drive.
 
I decided that this way I could retain all the software and avoid any unforeseen consequences of removing Dell datasafe.
 
In the meantime I will download a copy of the Windows recovery media and other discs that you mentioned and will contemplate trying a more elegant solution to the problem. However the main thing is that I can access both operating systems reliably and quickly.
 
Thanks again for all your help - I had wondered whether the legendary Linux community might not be as helpful as I had been led to believe but I have found my faith in human nature vidicated! :P

---

### Post by gregb49 on 2010-11-04
Surely there must be a more elegant solution as those with netbooks (no optical disk drive) will not be able to use a cd to boot

---

### Post by wilee-nilee on 2010-11-04
> **gregb49 said:**
> Surely there must be a more elegant solution as those with netbooks (no optical disk drive) will not be able to use a cd to boot

Yes most things can be done with a loaded thumb, and a user that has followed some standard protocol of backups and or hard copies, and ISO's of installs.

You ask this question with no suggestion what is the point really.

---

### Post by gregb49 on 2010-11-05
On Guy Fawkes day wilee-nilee said:> You ask this question with no suggestion what is the point really.I have an eeepc netbook on order which has Win7 installed. I am investigating how to boot from a USB drive so that I can install Ubuntu. It looks as if there is a problem with dual boot machines in that Win 7 writes to the MBR sometimes, so I'm investigating that.

---

### Post by Selgar on 2010-11-27
It turns out there is a more elegant solution:

[http://ubuntuforums.org/showthread.php?p=10170655#post10170655](http://ubuntuforums.org/showthread.php?p=10170655#post10170655)

This worked fine for me although it looks like it might be worth uninstalling DDSB in safe mode.

---

### Post by wilee-nilee on 2010-11-27
> **Selgar said:**
> It turns out there is a more elegant solution:

[http://ubuntuforums.org/showthread.php?p=10170655#post10170655](http://ubuntuforums.org/showthread.php?p=10170655#post10170655)

This worked fine for me although it looks like it might be worth uninstalling DDSB in safe mode.

Look in post 2 dell data safe is mentioned, you, you necromancer.;)

Just joking with you.:popcorn:

---

