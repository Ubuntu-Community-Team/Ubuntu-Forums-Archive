---
title: "removeable disk - fstab"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by stephan0h on 2010-07-04
Hello,

I've got a removeable disk which I want to mount on startup automatically at mountpoint "/backupsystem". If' it's not there I would like to have no error message.
Actually after upgrading to 10.4 I get the message: Continue to wait; or press S to skip mounting or M for manual recovery.". But I don't wand this if the disk is not there that's OK for me.

How would I configure fstab to achieve this?

Thanks,
Stephan

---

### Post by darkod on 2010-07-04
I don't think you can configure not to have the message when the disk is missing. If you want auto mount, then it will always show the message when the disk is not there (it can't be mounted).

You could simply mount it when ever you need it, instead of auto mount. In that case there will be no message when the disk is not there because there is no entry in fstab for it.

Besides, if the disk is not always there, why the auto mount entry at all?

---

### Post by stephan0h on 2010-07-05
I want it just for convenience - and because it worked before.

---

