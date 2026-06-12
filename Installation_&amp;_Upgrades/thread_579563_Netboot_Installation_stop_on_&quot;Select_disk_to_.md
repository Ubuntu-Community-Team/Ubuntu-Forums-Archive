---
title: "Netboot Installation stop on &quot;Select disk to partition&quot;"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by chris.zeman on 2007-10-18
I am attempting a netboot installation of Ubuntu 7.10, but the installer doesn't automatically select the disk (the only one in the system) to partition. I thought everything in my preseed file was correct since it is mostly a copy of an example I found.

Here is my preseed file:
```
#### Contents of the preconfiguration file

### Network configuration
d-i netcfg/choose_interface select auto
d-i netcfg/get_hostname string energy-management-install

### Mirror settings
d-i mirror/country string enter information manually
d-i mirror/http/hostname string automation
d-i mirror/http/directory string /ubuntu/7.10
d-i mirror/http/proxy string

### Partitioning
d-i partman-auto/disk string /dev/sda
d-i partman-auto/init_automatically_partition \
	select Guided - use entire disk
d-i partman-auto/choose_recipe \
	select All files in one partition (recommended for new users)
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition \
       select Finish partitioning and write changes to disk
d-i partman/confirm boolean true

### Clock and time zone setup
d-i clock-setup/utc boolean true
d-i time/zone string US/Central

d-i  prebaseconfig/reboot_in_progress   note

d-i     debconf/priority        select  critical
debconf debconf/priority        select  critical

base-config  base-config/intro          note
base-config  base-config/login          note

# The user's name and login.
passwd passwd/user-fullname            string user
passwd passwd/username                 string user
# And their password, but use caution!
passwd passwd/user-password            user password
passwd passwd/user-password-again      user password

#install desktop + standard packages
tasksel tasksel/first multiselect ubuntu-standard, ubuntu-desktop
d-i     finish-install/reboot_in_progress note
```

Thank you,
Chris

---

### Post by gsker on 2008-06-05
You ever solve this?  I'm seeing the samet thing on 8.04 and am baffled.

This is what it looks like when it asks the question:

Jun  6 17:51:17 debconf: --> INPUT critical partman-auto/select_disk
Jun  6 17:51:17 debconf: <-- 0 question will be asked
Jun  6 17:51:17 debconf: --> GO
Jun  6 17:51:19 debconf: <-- 0 ok
Jun  6 17:51:19 debconf: --> GET partman-auto/select_disk
Jun  6 17:51:19 debconf: <-- 0 SCSI.CCISS (-,0,0) (cciss/c0d0) - 300.0 GB Compaq Smart Array
Jun  6 17:51:19 debconf: --> METAGET partman/text/scsi_disk description
Jun  6 17:51:19 debconf: <-- 0 SCSI%s (%s,%s,%s) (%s)
Jun  6 17:51:19 debconf: --> GET partman-auto/expert_recipe
Jun  6 17:51:19 debconf: <-- 0 
Jun  6 17:51:19 debconf: --> GET partman-auto/expert_recipe_file
Jun  6 17:51:19 debconf: <-- 0 
Jun  6 17:51:19 debconf: --> GET partman-auto/choose_recipe
Jun  6 17:51:19 debconf: <-- 0 Separate /home, /usr, /var, and /tmp partitions

And if I put this in my preseed file:
d-i partman-auto/select_disk string SCSI.CCISS (-,0,0) (/dev/cciss/c0d0) - 300.0 GB Compaq Smart Array

It goes into this weird loop.  The important part *seems* to be the following, but it just loops over and over.

Jun  6 12:38:45 debconf: <-- 0
Jun  6 12:38:45 debconf: --> INPUT critical partman-auto/select_disk
Jun  6 12:38:45 debconf: <-- 30 question skipped
Jun  6 12:38:45 debconf: --> GO
Jun  6 12:38:45 debconf: <-- 0 ok
Jun  6 12:38:45 debconf: --> GET partman-auto/select_disk
Jun  6 12:38:45 debconf: <-- 0 SCSI.CCISS (-,0,0) (/dev/cciss/c0d0) - 300.0 GB Compaq Smart Array
Jun  6 12:38:45 debconf: --> METAGET partman/text/scsi_disk description
Jun  6 12:38:45 debconf: <-- 0 SCSI%s (%s,%s,%s) (%s)
Jun  6 12:38:45 partman: Error running 'tune2fs -l /dev/cciss/c0d0'
Jun  6 12:38:45 partman: Error running 'tune2fs -l /dev/cciss/c0d0'
Jun  6 12:38:45 partman: Error running 'tune2fs -l /dev/cciss/c0d0'


Any clues?  Wonder how I bump this, or if it's actually a bug?

I filed a bug report: [https://bugs.launchpad.net/bugs/237986](https://bugs.launchpad.net/bugs/237986)

---

