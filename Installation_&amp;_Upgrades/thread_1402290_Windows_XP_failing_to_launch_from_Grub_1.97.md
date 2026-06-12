---
title: "Windows XP failing to launch from Grub 1.97"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by solo321 on 2010-02-09
[LIST]
[*]I recently installed Unbuntu 9.10 Netbook remix on my Windows XP machine.  Whenever I go to launch windows xp, the main windows xp screen shows up.  But when it starts to load, the blue loading bar stops halfway and windows xp will not load.  A blue screen flashes real fast then it redirects me to the grub main screen.  
[*]I have tried to update and reinstall grub, the same thing happens.  Even when I launch into windows xp safe mode it fails to launch.  

[*]In summary windows xp launches from Grub but does not load correctly.

[*]Any help or advice?

[*]Thanks
[/LIST]

---

### Post by nerdtron on 2010-02-09
Please add more information. How did you installed Ubuntu Netbook Remix? What are are the options you chose during the installation? How about your partitions? Were did you installed Ubuntu and GRUB?

---

### Post by solo321 on 2010-02-09
I had Windows XP installed at first, then I installed Unbuntu Netbook remix via a Flashdrive.  I partitioned the hard drives so that Windows xp is (on /dev/sda1) and ubuntu is Ubuntu, Linux 2.6.31-19-generic.  

On the install of Ubuntu I choose to partition the hard drives automatically and just dragged the slider to size the partitions of the size I wanted.  I remember I selected Windows XP to be Primary and Ubuntu to be Secondary.  Then I updated Ubuntu, and since then i cant log into windows.

When I try and log into windows it goes to the XP loading screen.  The thinking bar slides across, stops 3/4 way, and reverts to a blue screen really fast and goes back to GRUB


.

---

### Post by epicoder on 2010-02-09
My guess is that the ubuntu partitioner didn't correctly grow/shrink the windows partition. You may have to reinstall. I'm still a n00b myself, so DON'T do it until there's another post confirming this.

EDIT:
You could try booting from your XP disk, going to the console, and running chkdsk /f.

---

### Post by solo321 on 2010-02-09
> **sh228 said:**
> My guess is that the ubuntu partitioner didn't correctly grow/shrink the windows partition. You may have to reinstall. I'm still a n00b myself, so DON'T do it until there's another post confirming this.

EDIT:
You could try booting from your XP disk, going to the console, and running chkdsk /f.



Ok Ill try that.  When I boot from GRUB it just fails like I explained.  I dont know entirely how to boot from console like that but Im sure I could figure it out.  Thanks.  

Does anyone else have any ideas/suggestions/confirmations?

---

### Post by oldfred on 2010-02-09
I copied all this from other posts. Do not run fixboot unless you want to overwrite grub and boot directly into windows to see if it works. You will then have to reinstall grub.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C: 
chkdsk C: /R
Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

Microsoft XP boot disk floppy
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

---

### Post by solo321 on 2010-02-09
> **oldfred said:**
> I copied all this from other posts. Do not run fixboot unless you want to overwrite grub and boot directly into windows to see if it works. You will then have to reinstall grub.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C: 
chkdsk C: /R
Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

Microsoft XP boot disk floppy
[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)


How do I mount my windows drive?  "Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\."

I have a netbook so I will just mount the recovery disks to a USB drive and boot from there.  I will try those ideas and see if it works.  

Jeez all this from just a failure to boot.

---

### Post by oldfred on 2010-02-09
I may have overposted. The instructions included everything including the kitchen sink.

I would first run chdsk  with the -f or which ever parameter it is to fix. (Changed with different versions). and you may have to run it several times until you get no errors. Then if that does not work, try the repair console and fix commands. the fix commands should reload the files if they have problems.

---

