---
title: "Mint 18.1 mate slow boot"
date: 2016-12-20
forum: MINT
---

### Post by martin154 on 2016-12-20
Hi All,

A couple of days ago I installed the latest 18.1 Mate 64b. Everything went well, the only problem is a relatively slow boot. Here the report using the command systemd-analyze blame

9.998s dev-sda2.device
7.041s ModemManager.service
6.740s accounts-daemon.service
6.242s NetworkManager.service
5.113s loadcpufreq.service
4.641s grub-common.service
3.148s thermald.service
3.137s virtualbox-guest-utils.service
2.980s polkitd.service
2.919s systemd-udevd.service
2.768s systemd-logind.service
2.766s networking.service
2.763s lvm2-monitor.service
2.663s rsyslog.service
2.661s lm-sensors.service
2.527s irqbalance.service
1.783s systemd-tmpfiles-setup-dev.service
1.773s keyboard-setup.service
1.473s ondemand.service
1.395s avahi-daemon.service
1.346s bluetooth.service
1.314s iio-sensor-proxy.service
1.311s console-kit-log-system-start.service

any tips on what I could disable and how in order to speed up boot?

Thanks in advance
Martin

---

