---
title: "My Folder is Gone Completely"
date: 2018-09-16
forum: Installation &amp; Upgrades
---

### Post by emran.a.mostofa on 2018-09-16
HI there,
I wanted to backup one of my folder in my Home directory and went to my google drive and selected my "My Study" folder to upload. It showed me that it would take 108+ hours to do so..so I let it upload in the background and started working in other tab.
Suddenly My laptop was frozen and nothing was working except mouse pointer.So I restarted my laptop and went to my google drive in my browser and since the whole "My Study" folder wasn't fully uploaded I deleted the folder in my google drive and again selected the folder to upload But this time again but my laptop froze again...so restarted it again Now I dont find my "My Study" folder in my home directory.
I searched My folder in the trash and even in the google drive trash.and when I go to properties of my Home I see the full storage(I think the folder is just vanished).
In that folder I had everything related to my study materials.I need them.They are of very very importance to me..

some one please please Help me..
what Should I do?

---

### Post by oldfred on 2018-09-17
Abnormal shutdown often causes file corruption. You almost never should force shutdown of system. And if mouse still worked, you probably could have closed system correctly.

How much data was taking 108 hours? Or do you have really slow Internet?

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274) 
    
But if files folders are gone but partition is still valid, your only recouse may be a scan of drive.
It requires you to have another drive with enough room for all your data. And it recovers deleted data. I had saved some files many times with additions & deletions & it recovered most of them. But then I had to compare each of them to try to recreate most current version. It also only recovers files by extension.

Best to also create image of partition that had your data and only work on image. If then you damage it, you still can create a new image. See link below on other recovery tools.
       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Other Linux tools:
       
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

