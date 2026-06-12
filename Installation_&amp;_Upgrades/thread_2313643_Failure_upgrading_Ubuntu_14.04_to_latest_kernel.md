---
title: "Failure upgrading Ubuntu 14.04 to latest kernel"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by knight69 on 2016-02-14
I am attempting to update Ubuntu 14.04.  It is presently running kernel  version 3.16.0-51-generic. Executing the command sudo apt-get upgrade  -f, gives the following results:
```

$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-30 linux-headers-3.16.0-30-generic
  linux-headers-3.16.0-45 linux-headers-3.16.0-45-generic
  linux-headers-3.16.0-46 linux-headers-3.16.0-46-generic
  linux-headers-3.16.0-48 linux-headers-3.16.0-48-generic
  linux-headers-3.16.0-49 linux-headers-3.16.0-49-generic
  linux-headers-3.16.0-50 linux-headers-3.16.0-50-generic
  linux-image-3.16.0-30-generic linux-image-3.16.0-45-generic
  linux-image-3.16.0-46-generic linux-image-3.16.0-48-generic
  linux-image-3.16.0-49-generic linux-image-3.16.0-50-generic
  linux-image-extra-3.16.0-30-generic linux-image-extra-3.16.0-45-generic
  linux-image-extra-3.16.0-46-generic linux-image-extra-3.16.0-48-generic
  linux-image-extra-3.16.0-49-generic linux-image-extra-3.16.0-50-generic
  linux-image-extra-3.16.0-53-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-image-3.16.0-53-generic linux-image-3.16.0-60-generic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bash-completion
  bind9-host binutils biosdevname bsdutils cups cups-browsed cups-client
  cups-common cups-core-drivers cups-daemon cups-filters
  cups-filters-core-drivers cups-ppdc cups-server-common curl dnsutils firefox
  gir1.2-gnomedesktop-3.0 gir1.2-gst-plugins-base-1.0 gir1.2-gudev-1.0
  gir1.2-ibus-1.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0 gir1.2-polkit-1.0
  gir1.2-vte-2.90 gnome-desktop3-data grub-common grub-pc grub-pc-bin
  grub2-common gstreamer1.0-plugins-base gstreamer1.0-x gtk2-engines-pixbuf
  gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-libs ibus ibus-gtk
  ibus-gtk3 ifupdown im-config indicator-session irqbalance isc-dhcp-client
  isc-dhcp-common krb5-locales libapt-inst1.5 libapt-pkg4.12 libbind9-90
  libblkid1 libcgmanager0 libcomerr2 libcups2 libcupscgi1 libcupsfilters1
  libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdns100
  libdpkg-perl libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
  libegl1-mesa libegl1-mesa-drivers libffi6 libfontembed1 libgail-common
  libgail18 libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgles2-mesa libgnome-desktop-3-7 libgnutls-openssl27 libgnutls26
  libgssapi-krb5-2 libgstreamer-plugins-base1.0-0 libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-common libgudev-1.0-0 libhunspell-1.3-0 libibus-1.0-5
  libido3-0.1-0 libisc95 libisccc90 libisccfg90 libk5crypto3 libkrb5-3
  libkrb5support0 libldb1 liblightdm-gobject-1-0 liblwres90 libmbim-glib0
  libmm-glib0 libmount1 libmtp-common libmtp-runtime libmtp9
  libnautilus-extension1a libnm-glib-vpn1 libnm-glib4 libnm-gtk-common
  libnm-gtk0 libnm-util2 libnss3 libnss3-nssdb libopenvg1-mesa libpam-systemd
  libpng12-0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0
  libpoppler-glib8 libpoppler44 libpython3.4 libpython3.4-minimal
  libpython3.4-stdlib libsmbclient libsndfile1 libss2 libssl1.0.0 libstdc++6
  libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libudev1
  libunity-control-center1 libuuid1 libvte-2.90-9 libvte-2.90-common
  libwayland-egl1-mesa libwbclient0 libxatracker2 libxml2 lshw modemmanager
  nautilus nautilus-data network-manager network-manager-gnome nginx
  nginx-common nginx-full ntpdate openssh-client openssh-server
  openssh-sftp-server openssl os-prober passwd policykit-1 poppler-utils
  python-apt python-apt-common python-ldb python-libxml2 python-samba
  python-software-properties python-urllib3 python3-apport python3-apt
  python3-distupgrade python3-gdbm python3-problem-report
  python3-software-properties python3-update-manager python3.4
  python3.4-minimal rsync samba-common samba-common-bin samba-libs smbclient
  software-properties-common software-properties-gtk ssh sudo systemd-services
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk udev
  unattended-upgrades unity-control-center unity-settings-daemon
  update-manager update-manager-core uuid-runtime wpasupplicant
203 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0 B/127 MB of archives.
After this operation, 92.4 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up gcc-4.8-base:amd64 (4.8.4-2ubuntu1~14.04.1) ...
(Reading database ... 390295 files and directories currently installed.)
Preparing to unpack .../libstdc++6_4.8.4-2ubuntu1~14.04.1_amd64.deb ...
Unpacking libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.1) over (4.8.4-2ubuntu1~14.04) ...
Setting up libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
(Reading database ... 390295 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-60-generic_3.16.0-60.80~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-60-generic (3.16.0-60.80~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-60-generic_3.16.0-60.80~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.16.0-60-generic' to '/boot/vmlinuz-3.16.0-60-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-60-generic /boot/vmlinuz-3.16.0-60-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-60-generic /boot/vmlinuz-3.16.0-60-generic
Preparing to unpack .../linux-image-3.16.0-53-generic_3.16.0-53.72~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-53-generic (3.16.0-53.72~14.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.16.0-53-generic_3.16.0-53.72~14.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.16.0-53-generic' to '/boot/vmlinuz-3.16.0-53-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-53-generic /boot/vmlinuz-3.16.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-53-generic /boot/vmlinuz-3.16.0-53-generic
Preparing to unpack .../libapt-pkg4.12_1.0.1ubuntu2.11_amd64.deb ...
Unpacking libapt-pkg4.12:amd64 (1.0.1ubuntu2.11) over (1.0.1ubuntu2.10) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.16.0-60-generic_3.16.0-60.80~14.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-3.16.0-53-generic_3.16.0-53.72~14.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


It appears to be trying to update the kernel to 3.16.0-60-generic but is missing earlier kernel versions on which it depends.  

  What can I can do to fix this problem short of reinstalling and rebuilding my system?

---

### Post by ian-weisser on 2016-02-14
That's not what the error message says at all.

The error message says 'no space left on device',
and suggests you run 'sudo apt-get autoremove' to free space on your /boot partition.

Re-read the error messages and look for those strings. There is a rhythm to these kinds of problems.

First, try the suggested autoremove.
If autoremove does not work, then try [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Safely_removing_old_kernels)

If you still have a problem after that, then please show us the complete output of:
```
uname -r
df -h
ls /boot
dpkg -l | grep linux
```

---

### Post by knight69 on 2016-02-14
I did run autoremove and nothing happened.  However, I found .Trash-0 folder inside /boot and deleted all the files inside which freed up enough space to do the upgrade.  Unfortunately, the upgrade crashed and now the system won't boot up.

---

### Post by ian-weisser on 2016-02-14
> **knight69 said:**
> I did run autoremove and nothing happened.  However, I found .Trash-0 folder inside /boot and deleted all the files inside which freed up enough space to do the upgrade.  Unfortunately, the upgrade crashed and now the system won't boot up.

Autoremove often does not return any feedback. Even when it does a lot.

A Trash folder inside /boot is very bad. It means a user with admin permissions used the File Manager to delete root-owned files from /boot...which is an awful thing to do.
Those files were placed by the package manager, and should be removed only by the package manager.
Otherwise, your next upgrade might crash the package manager, and the upgrade...oh.

Do you want help trying to fix your unbootable system, or do you want to install anew?
The former will teach you much about your system. The latter is usually much faster.

If you decide to reinstall, and if you were using LVM or encryption, then remember to backup your data before reinstalling, else it will surely all be overwritten.

---

### Post by ptn107 on 2016-02-15
You're wasting about 45mb per kernel in /boot by keeping old ones around. Save this code to a script and run it to clear out all but the current kernel. You will need to use sudo.

```

