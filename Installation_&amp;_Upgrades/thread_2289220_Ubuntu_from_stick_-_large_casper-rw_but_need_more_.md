---
title: "Ubuntu from stick - large casper-rw but need more space for system?"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by nick208 on 2015-08-02
Running Ubuntu desktop (15.04) from a** stick **and am quite happy with it. But as I install new programs* I am running out of space*. I have about 9gb on **casper-rw**. Can I change so that this is used for the system? 
*Bit of a noob*
Thanks

---

### Post by sudodus on 2015-08-02
You can use a casper-rw file or a casper-rw partition. If the file is in a FAT32 file system the size is limited to 4 GB. I suggest that you use a casper-rw partition. It should have a linux file system, for example ext2. You can use ext4 too, which is better, but then you should turn of journaling to avoid excessive wear.

Please tell me more about your system on the stick, in plain words, and also, please

- maximize a terminal window and

- run the following command and paste the output into a reply window (and put it within [noparse]```
tags
```[/noparse].

```
sudo lsblk -fm
```

In the following links and links from them it is described how to use casper-rw partitions for persistence

[One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot](http://ubuntuforums.org/showthread.php?t=2259682)

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by nick208 on 2015-08-03
**Thank you** sudodus, this is the output of

```
sudo lsblk -fm:

&#9500;&#9472;sda1 ntfs     Recovery A6FE9AB8FE9A7FEB                                &#9500;&#9472;sda1  400M root  disk  brw-rw----
&#9500;&#9472;sda2 vfat     ESP      F49A-D37B                                       &#9500;&#9472;sda2  100M root  disk  brw-rw----
&#9500;&#9472;sda3                                                                   &#9500;&#9472;sda3  128M root  disk  brw-rw----
&#9500;&#9472;sda4 ntfs     Acer     B8CC9D83CC9D3D16                                &#9500;&#9472;sda4 58.6G root  disk  brw-rw----
&#9492;&#9472;sda5 ntfs              F6B649C3B64984D9                                &#9492;&#9472;sda5  450M root  disk  brw-rw----
sdb                                                                      sdb    14.5G root  disk  brw-rw----
&#9500;&#9472;sdb1 vfat              C72D-FE03                            /cdrom     &#9500;&#9472;sdb1  4.9G root  disk  brw-rw----
&#9492;&#9472;sdb2 ext4     casper-rw
                         16d08e72-9e7f-4717-a9b2-c2781693eef7 /media/ubu &#9492;&#9472;sdb2  9.6G root  disk  brw-rw----
loop0  squashfs                                               /rofs      loop0     1G root  disk  brw-rw----
loop1  ext3              2ef7727d-a7b4-46f2-b3b8-547e23c03bcf /media/ubu loop1     1G root  disk  brw-rw----
```

I have a 16gb usb3 stick that I plug into a acer w700 tablet. I created the usb stick on anoter computer running ubuntu, but cant remember all the details at the moment (followed instructions from some ubuntu-page).
If I try to move something to casper-rw I get the message "*The folder &#8220;xx&#8221; cannot be copied because you do not have permissions to create it in the destination*."

---

### Post by sudodus on 2015-08-03
There is a configuration file, where you should have the boot option **persistent**, and that configuration file is different for different tools. It would help if you tell us which tool you used to create the USB boot drive. ***Unetbootin***, the Ubuntu ***Startup Disk Creator***, some other tool, or did you do it manually with several command lines in a terminal window?

Anyway, the casper-rw partition was mounted read-only or with root as owner. Please run a few more commands and post the output to get a few more details.

```
df
sudo ls -l /media
cat /etc/mtab
```

and please tell us which tool you used to create the USB boot drive :-)

-o-

I think that you will soon be able to

1. write files to the casper-rw partition (but it is probably better to avoid writing directly to it)

2. use the casper-rw partiiton for persistence (it will be there behind the curtain as an overlay file system).

---

### Post by nick208 on 2015-08-03
I think I may have used method 0 on [this link]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), so that would be usb-creator. But cant swear on it Bit of a jungle navigating through these things and I tend not to memorize path chosen :). Option 2 sounds great.
```

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1916740       0   1916740   0% /dev
tmpfs             385744   10880    374864   3% /run
/dev/sdb1        5130440 2171112   2959328  43% /cdrom
/dev/loop0       1075968 1075968         0 100% /rofs
/cow              999320  782096    164796  83% /
tmpfs            1928708      84   1928624   1% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
tmpfs            1928708       0   1928708   0% /sys/fs/cgroup
tmpfs            1928708       4   1928704   1% /tmp
cgmfs                100       0       100   0% /run/cgmanager/fs
tmpfs             385744      36    385708   1% /run/user/999
/dev/sdb2        9757624   22092   9216828   1% /media/ubuntu/casper-rw
ubuntu@ubuntu:~$ ls -l /media
total 4
lrwxrwxrwx  1 root root    6 Jul 18 01:22 cdrom -> /cdrom
drwxr-x---+ 3 root root 4096 Aug  3 14:13 ubuntu
ubuntu@ubuntu:~$ cat /etc/mtab
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1916740k,nr_inodes=479185,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,noexec,relatime,size=385744k,mode=755 0 0
/dev/sdb1 /cdrom vfat rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
/cow / overlay rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work 0 0
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
tmpfs /sys/fs/cgroup tmpfs rw,mode=755 0 0
cgroup /sys/fs/cgroup/systemd cgroup rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd 0 0
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0
efivarfs /sys/firmware/efi/efivars efivarfs rw,nosuid,nodev,noexec,relatime 0 0
cgroup /sys/fs/cgroup/cpuset cgroup rw,nosuid,nodev,noexec,relatime,cpuset,clone_children 0 0
cgroup /sys/fs/cgroup/net_cls,net_prio cgroup rw,nosuid,nodev,noexec,relatime,net_cls,net_prio 0 0
cgroup /sys/fs/cgroup/freezer cgroup rw,nosuid,nodev,noexec,relatime,freezer 0 0
cgroup /sys/fs/cgroup/hugetlb cgroup rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb 0 0
cgroup /sys/fs/cgroup/cpu,cpuacct cgroup rw,nosuid,nodev,noexec,relatime,cpu,cpuacct 0 0
cgroup /sys/fs/cgroup/perf_event cgroup rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event 0 0
cgroup /sys/fs/cgroup/memory cgroup rw,nosuid,nodev,noexec,relatime,memory 0 0
cgroup /sys/fs/cgroup/blkio cgroup rw,nosuid,nodev,noexec,relatime,blkio 0 0
cgroup /sys/fs/cgroup/devices cgroup rw,nosuid,nodev,noexec,relatime,devices 0 0
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=20,pgrp=1,timeout=300,minproto=5,maxproto=5,direct 0 0
mqueue /dev/mqueue mqueue rw,relatime 0 0
debugfs /sys/kernel/debug debugfs rw,relatime 0 0
hugetlbfs /dev/hugepages hugetlbfs rw,relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
cgmfs /run/cgmanager/fs tmpfs rw,relatime,size=100k,mode=755 0 0
tmpfs /run/user/999 tmpfs rw,nosuid,nodev,relatime,size=385744k,mode=700,uid=999,gid=999 0 0
gvfsd-fuse /run/user/999/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
/dev/sdb2 /media/ubuntu/casper-rw ext4 rw,nosuid,nodev,relatime,data=ordered 0 0
ubuntu@ubuntu:~$ 
```

