---
title: "new to ubuntu, need help asap please"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by vegetto71 on 2009-12-01
hello i am new to ubuntu and order ubuntu 9.10 desktop edition for my pc and its not installing right, it keeps  saying mountall filesystem could not be mounted: /lib/init/rw and before that it lists alot more, i think the entire filesystem that is supposed to be installed, my computer did have xp home edition on it but was stuck in a reboot glitch which i could not fix without my windows cd i didn't have here right now so i thought if i installed ubuntu until i get my windows xp cd back it would at least be fixed with a OS that doesn't fail to boot up, my computer is a hp pavilion a250n pent 4 HT 2.6, 512mb ram, not sure what other into may be need for someone to help but please just post it and i'll answer, thank you

---

### Post by Bunnybugs on 2009-12-01
> **vegetto71 said:**
> hello i am new to ubuntu and order ubuntu 9.10 desktop edition for my pc and its not installing right, it keeps  saying mountall filesystem could not be mounted: /lib/init/rw and before that it lists alot more, i think the entire filesystem that is supposed to be installed, my computer did have xp home edition on it but was stuck in a reboot glitch which i could not fix without my windows cd i didn't have here right now so i thought if i installed ubuntu until i get my windows xp cd back it would at least be fixed with a OS that doesn't fail to boot up, my computer is a hp pavilion a250n pent 4 HT 2.6, 512mb ram, not sure what other into may be need for someone to help but please just post it and i'll answer, thank you

Did you remove all the partitions and used it as a new one for Ubuntu? The guess I make is that your NTFS filesystem has crashed, and Ubuntu needs a harddrive.... If your harddrive is broken, XP won't work, and Ubuntu neither. But, before I'm sure about that, try to give us some more information... info about what the screen tells you, etc, etc... Or even better, try to make a picture of the bootscreen, and upload it to your forum-post from another computer!

---

### Post by nothingspecial on 2009-12-01
Does it offer to drop you to a maintinence/recovery shell.

If so list your partitions like so

```
fdisk -l
```

Then run fsck on all the partitions you can

```
fsck /dev/sda1
``` etc

If not boot from your live cd and follow the same procedure.

If it offers to fix anything, fix it.

---