#!/bin/bash

kernel_list=$(dpkg -l | awk '{print $2}' | grep linux-image- | grep -v $(uname -r) | grep -v linux-image-generic)
headers_list=$(dpkg -l | awk '{print $2}' | grep linux-headers- | grep -v $(uname -r | cut -d \- -f 1,2) | grep -v linux-headers-generic)
apt-get -y purge $kernel_list $headers_list
exit $?

```

---

### Post by ian-weisser on 2016-02-15
> **ptn107 said:**
> You're wasting about 45mb per kernel in /boot by keeping old ones around. Save this code to a script and run it to clear out all but the current kernel.

With a properly functioning package manager, this script will effectively do the same thing as autoremove.

---

### Post by knight69 on 2016-02-15
Ian-weisser, you are right.  It was very awful.  I manually removed all contents of  .Trash-0 which was inside /boot, re-ran sudo apt-get upgrade and the  installation crashed near the end.  Now the system only boots to the  (initramfs) prompt and I have no idea what to do.

Yes, I would like help trying to repair the system.  It is a server that  hosts my website.  Fortunately, I did back up my files before screwing  it up.

---

### Post by ian-weisser on 2016-02-15
Use (or create) a LiveUSB stick, and try the initramfs-prompt solution at [http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox](http://askubuntu.com/questions/137655/boot-drops-to-a-initramfs-prompts-busybox)

---

### Post by knight69 on 2016-02-15
I'll give that a try.  Thanks.

---

### Post by knight69 on 2016-02-15
Tried running fsck from live cd and it found and fixed (so it said) many inodes and ended saying FILE SYSTEM WAS MODIFIED.  Mounted sda1 to /mnt and found the kernels in /boot.  However, the system continued to boot to (initramfs).

Then I tried running gparted from live cd and get the following report:

Device              system                     size             used               unused             flags
/dev/sda1        ext2                      243.0 MB         114.4 MB          128.6 MB           boot
/dev/sda2        extended               297.85 GB        --------             -----------   
/dev/sda5        lvm2 pv                 297.85 GB       297.85 GB           16.0 MB           lvm

I have no idea what is happening here.  sda5 I thought was normally the swap partition, but the numbers don't make any sense.  I ran the check utility, but that didn't change anything and system still boots to the (initramfs) prompt.  

As a separate question, why would /boot be in a separate partition, and why is it so small?

---

