---
title: "cannot install karmic"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by b0b138 on 2009-10-14
I've been trying to install karmic, both alone and duel boot with jaunty. It seems to go through the install fine but never throws up a window saying install done, reboot now.  On reboot I got a grub error. Here is the end of a log file showing an error

```
Oct 14 02:26:41 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Oct 14 02:26:41 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Oct 14 02:26:42 ubuntu 50mounted-tests: debug: /dev/sda5 type not recognised; skipping
Oct 14 02:26:42 ubuntu os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Oct 14 02:26:42 ubuntu linux-boot-prober: debug: running /usr/lib/linux-boot-probes/50mounted-tests
Oct 14 02:26:42 ubuntu 50mounted-tests: debug: running /usr/lib/linux-boot-probes/mounted/40grub /dev/sda1 /dev/sda1 /var/lib/os-prober/mount ext4
Oct 14 02:26:42 ubuntu 40grub: debug: parsing menu.lst
Oct 14 02:26:42 ubuntu 40grub: result: /dev/sda1:/dev/sda1:Ubuntu 9.04, kernel 2.6.28-15-generic:/boot/vmlinuz-2.6.28-15-generic:/boot/initrd.img-2.6.28-15-generic:root=UUID=63114d08-fd84-4d49-9525-1627e2091a02 ro quiet splash
Oct 14 02:26:42 ubuntu 40grub: result: /dev/sda1:/dev/sda1:Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode):/boot/vmlinuz-2.6.28-15-generic:/boot/initrd.img-2.6.28-15-generic:root=UUID=63114d08-fd84-4d49-9525-1627e2091a02 ro single
Oct 14 02:26:42 ubuntu 40grub: result: /dev/sda1:/dev/sda1:Ubuntu 9.04, kernel 2.6.28-11-generic:/boot/vmlinuz-2.6.28-11-generic:/boot/initrd.img-2.6.28-11-generic:root=UUID=63114d08-fd84-4d49-9525-1627e2091a02 ro quiet splash
Oct 14 02:26:42 ubuntu 40grub: result: /dev/sda1:/dev/sda1:Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode):/boot/vmlinuz-2.6.28-11-generic:/boot/initrd.img-2.6.28-11-generic:root=UUID=63114d08-fd84-4d49-9525-1627e2091a02 ro single
Oct 14 02:26:42 ubuntu 40grub: result: /dev/sda1:/dev/sda1:Ubuntu 9.04, memtest86+:/boot/memtest86+.bin::
Oct 14 02:26:42 ubuntu 50mounted-tests: debug: /usr/lib/linux-boot-probes/mounted/40grub succeeded
Oct 14 02:26:42 ubuntu kernel: [ 1383.287524] EXT4-fs: mballoc: 0 preallocated, 0 discarded
Oct 14 02:26:42 ubuntu kernel: [ 1383.853961] EXT4-fs (sda1): barriers enabled
Oct 14 02:26:42 ubuntu kernel: [ 1383.854232] kjournald2 starting: pid 22139, dev sda1:8, commit interval 5 seconds
Oct 14 02:26:42 ubuntu kernel: [ 1383.854238] EXT4-fs (sda1): delayed allocation enabled
Oct 14 02:26:42 ubuntu kernel: [ 1383.854241] EXT4-fs: file extents enabled
Oct 14 02:26:42 ubuntu kernel: [ 1383.857804] EXT4-fs: mballoc enabled
Oct 14 02:26:42 ubuntu kernel: [ 1383.857814] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 14 02:26:42 ubuntu kernel: [ 1383.987978] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
Oct 14 02:26:42 ubuntu linux-boot-prober: debug: linux detected by /usr/lib/linux-boot-probes/50mounted-tests
Oct 14 02:26:42 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Oct 14 02:26:42 ubuntu grub-installer: info: Boot partition is on a Serial ATA RAID disk, multipath, or mdadm device
Oct 14 02:26:42 ubuntu grub-installer: error: Grub stage files not available
Oct 14 02:26:42 ubuntu python: log-output -t ubiquity umount /target/cdrom
Oct 14 02:26:42 ubuntu finish-install: Disabling CD in sources.list
```

