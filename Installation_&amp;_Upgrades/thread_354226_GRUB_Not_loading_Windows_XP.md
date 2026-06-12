---
title: "GRUB Not loading Windows XP?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Corgana on 2007-02-05
I'm trying to put my Windows XP partition in Menu.lst, but everything I try dosen't seem to work, How can I know what settings to put in the list?

Right now, I have Ubuntu on the first partition, (hda1) and ntfs windows on the second (hda2). it's all one hard drive.

```

title 		Windows
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root		(hd0,1)
chainloader +1

```

this is what i have right now, I stole it from some other guy, obviously it dosen't apply with mine.

Any thoughts? Thanks in advance :)

---

### Post by reiki on 2007-02-05
#1 try it without the maps, you may not need them.
#2 add one line after the chainloader +1 line... on that line only the word "boot" without the quotes.

---

### Post by glotz on 2007-02-05
That depends how your partitions are set up. You can use e.g. System > Administration > Disks to find out.

---

### Post by logos34 on 2007-02-05
> **Corgana said:**
> I'm trying to put my Windows XP partition in Menu.lst, but everything I try dosen't seem to work, How can I know what settings to put in the list?

Right now, I have Ubuntu on the first partition, (hda1) and ntfs windows on the second (hda2). it's all one hard drive.

```

title 		Windows
map 		(hd0) (hd1)
map 		(hd1) (hd0)
root		(hd0,1)
chainloader +1

```

this is what i have right now, I stole it from some other guy, obviously it dosen't apply with mine.

Any thoughts? Thanks in advance :)

You only need the 'map' lines if you are dual booting on two drives.

Try this:

> title        Windows
root        (hd0,1)  *or **rootnoverify (hd0,1)**
savedefault
makeactive
chainloader    +1

Your windows entry should be at the bottom in its own section ('Other operating systems'), separate from the Ubuntu kernel entries.  The reason is that if you put it in the ubuntu section the next time Automagic updates the kernel it will be deleted.

See [this link]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

