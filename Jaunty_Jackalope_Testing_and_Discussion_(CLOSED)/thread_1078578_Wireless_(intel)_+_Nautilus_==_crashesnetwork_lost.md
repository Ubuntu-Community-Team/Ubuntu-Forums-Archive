---
title: "Wireless (intel) + Nautilus == crashes/network lost"
date: 2009-02-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ormandj on 2009-02-23
Hi,

Repeatedly, I can connect via wireless, and attempt to transfer large files using samba or ssh (via nautilus) and my network connection will "stop" working. I still see an associated link, but can no longer pass network traffic. Disabling then re-enabling wireless fixes this issue, although I do have to kill Nautilus if I wish to use it further.

Has anybody else experienced this? I tried searching the bug tracker at launchpad.net, but it's really hard to search for such generic issues.

In Intrepid, Nautilus would often fail when streaming videos using Gstreamer-based applications, but the network connection didn't stop working, either.

Using rsync/scp to transfer the same file does not result in the loss of connectivity or the Nautilus lock-up.

Thanks!

---

### Post by klange on 2009-02-23
If you're experiencing the same issues I've had for the past year, it may have nothing to do with Nautilus.

The Intel wireless drivers (for the 3945, and others) are extremely buggy and are prone to firmware crashes (microcode errors) when they are not constantly being used. I'm surprised that this is cropping up again. In Intrepid, it seemed a slight workaround was in place that automatically reconnected the network after a crash, but from my experience a week ago it appears to have been removed.

If this is the case, a possible explanation for your issue is that network operations in Nautilus are file-by-file, with significant breaks in between, while doing a classic scp sends a more coherent stream of files. During the down time between files, you could be getting a microcode crash.

(Or I could be dead wrong... ;) )

---

### Post by ormandj on 2009-02-23
I wish it was that simple. It will fail during a single file transfer in Nautilus, requiring disable/enable NM as well as restarting Nautilus.

David

> **WindowsSucks said:**
> If you're experiencing the same issues I've had for the past year, it may have nothing to do with Nautilus.

The Intel wireless drivers (for the 3945, and others) are extremely buggy and are prone to firmware crashes (microcode errors) when they are not constantly being used. I'm surprised that this is cropping up again. In Intrepid, it seemed a slight workaround was in place that automatically reconnected the network after a crash, but from my experience a week ago it appears to have been removed.

If this is the case, a possible explanation for your issue is that network operations in Nautilus are file-by-file, with significant breaks in between, while doing a classic scp sends a more coherent stream of files. During the down time between files, you could be getting a microcode crash.

(Or I could be dead wrong... ;) )

---

