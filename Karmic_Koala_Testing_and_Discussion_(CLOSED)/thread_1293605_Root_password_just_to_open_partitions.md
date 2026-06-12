---
title: "Root password just to open partitions"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c-m on 2009-10-17
Why is it that in karmic every time i want to open one of my other partitions I have to type in my root password?

Here is my fstab:

```
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=ecbd4df3-fa31-48d3-89ff-8011d108c8db /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=4e014466-faee-408f-9fe5-b924303667bc /home           reiserfs defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by ajgreeny on 2009-10-17
Do you mean root password or your user password, and what are your "other partitions" and how are you mounting them?

Your fstab only shows the root and /home partitions on your disk, so you will need to either add another line, or lines, to mount other partitions at boot time, the contents of which will depend on the file systems they are formated to.

Can you show us the output of ```
sudo fdisk -l
``` in terminal, and tell us which of those partitions you want to mount.

---

### Post by ranch hand on 2009-10-17
You really ought to have a swap partition too.  If you do it is not in your fstab and therefore won't be used.  I would be more worried about that.

---

### Post by c-m on 2009-10-17
I don't bother with a swap partition, as far as i'm concerned its useless if you have 4gb or memory anyway.

I mean my root password.

I am clicking on the desktop icons to mount my other partitions. I really shouldn't have to manually edit the partition table, I thought that was just in the old days.

I haven't manually added partitions for 4 years now. Each installation has just picked them up and placed icons on the desktop. Mint does this on my laptop.

---

### Post by Rinzwind on 2009-10-17
Maybe a stupid question but ...
Did you change the owner and group permissions?

---

### Post by ajgreeny on 2009-10-17
And presumably you did make a root password after installing?  Ubuntu has no active root account, it is disabled by default, only user accounts, at least one of whom will be a member of the admin group and able to carry out root activities using sudo.  I am therefore baffled by your situation.

Try using the panel applet Disk-Mounter to see if that helps.

---

### Post by c-m on 2009-10-18
Hi.

yes i of course i have a root password. Its no big deal i can manually add the partitions to the table its just that i have never had to before.

This was a clean install but still using my old home directory from my previous jaunty install. For some reason in Karmic all the drives have weird names like ulc874bgfb9447b9gf bizarre.

---

### Post by ajgreeny on 2009-10-18
> Hi.

yes i of course i have a root password. Its no big deal i can manually add the partitions to the table its just that i have never had to before.
You are unusual having a root password.  Most people do not use a root account but use the sudo way as I noted before.
> This was a clean install but still using my old home directory from my previous jaunty install. For some reason in Karmic all the drives have weird names like ulc874bgfb9447b9gf bizarre.
I assume therefore tha karmic is using the UUIDs to refer to the partitions instead of just Disk, Disk1, Disk2, etc etc, or the Label you may have given it.  All partitions have a UUID, and it can be used in place of /dev/sdx# in many situations, as can the Label.  Karmic must be using UUIDs.  Not too bizarre

---

