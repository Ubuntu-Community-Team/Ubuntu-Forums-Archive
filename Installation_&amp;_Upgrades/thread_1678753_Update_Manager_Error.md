---
title: "Update Manager Error"
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by badnaam on 2011-01-30
I get errors when I install applications..including errors from update manager when I do a regular update.


```
installArchives() failed: Selecting previously deselected package linux-image-2.6.35-25-generic.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 191869 files and directories currently installed.)
Unpacking linux-image-2.6.35-25-generic (from .../linux-image-2.6.35-25-generic_2.6.35-25.44_i386.deb) ...
Done.
Preparing to replace openssh-client 1:5.5p1-4ubuntu4 (using .../openssh-client_1%3a5.5p1-4ubuntu5_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace update-manager 1:0.142.20 (using .../update-manager_1%3a0.142.22_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace update-manager-core 1:0.142.20 (using .../update-manager-core_1%3a0.142.22_i386.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace hplip 3.10.6-1ubuntu10.1 (using .../hplip_3.10.6-1ubuntu10.2_i386.deb) ...
Unpacking replacement hplip ...
Preparing to replace hpijs 3.10.6-1ubuntu10.1 (using .../hpijs_3.10.6-1ubuntu10.2_i386.deb) ...
Unpacking replacement hpijs ...
Preparing to replace libhpmud0 3.10.6-1ubuntu10.1 (using .../libhpmud0_3.10.6-1ubuntu10.2_i386.deb) ...
Unpacking replacement libhpmud0 ...
Preparing to replace libsane-hpaio 3.10.6-1ubuntu10.1 (using .../libsane-hpaio_3.10.6-1ubuntu10.2_i386.deb) ...
Unpacking replacement libsane-hpaio ...
Preparing to replace hplip-data 3.10.6-1ubuntu10.1 (using .../hplip-data_3.10.6-1ubuntu10.2_all.deb) ...
Unpacking replacement hplip-data ...
Preparing to replace hplip-cups 3.10.6-1ubuntu10.1 (using .../hplip-cups_3.10.6-1ubuntu10.2_i386.deb) ...
Unpacking replacement hplip-cups ...
Preparing to replace libvlccore4 1.1.4-1ubuntu1.2 (using .../libvlccore4_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement libvlccore4 ...
Preparing to replace vlc-data 1.1.4-1ubuntu1.2 (using .../vlc-data_1.1.4-1ubuntu1.3_all.deb) ...
Unpacking replacement vlc-data ...
Preparing to replace libvlc5 1.1.4-1ubuntu1.2 (using .../libvlc5_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement libvlc5 ...
Preparing to replace linux-generic 2.6.35.24.28 (using .../linux-generic_2.6.35.25.32_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.35.24.28 (using .../linux-image-generic_2.6.35.25.32_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.35-25.
Unpacking linux-headers-2.6.35-25 (from .../linux-headers-2.6.35-25_2.6.35-25.44_all.deb) ...
Selecting previously deselected package linux-headers-2.6.35-25-generic.
Unpacking linux-headers-2.6.35-25-generic (from .../linux-headers-2.6.35-25-generic_2.6.35-25.44_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.35.24.28 (using .../linux-headers-generic_2.6.35.25.32_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.35-1024.42 (using .../linux-libc-dev_2.6.35-1025.44_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace ssh-askpass-gnome 1:5.5p1-4ubuntu4 (using .../ssh-askpass-gnome_1%3a5.5p1-4ubuntu5_i386.deb) ...
Unpacking replacement ssh-askpass-gnome ...
Preparing to replace vlc-plugin-notify 1.1.4-1ubuntu1.2 (using .../vlc-plugin-notify_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement vlc-plugin-notify ...
Preparing to replace vlc-plugin-pulse 1.1.4-1ubuntu1.2 (using .../vlc-plugin-pulse_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement vlc-plugin-pulse ...
Preparing to replace vlc 1.1.4-1ubuntu1.2 (using .../vlc_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement vlc ...
Preparing to replace vlc-nox 1.1.4-1ubuntu1.2 (using .../vlc-nox_1.1.4-1ubuntu1.3_i386.deb) ...
Unpacking replacement vlc-nox ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-24-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.7271.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up openssh-client (1:5.5p1-4ubuntu5) ...
Setting up update-manager-core (1:0.142.22) ...
Setting up libhpmud0 (3.10.6-1ubuntu10.2) ...
Setting up libsane-hpaio (3.10.6-1ubuntu10.2) ...
Setting up hplip-data (3.10.6-1ubuntu10.2) ...
Setting up hpijs (3.10.6-1ubuntu10.2) ...
Setting up hplip (3.10.6-1ubuntu10.2) ...
Creating/updating hplip user account...
Setting up hplip-cups (3.10.6-1ubuntu10.2) ...
Setting up vlc-data (1.1.4-1ubuntu1.3) ...
Setting up libvlccore4 (1.1.4-1ubuntu1.3) ...
Setting up libvlc5 (1.1.4-1ubuntu1.3) ...
Setting up linux-image-generic (2.6.35.25.32) ...
Setting up linux-generic (2.6.35.25.32) ...
Setting up linux-headers-2.6.35-25 (2.6.35-25.44) ...
Setting up linux-headers-2.6.35-25-generic (2.6.35-25.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
Setting up linux-headers-generic (2.6.35.25.32) ...
Setting up linux-libc-dev (2.6.35-1025.44) ...
Setting up ssh-askpass-gnome (1:5.5p1-4ubuntu5) ...
Setting up vlc-nox (1.1.4-1ubuntu1.3) ...
Setting up vlc-plugin-notify (1.1.4-1ubuntu1.3) ...
Setting up vlc-plugin-pulse (1.1.4-1ubuntu1.3) ...
Setting up vlc (1.1.4-1ubuntu1.3) ...
Processing triggers for python-central ...
Setting up update-manager (1:0.142.22) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 alsa-driver-linuxant
Setting up alsa-driver-linuxant (1.0.23.1) ...
Building modules for the 2.6.35-24-generic kernel, please wait... done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.17322.log
dpkg: error processing alsa-driver-linuxant (--configure):
 subprocess installed post-installation script returned error exit status 2


Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick


Linux xxxx 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux
```

