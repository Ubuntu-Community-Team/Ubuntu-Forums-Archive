---
title: "Xorg crashes"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Glowing Fish on 2010-02-22
Hello, I posted previously about problems with my computer freezing.

Now at least it is freezing, and going to a screen where it lets me know what the error is. It gives me the option of running in "low graphics mode", but it doesn't work.

I have an Intel video card and a Flatron W2230S monitor.

The last entry in the error log is:

```
Fatal Server Error:
Failed to submit batchbuffer
Input/output error.
```

Any thoughts? What is a batchbuffer, anyway?

---

### Post by 23meg on 2010-02-22
Do you have the latest libdrm2 and libdrm-intel1 (2.4.18-1ubuntu2)?

---

### Post by Glowing Fish on 2010-02-22
> **23meg said:**
> Do you have the latest libdrm2 and libdrm-intel1 (2.4.18-1ubuntu2)?

Yes.

---

### Post by dino99 on 2010-02-22
have these packages installed with a nvidia card 8500 gt and all is fine.

Maybe you should erase xorg.conf if you have one, then reboot.

then run:
  system --> admin --> hardware driver: select yours, activate it then reboot.

---

### Post by gomyhr on 2010-02-22
> **Glowing Fish said:**
> 
```
Fatal Server Error:
Failed to submit batchbuffer
Input/output error.
```

Any thoughts? What is a batchbuffer, anyway?

A batchbuffer is a set of instructions to the GPU (Graphical Processor Unit) that it is supposed to compute. When the GPU hangs this error message may appear and the system will typically freeze. If you update to xserver-xorg-video-intel version 2.9.1-1ubuntu6 (new today), apport should offer to submit a bug report automatically when this happens. Btw, the more interesting log for this kind of problems is the output of dmesg.

There is more information about this kind of bug at [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) .

PS: We are currently having problems troubleshooting this kind of problems, but we're working on it.

---

### Post by Glowing Fish on 2010-02-22
> **gomyhr said:**
> A batchbuffer is a set of instructions to the GPU (Graphical Processor Unit) that it is supposed to compute. When the GPU hangs this error message may appear and the system will typically freeze. If you update to xserver-xorg-video-intel version 2.9.1-1ubuntu6 (new today), apport should offer to submit a bug report automatically when this happens. Btw, the more interesting log for this kind of problems is the output of dmesg.

There is more information about this kind of bug at [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) .

PS: We are currently having problems troubleshooting this kind of problems, but we're working on it.

I did update, and the problem persists.
Has this moved out of tech support territory, and into bug report territory?

---

