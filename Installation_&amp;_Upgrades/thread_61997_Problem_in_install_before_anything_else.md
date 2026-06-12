---
title: "Problem in install before anything else"
date: 2005-09-02
forum: Installation &amp; Upgrades
---

### Post by Pommy on 2005-09-02
Hi,

While installing ubuntu (Hoary) on a Dell machine off of the install CD, the following came up:

```
usb 2-1 new full speed USB Device uhci_hcd address 3
ata1: command 0xa0 timeout stat 0x58 host_stat 0x61
```

At which point the boot hangs and a ctrlaltdel/restart is needed.

After some messing around with both boot parameters and hardware and not figuring out what the problem is, I discovered that disconnecting my USB HP Deskjet printer (the only USB peripheral I have connected) causes the boot to hang up before the usb 2-1 line appears; instead, it hangs up at

```
elevator: using anticipatory as default io scheduler
```

I googled and searched for these messages to no avial :(
Any help or ideas? Or on what the offending component of my computer might be? Thanks in advance..

---

