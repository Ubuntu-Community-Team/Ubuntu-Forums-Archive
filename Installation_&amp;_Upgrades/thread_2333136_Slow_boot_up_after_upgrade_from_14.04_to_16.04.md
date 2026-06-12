---
title: "Slow boot up after upgrade from 14.04 to 16.04"
date: 2016-08-07
forum: Installation &amp; Upgrades
---

### Post by michaelbr on 2016-08-07
Greetings all:
I just upgraded Ubuntu from 14.04 to 16.04, my system is as follows:
          product: Intel(R) Core(TM) i3-3110M CPU @ 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1238MHz
          capacity: 2400MHz
          width: 64 bits

After the upgrade I got an "shim-signed" error, and also the boot time is higher than 14.04, how or what adjustment can I do to speed up the boot time?
ps: the shim-signed error was fixed by using the following instructions:
sudo apt-get purge grub\*
sudo apt-get install grub-efi
sudo apt-get autoremove
sudo update-grub

---

### Post by transit72 on 2016-10-09
I have the same problem with my Dell laptop:
Dell Inspiron 3542
CPU: Intel® Core™ i3-4005U CPU @ 1.70GHz × 4 
Memory: 4GB
HDD: 220GB
Additional Drivers: [ATTACH=CONFIG]271567[/ATTACH]

I  had Ubuntu 14.04 (in dual boot with Windows 8.1) and it would boot in  less than a minute! A few weeks ago I decided to upgrade it to 16.04 and  since then it takes about 4 minutes to boot :(
*systemd-analyze* says:
```
Startup finished in 7.235s (firmware) + 5.170s (loader) + 3.778s (kernel) + 3min 34.953s (userspace) = 3min 51.138s
```
and *systemd-analyze blame *gives:
```
    3min 346ms powerd.service
         26.801s NetworkManager-wait-online.service
         23.279s networking.service
         21.081s click-system-hooks.service
         19.512s snapd.firstboot.service
         15.699s systemd-user-sessions.service
         15.698s rsyslog.service
         15.698s iio-sensor-proxy.service
          9.130s nmbd.service
          9.114s winbind.service
          9.045s dev-sda7.device
          8.570s samba-ad-dc.service
          8.014s irqbalance.service
          7.915s speech-dispatcher.service
          7.893s apport.service
          7.613s grub-common.service
          7.602s ondemand.service
          4.380s accounts-daemon.service
          3.613s apparmor.service
          3.535s systemd-fsck@dev-disk-by\x2duuid-C0EE\x2d8DE3.service
          3.227s NetworkManager.service
          2.584s plymouth-start.service
          2.454s gpu-manager.service
          1.759s user@1000.service
          1.733s systemd-udevd.service
          1.688s keyboard-setup.service
          1.527s systemd-tmpfiles-setup-dev.service
          1.279s polkitd.service
          1.227s thermald.service
          1.104s avahi-daemon.service
          1.056s systemd-timesyncd.service
           956ms bluetooth.service
           934ms dev-mqueue.mount
           931ms dev-hugepages.mount
           904ms console-setup.service
           728ms systemd-rfkill.service
           712ms systemd-modules-load.service
           709ms lightdm.service
           694ms plymouth-quit-wait.service
           658ms systemd-logind.service
           648ms systemd-backlight@backlight:intel_backlight.service
           620ms ofono.service
           547ms upower.service
           546ms systemd-journald.service
           541ms alsa-restore.service
           541ms sys-kernel-debug.mount
           537ms binfmt-support.service
           434ms udisks2.service
           419ms smbd.service
           408ms dev-sda8.swap
           389ms ufw.service
           384ms systemd-tmpfiles-setup.service
           323ms systemd-sysctl.service
           302ms systemd-update-utmp.service
           297ms systemd-backlight@leds:dell::kbd_backlight.service
           295ms boot-efi.mount
           273ms proc-sys-fs-binfmt_misc.mount
           247ms colord.service
           221ms dns-clean.service
           205ms systemd-udev-trigger.service
           175ms pppd-dns.service
           155ms resolvconf.service
           151ms rtkit-daemon.service
           147ms systemd-localed.service
           127ms kmod-static-nodes.service
           123ms wpa_supplicant.service
           112ms systemd-hostnamed.service
            83ms snapd.socket
            76ms systemd-journal-flush.service
            74ms plymouth-read-write.service
            70ms systemd-tmpfiles-clean.service
            66ms systemd-remount-fs.service
            65ms systemd-random-seed.service
            59ms sys-fs-fuse-connections.mount
            53ms setvtrgb.service
            42ms openvpn.service
            24ms rc-local.service
            21ms systemd-update-utmp-runlevel.service
            14ms snapd.boot-ok.service
             9ms ureadahead-stop.service
```

Is there a way to speed up this powerd.service?

---

### Post by transit72 on 2016-10-13
After googling around I found this [https://bugs.launchpad.net/powerd/+bug/1443278](https://bugs.launchpad.net/powerd/+bug/1443278). So I went ahead and disabled the powerd.service and also removed it completely from my system. Boot time has greatly improved, but I would still like to know how it came to be installed in my system in the first place. Could it be a leftover from 14.04 that wasn't removed or did it come with the upgrade to 16.04? Any ideas anyone?

---

