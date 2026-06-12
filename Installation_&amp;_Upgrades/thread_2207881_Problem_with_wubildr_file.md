---
title: "Problem with wubildr file"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by omar_muhtaseb on 2014-02-25
Hi everybody, I'm a beginner with linux staff. I had a linuxmint on my laptop as a secondary OS, but I formatted the laptop and the linux is still exist but it gives me that I have to repair linux and gives me the file linux/winboot/wubildr.mbr. So any help please??

---

### Post by grahammechanical on 2014-02-25
> [COLOR=#000000]I formatted the laptop and the linux is still exist[/COLOR]

That should be impossible. A format of the hard drive will delete everything on the drive. Please explain what you did.

> [COLOR=#000000] linux/winboot/wubildr.mbr. [/COLOR]

That means that you installed using Wubi exe. Linux was installed inside Microsoft Windows in a similar fashion to installing any Windows application. My best guess is that you should use the Windows Add/Remove Programs utility to uninstall Linux and then re-install Linux.

Regards.

---

### Post by Mark Phelps on 2014-02-25
What might be the case, is that you're seeing a GRUB message -- presuming that you installed GRUB to the MBR of the hard drive, and now that you've reformatted the drive, the Linux partition containing the remainder of the GRUB code is gone, but there is still a bit of the GRUB code resident in the MBR.

So basically, you can't "repair linux" because it is gone.  You would need to reinstall it from scratch.

---

