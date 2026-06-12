---
title: "Installing and Updating Nvidia display drivers"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by helosk on 2011-02-28
So I just installed Ubuntu last night parallel to windows vista ultimate (no problems).

my biggest problem is that when I tried to install the nvidia display drivers, I somehow downloaded a server based driver (and am having amazingly difficult problems).

I use a dual monitor set up (both are plug and play LCD displays) and i'm not too worried about aesthetics but rather, performance.

I downloaded the correct driver but now I don't know how to install it...

can anyone please! help me?

is there a way to uninstall this server driver?

---

### Post by slimb on 2011-02-28
Did you download and install from NVIDIA's website or via APT?

You can get the NVIDIA drivers no problem from APT using

```
sudo apt-get install nvidia-current
```

For removal of the NVIDIA drivers you installed manually you can re-use the file you originally downloaded and run it again just add the --uninstall flag to it.

---

