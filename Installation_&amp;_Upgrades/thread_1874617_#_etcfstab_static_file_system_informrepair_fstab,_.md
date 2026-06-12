---
title: "# /etc/fstab: static file system informrepair fstab, and whatever else, so I can boot"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by sidewalkcynic on 2011-11-03
I installed 11.10 with a new partition table. My concept is to have the most active file systems near the center of the physical hard drive (home,var,tmp,swap); and the boot and root at the beginning of the HDD.

I have 5 large partitions dedicated to storing user files, and I adjust thier position and size to manuever the active partitions to the center of the HDD; and at installation I disgnate their mount points because I want them to be mounted at boot:

/media/A
/media/B
/media/C
/media/D
/media/E

I have names and size parameters for for the 5 users' partitions, and I want the partition names to be in a specific order in the Nautilus file browser, but because I did not know the order that Ubuntu would mount the partitions, I gave them the letter designations and would adjust the partitions' size and names using Gparted when I get the desktop up and going.

So, what happened is that the partions mounted in an order that shows up in Nautlus as:

/media/C
/media/D
/media/E
/media/A
/media/B

C,D, and E are at the end of the HDD, so, instead of resizing them, I just deleted and recreated them to the sizes that I needed them to be. Since, A and B are toward the center of the HDD, I took the time to resize them  with Gparted.

The problem, seems to me, to be that since I removed the mount points, or changed the UUID of C,D, and E, when I deleted them Ubuntu won't boot.

because I am in USBLive mode, I don't know how to get the blkid code, but here is the fstab and mstab.

fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=92139ec4-4b27-4b5d-9602-2cbafc1e48f7 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c326c3f9-ef96-4c1d-bf71-e622e5def5d5 /boot           ext4    defaults        0       2
# /home was on /dev/sda8 during installation
UUID=662489c5-863d-41ac-9fc4-9f3c069a43e6 /home           ext4    defaults        0       2
# /media/A was on /dev/sda5 during installation
UUID=f41bc4dc-892e-4ba1-952a-dc93e9d7cabf /media/A        ext4    defaults        0       2
# /media/B was on /dev/sda6 during installation
UUID=c8ca1423-ef83-4f20-a7ca-f7f2ac6cc429 /media/B        ext4    defaults        0       2
# /media/C was on /dev/sda13 during installation
UUID=d504c021-6c34-4b69-927d-ba1d1efa15d1 /media/C        ext4    defaults        0       2
# /media/D was on /dev/sda14 during installation
UUID=1f78e55f-da39-48ee-b9d8-355d70ed415c /media/D        ext4    defaults        0       2
# /media/E was on /dev/sda15 during installation
UUID=4ccadc18-76ae-4def-8dd2-3d486a392b0a /media/E        ext4    defaults        0       2
# /media/TIME was on /dev/mmcblk0p1 during installation
UUID=3cb310ee-f5fe-4fab-9e75-81a98d680bb1 /media/TIME     ext2    defaults        0       2
# /opt was on /dev/sda12 during installation
UUID=a697d062-1aa7-4456-b6c9-74d654b562dd /opt            ext4    defaults        0       2
# /tmp was on /dev/sda9 during installation
UUID=237bc714-885e-4aa9-a0e4-5d5f6937bd48 /tmp            ext4    defaults        0       2
# /usr was on /dev/sda10 during installation
UUID=ec86160e-661e-4ff6-b338-16bf7bcee095 /usr            ext4    defaults        0       2
# /usr/local was on /dev/sda11 during installation
UUID=8dedd26a-5e31-434b-a83d-00f0e161892c /usr/local      ext4    defaults        0       2
# /var was on /dev/sda3 during installation
UUID=280a8e1a-056b-4a27-908c-34d242690e15 /var            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=3ed15645-08c4-475d-b1d8-f115d5876a58 none            swap    sw              0       0
```
```
/dev/sda2 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda9 /tmp ext4 rw 0 0
/dev/sda1 /boot ext4 rw 0 0
/dev/sda8 /home ext4 rw 0 0
/dev/sda5 /media/A ext4 rw 0 0
/dev/sda6 /media/B ext4 rw 0 0
/dev/sda12 /opt ext4 rw 0 0
/dev/sda10 /usr ext4 rw 0 0
/dev/sda11 /usr/local ext4 rw 0 0
/dev/sda3 /var ext4 rw 0 0
/dev/mmcblk0p1 /media/TIME ext2 rw 0 0
```
I would like to make the mount points the proper designations that I have for them, but not that big of a deal since the labelling process of Gparted has handled it for the Nautilus sidepane:

/media/C     - NATURE
/media/D     - TECHs
/media/E     - HEALTH
/media/A     - SOCIETY
/media/B     - IDEOs

---

### Post by CharlesA on 2011-11-03
Just run this to get the correct UUID:

```
sudo blkid -c /dev/null
```

---

### Post by sidewalkcynic on 2011-11-03
```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
sudo: can't stat /etc/sudoers: Input/output error
sudo: no valid sudoers sources found, quitting
ubuntu@ubuntu:~$ 

```

This is probably because I am in USBLive mode???

---

### Post by CharlesA on 2011-11-03
It shouldn't matter since a liveUSB is the same as a liveCD.

What does this return?

```
cat /etc/sudoers
```

---

### Post by sidewalkcynic on 2011-11-03
```
ubuntu@ubuntu:~$ cat /etc/sudoers
cat: /etc/sudoers: Input/output error
ubuntu@ubuntu:~$ 

```

---

### Post by sidewalkcynic on 2011-11-03
What might have been the correction that I needed to do before I shutdown/reboot after having made the adjustments in Gparted?

Because, I guess, my best bet is to reinstall knowing the correct mount order. . .

---

### Post by CharlesA on 2011-11-03
> **sidewalkcynic said:**
> ```
ubuntu@ubuntu:~$ cat /etc/sudoers
cat: /etc/sudoers: Input/output error
ubuntu@ubuntu:~$ 

```

Hrm, thought my reply went thru. I said that you could try booting off a plain livecd and see what happens, since a liveusb and livecd are pretty much the same thing.

> **sidewalkcynic said:**
> What might have been the correction that I needed to do before I shutdown/reboot after having made the adjustments in Gparted?

I would have removed all the entries in fstab besides / and swap, but since you have your file system spread all over the place, I'm not quite sure how that would work.

It would probably be easier to just reinstall and make sure everything is ok that way. You could try editing fstab with the new UUID value, but you'd need to run that with sudo and that's not working for some reason.

---

### Post by sidewalkcynic on 2011-11-03
Well, I am in the system through root repair boot, or what ever it is. It allowed me to skip the mounting of C,D, and E.

From the blkid I got the UUID numbers and cut and pasted them to the corresponding places on the fstab.

Does that do it, or do I need anything else?

---

### Post by sidewalkcynic on 2011-11-03
Well, heck yeah. That does it - thanks for your help.

---

### Post by CharlesA on 2011-11-03
Awesome, glad you got it working. :)

---

