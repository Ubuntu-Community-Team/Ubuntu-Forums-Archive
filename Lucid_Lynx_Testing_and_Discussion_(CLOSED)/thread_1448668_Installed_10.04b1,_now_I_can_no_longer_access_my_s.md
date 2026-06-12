---
title: "Installed 10.04b1, now I can no longer access my swap"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Random21 on 2010-04-06
I have my drive partitioned so that I have a stable OS and a new OS that I can tinker with.  The two OS's share a 10 gig swap partition.  I have Karmic as my stable and put a fresh 10.04b1 on the other partition.  I decided that having my drive encrypted sounded sweet.  It stalled while it was trying to clean my swap so I simply rebooted.  Booted into Lucid just fine but now when I boot into Karmic it tells me it cannot mount or cannot access my swap partition.  I couldn't find help anywhere else and I don't have the time to spend a couple of hours reinstalling Lucid w/o encryption.

tl;dr
Karmic and Lucid
Lucid encrypted swap
Karmic cannot access

I'd be happy to give more information if needed.  Just tell me how to do it because I'm fairly new to this so I don't know all my commands and where all my files are.

Thank you

---

### Post by jaakan on 2010-04-06
I have not tried this but it might help

[https://we.riseup.net/debian/encrypted-swap]("https://we.riseup.net/debian/encrypted-swap")

[https://help.ubuntu.com/community/EncryptedFilesystemHowto3]("https://help.ubuntu.com/community/EncryptedFilesystemHowto3")

[https://help.ubuntu.com/community/EncryptedFilesystemHowto]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")

---

### Post by Random21 on 2010-04-07
I finally figured out the problem.  The UUID was changed during the Lucid install.  I thought UUID was only changed during a repartition.

---

### Post by QLee on 2010-04-07
> **Random21 said:**
> I finally figured out the problem.  The UUID was changed during the Lucid install.  I thought UUID was only changed during a repartition.

The UUID is set when the partition is formatted, not when it is partitioned.

---