---

### Post by sudodus on 2015-08-03
> **nick208 said:**
> I think I may have used method 0 on [this link]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), so that would be usb-creator. But cant swear on it Bit of a jungle navigating through these things and I tend not to memorize path chosen :). Option 2 sounds great.
```

ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1916740       0   1916740   0% /dev
tmpfs             385744   10880    374864   3% /run
/dev/sdb1        5130440 2171112   2959328  43% /cdrom
/dev/loop0       1075968 1075968         0 100% /rofs
[COLOR="#FF0000"]/cow              999320  782096    164796  83% /[/COLOR]
...
[COLOR="#FF0000"]/dev/sdb2        9757624   22092   9216828   1% /media/ubuntu/casper-rw[/COLOR]
ubuntu@ubuntu:~$ ls -l /media
total 4
lrwxrwxrwx  1 root root    6 Jul 18 01:22 cdrom -> /cdrom
[COLOR="#FF0000"]drwxr-x---+ 3 root root 4096 Aug  3 14:13 ubuntu[/COLOR]
ubuntu@ubuntu:~$ cat /etc/mtab
...
[COLOR="#FF0000"]/dev/sdb2 /media/ubuntu/casper-rw ext4 rw,nosuid,nodev,relatime,data=ordered 0 0[/COLOR]
ubuntu@ubuntu:~$ 
```

