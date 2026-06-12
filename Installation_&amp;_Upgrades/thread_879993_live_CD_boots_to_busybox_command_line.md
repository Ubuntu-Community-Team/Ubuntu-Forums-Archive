---
title: "live CD boots to busybox command line??"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by stuque on 2008-08-04
I just tried running the Ubuntu 8.04 Desktop livecd, and instead of booting into a graphical desktop, it boots into the busybox (?) command-line.

I've never had trouble on this computer with any previous Ubuntu live cds. Just the current 8.04

Any suggestions how can fix this, or at least go about debugging it?

---

### Post by TreeFinger on 2008-08-16
I am running into the same problem. I'm going to try what some people at this link suggest: [https://bugs.launchpad.net/ubuntu/+bug/217616](https://bugs.launchpad.net/ubuntu/+bug/217616)

if it works I will update this thread.

--edit

The following worked for me:

You must add extra boot options, I believe it is F6. Although, I am not positive.

I added the following to the beginning of the line of boot options.
```

noapic acpi=off all_generic_ide pci=nomsi

```

I am posting this from the Live session.

Could anyone explain what those options did?

---

