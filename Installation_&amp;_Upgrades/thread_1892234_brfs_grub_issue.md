---
title: "brfs grub issue"
date: 2011-12-07
forum: Installation &amp; Upgrades
---

### Post by andzaytsev on 2011-12-07
Hello, I installed Ubuntu 11.10 on the btrfs partition. Each time i boot there is a message displayed:
[CODE]Sparse file is not allowed. Press any key to continue...[CODE]
So after pressing any key everything boots normally.
How can I get rid of this message? It annoys me on 2 different notebooks.

---

### Post by drs305 on 2011-12-07
Looks like you are subject to a known bug.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/736743")

Post 8 states:
> Thanks, but there's no need to post further reproduction information to this bug. This is a missing feature and we know about it.

Nevertheless, you might want to read through the bug report and subscribe so you are notified if someone posts a solution.

On the down side, it seems to have persisted through at least Precise Alpha 1.

---

### Post by andzaytsev on 2011-12-07
Thank you, but is there any way to get rid of that message and speed up the boot?

---

### Post by drs305 on 2011-12-07
I see you added a comment to the bug report and that your system doesn't continue to boot as indicated it would.

Colin Watson is usually very helpful and perhaps he will respond in the bug report. 

There is also a suggestion in post #10 of the report that provides a possible method to allow it to continue (even if it still displays the message).

I don't have any btrfs partitions so I can't help by experimenting.

---

### Post by andzaytsev on 2011-12-07
Thank you. I discovered that it boots even without pressing a key. But it takes a long time to wait until the system is ready...

---

