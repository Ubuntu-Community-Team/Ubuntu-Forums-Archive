---
title: "Uninstallation Problems"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by raitosei on 2009-11-21
Not sure if this is the right place for this, but here we go.

I recently attempted to remove Ubuntu from my desktop (since my wireless adapter isn't compatible with it) via Windows 7's partition management program. I attempted to simply delete the partition, but I'm assuming this was a stupid thing to do, since now every time I turn on my computer, it says "GRUB loading, please wait...Error 22." I didn't realize it would no longer let me boot from Windows 7. Anyway, now I can't access Windows 7 on my computer, and I need to know how to fix this issue.

I'm running a Gateway desktop, if that helps any.

Thanks.

---

### Post by darkod on 2009-11-21
The first part was correct, you simply delete the ubuntu partition(s). After that once you have windows running you can just format that space with NTFS for use with windows.

Deleting the partition doesn't automatically erase grub bootloader from the MBR of the hard drive (Master Boot Record). You need to restore windows bootloader on the MBR. Boot with your win7 dvd and after the first screen where is asks about language selection, on the second screen close to the bottom there is something like Repair This Computer. Click there and follow the procedure, it will recognize your win7 installation and should just restore the bootloader.

---

### Post by raitosei on 2009-11-21
I don't have a Windows 7 DVD, I downloaded it from Microsoft.

---

### Post by darkod on 2009-11-21
Downloaded what, win7? And you didn't burn the image on a dvd? Still have the file on your comp?

You could use Ubuntu LiveCD and burn the win7 image on a dvd.

---

