---
title: "Ubunte freeze on startup for 90 seconds"
date: 2020-02-18
forum: Installation &amp; Upgrades
---

### Post by martinmolema on 2020-02-18
Hello fellow Ubuntu-fans,

I recently swapped a disk from a traditional HDD to an SSD. Since then I notice Ubuntu freezes during startup for 90 seconds. There are a number of disks in my system: (output of lsblk)
sda      8:0    0 465,8G  0 disk 
&#9492;&#9472;sda1   8:1    0 465,8G  0 part /mnt/backups
sdb      8:16   0 111,8G  0 disk 
&#9500;&#9472;sdb1   8:17   0 102,5G  0 part /
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0   9,4G  0 part [SWAP]
sdc      8:32   0 223,6G  0 disk 
&#9492;&#9472;sdc1   8:33   0 223,6G  0 part /mnt/ssd
sdd      8:48   0 931,5G  0 disk 
&#9492;&#9472;sdd1   8:49   0 931,5G  0 part /mnt/storage
sde      8:64   0 465,8G  0 disk 
&#9492;&#9472;sde1   8:65   0 465,8G  0 part /mnt/storage2
sdj      8:144  0   1,8T  0 disk 
&#9492;&#9472;sdj1   8:145  0   1,8T  0 part /mnt/usb

The disk I recently swapped is SDC (mounted as /mnt/ssd), formatted as EXT4 primary partition. It is NOT the boot-partition. In fact, the old disk wasn't even really used. There was however a second Lubuntu installation present. (perhaps GRUB is causing problems?)

The complete dump of DMESG is in the link below.
[URL="https://pastebin.com/tgDHaP9H"]
https://pastebin.com/tgDHaP9H[/URL]

uname -a output:
Linux jupiter 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:14:09 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

If anyone has a clue why this happens I would be very happy. Normally my system boots in seconds..... this is irritating. 

Thanks in advance!

Greetings Martin


An extract from DMESG:
```
[    6.435023] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
                Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
                (Note that use of the override may cause unknown side effects.)
[    6.675365] audit: type=1400 audit(1582029752.593:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=1134 comm="apparmor_parser"
[    6.675972] audit: type=1400 audit(1582029752.593:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-oopslash" pid=1133 comm="apparmor_parser"
[    6.677484] audit: type=1400 audit(1582029752.593:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=1132 comm="apparmor_parser"
[    6.677490] audit: type=1400 audit(1582029752.593:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=1132 comm="apparmor_parser"
[    6.677495] audit: type=1400 audit(1582029752.593:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=1132 comm="apparmor_parser"
[    6.678003] audit: type=1400 audit(1582029752.593:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-xpdfimport" pid=1137 comm="apparmor_parser"
[    6.681012] audit: type=1400 audit(1582029752.597:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=1129 comm="apparmor_parser"
[    6.681017] audit: type=1400 audit(1582029752.597:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1129 comm="apparmor_parser"
[    6.681021] audit: type=1400 audit(1582029752.597:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=1129 comm="apparmor_parser"
[    6.681024] audit: type=1400 audit(1582029752.597:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1129 comm="apparmor_parser"
[   94.385813] vboxdrv: loading out-of-tree module taints kernel.
[   94.386094] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   94.395251] vboxdrv: Found 6 processor cores
[   94.414757] vboxdrv: TSC mode is Invariant, tentative frequency 3299919745 Hz
[   94.414758] vboxdrv: Successfully loaded version 6.1.0 (interface 0x002d0001)
[   94.624258] VBoxNetFlt: Successfully started.
[   94.629875] VBoxNetAdp: Successfully started.
[   94.642652] RTL8211E Gigabit Ethernet r8169-300:00: attached PHY driver [RTL8211E Gigabit Ethernet] (mii_bus:phy_addr=r8169-300:00, irq=IGNORE)



```

---

### Post by kc1di on 2020-02-18
Please go to a terminal and type this command```
 systemd-analyze blame
``` and post the output here.

---

