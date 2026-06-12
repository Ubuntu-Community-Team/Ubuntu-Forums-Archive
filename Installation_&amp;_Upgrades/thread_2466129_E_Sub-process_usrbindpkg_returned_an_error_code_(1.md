---
title: "E: Sub-process /usr/bin/dpkg returned an error code (100)"
date: 2021-08-20
forum: Installation &amp; Upgrades
---

### Post by sevic332 on 2021-08-20
Hi there,

I'm unable to install any new package, it always returning this error:
E: Sub-process /usr/bin/dpkg returned an error code (100)

I'm using Ubuntu 20.04.2 LTS


Any idea?

---

### Post by Impavidus on 2021-08-20
You're probably unable to install any updates too, so that's bad.

Best to see all of the output. There's usually some hint about the cause of the problem. Run```
sudo apt update
sudo apt upgrade
```and post all output. And post the commands too.

One way to copy the output to the forum: Select the text in the terminal, right click &#8594; copy, then paste on the forum. Put code tags around it, [noparse]```
like this
```[/noparse].

---

### Post by guruao513 on 2021-08-20
Hi,

I am facng a similar issue. Following is the output of the upgrade command.


```
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.11.0-27-generic
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=73894523-aa88-4c85-9275-f8c6c729c68b)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.11.0-27-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-5.11.0-27-generic (--configure):
 installed linux-image-5.11.0-27-generic package post-installation script subpro
cess returned error exit status 1
Processing triggers for initramfs-tools (0.136ubuntu6.6) ...
update-initramfs: Generating /boot/initrd.img-5.11.0-25-generic
I: The initramfs will attempt to resume from /dev/sda6
I: (UUID=73894523-aa88-4c85-9275-f8c6c729c68b)
I: Set the RESUME variable to override this.
Error 24 : Write error : cannot write compressed block 
E: mkinitramfs failure cpio 141 lz4 -9 -l 24
update-initramfs: failed for /boot/initrd.img-5.11.0-25-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned 
error exit status 1
Errors were encountered while processing:
 linux-firmware
 linux-image-5.11.0-27-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by MAFoElffen on 2021-08-21
Just by coincidence, does your system have a separate /boot partition?

Please post the results of 
```
df -a
```

---

### Post by sevic332 on 2021-08-23
Hi ,

Here are outputs:

