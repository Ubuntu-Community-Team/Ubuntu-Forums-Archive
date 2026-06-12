---
title: "Disk Check Failure."
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MasterNetra on 2010-03-16
Disk checked KO my testing machine, it gets to the point where it says there is errors but doesn't budge any further. Even left it on overnight and it was still at that same spot the next morning. Pressing C to skip when it does its run doesn't work either.

---

### Post by JCoster on 2010-03-16
Happened to me yesterday.
Boot with a LiveCD and run fsck as root on the drive from terminal.

---

### Post by MasterNetra on 2010-03-16
> **JCoster said:**
> Happened to me yesterday.
Boot with a LiveCD and run fsck as root on the drive from terminal.

Never did that before. Is it something like:

```

sudo fsck /**dev**/sda1

```

?

EDIT: Nevermind figured out its /**dev**/sda1 (for me anyway)
-Thanks that fixed it.

---