### Post by martinmolema on 2020-02-19
Here it is..... is the MEssage Of The Day service to blame?! Immediately started some tests. WHen opening the link  [https://motd.ubuntu.com](https://motd.ubuntu.com) in a browser it can take up to 30 seconds to get a response. "Initial connection" = 23 seconds, SSL check 16 seconds (running parallel to 23 seconds), TTFB = 1 second, content download 0.89ms. 



      **1min 166ms motd-news.service**
          6.252s plymouth-quit-wait.service
          2.701s NetworkManager-wait-online.service
          1.370s keyboard-setup.service
          1.105s snapd.service
          1.039s dev-sdb1.device
           820ms mysql.service
           795ms fwupd.service
           699ms snap-core18-1650.mount
           678ms snap-gnome\x2dlogs-81.mount
           678ms mpd.service
           662ms snap-gnome\x2dcalculator-544.mount
           662ms snap-gnome\x2dsystem\x2dmonitor-127.mount
           655ms snap-drawio-8.mount
           628ms snap-gnome\x2dlogs-73.mount
           617ms snap-skype-109.mount
           612ms snap-gnome\x2dcharacters-375.mount
           587ms snap-core18-1668.mount
           550ms snap-gnome\x2dsystem\x2dmonitor-123.mount
           548ms snap-gnome\x2dcharacters-399.mount
           538ms mnt-fileserver-muziek.mount
           537ms systemd-journal-flush.service
           523ms snapd.seeded.service
           517ms apparmor.service
           509ms vboxdrv.service
           506ms snap-gnome\x2d3\x2d28\x2d1804-110.mount
           498ms plymouth-start.service
           498ms phpsessionclean.service
           491ms snap-snap\x2dstore-209.mount
           488ms mnt-fileserver-afbeeldingen.mount
           487ms mnt-fileserver-storage.mount
           484ms home-lars-Documenten-Netdisk.mount
           483ms mnt-fileserver-var\x2dwww.mount
           479ms mnt-fileserver-afbeeldingen\x2drw.mount
           474ms mnt-storage2.mount
           472ms home-martin-Documenten-Netdisk.mount
           466ms mnt-fileserver-bladmuziek.mount
           466ms mnt-fileserver-repositories.mount
           459ms udisks2.service
           452ms home-isa-Documenten-Netdisk.mount
           425ms home-yorick-Documenten-Netdisk.mount
           423ms mnt-net\x2dhomes.mount
           422ms snap-dosbox\x2dx-405.mount
           420ms snap-gnome\x2dcalculator-536.mount
           419ms snap-gnome\x2d3\x2d26\x2d1604-97.mount
           408ms mnt-fileserver-storage2.mount
           392ms mnt-fileserver-muziek\x2drw.mount
           388ms home-yvonne-Documenten-Netdisk.mount
           388ms plymouth-read-write.service
           384ms snap-core-8592.mount
           346ms snap-teams\x2dfor\x2dlinux-79.mount
           316ms home-martin-Documenten-Gedeeld.mount
           312ms snap-skype-112.mount
           309ms snap-postman-97.mount
           289ms dev-disk-by\x2duuid-a1cc96e3\x2d6bab\x2d49d3\x2db3b1\x2d08ee46f44567.swap
           277ms networkd-dispatcher.service
           271ms systemd-rfkill.service
           261ms mnt-storage.mount
           257ms snap-gnome\x2d3\x2d26\x2d1604-98.mount
           255ms ModemManager.service
           242ms snap-gnome\x2d3\x2d28\x2d1804-116.mount
           239ms snap-gtk\x2dcommon\x2dthemes-1440.mount
           213ms upower.service
           206ms accounts-daemon.service
           202ms apport-autoreport.service
           198ms snap-teams\x2dfor\x2dlinux-77.mount
           196ms snap-core-8268.mount
           174ms NetworkManager.service
           167ms systemd-udevd.service
           166ms systemd-logind.service
           164ms grub-common.service
           155ms bluetooth.service
           150ms avahi-daemon.service
           148ms gpu-manager.service
           143ms apache2.service
           136ms alsa-restore.service
           135ms rsyslog.service
           134ms snap-dosbox\x2dx-440.mount
           129ms systemd-modules-load.service
           126ms snap-postman-98.mount
           125ms dev-loop7.device
           124ms dev-loop8.device
           123ms systemd-journald.service
           122ms dev-loop6.device
           122ms thermald.service
           121ms pppd-dns.service
           114ms dev-loop9.device
           106ms dev-loop22.device
           104ms systemd-udev-trigger.service
           104ms dev-loop21.device
           102ms smbd.service
           102ms mnt-backups.mount
            98ms dev-loop12.device
            93ms backup_music.service
            91ms mnt-usb.mount
            90ms snap-gtk\x2dcommon\x2dthemes-1353.mount
            89ms vboxweb-service.service
            80ms dev-loop14.device
            73ms colord.service
            72ms [EMAIL="user@121.servic"]user@121.servic[/EMAIL]e
            71ms timidity.service
            69ms wpa_supplicant.service
            66ms bolt.service
            64ms systemd-timesyncd.service
            64ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            60ms nmbd.service
            56ms systemd-resolved.service
            54ms dev-loop10.device
            52ms dev-loop11.device
            52ms dev-loop16.device
            52ms dev-loop4.device
            51ms dev-loop15.device
            49ms dev-loop13.device
            48ms packagekit.service
            47ms dev-loop17.device
            47ms polkit.service
            43ms systemd-tmpfiles-setup-dev.service
            41ms dns-clean.service
            38ms apport.service
            38ms networking.service
            36ms gdm.service
            32ms systemd-tmpfiles-setup.service
            31ms dev-loop19.device
            30ms systemd-sysctl.service
            28ms ssh.service
            26ms speech-dispatcher.service
            22ms dev-loop26.device
            21ms dev-loop25.device
            20ms mnt-ssd.mount
            16ms dev-loop18.device
            16ms dev-hugepages.mount
            15ms dev-loop20.device
            14ms dev-loop5.device
            14ms kerneloops.service
            14ms dev-loop3.device
            14ms dev-loop1.device
            14ms dev-loop2.device
            13ms dev-loop0.device
            13ms systemd-random-seed.service
            13ms kmod-static-nodes.service
            12ms console-setup.service
            10ms systemd-remount-fs.service
             9ms sys-kernel-debug.mount
             7ms dev-mqueue.mount
             7ms systemd-user-sessions.service
             7ms ufw.service
             6ms dev-loop24.device
             6ms vboxballoonctrl-service.service
             6ms ureadahead-stop.service
             6ms systemd-update-utmp.service
             6ms systemd-update-utmp-runlevel.service
             5ms vboxautostart-service.service
             4ms rtkit-daemon.service
             3ms sys-fs-fuse-connections.mount
             3ms sabnzbdplus.service
             3ms setvtrgb.service
             2ms sys-kernel-config.mount
             2ms dev-loop27.device
           929us snapd.socket

---

### Post by martinmolema on 2020-02-19
Thanks to @kc1di I figured it out: using the systemd-analyze critical-chain command I saw the long wait was caused by a mount. Thought I had removed the old mount-points... except somehow my swap-file was on that old disk (probably explains some system slowness as well!). Removed the old reference to the swap-partition and now all is well.

[COLOR=#000000]@kc1di[/COLOR]

---

### Post by kc1di on 2020-02-19
Glad you got it sorted out. :)

---

