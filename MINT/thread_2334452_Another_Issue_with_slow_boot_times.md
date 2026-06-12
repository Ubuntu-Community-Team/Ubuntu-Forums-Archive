---
title: "Another Issue with slow boot times"
date: 2016-08-19
forum: MINT
---

### Post by rschanzenbacher on 2016-08-19
I would like to say first off I am very OCD and like to get the best possible times with an HDD (SDD is out of my way)

But anyways, I've been booting very slow lately. I run Linux Mint 18 Cinnamon.

And for some reason, the userspace load time takes 30-50seconds.

I've been googling for hours with no avail. Maybe someone here can uncover something I haven't

systemd-analyze:

```
$ systemd-analyze time
Startup finished in 4.297s (firmware) + 7.674s (loader) + 5.706s (kernel) + 27.917s (userspace) = 45.596s



```

systemd-analyze critical-chain

```

The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


graphical.target @27.601s
&#9492;&#9472;multi-user.target @27.591s
  &#9492;&#9472;smbd.service @27.153s +437ms
    &#9492;&#9472;nmbd.service @22.926s +4.210s
      &#9492;&#9472;network-online.target @22.925s
        &#9492;&#9472;network.target @22.914s
          &#9492;&#9472;wpa_supplicant.service @24.617s +480ms
            &#9492;&#9472;basic.target @14.400s
              &#9492;&#9472;sockets.target @14.400s
                &#9492;&#9472;acpid.socket @14.400s
                  &#9492;&#9472;sysinit.target @14.270s
                    &#9492;&#9472;systemd-update-utmp.service @14.072s +196ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @13.790s +271ms
                        &#9492;&#9472;local-fs.target @13.719s
                          &#9492;&#9472;run-cgmanager-fs.mount @16.409s
                            &#9492;&#9472;local-fs-pre.target @5.969s
                              &#9492;&#9472;systemd-remount-fs.service @5.837s +78ms
                                &#9492;&#9472;system.slice @2.378s
                                  &#9492;&#9472;-.slice @2.352s$ systemd-analyze critical-chain



```

systemd-analyze blame

```


$ systemd-analyze blame
          6.624s NetworkManager.service
          5.898s dev-sda7.device
          4.424s accounts-daemon.service
          4.210s nmbd.service
          3.807s samba-ad-dc.service
          3.233s lvm2-monitor.service
          2.785s systemd-fsck@dev-disk-by\x2duuid-4C0D\x2dC5B3.service
          2.621s console-setup.service
          2.620s binfmt-support.service
          2.620s networking.service
          2.525s systemd-fsck@dev-disk-by\x2duuid-77ed4c1b\x2dd757\x2d40a4\x2d8b
          2.403s ondemand.service
          2.246s systemd-udevd.service
          2.134s systemd-logind.service
          2.131s thermald.service
          2.131s console-kit-log-system-start.service
          1.999s pppd-dns.service
          1.998s gpu-manager.service
          1.990s rsyslog.service
          1.863s avahi-daemon.service
          1.655s polkitd.service
          1.448s loadcpufreq.service
          1.033s grub-common.service
           886ms upower.service
           879ms systemd-tmpfiles-setup-dev.service
           764ms keyboard-setup.service
           749ms systemd-modules-load.service
           713ms systemd-journald.service
           646ms irqbalance.service
           581ms home.mount
           480ms wpa_supplicant.service
           454ms speech-dispatcher.service
           447ms lm-sensors.service
           437ms smbd.service
           410ms plymouth-start.service
           375ms colord.service
           349ms boot-efi.mount
           328ms udisks2.service
           314ms tlp.service
           307ms systemd-backlight@backlight:intel_backlight.service
           271ms systemd-tmpfiles-setup.service
           259ms setvtrgb.service
           249ms sys-kernel-debug.mount
           240ms systemd-udev-trigger.service
           209ms dev-sda8.swap
           202ms dns-clean.service
           196ms systemd-update-utmp.service
           154ms kmod-static-nodes.service
           131ms dev-mqueue.mount
           129ms dev-hugepages.mount
           123ms systemd-journal-flush.service
           122ms systemd-sysctl.service
           121ms ufw.service
           102ms systemd-user-sessions.service
            97ms user@1000.service
            94ms plymouth-read-write.service
            87ms rtkit-daemon.service
            78ms systemd-remount-fs.service
            59ms proc-sys-fs-binfmt_misc.mount
            58ms console-kit-daemon.service
            55ms resolvconf.service
            55ms systemd-hostnamed.service
            54ms hddtemp.service
            37ms systemd-random-seed.service
            24ms plymouth-quit-wait.service
            24ms alsa-restore.service
            24ms plymouth-quit.service
            12ms cpufrequtils.service
            11ms openvpn.service
            11ms systemd-update-utmp-runlevel.service
            10ms rc-local.service
             6ms ureadahead-stop.service
             3ms sys-fs-fuse-connections.mount

```

Bootchart: [https://imagebin.ca/v/2s7xj5xY6hcv](https://imagebin.ca/v/2s7xj5xY6hcv)


Thanks in Advance!

---

