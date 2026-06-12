---
title: "slow booting in 18.10 system"
date: 2019-04-02
forum: Installation &amp; Upgrades
---

### Post by tojonukokhadush on 2019-04-02
i recently network upgraded from 18.04 system to 18.10 system. what i started experiencing is extremely slow booting of the system. earlier in 18.04 system, it was the matter of a blink. how come this happened just because of upgrading? i started hating ubuntu already. :confused::confused::confused: please help, how can i fix this!

---

### Post by Rubi1200 on 2019-04-04
Hi,

please use the link for the boot info summary in my signature and post the results here so we can see what is going on.

Thanks.

---

### Post by tojonukokhadush on 2019-04-04
it did not boot on usb. i would have better downloaded OS itself and fresh installed that in the same time.

---

### Post by tojonukokhadush on 2019-04-04
okay, it worked. here's the url-


[http://paste.ubuntu.com/p/7V62sjZdb7/]("http://pastte.ubuntu.com/p/7V62sjZdb7/")

---

### Post by Rubi1200 on 2019-04-04
I get an error when clicking on the link [https://prnt.sc/n7k794](https://prnt.sc/n7k794)

Can you try pasting the results into the post here using the code tags (Go Advanced >> [https://prnt.sc/n7k7w2](https://prnt.sc/n7k7w2))

Thanks.

---

### Post by oldfred on 2019-04-04
Is this your link. Actual link, not label has extra t in paste.
[http://paste.ubuntu.com/p/7V62sjZdb7/](http://paste.ubuntu.com/p/7V62sjZdb7/)

Post these also (just post first page in code tags to preserve format):
        systemd-analyze 
systemd-analyze blame
systemd-analyze critical-chain

---

### Post by tojonukokhadush on 2019-04-05
i tried the boot repair three times. what i got are-

```
[http://paste.ubuntu.com/p/7V62sjZdb7/](http://paste.ubuntu.com/p/7V62sjZdb7/)
```
```
[http://paste.ubuntu.com/p/8M4k4gFzQj/](http://paste.ubuntu.com/p/8M4k4gFzQj/)
```
```
[http://paste.ubuntu.com/p/cSwfRn2DvB/](http://paste.ubuntu.com/p/cSwfRn2DvB/)
```

---

### Post by tojonukokhadush on 2019-04-05
systemd-analyze

```
Startup finished in 4.297s (kernel) + 1min 9.394s (userspace) = 1min 13.692s
graphical.target reached after 1min 8.968s in userspace
```

systemd-analyze blame

```
         38.212s plymouth-quit-wait.service
         25.437s NetworkManager-wait-online.service
         16.495s networkd-dispatcher.service
         15.394s systemd-journal-flush.service
         13.819s apparmor.service
         13.716s apt-daily-upgrade.service
         12.506s ModemManager.service
         12.198s logrotate.service
         11.967s dev-sda1.device
         11.300s udisks2.service
          9.213s accounts-daemon.service
          7.048s plymouth-read-write.service
          6.923s grub-common.service
          6.549s NetworkManager.service
          6.547s wpa_supplicant.service
          6.231s apport.service
          6.176s systemd-logind.service
          6.156s avahi-daemon.service
          5.870s rsyslog.service
          5.863s thermald.service
          5.858s gpu-manager.service
          5.760s bluetooth.service
          5.361s apport-autoreport.service
          3.882s systemd-udevd.service
          3.418s gdm.service
          1.851s systemd-tmpfiles-clean.service
          1.847s polkit.service
          1.840s networking.service
          1.688s fwupd.service
          1.539s systemd-sysusers.service
          1.252s keyboard-setup.service
          1.237s packagekit.service
          1.131s systemd-modules-load.service
           965ms dns-clean.service
           955ms systemd-resolved.service
           811ms upower.service
           807ms pppd-dns.service
           799ms kmod-static-nodes.service
           771ms systemd-sysctl.service
           750ms systemd-backlight@backlight:acpi_video0.service
           727ms systemd-journald.service
           602ms systemd-random-seed.service
           598ms swapfile.swap
           547ms systemd-tmpfiles-setup.service
           520ms systemd-tmpfiles-setup-dev.service
           506ms switcheroo-control.service
           479ms systemd-user-sessions.service
           478ms openvpn.service
           463ms grub-initrd-fallback.service
           451ms systemd-rfkill.service
           410ms console-setup.service
           385ms kerneloops.service
           363ms systemd-timesyncd.service
           346ms plymouth-start.service
           339ms ifplugd.service
           333ms ifupdown-pre.service
           268ms colord.service
           259ms systemd-udev-trigger.service
           258ms bolt.service
           210ms user@1000.service
           177ms dev-hugepages.mount
           176ms dev-mqueue.mount
           158ms systemd-update-utmp.service
           157ms alsa-restore.service
           128ms systemd-remount-fs.service
            79ms setvtrgb.service
            71ms sys-kernel-debug.mount
            45ms rtkit-daemon.service
            44ms ufw.service
            27ms systemd-update-utmp-runlevel.service
            10ms sys-kernel-config.mount
             4ms sys-fs-fuse-connections.mount

```




systemd-analyze critical-chain

```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.


graphical.target @1min 8.968s
&#9492;&#9472;multi-user.target @1min 8.967s
  &#9492;&#9472;kerneloops.service @55.651s +385ms
    &#9492;&#9472;network-online.target @55.534s
      &#9492;&#9472;NetworkManager-wait-online.service @30.096s +25.437s
        &#9492;&#9472;NetworkManager.service @23.532s +6.549s
          &#9492;&#9472;dbus.service @23.517s
            &#9492;&#9472;basic.target @23.385s
              &#9492;&#9472;paths.target @23.384s
                &#9492;&#9472;cups.path @23.384s
                  &#9492;&#9472;sysinit.target @23.309s
                    &#9492;&#9472;systemd-timesyncd.service @20.989s +363ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @20.419s +547ms
                        &#9492;&#9472;systemd-journal-flush.service @5.022s +15.394s
                          &#9492;&#9472;systemd-journald.service @4.289s +727ms
                            &#9492;&#9472;systemd-journald-audit.socket @4.287s
                              &#9492;&#9472;system.slice @4.140s
                                &#9492;&#9472;-.slice @4.140s



```

---

### Post by oldfred on 2019-04-05
Looks like a lot related to network manager.

       Slow boot issue
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1723809](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1723809)
[https://forums.linuxmint.com/viewtopic.php?t=282437](https://forums.linuxmint.com/viewtopic.php?t=282437)
$ systemctl unmask NetworkManager-wait-online.service
$ systemctl enable NetworkManager-wait-online.service

---

### Post by tojonukokhadush on 2019-04-05
so, whats the final point? masking the network-manager-wait-online-service seems no useful. what exactly would solve this problem then? as the boot was perfectly fine in 18.04 and the upgrade was securely via network. there should be no alteration in the working mechanism logically. i shall share the boot repair recommendation that was generated and i feel its more logical in my scenario. what it says is-

"The boot files of Ubuntu 18.10 are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, sart of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate/boot partition:] option of [Boot Repair]."

Please suggest specific solution.

---

### Post by oldfred on 2019-04-05
Ignore the boot is far from start of disk unless system is very old.
That error message is for old BIOS that could only boot from first 137GB of a drive. Some installs to USB devices may have same type of issue.
But if not booting then better to have a smaller / (root) inside first 137GB and use rest of drive as /home or data partition(s).
Have yet to see a newer UEFI based system have trouble booting because of issue of where boot files are on drive.

Best to add to bug report with your info. And follow it to see if someone posts a workaround or if bug if fixed and you can separately update.

One other issue is related to snaps. If you use snaps, they you need to keep them. I uninstall all of them.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) &

---

### Post by tojonukokhadush on 2019-04-07
this seems too messy. i shall better wait some days for 19.04 to be released. hope problem would be solved then. thank you for the help.

---

