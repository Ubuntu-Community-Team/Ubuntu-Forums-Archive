---
title: "Confirmed mapper-root device exists but boot fails on non-existenceing root device"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by ubunteduser on 2008-08-17
Hello. I could not find a thread that exactly matched my problems. So please help if you know the answer.

I have an existing Hardy desktop 64-bit (8.04) installation and it failed boot on power outage. Booting fails on Hardy installation and drops to BusyBox. After turning off splash I saw some messages just before it dropped to busybox.

[INDENT][INDENT]Check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev/
Reading all physical volumes. This may take a while...
Found volume group "home" using metadata type lvm2
Found volume group "root uisng metadata type lvm2
ALERT! /dev/mapper/root-root does not exists. Dropping to a shell!
[/INDENT][/INDENT]

/dev/mapper/root-root is my device, though not a standard name. I checked boot args and checked modules.

"ls /dev/mapper" shows root-root is there.

"ls /dev/root/root" shows that it is there (is /dev/mapper/root-root linked to /dev/root/root)

"lvm lvscan" shows that /dev/root/root is recognized as a logical volume.

Can anyone help me find what is up and how I can get my machine up?

Edward Ing

---

### Post by ubunteduser on 2008-08-17
Some supplementary information:

If I look at the /etc/lvm/backup 's to look at LVM descriptions I see that the descriptions are generated.
I have two logical volumes to mount, but for root VG description it says in the description 
"Created *after* executing 'vgscan'" where as for my "home" drive it says "Created *after* executing 'vgchange -a y'

Is there anything suspicious here?

---

### Post by ubunteduser on 2008-08-17
More debugging and it looks like it hangs at the test in one of the boot scripts at the command "/lib/udev/vol_id /dev/mapper/root-root".

When it drops to initramfs, I run the command "/lib/udev/vol_id /dev/mapper/root-root" manually and I get "unknown volume type"

Any additional information would be useful.

I do the scans and the volumes are there, except for this problem.
I do the scans and the volumes are there, except for this problem.

> **ubunteduser said:**
> Some supplementary information:

If I look at the /etc/lvm/backup 's to look at LVM descriptions I see that the descriptions are generated.
I have two logical volumes to mount, but for root VG description it says in the description 
"Created *after* executing 'vgscan'" where as for my "home" drive it says "Created *after* executing 'vgchange -a y'

Is there anything suspicious here?

---

