---
title: "Interruption of Apt-get install / strg-c while apt-get install"
date: 2018-05-02
forum: Installation &amp; Upgrades
---

### Post by ju7 on 2018-05-02
Hi,

after interrupting apt-get install I errors with kernel packages.

I've tried to purge these kernel-packages (not my current 4.13.0-37-generic) with

sudo dpkg --purge linux-headers-4.13.0-36  linux-headers-4.13.0-36-generic linux-image-4.13.0-36-generic  linux-image-extra-4.13.0-36-generic
, but some wont go, because of missing pot-install-scripts and things..

If I try to install anything (for example the trouble makers to finx the postinstall-script problem), i get .. ok, now i cannot reach de.archive.ubuntu.com,  but some time before I get errors while processing this and other kernel packages..
So I cannot reinstall and cannot remove them. 

Any idea? :(


dpkg -l | grep linux-
gives

```
ii  linux-base                                    4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                                1.157.16                                     all          Firmware for Linux kernel drivers
iU  linux-generic                                 4.4.0.121.127                                amd64        Complete Generic Linux kernel and headers
iU  linux-generic-hwe-16.04                       4.13.0.39.58                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.13.0-37                       4.13.0-37.42~16.04.1                         all          Header files related to Linux kernel version 4.13.0
ii  linux-headers-4.13.0-37-generic               4.13.0-37.42~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
pi  linux-headers-4.13.0-39                       4.13.0-39.44~16.04.1                         all          Header files related to Linux kernel version 4.13.0
pi  linux-headers-4.13.0-39-generic               4.13.0-39.44~16.04.1                         amd64        Linux kernel headers for version 4.13.0 on 64 bit x86 SMP
pi  linux-headers-4.4.0-121                       4.4.0-121.145                                all          Header files related to Linux kernel version 4.4.0
pi  linux-headers-4.4.0-121-generic               4.4.0-121.145                                amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                         4.4.0.121.127                                amd64        Generic Linux kernel headers
pi  linux-headers-generic-hwe-16.04               4.13.0.39.58                                 amd64        Generic Linux kernel headers
ii  linux-image-4.13.0-37-generic                 4.13.0-37.42~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
pF  linux-image-4.13.0-39-generic                 4.13.0-39.44~16.04.1                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-4.4.0-119-generic                 4.4.0-119.143                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pF  linux-image-4.4.0-121-generic                 4.4.0-121.145                                amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.10.0-28-generic           4.10.0-28.32~16.04.2                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rH  linux-image-extra-4.10.0-42-generic           4.10.0-42.46~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-26-generic           4.13.0-26.29~16.04.2                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-31-generic           4.13.0-31.34~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-32-generic           4.13.0-32.35~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
pH  linux-image-extra-4.13.0-36-generic           4.13.0-36.40~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.13.0-37-generic           4.13.0-37.42~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.13.0-38-generic           4.13.0-38.43~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
pU  linux-image-extra-4.13.0-39-generic           4.13.0-39.44~16.04.1                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-119-generic           4.4.0-119.143                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
pU  linux-image-extra-4.4.0-121-generic           4.4.0-121.145                                amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.121.127                                amd64        Generic Linux kernel image
iU  linux-image-generic-hwe-16.04                 4.13.0.39.58                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                          4.4.0-121.145                                amd64        Linux Kernel Headers for development
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                               3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                               2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-utils                                3:6.03+dfsg-11ubuntu1                        amd64        collection of bootloaders (utilities)
```


purge for 4.13.0-36 for example gives me:

```
sudo dpkg --purge linux-headers-4.13.0-36 linux-headers-4.13.0-36-generic linux-image-4.13.0-36-generic linux-image-extra-4.13.0-36-generic
dpkg: Warnung: Die Anforderung, linux-headers-4.13.0-36 zu entfernen, wird ignoriert; es ist nicht installiert
dpkg: Warnung: Die Anforderung, linux-headers-4.13.0-36-generic zu entfernen, wird ignoriert; es ist nicht installiert
(Lese Datenbank ... 349197 Dateien und Verzeichnisse sind derzeit installiert.)
Entfernen von linux-image-4.13.0-36-generic (4.13.0-36.40~16.04.1) ...
Entfernen von linux-image-extra-4.13.0-36-generic (4.13.0-36.40~16.04.1) ...
depmod: FATAL: could not load /boot/System.map-4.13.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
Error! Your kernel headers for kernel 4.13.0-36-generic cannot be found.
Please install the linux-headers-4.13.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.13.0-36-generic cannot be found.
Please install the linux-headers-4.13.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.13.0-36-generic cannot be found.
Please install the linux-headers-4.13.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-36-generic
WARNING: missing /lib/modules/4.13.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.13.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_WIybcm/lib/modules/4.13.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_WIybcm/lib/modules/4.13.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-36-generic /boot/vmlinuz-4.13.0-36-generic
Grub-Konfigurationsdatei wird generiert &#8230;
grub-probe: Fehler: Laufwerk »mduuid/c546cf6975b6c56cc3f9ee84f768482a,2« wurde nicht gefunden..
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: Fehler beim Bearbeiten des Paketes linux-image-extra-4.13.0-36-generic (--purge):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
Fehler traten auf beim Bearbeiten von:
 linux-image-extra-4.13.0-36-generic
```

---

### Post by TheFu on 2018-05-02
It is best NOT to use dpkg directly except for those things which were installed using only dpkg.  If you install something with apt, apt-get, aptitude, or some GUI package manager, then use those to remove it, so that dependencies are handled too.

Never manually delete files that were installed using packages unless the packages have already been removed through the package manager.

The best way I know to fix dependency issues like above is to reinstall the problem package using a package manager, then remove it using the package manager.

If there are PPAs involved, it can be more complex.
If any .deb files have been manually installed, then it can be more complex.

Or did I completely miss the issue?

---

### Post by ju7 on 2018-05-03
I did not install the Kernelupdates manually.. I only want to apt-get install new packages and get errors with these kernel-images but i cannot remove them..

For apt-get install php-imap for example i get:

```
depmod: FATAL: could not load /boot/System.map-4.13.0-38-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
Error! Your kernel headers for kernel 4.13.0-38-generic cannot be found.
Please install the linux-headers-4.13.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.13.0-38-generic cannot be found.
Please install the linux-headers-4.13.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 4.13.0-38-generic cannot be found.
Please install the linux-headers-4.13.0-38-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-38-generic
WARNING: missing /lib/modules/4.13.0-38-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.13.0-38-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_4HicP8/lib/modules/4.13.0-38-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_4HicP8/lib/modules/4.13.0-38-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
Grub-Konfigurationsdatei wird generiert &#8230;
grub-probe: Fehler: Laufwerk »mduuid/c546cf6975b6c56cc3f9ee84f768482a,2« wurde nicht gefunden..
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
dpkg: Fehler beim Bearbeiten des Paketes linux-image-extra-4.13.0-38-generic (--remove):
 Unterprozess installiertes post-removal-Skript gab den Fehlerwert 1 zurück
Es wurde kein Apport-Bericht verfasst, da das Limit MaxReports bereits erreicht ist.
                                                                                    Fehler traten auf beim Bearbeiten von:
 linux-image-extra-4.4.0-119-generic
 linux-image-4.4.0-119-generic
 linux-image-extra-4.10.0-28-generic
 linux-image-extra-4.10.0-42-generic
 linux-image-extra-4.13.0-26-generic
 linux-image-extra-4.13.0-31-generic
 linux-image-extra-4.13.0-32-generic
 linux-image-extra-4.13.0-38-generic

```
If I try to remove  linux-image-extra-4.13.0-38-generic for example (causing errors while apt-get install) I get the errors described above.
When I try to install it to get rid of these "missing .." errors I get in trouble with the other ones.

Is there a way to completely remove these kernel-images and extras, a "force" for example? Or a way to ignore them?

Please help. Never had such problems with apt (since 10years+)

---

### Post by TheFu on 2018-05-03
From the error message:
```
Error! Your kernel headers for kernel 4.13.0-38-generic cannot be found.
Please install the linux-headers-4.13.0-38-generic package,
```

Did you do that?  Those sorts of helpful ideas ARE there to be helpful.  ;)

If you use --force, almost always bad things will happen. It will probably leave you with a system in worse condition than now.  Go ahead and force it, but expect to also reinstall the OS. The manpage will explain how to use force options.

---

### Post by ju7 on 2018-05-05
No, i m running into errors with any apt-get install. But there s another interesting message:

grub-probe: Fehler: Laufwerk »mduuid/c546cf6975b6c56cc3f9ee84f768482a,2« wurde nicht gefunden..

Ok, I got it: /boot/grub/device.map was missing. /dev/sdb of raid1 is faulty..
after sudo grub-mkdevicemap apt-get install gives no errors anymore but did 1000s of grub configs J

---

