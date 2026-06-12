---
title: "x-server fails after installing old HD in new computer"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2008-10-23
Hi,
I had a hardware crash on my old server (HP Vector 420) and I'm trying to install the old hard drive in a "new" Dell Optiplex. Grub works fine but when I boot into Ubuntu (7.10) the load fails to start x-server. How should I go about reconfiguring (especially considering that I can't get into the OS)?
Thanks,
David

[Oh...I suppose I should have noted that the hard drive is loaded with Edubuntu]

---

### Post by cariboo on 2008-10-23
You could try:

```
sudo dpkg-reconfigure -phigh xserver-org
```

The new motherboard must have a different graphics adapter.

Jim

---

### Post by dbclinton on 2008-10-24
Thanks. You were right about the adapter. In the end I realized that the video card from the old system wasn't built into the motherboard so I simply moved it over to the new computer and everything's working fine!
Just try doing THAT with Windows! :)

---

