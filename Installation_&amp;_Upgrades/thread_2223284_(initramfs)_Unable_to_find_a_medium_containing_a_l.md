---
title: "(initramfs) Unable to find a medium containing a live filesystem"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by will39 on 2014-05-10
I've got a Gateway DX4640, which I recently broke the installation of Windows 7 on.

I was planning to install Ubuntu 14.04 (to backup all my files and then reinstall Windows) until I came across this error:

```
(initramfs) Unable to find a medium containing a live filesystem
```

Can't seem to fix it, so I was wondering if you guys could offer some help.

---

### Post by slickymaster on 2014-05-10
Hi will39, welcome to the forums.

The first thing I advise you to check is whether you have a faulty disc or a corrupted download. Did you check the md5sum on the downloaded ISO? There's a link to the Ubuntu hashes [here]("https://help.ubuntu.com/community/HowToMD5SUM").

One other thing you should check is the DVD integrity before it boots. Start up with the DVD and as soon as you see the purple screen with the two icons at the bottom, tap the space bar, then choose your language, after which you'll see a menu with a disc check as one of the choices.

---

### Post by will39 on 2014-05-10
I actually messed up the partitions, but I fixed it now. Windows is up and running again. But thanks for the response!

---

### Post by slickymaster on 2014-05-10
No problem. As long as you have the situation fixed, that's all that matters.

---

### Post by will39 on 2014-06-09
I've reopened this thread because once again I need the Ubuntu installation to resize my partitions. 

I've tried the disk checker, and nothing seemed to happen. It just stayed at a black screen with the blinking underscore thingy, and after a few minutes, proceeded to the "Unable to find a medium containing a live file system" screen.

---

### Post by will39 on 2014-06-09
Ok, never mind again. I fixed it by enabling the "acpi=off" thing in the spacebar F6 menu.

---

