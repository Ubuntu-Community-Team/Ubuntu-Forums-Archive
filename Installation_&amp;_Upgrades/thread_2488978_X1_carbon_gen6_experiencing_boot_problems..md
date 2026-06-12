---
title: "X1 carbon gen6 experiencing boot problems."
date: 2023-07-14
forum: Installation &amp; Upgrades
---

### Post by jessebett on 2023-07-14
This the pastebin link to my boot-repair info. [https://paste.ubuntu.com/p/yZ4J4bF4RW/](https://paste.ubuntu.com/p/yZ4J4bF4RW/) . Ubuntu 23.04. My laptop initially used to boot with no issues but after two months of use, It takes 3 - 5 minutes to boot on average, sometimes it fails to boot and apps such as chrome take two minutes to open and sometimes crash after a cold boot. The system generally feels very laggy after a cold boot. This was not the case during the first few weeks after the clean install.CPU temperatures easily hit 96 degrees celcius which was not the case after OS initial installation. Please help.

---

### Post by tea for one on 2023-07-14
```
systemd-analyze blame
```
Run this command after booting successfully, it should show some pertinent info.

---

### Post by jessebett on 2023-07-15
After running **systemd-analyze blame** , this is the output.
```

2min 44.988s plymouth-quit-wait.service
2min 41.933s e2scrub_reap.service
2min 21.468s mysql.service
1min 18.113s snapd.service
1min 14.926s apport.service
1min 12.146s user@125.service
  1min 301ms udisks2.service
     59.898s snapd.seeded.service
     47.818s phpsessionclean.service
     47.539s ModemManager.service
     42.825s NetworkManager.service
     41.972s accounts-daemon.service
     26.721s avahi-daemon.service
     26.717s bluetooth.service
     26.673s dbus.service
     26.015s NetworkManager-wait-online.service
     25.519s grub-common.service
     24.093s systemd-tmpfiles-clean.service
     18.954s power-profiles-daemon.service
     17.678s polkit.service
     17.186s rsyslog.service
     16.894s secureboot-db.service
     14.559s switcheroo-control.service
     14.551s thermald.service
     14.551s systemd-logind.service
     12.166s gpu-manager.service
     12.005s update-notifier-download.service
      7.144s upower.service
      6.425s wpa_supplicant.service
      5.853s apache2.service
      5.180s fwupd.service
      4.707s bolt.service
      4.424s dev-loop25.device
      4.422s dev-loop27.device
      4.422s dev-loop29.device
      4.421s dev-loop26.device
      4.420s dev-loop28.device
      4.418s dev-loop35.device
      4.415s dev-loop30.device
      4.411s dev-loop37.device
      4.407s dev-loop36.device
      3.629s systemd-modules-load.service
      3.365s modprobe@drm.service
      3.273s dev-loop33.device
      3.271s dev-loop31.device
      3.259s dev-loop32.device
      3.047s dev-loop23.device
      3.010s dev-loop20.device
      3.003s dev-loop19.device
      2.993s dev-loop21.device
      2.980s dev-loop34.device
      2.958s dev-loop18.device
      2.958s dev-loop15.device
      2.947s dev-loop17.device
      2.912s dev-loop16.device
      2.906s dev-loop12.device
      2.844s dev-loop22.device
      2.834s dev-loop14.device
      2.816s dev-loop9.device
      2.770s dev-loop11.device
      2.754s dev-loop13.device
      2.741s dev-loop10.device
      2.729s dev-loop24.device
      2.556s dev-loop8.device
      2.370s boot-efi.mount
      2.253s kerneloops.service
      2.229s cups.service
      1.797s gdm.service
      1.277s systemd-oomd.service
      1.274s systemd-resolved.service
      1.267s systemd-timesyncd.service
      1.117s apparmor.service
       951ms systemd-rfkill.service
       904ms systemd-tmpfiles-setup.service
       658ms openvpn.service
       582ms dev-sda2.device
       438ms systemd-user-sessions.service
       309ms snap-bare-5.mount
       301ms snapd.apparmor.service
       297ms snap-code-133.mount
       290ms snap-code-134.mount
       271ms snap-core-15419.mount
       265ms snap-core-15511.mount
       257ms snap-core18-2751.mount
       246ms snap-core18-2785.mount
       242ms snap-core20-1950.mount
       238ms snap-core20-1974.mount
       234ms snap-core22-806.mount
       230ms snap-core22-817.mount
       225ms snap-discord-153.mount
       220ms snap-figma\x2dlinux-156.mount
       220ms user@1000.service
       216ms systemd-binfmt.service
       215ms snap-firefox-2880.mount
       215ms systemd-udevd.service
       211ms snap-firefox-2908.mount
       205ms snap-gnome\x2d3\x2d28\x2d1804-198.mount
       203ms grub-initrd-fallback.service
       200ms snap-gnome\x2d3\x2d34\x2d1804-93.mount
       196ms snap-gnome\x2d3\x2d38\x2d2004-140.mount
       192ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
       185ms snap-gnome\x2d42\x2d2204-111.mount
       184ms colord.service
       179ms snap-gnome\x2d42\x2d2204-120.mount
       174ms systemd-udev-trigger.service
       168ms systemd-journald.service
       168ms keyboard-setup.service
       167ms snap-gtk\x2dcommon\x2dthemes-1535.mount
       158ms snap-htop-3735.mount
       154ms snap-htop-3758.mount
       149ms snap-lsd-62.mount
       145ms snap-postman-207.mount
       140ms snap-postman-209.mount
       135ms snap-shortwave-79.mount
       130ms systemd-update-utmp.service
       130ms snap-slack-79.mount
       125ms snap-slack-82.mount
       118ms snap-snap\x2dstore-558.mount
       118ms systemd-fsck@dev-disk-by\x2duuid-1B6C\x2d99AB.service
       112ms snap-snap\x2dstore-959.mount
       106ms snap-snapd-19361.mount
       103ms systemd-journal-flush.service
        99ms snap-snapd-19457.mount
        94ms snap-snapd\x2ddesktop\x2dintegration-83.mount
        87ms snap-spotify-67.mount
        81ms console-setup.service
        80ms snap-webstorm-323.mount
        76ms plymouth-read-write.service
        74ms snap-webstorm-327.mount
        66ms var-snap-firefox-common-host\x2dhunspell.mount
        64ms proc-sys-fs-binfmt_misc.mount
        58ms ufw.service
        51ms systemd-remount-fs.service
        46ms plymouth-start.service
        45ms sys-kernel-debug.mount
2min 44.988s plymouth-quit-wait.service
2min 41.933s e2scrub_reap.service
2min 21.468s mysql.service
1min 18.113s snapd.service
1min 14.926s apport.service
1min 12.146s user@125.service
  1min 301ms udisks2.service
     59.898s snapd.seeded.service
     47.818s phpsessionclean.service
     47.539s ModemManager.service
     42.825s NetworkManager.service
     41.972s accounts-daemon.service
     26.721s avahi-daemon.service
     26.717s bluetooth.service
     26.673s dbus.service
     26.015s NetworkManager-wait-online.service
     25.519s grub-common.service
     24.093s systemd-tmpfiles-clean.service
     18.954s power-profiles-daemon.service
     17.678s polkit.service
     17.186s rsyslog.service
     16.894s secureboot-db.service
     14.559s switcheroo-control.service
     14.551s thermald.service
     14.551s systemd-logind.service
     12.166s gpu-manager.service
     12.005s update-notifier-download.service
      7.144s upower.service
      6.425s wpa_supplicant.service
      5.853s apache2.service
      5.180s fwupd.service
      4.707s bolt.service
      4.424s dev-loop25.device
      4.422s dev-loop27.device
      4.422s dev-loop29.device
      4.421s dev-loop26.device
      4.420s dev-loop28.device
      4.418s dev-loop35.device
      4.415s dev-loop30.device
      4.411s dev-loop37.device
      4.407s dev-loop36.device
      3.629s systemd-modules-load.service
      3.365s modprobe@drm.service
      3.273s dev-loop33.device
      3.271s dev-loop31.device
      3.259s dev-loop32.device
      3.047s dev-loop23.device
      3.010s dev-loop20.device
      3.003s dev-loop19.device
      2.993s dev-loop21.device
      2.980s dev-loop34.device
      2.958s dev-loop18.device
      2.958s dev-loop15.device
      2.947s dev-loop17.device
      2.912s dev-loop16.device
      2.906s dev-loop12.device
      2.844s dev-loop22.device
      2.834s dev-loop14.device
      2.816s dev-loop9.device
      2.770s dev-loop11.device
      2.754s dev-loop13.device
      2.741s dev-loop10.device
      2.729s dev-loop24.device
      2.556s dev-loop8.device
      2.370s boot-efi.mount
      2.253s kerneloops.service
      2.229s cups.service
      1.797s gdm.service
      1.277s systemd-oomd.service
      1.274s systemd-resolved.service
      1.267s systemd-timesyncd.service
      1.117s apparmor.service
       951ms systemd-rfkill.service
       904ms systemd-tmpfiles-setup.service
       658ms openvpn.service
       582ms dev-sda2.device
       438ms systemd-user-sessions.service
       309ms snap-bare-5.mount
       301ms snapd.apparmor.service
       297ms snap-code-133.mount
       290ms snap-code-134.mount
       271ms snap-core-15419.mount
       265ms snap-core-15511.mount
       257ms snap-core18-2751.mount
       246ms snap-core18-2785.mount
       242ms snap-core20-1950.mount
       238ms snap-core20-1974.mount
       234ms snap-core22-806.mount
       230ms snap-core22-817.mount
       225ms snap-discord-153.mount
       220ms snap-figma\x2dlinux-156.mount
       220ms user@1000.service
       216ms systemd-binfmt.service
       215ms snap-firefox-2880.mount
       215ms systemd-udevd.service
       211ms snap-firefox-2908.mount
       205ms snap-gnome\x2d3\x2d28\x2d1804-198.mount
       203ms grub-initrd-fallback.service
       200ms snap-gnome\x2d3\x2d34\x2d1804-93.mount
       196ms snap-gnome\x2d3\x2d38\x2d2004-140.mount
       192ms snap-gnome\x2d3\x2d38\x2d2004-143.mount
       185ms snap-gnome\x2d42\x2d2204-111.mount
       184ms colord.service
       179ms snap-gnome\x2d42\x2d2204-120.mount
       174ms systemd-udev-trigger.service
       168ms systemd-journald.service
       168ms keyboard-setup.service
       167ms snap-gtk\x2dcommon\x2dthemes-1535.mount
       158ms snap-htop-3735.mount
       154ms snap-htop-3758.mount
       149ms snap-lsd-62.mount
       145ms snap-postman-207.mount
       140ms snap-postman-209.mount
       135ms snap-shortwave-79.mount
       130ms systemd-update-utmp.service
       130ms snap-slack-79.mount
       125ms snap-slack-82.mount
       118ms snap-snap\x2dstore-558.mount
       118ms systemd-fsck@dev-disk-by\x2duuid-1B6C\x2d99AB.service
       112ms snap-snap\x2dstore-959.mount
       106ms snap-snapd-19361.mount
       103ms systemd-journal-flush.service
        99ms snap-snapd-19457.mount
        94ms snap-snapd\x2ddesktop\x2dintegration-83.mount
        87ms snap-spotify-67.mount
        81ms console-setup.service
        80ms snap-webstorm-323.mount
        76ms plymouth-read-write.service
        74ms snap-webstorm-327.mount
        66ms var-snap-firefox-common-host\x2dhunspell.mount
        64ms proc-sys-fs-binfmt_misc.mount
        58ms ufw.service
        51ms systemd-remount-fs.service
        46ms plymouth-start.service
        45ms sys-kernel-debug.mount
        44ms dev-hugepages.mount
        44ms dev-mqueue.mount
        44ms sys-kernel-tracing.mount
        42ms systemd-sysusers.service
        38ms kmod-static-nodes.service
        38ms modprobe@configfs.service
        34ms modprobe@fuse.service
        34ms rtkit-daemon.service
        32ms systemd-backlight@leds:tpacpi::kbd_backlight.service
        32ms systemd-random-seed.service
        31ms systemd-tmpfiles-setup-dev.service
        21ms systemd-backlight@backlight:intel_backlight.service
        20ms user-runtime-dir@125.service
        20ms snapd.socket
        16ms swapfile.swap
        15ms user-runtime-dir@1000.service
        13ms systemd-sysctl.service
        10ms systemd-update-utmp-runlevel.service
         9ms setvtrgb.service
         9ms alsa-restore.service
         5ms sys-fs-fuse-connections.mount
         5ms modprobe@efi_pstore.service
         3ms sys-kernel-config.mount

```

After running **systemd-analyze critical-chain**

```

graphical.target @4min 4.773s
&#9492;&#9472;multi-user.target @4min 4.773s
  &#9492;&#9472;plymouth-quit-wait.service @1min 19.783s +2min 44.988s
    &#9492;&#9472;systemd-user-sessions.service @1min 19.320s +438ms
      &#9492;&#9472;network.target @1min 16.446s
        &#9492;&#9472;NetworkManager.service @33.618s +42.825s
          &#9492;&#9472;dbus.service @6.907s +26.673s
            &#9492;&#9472;basic.target @6.894s
              &#9492;&#9472;sockets.target @6.894s
                &#9492;&#9472;snapd.socket @6.874s +20ms
                  &#9492;&#9472;sysinit.target @6.870s
                    &#9492;&#9472;snapd.apparmor.service @6.568s +301ms
                      &#9492;&#9472;apparmor.service @4.248s +1.117s
                        &#9492;&#9472;local-fs.target @4.182s
                          &#9492;&#9472;run-snapd-ns-snapd\x2ddesktop\x2dintegration.mnt.mo>
                            &#9492;&#9472;run-snapd-ns.mount @2min 35.504s
                              &#9492;&#9472;local-fs-pre.target @966ms
                                &#9492;&#9472;systemd-tmpfiles-setup-dev.service @934ms +31>
                                  &#9492;&#9472;systemd-sysusers.service @836ms +42ms
                                    &#9492;&#9472;systemd-remount-fs.service @780ms +51ms
                                      &#9492;&#9472;systemd-journald.socket @757ms
                                        &#9492;&#9472;system.slice @733ms
                                          &#9492;&#9472;-.slice @733ms



```

---

### Post by oldfred on 2023-07-15
Some things to review:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

Ubuntu is converting everything to snaps.
I am not a fan of snaps and do not have them installed in my Kubuntu install.

boot time cut in half by removing snap, they since have improved boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)

---

### Post by tea for one on 2023-07-15
As your PC booted in a timely fashion after your initial installation, I wonder if a recent kernel has caused the slower boot.
Can you try an older kernel via Advanced Options in the Grub menu?

---

### Post by jessebett on 2023-07-17
Thank you for your reply, turning off [COLOR=#000000]NetworkManager-wait   reduced the boot time.[/COLOR]

---

