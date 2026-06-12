---
title: "lubuntu 16.04 fresh setup boots extremely slow"
date: 2016-10-30
forum: Installation &amp; Upgrades
---

### Post by paunik on 2016-10-30
lubuntu 16.04 32bit on Asus eee pc 900 2GB RAM boots almost 3 minutes, most of it screen blank.
Can somebody hint to newcomer where the problem lies.

Thanks!
(dmesg.zip attached)


systemd-analyze
Startup finished in 5.327s (kernel) + 2min 47.041s (userspace) = 2min 52.368s


systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

```
graphical.target @2min 46.761s
 multi-user.target @2min 46.759s
  getty.target @2min 46.756s
    [EMAIL="getty@tty1.servic"]getty@tty1.servic[/EMAIL]e @2min 46.746s
      rc-local.service @2min 46.247s +64ms
        network-online.target @2min 46.245s
          NetworkManager-wait-online.service @2min 39.002s +7.242s
            NetworkManager.service @2min 37.628s +1.338s
              dbus.service @2min 37.537s
                basic.target @2min 37.394s
                  sockets.target @2min 37.393s
                    pcscd.socket @2min 37.390s
                      sysinit.target @2min 37.373s
                        apparmor.service @6.515s +2min 30.844s
                          local-fs.target @6.491s
                            run-user-1000-gvfs.mount @2min 44.037s
                              run-user-1000.mount @2min 41.263s
                                local-fs-pre.target @2.091s
                                  systemd-remount-fs.service @1.986s +49ms
                                    systemd-journald.socket @421ms

systemd-analyze blame
2min 30.844s apparmor.service
    2min 30.543s plymouth-read-write.service
          7.242s NetworkManager-wait-online.service
          4.695s dev-sda1.device
          2.202s systemd-rfkill.service
          2.194s systemd-tmpfiles-setup.service
          1.858s ModemManager.service
          1.753s ufw.service
          1.734s networking.service
          1.730s accounts-daemon.service
          1.544s systemd-logind.service
          1.441s upower.service
          1.338s NetworkManager.service
          1.281s console-setup.service
          1.171s irqbalance.service
          1.164s grub-common.service
          1.083s apport.service
           920ms ondemand.service
           787ms lightdm.service
           776ms systemd-journald.service
           669ms systemd-fsck@dev-disk-by\x2duuid-98575ca6\x2d8199\x2d4918\x2d9c
           664ms systemd-fsck@dev-disk-by\x2duuid-40090a5b\x2de846\x2d4373\x2da9
           661ms systemd-journal-flush.service
           660ms gpu-manager.service
           595ms keyboard-setup.service
           499ms systemd-udev-trigger.service
           401ms alsa-restore.service
           390ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
           380ms ntp.service
           368ms polkitd.service
           346ms udisks2.service
           317ms pppd-dns.service
           313ms rsyslog.service
           250ms systemd-update-utmp-runlevel.service
           233ms systemd-udevd.service
           178ms systemd-random-seed.service
           173ms resolvconf.service
           166ms dev-mqueue.mount
           165ms kmod-static-nodes.service
           163ms systemd-modules-load.service
           117ms home.mount
           103ms systemd-update-utmp.service
           101ms sys-kernel-debug.mount
            91ms wpa_supplicant.service
            82ms var.mount
            80ms dev-disk-by\x2duuid-e85a8779\x2dee02\x2d42b1\x2d9a8a\x2da22bbfb
            79ms plymouth-start.service
            79ms systemd-tmpfiles-setup-dev.service
            74ms dev-hugepages.mount
            71ms systemd-user-sessions.service
            71ms setvtrgb.service
            64ms rc-local.service
            60ms systemd-sysctl.service
            60ms systemd-tmpfiles-clean.service
            58ms sys-fs-fuse-connections.mount
            57ms [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
            52ms [EMAIL="systemd-backlight@backlight:eeepc.servic"]systemd-backlight@backlight:eeepc.servic[/EMAIL]e
            49ms systemd-remount-fs.service
            37ms ureadahead-stop.service
            17ms plymouth-quit-wait.service
```

---

### Post by DieB on 2016-10-30
Hi, your  systemd-analyze critical-chain clearly shows the culprit  > apparmor.service @6.515s +2min 30.844s. Have you installed any extr apparmor packages besides the ones that ship with standard installation?

---

### Post by paunik on 2016-10-30
[I][COLOR=#000000]"Have you installed any extr apparmor packages besides the ones that ship with standard installation?"
[/COLOR][/I][COLOR=#000000]No.
But what should be the fix to be then?[/COLOR]

---

### Post by DieB on 2016-10-31
Hi, i stuck my nose into the interwebs and your dmesg and still am quite clueless. 

Yet my steps (if it were my system) would be to try these things separately and check boot times again - **pelase reset settings to original if there is no change in boottime after the changes**

[LIST]
[*] disable splash in grub
run in a terminal
```
sudo gedit /etc/default/grub
```
change 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```
save and run in terminal
```
sudo update-grub
```
reboot and check `systemd-analyze` and `systemd-analyze blame`again


[*] add following options to grub 
that it looks like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_backlight=vendor"
```
sudo update-grub again and reboot and check times again


[*] disable plymouth
change grub line to look like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet noplymouth"
```
sudo update-grub again and reboot and check times again


[*] check the status of apparmor profiles
in a terminal type 
```
sudo aa-status
```
and if there are no profiles in enforce mode (as my brief look on your dmesg might suggest) or even if there are, disable apparmor for test reasons with folloing command in a terminal 
```
sudo systemctl disable apparmor
```
reboot and check times again -  if no change re-enable again by running above command with enable instead of disable
[/LIST]

please let me know what the effects were

plus I noticed you might have some weired configueration with three harddrives and 5 partitions - like swap on /dev/sdb1? this might also be a reason for lame boot times, pls tell us more about your setup.

---

### Post by wildmanne39 on 2016-10-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by paunik on 2016-11-06
disabling splash in grub gave systemd-analyze output: Startup finished in 5.387s (kernel) + 21.320s (userspace) = 26.707s

adding acpi_backlight=vendor instead splash gave systemd-analyze output: Startup finished in 5.394s (kernel) + 21.330s (userspace) = 26.725s

adding noplymouth instead splash gave systemd-analyze output: Startup finished in 5.397s (kernel) + 21.306s (userspace) = 26.704s

so disabling splash seems to be the solution... thanks!

I'ts a Asus eee pc 900 with a slow proprietary mPCI 4GB ssd and very slow proprietary mPCI 16GB ssd and to give to system some kind of disk space I moved swap, /var and /home to the 16GB slow ssd...

---

