---
title: "ubiquity.components.partman Crash During Installation (Exit Code 141)"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by MrQuan on 2010-09-20
I've tried installing Ubuntu 9.10 on four small Pentium 3 touchscreen PCs.  The first install went without a hitch using the USB stick install and runs nicely, but I consitantly get the same error on the other three of them.  I'm installing from the same USB stick and trying to do a complete new install (i.e. reformat/parition) and it seems to boot up ok.  I hit F12 to enter the boot menu and select boot from UBS stick to run the ubuntu installer.

After selecting the language and locale in the installation wizard I click the forward button and see a dialog pop up that says something like 'loading partitions' then I get an error message that says ubiquity.components.partman crashed with exit code 141.

I can load up the liveCD and I opened GParted and deleted all the partitions on the harddrive and then tried installing for in the LiveCD and by restarting and installing from USB again.  Both failed with the same error.

Here's the end of the syslog.  I've also zipped up the complete file and attached it.  Any help would be greatly appreciated!

```
Sep 21 10:25:51 ubuntu localechooser: info: Default country = 'US'
Sep 21 10:25:51 ubuntu localechooser: info: Set debian-installer/consoledisplay = 'console-setup'
Sep 21 10:25:51 ubuntu localechooser: info: Set debian-installer/country = 'AU'
Sep 21 10:25:51 ubuntu localechooser: info: Set debian-installer/locale = 'en_AU.UTF-8'
Sep 21 10:25:51 ubuntu localechooser: info: Selected locale (debian-installer/locale) = 'en_AU.UTF-8'
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu 10freedos: debug: /dev/sdb1 is a FAT32 partition
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu 20microsoft: debug: /dev/sdb1 is a FAT32 partition
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing
Sep 21 10:25:52 ubuntu ubiquity: : No such file or directory
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing: No such file or directory
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing: No such file or directory
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing: No such file or directory
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu 30utility: debug: /dev/sdb1 is a FAT32 partition
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing: No such file or directory
Sep 21 10:25:52 ubuntu ubiquity: ls: cannot access /casper-rw-backing: No such file or directory
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Sep 21 10:25:52 ubuntu os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Sep 21 10:25:54 ubuntu ubiquity[5846]: debconffilter_done: ubi-timezone (current: ubi-timezone)
Sep 21 10:25:54 ubuntu ubiquity[5846]: Step_before = stepLocation
Sep 21 10:25:55 ubuntu ubiquity[5846]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option 
Sep 21 10:25:55 ubuntu ubiquity[5846]: switched to page console_setup
Sep 21 10:26:03 ubuntu ubiquity: Your console font configuration will be updated the next time your system
Sep 21 10:26:03 ubuntu ubiquity: boots. If you want to update it now, run 'setupcon' from a virtual console.
Sep 21 10:26:03 ubuntu ubiquity[5846]: log-output -t ubiquity setxkbmap -model pc105 -layout us -option  -option 
Sep 21 10:26:03 ubuntu ubiquity[5846]: debconffilter_done: ubi-console-setup (current: ubi-console-setup)
Sep 21 10:26:03 ubuntu ubiquity[5846]: Step_before = stepKeyboardConf
Sep 21 10:26:04 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Sep 21 10:26:07 ubuntu ubiquity[5846]: debconffilter_done: ubiquity.components.partman (current: ubiquity.components.partman)
Sep 21 10:26:07 ubuntu ubiquity[5846]: dbfilter_handle_status: ('ubiquity.components.partman', 141)
Sep 21 10:28:50 ubuntu ubiquity[5846]: dbfilter_handle_status: response -7
Sep 21 10:28:51 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 21 10:28:51 ubuntu ubiquity[5846]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^console-setup/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
Sep 21 10:28:51 ubuntu ubiquity: debconf: DbDriver "targetdb": could not open /target/var/cache/debconf/config.dat
Sep 21 10:28:51 ubuntu ubiquity[5846]: log-output -t ubiquity debconf-copydb configdb targetdb -p ^xserver-xorg/ --config=Name:targetdb --config=Driver:File --config=Filename:/target/var/cache/debconf/config.dat
```

---

### Post by MrQuan on 2010-09-21
I've managed to get it working by formatting my USB stick and using the 'USB Startup Disk Creator' to rebuild everything.

It has now successfully installed - I'm not sure what corrupted it, but it seems good now :-)

---

