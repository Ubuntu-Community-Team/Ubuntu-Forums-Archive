---
title: "Can't boot Karmic. &quot;error: no such device&quot;"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by wyclif on 2010-04-27
Hi all, I just tried installing Karmic (9.10) on an IBM ThinkPad t40. I've run various Linux distros on this laptop without incident, but now after doing a full install, I can't boot the system.  Here's the error I get:

[INDENT]error: no such device (then a long string that looks like UDMI)[/INDENT]

I have access to the GRUB default menu and the GRUB prompt. I've read the GRUB documentation as well as various threads here, but I honestly don't know what I'm missing here.

---

### Post by oldfred on 2010-04-28
Is this error when you try to boot windows. Did you install grub to more than just the MBR?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

If you have grub in the windows partition see this:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Or grub files in the windows boot or Boot.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

