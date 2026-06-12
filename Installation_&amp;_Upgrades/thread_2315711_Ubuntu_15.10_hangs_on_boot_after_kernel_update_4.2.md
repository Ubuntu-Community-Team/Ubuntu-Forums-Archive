---
title: "Ubuntu 15.10 hangs on boot after kernel update 4.2.0"
date: 2016-03-01
forum: Installation &amp; Upgrades
---

### Post by nworbnhoj on 2016-03-01
I recently made fresh installs of Ubuntu 15.20 64bit on 5 x Lenovo T400 Thinkpads. All good.

However on first boot, Software Updater identifies and installs a significant number of packages and then requires a reboot. The T400 boot process hangs and is unresponsive. By trial and error I have narrowed the problem down to the updated Linux kernel 4.2.0. I progressively installed package updates and rebooted the T400 manually until only 8 packages remained to be updated.
[LIST]
[*]Complete Generic Linux kernel and headers 
[*]Firmware for Linux kernel drivers 
[*]Generic Linux kernel headers 
[*]Generic Linux kernel image 
[*]Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP 
[*]Linux kernel Headers for development 
[*]Linux kernel headers for version 4.2.0 on 64 bit x86 SMP 
[*]Linux kernel image for version 4.2.0 on 64 bit x86 SMP 
[/LIST]
If I proceed to install these 8 packages and reboot then the T400 hangs during the boot process with a blank screen.

The first time I encountered this problem (after installing all package updates in the one hit) the boot process hung with errors referring to "plymouthd blocked for more than 120 seconds" during the terminal output OR hung in the very first Ubuntu graphic just after the first orange dot appeared. I was unable to locate relevant prior history of this type of failure. 

How can i proceed to troubleshoot & resolve this issue?

Thanks in advance.

---

### Post by puranik2 on 2016-03-01
I have a very similar issue with my Lenovo T400 Thinkpad. I think it has something to do with the very latest kernel: 4.2.0-30.

