---
title: "Won't standby, usb_bluetooth refusing to freeze"
date: 2015-10-22
forum: MINT
---

### Post by stuppie2 on 2015-10-22
I am running Linux Mint 17.1 Rebecca on a Yoga Pro laptop. The laptop will only go into standby once and then will not until it is restarted. When attempting to standby it will freeze for 20 seconds and then come back up. Running pm-suspend on the command line shows no output. dmesg has some useful logs. The relevent part is below

```
[60991.396195] Freezing user space processes ... 
[61011.412504] Freezing of tasks failed after 20.000 seconds (1 tasks refusing to freeze, wq_busy=0):
[61011.412578] usb_bluetooth   D ffff88025f214440     0 14665  14591 0x00000004
[61011.412581]  ffff88024bbc5b50 0000000000000002 ffff88024dce47d0 ffff88024bbc5fd8
[61011.412584]  0000000000014440 0000000000014440 ffff88024dce47d0 ffff8802515a6c80
[61011.412586]  ffff8802515a6c84 ffff88024dce47d0 00000000ffffffff ffff8802515a6c88
[61011.412588] Call Trace:
[61011.412594]  [<ffffffff8171a3a9>] schedule_preempt_disabled+0x29/0x70
[61011.412596]  [<ffffffff8171c215>] __mutex_lock_slowpath+0x135/0x1b0
[61011.412598]  [<ffffffff8171c2af>] mutex_lock+0x1f/0x2f
[61011.412601]  [<ffffffff81532a54>] usb_unlocked_disable_lpm+0x24/0x50
[61011.412603]  [<ffffffff81534f48>] usb_port_suspend+0x128/0x440
[61011.412606]  [<ffffffff8154a55a>] generic_suspend+0x2a/0x40
[61011.412608]  [<ffffffff815413df>] usb_suspend_both+0x1bf/0x1e0
[61011.412610]  [<ffffffff815425d3>] usb_runtime_suspend+0x33/0x70
[61011.412613]  [<ffffffff815425a0>] ? usb_probe_interface+0x2f0/0x2f0
[61011.412615]  [<ffffffff8149a166>] __rpm_callback+0x36/0xc0
[61011.412617]  [<ffffffff811d9074>] ? mntput+0x24/0x40
[61011.412619]  [<ffffffff8149a214>] rpm_callback+0x24/0x80
[61011.412620]  [<ffffffff8149a396>] rpm_suspend+0x126/0x6e0
[61011.412622]  [<ffffffff8149ba5d>] __pm_runtime_suspend+0x5d/0x80
[61011.412625]  [<ffffffff81542630>] ? usb_runtime_resume+0x20/0x20
[61011.412627]  [<ffffffff8154265a>] usb_runtime_idle+0x2a/0x40
[61011.412628]  [<ffffffff8149a166>] __rpm_callback+0x36/0xc0
[61011.412630]  [<ffffffff8149abfd>] rpm_idle+0x1bd/0x2b0
[61011.412631]  [<ffffffff8149b86d>] pm_runtime_allow+0x8d/0x90
[61011.412634]  [<ffffffff8149426a>] control_store+0xca/0xd0
[61011.412636]  [<ffffffff81489ab8>] dev_attr_store+0x18/0x30
[61011.412639]  [<ffffffff8122f418>] sysfs_write_file+0x128/0x1c0
[61011.412643]  [<ffffffff811b9534>] vfs_write+0xb4/0x1f0
[61011.412644]  [<ffffffff811b9f69>] SyS_write+0x49/0xa0
[61011.412647]  [<ffffffff8172663f>] tracesys+0xe1/0xe6
[61011.412654] 
[61011.412654] Restarting tasks ... done.
```

```
Output of ps aux | grep blue
root     14665  0.0  0.0   4440   716 ?        D    15:20   0:00 /bin/sh /usr/lib/pm-utils/power.d/usb_bluetooth true
```

I have tried both: rfkill block bluetooth and service bluetooth stop and have added them both to /etc/rc.local with no effect.
And I also added blacklist btusb and blacklist bluetooth to /etc/modprobe.d/blacklist.conf
None of these seem to work as the usb_bluetooth task still starts and the laptop won't go into standby.
I have also tried apt-get purge "bluez*", but this removes my network-manager for some reason and when I reinstall it, bluetooth comes back.....

---

### Post by howefield on 2015-10-22
Thread moved to the "*MINT*" forum.

---

