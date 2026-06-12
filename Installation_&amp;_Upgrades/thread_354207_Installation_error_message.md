---
title: "Installation error message"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by chris_lenney on 2007-02-05
On trying to install ubuntu I get the following error message in the early stages of installation:

"The ext3 file system creation in partition #1 of IDE1 Master (hda) failed"

Anyone have any idea what this means and how i go about sorting it out?

Cheers

Chris

---

### Post by jpeddicord on 2007-02-05
Try restarting your PC and running it again. Sometimes the installer will try to do things too early in the installation with your drive and it will not mount correctly.

If it still happens, you can try running the following in a terminal to refresh that part of the drive.

```
sudo umount /dev/hda1
```

Jacob

---

