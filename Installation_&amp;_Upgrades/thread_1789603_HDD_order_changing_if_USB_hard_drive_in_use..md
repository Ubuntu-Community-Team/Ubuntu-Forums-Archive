---
title: "HDD order changing if USB hard drive in use."
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by pjd99 on 2011-06-24
Apologies if this has been posted before but every search I try returns hits on "failing to boot from a USB device".

I recently dist-upgraded to 11.04 from 10.10. Never had any trouble with this in Maverick so trying to figure why it has started happening in Natty.

During normal operation, my main hard disk is sda, /backup is sdb. If I reboot with an external drive plugged in and turned on, the external becomes sda, sda becomes sdb and sdb becomes sdc. 

When this happens it usually tells me it cant find /home and to hit m to drop to the maintenance shell. When it first happened my reaction was WTF? but then checked out fstab and mtab to see what was going on and saw that the reordering had occurred. 

Anyone else had something like this? Removing the external and restarting fixes the problem, but IMO it shouldn't be occurring in the first place (same goes for Natty's bluetooth regression - I mean, I had these problems back in 8.10, but they had been fixed - until 11.04...)

I'll try to reproduce to get a more definite picture, (at work at the moment so will kill it again when I get home) as i'm sure / mounts but /home doesn't and they're on the same device.

---

### Post by vanadium on 2011-06-24
The possibility of change of device name in modern hardware is the reason that today, UUIDs are used to reference partitions. Replace the device names in your /etc/fstab by UUID references.

---

### Post by jocko on 2011-06-24
> **pjd99 said:**
> Apologies if this has been posted before but every search I try returns hits on "failing to boot from a USB device".

I recently dist-upgraded to 11.04 from 10.10. Never had any trouble with this in Maverick so trying to figure why it has started happening in Natty.

During normal operation, my main hard disk is sda, /backup is sdb. If I reboot with an external drive plugged in and turned on, the external becomes sda, sda becomes sdb and sdb becomes sdc. 

When this happens it usually tells me it cant find /home and to hit m to drop to the maintenance shell. When it first happened my reaction was WTF? but then checked out fstab and mtab to see what was going on and saw that the reordering had occurred. 

Anyone else had something like this? Removing the external and restarting fixes the problem, but IMO it shouldn't be occurring in the first place (same goes for Natty's bluetooth regression - I mean, I had these problems back in 8.10, but they had been fixed - until 11.04...)

I'll try to reproduce to get a more definite picture, (at work at the moment so will kill it again when I get home) as i'm sure / mounts but /home doesn't and they're on the same device.

Ubuntu has used UUID's instead of device nodes (/dev/sdXY) for years for this exact reason. Unless the device nodes are specifically hard-coded into the boot sequence, they often change between boots, particularly (in my experience) if you have several disk controllers on your motherboard, or if you sometimes boot with external disks connected.
See my [old post from 2007]("http://ubuntuforums.org/showpost.php?p=3397251&postcount=3") or [another from 2008]("http://ubuntuforums.org/showpost.php?p=4992187&postcount=3") for how to solve it...

---

### Post by pjd99 on 2011-06-24
> **vanadium said:**
> The possibility of change of device name in modern hardware is the reason that today, UUIDs are used to reference partitions. Replace the device names in your /etc/fstab by UUID references.

This. I just checked fstab and for some reason / and /home weren't referenced by UUID but all other partitions were... I assume it's because when I installed 10.10, I only reformatted / and /home, while the others were resized to make way for a windows 7 partition.

Cheers for the quick replies (though if i actually spent 10 minutes looking at my system config i'd have sorted it out). Haven't played with the internals of Linux for a few years and remember being thoroughly confused the first time I saw a UUID after the switch...

---

### Post by vanadium on 2011-06-24
It is actually easy to update. Learn about the UUID of your partitions from the command:

```

sudo blkid

```
You can just copy the relevant 'UUID="<number>" part from the terminal, and paste it over the device name in your /etc/fstab file.

For example, an output such as
```

$ sudo blkid
[sudo] password for vanadium: 
/dev/sda1: UUID="521cd407-2a4d-4ea8-a8e6-703d2370f2d0" TYPE="ext4" 

```
would lead you to update the corresponding line in /etc/fstab from
```

/dev/sda1 /               ext4    errors=remount-ro 0       1

```

changes to

```

UUID=521cd407-2a4d-4ea8-a8e6-703d2370f2d0 /               ext4    errors=remount-ro 0       1

```

---

### Post by pjd99 on 2011-06-24
> **vanadium said:**
> It is actually easy to update. Learn about the UUID of your partitions from the command:

```

sudo blkid

```You can just copy the relevant 'UUID="<number>" part from the terminal, and paste it over the device name in your /etc/fstab file.

For example, an output such as
```

$ sudo blkid
[sudo] password for vanadium: 
/dev/sda1: UUID="521cd407-2a4d-4ea8-a8e6-703d2370f2d0" TYPE="ext4" 

```would lead you to update the corresponding line in /etc/fstab from
```

/dev/sda1 /               ext4    errors=remount-ro 0       1

```changes to

```

UUID=521cd407-2a4d-4ea8-a8e6-703d2370f2d0 /               ext4    errors=remount-ro 0       1

```

Thanks. 

I remember hating UUID's at first, I had a server where i'd switch out a hard drive on one channel that I wanted mounted in the same location, and it really annoyed me.

---

### Post by Paddy Landau on 2011-06-24
A way to get around UUID's is to use labels.

I label every partition (USB sticks and external USB drives included) with a unique label.  An extract from my fstab looks like this:

```
LABEL=paddylinux  /      ext4  errors=remount-ro  0  1
LABEL=paddyhome   /home  ext4  defaults           0  2
LABEL=linuxswap   none   swap  sw                 0  0
```It's easier to understand, and will work if my HDD breaks and I restore a clone.

---

