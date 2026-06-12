---
title: "Live CD and NVraid problems"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by dave on 2008-01-13
I can't find an answer to this question (though it's probably somewhere)...

I am using NVraid 5 setup, but ubuntu is not able to detect the array.  I have followed the fakeRaid guide on the wiki to no avail.

In the bios I have my 3 harddrives setup in raid 5, it says the array is active.  When I get into the livecd I don't see the drives, and running dmraid (with any options) gives the error: "no block devices found"

I'm out of ideas, and am really thinking about buying a new mobo with pci-ex16 so I can buy one of them 8sata port adaptec hardware cards.  Anyone have ideas how to make nvraid work?

--
dave

---

### Post by Pumalite on 2008-01-13
[http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid](http://gentoo-wiki.com/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid)

---

### Post by dave on 2008-01-13
I've been through that one as well.  I have read through a bunch of docs, but none mention anything about "no block devices found" error.  I just tripple-checked, and my raid is set up right (in bios) but I can't figure out anything about how to get ubuntu to see the raid.

--
dave

---

### Post by Pumalite on 2008-01-13
What do you have installed in your Raid?

---

### Post by dave on 2008-01-13
Nothing.

It's blank.  3 x 500gb drives.

--
dave

---

### Post by Pumalite on 2008-01-13
Disable it in BIOS then and you'll be a lot happier.

---

