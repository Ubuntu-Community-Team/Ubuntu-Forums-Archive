---
title: "preseed / partman not partitioning disk"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by gr8rcake on 2011-11-13
Issue: Preseeding appears to work up until the partitioning of the disk /dev/sda. At his point I get a "no root partition is defined" message.

If the:

```
d-i partman/choose_partition select finish
d-i partman/confirm boolean true

```

lines are commented out, the screen displays any existing partitions on the disk and doesn't present a "next" button.

It appears as if the installer is reading the disk, but not writing the new partition table to the disk.

I have tried this in both LVM and regular modes. It doesn't appear to be due to the partitioning scheme, as I have tried dozens of different ones from web.

I have replaced the entire partition section with web examples, with the same results.

If I wipe out the partition table beforehand with:

```
# dd if=/dev/zero of=/dev/sda count-1 bs=512
```

I get the same symptoms, except in the case where the above partman statements are commented out, a blank display of partitions is presented.

The partition tables definitely don't get written. The original OS can always boot after the preseed failures.

Fedora kickstart works perfectly on the system. I have also successfully used ntfsclone on the system to install windows using a livecd.

Realising this is a fake RAID system, I have tried the dmraid options in grub and preseed file with no change in the symptoms.

---------------

My grub boot options are

```
priority=critical preseed/url=http://server/seedfile.seed  interface=auto netcfg/dhcp_timeout=60 auto=true ip=dhcp
```

System Info

```
OS: Ubuntu 11.10
HW: Acer AM3410 desktop PC (Fake RAID)
```

I am getting the initrd and linux files from this directory of the installation CD

```
/install/netboot/ubuntu-installer/i386/
```

I am using this ISO as the source CD for the initrd and linux kernel files

```
ubuntu-11.10-server-i386.iso
```

The preseed file looks like this:

```
d-i debian-installer/locale string en_US
d-i console-setup/ask_detect boolean false
d-i console-setup/layoutcode string us
d-i netcfg/choose_interface select eth0
d-i netcfg/disable_dhcp boolean true
d-i netcfg/get_nameservers string 192.168.1.254
d-i netcfg/get_ipaddress string 192.168.1.150
d-i netcfg/get_netmask string 255.255.255.0
d-i netcfg/get_gateway string 192.168.1.254
d-i netcfg/confirm_static boolean true
d-i netcfg/get_hostname string unassigned-hostname
d-i netcfg/get_domain string unassigned-domain
d-i netcfg/wireless_wep string
d-i mirror/country string manual
d-i mirror/http/hostname string archive.ubuntu.com
d-i mirror/http/directory string /ubuntu
d-i mirror/http/proxy string
d-i clock-setup/utc boolean true
d-i time/zone string US/Pacific
d-i clock-setup/ntp boolean true
d-i clock-setup/ntp-server string 0.pool.ntp.org
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string regular
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
d-i partman-auto-lvm/guided_size string max
d-i partman-auto/choose_recipe select boot-root
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto-lvm/new_vg_name string vg00
d-i partman-auto-lvm/new_vg_name_exists string
d-i partman-lvm/vgcreate string vg00
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              4096 4096 4096 ext4                             \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              100 1000 100000000 ext4                         \
                      $defaultignore{ }                       \
                      $primary{ }                             \
                      method{ lvm }                           \
                      device{ /dev/sda }                      \
                      vg_name{ vg00 }                         \
              .                                               \
              4096 2 100000000 ext4                           \
                      method{ format } format{ } $lvmok{ }    \
                      in_vg{ vg00 }                           \
                      lv_name{ vg00-lv01 }                    \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
              .                                               \
              4096 4096 300% linux-swap                       \
                      method{ swap } format{ }                \
              .
d-i partman/default_filesystem string ext4
d-i partman-partitioning/confirm_write_new_label boolean true
d-i partman/choose_partition select finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true
d-i passwd/root-login boolean true
d-i passwd/make-user boolean false
d-i passwd/root-password password r00tme
d-i passwd/root-password-again password r00tme
d-i user-setup/encrypt-home boolean false
tasksel tasksel/first multiselect lamp-server, print-server
d-i pkgsel/include string openssh-server build-essential
d-i pkgsel/updatedb boolean true
d-i grub-installer/only_debian boolean true
d-i grub-installer/with_other_os boolean true
d-i finish-install/reboot_in_progress note
```

Any assistance would be very welcome. I've been banging my head against the wall for a week. Ouch!

---

### Post by gr8rcake on 2011-11-13
Cleaned up code section to make it easier to read

---

### Post by westie457 on 2011-11-13
Hello, welcome to the Forum.

Willing to admit that I know nothing about setting up LVM or Fakeraid or anything that is not classed as a vanilla install. However a /Root partition has to be created before an install will go ahead whether or not you have a separate /Boot partition.

Take a look at [this]("https://help.ubuntu.com/community/FakeRaidHowto") even though it probably is not what you are doing it should give you some clues.

Good luck.

---

### Post by gr8rcake on 2011-11-13
Thanks for the quick reply.

This section of the preseed file shows the root partition being defined.

I don't understand why the partition table isn't being updated.

I would have thought Ubuntu would automatically create the defined partitions without you having to create them beforehand. Fedora does it seamlessly, I would think Ubuntu would too.


```
              4096 2 100000000 ext4                           \
                      method{ format } format{ } $lvmok{ }    \
                      in_vg{ vg00 }                           \
                      lv_name{ vg00-lv01 }                    \
                      use_filesystem{ } filesystem{ ext4 }    \
                      mountpoint{ / }                         \
```

---

### Post by gr8rcake on 2011-11-22
When I use the example in the installation-guide package , usr/share/doc/installation-guide-i386/example-preseed.txt.gz, I get the following message on the screen "no root file system is defined"

It's as if the installer isn't formatting the disks at all.

Any help would be really appreciated. This is driving me crazy.

---

### Post by gr8rcake on 2011-11-23
It might be due to dmraid. The last two deb packages accessed on the proxy server prior to the failure are related to dmraid:

```
1321981599.123      0 192.168.1.99 TCP_MEM_HIT/200 10820 GET http://192.168.1.100:3128/ubuntu/pool/main/d/dmraid/dmraid-udeb_1.0.0.rc16-3ubuntu2_amd64.udeb - HIER_NONE/- application/x-debian-package
1321981599.144      1 192.168.1.99 TCP_MEM_HIT/200 93559 GET http://192.168.1.100:3128/ubuntu/pool/main/d/dmraid/libdmraid1.0.0.rc16-udeb_1.0.0.rc16-3ubuntu2_amd64.udeb - HIER_NONE/- application/x-debian-package
```

And this thread seems to imply this is an issue. [http://ubuntuforums.org/showthread.php?t=1836834](http://ubuntuforums.org/showthread.php?t=1836834)

I changed the BIOS setting in the "Integrated peripherals" section to "Native IDE" from "AHCI RAID", but got the same issue. I can install Fedora with this "Native IDE" setting without issue.

Very, very strange.

---