I had a pre-existing 15.10 install that I upgraded a few days ago. After rebooting, it hung repeatedly in two situations: 1) just after I logged in and 2) if I used the mouse to click Shut Down.. and chose Restart. (I wasn't exhaustive in the search.) Both of these hangs were so bad that I couldn't use the Ctrl-Alt-F? keys or even REISUB.

I reinstalled 15.10 (because I didn't know what else to do) and everything worked fine until software update brought me back to the latest kernel. Then it started hanging again.

The temporary solution that I've found,if you've already installed the bad kernel, is to hold Shift down during boot and choose an old kernel.

---

### Post by nworbnhoj on 2016-03-02
Sounds very similar. There is also another possibly related thread [http://ubuntuforums.org/showthread.php?t=2315640](http://ubuntuforums.org/showthread.php?t=2315640)

---

### Post by nworbnhoj on 2016-03-02
Thankyou for the boot+shift trick, it has enabled me to see some logs (and plymouthd still features)
```

Mar  2 12:55:08 T400 kernel: [  480.112369] INFO: task plymouthd:298 blocked for more than 120 seconds.
Mar  2 12:55:08 T400 kernel: [  480.112373]       Not tainted 4.2.0-30-generic #36-Ubuntu
Mar  2 12:55:08 T400 kernel: [  480.112377] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar  2 12:55:08 T400 kernel: [  480.112381] plymouthd       D ffff88007c496640     0   298      1 0x00000000
Mar  2 12:55:08 T400 kernel: [  480.112388]  ffff88007506f798 0000000000000082 ffff880079501980 ffff8800351072c0
Mar  2 12:55:08 T400 kernel: [  480.112396]  0000000000000046 ffff880075070000 ffff8800797b1148 ffff8800797b1208
Mar  2 12:55:08 T400 kernel: [  480.112402]  0000000000000000 0000000000000004 ffff88007506f7b8 ffffffff817eeca7
Mar  2 12:55:08 T400 kernel: [  480.112409] Call Trace:
Mar  2 12:55:08 T400 kernel: [  480.112417]  [<ffffffff817eeca7>] schedule+0x37/0x80
Mar  2 12:55:08 T400 kernel: [  480.112424]  [<ffffffff8152bc16>] rpm_resume+0x186/0x660
Mar  2 12:55:08 T400 kernel: [  480.112431]  [<ffffffff810bd800>] ? wake_atomic_t_function+0x60/0x60
Mar  2 12:55:08 T400 kernel: [  480.112438]  [<ffffffff8152c94e>] __pm_runtime_resume+0x4e/0x70
Mar  2 12:55:08 T400 kernel: [  480.112493]  [<ffffffffc02d9053>] radeon_dvi_detect+0x33/0x4d0 [radeon]
Mar  2 12:55:08 T400 kernel: [  480.112508]  [<ffffffffc015ceea>] drm_helper_hpd_irq_event+0x9a/0x130 [drm_kms_helper]
Mar  2 12:55:08 T400 kernel: [  480.112546]  [<ffffffffc02b4930>] radeon_resume_kms+0x210/0x3d0 [radeon]
Mar  2 12:55:08 T400 kernel: [  480.112583]  [<ffffffffc02b2143>] radeon_pmops_runtime_resume+0x73/0xb0 [radeon]
Mar  2 12:55:08 T400 kernel: [  480.112592]  [<ffffffff8141571f>] pci_pm_runtime_resume+0x7f/0xb0
Mar  2 12:55:08 T400 kernel: [  480.112601]  [<ffffffff81519bc9>] vga_switcheroo_runtime_resume+0x39/0x40
Mar  2 12:55:08 T400 kernel: [  480.112607]  [<ffffffff8152b737>] __rpm_callback+0x37/0x80
Mar  2 12:55:08 T400 kernel: [  480.112613]  [<ffffffff81519b90>] ? vga_switcheroo_runtime_suspend+0x60/0x60
Mar  2 12:55:08 T400 kernel: [  480.112619]  [<ffffffff8152b7a8>] rpm_callback+0x28/0x90
Mar  2 12:55:08 T400 kernel: [  480.112625]  [<ffffffff81519b90>] ? vga_switcheroo_runtime_suspend+0x60/0x60
Mar  2 12:55:08 T400 kernel: [  480.112631]  [<ffffffff8152beeb>] rpm_resume+0x45b/0x660
Mar  2 12:55:08 T400 kernel: [  480.112638]  [<ffffffff8152c94e>] __pm_runtime_resume+0x4e/0x70
Mar  2 12:55:08 T400 kernel: [  480.112676]  [<ffffffffc02b6b26>] radeon_driver_open_kms+0x36/0x1b0 [radeon]
Mar  2 12:55:08 T400 kernel: [  480.112707]  [<ffffffffc0069764>] drm_open+0x1c4/0x410 [drm]
Mar  2 12:55:08 T400 kernel: [  480.112714]  [<ffffffff81201e51>] ? exact_lock+0x11/0x20
Mar  2 12:55:08 T400 kernel: [  480.112745]  [<ffffffffc006fdd9>] drm_stub_open+0xa9/0x120 [drm]
Mar  2 12:55:08 T400 kernel: [  480.112753]  [<ffffffff812024cf>] chrdev_open+0xbf/0x1b0
Mar  2 12:55:08 T400 kernel: [  480.112762]  [<ffffffff811fb6af>] do_dentry_open+0x1ff/0x310
Mar  2 12:55:08 T400 kernel: [  480.112768]  [<ffffffff81202410>] ? cdev_put+0x30/0x30
Mar  2 12:55:08 T400 kernel: [  480.112774]  [<ffffffff811fc846>] vfs_open+0x56/0x60
Mar  2 12:55:08 T400 kernel: [  480.112781]  [<ffffffff8120be8d>] path_openat+0x1ed/0x12c0
Mar  2 12:55:08 T400 kernel: [  480.112788]  [<ffffffff8120e15a>] do_filp_open+0x8a/0x100
Mar  2 12:55:08 T400 kernel: [  480.112795]  [<ffffffff811deec7>] ? kmem_cache_alloc+0x187/0x200
Mar  2 12:55:08 T400 kernel: [  480.112802]  [<ffffffff8121b996>] ? __alloc_fd+0x46/0x110
Mar  2 12:55:08 T400 kernel: [  480.112808]  [<ffffffff811fcc08>] do_sys_open+0x138/0x280
Mar  2 12:55:08 T400 kernel: [  480.112815]  [<ffffffff81067aa4>] ? __do_page_fault+0x1b4/0x400
Mar  2 12:55:08 T400 kernel: [  480.112822]  [<ffffffff811fcd6e>] SyS_open+0x1e/0x20
Mar  2 12:55:08 T400 kernel: [  480.112828]  [<ffffffff817f2d72>] entry_SYSCALL_64_fastpath+0x16/0x75

```

---

### Post by nworbnhoj on 2016-03-02
Exact bug report here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548867)
It has already been fixed for VMware
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587/comments/45](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548587/comments/45)

---

### Post by nworbnhoj on 2016-03-02
I have removed the problem kernel with 
```
apt-get --purge remove linux-image-4.2.0-30-generic linux-image-extra-4.2.0-30-generic
```
and will wait for the next kernel before I update again

---

### Post by nworbnhoj on 2016-03-02
There is a workaround for this issue on the Lenovo T400

Configure BIOS settings:[INDENT]"Graphic mode=Discrete"
"OS Detection for Switchable Graphics=Disabled"
[/INDENT]

---

