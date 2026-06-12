---
title: "no resolv.conf after do-release-upgrade to 23.04 and sysvinit holdovers"
date: 2023-11-11
forum: Installation &amp; Upgrades
---

### Post by aathan on 2023-11-11
Three items related to do-release-upgrade to 23.04

Funky things happened during the upgrade due to console/terminal handling issues (described in one of the items below).


(1) netplan apply and systemctl restart systemd-networkd do not seem to write resolv.conf and I have to create one by hand after every reboot

I'm not clear on what the right way to restart networking is, under 23.04

```

# cat /etc/netplan/50-cloud-init.yaml
network:
    ethernets:
        enp0s3:
            #dhcp4: true
            dhcp4: false
            addresses: [192.168.1.10/24]
            #gateway4: 192.168.1.1
            routes:
                - to: default
                  via: 192.168.1.1
            nameservers:
              addresses: [192.168.1.1]

```


```
# systemctl list-unit-files | grep -i network
networkd-dispatcher.service            enabled         enabled
systemd-network-generator.service      disabled        enabled
systemd-networkd-wait-online.service   enabled-runtime disabled
systemd-networkd-wait-online@.service  disabled        enabled
systemd-networkd.service               enabled-runtime enabled
systemd-networkd.socket                disabled        enabled
network-online.target                  static          -
network-pre.target                     static          -
network.target                         static          -

```

(2) Prior to the upgrade, my console had a login: prompt. Now it doesn't. After the system is booted and I can ssh into it, the vbox console screen is just a non-blinking cursor at the upper left.

Dyrung the boot I *do* see the grub menu during boot, but this was only after changing `GRUB_TIMEOUT_STYLE=menu` in /etc/default/grub and update-grub. (The black screen was pretty terrifying on first reboot by the way.)

getty seems to be running...

```

# systemctl list-units --type service | grep getty
  getty@tty1.service                 loaded active running Getty on tty1
  getty@tty2.service                 loaded active running Getty on tty2
  getty@tty3.service                 loaded active running Getty on tty3
  getty@tty4.service                 loaded active running Getty on tty4
  getty@tty5.service                 loaded active running Getty on tty5
  getty@tty6.service                 loaded active running Getty on tty6

```

(3) During do-release-upgrade, on two separate systems I upgraded today, the upgrade did not go smoothly. Where can I best report some of those issues?

Briefly:
(3a) Either apt or the release upgrader put the console into a mode where if you have to drop into a shell to review changes (Z), and then use emacs to look around, the control characters used to navigate emacs seem to instead be captured by the upgrader. This can be catastrophic when exiting emacs because ^X^C causes the intr (^C) to kill something in the upgrader
(3b) apt/dpkg was then left in this crazy state where apt-get would refuse to install any new packages due to dependency conflicts on totally unrelated packages, and `apt --fix-broken install` did nothing, and I could do nothing to force apt to install specific packages it claimed were missing etc. Ultimately, I had to resort to manually downloading packages using `apt-get download <package>` individually copy-pasting from the dependency problems spit out by apt. I was then able to install those using `dpkg -i` on the individual deb's, which were being dropped into my current directory due to some other issue (I failed to capture the error message). After a couple of hours of this, I was able to resolve the dependency issues and apt-get upgrade was then able to proceed further. On that system there were also some i386 packages installed for some reason, which I had to clear out, and I have no idea if those predated the upgrade, but they certainly impeded my progress. What bothered me is that what I was doing seemed computable by apt. It just refused to do the installs I was asking it to do, so I had to apt download and dpkg -i instead.
(3c) once whatever weird thing happens with the console in cases described in 4a, there seems to be no way to reset the terminal without killing/restarting the upgrader/apt. In at least one case the console was left in "line mode" where you have to hit enter before any keys are registered. This made it quite tricky to navigate the text menus that come up (e.g., to select between keeping your config file, installing the new one, viewing a 3-way diff, etc... then navigating to the Ok)

(4) This is a very old system that was (years ago) virtualized and now runs in vbox, it has cruft from older systems, including for example, the `service` command from sysvinit. Any hints on really cleaning it up, or do I need to just do a completely clean install somewhere and just move my user files over at some point?


It really sucks that after so many years, and even though I'm not a linux noob, but certainly not a systemd guru, every single time I do a do-release-upgrade I am praying I don't drop into hell just because I used the wrong editor or pressed the wrong key. About 50% of the time I end up in some multi-hour problem solving scenario for one reason or another. At least I know enough to find my way out of a cave with a flashlight (dpkg), albeit slowly.

I'm just venting. I know it's hard and I generally love my ubuntu experiences and appreciate all the work done by the community.

---

### Post by ubfan1 on 2023-11-11
A new install, with moving your user files has got to be easier than debugging a setup with multi-layered old OSes.  Should be easy to set up, expect things to "just work", easy to check, then make the real effort moving your user files.

---

