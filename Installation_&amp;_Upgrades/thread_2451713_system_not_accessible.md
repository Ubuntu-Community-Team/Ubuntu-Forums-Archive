---
title: "system not accessible"
date: 2020-10-09
forum: Installation &amp; Upgrades
---

### Post by peter-w-howes on 2020-10-09
Hello all,
I'm having an issue booting, I did edit the grub config not so long ago to remove some debugging for Plymouth that was enabled and also to try and remove traces of errors with /dev/SDB which doesn't actually exist on the system but it's somehow referenced in it
That was a week or so ago, since I have powered off the system with no problems, up until today when it could no longer find /Dev/mapper/Ubuntu--vg-root and fell back to busybox. There are also some errors before in the boot process about acpi 

I tried boot-repair but no luck, the paste output is here:

[https://paste.ubuntu.com/p/VFP8x9XfM3/](https://paste.ubuntu.com/p/VFP8x9XfM3/)

Any help appreciated!
Thanks,
Peter

---

