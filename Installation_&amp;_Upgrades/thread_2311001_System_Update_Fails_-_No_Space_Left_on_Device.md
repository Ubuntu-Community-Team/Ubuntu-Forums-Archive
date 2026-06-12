---
title: "System Update Fails - No Space Left on Device"
date: 2016-01-23
forum: Installation &amp; Upgrades
---

### Post by kuv02 on 2016-01-23
Hey guys. I've read [http://ubuntuforums.org/showthread.php?t=2309183](http://ubuntuforums.org/showthread.php?t=2309183) but could not execute it sucessfully.

This is what I did:

```
 ~$ df -h 
Dateisystem                  Größe Benutzt Verf. Verw% Eingehängt auf 
udev                          3,9G       0  3,9G    0% /dev 
tmpfs                         791M    9,4M  781M    2% /run 
/dev/mapper/kubuntu--vg-root  212G     29G  173G   15% / 
tmpfs                         3,9G     88K  3,9G    1% /dev/shm 
tmpfs                         5,0M    4,0K  5,0M    1% /run/lock 
tmpfs                         3,9G       0  3,9G    0% /sys/fs/cgroup 
/dev/sda1                     236M    233M     0  100% /boot 
tmpfs                         791M       0  791M    0% /run/user/115 
tmpfs                         791M     12K  791M    1% /run/user/1000



```

```
 ~$ dpkg -l | grep linux-image 
ii  linux-image-3.19.0-21-generic                 3.19.0-21.21                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-25-generic                 3.19.0-25.26                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-32-generic                 3.19.0-32.37                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-33-generic                 3.19.0-33.38                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-42-generic                 3.19.0-42.48                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
rc  linux-image-extra-3.19.0-15-generic           3.19.0-15.15                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-21-generic           3.19.0-21.21                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-25-generic           3.19.0-25.26                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-32-generic           3.19.0-32.37                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-33-generic           3.19.0-33.38                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iF  linux-image-extra-3.19.0-42-generic           3.19.0-42.48                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iU  linux-image-extra-3.19.0-47-generic           3.19.0-47.53                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iU  linux-image-generic                           3.19.0.47.46                               amd64        Generic Linux kernel image
 
dpkg -l | grep linux-header 
ii  linux-headers-3.19.0-21                       3.19.0-21.21                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-21-generic               3.19.0-21.21                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-25                       3.19.0-25.26                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-25-generic               3.19.0-25.26                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-32                       3.19.0-32.37                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-32-generic               3.19.0-32.37                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-33                       3.19.0-33.38                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-33-generic               3.19.0-33.38                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-42                       3.19.0-42.48                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-42-generic               3.19.0-42.48                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-47                       3.19.0-47.53                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-47-generic               3.19.0-47.53                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-generic                         3.19.0.47.46                               amd64        Generic Linux kernel headers

```

