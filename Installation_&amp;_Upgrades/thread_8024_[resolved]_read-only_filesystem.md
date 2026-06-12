---
title: "[resolved] read-only filesystem"
date: 2004-12-13
forum: Installation &amp; Upgrades
---

### Post by marwal on 2004-12-13
After installing Ubuntu alot of commands (and errors during startup) brings to my attention that this is a read-only filesystem.

Like "man slocate"
Cannot create temporary filename - filesystem read-only (i've translated it from swedish).

or

"slocate -u"
FATAL ERROR : slocate :create_db:fopen: *** read-only filesystem

modprobe during startup also gets "not allowed" all the time.

I sure don't want a read-only filesystem. I can think of a world of trouble for me with such a system.

I did nothing remmarkable during install. Went with defaults and let Ubuntu upgrade packages.

What should I do here?


(specs : Inspiron 9100, radeon 8700, 60 Gb HD, 3.2 Ghz P4, 512 MB DDR SDRAM)

---

### Post by marwal on 2004-12-13
I see the upgrading didn't go too well either. :roll:

Readin database ... dpkg: error
'libgsml' is missing final newline

I really don't wanna switch back to Mandrake 10. [-X

---

### Post by marwal on 2004-12-13
All worked out.
Reinstalled, using ReiserFS, manually added partitions (root and home) instead of autopartitioning, skipped update in post-install, rebooted and manually updated with apt-get.
Now it runs like clockwork. :D

---

