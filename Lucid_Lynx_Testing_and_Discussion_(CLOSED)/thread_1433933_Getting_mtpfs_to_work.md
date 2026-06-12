---
title: "Getting mtpfs to work"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Jordanwb on 2010-03-19
So almost a month ago I submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/mtpfs/+bug/528802") for mtpfs and nothing has happened. Interestingly enough a [similar bug report]("https://bugs.launchpad.net/ubuntu/+source/mtpfs/+bug/200522") for mtpfs was filed almost 2 years ago, similarly, nothing ever became of it. I tried downloading the mtpfs package from the jaunty (the only release where mtpfs worked, I even wrote a working udev rule to automount) repo but it didn't work either. So what do I do know?

I tried downloading the source code from the author's site and did the ".configure && make && make install" but the first bit failed due to fuse, libmtp, id3tag and mad weren't installed (they were, just under another name). So I didn't bother trying to understand the 3500+ line shell file.

Before anyone asks what's wrong with gphoto2: It doesn't work either. I tried copying a photo and a song, neither showed up. When I unmount my Zen, gvfs-gphoto2 crashes.

*Edit*

Hey another [mtpfs bug]("https://bugs.launchpad.net/ubuntu/+source/mtpfs/+bug/192908") report which fell through the cracks. Also interesting: this user also has a Creative ZEN.

---

### Post by gordintoronto on 2010-03-19
Nautilus doesn't see the Zen as if it were a hard drive?

---

### Post by Jordanwb on 2010-03-19
> **gordintoronto said:**
> Nautilus doesn't see the Zen as if it were a hard drive?

Sort of. I can browse the Zen like a folder using gphoto2 but it's not actually mounted (no /dev node)

---

