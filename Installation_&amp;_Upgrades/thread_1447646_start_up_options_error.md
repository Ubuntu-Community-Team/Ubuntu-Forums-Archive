---
title: "start up options error"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by alan.p on 2010-04-05
I am a newbie and after installation, I have a choice to either start Ubuntu or Windows.
When I select Ubuntu it gives me an error msg:

Windows failed to start.  A recent hardware or software change might be the cause.
To fix the problem:
1. Insert windows install disc and restart
2. Choose lang settings and click next
3. click repair computer

If you do not have this disk, contact your system admin or computer mang. for assitance.

File: \wubildr.mbr
Status: 0xl000000f
Info:The selected entry could not be loaded b/c the application is missing or currupt.

However, when first selecting windows it gives me the option again to choose between Ubuntu and Win, and then Ubuntu starts just fine. 

Is there a way to fix?

---

### Post by oldfred on 2010-04-05
This is usually the fix:

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