Right now I'm trying to duel boot but haven't bothered rebooting yet.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009499f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux   (/home)
/dev/sdb2           30402       60801   244188000    5  Extended
/dev/sdb5           30402       60801   244187968+  83  Linux   (extra partition)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf485f485

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8177    65681721   83  Linux   (/ for jaunty)
/dev/sda2            9487        9729     1951897+   5  Extended
/dev/sda3            8178        9486    10514542+  83  Linux   (space made from resizing sda1 to try a duel boot)
/dev/sda5            9487        9729     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```

---

### Post by b0b138 on 2009-10-14
here's another log

```
Oct 14 02:26:42 ubuntu kernel: [ 1383.857814] EXT4-fs (sda1): mounted filesystem with ordered data mode
Oct 14 02:26:42 ubuntu kernel: [ 1383.987978] EXT4-fs: mballoc: 0 blocks 0 reqs (0 success)
Oct 14 02:26:42 ubuntu linux-boot-prober: debug: linux detected by /usr/lib/linux-boot-probes/50mounted-tests
Oct 14 02:26:42 ubuntu grub-installer: info: Installing grub on '/dev/sda'
Oct 14 02:26:42 ubuntu grub-installer: info: Boot partition is on a Serial ATA RAID disk, multipath, or mdadm device
Oct 14 02:26:42 ubuntu grub-installer: error: Grub stage files not available
Oct 14 02:26:42 ubuntu python: log-output -t ubiquity umount /target/cdrom
Oct 14 02:26:42 ubuntu finish-install: Disabling CD in sources.list
Oct 14 02:26:42 ubuntu python: Exception during installation:
Oct 14 02:26:42 ubuntu python: Traceback (most recent call last):
Oct 14 02:26:42 ubuntu python:   File "/usr/share/ubiquity/install.py", line 2323, in <module>
Oct 14 02:26:42 ubuntu python:     install.run()
Oct 14 02:26:42 ubuntu python:   File "/usr/share/ubiquity/install.py", line 460, in run
Oct 14 02:26:42 ubuntu python:     self.configure_bootloader()
Oct 14 02:26:42 ubuntu python:   File "/usr/share/ubiquity/install.py", line 1740, in configure_bootloader
Oct 14 02:26:42 ubuntu python:     "GrubInstaller failed with code %d" % ret)
Oct 14 02:26:42 ubuntu python: InstallStepError: GrubInstaller failed with code 1
Oct 14 02:26:42 ubuntu python: 
Oct 14 02:26:42 ubuntu ubiquity[3322]: debconffilter_done: ubiquity.components.install (current: None)
Oct 14 02:26:42 ubuntu ubiquity[3322]: Exception in GTK frontend (invoking crash handler):
Oct 14 02:26:42 ubuntu ubiquity[3322]: Traceback (most recent call last):
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/lib/ubiquity/bin/ubiquity", line 457, in <module>
Oct 14 02:26:42 ubuntu ubiquity[3322]:     main(oem_config)
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/lib/ubiquity/bin/ubiquity", line 442, in main
Oct 14 02:26:42 ubuntu ubiquity[3322]:     install(args[0], query=options.query)
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/lib/ubiquity/bin/ubiquity", line 245, in install
Oct 14 02:26:42 ubuntu ubiquity[3322]:     ret = wizard.run()
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 457, in run
Oct 14 02:26:42 ubuntu ubiquity[3322]:     self.progress_loop()
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 967, in progress_loop
Oct 14 02:26:42 ubuntu ubiquity[3322]:     (ret, realtb))
Oct 14 02:26:42 ubuntu ubiquity[3322]: RuntimeError: Install failed with exit code 1
Oct 14 02:26:42 ubuntu ubiquity[3322]: Traceback (most recent call last):
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/share/ubiquity/install.py", line 2323, in <module>
Oct 14 02:26:42 ubuntu ubiquity[3322]:     install.run()
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/share/ubiquity/install.py", line 460, in run
Oct 14 02:26:42 ubuntu ubiquity[3322]:     self.configure_bootloader()
Oct 14 02:26:42 ubuntu ubiquity[3322]:   File "/usr/share/ubiquity/install.py", line 1740, in configure_bootloader
Oct 14 02:26:42 ubuntu ubiquity[3322]:     "GrubInstaller failed with code %d" % ret)
Oct 14 02:26:42 ubuntu ubiquity[3322]: InstallStepError: GrubInstaller failed with code 1
Oct 14 02:26:42 ubuntu ubiquity[3322]: 
Oct 14 02:26:42 ubuntu ubiquity[3322]: 
```

---

### Post by b0b138 on 2009-10-14
bump

---

### Post by VMC on 2009-10-14
According to those logs grub failed to install. How are you setup at present? You mentioned both alone and with jaunty.

It doesn't matter right now. You can chroot to karmic and then issue "grub-install" message, following [this]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") document.

---

### Post by b0b138 on 2009-10-15
Thanks that worked. I did have to do grub-install --recheck /dev/sda first as update-grub and grub-install both kept giving errors.

Any ideas why the installer couldn't install grub?

---

### Post by VMC on 2009-10-15
Maybe because of raid:
```
ubuntu grub-installer: info: Boot partition is on a Serial ATA RAID disk, multipath, or mdadm device
ubuntu grub-installer: error: Grub stage files not available
u
```

Also the python script may reveal an answer:
```
Exception during installation:
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2323, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 460, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1740, in configure_bootloader
    "GrubInstaller failed with code %d" % ret)
GrubInstaller failed with code 1

None)
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 457, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 442, in main
    install(args[0], query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 245, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 457, in run
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 967, in progress_loop
    (ret, realtb))
Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2323, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 460, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1740, in configure_bootloader
    "GrubInstaller failed with code %d" % ret)
GrubInstaller failed with code 1

Oct 14 02:26:42 ubuntu ubiquity[3322]:

```

---