After that I tried dpkg -P but some "FATAL" messages showed up, see below:
```
 sudo dpkg -P linux-image{,-extra}-3.19.0-{15,21,25}-generic 
[sudo] password for ronny:  
dpkg: Warnung: Die Anforderung, linux-image-3.19.0-15-generic zu entfernen, wird ignoriert; es ist nicht installiert 
(Lese Datenbank ... 296539 Dateien und Verzeichnisse sind derzeit installiert.) 
Entfernen von linux-image-3.19.0-21-generic (3.19.0-21.21) ... 
Examining /etc/kernel/prerm.d. 
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
dkms: removing: bbswitch 0.7 (3.19.0-21-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  bbswitch 
Version: 0.7 
Kernel:  3.19.0-21-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

bbswitch.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-21-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
dkms: removing: nvidia-352 352.63 (3.19.0-21-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  nvidia-352 
Version: 352.63 
Kernel:  3.19.0-21-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

nvidia_352.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-21-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 


nvidia_352_uvm.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-21-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
update-initramfs: Deleting /boot/initrd.img-3.19.0-21-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-42-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-42-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-25-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-25-generic 
erledigt 
The link /vmlinuz.old is a damaged link 
Removing symbolic link vmlinuz.old  
 you may need to re-run your boot loader[grub] 
The link /initrd.img.old is a damaged link 
Removing symbolic link initrd.img.old  
 you may need to re-run your boot loader[grub] 
Löschen der Konfigurationsdateien von linux-image-3.19.0-21-generic (3.19.0-21.21) ... 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
Entfernen von linux-image-3.19.0-25-generic (3.19.0-25.26) ... 
Examining /etc/kernel/prerm.d. 
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
dkms: removing: bbswitch 0.7 (3.19.0-25-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  bbswitch 
Version: 0.7 
Kernel:  3.19.0-25-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

bbswitch.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-25-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
dkms: removing: nvidia-352 352.63 (3.19.0-25-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  nvidia-352 
Version: 352.63 
Kernel:  3.19.0-25-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

nvidia_352.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-25-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 


nvidia_352_uvm.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-25-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-42-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-42-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
The link /vmlinuz is a damaged link 
Removing symbolic link vmlinuz  
 you may need to re-run your boot loader[grub] 
The link /initrd.img is a damaged link 
Removing symbolic link initrd.img  
 you may need to re-run your boot loader[grub] 
Löschen der Konfigurationsdateien von linux-image-3.19.0-25-generic (3.19.0-25.26) ... 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
dpkg: Warnung: Die Anforderung, linux-image-extra-3.19.0-15-generic zu entfernen, wird ignoriert; es ist nicht installiert 
Entfernen von linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ... 
depmod: FATAL: could not load /boot/System.map-3.19.0-21-generic: No such file or directory 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-21-generic 
grep: /boot/config-3.19.0-21-generic: Datei oder Verzeichnis nicht gefunden 
depmod: WARNING: could not open /tmp/mkinitramfs_ocwBin/lib/modules/3.19.0-21-generic/modules.order: No such file or directory 
depmod: WARNING: could not open /tmp/mkinitramfs_ocwBin/lib/modules/3.19.0-21-generic/modules.builtin: No such file or directory 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-21-generic /boot/vmlinuz-3.19.0-21-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-42-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-42-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
Löschen der Konfigurationsdateien von linux-image-extra-3.19.0-21-generic (3.19.0-21.21) ... 
Entfernen von linux-image-extra-3.19.0-25-generic (3.19.0-25.26) ... 
depmod: FATAL: could not load /boot/System.map-3.19.0-25-generic: No such file or directory 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-25-generic 
grep: /boot/config-3.19.0-25-generic: Datei oder Verzeichnis nicht gefunden 
depmod: WARNING: could not open /tmp/mkinitramfs_QCofPX/lib/modules/3.19.0-25-generic/modules.order: No such file or directory 
depmod: WARNING: could not open /tmp/mkinitramfs_QCofPX/lib/modules/3.19.0-25-generic/modules.builtin: No such file or directory 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-25-generic /boot/vmlinuz-3.19.0-25-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-42-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-42-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
Löschen der Konfigurationsdateien von linux-image-extra-3.19.0-25-generic (3.19.0-25.26) ...


```
I continued to remove the headers too:
```
 ~$ sudo dpkg -P linux-headers-3.19.0-{15,21,25}{,-generic}       
dpkg: Warnung: Die Anforderung, linux-headers-3.19.0-15 zu entfernen, wird ignoriert; es ist nicht installiert 
dpkg: Warnung: Die Anforderung, linux-headers-3.19.0-15-generic zu entfernen, wird ignoriert; es ist nicht installiert 
(Lese Datenbank ... 294555 Dateien und Verzeichnisse sind derzeit installiert.) 
Entfernen von linux-headers-3.19.0-21-generic (3.19.0-21.21) ... 
dpkg: Warnung: Während Entfernens von linux-headers-3.19.0-21-generic ist Verzeichnis »/lib/modules/3.19.0-21-generic« nicht leer, wird daher nicht gelöscht 
Entfernen von linux-headers-3.19.0-25-generic (3.19.0-25.26) ... 
dpkg: Warnung: Während Entfernens von linux-headers-3.19.0-25-generic ist Verzeichnis »/lib/modules/3.19.0-25-generic« nicht leer, wird daher nicht gelöscht 
Entfernen von linux-headers-3.19.0-21 (3.19.0-21.21) ... 
Entfernen von linux-headers-3.19.0-25 (3.19.0-25.26) ...


```
This is the resulting situation:
```
 ~$ df -h 
Dateisystem                  Größe Benutzt Verf. Verw% Eingehängt auf 
udev                          3,9G       0  3,9G    0% /dev 
tmpfs                         791M    9,4M  781M    2% /run 
/dev/mapper/kubuntu--vg-root  212G     29G  173G   15% / 
tmpfs                         3,9G     88K  3,9G    1% /dev/shm 
tmpfs                         5,0M    4,0K  5,0M    1% /run/lock 
tmpfs                         3,9G       0  3,9G    0% /sys/fs/cgroup 
/dev/sda1                     236M    204M   20M   92% /boot 
tmpfs                         791M       0  791M    0% /run/user/115 
tmpfs                         791M     12K  791M    1% /run/user/1000 
ronny@rf-acer:~$ dpkg -l | grep linux-image 
ii  linux-image-3.19.0-32-generic                 3.19.0-32.37                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-33-generic                 3.19.0-33.38                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-42-generic                 3.19.0-42.48                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-47-generic                 3.19.0-47.53                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-32-generic           3.19.0-32.37                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-33-generic           3.19.0-33.38                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iF  linux-image-extra-3.19.0-42-generic           3.19.0-42.48                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iF  linux-image-extra-3.19.0-47-generic           3.19.0-47.53                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
iU  linux-image-generic                           3.19.0.47.46                               amd64        Generic Linux kernel image 
ronny@rf-acer:~$ dpkg -l | grep linux-he 
ii  linux-headers-3.19.0-32                       3.19.0-32.37                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-32-generic               3.19.0-32.37                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-33                       3.19.0-33.38                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-33-generic               3.19.0-33.38                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-42                       3.19.0-42.48                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-42-generic               3.19.0-42.48                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-47                       3.19.0-47.53                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-47-generic               3.19.0-47.53                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-generic                         3.19.0.47.46                               amd64        Generic Linux kernel headers
```

