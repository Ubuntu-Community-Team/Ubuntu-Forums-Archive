---
title: "Oops - 32bit installed instead of x64; what ..."
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-05-08
... can I do? Will installing x64 (Hardy) on the same partition import ALL migrated files???

Say 'Yes', please???

---

### Post by Moozillaaa on 2010-05-08
So I found out how it happened, since you asked ;)

I migrated a Hardy x64 install to another disk, doing the cp command - cp /dev/sdx /dev/sdy. But, I did it with the wrong  live Hardy disk  - it was a Hardy 32bit disk.

I'm surprised it went over at all. Everything booted fine afterwards, didn't even have to change UUID, only the GRUB entries. I DID notice that some stuff did NOT copy - browse history, FF settings, bookmarks...

So what can I now do?

---

### Post by Moozillaaa on 2010-05-09
bumpin' here...

---

