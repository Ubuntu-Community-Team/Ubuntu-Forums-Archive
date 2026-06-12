---
title: "Problem installing VirtualBox addins to Lucid"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sendervictorius on 2010-04-03
I installed Lucid Beta 1 on VirtualBox 3.0.8 running on Ubuntu 9.10 amd64 Desktop.

VBoxLinuxAdditions-amd64.run fails when building the kernel module. I get a compile error:
```

/tmp/vbox.0/cmc.c: In function ‘vboxadd_hgcm_callback’:
/tmp/vbox.0/cmc.c:34: error: ‘TASK_UNINTERRUPTIBLE’ undeclared (first use in this function)

```Is there something I need to do to get this thing compiling correctly?

---

### Post by howefield on 2010-04-03
Not sure about that specific error, but were it me, I'd install the current version of Virtualbox (3.1.6) which will use an updated set of guestadditions.

Might help, might not.

---

### Post by Sendervictorius on 2010-04-13
Yes, I removed the old VBox, downloaded and installed the VBox 3.1.6 deb, and it worked.

---

### Post by null_pointer_us on 2010-04-13
You may want to install DKMS, which will automatically recompile the guest additions' kernel modules for you whenever you update the kernel.

---

