---
title: "[SOLVED] dual hard drive dual boot problems"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by werdna5225 on 2006-11-02
I have two hard drives, one with windows xp, and one with dapper.  Dapper is set as master and windows is set as slave.  I edited grub to show the windows drive but when I select windows I get error 21:  Selected disk does not exist.   Now what do I do? 

Here is a link to another thread that explains what I have already done.[http://www.ubuntuforums.org/showthread.php?t=285642]("http://www.ubuntuforums.org/showthread.php?t=285642")

---

### Post by confused57 on 2006-11-02
Maybe this link can help for your entry to boot Windows:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Make sure your hd jumper settings are correct and that the slave controller is enabled in bios.

---

### Post by werdna5225 on 2006-11-03
How do I enable the slave in bios?  I tried the links ang I did everything it said to do but I am still getting the same error message.  Any other ideas?

When I get to grub and select windows I get the screen:  Booting 'Windows XP'
rootnoverify (hd1,0)
savedefault
makeactive
Error 21:  Selected disk does not exist.

I have ubuntu set as master and it is on a Western Digital 80GB IDE drive.  Windows XP is on a Seagate 250 GB Ultra ATA-100 hard drive.  I have the Windows XP drive formatted to NTFS and I have 3 partitions, one for XP, onr for music, and one for everything else.

---

### Post by confused57 on 2006-11-03
> **werdna5225 said:**
> How do I enable the slave in bios?  I tried the links ang I did everything it said to do but I am still getting the same error message.  Any other ideas?

When I get to grub and select windows I get the screen:  Booting 'Windows XP'
rootnoverify (hd1,0)
savedefault
makeactive
Error 21:  Selected disk does not exist.

I have ubuntu set as master and it is on a Western Digital 80GB IDE drive.  Windows XP is on a Seagate 250 GB Ultra ATA-100 hard drive.  I have the Windows XP drive formatted to NTFS and I have 3 partitions, one for XP, onr for music, and one for everything else.
I assume you have the Windows drive jumper is set to "slave" or "cable select", if supported.
   You can check the if your slave drive is enabled, by entering bios during bootup by pressing a key(F1, F2, del, etc)...bootup screen should tell you which key to press.
Look for something like Primary IDE controller(or IDE1), my Dell has the Primary master drive designated as hd0 and the Primary slave drive designated as hd1...what I had to do was change the hd1 from "off" to "auto"( may be "enabled" in some bios).
Yours is probably different, but look for something along those lines...may or may not be your problem, but worth checking.

---

### Post by werdna5225 on 2006-11-03
I finally got it fixed.  I re-installed Ubuntu while I had both hard drives plugged in, windows is master and ubuntu is slave.I also put in a new cable cuz the other was messed up.  Thank You.

---

