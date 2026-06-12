---
title: "cannot access other hard drives"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by scoobydoo518 on 2006-09-12
Evening All,

   I am trying the Live CD(i386 on an AMD 64 X2 4200+) and for some reason cannot access other hard drives on my system. I can "see" all drives in Disks manager but when I click on one to browse I get an error that I don't have permissions to view contents of "disks-conf-hdd1". the properties tab does not allow me to make the drive readable(formatted NTFS). In fact I cannot access even my other linux drive(Suse 10.1 x86_64).

Is this because I'm using the Live version and all will work if I do an install?

Suggestions?

TIA

---

### Post by goatflyer on 2006-09-12
The livecd ships with a conservatively restrictive /etc/fstab on purpose.  There is no problem accessing drives after installation, but if you want to try it using the live cd, open a terminal window and

gksudo nautilus

Be careful, you are superuser....

---

### Post by randell6564 on 2006-09-12
> **scoobydoo518 said:**
> Evening All,

   I am trying the Live CD(i386 on an AMD 64 X2 4200+) and for some reason cannot access other hard drives on my system. I can "see" all drives in Disks manager but when I click on one to browse I get an error that I don't have permissions to view contents of "disks-conf-hdd1". the properties tab does not allow me to make the drive readable(formatted NTFS). In fact I cannot access even my other linux drive(Suse 10.1 x86_64).

Is this because I'm using the Live version and all will work if I do an install?

Suggestions?

TIA
You will have no problems accessing your other HD's AFTER you install Ubuntu and add those HD's to your /etc/fstab
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by randell6564 on 2006-09-12
> **scoobydoo518 said:**
> Evening All,

   I am trying the Live CD(i386 on an AMD 64 X2 4200+) and for some reason cannot access other hard drives on my system. I can "see" all drives in Disks manager but when I click on one to browse I get an error that I don't have permissions to view contents of "disks-conf-hdd1". the properties tab does not allow me to make the drive readable(formatted NTFS). In fact I cannot access even my other linux drive(Suse 10.1 x86_64).

Is this because I'm using the Live version and all will work if I do an install?

Suggestions?

TIA
You will have no problems accessing your other HD's AFTER you install Ubuntu and add those HD's to your /etc/fstab
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

