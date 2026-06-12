---
title: "Need patching help"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by Keith Fox on 2010-02-14
I'm new to applying patches and I came across a scenario where I need to apply a patch. I created a "USB7" which is basically a 6 digit hardware device that displays any characters you want. I was able to get it working using a VirtualBox and Windows XP virtual machine using HyperTerminal, and for Linux this device requires a patch for it to work.  Look at this page for the patch itself and directions, but the directions are meek and limiting.  Please help me command this patch to work:
Patch:  [http://spiffie.org/kits/usb7/driver_linux.shtml#above2623](http://spiffie.org/kits/usb7/driver_linux.shtml#above2623)
Device description:  [http://spiffie.org/kits/usb7/protocol_3.shtml](http://spiffie.org/kits/usb7/protocol_3.shtml)

---

### Post by falconindy on 2010-02-14
What you linked to is a kernel patch that requires recompiling your kernel. However, it's fairly old -- the kernel mentioned is 2.6.25 which was released roughly 2 years ago. I'm not certain about 2.6.31, but this patch does **not** apply cleanly to 2.6.32 source.

- If you want to go ahead and try it, you'll need to first get the kernel source from kernel.org.
- Unzip it somewhere, let's say "$HOME/dev/". The source will all be contained in a directory called "linux-2.6.31".
- Save the linked patch as a file in the unzipped source folder ($HOME/dev/linux-2.6.31).
- To apply the patch, execute the following from the source folder (where the patch is also saved):
```
patch -Np1 -i usb.patch
```

You'll likely get rejects, similar to:
```
patching file drivers/usb/core/config.c
Hunk #1 FAILED at 137.
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/core/config.c.rej
patching file drivers/usb/host/uhci-q.c
patch unexpectedly ends in middle of line
Hunk #1 FAILED at 1042.
1 out of 1 hunk FAILED -- saving rejects to file drivers/usb/host/uhci-q.c.rej
```
Needless to say, rejects are bad. If it **does** patch cleanly, you'll need to finish the job by compiling the kernel. There's a bazillion references on the Internet about how to do this. It's not always a straight forward process, though.

---

