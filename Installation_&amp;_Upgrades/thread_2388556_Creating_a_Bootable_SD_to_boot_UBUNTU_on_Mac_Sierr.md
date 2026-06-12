---
title: "Creating a Bootable SD to boot UBUNTU on Mac Sierra"
date: 2018-04-04
forum: Installation &amp; Upgrades
---

### Post by pka3 on 2018-04-04
Hello all,

I am in need of serious help. I have ran into some difficulty lately trying to install Ubuntu 16.04 onto a bootable SD card in order to boot on Mac High Sierra.

I tried many different softwares (Unetbootin, rEFit, Etcher, Mac Linux USB loader. All claiming to help but non have helped thus far.

Each time I try I run into this same problem on my mac. I have attached a copy of the code I receive when I attempt to boot it up.

---

### Post by TheFu on 2018-04-05
If you have an ISO, you can just use dd.  OSX uses different options than Linux, but it is the same tool. Think the only different is lack of support for K/M size specs.
General form:
```
sudo dd if=/path/to/ubuntu.iso of=/dev/path/to/SD-card/device bs=4096
```

Don't get those backwards and if you specify the wrong device, wiping OSX is possible. Be very careful.

The command I'd use on my Linux system is:
```
sudo dd if=/tmp/ubuntu.iso of=/dev/sdb bs=4M
```

If anything automatically mounts storage on the Mac, you'll need to umount it before removing it.  You can also google for this answer if mine isn't clear. I looked it up last week - easily found.

---

### Post by pka3 on 2018-04-05
Thanks for the prompt reply. By the way, I am a bit of a noob. I hope I can get this right. Thanks again.

> **TheFu said:**
> If you have an ISO, you can just use dd.  OSX uses different options than Linux, but it is the same tool. Think the only different is lack of support for K/M size specs.
General form:
```
sudo dd if=/path/to/ubuntu.iso of=/dev/path/to/SD-card/device bs=4096
```

Don't get those backwards and if you specify the wrong device, wiping OSX is possible. Be very careful.

The command I'd use on my Linux system is:
```
sudo dd if=/tmp/ubuntu.iso of=/dev/sdb bs=4M
```

If anything automatically mounts storage on the Mac, you'll need to umount it before removing it.  You can also google for this answer if mine isn't clear. I looked it up last week - easily found.

---

