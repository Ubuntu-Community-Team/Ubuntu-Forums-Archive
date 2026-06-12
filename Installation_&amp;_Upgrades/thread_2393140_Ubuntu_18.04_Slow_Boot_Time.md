---
title: "Ubuntu 18.04 Slow Boot Time"
date: 2018-05-30
forum: Installation &amp; Upgrades
---

### Post by dvira on 2018-05-30
I've recently installed Ubuntu 18.04 Desktop on my PC (which earlier had  Windows 10). However, I noticed it takes a few minutes to boot,  sometimes 4-5 mins. From past experience with Ubuntu I know this is too  much and that it can boot in seconds. I've run a few commands to find out what is taking time but I an unable  to figure out what to do with the information. I'm pasting the output here:
```
Startup finished in 1min 28.110s (kernel) + 2min 4.802s (userspace) = 3min 32.912s
graphical.target reached after 22.914s in userspace
     2min 3.939s fstrim.service
         46.368s apt-daily.service
         21.356s plymouth-quit-wait.service
          4.226s NetworkManager-wait-online.service
          3.188s apt-daily-upgrade.service
          1.117s fwupd.service
           800ms colord.service
           611ms NetworkManager.service
           579ms dev-sda2.device
           546ms udisks2.service
           429ms ModemManager.service
           427ms accounts-daemon.service
           416ms upower.service
           375ms networkd-dispatcher.service
           350ms plymouth-start.service
           322ms systemd-logind.service
           319ms polkit.service
           302ms dev-loop0.device
           275ms dev-loop1.device
           255ms dev-loop5.device
           250ms dev-loop2.device
           249ms dev-loop4.device
           248ms dev-loop3.device
           197ms gdm.service
           173ms packagekit.service
           172ms thermald.service
           170ms systemd-journal-flush.service
           148ms user@1000.service
           140ms systemd-modules-load.service
           127ms systemd-resolved.service
           126ms keyboard-setup.service
           123ms systemd-timesyncd.service
            98ms snapd.seeded.service
            97ms grub-common.service
            89ms swapfile.swap
            87ms snap-core-4486.mount
            87ms systemd-rfkill.service
            81ms systemd-udev-trigger.service
            78ms apport.service
            75ms bolt.service
            72ms snap-gnome\x2dcalculator-154.mount
            62ms snap-gnome\x2dlogs-25.mount
            59ms snap-gnome\x2dsystem\x2dmonitor-36.mount
            57ms wpa_supplicant.service
            57ms apparmor.service
            55ms systemd-journald.service
            54ms bluetooth.service
            53ms avahi-daemon.service
            43ms speech-dispatcher.service
            42ms dev-loop8.device
            42ms snap-gnome\x2dsystem\x2dmonitor-39.mount
            40ms gpu-manager.service
            39ms snap-core-4650.mount
            38ms pppd-dns.service
            37ms snap-gnome\x2dcalculator-167.mount
            36ms systemd-fsck@dev-disk-by\x2duuid-1F60\x2dF1CD.service
            35ms rsyslog.service
            35ms dev-loop11.device
            32ms dev-loop9.device
            32ms snap-gnome\x2d3\x2d26\x2d1604-59.mount
            31ms systemd-udevd.service
            29ms snap-gnome\x2d3\x2d26\x2d1604-64.mount
            29ms systemd-tmpfiles-setup-dev.service
            28ms snap-gnome\x2dcharacters-86.mount
            27ms dev-loop10.device
            27ms snapd.service
            26ms snap-gnome\x2dlogs-31.mount
            23ms alsa-restore.service
            17ms networking.service
            13ms kmod-static-nodes.service
            13ms snap-gnome\x2dcharacters-69.mount
            12ms setvtrgb.service
            12ms plymouth-read-write.service
            11ms systemd-tmpfiles-setup.service
            10ms sys-kernel-debug.mount
            10ms dev-hugepages.mount
            10ms systemd-sysctl.service
             8ms kerneloops.service
             8ms systemd-tmpfiles-clean.service
             8ms systemd-random-seed.service
             7ms systemd-remount-fs.service
             7ms ufw.service
             6ms dev-mqueue.mount
             6ms sys-kernel-config.mount
             6ms dev-loop7.device
             6ms sys-fs-fuse-connections.mount
             6ms dev-loop6.device
             6ms boot-efi.mount
             5ms systemd-update-utmp-runlevel.service
             5ms dns-clean.service
             4ms systemd-update-utmp.service
             4ms console-setup.service
             4ms ureadahead-stop.service
             3ms rtkit-daemon.service
             2ms systemd-user-sessions.service
             1ms snapd.socket
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @22.914s
&#9492;&#9472;multi-user.target @22.914s
  &#9492;&#9472;kerneloops.service @5.781s +8ms
    &#9492;&#9472;network-online.target @5.780s
      &#9492;&#9472;NetworkManager-wait-online.service @1.553s +4.226s
        &#9492;&#9472;NetworkManager.service @939ms +611ms
          &#9492;&#9472;dbus.service @864ms
            &#9492;&#9472;basic.target @861ms
              &#9492;&#9472;sockets.target @861ms
                &#9492;&#9472;snapd.socket @860ms +1ms
                  &#9492;&#9472;sysinit.target @858ms
                    &#9492;&#9472;systemd-timesyncd.service @735ms +123ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @719ms +11ms
                        &#9492;&#9472;local-fs.target @715ms
                          &#9492;&#9472;run-user-1000-gvfs.mount @9.561s
                            &#9492;&#9472;run-user-1000.mount @2.032s
                              &#9492;&#9472;local-fs-pre.target @235ms
                                &#9492;&#9472;keyboard-setup.service @108ms +126ms
                                  &#9492;&#9472;systemd-journald.socket @105ms
                                    &#9492;&#9472;system.slice @105ms
                                      &#9492;&#9472;-.slice @103ms
```

Any pointers/help in reducing boot time is appreciated.

---

