---
title: "Error 13"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by snkngshps on 2009-04-08
I just ran some updates with Jaunty and it prompted me to restart. I accepted and now I can't boot the computer! This is the error I'm getting:

```
Boot from (hd0,0) ext4 6ef3621e-9e0e-4b8c-8d58-ef61a508becf

Error 13: Invalid or unsupported executable format

Press any key to continue...
```

I googled this error and it seems to be happening with people that are dual booting XP and Ubuntu and mess up their grub loader, but I'm only single booting Ubuntu and haven't messed with the grub loader at all. Any ideas?

---

### Post by miklcct on 2009-04-09
Boot into a working kernel and install GRUB2. (GRUB legacy does not support ext4)

---

### Post by JPorter on 2009-04-09
Wait, what?  I've been running Ext4 for some time and I'm not aware that I'm running Grub 2.

Maybe so, I dunno, but after doing an update this evening (which hard-locked in the middle of processing something with fonts) my system is now unbootable.  I get the "ata1: softreset failed (device not ready)", the usplash starts to do its dance, and then the system drops to busybox prompt and claims that /dev/disk/by-uuid/(my uuid) does not exist.  Which of course it does, and I can mount it directly within busybox.

Now the system does the same thing when I try to boot from a USB key as well, with the Jaunty beta loaded on it.  It's nuts.

Any ideas?

---

