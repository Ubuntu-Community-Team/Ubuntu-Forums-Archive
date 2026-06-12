---
title: "Kubuntu partitioning during install"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by reg-br on 2006-08-24
I have a HD with some fat32 partitions, i want to delete one of them to create the linux / and /swap partitions. Does anyone know if the kubuntu graphical installer can do it and if it preserves my other fat32 partitions ? (i have the desktop kubu-live cd)

---

### Post by orb9220 on 2006-08-24
Yes it will or you can also delete the partitions from windows so they show up as unallocated space to gpart during the install.

Or when they show up during the install just select partitions and delete then create your ext3 partition for root / and a swap partitiom twice the size of your ram.

---

### Post by reg-br on 2006-08-25
Ok, thanks for replying. ;) I pretend to install on an old cpu, only 256k ram, don't you think is better to allocate more swap space? Also i'm planning to put xubuntu after testing kde there (it was too slow). I think this partitioning tool also comes with xubuntu, correct ?

---

