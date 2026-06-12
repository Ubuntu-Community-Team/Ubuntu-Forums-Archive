---
title: "Unistall Windows Vista from an Ubuntu/Vista dual-boot?"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by SimplyWillis on 2011-03-18
Hey everyone. I have a single hard-drive on a spare computer and I decided to try out Ubuntu on recommendation from a friend. I really like it now but at first I just dual-booted it, and now I want Vista gone. I know it's unnecessary to have just one OS but my hard-drive isn't particularly big and I'd prefer to have Ubuntu by itself. Can anyone tell me how to eliminate vista and leave Ubuntu as my sole operating system (I've all my files from computer on another computer so I don't have to worry about losing anything). Thanks in advance.

---

### Post by zvacet on 2011-03-20
Boot your Ubuntu live CD and with **gparted** remove Vista partition.On that unallocated place you can extend your Ubuntu.

---

### Post by kansasnoob on 2011-03-20
It would be best to first see the output of these two commands:

```
sudo parted -l
```

```
df -H
```

---

