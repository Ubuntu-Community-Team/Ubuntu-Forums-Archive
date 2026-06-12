---
title: "During Boot, many short-time-&quot;a start job is running&quot;"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by fg92 on 2019-03-06
Hi,
I am French : my English could be bad...

I have a laptop with a multi-boot Windows+Ubuntu+Debian, freshly installed.
The Ubuntu version is 18.04.2, the Debian version is 9.8.
The last installation was the Debian one.
After that, the Ubuntu-boot shows many short-time-"a start job is running" (less than 5 seconds for each job) :
- one about the swap partition ;
- one about the /home partition ;
- 1 or 2 about Kernel something.

I have looked to the logs, like /var/log/boot.log ; there is no "start job is running".
I have run $ systemd-analyze critical-chain, there is no job about these 2 partitions listed.

Do you know this issue ?
Is there some solutions ?
Thanks in advance.

Note : I use Linux for many years and I have already made multi-boot.

---

### Post by kc1di on 2019-03-06
Try the command systemd-analyze blame.  What is using the most start up time?

Essayez la commande systemd-analyse blame. Qu'est-ce qui utilise le plus de temps de démarrage? (Google Translate)

---

### Post by fg92 on 2019-03-06
I had already tried this command $ systemd-analyze blame. The result :
```

         21.480s systemd-journal-flush.service
         19.036s dev-sda10.device
         11.143s systemd-udevd.service
          9.932s systemd-sysctl.service
          9.855s snap-skype-66.mount
          9.367s dev-loop1.device
          8.520s udisks2.service
          7.242s NetworkManager-wait-online.service
          6.224s snapd.service
          5.232s NetworkManager.service
          4.839s networkd-dispatcher.service
          3.935s accounts-daemon.service
          3.640s thermald.service
          3.533s ModemManager.service
          2.603s systemd-modules-load.service
          1.899s polkit.service
          1.795s keyboard-setup.service
          1.768s plymouth-start.service
          1.447s snap-core-6405.mount
          1.156s dev-loop0.device
           916ms systemd-tmpfiles-setup-dev.service
           785ms avahi-daemon.service
           758ms systemd-journald.service
           727ms dev-hugepages.mount
           725ms systemd-remount-fs.service
           721ms dev-mqueue.mount
           720ms sys-kernel-debug.mount
           650ms rsyslog.service
           445ms apport.service
           437ms systemd-fsck@dev-disk-by\x2duuid-a311b893\x2dd7aa\x2d45c4\x2db956\x2dbfa481dc7de9.service
           434ms gpu-manager.service
           420ms wpa_supplicant.service
           384ms kmod-static-nodes.service
           344ms systemd-random-seed.service
           326ms systemd-logind.service
           315ms speech-dispatcher.service
           310ms lm-sensors.service
           307ms user@1000.service
           285ms lightdm.service
           283ms plymouth-quit-wait.service
           280ms apparmor.service
           262ms grub-common.service
           252ms upower.service
           221ms systemd-udev-trigger.service
           207ms home.mount
           188ms systemd-rfkill.service
           151ms ufw.service
           144ms systemd-timesyncd.service
           143ms systemd-resolved.service
           142ms dev-disk-by\x2duuid-ba09019e\x2d2afd\x2d45d5\x2dbdcc\x2d0e1e36ad4838.swap
           139ms systemd-update-utmp.service
           124ms systemd-tmpfiles-setup.service
            77ms plymouth-read-write.service
            75ms snapd.seeded.service
            46ms systemd-tmpfiles-clean.service
            33ms alsa-restore.service
            29ms hddtemp.service
            25ms kerneloops.service
            24ms setvtrgb.service
            22ms snapd.socket
            22ms pppd-dns.service
            12ms ureadahead-stop.service
            11ms systemd-update-utmp-runlevel.service
             9ms systemd-user-sessions.service
             9ms sys-fs-fuse-connections.mount
             7ms sys-kernel-config.mount
             7ms console-setup.service
             6ms systemd-backlight@backlight:acpi_video0.service
             6ms rtkit-daemon.service

```
I think that is not significant.
Have you an other idea ?
Thanks in advance.

---

