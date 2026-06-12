---
title: "Uninstalling ubuntu problems"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by cyrus221 on 2008-01-13
Im giving my old computer to my parents next week, and I asked them if they wanted to try something new. They are pretty familiar with windows xp, so I figured i'd take off my Ubuntu installation to make everything less confusing. I have ubuntu 7.10 installed, gutsy i believe, and im having a lot of trouble with the MBR(master boot record). This is how I set it up:

I have two harddisks, lets just say 70GB (windowsxp.primary partition) and 750GB(ubuntu). So, i don't have a WinXP CD, BUT i do have a Vista upg CD. When I set my BIOS to boot from CD, it tells me "Press any key to boot from cd or dvd..." then loads proceeds to load grub. I want to be able to boot straight into windows xp, as if it were preinstalled or something.

I downloaded Fixmbr.exe from [http://www.sysint.no/EN/Download.aspx](http://www.sysint.no/EN/Download.aspx), and tried to do a command prompt fix of my MBR( mbrfix /drive 0 fixmbr /yes) but it doesn't fix the grub problem. Is the problem that Im telling it to fix drive 0, when ubuntu is installed on the other HD?

if anyone has another way to do this, by all means please tell me. I need this fix fast.

---

### Post by Partyboi2 on 2008-01-13
try using super grub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

