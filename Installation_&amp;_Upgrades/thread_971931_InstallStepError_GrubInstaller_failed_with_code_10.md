---
title: "InstallStepError: GrubInstaller failed with code 10 (using RAID)"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by marcog on 2008-11-05
I'm trying to install Intrepid, but the installer crashes right at the end when setting up grub. I suspect the issue is related to RAID (I am using dmraid).

Links to the full crash dump and syslog are below. The crucial bit (I think) is this:

```
Nov  5 16:37:46 ubuntu python: log-output -t ubiquity umount /target/cdrom
Nov  5 16:37:46 ubuntu finish-install: Disabling CD in sources.list
Nov  5 16:37:46 ubuntu python: Exception during installation:
Nov  5 16:37:46 ubuntu python: Traceback (most recent call last):
Nov  5 16:37:46 ubuntu python:   File "/usr/share/ubiquity/install.py", line 2112, in <module>
Nov  5 16:37:46 ubuntu python:     install.run()
Nov  5 16:37:46 ubuntu python:   File "/usr/share/ubiquity/install.py", line 428, in run
Nov  5 16:37:46 ubuntu python:     self.configure_bootloader()
Nov  5 16:37:46 ubuntu python:   File "/usr/share/ubiquity/install.py", line 1599, in configure_bootloader
Nov  5 16:37:46 ubuntu python:     "GrubInstaller failed with code %d" % ret)
Nov  5 16:37:46 ubuntu python: InstallStepError: GrubInstaller failed with code 10
Nov  5 16:37:46 ubuntu python: 
Nov  5 16:37:46 ubuntu ubiquity[8158]: debconffilter_done: Install (current: None)
Nov  5 16:37:46 ubuntu ubiquity[8158]: Exception in GTK frontend (invoking crash handler):
Nov  5 16:37:46 ubuntu ubiquity[8158]: Traceback (most recent call last):
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
Nov  5 16:37:46 ubuntu ubiquity[8158]:     main()
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
Nov  5 16:37:46 ubuntu ubiquity[8158]:     install(args[0])
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
Nov  5 16:37:46 ubuntu ubiquity[8158]:     ret = wizard.run()
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 437, in run
Nov  5 16:37:46 ubuntu ubiquity[8158]:     self.progress_loop()
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 825, in progress_loop
Nov  5 16:37:46 ubuntu ubiquity[8158]:     (ret, realtb))
Nov  5 16:37:46 ubuntu ubiquity[8158]: RuntimeError: Install failed with exit code 1
Nov  5 16:37:46 ubuntu ubiquity[8158]: Traceback (most recent call last):
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/share/ubiquity/install.py", line 2112, in <module>
Nov  5 16:37:46 ubuntu ubiquity[8158]:     install.run()
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/share/ubiquity/install.py", line 428, in run
Nov  5 16:37:46 ubuntu ubiquity[8158]:     self.configure_bootloader()
Nov  5 16:37:46 ubuntu ubiquity[8158]:   File "/usr/share/ubiquity/install.py", line 1599, in configure_bootloader
Nov  5 16:37:46 ubuntu ubiquity[8158]:     "GrubInstaller failed with code %d" % ret)
Nov  5 16:37:46 ubuntu ubiquity[8158]: InstallStepError: GrubInstaller failed with code 10
Nov  5 16:37:46 ubuntu ubiquity[8158]: 

```

as well as maybe this, which appears above:

```
Nov  5 16:37:45 ubuntu grub-installer: info: architecture: amd64/generic
Nov  5 16:37:45 ubuntu grub-installer: info: Identified partition label for /dev/mapper/isw_cfifhcidij_Volume01: loop
Nov  5 16:37:45 ubuntu grub-installer: dpkg - warning: ignoring request to remove grub-pc which isn't installed.
Nov  5 16:37:45 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/mapper/isw_cfifhcidij_Volume02
Nov  5 16:37:45 ubuntu kernel: [ 1384.227885] cramfs: wrong magic
Nov  5 16:37:45 ubuntu kernel: [ 1384.256427] kjournald starting.  Commit interval 5 seconds
Nov  5 16:37:45 ubuntu kernel: [ 1384.256439] EXT3-fs: mounted filesystem with ordered data mode.
Nov  5 16:37:45 ubuntu 50mounted-tests: debug: mounted as ext3 filesystem
Nov  5 16:37:45 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10freedos
Nov  5 16:37:45 ubuntu 10freedos: debug: /dev/mapper/isw_cfifhcidij_Volume02 is not a FAT partition: exiting
Nov  5 16:37:45 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/10qnx
Nov  5 16:37:45 ubuntu 10qnx: debug: /dev/mapper/isw_cfifhcidij_Volume02 is not a QNX4 partition: exiting
Nov  5 16:37:45 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/20microsoft
Nov  5 16:37:45 ubuntu 20microsoft: debug: /dev/mapper/isw_cfifhcidij_Volume02 is not a MS partition: exiting
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/30utility
Nov  5 16:37:46 ubuntu 30utility: debug: /dev/mapper/isw_cfifhcidij_Volume02 is not a FAT partition: exiting
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/40lsb
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/70hurd
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/80minix
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Nov  5 16:37:46 ubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris

```

Not sure if this output of lspci might help:

```
ubuntu@ubuntu:~$ lspci 
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation Device 05e1 (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

```

Crash dump: [http://people.cs.uct.ac.za/~mgallott/resources/grub_crash/_usr_lib_ubiquity_bin_ubiquity.0.crash](http://people.cs.uct.ac.za/~mgallott/resources/grub_crash/_usr_lib_ubiquity_bin_ubiquity.0.crash)
Syslog: [http://people.cs.uct.ac.za/~mgallott/resources/grub_crash/syslog](http://people.cs.uct.ac.za/~mgallott/resources/grub_crash/syslog)

---

