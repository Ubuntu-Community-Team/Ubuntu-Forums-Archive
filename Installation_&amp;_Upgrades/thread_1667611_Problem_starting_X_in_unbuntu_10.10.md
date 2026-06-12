---
title: "Problem starting X in unbuntu 10.10"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by xain on 2011-01-15
Hi, I recently installed ubuntu 10.10 on my old Toshiba A100 where I've been running XP and mint - different hard drives though - with no problems for ages. The installation went fine, I can log in with my user account, but after that the screen shows only the wallpaper (with the mouse enabled). Any hints on how to troubleshoot it ?

These are the [Xorg]("http://paste.ly/3s1g") and the [messages]("http://paste.ly/3s1s") log files.

Thanks

---

### Post by Rubi1200 on 2011-01-15
Hi,
what graphics card do you have installed?

Try these commands from the terminal (either in safe graphics mode or recovery mode):
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by xain on 2011-01-15
Thanks for your reply. I could successfuly load X in safe mode (it looks just perfect). When I run the commands you mentioned I get:

mv: cannot stat `/etc/X11/xorg.conf': No such file or directory

and

Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

Now, is there a simple way to make this safe-mode the default so I don't have to go throught the recovery mode every time ?

---

### Post by Rubi1200 on 2011-01-15
Okay, we are making progress. Still need to know what graphics card you have please.

---

### Post by xain on 2011-01-15
I forgot to post it ... my card is:

01:00.0 VGA compatible controller: ATI Technologies Inc M24 [Radeon Mobility X600] (prog-if 00 [VGA controller])
        Subsystem: Toshiba America Info Systems Device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at 90000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at c0000000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at 98000000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint, MSI 00
        Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [100] Advanced Error Reporting
        Kernel driver in use: radeon
        Kernel modules: radeon

---

### Post by Rubi1200 on 2011-01-15
I think you may need to configure the drivers for it.

This is what I found:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Hope this helps.

---