now I'm getting optimistic and try apt-get autoremove:
```
 ~$ sudo apt-get autoremove  
Paketlisten werden gelesen... Fertig 
Abhängigkeitsbaum wird aufgebaut.        
Statusinformationen werden eingelesen.... Fertig 
Die folgenden Pakete werden ENTFERNT: 
  libcuda1-346 linux-headers-3.19.0-42 linux-headers-3.19.0-42-generic linux-image-3.19.0-42-generic linux-image-extra-3.19.0-42-generic nvidia-opencl-icd-346 
0 aktualisiert, 0 neu installiert, 6 zu entfernen und 0 nicht aktualisiert. 
4 nicht vollständig installiert oder entfernt. 
Nach dieser Operation werden 289 MB Plattenplatz freigegeben. 
Möchten Sie fortfahren? [J/n]  
(Lese Datenbank ... 244641 Dateien und Verzeichnisse sind derzeit installiert.) 
Entfernen von linux-image-extra-3.19.0-42-generic (3.19.0-42.48) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-42-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-42-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
Entfernen von libcuda1-346 (352.63-0ubuntu0.15.04.1) ... 
Entfernen von linux-headers-3.19.0-42-generic (3.19.0-42.48) ... 
Entfernen von linux-headers-3.19.0-42 (3.19.0-42.48) ... 
Entfernen von linux-image-3.19.0-42-generic (3.19.0-42.48) ... 
Examining /etc/kernel/prerm.d. 
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
dkms: removing: bbswitch 0.7 (3.19.0-42-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  bbswitch 
Version: 0.7 
Kernel:  3.19.0-42-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

bbswitch.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-42-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
dkms: removing: nvidia-352 352.63 (3.19.0-42-generic) (x86_64) 

-------- Uninstall Beginning -------- 
Module:  nvidia-352 
Version: 352.63 
Kernel:  3.19.0-42-generic (x86_64) 
------------------------------------- 

Status: Before uninstall, this module version was ACTIVE on this kernel. 

nvidia_352.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-42-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 


nvidia_352_uvm.ko: 
 - Uninstallation 
   - Deleting from: /lib/modules/3.19.0-42-generic/updates/dkms/ 
 - Original module 
   - No original module was found for this module on this kernel. 
   - Use the dkms install command to reinstall any previous module version. 

depmod.... 

DKMS: uninstall completed. 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
update-initramfs: Deleting /boot/initrd.img-3.19.0-42-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
Entfernen von nvidia-opencl-icd-346 (352.63-0ubuntu0.15.04.1) ... 
linux-image-extra-3.19.0-47-generic (3.19.0-47.53) wird eingerichtet ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
update-initramfs: Generating /boot/initrd.img-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-47-generic /boot/vmlinuz-3.19.0-47-generic 
Grub-Konfigurationsdatei wird generiert … 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-47-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-47-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-33-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-33-generic 
Linux-Abbild gefunden: /boot/vmlinuz-3.19.0-32-generic 
initrd-Abbild gefunden: /boot/initrd.img-3.19.0-32-generic 
erledigt 
linux-image-generic (3.19.0.47.46) wird eingerichtet ... 
linux-generic (3.19.0.47.46) wird eingerichtet ... 
ronny@rf-acer:~$ dpkg -l | grep linux- 
ii  linux-firmware                                1.143.7                                    all          Firmware for Linux kernel drivers 
ii  linux-generic                                 3.19.0.47.46                               amd64        Complete Generic Linux kernel and headers 
ii  linux-headers-3.19.0-32                       3.19.0-32.37                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-32-generic               3.19.0-32.37                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-33                       3.19.0-33.38                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-33-generic               3.19.0-33.38                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-3.19.0-47                       3.19.0-47.53                               all          Header files related to Linux kernel version 3.19.0 
ii  linux-headers-3.19.0-47-generic               3.19.0-47.53                               amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP 
ii  linux-headers-generic                         3.19.0.47.46                               amd64        Generic Linux kernel headers 
ii  linux-image-3.19.0-32-generic                 3.19.0-32.37                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-33-generic                 3.19.0-33.38                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
rc  linux-image-3.19.0-42-generic                 3.19.0-42.48                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-3.19.0-47-generic                 3.19.0-47.53                               amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-32-generic           3.19.0-32.37                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-33-generic           3.19.0-33.38                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
rc  linux-image-extra-3.19.0-42-generic           3.19.0-42.48                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-extra-3.19.0-47-generic           3.19.0-47.53                               amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP 
ii  linux-image-generic                           3.19.0.47.46                               amd64        Generic Linux kernel image 
ii  linux-libc-dev:amd64                          3.19.0-47.53                               amd64        Linux Kernel Headers for development 
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu4                       all          base package for ALSA and OSS sound systems



```
My System demands a restart. Lets see if it worked.

