---
title: "Explanation please"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by OperatorA on 2010-09-24
Good morning :-)

I was dorking around in a dos window in Windows-XP and I found this...

C:\ubuntu>dir
 Volume in drive C has no label.
 Volume Serial Number is FC32-FBDF

 Directory of C:\ubuntu

09/20/2010  08:39 AM    <DIR>          .
09/20/2010  08:39 AM    <DIR>          ..
09/20/2010  08:39 AM    <DIR>          disks
09/20/2010  08:39 AM    <DIR>          install
09/20/2010  08:39 AM             1,150 Ubuntu.ico
09/20/2010  08:39 AM         1,467,844 uninstall-wubi.exe
09/20/2010  08:39 AM    <DIR>          winboot
               2 File(s)      1,468,994 bytes
               5 Dir(s)  35,682,684,928 bytes free

C:\ubuntu>

I thought I had done a direct install without "wubi".

I see a file " uninstall-wubi.exe  "...does that mean i installed with wubi, and if i wanted to uninstall say to do a clean install of "KuBuntu" or some other flavor can i run  " uninstall-wubi.exe  " and uninstall Ubuntu like it was a "file" and not an hard install of the OS? (I am satisfied with Ubuntu - no problems)
Just curious and learning.

Thanks guys for your replies...you'all really are good teachers and in the week and a half I have used Linux you have already taught me a lot...

Larry:confused:

---

### Post by pmlxuser on 2010-09-24
you don't install clean install from windows; you need to start with CD or usb to do that...

creat separate partition for ubuntu and do that, else use ubuntu partitioning if you are up for the task..

---

### Post by pricetech on 2010-09-24
Shrink your partition using Disk Management in Windows before you install Ubuntu.  Reboot after shrinking and let XP do its checkdisk thing, then install.

Back Up your data FIRST, before doing anything else.

---

### Post by coffeecat on 2010-09-24
It looks as though you have done a Wubi install. You wouldn't get a C:\ubuntu folder without one. What is in the folders C:\ubuntu\disks and C:\ubuntu\install?

Have a look in Add/Remove programs in XP. You will probably see Wubi in there for uninstallation.

---

### Post by OperatorA on 2010-09-24
That is what I thought I did. Re-booted machine with Ubuntu in the CD reader and went from there...that is why I asked the "wubi" question Did it do a clean install as I thought I did, or default to "wubi" in some way...

Larry

---

### Post by OperatorA on 2010-09-24
I checked "Add & Remove Programs" and it showed an entry for "Ubuntu" but no "wubi" entry. Am I to assume it DID install with "wubi" even though I thought i has split the partition and done a clean install? 

I's ok if it did do a "wubi" i just want to be clear how it ACTUALLY did do the install is all...if "wubi" no problen killing Ubuntu say if i want a clean install of KuBuntu...though i find the Kubuntu desktop id ubuntu a bit 'busy' for me for a better word...

Just run the windows "Add & Remove"...(above paragraph):P

Thanks for all the replys guys...
Larry

---

### Post by Frogs Hair on 2010-09-24
Wubi is just the installer and the file/s are located in local disk c and are outside of program files. They should be removed automatically if you remove Ubuntu from add/remove programs in Windows.

---

### Post by OperatorA on 2010-09-24
> **Frogs Hair said:**
> Wubi is just the installer and the file/s are located in local disk c and are outside of program files. They should be removed automatically if you remove Ubuntu from add/remove programs in Windows.
So if I understand it right, To remove "Ubuntu" in order to do a clean install of another variant...all I need do is run Wundows-XP "Add & Remove Programs/Ubuntu"..then run dfrag and reinstall another variant.
Cool (said the old hippie..) ... Once i feel comfortable with it I will run Ubuntu or a variant of it and wipe Windows.

Wife has threatened castration if I touch "our" (mine actually)
 laptop and install Linux on it...LOL

I have already had Ubuntu for two weeks and already prefer it to Windows. I like the feature that makes you enter a password to change things...keeps "others" from screwing with my computer when I am not around...

Thanks one and all...
Larry

---

### Post by Frogs Hair on 2010-09-24
Wubi installs Ubuntu inside the Windows partition  and uses the Windows boot loader . To install Ubuntu on its own partition you will have to download the ISO create a disk and follow the dual boot instructions from the disk . This type of installation is completely independent of windows , check Youtube for how to videos if interested. If you want to continue using Wubi and try another variant , you must remove the current installation download Wubi again and install the variant from the selection on the Wubi drop-down menu .

---

### Post by OperatorA on 2010-09-24
> **Frogs Hair said:**
> Wubi installs Ubuntu inside the Windows partition  and uses the Windows boot loader . To install Ubuntu on its own partition you will have to download the ISO create a disk and follow the dual boot instructions from the disk . This type of installation is completely independent of windows , check Youtube for how to videos if interested. If you want to continue using Wubi and try another variant , you must remove the current installation download Wubi again and install the variant from the selection on the Wubi drop-down menu .
I thought I HAD used the stand alone install *iso...that is my confusion...
Everybody says since "Ubuntu" shows up in Windows "Add & Remofe Programs" menu then it was a "wubi" install...just wanted to be sure.

I have the "factory" disks from Ubuntu now and if i reinstall Ubuntu i will use them.

I believe I Prefer the "Gnome" (Ubuntu) desk-top as opposed to the "KDE" (Kubuntu)version...I like a cleaner look with less "flash" on my desktop.

Will consider a "wubi" install of KuBuntu just to try it out without the clutter of two desktops leftovers though. 

That is why i wanted to be sure it was "wubi" removable by Windows and NOT a HARD install...

I know Linux (in some form - Ubuntu probably) is my future OS.

If Windows-XP gets hosed for what ever reason it is gone and a clean install of Ubuntu will go on my hard drive. Besides I DID make all the restore disks when I first got the PC and I still have then in my "crap-box" after 5 years...I am kinda anal about stuff like that...laughing at myself here...

You Forum guys (and galls) are great ...

Larry

---

