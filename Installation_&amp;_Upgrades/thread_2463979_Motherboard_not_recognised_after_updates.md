---
title: "Motherboard not recognised after updates"
date: 2021-06-22
forum: Installation &amp; Upgrades
---

### Post by 03go on 2021-06-22
I updated my Dell Vostro 5502 laptop (intel 11th Gen Intel® Core&#8482; i5-1135G7 processor) from Ubuntu 20.04.1 to 20.04.2 (it was a series of security and other system patches). During update, an error was reported:
```
Processing triggers for linux-image-5.10.0-1029-oem (5.10.0-1029.30) .../etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.10.0-1029-oem
W: Possible missing firmware /lib/firmware/i915/tgl_huc_7.5.0.bin for module i915
```

After update and restart, motherboard functions stopped to work (no battery indicator, no sound, no display brightness control).

I tried to resolve the error by downloading missing gl_huc_7.5.0.bin (I didn't try initiating update-initramfs, that would be my next try)

Any suggestions how to fix this?

This is excerpt from upgrade log (hystory.log):
```
Start-Date: 2021-06-22  11:50:36Commandline: aptdaemon role='role-commit-packages' sender=':1.84'
Install: libpam0g:i386 (1.3.1-5ubuntu4.2, automatic), libgssapi3-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libdevmapper1.02.1:i386 (2:1.02.167-1ubuntu1, automatic), libkrb5-3:i386 (1.17-6ubuntu4.1, automatic), libgssapi-krb5-2:i386 (1.17-6ubuntu4.1, automatic), libnghttp2-14:i386 (1.40.0-1build1, automatic), libseccomp2:i386 (2.5.1-1ubuntu1~20.04.1, automatic), libcom-err2:i386 (1.45.5-2ubuntu1, automatic), libwind0-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libsasl2-modules-db:i386 (2.1.27+dfsg-2, automatic), libssh-4:i386 (0.9.3-2ubuntu2.1, automatic), libargon2-1:i386 (0~20171227-0.2, automatic), libbrotli1:i386 (1.0.7-6ubuntu0.1, automatic), libsystemd0:i386 (245.4-4ubuntu3.7, automatic), gcc-10-base:i386 (10.2.0-5ubuntu1~20.04, automatic), libacl1:i386 (2.2.53-6, automatic), libheimntlm0-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libkmod2:i386 (27-1ubuntu2, automatic), libpsl5:i386 (0.21.0-1ubuntu1, automatic), libmount1:i386 (2.34-0.1ubuntu9.1, automatic), libsqlite3-0:i386 (3.31.1-4ubuntu0.2, automatic), libbz2-1.0:i386 (1.0.8-2, automatic), libgpg-error0:i386 (1.37-1, automatic), zlib1g:i386 (1:1.2.11.dfsg-2ubuntu1.2, automatic), libgmp10:i386 (2:6.2.0+dfsg-4, automatic), libheimbase1-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libc6:i386 (2.31-0ubuntu9.2, automatic), libk5crypto3:i386 (1.17-6ubuntu4.1, automatic), libsasl2-2:i386 (2.1.27+dfsg-2, automatic), libudev1:i386 (245.4-4ubuntu3.7, automatic), libapparmor1:i386 (2.13.3-7ubuntu5.1, automatic), libcrypt1:i386 (1:4.4.10-10ubuntu4, automatic), systemd-timesyncd:i386 (245.4-4ubuntu3.7, automatic), libblkid1:i386 (2.34-0.1ubuntu9.1, automatic), libsasl2-modules:i386 (2.1.27+dfsg-2, automatic), libkrb5support0:i386 (1.17-6ubuntu4.1, automatic), libcap2:i386 (1:2.32-1, automatic), libuuid1:i386 (2.34-0.1ubuntu9.1, automatic), libgcrypt20:i386 (1.8.5-5ubuntu1, automatic), libhcrypto4-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libkeyutils1:i386 (1.6-6ubuntu1, automatic), libselinux1:i386 (3.0-1build2, automatic), liblz4-1:i386 (1.9.2-2ubuntu0.20.04.1, automatic), libpcre2-8-0:i386 (10.34-7, automatic), systemd:i386 (245.4-4ubuntu3.7, automatic), libhogweed5:i386 (3.5.1+really3.5.1-2ubuntu0.2, automatic), libdb5.3:i386 (5.3.28+dfsg1-0.6ubuntu2, automatic), libgcc-s1:i386 (10.2.0-5ubuntu1~20.04, automatic), libnettle7:i386 (3.5.1+really3.5.1-2ubuntu0.2, automatic), libcap-ng0:i386 (0.7.9-2.1build1, automatic), libgnutls30:i386 (3.6.13-2ubuntu1.3, automatic), libroken18-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libffi7:i386 (3.3-4, automatic), libunistring2:i386 (0.9.10-2, automatic), libp11-kit0:i386 (0.23.20-1ubuntu0.1, automatic), libasn1-8-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libkrb5-26-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libcryptsetup12:i386 (2:2.2.2-3ubuntu2.3, automatic), libssl1.1:i386 (1.1.1f-1ubuntu2.4, automatic), libtasn1-6:i386 (4.16.0-2, automatic), libjson-c4:i386 (0.13.1+dfsg-7ubuntu0.3, automatic), liblzma5:i386 (5.2.4-1ubuntu1, automatic), libhx509-5-heimdal:i386 (7.7.0+dfsg-1ubuntu1, automatic), libip4tc2:i386 (1.8.4-3ubuntu2, automatic), libidn2-0:i386 (2.2.0-2, automatic), libgpg-error-l10n:amd64 (1.37-1, automatic), libaudit1:i386 (1:2.8.5-2ubuntu6, automatic)
Upgrade: bluez:amd64 (5.53-0ubuntu3.1, 5.53-0ubuntu3.2), gir1.2-secret-1:amd64 (0.20.3-0ubuntu1, 0.20.4-0ubuntu1), libxml2-utils:amd64 (2.9.10+dfsg-5, 2.9.10+dfsg-5ubuntu0.20.04.1), bluez-cups:amd64 (5.53-0ubuntu3.1, 5.53-0ubuntu3.2), libwbclient0:amd64 (2:4.11.6+dfsg-0ubuntu1.8, 2:4.11.6+dfsg-0ubuntu1.9), yaru-theme-icon:amd64 (20.04.10.1, 20.04.11.1), libsystemd0:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), grub-common:amd64 (2.04-1ubuntu26.11, 2.04-1ubuntu26.12), libsecret-1-0:amd64 (0.20.3-0ubuntu1, 0.20.4-0ubuntu1), python3-libxml2:amd64 (2.9.10+dfsg-5, 2.9.10+dfsg-5ubuntu0.20.04.1), grub2-common:amd64 (2.04-1ubuntu26.11, 2.04-1ubuntu26.12), udev:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), libsecret-common:amd64 (0.20.3-0ubuntu1, 0.20.4-0ubuntu1), libnss-mymachines:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), yaru-theme-gtk:amd64 (20.04.10.1, 20.04.11.1), libudev1:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), samba-libs:amd64 (2:4.11.6+dfsg-0ubuntu1.8, 2:4.11.6+dfsg-0ubuntu1.9), grub-efi-amd64-bin:amd64 (2.04-1ubuntu44, 2.04-1ubuntu44.2), systemd-sysv:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), libpam-systemd:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), libhogweed5:amd64 (3.5.1+really3.5.1-2ubuntu0.1, 3.5.1+really3.5.1-2ubuntu0.2), libsmbclient:amd64 (2:4.11.6+dfsg-0ubuntu1.8, 2:4.11.6+dfsg-0ubuntu1.9), yaru-theme-gnome-shell:amd64 (20.04.10.1, 20.04.11.1), grub-efi-amd64:amd64 (2.04-1ubuntu44, 2.04-1ubuntu44.2), libnettle7:amd64 (3.5.1+really3.5.1-2ubuntu0.1, 3.5.1+really3.5.1-2ubuntu0.2), bluez-obexd:amd64 (5.53-0ubuntu3.1, 5.53-0ubuntu3.2), grub-efi-amd64-signed:amd64 (1.167+2.04-1ubuntu44, 1.167.2+2.04-1ubuntu44.2), systemd-container:amd64 (245.4-4ubuntu3.6, 245.4-4ubuntu3.7), libbluetooth3:amd64 (5.53-0ubuntu3.1, 5.53-0ubuntu3.2), yaru-theme-sound:amd64 (20.04.10.1, 20.04.11.1)
Remove: netplan.io:amd64 (0.102-0ubuntu1~20.04.2), plymouth-themes:amd64 (0.9.4git20200323-0ubuntu6.2), snapd:amd64 (2.49.2+20.04), plymouth-label:amd64 (0.9.4git20200323-0ubuntu6.2), plymouth-theme-ubuntu-text:amd64 (0.9.4git20200323-0ubuntu6.2), systemd-timesyncd:amd64 (245.4-4ubuntu3.6), ubuntu-minimal:amd64 (1.450.2), plymouth-theme-spinner:amd64 (0.9.4git20200323-0ubuntu6.2), systemd:amd64 (245.4-4ubuntu3.6), libnss-systemd:amd64 (245.4-4ubuntu3.6), plymouth:amd64 (0.9.4git20200323-0ubuntu6.2), dbus-user-session:amd64 (1.12.16-2ubuntu2.1)
End-Date: 2021-06-22  11:51:23
```

---

### Post by MAFoElffen on 2021-06-22
Two ideas... First, is your BIOS updated to the manufacturer's latest update? Second, at the Grub Menu, if your select the last installed 5.8 kernel, does it work as it did? 

If updating your BIOS fixes you, then you are Golden. 

If it doesn't and using the last kernel version fixes that... Then please file a bug to Launchpad explaining that, so they can file a bug to upstream kernel.org... So they can fix that in the new Kernel.

Does that make sense to you?

---

### Post by 03go on 2021-06-22
[B][FONT=arial black]Solved:

[/FONT][/B][FONT=arial black]I figured out after reading [this article]("https://askubuntu.com/questions/1290223/audio-and-battery-status-gone-after-update-ubuntu-20-04-lts") that the problem was broken systemd.
After ```
apt reinstall systemd
``` everything was back again. (Including QEMU/KVM virtual machine which was not starting).

Just lost mere 5 hours, that's a triffle :smile:[/FONT]

---

### Post by 03go on 2021-06-22
I updated BIOS and tried other kernels prior to asking question... but systemd was the issue... see my reply to thread

---

### Post by MAFoElffen on 2021-06-22
Happy all is well now!

---

