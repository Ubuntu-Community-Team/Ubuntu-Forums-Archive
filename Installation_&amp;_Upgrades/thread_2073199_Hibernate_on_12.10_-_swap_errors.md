---
title: "Hibernate on 12.10 - swap errors"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by pastim on 2012-10-19
I upgraded to 12.10 yesterday (Yes - I am an IT masochist).  The main problem I have is that hibernation does not work.  It worked fine on 12.04.

The error I get is a load of messages like the following

```

132.nnnnnn write-error on swap-device 8.0:mmmmmmmmm

```

where n and m are various increasing digits.

I have checked the swap partition is active.  I even resized it (using a live DVD and GParted) to get a bit more space than memory to see if that was the problem, and made sure the partition is mounted again in /etc/fstab.  No change.  

With my very limited knowledge it rather looks as if the disks, or the drivers, are being turned off before hibernation has completed.

The reason I use hibernation is that suspension doesn't work on my 5 year old desktop.  I also like the whole thing to be powered off.

Has anyone else got a similar problem.  Is it a new 'feature'?

---

### Post by plucky on 2012-10-19
> I have checked the swap partition is active. I even resized it (using a live DVD and GParted) to get a bit more space than memory to see if that was the problem, and made sure the partition is mounted again in /etc/fstab. No change. 


If the resize changed the UUID of the partition,you also need to update the value in /etc/initramfs-tools/conf.d/resume.

Open a terminal and post output for ```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```


Good Luck

---

### Post by pastim on 2012-10-19
> **plucky said:**
> If the resize changed the UUID of the partition,you also need to update the value in /etc/initramfs-tools/conf.d/resume.

Open a terminal and post output for ```
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```Good Luck
When the problem first occurred I hadn't changed the swap partition at all.

For unrelated reasons I later decided to do a clean 12.10 installation, rather than an upgrade.

I still have the same problem.  The UUIDs, Resume and fstab are all in line.

```

/dev/sda1: UUID="DEEC967BEC964E21" TYPE="ntfs" 
/dev/sda2: LABEL="Data1" UUID="CA1C8D6F1C8D56FB" TYPE="ntfs" 
/dev/sda5: LABEL="Data2" UUID="9C64F46C64F44A92" TYPE="ntfs" 
/dev/sda6: UUID="cbb73306-eebf-4e52-92e7-ecf850c35fcb" TYPE="swap" 
/dev/sda7: UUID="ab96c116-69bd-4fbc-961c-9285ba96ca24" TYPE="ext4" 
/dev/sdb2: LABEL="Media" UUID="6AD0129FD0127195" TYPE="ntfs" 

```And

```

RESUME=UUID=cbb73306-eebf-4e52-92e7-ecf850c35fcb
[code]

And

[code]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=ab96c116-69bd-4fbc-961c-9285ba96ca24 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=cbb73306-eebf-4e52-92e7-ecf850c35fcb none            swap    sw              0       0


```Although the hibernation didn't fully work (the monitor switched off but not the system) when rebooting manually (using the PC's restart button) the session did resume after a fashion.  This is a little more of a hint that there is a timing problem with hibernation in 12.10.

---

### Post by funicorn on 2012-10-19
paste the log in /var/log/pm-hibernate

---

### Post by pastim on 2012-10-19
> **funicorn said:**
> paste the log in /var/log/pm-hibernate

There isn't one.

---

