---
title: "Ubuntu GRUB won't boot XP anymore!"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by donkthemagicllama on 2005-10-06
I had a system configured as follows:

40GB drive
10GB FAT32 partition with Win98
30GB NTFS partition with XP

I never used the 98 partition, so I installed Ubuntu over it, deleting the old partition.

When I first finished, GRUB didn't see any Windows installations at all, and installed with Ubuntu as the only option.  I need XP to work still, so I attempted to fix it by using the XP CD and performing a recovery.  It recovered, but apparently didn't overwrite the MBR, since GRUB was still in use, and it didn't let me choose XP.  Also, somehow, this broke Ubuntu.

I realized at this point that my XP partition and the installation were still OK.  In fact, if I booted with a boot CD that contained NTLDR, I could still boot XP and it worked fine.

I reinstalled Ubuntu again, this time, GRUB saw the XP installation.

Now, when I reboot, I get GRUB with XP and Ubuntu options.  Ubuntu works fine, but XP won't boot from GRUB.  It just hangs.

Any suggestions?  In retrospect, this was a dumb way to go about this, but I figure I'm so close (i.e. it will still boot with the NTLDR CD) that there must be some way to repair the boot sector (I assume that's what the problem is) on the XP partition?

Thanks...

---

### Post by manicka on 2005-10-06
First I'd check /boot/grub/menu.lst and see if the XP entry looks something like this 
```
title           Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```
If not run in a terminal
```

sudo gedit /boot/grub/menu.lst
```
and change the entry, then try again

If that doesn't work I would run 'fixmbr' from the recovery console of your xp disc (this should remove grub and make XP bootable), then restore grub following the advice at this thread.
[http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

### Post by donkthemagicllama on 2005-10-06
Yes, that's exactly what my GRUB entry looks like.

I think my problem has do to with XP not being on the first partition?
I'm not at my Ubuntu PC right now (it's at work), but after perusing the forums, I ran across another menu.lst that had a line like this... is this what I should have in my XP entry?

chainloader (hd0,1)+1

Not knowing how GRUB works, is it possible "chainloader +1" is attempting to boot from the wrong partition (XP is on hda2 -- hd0,1 in GRUB parlance).

Sound likely?  Or am I getting this all wrong?

---

### Post by Emerzen on 2005-10-06
title           Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1
-------------------------------------------------------
in the above, try changing-> root    (hd0,0) to -> root   (hd0,1) but don't change the changeloader line.

---

### Post by asterix404 on 2005-10-06
what does it say when you try to find your windows partition and do you only have one disk in your computer?

if it sais something like can not find nessacary system file on system(0)/partition(0)/.... or something to that affect that means that you basicly set your root to windows incorrectly. To fix that problem do the above, however XP has a nasty feature of saying something like "New Harddrive found" and will ask you if you want to format it as NTFS or whatever since windows can't read anything other then NTFS and fat32 and will bitch at you for having anything else. DO NOT FORMAT! This is a problem with having a windows and linux install on the same partition, hopefully you will be careful and not let someone erase your ubuntu parition. 

Don't run the fixmbr as that will totally destroy your chances of getting the ubuntu parition to be accessed, and if you want to run it you will have to install all over again which I am guessing you don't want to do.

---

### Post by manicka on 2005-10-06
[QUOTE=asterix404]
Don't run the fixmbr as that will totally destroy your chances of getting the ubuntu parition to be accessed, and if you want to run it you will have to install all over again which I am guessing you don't want to do.[/QUOTE]

Yes, running fixmbr is a drastic step but doesn't mean that your ubuntu partition can't be accessed, requiring a reinstall. It's a fiddly but fairly straight forward process to reinstall grub after fixmbr. Just follow the steps at the link mentioned previously.

---

### Post by donkthemagicllama on 2005-10-06
Sorry, my GRUB root line does indicate the correct drive (hd0,1).

I tried running fixboot c: from teh XP recovery console, and now instead of getting no message, I get:
"error occurred"

I haven't tried fixmbr yet, as I want to know how to fix what it breaks first.

I think the problem stems from the fact taht I never did boot off this drive (it was my e:\ drive).  I had 98 installed on my c:\ drive, then installed XP on my e:\ drive so I could dual boot.  I wiped out the c:\ partition with Ubuntu.  NTLDR and NTDETECT.COM are in the root directory of e:\ (hd0,1).

Any more suggestions?  Will fixmbr actually help, considering that my hd0,0 drive is NOT a Windows NTFS partition?

Thanks for the help thus far!

---

### Post by manicka on 2005-10-06
fixmbr will just rewrite the mbr so that windows only can boot. It shouldn't matter what disk it's on.

---