df -a:
[COLOR=#000000] ```
[/COLOR][FONT=&quot]Filesystem     1K-blocks      Used Available Use% Mounted on[/FONT]
[FONT=&quot]sysfs                  0         0         0    - /sys
proc                   0         0         0    - /proc
udev             5985920         0   5985920   0% /dev
devpts                 0         0         0    - /dev/pts
tmpfs            1203092      2268   1200824   1% /run
/dev/sda2      959863856 103449000 807586648  12% /
securityfs             0         0         0    - /sys/kernel/security
tmpfs            6015440     83352   5932088   2% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            6015440         0   6015440   0% /sys/fs/cgroup
cgroup2                0         0         0    - /sys/fs/cgroup/unified
cgroup                 0         0         0    - /sys/fs/cgroup/systemd
pstore                 0         0         0    - /sys/fs/pstore
efivarfs               0         0         0    - /sys/firmware/efi/efivars
none                   0         0         0    - /sys/fs/bpf
cgroup                 0         0         0    - /sys/fs/cgroup/blkio
cgroup                 0         0         0    - /sys/fs/cgroup/devices
cgroup                 0         0         0    - /sys/fs/cgroup/cpuset
cgroup                 0         0         0    - /sys/fs/cgroup/cpu,cpuacct
cgroup                 0         0         0    - /sys/fs/cgroup/pids
cgroup                 0         0         0    - /sys/fs/cgroup/memory
cgroup                 0         0         0    - /sys/fs/cgroup/rdma
cgroup                 0         0         0    - /sys/fs/cgroup/perf_event
cgroup                 0         0         0    - /sys/fs/cgroup/hugetlb
cgroup                 0         0         0    - /sys/fs/cgroup/net_cls,net_prio
cgroup                 0         0         0    - /sys/fs/cgroup/freezer
systemd-1              0         0         0    - /proc/sys/fs/binfmt_misc
mqueue                 0         0         0    - /dev/mqueue
tracefs                0         0         0    - /sys/kernel/tracing
debugfs                0         0         0    - /sys/kernel/debug
hugetlbfs              0         0         0    - /dev/hugepages
fusectl                0         0         0    - /sys/fs/fuse/connections
configfs               0         0         0    - /sys/kernel/config
/dev/loop0        310400    310400         0 100% /snap/wine-platform-5-stable/16
/dev/loop7        156800    156800         0 100% /snap/opera/137
/dev/loop8         82048     82048         0 100% /snap/ffmpeg/1286
/dev/loop9        464128    464128         0 100% /snap/phpstorm/227
/dev/loop14       166784    166784         0 100% /snap/gnome-3-28-1804/145
/dev/loop12        33152     33152         0 100% /snap/snapd/12704
/dev/loop2        330624    330624         0 100% /snap/wine-platform-6-stable/3
/dev/loop4        330624    330624         0 100% /snap/wine-platform-6-stable/5
/dev/loop6         66688     66688         0 100% /snap/gtk-common-themes/1515
/dev/loop1        464896    464896         0 100% /snap/phpstorm/222
/dev/loop3        156800    156800         0 100% /snap/opera/136
/dev/loop16        52224     52224         0 100% /snap/snap-store/547
/dev/loop17        52224     52224         0 100% /snap/snap-store/542
/dev/loop15       134784    134784         0 100% /snap/docker/796
/dev/loop10       224256    224256         0 100% /snap/gnome-3-34-1804/66
/dev/loop24        66432     66432         0 100% /snap/gtk-common-themes/1514
/dev/loop18         5632      5632         0 100% /snap/notepad-plus-plus/287
/dev/loop26        33792     33792         0 100% /snap/chromium-ffmpeg/17
/dev/loop5         56832     56832         0 100% /snap/core18/2128
/dev/loop22       168832    168832         0 100% /snap/gnome-3-28-1804/161
/dev/loop20       345600    345600         0 100% /snap/wine-platform-runtime/233
/dev/loop13       101888    101888         0 100% /snap/core/11420
/dev/loop27         5632      5632         0 100% /snap/notepad-plus-plus/288
/dev/loop11        56832     56832         0 100% /snap/core18/2074
/dev/loop21       224256    224256         0 100% /snap/gnome-3-34-1804/72
/dev/loop23        33152     33152         0 100% /snap/snapd/12398
/dev/loop25       101760    101760         0 100% /snap/core/11316
/dev/nvme0n1p1     98304     43451     54853  45% /boot/efi
tmpfs            1203092      2264   1200828   1% /run/snapd/ns
nsfs                   0         0         0    - /run/snapd/ns/docker.mnt
/dev/loop28       345728    345728         0 100% /snap/wine-platform-runtime/234
tmpfs            1203088        60   1203028   1% /run/user/1000
gvfsd-fuse             0         0         0    - /run/user/1000/gvfs
/dev/fuse              0         0         0    - /run/user/1000/doc
[/FONT]
[FONT=&quot]nsfs                   0         0         0    - /run/snapd/ns/snap-store.mnt[/FONT][COLOR=#000000]
```

[/COLOR]sudo apt update
sudo apt upgrade[COLOR=#000000]

[/COLOR][COLOR=#000000] ```
[/COLOR][FONT=&quot][9:43 AM] Aleksandar Tadic[/FONT]
[FONT=&quot]    Hit:1 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal InReleaseHit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                                                     Hit:3 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) focal InRelease                                                                                                                                                          Hit:4 [http://ppa.launchpad.net/yann1ck/onedrive/ubuntu](http://ppa.launchpad.net/yann1ck/onedrive/ubuntu) focal InRelease                                                                                                                                           Hit:5 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                                                                                                                                                          Ign:6 [https://artifacts.elastic.co/packages/5.x/apt](https://artifacts.elastic.co/packages/5.x/apt) stable InRelease                                                                                                Hit:7 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal InRelease                                                                                     Hit:8 [https://artifacts.elastic.co/packages/5.x/apt](https://artifacts.elastic.co/packages/5.x/apt) stable Release                                                      Hit:9 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal-updates InRelease                                                                                     Hit:10 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease                                                                                 Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]                                                      Get:12 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]                              Hit:13 [http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu](http://nyc2.mirrors.digitalocean.com/mariadb/repo/10.4/ubuntu) focal InRelease                                     Hit:14 [http://apt.insync.io/ubuntu](http://apt.insync.io/ubuntu) focal InRelease                                                                       Fetched 214 kB in 2s (117 kB/s)                          Reading package lists... DoneBuilding dependency tree      Reading state information... Done80 packages can be upgraded. Run 'apt list --upgradable' to see them. 


[/FONT]
&#8203;
[FONT=&quot][9:44 AM] Aleksandar Tadic[/FONT]

[FONT=&quot]Reading package lists... DoneBuilding dependency tree      Reading state information... DoneCalculating upgrade... DoneThe following package was automatically installed and is no longer required:  shimUse 'sudo apt autoremove' to remove it.The following NEW packages will be installed:  gir1.2-clutter-1.0 gir1.2-clutter-gst-3.0 gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-gtkclutter-1.0 libjcat1 libllvm12 linux-headers-5.10.0-1044-oem linux-image-5.10.0-1044-oem linux-modules-5.10.0-1044-oem  linux-oem-5.10-headers-5.10.0-1044The following packages have been kept back:  libdrm-amdgpu1 libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libegl-mesa0 libgbm1 libgl1-mesa-dri libglapi-mesa libglx-mesa0 libosmesa6 mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-driversThe following packages will be upgraded:  alsa-ucm-conf base-files distro-info-data docker.io firefox firefox-locale-en fwupd fwupd-signed galera-4 gnome-settings-daemon gnome-settings-daemon-common gnome-shell-extension-desktop-icons  google-chrome-stable grub-common grub-pc grub-pc-bin grub2-common insync language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libc-ares2 libdbi-perl libdrm-common  libexiv2-27 libfwupd2 libfwupdplugin1 libmariadb3 libpq5 libssl-dev libssl1.1 libxatracker2 linux-firmware linux-headers-oem-20.04b linux-image-oem-20.04b linux-libc-dev linux-oem-20.04 linux-oem-20.04b  login mariadb-client-10.4 mariadb-client-core-10.4 mariadb-common mariadb-server mariadb-server-10.4 mariadb-server-core-10.4 mysql-common openssh-client openssl openvpn passwd php8.0-igbinary  python3-distupgrade shim shim-signed teamviewer ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk update-notifier update-notifier-common wireless-regdb xserver-common xserver-xephyr xserver-xorg-core  xserver-xorg-legacy xwayland66 upgraded, 11 newly installed, 0 to remove and 14 not upgraded.1 not fully installed or removed.13 standard security updatesNeed to get 0 B/631 MB of archives.After this operation, 505 MB of additional disk space will be used.Do you want to continue? [Y/n] yExtracting templates from packages: 100%Preconfiguring packages .../tmp/grub-pc.config.HGddFy: 1: dpkg: Permission deniedsetting xserver-xorg-legacy/xwrapper/allowed_users from configuration fileCould not exec dpkg!E: Sub-process /usr/bin/dpkg returned an error code (100)   [/FONT][COLOR=#000000]
```[/COLOR]

---

### Post by Impavidus on 2021-08-23
Formatting of your output is a bit off (the linebreaks are missing), so it's a bit hard to read. There appears to be a lot of rubbish in your package management, but this may be fixable. A bigger problem is the rather unexpected error: [FONT=&amp]"dpkg: Permission denied". I'm not sure I've seen that one before. What does```
ls -l /usr/bin/dpkg
```tell?

@[/FONT]guruao513: Your issue is completely different. Please start your own thread.

---

### Post by sevic332 on 2021-08-23
@impavidus sorry i was unable to edit my post.

Here is output of: [FONT=&quot]*** ls -l /usr/bin/dpkg***: 

```
[/FONT][FONT=&quot]$ ls -l /usr/bin/dpkg [/FONT][FONT=&quot]total 4128[/FONT][FONT=&quot]-rw-r--r-- 1 aleksandar aleksandar    4460 &#1072;&#1074;&#1075;  6 17:15 control.tar.xz
-rw-r--r-- 1 aleksandar aleksandar 1123204 &#1072;&#1074;&#1075;  6 17:15 data.tar.xz
-rw-r--r-- 1 aleksandar aleksandar       4 &#1072;&#1074;&#1075;  6 17:15 debian-binary
-rw-rw-r-- 1 aleksandar aleksandar 1957810 &#1084;&#1072;&#1088;  6  2018 dpkg_1.17.5ubuntu5.8_amd64.deb
[/FONT]
[FONT=&quot]-rw-r--r-- 1 aleksandar aleksandar 1127856 &#1084;&#1072;&#1088; 23  2020 dpkg_1.19.7ubuntu3_amd64.deb[/FONT][FONT=&quot]
```
[/FONT]

---

### Post by Impavidus on 2021-08-23
Are you telling us that your /usr/bin/dpkg is a directory? It's supposed to be an executable file. And everything in /usr/bin is supposed to be owned by root. Something must be terribly wrong on your system. I wouldn't trust it anymore.

Have you any idea what could have caused this? Entering random commands you found on the web, messing with /usr/bin bypassing the package manager, messing with different partitions and mountpoints? If this happened spontaneously, consider the possibility that your harddrive is broken.

The tools you need to fix a broken system are broken. The normal course of action is a fresh install. That takes 30 minutes. First check the health of your hard drive. That could take up to a few hours, depending on the drive.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by MAFoElffen on 2021-08-23
If that is your output, then yes. You have no other options, but to reinstall. There are two two very closely tied utilities, that are required. dpkg and apt, which depends on dpkg. If those are bad, bad juju...

To explain what you should have seen as output on that:
```

mafoelffen@ubuntu:$ ls -l /usr/bin/dpkg
-rwxr-xr-x 1 root root 309672 Mar 22  2020 /usr/bin/dpkg

```

---

### Post by sevic332 on 2021-08-24
Hi Everybody,

Thanks for help.
I'm going to reinstall OS, so this ticket can be closed.

---

