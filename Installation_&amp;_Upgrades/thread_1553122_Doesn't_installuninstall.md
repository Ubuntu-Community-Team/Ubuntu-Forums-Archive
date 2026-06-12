---
title: "Doesn't install/uninstall"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by VespaHive on 2010-08-14
I installed ubuntu by using Wubi to try it out. When I restatered and booted up ubuntu it said claimed to be finishing up installations which was taking nearly 1.5 hours of getting nowhere before I got frustrated and shut it off. I wen't back on windows to see if a re installation would be better. But my computer didn't seem to agree on that and wouldn't uninstall it. So I manually deleted the files myself. Now when I start up my computer I still see the choice to boot up kubuntu but yet there is no kubuntu if I select it. Any ideas how to get rid of the selection and why wubi didn't work? Not even live CD's are working on my computer.

---

### Post by lemming465 on 2010-08-15
> **VespaHive said:**
> ... So I manually deleted the files myself. Now when I start up my computer I still see the choice to boot up kubuntu but yet there is no kubuntu if I select it.
With a WUBI install the first thing the computer runs is the windows boot loader.  If you select the kubuntu option, that tries to transition to a Linux boot loader (GRUB).  However, you deleted the underlying grub files, so that now fails.

> **VespaHive said:**
> Any ideas how to get rid of the selection 
If your windows install is XP or older, remove the kubuntu entry from C:\boot.ini using a text editor such as notepad.  You might have to change attributes on the file to make it visible and writable.  For Vista or Windows 7, they went to a new boot loader with a binary DB file; I suggest deleting the stale kubuntu entry using ["easybcd"]("http://neosmart.net/dl.php?id=1").

> **VespaHive said:**
> ... why wubi didn't work? Not even live CD's are working on my computer.
If live CD's don't work, then whatever underlying hardware issue is preventing those is probably the same one that is messing up the WUBI installs.  Sorry!  Your best bet is try a different distribution or release. E.g. an older version of Ubuntu, or for the adventurous the alpha-3 release of the future maverick meerkat 10.10.  Or something else entirely; if you a KDE fan that might be OpenSuSE.

---

