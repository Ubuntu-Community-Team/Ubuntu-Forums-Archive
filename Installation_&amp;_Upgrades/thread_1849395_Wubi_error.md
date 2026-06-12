---
title: "Wubi error"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by Piticul on 2011-09-24
I downloaded wubi and ubuntu 11.04 desktop cd iso from the ubuntu website and I puttem in the same folder. I installed it and I rebooted. After the ubuntu logo it loads 5 red dots and after that it says me  '' Could not find the iso(/ubuntu/install/installation.iso) ". I checked that file in Windows and it exists! I'm using windows 7 32bit Ultimate .. any help?

---

### Post by bcbc on 2011-09-24
What 'drive' did you install Wubi on? Your C: drive or another? If another, is it on an external drive? Something else?

---

### Post by Piticul on 2011-09-24
> **bcbc said:**
> What 'drive' did you install Wubi on? Your C: drive or another? If another, is it on an external drive? Something else?
I installed it on C:

---

### Post by bcbc on 2011-09-24
Try running chkdsk /r from windows. If your drive needs defragmenting do that as well.

---

### Post by Piticul on 2011-09-24
> **bcbc said:**
> Try running chkdsk /r from windows. If your drive needs defragmenting do that as well.

It says :
The type of the file system is NTFS.
Cannot lock current drive.

EDIT: I tried checking the C drive and this shows : [IMAGE]("http://postimage.org/image/1cphuzeec/")

---

### Post by bcbc on 2011-09-24
Look in the (hidden) C:\found.000 folder to see what it recovered. 

When you run chkdsk using the GUI, Computer, right-click on C:, Properties, Tools, Check disk for error, fix automatically - it should tell you it needs to reboot. Schedule the check for the next time you boot and then reboot to complete. Make sure everything is clean before retrying.

The /f represents "Fix errors automatically". The /r represents "scan for bad blocks".

---

### Post by Piticul on 2011-09-25
I can't find the found.000 folder.. I tried  search option of Windows, tried to find it on cmd using cd and dir.. nothing.. i checked that hidden folders are visible, and nothing.

---

### Post by bcbc on 2011-09-25
did you go to an administrator command prompt?

---

### Post by Piticul on 2011-09-26
Yes, sir.
I forgot to mention that I had another Windows in the past and I didn't delete it. I installed the actual Windows (7) on C partition.. the other one was in D. Could be this the problem?

---

### Post by bcbc on 2011-09-26
It doesn't matter which partition you install on - usually. 

So where are you at? You've run chkdsk and it told you it corrected some corruption. Did you try reinstalling after that?

---

### Post by Piticul on 2011-09-26
I guess no(t). I left the computer doing the checks and I went to sleep. When I woke up, I checked it everything is ok and I shutted down the PC. After 7 hours I started it again.
P.S: Why the step 4 take so many time? Idk, maybe 30-60 minutes ?!

---

### Post by rob45 on 2011-09-26
hi ,it sounds to me like your ubuntu install has been saved on D drive rather than C drive,that is why windows cant find it. When using wubi to install ubuntu windows is in charge of the boot mbr(master boot record).If you can get in to windows try searching for the file you mentioned ,if it is on the D drive point it to the C drive,move it to the C drive so windows can see it. If that makes sense?










9

---

### Post by Piticul on 2011-09-26
Hi rob45, my ubuntu folder is located on C, also the installation.iso in C:\ubuntu\install\

---

### Post by bcbc on 2011-09-26
> **Piticul said:**
> I guess no(t). I left the computer doing the checks and I went to sleep. When I woke up, I checked it everything is ok and I shutted down the PC. After 7 hours I started it again.
P.S: Why the step 4 take so many time? Idk, maybe 30-60 minutes ?!

I guess in step 4 it's trying to locate and correct for bad sectors. It does take a long time, but maybe it shouldn't be as long as you're reporting.

---

### Post by Piticul on 2011-09-26
Ok, I see this is getting harder and harder.. I decided to install ubuntu from USB. I have the iso, now i need to copy it to usb. How could I delete the windows from D drive and make a 150GB partition for ubuntu? Can you give me tutorials for those?

---

### Post by bcbc on 2011-09-26
When you install a newer windows version over an older one, it combines the boot loaders - usually installing the new one on the old windows' partition. So you need to be careful when you delete one of these.

Why don't you boot that USB in live mode - select "Try it" without installing, and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That will help identify where the boot files are.

---

