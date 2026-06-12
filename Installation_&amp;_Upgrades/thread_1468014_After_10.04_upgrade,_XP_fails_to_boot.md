---
title: "After 10.04 upgrade, XP fails to boot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Thecheffer on 2010-05-01
Hi,
Firstly, apologies.... I am a complete ubuntu first-timer.  Installed v9 a couple of weeks back and have been causally mucking about with it since.  I managed to get XP and ubuntu running as a dual boot system (which was an achievement :lolflag:).

Anyway, i've upgraded to 10.04 - and already loving it.  However... my XP o/s no longer boots.  It use to prior to the upgrade.  Now, when the XP o/s is selected from GRUB2, I just get a series of bleeps and a flashing _.

Now, I am a complete novice.  I actually have no idea where to even begin trouble shooting GRUB2 (and i'm assuming its a problem with GRUB).
  
Can anyone give me any pointers at all - i.e what/where to check.

Thanks in advance (the first of many posts I fear....:) )

---

### Post by awam66 on 2010-05-01
How did you upgrade to 10.04?
Did you do a fresh install or an upgrade.
If a fresh install did you set your partitions correctly?

---

### Post by Thecheffer on 2010-05-01
> **awam66 said:**
> How did you upgrade to 10.04?
Did you do a fresh install or an upgrade.
If a fresh install did you set your partitions correctly?

Hi, cheers for the response. 
I performed an upgrade - after being prompted by the automatic Upgrade Manager.

---

### Post by SilentPirate007 on 2010-05-01
Do you have both OS's on the same hard drive (partitoned) or on seperate hard drives?

In either cases are you able to access windows from within ubuntu?

Perhaps you could try repairing grub?
[https://wiki.ubuntu.com/Grub2#Recove...20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by Ethangar on 2010-05-01
I'm afraid that I just ran into the same thing. I was pleasantly surprised when the upgrade went without a hitch. There were a couple settings that I had to tweek to get it back to the way that it was but only minor things.

I have my 9.10? The version where they changed to grub2. Can I use that to do any adjustments to grub or did they change it with 10.04? Reason being that my burner is a bit flaky and it might take me 6 disks to get a good copy.

---

### Post by Ethangar on 2010-05-01
Found the answer in another thread. I'm back in windows now so it worked for me.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by Thecheffer on 2010-05-02
> **Ethangar said:**
> Found the answer in another thread. I'm back in windows now so it worked for me.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Awesome - tried this method and my WinXP partition is now back up and running.

Thanks for all the replies

---

