---
title: "Reinstall ubuntu 12.04"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by donny.davis on 2013-04-28
I want to install oracle 11g Express edition on my ubuntu 12.04.
but only 64 bit download is available and my OS has 32-bit.
so i decided to reinstall Ubuntu with a 64-bit version.
But me concerned about My files and videos in Home directory
(those are very important and also i do not have a External hard disk)

Please suggest a method of reinstalling my OS without losing my data.

Thank you.

---

### Post by Virtuality314 on 2013-04-28
You could compress the files and upload them to a cloud storage like Ubuntu One, Google Drive or Dropbox.

---

### Post by Warren Hill on 2013-04-28
If your data is important to you backup.  You can then install fresh and restore your data from the backup.

External USB drives are not expensive and hardware can fail at any time without warning.

---

### Post by donny.davis on 2013-04-28
ya backup is good idea.
But what will happen if i use a Live USB and try to install on '/' and on format option unchecked ??

---

### Post by Virtuality314 on 2013-04-28
Right...

Make a seperate partition with GParted which will be big enough for your data. Then copy over your files or use something like RSync (or Grsync if you don't like cmd) to backup your data.
Then, in the installation process of Ubuntu, make sure you do not format or use that partition which has your data on it.

And seriously consider getting an external hard-drive, as your computer could overheat or fail at any time.

---

