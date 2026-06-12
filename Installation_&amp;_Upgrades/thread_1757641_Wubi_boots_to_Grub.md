---
title: "Wubi boots to Grub"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by tdp2110 on 2011-05-13
Hey All, total n00b here. I recently installed Wubi inside of Windows 7 (just this week). Things were going well until today, when I can no longer boot to Linux--after selecting `Ubuntu' on the boot page, I get sent to a Grub screen (I'm blaming Windowz update for this)

I've tried a bunch of potential fixes from these forums but I'm still **** out of luck.

Any help would be greatly appreciated. Thanks.

---

### Post by bcbc on 2011-05-13
What release of Ubuntu are you running?
What version of grub does it say (top of screen). 1.98xxx or 1.99~rc1xxxx?
Any hard shutdown's or freezes lately?

---

### Post by tdp2110 on 2011-05-13
Thanks for the reply. I just downloaded Wubi this week, so I'm assuming I have Ubuntu 11.04 (but I don't know how to check without booting).

GNU GRUB version 1.97~beta4

Yes, I believe I had to hard shutdown once this week during some sort of freeze-up (though I'm pretty sure I was still able to boot Ubuntu after that).

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> Thanks for the reply. I just downloaded Wubi this week, so I'm assuming I have Ubuntu 11.04 (but I don't know how to check without booting).

GNU GRUB version 1.97~beta4

Yes, I believe I had to hard shutdown once this week during some sort of freeze-up (though I'm pretty sure I was still able to boot Ubuntu after that).

That's not 11.04 (it would say 1.99~rc1-13ubuntu3 if it was).

Where did you get the wubi.exe from? or if you installed from CD where did you get it?

PS do you have an Ubuntu CD you can boot from? you might need it to repair.

Edit: I think that might be karmic (9.10). If that rings a bell, then there is a special boot file you need to replace for karmic - it's an easy fix. But I'll wait for you to confirm where you got wubi.exe before recommending you try this.

---

### Post by tdp2110 on 2011-05-13
I got wubi.exe from [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Uh, not sure about the version ..

Unfortunately I don't have a Live CD

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> I got wubi.exe from [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Uh, not sure about the version ..

Unfortunately I don't have a Live CD

That links to the 11.04 wubi.exe (unless you have a bad mirror) but that doesn't match the grub version you are getting. Can you locate wubi.exe on your hard drive and tell me the size? e.g. 1495KB (if you just see 1.4MB then right click, Properties and get the full size). Also look at the digital signature (signed by Canonical) and see what the timestamp says.

---

### Post by tdp2110 on 2011-05-13
1495KB

(Size: 1.45 MB (1,530,520 bytes), Size on disk: 1.46 MB (1,531,904 bytes))

Canonical timestamp: Weds, April 27, 2011 12:44:18PM

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> 1495KB

(Size: 1.45 MB (1,530,520 bytes), Size on disk: 1.46 MB (1,531,904 bytes))

Canonical timestamp: Weds, April 27, 2011 12:44:18PM

Have you replaced the file C:\wubildr ? What size is it?

---

### Post by tdp2110 on 2011-05-13
I tried doing this, but it seems I used a version for Ubuntu 9.10 from [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

That has size 79KB

The old (coming from the original download of Wubi) version has size 145KB

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> I tried doing this, but it seems I used a version for Ubuntu 9.10 from [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

That has size 79KB

The old (coming from the original download of Wubi) version has size 145KB
That explains it. You're using a Karmic Wubildr for Natty - and that won't work.

But I suppose you only tried that because Natty was broken, so it doesn't help fix it.
Let's try and get better diagnostics. First replace the karmic wubildr (C:\wubildr) from the one in C:\ubuntu\winboot\wubildr (change drive letter if you installed on a different drive - not C:\wubildr though which must be on C:\).

Then boot to Ubuntu and report back on the error you get.
When you are at the grub prompt give me the results of:
```
echo $root
```

Also confirm the contents of:
C:\ubuntu\disks (change drive letter as required)

---

### Post by tdp2110 on 2011-05-13
Upon updating wubildr, the grub version changed to: GNU GRUB version 1.99~rcl-13ubuntu3

grub> echo $root
memdisk

C:\ubuntu\ only contains:
   install\
   winboot\
   Ubuntu.ico
   uninstall-wubi.exe
(hidden files are set to viewable)

Interestingly, this change to wubildr also changed the result of:

grub> ls

from: (hd0) (hd0,1) (hd0,2)
to: (memdisk) (hd0) (hd0,msdos1) (hd0,msdos2)   #I'm pretty sure, this is what it said

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> Upon updating wubildr, the grub version changed to: GNU GRUB version 1.99~rcl-13ubuntu3

grub> echo $root
memdisk

C:\ubuntu\ only contains:
   install\
   winboot\
   Ubuntu.ico
   uninstall-wubi.exe
(hidden files are set to viewable)

Interestingly, this change to wubildr also changed the result of:

grub> ls

from: (hd0) (hd0,1) (hd0,2)
to: (memdisk) (hd0) (hd0,msdos1) (hd0,msdos2)   #I'm pretty sure, this is what it said

You're missing your C:\ubuntu\disks directory. This contains the virtual disks Wubi requires. The fact they are missing indicates most likely that there was some ntfs corruption and Windows has auto repaired and either deleted them or moved them to a hidden C:\FOUND.000 folder.

This corruption can occur by hard shutdowns - instead if you think it's locked up it's best to use Alt+SysRq R-E-I-S-U-B to safely reboot.

So, to try to repair go and look for those C:\FOUND.??? folders and see if you can find the missing files. The most important is the root.disk (although it could be renamed to something generic - it's the big one matching the size of your install).

If you find swap.disk and root.disk copy them back into C:\ubuntu\disks\
If you find the whole \disks folder, copy that back.

---

### Post by tdp2110 on 2011-05-13
uh oh ... No sign of these files/folders (hidden files are indeed set to viewable). Does this mean I'm Micro$crewed?

---

### Post by bcbc on 2011-05-13
Yeah, pretty much...

You could try running chkdsk, but it seems that windows has already auto-repaired the corruption. Anyway, give it a try... go to Computer, right click on C:, Properties, Tools, Check disk for errors, fix automatically. You'll need to reboot to complete. See if that found anything.

---

### Post by tdp2110 on 2011-05-13
Ran CHKDSK, no change

---

### Post by tdp2110 on 2011-05-13
Oh well, I guess I'll reinstall Wubi
Hopefully next time I won't be such a n00bie.

Thanks again for your help--you're a true Ubuntu ninja!

---

### Post by bcbc on 2011-05-13
> **tdp2110 said:**
> Oh well, I guess I'll reinstall Wubi
Hopefully next time I won't be such a n00bie.

Thanks again for your help--you're a true Ubuntu ninja!

No prob!  

If it hangs up on you again there may be some hardware incompatibility - perhaps you need a special kernel boot override option.  It doesn't happen very often that the whole disks directory goes missing, but I have seen it reported a few times.

Post your specs if you like... and I'll see if there's any info on it. 

Good luck!

---

