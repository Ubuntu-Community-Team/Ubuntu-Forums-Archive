---
title: "How do I send tty4 output to ttyS0 during preseed install?"
date: 2019-03-10
forum: Installation &amp; Upgrades
---

### Post by xyst on 2019-03-10
During installation quite a bit of debug output gets sent to tty4 but I can't seem to find a way to get the installer to combine the tty0 and tty4 output and send it to ttyS0 (serial).
I want a better way to debug installation issues that happen when I only have serial over lan access to a server.
When late_command fails, for example, there is a lot of useful info in tty4.

Here are the kernel params that I am passing
```

console=tty0 console=ttyS0,115200n8 DEBIAN_FRONTEND=text BOOT_DEBUG=2 noshell

```

---