---

### Post by kuv02 on 2016-01-23
ok that worked. My boot partition is slimed down as needed.
```
 ~$ df -h 
Dateisystem                  Größe Benutzt Verf. Verw% Eingehängt auf 
udev                          3,9G       0  3,9G    0% /dev 
tmpfs                         791M    9,4M  782M    2% /run 
/dev/mapper/kubuntu--vg-root  212G     28G  174G   14% / 
tmpfs                         3,9G     84K  3,9G    1% /dev/shm 
tmpfs                         5,0M    4,0K  5,0M    1% /run/lock 
tmpfs                         3,9G       0  3,9G    0% /sys/fs/cgroup 
**/dev/sda1                     236M    164M   61M   74% /boot **
tmpfs                         791M       0  791M    0% /run/user/115 
tmpfs                         791M     12K  791M    1% /run/user/1000

```

This is a really annoying bug:  it happens because you keep your system up to date. This should be prohibited by the kernel guys.

I found this command in the other thread:
```
sudo sed -i 's/^..\(.*Remove-Unused.*\)/\1/g' /etc/apt/apt.conf.d/50unattended-upgrades
```
is this setting up an outo remove/purge of old kernels? Is it save to use?

---

### Post by matt_symes on 2016-01-23
Hi

There was a mistake in the sed command on my other post. I have updated that other post and below is a copy and paste from the update......

Somehow i managed to uncomment the line but forgot to change the false to true. 

I must have been pretty distracted when i posted. 

Anyway i have updated that post and and i'll post the updated command below as well.

```
sudo sed -i 's/^[\/]*\(.*Remove-Unused.*\) "false";/\1 "true";/g' /etc/apt/apt.conf.d/50unattended-upgrades
```

If you want to know if it's safe to use...

```
matthew-xu-16-04:/home/matthew:0 % grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
matthew-xu-16-04:/home/matthew:0 % sudo sed -i 's/^[\/]*\(.*Remove-Unused.*\) "false";/\1 "true";/g' /etc/apt/apt.conf.d/50unattended-upgrades
matthew-xu-16-04:/home/matthew:0 % grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
Unattended-Upgrade::Remove-Unused-Dependencies "true";
matthew-xu-16-04:/home/matthew:0 % 
```

Kind regards

---

### Post by kuv02 on 2016-01-23
Thank you. So at least this thread was somehow helpful. ;)

I will start another thread, because this problem was just a distraction from my real problem: Blackscreens during start up

---

### Post by matt_symes on 2016-01-23
Hi

If you run that sed command in post #3 then that should enable autoremove for you.

Kind regards

---

### Post by kuv02 on 2016-01-23
Yes I did, and verified with the output you provided to prove what it did. Thanks

---

