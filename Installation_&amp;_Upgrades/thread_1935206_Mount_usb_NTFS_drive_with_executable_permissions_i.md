---
title: "Mount usb NTFS drive with executable permissions in Natty"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by agestrada on 2012-03-03
Hi, I upgraded from Lucid and now I can't run scripts and executables from my external NTFS drive anymore. I've read the forums and for some reason they changed the default behaviour. For portability reasons, using fstab to mount the drive is not an option. 

How can I change the automount daemon or remount the drive with executable permissions?.
I've tried without success:
```

sudo mount /media/namehere -o remount,exec

```
Thanks,

---

### Post by agestrada on 2012-03-10
Bump. Any idea?

---

### Post by sudodus on 2012-03-10
If you have read access you can run

```
bash /path/program
```
instead of
```
/path/program
```

But back to your problem: you upgrade to what version and flavour, [KLX]ubuntu 11.04? If you mount it by 'going to it' with the file browser, what happens?

---

### Post by Morbius1 on 2012-03-10
Your syntax is a little discombobulated.

1st: Unmount ( but do not remove ) the external drive.

2nd: To mount it:
```
sudo mount /dev/sdd1 /home/username/Temp -o umask=000
```** Replace /dev/sdd1 with the real device name. If you don't know what it is run:
```
sudo blkid
```** Make sure that /home/username/Temp exists.
** And don't forget to unmount it before removing it:
```
sudo umount /home/username/Temp.
```

---

### Post by agestrada on 2012-03-11
Thanks for your answers.

@sudodus: I upgraded to Ubuntu 11.04 Natty, no specific flavour. I'm considering trying Kubuntu but that's another story. The bash command works OK for scripts but not for binaries. If I use the browser the drive is mounted with r/w permissions but I can't execute any script or binary.

@Morbius1: Yes, at the end I couldn't find a way to change the automounter for USB and the best option is to umount/mount the drive. This seems to work just fine:

```

sudo umount /path/toMount
sudo mount -t ntfs-3g -L <DriveLabel> /path/toMount

```

---

### Post by sudodus on 2012-03-11
You need execute permission to run an executable file, so you need to mount the ntfs drive with execute permission for that, it is not enough with read/write permissions. An alternative is not to keep linux executables on a file system, that belongs to Windows. Instead you can have an ext file system (for example ext3 on a separate partition on your external drive).

See ```
man mount
```

```
Mount options for ntfs
       iocharset=name
              Character set to use when returning file  names.   Unlike  VFAT,
              NTFS  suppresses  names  that  contain unconvertible characters.
              Deprecated.

       nls=name
              New name for the option earlier called iocharset.

       utf8   Use UTF-8 for converting file names.

       uni_xlate={0|1|2}
              For 0 (or `no' or `false'), do  not  use  escape  sequences  for
              unknown  Unicode  characters.   For 1 (or `yes' or `true') or 2,
              use vfat-style 4-byte escape sequences starting with ":". Here 2
              give  a  little-endian  encoding  and  1 a byteswapped bigendian
              encoding.

       posix=[0|1]
              If enabled (posix=1), the filesystem distinguishes between upper
              and  lower case. The 8.3 alias names are presented as hard links
              instead of being suppressed. This option is obsolete.

       uid=value, gid=value and umask=value
              Set the file permission on the filesystem.  The umask  value  is
              given in octal.  By default, the files are owned by root and not
              readable by somebody else.

```

---

### Post by agestrada on 2012-03-12
Yes, that's true. Actually, I use the appropriate mask to mount an internal NTFS partition with executable permissions using fstab. As I said, using 
```

sudo umount /path/toMount 
sudo mount -t ntfs-3g -L <DriveLabel> /path/toMount

```works for the external USB drive. I don't understand why in this case it mounts it with executable permissions as I don't see any mask of flag. But it works for me in my two machines so it's enough.

---

### Post by agestrada on 2012-04-09
A better solution is to create a udev rule as explained in this post:
[http://ubuntuforums.org/showpost.php?p=11636662&postcount=1](http://ubuntuforums.org/showpost.php?p=11636662&postcount=1)

Create a file in /etc/udev/99-usb-disks.rules and enter
```

     ENV{ID_FS_TYPE}=="ntfs", ENV{ID_FS_TYPE}="ntfs-3g" 

```unplug usb disk
replug usb disk
now all files should have 777 permissions

---

