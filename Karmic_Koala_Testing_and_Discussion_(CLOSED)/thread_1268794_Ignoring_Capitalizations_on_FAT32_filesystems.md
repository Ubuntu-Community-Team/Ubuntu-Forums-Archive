---
title: "Ignoring Capitalizations on FAT32 filesystems"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fraser_m on 2009-09-17
Has the way capitalizations and symbols are handled on FAT32 filesystems changed since Jaunty? When I rsync a folder to a FAT32 drive, file and folder names such as "IT" and "X&Y" are changed to "it" and "x&y". It's as if it doesn't like upper case letters anywhere but the start of words.

It's annoying, because every time I rsync to update the folder, it deletes them, and resyncs them with re-capitalized words.

Is there any way to retain them?

---

### Post by cariboo on 2009-09-17
It's a problem with fat32 file systems, it seems to have a mind of its own. :) I've had times where it changes lowercase to uppercase when transferring files.

Edit: Try remounting the fat32 partition with this option:
 -o shortname=winnt

---

### Post by fraser_m on 2009-09-17
This makes it work perfectly. It's a removable SD card, though, so is there any way of making these changes permanent?

---

### Post by MacUntu on 2009-09-17
See [http://ubuntuforums.org/showthread.php?t=1257499](http://ubuntuforums.org/showthread.php?t=1257499)

---

### Post by fraser_m on 2009-09-17
So there's no way to do it automatically without recompiling the kernel?

---

### Post by MacUntu on 2009-09-17
Sorry, I don't know.

---