*****************************The alsa driver error log************
```

rm -f .depend *.o snd.map*
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/include'
rm -f .depend core *.o sndversions.h modules/*.ver modules/*.stamp
make -C sound clean
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/include/sound'
rm -f *.h
rm -f .includes*
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/include/sound'
rm -f *.orig *.rej *~ .#*
rm -rf linux/regulator
rm -rf linux/usb
rm -f linux/* asm/* media/*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/include'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/acore'
make -C ioctl32 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/ioctl32'
make -C oss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/oss'
make -C seq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq'
make -C oss mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq/oss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore/seq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/acore'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c'
make -C l3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/l3'
make -C other mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c/other'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/i2c'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers'
make -C mpu401 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/mpu401'
make -C opl3 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl3'
make -C opl4 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/opl4'
make -C pcsp mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/pcsp'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/drivers'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/isa'
make -C ad1816a mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1816a'
make -C ad1848 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/ad1848'
make -C cs423x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/cs423x'
make -C es1688 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/es1688'
make -C gus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/gus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/gus'
make -C msnd mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/msnd'
make -C opti9xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/opti9xx'
make -C sb mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/sb'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/sb'
make -C wavefront mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wavefront'
make -C wss mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa/wss'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/isa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/synth'
make -C emux mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth/emux'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/synth'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pci'
make -C ac97 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ac97'
make -C ali5451 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ali5451'
make -C asihpi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/asihpi'
make -C au88x0 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/au88x0'
make -C aw2 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/aw2'
make -C ca0106 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ca0106'
make -C cs46xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs46xx'
make -C cs5535audio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/cs5535audio'
make -C ctxfi mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ctxfi'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ctxfi'
make -C echoaudio mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/echoaudio'
make -C emu10k1 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/emu10k1'
make -C hda mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/hda'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/hda'
make -C ice1712 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ice1712'
make -C korg1212 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/korg1212'
make -C lx6464es mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/lx6464es'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/lx6464es'
make -C mixart mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/mixart'
make -C nm256 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/nm256'
make -C oxygen mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/oxygen'
make -C pcxhr mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pcxhr'
make -C pdplus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/pdplus'
make -C riptide mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/riptide'
make -C rme9652 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/rme9652'
make -C trident mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/trident'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/trident'
make -C vx222 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/vx222'
make -C ymfpci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci/ymfpci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pci'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/codecs'
make -C core mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/core'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/core'
make -C fabrics mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/fabrics'
make -C soundbus mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
make -C i2sbus mrproper
make[3]: Entering directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[3]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus/i2sbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa/soundbus'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/aoa'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/soc'
make -C atmel mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/atmel'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/atmel'
make -C au1x mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/au1x'
make -C blackfin mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/blackfin'
make -C codecs mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/codecs'
make -C davinci mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/davinci'
make -C fsl mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/fsl'
make -C imx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/imx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/imx'
make -C omap mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/omap'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/omap'
make -C pxa mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/pxa'
make -C s3c24xx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s3c24xx'
make -C s6000 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/s6000'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/s6000'
make -C sh mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/sh'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/sh'
make -C txx9 mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/soc/txx9'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc/txx9'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/soc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/usb'
make -C caiaq mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/caiaq'
make -C misc mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/misc'
make -C usx2y mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb/usx2y'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/usb'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make -C pdaudiocf mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf'
make -C vx mrproper
make[2]: Entering directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[2]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia/vx'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/pcmcia'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/misc'
rm -f .depend *.[oas] *.ko .*.cmd .*.tmp *.mod.c *.isapnp
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/misc'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/test'
rm -f *.o mmap_test osspcm osspcm1 ossdelay
rm -f *~ *.orig *.rej .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/test'
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *.orig *.rej *~ .#*
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant/utils'
rm -f *~ out.txt *.orig *.rej .#* .gdb_history
rm -f doc/*~
rm -f config.cache config.log config.status Makefile.conf
rm -f utils/alsa-driver.spec
rm -f `find alsa-kernel -name "*~"`
rm -f `find alsa-kernel -name "*.orig"`
rm -f `find alsa-kernel -name "*.rej"`
rm -f `find alsa-kernel -name ".#*"`
rm -f `find alsa-kernel -name "out.txt"`
rm -f `find . -name "Module.markers"`
rm -f `find . -name "modules.order"`
rm -rf autom4te.cache
echo skipping rm -f alsa-kernel/include/version.h
skipping rm -f alsa-kernel/include/version.h
rm -fr .tmp_versions
rm -f Module.symvers
find include/sound -name "*.h" -type l | xargs rm -f
rm -fr include/generated
find . -name "*.in" -a ! -name "configure.in" | sed 's/.in$//g' | xargs rm -f
rm -fr builds
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/lib/alsa-driver-linuxant
checking cross compile... 
checking for directory with ALSA kernel sources... ../alsa-kmirror
checking for directory with kernel source... /lib/modules/2.6.35-24-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-24-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/2.6.35-24-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i686
checking for ISA DMA API... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos_params.h... yes
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for usb_endpoint_dir_in and related functions... yes
checking for usb_endpoint_xfer_control... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for fmode_t... yes
checking for hrtimer_get_expires... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.23
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
checking for kernel linux/usb/ch9.h... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for bool... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for cards to compile driver for... all
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  Makefile.conf.in seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
(cd include/sound && ln -s ../../alsa-kernel/include/*.h .)
make dep
make[1]: Entering directory `/usr/lib/alsa-driver-linuxant'
#@for d in include acore i2c drivers isa synth pci aoa soc usb pcmcia misc; do if ! make -C $d prepare; then exit 1; fi; done
make[1]: Leaving directory `/usr/lib/alsa-driver-linuxant'
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/usr/lib/alsa-driver-linuxant  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hrtimer.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hrtimer.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/hwdep.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/hwdep.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memory_wrapper.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/memalloc.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.inc:1,
                 from /usr/lib/alsa-driver-linuxant/acore/memalloc.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/sgbuf.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/alsa-autoconf.h:4,
                 from /usr/lib/alsa-driver-linuxant/acore/sgbuf.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm.c:1:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
  CC [M]  /usr/lib/alsa-driver-linuxant/acore/pcm_native.o
In file included from /usr/lib/alsa-driver-linuxant/include/config.h:6,
                 from /usr/lib/alsa-driver-linuxant/include/adriver.h:25,
                 from /usr/lib/alsa-driver-linuxant/acore/pcm_native.c:2:
/usr/lib/alsa-driver-linuxant/include/config1.h:175: warning: "CONFIG_SND_HDA_INPUT_BEEP_MODE" redefined
./include/generated/autoconf.h:2222: note: this is the location of the previous definition
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c: In function ‘snd_pcm_hw_params’:
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:489: error: implicit declaration of function ‘pm_qos_remove_requirement’
/usr/lib/alsa-driver-linuxant/acore/pcm_native.c:492: error: implicit declaration of function ‘pm_qos_add_requirement’
make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/pcm_native.o] Error 1
make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [compile] Error 2
**********************************************
```

---

### Post by badnaam on 2011-01-30
I tried to uninstall the linuxant driver and now my sound does not work at all. I can't even start alsamixer (says can't find "mixer").

Here is teh result of the alsa diagnostic script.


```
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.60
!!################################

!!Script ran on: Mon Jan 31 04:19:33 UTC 2011


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      Satellite L305
Product Version:   PSLB8U-142025


!!Kernel Information
!!------------------

Kernel release:    2.6.35-25-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
	Subsystem: 1179:ff66


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------



!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
aes_i586
aes_generic
binfmt_misc
parport_pc
ppdev
joydev
arc4
i915
drm_kms_helper
drm
rtl8187
mac80211
led_class
cfg80211
eeprom_93cx6
psmouse
intel_agp
i2c_algo_bit
serio_raw
video
agpgart
output
lp
parport
usb_storage
r8169
ahci
mii
libahci


!!ALSA/HDA dmesg
!!------------------
```

---

