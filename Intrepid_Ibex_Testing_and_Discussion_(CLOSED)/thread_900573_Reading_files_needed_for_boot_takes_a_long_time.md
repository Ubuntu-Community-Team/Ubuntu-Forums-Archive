---
title: "Reading files needed for boot takes a long time"
date: 2008-08-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2008-08-25
Booting seems to be taking longer and longer, and it's all down to the initial boot stage where it's "reading files necessary to boot." This sits churning the disk for a while - the rest of the boot takes about 20 seconds.

This didn't happen with a clean install (alpha 4) but I'm not sure at what stage the problem crept in. 

It looks like firewire is doing something odd. Seemingly relevant parts from dmesg:

```

[    6.299313] JFS: nTxBlock = 8192, nTxLock = 65536
[    6.344458] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f698b416241]
[   75.919284] udevd version 124 started
[   76.412436] ACPI: WMI-Acer: Mapper loaded
```

On the boot line I've tried specifying clocksource=hpet, removing quiet and splash, changed concurrency in /etc/init.d/rc from none to shell and back; no change.

--edit

Actually, I just noticed this:
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-rc3-ultimate

``` I'm running 2.6.26-5. This doesn't look right.

---

### Post by jfernyhough on 2008-08-25
Deleted the residual 2.6.27.rc3 file from /var/lib/initramfs-tools, triggered an initramfs update, rebuilt the initramfs for 2.6.26-5.

No difference.

I'm wondering if it's readahead.

/etc/readahead/boot is 6048 lines long.

---

### Post by jfernyhough on 2008-08-25
Tried reprofiling with GRUB. Has shortened the readahead list considerably to 1348 lines, seems to have helped with initial boot time.

Interesting.

---

### Post by jfernyhough on 2008-08-25
Nope, it's grown 2536 lines and half of the files are pretty irrelevant to the boot process, e.g. /usr/share/applications/screensavers/jigglypuff.desktop


"Reading files..." still takes 30 seconds or more.

---

### Post by Duf_Sh on 2008-08-25
+1 for me
Readahead list is 6192 lines long, loading the likes of aMSN, printer drivers, khotnewstuff cache and screensavers...
I'm not a MoTU but this doesn't seem very relevant for booting my computer

---

### Post by RAOF on 2008-08-26
I'd suggest filing a bug against readahead.  That sounds like it's being somewhat over enthusiastic.

---

### Post by jfernyhough on 2008-08-26
Bug reported: [https://bugs.launchpad.net/ubuntu/+source/readahead/+bug/261426](https://bugs.launchpad.net/ubuntu/+source/readahead/+bug/261426)

---

### Post by BC7333 on 2008-08-26
Also experienced this with intrepid with kernel 2.6.26.. with 2.6.27 it's down to a few seconds.

brian@brian-laptop:~$ uname -r
2.6.27-1-generic
brian@brian-laptop:~$ 

If you need your bug confirmed let me know and any additional info that might help.

---

### Post by Nullack on 2008-08-26
That would be good as its in new status - if your replicating the problem

---

