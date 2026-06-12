---
title: "ntfs mounting problem"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by w3rt on 2009-01-14
upgraded from intrepid to jaunty today, i haveonly had one problem, I am unable to mount ntfs partitions, i get the error "cannot get volume.fstype.alternative

Has anyone else had this error too?

---

### Post by minisori on 2009-01-14
Yes, it's aalready reported in launchpad, and seem a gnome problem. You can still mount the drive using the command line.

---

### Post by Gourgi on 2009-01-14
you can use ntfs-config ;)

---

### Post by Bucky Ball on 2009-01-14
You can install ntfs-3g from Synaptic Package Manager. Should fix things.

---

### Post by kurros on 2009-01-14
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443)

For whatever reason */usr/share/hal/fdi/policy/10osvendor/20-ntfs-3g-policy.fdi* in the current *ntfs-3g* package is only matching against storage.hotpluggable = true (so a removable HDD, etc works but not a local one).

Removing the <match key="@block.storage_device:storage.hotpluggable" bool="true"> and </match> block around the merge/append tags fixes your issue.

Edit: you will have to run *sudo /etc/init.d/hal restart* to reload the policy files without a reboot

---

### Post by minisori on 2009-01-21
Thx that fixed it :D

---

