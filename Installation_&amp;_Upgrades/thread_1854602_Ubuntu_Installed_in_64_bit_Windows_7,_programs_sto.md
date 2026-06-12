---
title: "Ubuntu Installed in 64 bit Windows 7, programs stopped working"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by mpjoy on 2011-10-04
In an unfortunate moment on an impulse I installed Ubuntu using wubi in my perfectly working 64 bit windows 7 computer to make it a dual boot computer. The moment ubuntu got installed a program which was running in Windows stopped working. Dual booting was working fine except that some programs in Windows was not working. I removed ubuntu, still they are not working. 
 
How do I make my computer work properly as before? What did Ubuntu do to destroy my computer? I tried all different forums, etc, I never could find a solution. PLEASE HELP.

---

### Post by haqking on 2011-10-04
> **mpjoy said:**
> In an unfortunate moment on an impulse I installed Ubuntu using wubi in my perfectly working 64 bit windows 7 computer to make it a dual boot computer. The moment ubuntu got installed a program which was running in Windows stopped working. Dual booting was working fine except that some programs in Windows was not working. I removed ubuntu, still they are not working. 
 
How do I make my computer work properly as before? What did Ubuntu do to destroy my computer? I tried all different forums, etc, I never could find a solution. PLEASE HELP.

edit: ignore me ;-)

I misread your post

---

### Post by Mark Phelps on 2011-10-04
And, of course, it didn't occur to you to make a backup of your Win7 setup PRIOR to fiddling around with Ubuntu, right?

The standard "solution" in Windows in these cases is to look for a System Restore point that was made BEFORE you did the Ubuntu install.  If you can find one, and if it works, you'll probably be OK.

If that doesn't work, since this is not REALLY a Windows 7 forum, you should then go over to sevenforums.com and look through their forum for tutorials that walk you through the following processes:
1) Repairing/replacing damaged system files
2) Doing a Repair Install of Win7

In both cases, you are likely to need Win7 Install media (i.e., the Win7 DVD).  If you don't have this, you can do some limited work by using the Win7 Backup feature to create and burn a Win7 Repair CD.  You can boot into the Win7 Command Line from that and run sfc /scannow -- but you can't reinstall from that.

If neither of these work, then you are looking at a complete Restore to factory settings -- meaning, you will lose ALL your apps and ALL your data.

---

### Post by mpjoy on 2011-10-05
Thanks for the reply. That's right, I didn't do any backing up. Never expected that ubuntu will corrupt system files! 
I tried to system restore to a previous time point but that also didn't help. Since I do not have Win 7 Install media, I have to try 'other' methods.
 
But it will be useful to know what are the files ubuntu installation will be deleting or changing! Problems are with programs using communication ports.
 
 
> **Mark Phelps said:**
> And, of course, it didn't occur to you to make a backup of your Win7 setup PRIOR to fiddling around with Ubuntu, right?
 
The standard "solution" in Windows in these cases is to look for a System Restore point that was made BEFORE you did the Ubuntu install. If you can find one, and if it works, you'll probably be OK.
 
If that doesn't work, since this is not REALLY a Windows 7 forum, you should then go over to sevenforums.com and look through their forum for tutorials that walk you through the following processes:
1) Repairing/replacing damaged system files
2) Doing a Repair Install of Win7
 
In both cases, you are likely to need Win7 Install media (i.e., the Win7 DVD). If you don't have this, you can do some limited work by using the Win7 Backup feature to create and burn a Win7 Repair CD. You can boot into the Win7 Command Line from that and run sfc /scannow -- but you can't reinstall from that.
 
If neither of these work, then you are looking at a complete Restore to factory settings -- meaning, you will lose ALL your apps and ALL your data.

---

### Post by CharlesA on 2011-10-05
Do a system restore and pray.

I'd suggest going over to the sevenforums as well.

---

