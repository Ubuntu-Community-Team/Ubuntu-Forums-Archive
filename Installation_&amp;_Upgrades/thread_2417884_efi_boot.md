---
title: "efi boot"
date: 2019-04-28
forum: Installation &amp; Upgrades
---

### Post by bjlockie on 2019-04-28
I converted from BIOS booting to EFI booting, hoping it would be faster.
I think it is a bit faster but not as fast as I think it could be.

I'm pretty sure I ended up with it booting grub-efi which then loads lubuntu.
Is there a way to boot lubuntu directly?
It won't be able to upgrade the kernel if I do that, right?
How much time will I save, 1 second? :-)

Can I apt remove grub2 since I installed grub-efi?

---

### Post by VMC on 2019-04-29
Are you talking about **systemd-boot **or your booting with grub. there totally different. If its not **systemd-boot**, then no you need grub files.

---

### Post by oldfred on 2019-04-29
What is slow?
Post these in code tags (# in forums advanced editor):
 systemd-analyze
systemd-analyze critical-chain
systemd-analyze blame

---

### Post by bjlockie on 2019-04-29
> **VMC said:**
> Are you talking about **systemd-boot **or your booting with grub. there totally different. If its not **systemd-boot**, then no you need grub files.

I mean since I installed grub-efi, can I remove non-efi grub?

/boot/efi/EFI/ubuntu$ ls -l
total 1420
-rwxr-xr-x 1 root root     117 Apr 27 15:14 grub.cfg
-rwxr-xr-x 1 root root 1447800 Apr 27 15:14 grubx64.efi

:/boot/efi/EFI/ubuntu$ cat grub.cfg 
search.fs_uuid 12554e38-e51e-4761-8a79-efe2780391e3 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

---

### Post by bjlockie on 2019-04-29
> **oldfred said:**
> What is slow?
Post these in code tags (# in forums advanced editor):
 systemd-analyze
systemd-analyze critical-chain
systemd-analyze blame

$ systemd-analyze
Startup finished in 14.321s (firmware) + 266ms (loader) + 3.234s (kernel) + 19.411s (userspace) = 37.233s 
graphical.target reached after 6.859s in userspace

```
$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @6.859s
&#9492;&#9472;multi-user.target @6.859s
  &#9492;&#9472;postfix.service @6.857s +1ms
    &#9492;&#9472;postfix@-.service @6.655s +201ms
      &#9492;&#9472;network-online.target @6.653s
        &#9492;&#9472;NetworkManager-wait-online.service @2.756s +3.896s
          &#9492;&#9472;NetworkManager.service @2.680s +73ms
            &#9492;&#9472;dbus.service @2.674s
              &#9492;&#9472;basic.target @2.650s
                &#9492;&#9472;sockets.target @2.650s
                  &#9492;&#9472;snapd.socket @2.648s +1ms
                    &#9492;&#9472;sysinit.target @2.646s
                      &#9492;&#9472;systemd-udev-settle.service @224ms +2.422s
                        &#9492;&#9472;systemd-udev-trigger.service @167ms +55ms
                          &#9492;&#9472;systemd-journald.socket @162ms
                            &#9492;&#9472;system.slice @156ms
                              &#9492;&#9472;-.slice @156ms
$ systemd-analyze blame 
          8.898s apt-daily.service
          3.896s NetworkManager-wait-online.service
          3.853s apt-daily-upgrade.service
          2.422s systemd-udev-settle.service
           580ms systemd-logind.service
           568ms apport.service
           560ms grub-common.service
           483ms plymouth-quit.service
           443ms udisks2.service
           300ms dev-nvme0n1p2.device
           286ms nut-driver.service
           279ms lm-sensors.service
           201ms [EMAIL="postfix@-.servic"]postfix@-.servic[/EMAIL]e
           173ms systemd-timesyncd.service
           167ms systemd-resolved.service
           162ms snapd.service
           141ms networkd-dispatcher.service
           135ms accounts-daemon.service
           108ms upower.service
           106ms ModemManager.service
            86ms hdd\x2dstorage.mount
            86ms rsyslog.service
            73ms NetworkManager.service
            72ms thermald.service
            67ms avahi-daemon.service
            61ms wpa_supplicant.service
            61ms systemd-journal-flush.service
            60ms ofono.service
            58ms motd-news.service
            57ms virtualbox.service
            56ms gpu-manager.service
            55ms systemd-udev-trigger.service
            51ms keyboard-setup.service
            44ms systemd-journald.service
            38ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            36ms apparmor.service
            34ms lvm2-monitor.service
            32ms colord.service
            28ms systemd-udevd.service
            26ms polkit.service
            25ms [EMAIL="systemd-fsck@dev-disk-by\x2duuid-812C\x2dB4BC.servic"]systemd-fsck@dev-disk-by\x2duuid-812C\x2dB4BC.servic[/EMAIL]e
            24ms pppd-dns.service
            20ms kerneloops.service
            19ms plymouth-start.service
            17ms systemd-modules-load.service
            15ms bluetooth.service
            15ms systemd-tmpfiles-setup.service
            13ms nut-monitor.service
            12ms binfmt-support.service
            12ms systemd-update-utmp.service
```

---

### Post by oldfred on 2019-04-29
Please use code tags to preserve formatting or longer terminal output.
Easy to add with forum's advanced editor and # icon.

Those files are essential for booting in UEFI boot mode.

If a fast SSD, that boot may be a bit slow, but if slow HDD that is normal.

---

### Post by bjlockie on 2019-04-30
> **oldfred said:**
> If a fast SSD, that boot may be a bit slow, but if slow HDD that is normal.
It boots off an nvme drive so it should be fast.
It seems to sit there with a blank screen for a long time.

---

### Post by bjlockie on 2019-04-30
> **bjlockie said:**
> Can I apt remove grub2 since I installed grub-efi?

Apparently not.
```

$ sudo apt remove grub2-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  grub-efi-amd64-bin
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  grub-efi grub-efi-amd64 grub-efi-amd64-signed grub2-common

```

---

