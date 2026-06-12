---
title: "How to reformat &amp; install Ubuntu from within Windows 2000 Professional?"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by SWriverstone on 2008-06-22
I inherited an old Sony Vaio PCG-SR33 notebook that I want to install Ubuntu on.

The notebook does NOT have any kind of CD-ROM or floppy disk drive. (They were separate, plug-in devices that are long gone for some reason...) It has a single USB port.

I downloaded the CD image and burned it (actually created the CD from the image, didn't just burn the .iso file to CD). Then I connected an external CD drive (via USB) which Win2000 recognizes fine.

I checked the Sony Vaio notebook's BIOS settings, and it *is* set to boot from CD before hard disk. But I cannot get the system to boot from the Ubuntu CD. I don't believe this is due to a problem with the CD...but with the fact that the system does not in fact recognize the external CD drive until Windows 2000 is loaded (catch-22).

Is there **any** way to reformat the C: drive and install Ubuntu starting from *within* Windows 2000? I've explored the files on the Ubuntu CD to no avail.

Otherwise, I feel like I'm screwed---I really want to try out Ubuntu...but can't get it installed! All I can do on this notebook is launch Windows 2000.

Thanks,
Scott

---

### Post by illuminatifire on 2009-10-06
Try Xubuntu Jaunty (9.x) release. I usually had problems installing linux copies on my sr33 and usually had to go through this elaborate process but this version doesn't halt midway after detecting the cdrom. Plus its a little lighter than the Ubuntu release.

---

### Post by Mark Phelps on 2009-10-06
> **SWriverstone said:**
> The notebook does NOT have any kind of CD-ROM or floppy disk drive.  ... Then I connected an external CD drive (via USB) which Win2000 recognizes fine.
But I cannot get the system to boot from the Ubuntu CD. I don't believe this is due to a problem with the CD.
That's because the PC apparently does not have the option to boot from an external drive -- which I'm guessing you're connecting via USB.

> Is there **any** way to reformat the C: drive and install Ubuntu starting from *within* Windows 2000? I've explored the files on the Ubuntu CD to no avail.

According to the Wubi Guide, Windows 2000 is supported, so you can try starting Win 2K, with the external CD drive connected, launch the Ubuntu CD, and see if it offers to install "side-by-side"  (i.e., inside Windows).

---

