---
title: "Wrong icons in hard disk devices last upgrade"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by deflagmator on 2009-10-13
With last upgrade the places shows wrong icons for cdrom and hd mounted devices. 

have you experienced the same?

---

### Post by smb on 2009-10-13
Same problem. Also almost all files are marked with ubuntu one tick.

---

### Post by Boondoklife on 2009-10-13
> **deflagmator said:**
> With last upgrade the places shows wrong icons for cdrom and hd mounted devices. 

have you experienced the same?
I filed a bug for this:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/450610](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/450610)

---

### Post by Boondoklife on 2009-10-13
> **smb said:**
> Same problem. Also almost all files are marked with ubuntu one tick.

Ubuntu-sync check was reported: [https://bugs.launchpad.net/ubuntuone-client/+bug/450210](https://bugs.launchpad.net/ubuntuone-client/+bug/450210)

---

### Post by thecow on 2009-10-13
Ah, for some reason my Karmic has a green checkmark above all folders ha.  Not sure what to make of that

---

### Post by TeutonJon78 on 2009-10-13
+1 for me.

It seems odd that a change would affect both CD and floppy mapping, since they were always different icons, but now get mapped to iPod/MP3 player icons.

---

### Post by tekstr1der on 2009-10-13
Fix is committed:

```
devicekit-disks (007-2ubuntu2) karmic; urgency=low

  * 07-media-player-icon.patch: Fix stupid typo which caused _all_ devices to
    get marked as a media player.

```

Should be in the repo's soon.

---

