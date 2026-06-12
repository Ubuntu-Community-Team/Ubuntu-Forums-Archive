---
title: "Help with dual-booting"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by Wazoot on 2008-04-20
Yes. I currently have Windows XP installed,and am on the Ubuntu 7.04 liveCD. I have done a clean install of Ubuntu over windows before on one of my older computers, But the GNOME Partition editor doesnt seem to want to apply the changes i make. Can anyone help me? :KS :)

*Here is the error details*

GParted 0.2.5

Resize /dev/sda1 from 111.78 GiB to 101.95 GiB    ( ERROR )
     	
check filesystem on /dev/sda1 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v1.13.1 (libntfs 9:0:0)
Device name : /dev/sda1
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 120023253504 bytes (120024 MB)
Current device size: 120023253504 bytes (120024 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 5313165 (0x51128d): extra cluster in $Bitmap
Cluster accounting failed at 5313166 (0x51128e): extra cluster in $Bitmap
Cluster accounting failed at 5313167 (0x51128f): extra cluster in $Bitmap
Cluster accounting failed at 5313168 (0x511290): extra cluster in $Bitmap
Cluster accounting failed at 5313169 (0x511291): extra cluster in $Bitmap
Cluster accounting failed at 5313170 (0x511292): extra cluster in $Bitmap
Cluster accounting failed at 9625814 (0x92e0d6): extra cluster in $Bitmap
Cluster accounting failed at 9625815 (0x92e0d7): extra cluster in $Bitmap
Cluster accounting failed at 9625816 (0x92e0d8): extra cluster in $Bitmap
Filesystem check failed! Totally 9 cluster accounting mismatches.
ERROR: NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The usage of the /f parameter is very IMPORTANT! No modification was
and will be made to NTFS by this software until it gets repaired.

========================================

---

### Post by Shazaam on 2008-04-20
I would do as it suggests and run chkdsk /f in Windows. AND, defrag Windows before you resize.

---

### Post by Wazoot on 2008-04-21
I have run defrag in windows TWICE, and chkdsk TWICE in windows and still the same error?
I've got 8.04 beta ubuntu dual-booting with Wubi at the moment so im satisfied with that. But once 8.04 comes out of beta i want to be able to actually partition my hd and install it.
Can anyone help me now? lol :(

---

### Post by Kevbert on 2008-04-21
With windows you may have a paging file towards the end of the drive. If this block of data has not been moved you'll need to turn off this file. It can be found at Control Panel - System - Advanced Tab. Now click on Settings under Performance and select the Advance Tab. Now click on Change, the Virtual Memory paging file and select the No Paging File radio button. No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again. There should now be extra room at the end of the disk.
Don't forget to back everything up.

---

### Post by Wazoot on 2008-04-21
Thanks. I will do a reboot and a defrag now. 
Now im installed using Wubi, and when it UBuntu boots up it boots to a black screen? Loading bar does fine, then boots into a black screen or a dos sort of thing. Can anyone help with this?

---

### Post by Kevbert on 2008-04-21
It suggests that you have a display driver problem and you can't start the graphical interface X. You could try Ctrl-Alt-F7 to see if you can get X.  If not, I'd search on the forums for your graphics card.

---

### Post by Wazoot on 2008-04-21
Thanks so much for your help K. Im pretty new to Linux so yeah. :KS   ill try and do that now. Ill post when im done =D and hopefully into linux...

---

### Post by Wazoot on 2008-04-21
> **Kevbert said:**
> It suggests that you have a display driver problem and you can't start the graphical interface X. You could try Ctrl-Alt-F7 to see if you can get X.  If not, I'd search on the forums for your graphics card.

Ok. ive rebooted into Ubuntu and it is still a black screen. I tried the ctrl-alt-F7 thing and that didnt work either...im starting to think my Ubuntu 8.04 beta is screwed.

---

### Post by Wazoot on 2008-04-21
*bump*
OK. i had enough of this so i wiped Ubuntu/Wubi off my system and did a fresh install of Ubuntu with Wubi. I am in Linux now =]   Hopefully with this it will fix my problems..will post if any more.  Thanks for all of your help guys. :popcorn:

---

### Post by Wazoot on 2008-04-21
Ok. i had enough with the beta. I resorted to Ubuntu 7.10 wubi. 
=] :KS

---

