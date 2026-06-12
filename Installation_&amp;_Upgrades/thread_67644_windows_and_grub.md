---
title: "windows and grub"
date: 2005-09-20
forum: Installation &amp; Upgrades
---

### Post by uten on 2005-09-20
ok today i installed ubuntu on my laptop. unfortunately it overheated during installation, right after partitioning. i let it cool down and continued the install later. but the grub config tool did not pick up windows xp home. how can i add a space for it to my menu.lst config file, i cant figure out how the hd(0,0) thing goes. here is how my partitions are setup:

1. ext3 -/
2 ext3 -/otheros
3. fat32 - /windows
4. fat32- /storage

i figure during the botched installation that the mbr was erased, so grub picked up no sign of windows.

---

### Post by Borusa on 2005-09-21
[http://www.frankandjacq.com/ubuntuguide/5.04/#addwindowsentrygrubmenu](http://www.frankandjacq.com/ubuntuguide/5.04/#addwindowsentrygrubmenu)

For your setup, the entry would need to be 
```

root (hd0,2)

```

(it's the partition number minus one)

---

### Post by uten on 2005-09-21
[QUOTE=Borusa][http://www.frankandjacq.com/ubuntuguide/5.04/#addwindowsentrygrubmenu](http://www.frankandjacq.com/ubuntuguide/5.04/#addwindowsentrygrubmenu)

For your setup, the entry would need to be 
```

root (hd0,2)

```

(it's the partition number minus one)[/QUOTE]
 kool, thnx

---

