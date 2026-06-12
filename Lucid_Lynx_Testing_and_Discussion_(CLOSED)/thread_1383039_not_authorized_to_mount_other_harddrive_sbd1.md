---
title: "not authorized to mount other harddrive sbd1"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-01-16
as the title says and can't find how to authorize myself. i'm the only user on this computer.  what do i check first and how do i proceed?

just upgraded to alpha 2 today, karmic was working fine.

---

### Post by seeker5528 on 2010-01-16
Don't know what changed with the mounting of detected partitions, I had two that were being mounted automatically, then they stopped being mounted automatically, but I could still go to places and click on them to access them.

My solution was to use mountmanager to set them up. Once it's installed it should show on the Gnome menu at 'System --> Administration --> MountManager'.

You may have to create the mountpoint before hand:

```
sudo mkdir /media/sdb1
```

: or some noise like that. 

Later, Seeker

---

### Post by Ibidem on 2010-01-16
Nautilus or terminal?
User Accounts Admin (command users-admin) if it's privilege.
If you're using USB, install usbmount (would automount as /media/usb0).
Are you using sudo?
That's probably sdb1, I guess
Ibidem

---

### Post by mc4man on 2010-01-16
The mounting of internal disks (partitions) that **aren't** automounted at boot (fstab entry) was fixed to no longer require the admin user to authenticate

As seen [here]("https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/465054") 

That continues to work as expected in lucid ( though don't believe has been applied to karmic where bug was filed, though can be  manually added

Does your sdb1 have an fstab entry (automount at boot

---

### Post by buzzmandt on 2010-01-16
seems there is no entry in fstab or mtab, how do i correct this?
oh wait, just thought of this, the hard drive is in ntfs
here is ntfs aptitude search for what is installed.
```
buzzmandt@buzzmain:~$ aptitude search ntfs
p   libntfs-3g-dev                  - ntfs-3g filesystem in userspace (FUSE) lib
i   libntfs-3g54                    - ntfs-3g filesystem in userspace (FUSE) lib
p   libntfs-dev                     - library that provides common NTFS access f
p   libntfs-gnomevfs                - NTFS GNOME virtual filesystem module      
i A libntfs10                       - library that provides common NTFS access f
i   ntfs-3g                         - read-write NTFS driver for FUSE           
p   ntfs-config                     - Enable/disable write support for any NTFS 
p   ntfsdoc                         - documentation about NTFS partitions format
i A ntfsprogs                       - tools for doing neat things in NTFS partit
p   scrounge-ntfs                   - Data recovery program for NTFS filesystems
buzzmandt@buzzmain:~$ 

```


```
buzzmandt@buzzmain:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2a3df03f-4434-4a63-9088-1ae43d56f095 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ad8b20ab-30d0-4079-bd85-a67b680b6960 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
buzzmandt@buzzmain:~$ 

```
```
buzzmandt@buzzmain:~$ cat /etc/mtab
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/buzzmandt/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=buzzmandt 0 0
buzzmandt@buzzmain:~$ 

```

---

### Post by MacUntu on 2010-01-16
Did this happen in a fail-safe graphics mode session? Maybe this is connected: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/508379](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/508379)

I guess if you see "active = FALSE" when running 'ck-list-sessions' that's your problem.

---

### Post by garvinrick4 on 2010-01-16
Can you see sdb1 and mount it in a Live CD

---

### Post by buzzmandt on 2010-01-16
> **garvinrick4 said:**
> Can you see sdb1 and mount it in a Live CD

yes, ran live mint and put the music from it onto thumb drive. reformatted it to ext3 and named it 'secondary'

now, back in ubuntu lynx, from 'places', 'computer' i see the drive and can open it, but trying to open anything in it such as folder 'lost and found' it says i don't have permission.  trying to paste anything to the drive it says i don't have permission.  i tried 'sudo nautilus' and opened the drive and i can open the 'lost and found' folder just fine.  

how do i set permissions on drives?

---

### Post by PaulInBHC on 2010-01-16
Post 7 helped me, don't know if it applies to your problem.

[http://ubuntuforums.org/showthread.php?t=1373546](http://ubuntuforums.org/showthread.php?t=1373546)

---

### Post by VMC on 2010-01-16
> **buzzmandt said:**
> as the title says and can't find how to authorize myself. i'm the only user on this computer.  what do i check first and how do i proceed?

just upgraded to alpha 2 today, karmic was working fine.

How did you upgrade? Using a sudo aptitude or apt-get? Did you check permissions on any folder on the sbd1 HD? Are they root access only?

---

### Post by buzzmandt on 2010-01-17
> **VMC said:**
> How did you upgrade? Using a sudo aptitude or apt-get? Did you check permissions on any folder on the sbd1 HD? Are they root access only?

sudo update-manager -d

there is only one folder on the drive, it is called 'lost and found' it is root access only. when i ran root nautilus i could access it. i can't make any more folders it gives me permission denied.  i could run root nautilus and make folders then change the permissions to me but that kinda takes away from having a fully functional and easy to access extra hard drive.

---

### Post by SalvoMaltese on 2010-01-17
I have this problem too.

Fresh install of Kubuntu lucid, I can mount NTFS partitions, i can NOT mount ext* partitions. (ext2 boot, ext4 karmic partition).

If I run "sudo dolphin" I can mount any partition without problems.

---

### Post by VMC on 2010-01-17
> **buzzmandt said:**
> sudo update-manager -d

there is only one folder on the drive, it is called 'lost and found' it is root access only. when i ran root nautilus i could access it. i can't make any more folders it gives me permission denied.  i could run root nautilus and make folders then change the permissions to me but that kinda takes away from having a fully functional and easy to access extra hard drive.

After plugging in one of my usb flash drive, here is my permissions:
/dev/sdb1 on /media/MUSIC type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

From a terminal output 'mount', the drive in question will show its permissions.

---

### Post by ranch hand on 2010-01-17
> **buzzmandt said:**
> sudo update-manager -d

there is only one folder on the drive, it is called 'lost and found' it is root access only. when i ran root nautilus i could access it. i can't make any more folders it gives me permission denied.  i could run root nautilus and make folders then change the permissions to me but that kinda takes away from having a fully functional and easy to access extra hard drive.
You are not trying to create another folder within "lost and found" are you?

---

### Post by buzzmandt on 2010-01-17
> **ranch hand said:**
> You are not trying to create another folder within "lost and found" are you?
lol, no.

---

### Post by MacUntu on 2010-01-17
Does this still happen after the latest updates?

---

### Post by mc4man on 2010-01-17
When it was a ntfs partition you should have had write perms. automatically if you were in the plugdev group ( which yiou should have been

Now I gather it's an ext3 so you need to chown it 
I'm sure there are various ways, what i do, noting I never automount other partitions at boot ( no fstab entry
( whether they are auto mounted or not you still have to click on something to open, I'd just as soon click on the drive in places than an icon on the desktop.
Plus I can unmount if desired without being root.

Anyway an ex.
just made an ext3 partition named data on /dev/sdb5 (the volume label is irrelevant here

With it unmounted, 1 at a time, blue is specific to me
```
sudo mkdir /media/fix
sudo mount /dev/sd[COLOR="Blue"]b5[/COLOR] /media/fix
sudo chown [COLOR="Blue"]doug[/COLOR]:[COLOR="Blue"]doug[/COLOR] /media/fix
sudo umount /dev/sd[COLOR="Blue"]b5[/COLOR] /media/fix
sudo rmdir /media/fix


```

Now I can mount 'data' from places (no authenication), write to it, and unmount if desired, again with no auth.

---

