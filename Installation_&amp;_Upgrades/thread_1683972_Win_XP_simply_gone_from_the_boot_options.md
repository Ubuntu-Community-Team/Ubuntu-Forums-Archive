---
title: "Win XP simply gone from the boot options"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by pointee on 2011-02-08
Hi Forum!

I am an ubuntu newbie. 
so far, my two partitions (ubuntu and WinXP) worked fine, i always had a boot option at startup. however, my Win boot option simply disappeared. I did not do any update recently, so I do not really understand what could have happened. 
My /media/windows is also completely empty. when i try to open the windows partition, it says "could not mount".

could someone please help me?

many thanks!

---

### Post by oldfred on 2011-02-08
If windows needs chkdsk run, Ubuntu may not mount it, so you do not damage it to a point that chkdsk could not fix it.

I would try chkdsk first, from your XP CD.

XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by pointee on 2011-02-08
thanks for the reply, however, i cannot do that as i am on the road (abroad) and do not have the XP CD.

---

### Post by oldfred on 2011-02-08
You can download any of these to run chkdsk. They will not repair most things with XP.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by gordintoronto on 2011-02-08
You could open Accessories/Terminal and paste in this command:
sudo update-grub

It will ask for your password, and it won't display it as you type.

---

### Post by cipherboy_loc on 2011-02-08
If update-grub does not work, try running the boot script in my signature and posting the resulting results.txt file.


Cipherboy

---

### Post by pointee on 2011-02-08
update-grub worked!!! thanks a lot!!
but what has happened? and what did this update-grub do?

---

### Post by gordintoronto on 2011-02-08
It looked at what was on the computer, and rebuilt the boot script. I can't imagine how it got borked in the first place.

---

