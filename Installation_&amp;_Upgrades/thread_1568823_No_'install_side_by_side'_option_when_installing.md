---
title: "No 'install side by side' option when installing"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by rodericke on 2010-09-05
I recently tried to install Ubuntu after trying it via Wubi for a couple of nights. However, when trying to install, there is no 'install side by side' and I am unnerved at the thought of manual partitioning. Is the 'side by side' no longer an option?

---

### Post by TBABill on 2010-09-05
Side by side is definitely still an option, even with more than one OS. Did you boot into the Live CD, then click "install Ubuntu" or did you go straight to install without fully booting? I know you get the option when going into the LiveCD fully and double clicking "install Ubuntu" on the desktop.

---

### Post by rodericke on 2010-09-05
Tried what you said with no luck. It is partitioned as follows. 1.6GB Windows Recovery Loader/248GB unknown. It isn't even recognizine my operating system which is windows vista home premium.

---

### Post by bcbc on 2010-09-05
> **rodericke said:**
> Tried what you said with no luck. It is partitioned as follows. 1.6GB Windows Recovery Loader/248GB unknown. It isn't even recognizine my operating system which is windows vista home premium.

Shrink your windows partition using Windows Vista's disk utility. Then use the manual option to select the new partition. With windows vista/7 you should never let Ubuntu (ubiquity or gparted etc) shrink the windows partition.

---

### Post by oldfred on 2010-09-05
Often gparted and Ubuntu will not 'see' a windows partition that needs chkdsk. If chkdsk flag is set or partition has errors then gparted does not want to mount it or modify it as it may cause even bigger issues. Run chkdsk.

Run chkdsk several times, until no more errors are detected.
Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

