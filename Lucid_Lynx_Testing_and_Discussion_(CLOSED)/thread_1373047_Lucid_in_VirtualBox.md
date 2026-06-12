---
title: "Lucid in VirtualBox"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gabo.cr on 2010-01-05
Is it valid to try Lucid Lynx Alpha1 in VirtualBox?
Are there any recommendations?

---

### Post by gabo.cr on 2010-01-05
Ups!
I found the answer.

> Is testing Lucid in a virtual machine useful?

For testing kernels, X, and anything that interacts directly or at a low level with hardware, it's hard to produce useful bug reports. If filing bug reports from virtual machine installs, don't forget that they will be reports about Ubuntu failing to work on that particular virtual machine, and don't forget to indicate that you're testing on a virtual machine in your bug report. While virtual machines are a valid use case, bugs from real hardware are much more useful. If, however, you're only looking to test high-level functionality such as userspace applications, user interfaces, documentation, translations and so on, virtual machines are mostly fine.


---

