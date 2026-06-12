---
title: "Ubuntu 10.10 to extra drive from within Windows"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Nthkentman on 2010-11-19
Ok... After 22 unsuccessful tries at CD/DVD installs using WUBI, Versions 9 and 10 various flavours I have succeeded in installing Ubuntu 10-10 onto a spare drive (Secondary master) WITHOUT utilising the WUBI update download (Which takes Aeons) when it cannot find the ISO etc.

I am running XP with SP3 on the machine for the Ubuntu install. I have internet access on another machine to check for ****-ups, advice and other stuff.

DON'T get all shouty at me if you decide to install on your precious internet access PC and it's the only one you have and you **** it up !

So, this is how I did it.

1    Download (If you haven't already got it) Winzip for your Windows install on Primary (1st) Hard Drive. Install as required and if you want to register it/pay for it then do so, but it will work Ok. (It is useful after all)
2    Format the extra drive NTFS & Download the correct 10-10 ISO onto THATdrive root 
3    Using Winzip unzip WUBI installer file from the ISO to the drive root of your 2nd drive where Ubuntu is going to be. Leave everything else as is.

DISCONNECT YOUR INTERNET/NETWORK CONNECTION AT THIS POINT OR THE INSTALL MAY TRY TO DOWNLOAD THE ENTIRE ISO AGAIN.

4    Reboot into Windows
5    Run WUBI, either click on file in root of extra (2nd) drive OR from RUN menu.
6    Follow instructions on where you need to install Ubuntu (I used the 2nd 80 gig drive where the ISO and unzipped entire zip file is) Make sure you choose a suitable size install... I had plenty of space so chose 20 gig. Your choice/size is up to you.

THIS WAY IT LEAVES THE ENTIRE WINDOWS INSTALLATION ALONE AND UNAFFECTED APART FROM THE CHOICE OF BOOT AT START

7    Ensure you remember the password you choose as needed again later when using the WUBI installer. (Write it down)
8    Wait while the system installs and asks for reboot, THEN when the PC reboots select Ubuntu to boot into. 
9    Wait until installation finishes. (Depends on your PC speed how long to install)
10   Follow the screen instructions where required to boot into Ubuntu when finished and reconnect your internet/network connections as required to carry on surfing etc.

NOTE
The very first time I installed Ubuntu 10-10 I upgraded/updated to whatever new files are needed using the manager. LOOK VERY CAREFULLY at what is being updated when doing this as GRUB can be overwritten leaving you back at square one again and no boot! At this point remove sharp objects from the area around you (Prevents premature suicide attempts) and insert the Windows disk of your operating system and restore the MBR to Windows boot only. Plenty of sites advising how to do this.

DAMHIKIJD.... OK!

Hope this simple install guide gets you going and check on the forums for issues but DON'T ASK ME 'cos I are a relative Ubuntu Newbie meself !

If anyone can see anything needed to add/subtract from this post please do so and improve the experience for new users

---

### Post by mikewhatever on 2010-11-19
What was the point of using wubi when installing to an external hdd?

---

### Post by cybergnome on 2010-11-19
Wubi doesn't exactly leave the Windows installation alone.  It creates folders, files and registry entries, all of which are the price for installing inside of Windows and being able to use a Windows uninstaller.

---

### Post by Nthkentman on 2010-11-20
> **mikewhatever said:**
> What was the point of using wubi when installing to an external hdd?


Well Mike, in other posts I have described the problems with particular CD/DVD drives. The system would not accept/boot from a drive other than the HD with Windows on it.

Given that every time I tried it failed I went the WUBI route several times which for whatever reason failed to see the CD/DVD drive and attempted a *very* lengthy download of a new ISO.

I am not (As some also are not) perhaps as technically minded with Ubuntu as yourself and others that are more adept at installing, hence my suggestions of a way to install if you have been frustrated by attempts so far.

I accept there are probably many ways to install a distro, but this one worked OK for me and is up and running so it might help others who have similar problems.

Cheers

Have a nice weekend...

---

### Post by Nthkentman on 2010-11-20
> **cybergnome said:**
> Wubi doesn't exactly leave the Windows installation alone.  It creates folders, files and registry entries, all of which are the price for installing inside of Windows and being able to use a Windows uninstaller.

Fair comment, and for new Ubuntu users who have grown up with Windows flavours a small addition which does not upset their installation where they can go back to their original O.S is a relief and one les worry.

---

