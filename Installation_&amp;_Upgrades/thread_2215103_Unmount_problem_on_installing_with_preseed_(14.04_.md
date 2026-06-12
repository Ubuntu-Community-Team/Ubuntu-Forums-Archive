---
title: "Unmount problem on installing with preseed (14.04 b2)"
date: 2014-04-04
forum: Installation &amp; Upgrades
---

### Post by Takashi Asari on 2014-04-04
Hi,

I'm trying to auto-install Ubuntu Server 14.04 beta2 using Preseed.
My installation targets have already ext4-formatted /dev/vdb's, but I'd like to ignore it and just install Ubuntu into /dev/vda.
I've read through [the manual]("https://help.ubuntu.com/14.04/installation-guide/amd64/apb.html") and [the example]("https://help.ubuntu.com/14.04/installation-guide/example-preseed.txt"), and wrote preseed.cfg like:

```
d-i partman-auto/disk string /dev/vda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
d-i partman-lvm/confirm_nooverwrite boolean true
```

Created a preseeded bootable ISO image, boot with it, and I got a message like following:

> [!!] Partition disks

The installer has detected that the following disks have mounted partitions:

/dev/vdb

Do you want the installer to try to unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there.

Unmount partitions that are in use?

<Go Back> <Yes> <No>

Does anyone know how can I avoid this message? I tried to take a look at debug log, which said that:

> --> GET partman/filter_mounted
<-- 0 true
--> SUBST partman/unmount_active DISKS /dev/vdb
Adding [DISKS] -> /dev/vdb
<-- 0
--> FSET partman/unmount_active seen false
<-- 0 false
--> INPUT critical partman/unmount_active
<-- 0 question will be asked
--> GO

I thought that setting "*d-i partman/unmount_active boolean true*" should be enough, but no effect.

I'm not in haste, for the number of my installation targets is just <=10 for now and I can manually select <Yes> and press Enter.
But automation is beautiful. Any help will be appreciated,  thanks in advance!

---

### Post by directhex2 on 2014-04-23
If you drop to a console & check, has one of your partitions on /dev/vda been mounted to /media?

I'm trying to determine the culprit for this.

---

### Post by directhex2 on 2014-04-23
I've tracked down the problem to a change in debian-installer-utils 1.98

---

### Post by Stefan_Felkel on 2014-05-06
I invested some time into the same problem. For some reason, /dev/sda1 is mounted on /media.
As described above, *"d-i partman/unmount_active boolean true"* had no effect. 
The dialog doesn't appear with preseeing "d-i partman/filter_mounted boolean false", but that didn't help either, because the repartitioning I'm performing afterwards during the install is only successful when all partitons are not mounted.

Finally I was successful by using a simple "umount /media" as early command. 

```
d-i preseed/early_command string umount /media
```

Although it doesn't clarify the problem's root, it solved my situation - the dialog didn't appear again due to the partition wasn't mounted at this time.

---

### Post by bbach on 2014-05-28
> **Stefan_Felkel said:**
> I invested some time into the same problem. For some reason, /dev/sda1 is mounted on /media.
As described above, *"d-i partman/unmount_active boolean true"* had no effect. 
The dialog doesn't appear with preseeing "d-i partman/filter_mounted boolean false", but that didn't help either, because the repartitioning I'm performing afterwards during the install is only successful when all partitons are not mounted.


Stefan, Thanks for this workaround!

The problem with setting: 

```
d-i partman/unmount_active boolean true
```
according to [https://wiki.debian.org/DebianInstaller/Preseed](https://wiki.debian.org/DebianInstaller/Preseed) is:
> [FONT=inherit]
If your preseed value is being ignored and whilst using DEBCONF_DEBUG=5 to watch the debconf output you see "FSET blah false" it just means that a piece of code really wants that question to be seen, and such questions are not normally preseedable - the only way to avoid them is to avoid the situation that gives rise to that question being asked.[/FONT]
[FONT=inherit]
Not sure why the old drive is getting mounted anyway.  I guess it is mounted to look for old OSs and is not properly unmounted.  -- Bud[/FONT]
[FONT=inherit]
[/FONT]

---

### Post by Takashi Asari on 2014-09-17
> **directhex2 said:**
> If you drop to a console & check, has one of your partitions on /dev/vda been mounted to /media?


Yes, in my case, /dev/vdb was mounted on /media, too, as stefan wrote.


> **Stefan_Felkel said:**
> Finally I was successful by using a simple "umount /media" as early command. 

```
d-i preseed/early_command string umount /media
```

Although it doesn't clarify the problem's root, it solved my situation - the dialog didn't appear again due to the partition wasn't mounted at this time.

Thank you very much for your effort and the simple workaround! It worked like a charm.

---

### Post by Jacob_J._Walker on 2014-10-19
I'm new to the forums, so I hope I'm not breaking etiquette, but I have the same problem of trying to preseed a Lubuntu install, where I just want to wipe the drive automatically and use the whole drive, and if there was already Lubuntu on the system, it gives me this warning.  I have tried the early_command fix to unmount /media but it didn't work for me.  I thought maybe I could do an early_command that would just wipe the disk like a dd or something, so that there would be nothing to mount :-)  But so far that hasn't worked either.  If this should go in a new post, let me know.

---

### Post by makuk662 on 2015-06-29
This issue has been reported as a bug [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1347726](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1347726)

---