### Post by MAFoElffen on 2023-11-11
/etc/resolv.conf has not existed as a files since around 18.04, when it was replaced by a symlink:
```

mafoelffen@Mikes-ThinkPad-T520:~$ ls -lah /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Sep 23  2021 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

mafoelffen@Mikes-B460M:~$ ls -lah /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Nov 18  2022 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

mafoelffen@msi-ubuntu:~$ ls -lah /etc/resolv.conf
lrwxrwxrwx 1 root root 39 Aug  9  2022 /etc/resolv.conf -> ../run/systemd/resolve/stub-resolv.conf

mafoelffen@msi-ubuntu:~$ sudo ls -lah /run/systemd/resolve/stub-resolv.conf
-rw-r--r-- 1 systemd-resolve systemd-resolve 938 Nov 11 17:19 /run/systemd/resolve/stub-resolv.conf

```
The first thing to check would be these...
```

mafoelffen@msi-ubuntu:~$ sudo ls -lah /run/systemd/resolve/stub-resolv.conf
-rw-r--r-- 1 systemd-resolve systemd-resolve 938 Nov 11 17:19 /run/systemd/resolve/stub-resolv.conf

mafoelffen@msi-ubuntu:~$ grep . /run/systemd/resolve/stub-resolv.conf
# This is /run/systemd/resolve/stub-resolv.conf managed by man:systemd-resolved(8).
# Do not edit.
#
# This file might be symlinked as /etc/resolv.conf. If you're looking at
# /etc/resolv.conf and seeing this text, you have followed the symlink.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "resolvectl status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs should typically not access this file directly, but only
# through the symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a
# different way, replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.
nameserver 127.0.0.53
options edns0 trust-ad
search hsd1.wa.comcast.net

```
Which is the psuedo resolv.conf file dynamically created by daemon systemd-resolved...

The next step would be to check the service by doing
```

sudo systemctl status systemd-resolved --no-pager

```

---

### Post by aathan on 2023-11-13
Looks like systemd-resolved was missing from the system, for some reason. This happened on two different recently do-release-update'd systems.  Where can I report and/or look for why this happened?

---

### Post by MAFoElffen on 2023-11-13
Report it as a bug against 'systemd'. That is where I see other 'systemd-resolved' bugs filed.

What I would do first is ensure it is there or not first...
```

mafoelffen@msi-ubuntu:~$ ls -l /lib/systemd/system/systemd-resolved.service
-rw-r--r-- 1 root root 1.8K Sep 19 09:57 /lib/systemd/system/systemd-resolved.service

```
If it "is" missing, then boot form any recent Linux LiveUSB, such as the Ubuntu Installer... chroot into the installed system so that you have working networking from it, then do
```

sudo apt install --reinstall systemd

```
I just spun up a VM to test that, and it worked fine. Do you need information on how to chroot into your installed system to fix that?

Or I could post the systemd-resolved.service unit file contents for you to copy into where it goes, to patch that, for the reinstall...
```

#  SPDX-License-Identifier: LGPL-2.1-or-later
#
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
[Unit]
Description=Network Name Resolution
Documentation=man:systemd-resolved.service(8)
Documentation=man:org.freedesktop.resolve1(5)
Documentation=https://www.freedesktop.org/wiki/Software/systemd/writing-network-configuration-managers
Documentation=https://www.freedesktop.org/wiki/Software/systemd/writing-resolver-clients
DefaultDependencies=no
After=systemd-sysusers.service systemd-networkd.service
Before=network.target nss-lookup.target shutdown.target
Conflicts=shutdown.target
Wants=nss-lookup.target
[Service]
AmbientCapabilities=CAP_SETPCAP CAP_NET_RAW CAP_NET_BIND_SERVICE
BusName=org.freedesktop.resolve1
CapabilityBoundingSet=CAP_SETPCAP CAP_NET_RAW CAP_NET_BIND_SERVICE
ExecStart=!!/lib/systemd/systemd-resolved
LockPersonality=yes
MemoryDenyWriteExecute=yes
NoNewPrivileges=yes
PrivateDevices=yes
PrivateTmp=yes
ProtectProc=invisible
ProtectClock=yes
ProtectControlGroups=yes
ProtectHome=yes
ProtectKernelLogs=yes
ProtectKernelModules=yes
ProtectKernelTunables=yes
ProtectSystem=strict
Restart=always
RestartSec=0
RestrictAddressFamilies=AF_UNIX AF_NETLINK AF_INET AF_INET6
RestrictNamespaces=yes
RestrictRealtime=yes
RestrictSUIDSGID=yes
RuntimeDirectory=systemd/resolve
RuntimeDirectoryPreserve=yes
SystemCallArchitectures=native
SystemCallErrorNumber=EPERM
SystemCallFilter=@system-service
Type=notify
User=systemd-resolve
WatchdogSec=3min
[Install]
WantedBy=multi-user.target
Alias=dbus-org.freedesktop.resolve1.service

```
If you do that, just ensure the permissions are 644.

---

