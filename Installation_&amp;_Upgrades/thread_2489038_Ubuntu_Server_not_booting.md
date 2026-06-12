---
title: "Ubuntu Server not booting"
date: 2023-07-16
forum: Installation &amp; Upgrades
---

### Post by ubu-boot134-324 on 2023-07-16
Hi everyone!

I followed the instructions from here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That's why I opened this thread.

Here is my pastebin: [https://paste.ubuntu.com/p/tZPr4Z4Z58/](https://paste.ubuntu.com/p/tZPr4Z4Z58/)

Any help would be appreciated!

---

### Post by MAFoElffen on 2023-07-17
I didn't see a problem with any of the boot files, but...

Line 55 says:
```

SecureBoot enabled.

```
Have you didn't mention that you setup any MOK Key on the firs boot to enroll any signing keys for SecureBoot. Did you try entering the BIOS setup, disabling "SecureBoot", and see if it boots?

---

### Post by ubu-boot134-324 on 2023-07-17
This thread can be closed.
I'm sorry! Here is the full thread that explains my problem in detail: [https://ubuntuforums.org/showthread.php?t=2489056](https://ubuntuforums.org/showthread.php?t=2489056)

---

### Post by MAFoElffen on 2023-07-17
That really didn't explain anything fully(?) oldfred also asked if SecureBoot was enabled. I didn't see where you responded bsck anywhere to say where you found anything... But yo have marked this as "Solved".

I am curious, and ma asking what Solved your problem.

---

