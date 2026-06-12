---
title: "Upgrade to Heron from an encrypted partition"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by damatta on 2008-04-25
Hello,

I dual boot Gutsy Gibbon x64 and Windows XP x64 from the same HD. However, Gutsy was encrypted using the alternate CD. Are there any warnings for users in my situation? I fear losing my windows partition or messing up badly my Ubuntu during the upgrade procedure. I intend following these steps ([http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html](http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html)) and still have my encrypted partition in the end with my personal files in /home/desktop.

Any help is pretty much appreciated.

Thanks in advance

---

### Post by IamAcoconut on 2008-04-27
You are welcome :P

I've got the same situation. I'd make sure that nothing connected to encryption is listed as an **obsolete** package. I'll make a backup of **menu.lst** and compare it with the new file before rebooting, well at least the options, so I don't get stuck with splash. And first of all I'm downloading the LiveCD to see whether the distro works with my computer, 'cos - according to the poll in another thread - more often than not this LTS is malfunctioning seriously. 

If your /home is not a big thing, make a backup, to avoid f***ing with LiveCD to gain access to encrypted data.

***Bump***
I hope for someone more competent/experienced to have their say.

---

### Post by damatta on 2008-04-27
This thing of upgrading from an encrypted partition doesn't seem much reliable, not to someone with my skills. I had a backup of /home and some sys configs and i'm happily running Heron right now. And I suggest people in the same situation to do the same. At least for me, it was easier to spend some time reinstalling than fixing stuff.

---

### Post by IamAcoconut on 2008-04-30
But since you made a backup you could try the upgrade anyway, you had nothing to loose.
I can't go for it (make backup of everything) since my dvd burner's malfunctioning (it might be a system issue) recently... 

Well maybe someone else has come across the problem, and may give some advice. Or just say "go ahead".

Bump.

---

