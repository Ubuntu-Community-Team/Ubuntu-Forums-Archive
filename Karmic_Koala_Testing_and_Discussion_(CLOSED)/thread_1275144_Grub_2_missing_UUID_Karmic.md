---
title: "Grub 2 missing UUID Karmic"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kismet on 2009-09-25
I just installed 9.10 alpha 6 and it worked fine for a couple days, but now it can't find the ext4 partition it was installed on.

It fails because it can't find the device by uuid. It then drops to ASH.

In ash, I goto /dev/disk/by-uuid/ and the partition isn't there.

I can boot into my old 9.04 install and mount the partition there, and I can see all the files. In the grub.cfg it lists a uuid for the partition, but even when I boot into 9.04 it doesn't seem to get a uuid. 

I'm thinking I could probably install grub 1.5 and just point it to /dev/sda3 in order to boot up into 9.10, but I was wondering if anyone knew why this was happening, and how I can fix grub 2/uuid problem for 9.10.

---

### Post by Kismet on 2009-09-26
So no one has insight on to why a partition would not get a uuid?

---

