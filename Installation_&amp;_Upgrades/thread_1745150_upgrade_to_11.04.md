---
title: "upgrade to 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by katzman2 on 2011-04-30
started the upgrade to 11.04 from version 10 (do not remember the release number) and got a message back that the root directory did not have enough space.  Need 400 meg.  Did the cleanup sudo apt-get clean and still could not get enough removed.  Cannot just go in and delete files outright.  What can I do to remove files?
Thanks
steve

---

### Post by mikewhatever on 2011-04-30
Can you post the outputs of the following commands:
```
df -h
dpkg -l | grep linux-image
```

Perhaps we can still find something to delete.

---

### Post by katzman2 on 2011-04-30
dpkg -l | grep linux-image
rc  linux-image-2.6.32-21-generic        2.6.32-21.32                                      Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.32-27-generic        2.6.32-27.49                                      Linux kernel image for version 2.6.32 on x86/x86_64
ii  linux-image-2.6.35-24-generic        2.6.35-24.42                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-25-generic        2.6.35-25.44                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-27-generic        2.6.35-27.48                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-2.6.35-28-generic        2.6.35-28.50                                      Linux kernel image for version 2.6.35 on x86/x86_64
ii  linux-image-generic                  2.6.35.28.36                                      Generic Linux kernel image

That is what came back

---

### Post by mikewhatever on 2011-05-01
You can remove the old kernels (search for 'linux-image'):
2.6.32-21
2.6.32-27
2.6.35-24
2.6.35-25
2.6.35-27

just be careful and don't remove the last one.

When done, run **sudo apt-get autoremove** to remove the older versions of the linux-headers.

---

### Post by katzman2 on 2011-05-03
Still has not worked.  Below are two screen shots-one of the error message and the other of the PC directories showing the size of each directory from the  root directory up.
Thanks[IMG]file:///home/katter/Desktop/Screenshot-2.png[/IMG]

---

