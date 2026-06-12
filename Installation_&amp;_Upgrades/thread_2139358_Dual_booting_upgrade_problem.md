---
title: "Dual booting upgrade problem"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by ScottishGirl on 2013-04-26
HI :)

This afternoon I decided to do a system upgrade from 12.04 to 12.10.  I ran the update manager and everything downloaded and updated fine.  However, when I restarted and chose the 'Ubuntu' option from the dual boot options nothing happened.  I got the Ubuntu splashscreen then nothing but a dark screen.  I did think that perhaps my HD hadn't recognised the two partitions, but that should have meant that Windows 7 should have booted, however I definitely saw a dual boot choice screen. I think that problem is that the upgrade removed the boot manager from the Ubuntu partition.  Is there a way to get the Ubuntu partition to boot?  I have GParted but I am reluctant to use it as I don't want to risk removing the Windows 7 partition.

I have no access to the terminal so I can't post any system information.

---

### Post by fantab on 2013-04-26
Sounds like a Graphics issue. What Graphics do you have on your machine? And What bootloader are you using?

Try 'NOMODESET' option and see if Ubuntu boots. If it boots check for 'additional driver' and if available then you can install 'em. Read: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ScottishGirl on 2013-04-27
Hi fantab

I have managed to 'solve' the problem.  I got out my old 12.04 DVD and reinstalled that.  This is the third time that I have used the update manager to update my system and it has never worked.  Thanks for your advice fantab.  :)

---

### Post by fantab on 2013-04-27
I always do a clean install as opposed to upgrade from update manager. I'm glad that you could solve your problem by doing a clean install.

Don't forget to Mark the thread as 'Solved'.

---

