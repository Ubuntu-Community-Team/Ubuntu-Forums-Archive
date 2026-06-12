---
title: "Update-initramfs keeps failing: missing modules.builtin.modinfo"
date: 2021-08-26
forum: Installation &amp; Upgrades
---

### Post by spider-3b on 2021-08-26
Hi

I&#8217;m trying to update initramfs to enable hibernation, however it keeps failing because:
```

[COLOR=#000000]Update-initramfs: Generating/boot/initrd.img-5.3.0-46-generic
[/COLOR][COLOR=#000000]W: Can&#8217;t find modules.builtin.modinfo (for locating built-in drivers&#8217; firmware, supported in Linux >= 5.2)[/COLOR]
[COLOR=#000000]
[/COLOR]
[COLOR=#000000]Update-initramfs: Generating/boot/initrd.img-5.3.0-51-generic[/COLOR]
[COLOR=#000000]W: Can&#8217;t find modules.builtin.modinfo (for locating built-in drivers&#8217; firmware, supported in Linux >= 5.2)
[/COLOR]
```

---

### Post by mikewhatever on 2021-08-28
Is this Ubuntu related? Where does kernel 5.3 come from?

---

### Post by deadflowr on 2021-08-28
There are some 5.3 kernels available within the 18.04 archives.
Though they aren't tied to any meta-packages like the 4.15 or 5.4 packages are.
They might have been tied to the hwe packages at some time.
(or even more probable, they could have been related to the -edge version of the hwe stack)
Perhaps the OP either removed or never had the meta-packages installed.
(I'm using the term meta-package loosely here as I've never known what they actually consider them to be called)

That said the versions shown are really old, even for those 5.3 kernels.
Last one I can see is 5.3.0-76.
I would suggest installing the HWE stack meta-packages,
which will update the kernel to the 5.4 stack which at least has support.

```
sudo apt update
sudo apt install linux-generic-hwe-18.04
```

Or is there some reason not to?

---

