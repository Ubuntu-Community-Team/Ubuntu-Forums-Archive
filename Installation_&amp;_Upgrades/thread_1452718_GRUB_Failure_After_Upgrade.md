---
title: "GRUB Failure After Upgrade"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by RichC on 2010-04-12
Just tried upgrading 9.10 to 10.04 via internet on a dual boot system with Windows XP. I guess I made a mistake in choosing to keep my existing menu.lst during the upgrade. Now GRUB shows only selections for 9.10, 9.04, and Windows XP, and none of the non-Windows GRUB selections get me into a working UBUNTU environment. The system just quits or locks up. Is there anyway to rescue the UBUNTU system now?

---

### Post by oldfred on 2010-04-12
You mention menu.lst, were you still running grub legacy (0.97) with Karmic? I do not know if Lucid even knows what grub legacy is?

You may be able to manually boot by totally editing a boot entry , but I am not sure.

This will show what you have.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by RichC on 2010-04-12
Sorry, I don't know what grub legacy is. Right now I don't know how to get into a working Linux on my system. When I try to boot, GRUB does not show any listing for 10.04 and the other Linux selections that are listed in my GRUB (i.e. for 9.04 and 9.10) do not work. I can still boot up into Windows XP from the GRUB listing. Is there a way to edit GRUB from within Windows?

---

### Post by oldfred on 2010-04-12
No you cannot edit grub from windows. Windows does not even see the Ubuntu partitions although there are some drivers available that may let you do some things.

You need to use a liveCD, you can down load Ubuntu's desktop install or any of the many repair type CD's available that are based on linux.

---

