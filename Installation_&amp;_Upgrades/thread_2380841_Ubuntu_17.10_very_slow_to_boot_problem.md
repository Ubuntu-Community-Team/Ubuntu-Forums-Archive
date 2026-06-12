---
title: "Ubuntu 17.10 very slow to boot problem"
date: 2017-12-22
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2017-12-22
Hi 
I have upgrade from ubuntu 16.04 to 17.10 now it takes about 5 minutes to boot the computer.
need help

Tks

---

### Post by vasa1 on 2017-12-23
Post the output of```
systemd-analyze blame
```for people to look at.

---

### Post by hoboy on 2017-12-23
systemd-analyze blame
    1min 47.106s plymouth-quit-wait.service
    1min 43.281s apt-daily.service
    1min 25.822s docker.service
     1min 9.666s [email]postgresql@9.6-main.servic[/email]e
     1min 1.335s [email]postgresql@9.5-main.servic[/email]e
         41.623s libvirtd.service
         38.263s lxd-containers.service
         30.815s nmbd.service
         29.371s snapd.service
         27.977s teamviewerd.service
         27.402s [email]tor@default.servic[/email]e
         22.152s systemd-resolved-update-resolvconf.service
         22.118s apparmor.service
         18.780s NetworkManager-wait-online.service
         18.012s ebtables.service
         17.251s NetworkManager.service
         16.992s dev-sda1.device
         15.606s ModemManager.service
         14.609s udisks2.service
         13.435s apt-daily-upgrade.service
         12.920s accounts-daemon.service
         12.130s lxc-net.service
         11.303s gpu-manager.service
          9.905s plymouth-read-write.service
          8.514s mono-xsp4.service
          8.435s odoo.service
          7.973s speech-dispatcher.service
          7.428s apport.service
          6.964s networking.service
          6.687s alsa-restore.service
          6.681s tor.service
          6.668s monopd.service
          6.268s winbind.service
          6.268s smbd.service
          6.050s bluetooth.service
          5.608s colord.service
          5.165s elasticsearch.service
          4.618s virtualbox.service
          4.528s polkit.service
          4.215s thermald.service
          4.108s qemu-kvm.service
          3.765s lxc.service
          3.723s rsyslog.service
          3.675s ssh.service
          3.648s binfmt-support.service
          3.345s gdm.service
          3.269s grub-common.service
          3.252s systemd-tmpfiles-setup.service
          2.836s upower.service
          2.731s fwupd.service
          2.702s [email]user@135.servic[/email]e
          2.700s lvm2-monitor.service
          2.217s keyboard-setup.service
          2.070s systemd-logind.service
          1.862s snap-pycharm\x2dprofessional-43.mount
          1.787s sys-kernel-debug.mount
          1.784s dev-mqueue.mount
          1.781s dev-hugepages.mount
          1.748s avahi-daemon.service
          1.711s systemd-tmpfiles-setup-dev.service
          1.688s plymouth-start.service
          1.639s snap-core-3604.mount
          1.604s systemd-udevd.service
          1.491s packagekit.service
          1.380s snap-pycharm\x2dprofessional-45.mount
          1.209s snap-core-3440.mount
          1.156s wpa_supplicant.service
          1.136s systemd-modules-load.service
          1.020s dev-loop1.device
           978ms console-setup.service
           976ms systemd-random-seed.service
           972ms systemd-resolved.service
           959ms dev-loop0.device
           949ms systemd-rfkill.service
           947ms systemd-user-sessions.service
           826ms dns-clean.service
           804ms schroot.service
           778ms dev-loop2.device
           757ms systemd-journal-flush.service
           754ms sysstat.service
           718ms systemd-udev-trigger.service
           650ms pppd-dns.service
           621ms systemd-timesyncd.service
           591ms sys-kernel-config.mount
           585ms sys-fs-fuse-connections.mount
           562ms kerneloops.service
           472ms vsftpd.service
    1min 47.106s plymouth-quit-wait.service
    1min 43.281s apt-daily.service
    1min 25.822s docker.service
     1min 9.666s [email]postgresql@9.6-main.servic[/email]e
     1min 1.335s [email]postgresql@9.5-main.servic[/email]e
         41.623s libvirtd.service
         38.263s lxd-containers.service
         30.815s nmbd.service
         29.371s snapd.service
         27.977s teamviewerd.service
         27.402s [email]tor@default.servic[/email]e
         22.152s systemd-resolved-update-resolvconf.service
         22.118s apparmor.service
         18.780s NetworkManager-wait-online.service
         18.012s ebtables.service
         17.251s NetworkManager.service
         16.992s dev-sda1.device
         15.606s ModemManager.service
         14.609s udisks2.service
         13.435s apt-daily-upgrade.service
         12.920s accounts-daemon.service
         12.130s lxc-net.service
         11.303s gpu-manager.service
lines 1-23/110 21%

---

