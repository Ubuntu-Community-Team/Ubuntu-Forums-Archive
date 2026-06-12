---
title: "Failed to bootup ubuntu 8.04.4 after upgrade with wubi installation mode"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by drzhf on 2011-11-09
hi,

I just installed the ubuntu 8.04.4 with wubi into Windows XP's C: partition with NTFS, it works fine.

but after I update the ubuntu 8.04.4 to latest kernel verison, the grub failed boot the new kernel up, neither recovery mode.

the message shows that the "error code = 21" and ask me to do "chkdsk /r" on windows; but it still raise same error after I did it.

any advice for that?

Regards,

---

### Post by bcbc on 2011-11-09
Is the root.disk still there? C:\ubuntu\disks\root.disk

There aren't many people using such an old release for Wubi and it uses a different version of grub so I'm not up to date on what the error might be. Probably best to search for threads around 2008 with error code 21 ?!

---

### Post by Rubi1200 on 2011-11-11
> **drzhf said:**
> hi,

I just installed the ubuntu 8.04.4 with wubi into Windows XP's C: partition with NTFS, it works fine.

but after I update the ubuntu 8.04.4 to latest kernel verison, the grub failed boot the new kernel up, neither recovery mode.

the message shows that the "error code = 21" and ask me to do "chkdsk /r" on windows; but it still raise same error after I did it.

any advice for that?

Regards,
Hi and welcome to the forums :)

Is there a particular reason for installing such an old version of Wubi?

I think you would be better off using the latest version unless your hardware does not support it.

---