df: When the sizes of / and /media/ubuntu/casper-rw are different, you have no persistence

[COLOR="#FF0000"]drwxr-x---+ 3 root root 4096 Aug  3 14:13 ubuntu[/COLOR] shows that only root has write access to the partition

cat /etc/mtab: The partition is mounted rw, read-write.

So in order to write to the casper-rw partition, you should be able to write with root privilages

```
sudo cp source /media/ubuntu/casper-rw/some-directory
```

but as I wrote in my previous post, it is better to make it active for persistence. You should add the word **persistent** into a file.

Please search for files with the extension **cfg**. You can try with the following command

```
find /cdrom -name "*.cfg"
```

and tell us which files you find (the file names). You can also start looking into them, and post them if they are not too big. We are searching for a rather small text file, I think much less than 100 lines.

-o-

But if we cannot solve it this way, maybe we should try another method to create the persistent live system, either with Unetbootin from the developer's PPA

[Installation/FromUSBStick#Unetbootin](https://help.ubuntu.com/community/Installation/FromUSBStick#Unetbootin)

or with a method, that I have developed recently, see post #6 and the following in this link

[One pendrive for all PC (Intel/AMD) computers - single boot, dual boot, multi boot](http://ubuntuforums.org/showthread.php?t=2259682)

---

### Post by nick208 on 2015-08-04
```
ubuntu@ubuntu:~$ find /cdrom -name "*.cfg"
/cdrom/boot/grub/x86_64-efi/grub.cfg
/cdrom/boot/grub/grub.cfg
/cdrom/boot/grub/loopback.cfg
/cdrom/syslinux/adtxt.cfg
/cdrom/syslinux/dtmenu.cfg
/cdrom/syslinux/exithelp.cfg
/cdrom/syslinux/gfxboot.cfg
/cdrom/syslinux/menu.cfg
/cdrom/syslinux/prompt.cfg
/cdrom/syslinux/rqtxt.cfg
/cdrom/syslinux/stdmenu.cfg
/cdrom/syslinux/txt.cfg
/cdrom/syslinux/syslinux.cfg
```
If I did the grep below correctly, there looks like a lot of occurences of the word **persistent**.
```
ubuntu@ubuntu:~$ grep persistent -r --include=\*.cfg /cdrom
/cdrom/boot/grub/grub.cfg:    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --- cdrom-detect/try-usb=true noprompt persistent
/cdrom/boot/grub/grub.cfg:    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --- cdrom-detect/try-usb=true noprompt persistent
/cdrom/boot/grub/grub.cfg:    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --- cdrom-detect/try-usb=true noprompt persistent
/cdrom/boot/grub/loopback.cfg:    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash --- cdrom-detect/try-usb=true noprompt persistent
/cdrom/boot/grub/loopback.cfg:    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash --- cdrom-detect/try-usb=true noprompt persistent
/cdrom/syslinux/rqtxt.cfg:append noprompt cdrom-detect/try-usb=true persistent vga=788 initrd=/install/initrd.gz rescue/enable=true --- quiet
/cdrom/syslinux/txt.cfg:append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash ---
/cdrom/syslinux/txt.cfg:append noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash ---
```


By the way, settings, files and such are saved after reboot.
Thanks

---

### Post by sudodus on 2015-08-04
I think that the Startup Disk Creator alias usb-creator boots via syslinux, so I guess the relevant configuration should is in the syslinux directory or via that entry. Anyway, if your  settings, files and such are saved after reboot, persistence is working now. Congratulations :KS

If you feel that the problem (in your first post) is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by nick208 on 2015-08-04
Thanks for guiding me through this. So my conclusion is that persistence is working,** but casper-rw is not used**. So I will soon run out of space. Does that make sense?

---

### Post by sudodus on 2015-08-04
Are you sure that casper-rw is not used? I think that persistance is working, and that it is using the casper-rw partition, unless you have a casper-rw file, that might be found first (before the casper-rw partition).

When you have persistence running, please run the command df and post the output!

```
df
```

You can search for a casper-rw file

```
sudo find / -name casper-rw
```

---

### Post by nick208 on 2015-08-04
```
ubuntu@ubuntu:/cdrom$ sudo find / -name casper-rw
/dev/disk/by-label/casper-rw
/media/ubuntu/casper-rw
/cdrom/casper-rw
```
Does that meant that there is one partition and one file?
I havent changed anything so **[FONT=fixedsys]df[/FONT]** should be the same. If I download files the free space of the home folder gets smaller and the casper-rw partition stays the same.

---

### Post by sudodus on 2015-08-04
These
/dev/disk/by-label/casper-rw
/media/ubuntu/casper-rw

point to the partition

This

/cdrom/casper-rw

is a file. Check the size of it

```
ls -lh /cdrom/casper-rw
```

If you remove or rename the file, the casper-rw partition should be used instead.

---

### Post by nick208 on 2015-08-04
**Working!** Renamed the casper-rw file and then the partition was used. *Thanks*!
Now I just have to figure out how to move the settings and configurations (language, wifi, bluetooth etc) from the renamed casper-rw to the partition.

---

### Post by sudodus on 2015-08-04
You should be able to test it, 'dry run' (with the actual paths for sourcedir and targetdir)

```
sudo rsync -Havn sourcedir/ targetdir
```

The trailing slash is important. Then copy with

```
sudo rsync -Hav sourcedir/ targetdir
```

See ```
man rsync
``` for more details.

---

### Post by nick208 on 2015-08-04
Managed to get myself into an *infinite loop* with rsync.:eek: But now its pretty much working. Suddenly I seem to be able to access the win partition aswell.
Thanks again.

---

### Post by sudodus on 2015-08-04
Maybe you put a space before the slash. The slash should be directly after 'sourcedir', and there should be a space after the slash.

---

### Post by nick208 on 2015-08-04
Possibly. Got the destination folder wrong, thought I could use "." but probablty should have been ~/.
Anyways, now I have another question about autostarting. Since I use the stick on a tablet (with no way of selecting) I have to plugin a keyboard to be able to select the boot option and start. I wonder how I can make it automatical - booting the first option automatically. But I guess that should be a **new thread**?

---

### Post by sudodus on 2015-08-05
Yes, it is a good idea to start a new thread with a good descriptive title for this new problem.

Explain what you have and what you want. (Tell them that you created this system with the Ubuntu Startup Disk Creator ...)

You can post a link from this thread to the new thread, so that I and others who have followed this thread can find your new thread.

---

### Post by sudodus on 2015-08-05
I just found [this link to a post by C.S.Cameron](http://ubuntuforums.org/showthread.php?t=2289403&p=13333137#post13333137), that explains where to put the boot option persistent, when created by the Startup Disk Creator:

```
/cdrom/syslinux/txt.cfg
```

---

