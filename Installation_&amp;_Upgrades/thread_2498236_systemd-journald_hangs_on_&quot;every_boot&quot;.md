---
title: "systemd-journald hangs on &quot;every boot&quot;"
date: 2024-06-05
forum: Installation &amp; Upgrades
---

### Post by tuan888 on 2024-06-05
Odroid Xu4, running ubuntu18 or ubuntu20 on Samsung SD card (for boot and /) without any issue. 
```
root@odroid:~# uname -a  (no newer odroid kernel on linux-image) 
Linux odroid 4.14.180-176 #1 SMP PREEMPT Tue May 19 00:40:55 -03 2020 armv7l armv7l armv7l GNU/Linux



```But since I upgrade to Ubuntu22, 48 out of 50 boots stop at:


```
[   27.801476] systemd[1]: Starting Remount Root and Kernel File Systems...
[   27.829788] EXT4-fs (mmcblk1p2): re-mounted. Opts: errors=remount-ro
[   27.830911] systemd[1]: Starting Coldplug All udev Devices...
[   27.864448] systemd[1]: Started Journal Service.
[   28.142698] systemd-journald[310]: Received client request to flush runtime journal.
or this line:
[    9.022411] systemd-journald[296]: File /var/log/journal/05196698763340e89230914b2c1b3c57/system.journal corrupted or uncleanly shut down, renaming and replacing.


```
After many "read, trial and error" (I can see that some people have had this issue before, some years ago): 


1) There is no use of the journal on the SD card at any time (ubuntu18, u20, u22)
```
root@odroid:~# debugfs -R features /dev/mmcblk1p2
debugfs 1.46.5 (30-Dec-2021)
Filesystem features: ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
```
2) my workaround is: mount the sd on a linux laptop and remove the whole journal director at /var/log/journal and try to boot again. With that trick 7 out of 10 times will success, if not try to remove the journal dir again (and again until success).
3) Try to disable journal but after the reboot it activate again


My temporary solution is making 2 temp scripts:


```
root@odroid:~# cat reboot.ksh
rm -fr /var/log/journal/05*
reboot
root@odroid:~# cat poweroff.ksh
rm -fr /var/log/journal/05*
shutdown
```


The issue is gone when I use a Samsung SD card, but on a new Kingston (also a 32GB) the success rate is 7 out 10 boot.


Do you have any clue? what can it be? 


thanks on advance.


```
root@odroid:~# df
Filesystem     1K-blocks    Used Available Use% Mounted on
tmpfs             204244    3836    200408   2% /run
/dev/mmcblk1p2  20833900 9125260  11677448  44% /
tmpfs            1021216       0   1021216   0% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
/dev/mmcblk1p3   8796228      24   8331112   1% /usb4
/dev/mmcblk1p1    130798   18000    112798  14% /media/boot
tmpfs             204240     140    204100   1% /run/user/110
tmpfs             204240     132    204108   1% /run/user/0
root@odroid:~#

```

If success the dmesg:
```
[   27.757450] systemd[1]: Starting Remount Root and Kernel File Systems...
[   27.784454] EXT4-fs (mmcblk1p2): re-mounted. Opts: errors=remount-ro
[   27.789635] systemd[1]: Starting Coldplug All udev Devices...
[   27.820384] systemd[1]: Started Journal Service.
[   28.087538] systemd-journald[300]: Received client request to flush runtime journal.
[   28.115494] systemd-journald[300]: File /var/log/journal/05196698763340e89230914b2c1b3c57/system.journal corrupted or uncleanly shut down, renaming and replacing.
[   28.463906] loop: module loaded
[   29.036566] gpiomem-exynos 13400000.gpiomem: Initialised: GPIO register area is 2
[   29.036715] gpiomem-exynos 13400000.gpiomem: Initialised: Registers at 0x13400000
[   29.036721] gpiomem-exynos 13400000.gpiomem: Initialised: Registers at 0x14010000
[   29.038697] input: gpio_keys as /devices/platform/gpio_keys/input/input0
[   29.646065] EXT4-fs (mmcblk1p3): mounted filesystem without journal. Opts: (null)
[   29.834558] usb 1-1: reset high-speed USB device number 2 using exynos-ehci
[   30.005405] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   30.034170] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
```

---

