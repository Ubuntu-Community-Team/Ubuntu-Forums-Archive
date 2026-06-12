---
title: "Getting initramfs when trying to boot"
date: 2011-10-25
forum: Installation &amp; Upgrades
---

### Post by leonardopessoa on 2011-10-25
Hi there,

I've installed Ubuntu 11.10 on this computer (Pentium D, 768mb RAM) with Wubi (which obviously means that I'm dual booting with Windows) but after reboot I'm getting the initramfs screen.
I've tryied to boot with the LIVE cd and also Ubuntu Rescue Remix but no deal. With the LIVE cd I get to the same screen and the Ubuntu Rescue it can't find a init.zl something file.
Tryied to change my HD to another one with nothing installed but I still hit the initramfs screen.
The error message appears as follows:
```

Gave up waiting for root device
- boot args (cat /proc/cmdline)
- Missing models (cat/proc/modules; ls /dev)
ALERT! (/dev/disk/by_uuid/00F0FA0CF0 does not exist. Dropping to shell)

```

If I wait, it starts to print thousands of messages like:
```
IO error, dev sr0, logical block 178898
BUFFER I/O: error on device sr0
```

With the CD, I get no erros on the initramfs screen.
Tryied to mount the HD manually on the initramfs but I get "cannot read /etc/fstab no such file or directory"

I don't know what else to do since I can't even run a live CD.
I guess the CD is just fine.


Thank you very much!

---

