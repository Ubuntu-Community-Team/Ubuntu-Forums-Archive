---
title: "Getting External Drives to &quot;Mount&quot; - when they refuse to!"
date: 2015-05-16
forum: MINT
---

### Post by mintynz on 2015-05-16
Running Mint 17.1, we have two external drives that fail to mount.

1 - a small laptop HDD with windows 7 - placed into a external enclosure box.

2 - a WD 750gb external with data files was running on a TV set top box (usb recorder) and now wont mount.

I've tried to follow some of the fixes for mounting drives but still getting lost. Both show up in Mint but both will not mount as they are. The small 2.5" will mount if I put it into a "Multi Dock" and restart but cant do that with the plastic cased WD750.

Can you help? Thought I could fix the problems with "Disks" program but cant seem to do it. OPtions are greyed out and most other fixes are via Terminal.


Thanks.

---

### Post by Bucky Ball on 2015-05-17
*Thread moved to **MINT**.*

Welcome. You can see them but they won't mount? How are you trying to mount them and what happens exactly when you try? Open a terminal and:

```
sudo mount -a
```

Please report any error messages. Presuming the Win drive is formatted NTFS. What is the other drive formatted in?

---

