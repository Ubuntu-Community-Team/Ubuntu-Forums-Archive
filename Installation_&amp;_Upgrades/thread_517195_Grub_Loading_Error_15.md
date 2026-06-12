---
title: "Grub Loading: Error 15"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by lwalper on 2007-08-04
I was having trouble with Edgy not wanting to play DVDs, so decided to upgrade to Fiesty 7.04 - apparently that was the wrong thing to do. Now, after re-installing 3 times I get a "Loading Grub: error 15" and the machine won't load software. Same problem even after re-installing each time. What's the deal?

I'm now booted from the installation CD. Have read on the forum various fixes. Have tried to use grub-install which just gives me a list of options for grub-install and doesn't actually do anything.

I was given this link [URL="http://forums.gentoo.org/viewtopic-p-3056992.html"]
http://forums.gentoo.org/viewtopic-p-3056992.html[/URL]
which was interesting reading, but completely over my head.

I've looked for the /boot/grub folder (for the menu.lst file -- it does not exist.

HELP!!

---

### Post by Pumalite on 2007-08-04
Quoted from the GNU/GRUB manual

    15 : File not found
        This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

Re-install Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Or use this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by lwalper on 2007-08-04
Ok, thanks, I'll try that. I've just downloaded the SuperGrub iso.

---

