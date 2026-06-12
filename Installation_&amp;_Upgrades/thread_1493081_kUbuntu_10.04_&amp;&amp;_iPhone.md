---
title: "kUbuntu 10.04 &amp;&amp; iPhone"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by abominable on 2010-05-25
Hello to everyone.

I have installed kUbuntu 10.04 (actually upgraded from 9.10). And installed iFuse (0.9.7-1) I also have iPhone 3Gs firmware 3.1.3 jailbroken with Spirit.

I have read that by plugin it in, I would discover it in the Places. But I don't. After plugin it in I also tried ```
sudo mkdir /mnt/iPhone
sudo ifuse --root /mnt/iPhone/
```

But I get the error message ```
Failed to start AFC service 'com.apple.afc2' on the device.
This service enables access to the root filesystem of your device.
Your device needs to be jailbroken and have this service installed.
Note that PwnageTool installs it while blackra1n does not.

```

Do you have any idea on how to solve this problem.

Thank you in advance.

---

### Post by DinkyDogg on 2010-05-27
In Cydia, search for "afc2" and install the package. This will make it mountable with ifuse, but I think that Ubuntu should be able to mount it automatically without ifuse.

I'm having the same problem as you, though... I can mount it manually with ifuse, but I don't know how to make Amarok or Rhythmbox recognize it so I can sync music to it.

---

### Post by abominable on 2010-05-27
Thanx for your reply.

I will check it soon and write back any foundings.

---

