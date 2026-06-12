---
title: "Grub Loop"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Heretrix on 2010-04-04
Whenever I start my computer "GRUB" flashes on the screen, and then reboots. It just keeps doing this over and over and over and I have absolutely no control. The only way I can bypass it is if I use an Ubuntu LiveCD.

Any ideas?

Oh, and I don't have Windows restore CDs.

---

### Post by prodigy_ on 2010-04-04
More info needed. Boot from Live CD run [this script](http://bootinfoscript.sourceforge.net/). Post the output here.

---

### Post by Heretrix on 2010-04-04
Results are attached.

---

### Post by prodigy_ on 2010-04-04
Bootloader couldn't be detected - probably MBR is corrupted. Since you don't have Linux installed, use [this guide](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD).

---

### Post by Heretrix on 2010-04-04
Something bad always happens when I step anywhere near Windows, ah well, giving the tutorial a go.

-- Edit --

So just rewriting the MBR (bootrec.exe /fixmbr) fixed the problem. But thank you for sending me to that guide, I've really benefited now from getting that Restore CD.

---

