---
title: "Upgraded Ubuntu Mate to 22.04 now all drives added 1 to end and original not availabl"
date: 2022-11-10
forum: Installation &amp; Upgrades
---

### Post by BudworthTDog on 2022-11-10
Hello, I recently update my Ubuntu Mate from 20.04 to 22.04 and ever since I am having trouble with all my additional drives. The original drives are not accessible.  In Caja it has an X over the file and when I try to access it it gives me an error that says 'You do not have the permissions necessary to view the contents of "Name of here"'

It also added an additional drive with the name of the original drive with a 1 at the end. These drives are accessible. It looks like this in Caja. 

[IMG]https://i.imgur.com/cR5VCfc.png[/IMG]

Also the files will not play in Plex, says they are not mounted. I'm pretty sure this is all a permission issue but I'm not sure where to start. Any help would be appreciated.

---

### Post by yancek on 2022-11-11
Did you update 20.04 to 22.04 using the terminal or the software updater?  Did you install 22.04 from a usb to the same partition on which you had 20.04.  It would be useful to know the number of drives/partitions you have.  Post the output of either of the following commands here:

```
sudo fdisk -l
sudo parted -l
```

Are you able to boot and use the updated 22.04?  What does "original drives are not accessible" mean?  Is 22.04 on a new drive?  Partitions on external or additional drives are generally not accessible by a normal user until permissions are set to allow it.  Are these additional drives/partitions shown under /media/username?  If so, show the owner/group and permissions with the following command:

```
 ls -l /media/username
```

Insert your actual user name above.

---

### Post by &amp;KyT$0P# on 2022-11-11
In addition to the information yancek requested, please also post the output from running the following command in Terminal -
```
findmnt
```

---

### Post by ActionParsnip on 2022-11-11
also what is the output of:
```

cat -n /etc/fstab

```

---

### Post by BudworthTDog on 2022-11-11
Thank you for your reply, I updated from 20.04 to 22.04 through the  Software Updater, not through the terminal. The output for sudo fdisk -l  is as follows. 

> Disk /dev/loop0: 55.56 MiB, 58261504 bytes, 113792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 55.58 MiB, 58281984 bytes, 113832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 63.2 MiB, 66265088 bytes, 129424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 346.33 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 47.98 MiB, 50315264 bytes, 98272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 47.99 MiB, 50319360 bytes, 98280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 10.91 TiB, 12000138625024 bytes, 23437770752 sectors
Disk model: ST12000NM0007-2A
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 86C52E52-9391-46B8-A2ED-71138DE9DCAD

Device     Start         End     Sectors  Size Type
/dev/sda1   2048 23437768703 23437766656 10.9T Linux filesystem


Disk /dev/sdb: 447.13 GiB, 480103981056 bytes, 937703088 sectors
Disk model: SATA SSD        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 237779C1-0F9B-4689-8A98-5F0375295767

Device       Start       End   Sectors   Size Type
/dev/sdb1     2048   1050623   1048576   512M EFI System
/dev/sdb2  1050624 937701375 936650752 446.6G Linux filesystem


Disk /dev/sdc: 10.91 TiB, 12000138625024 bytes, 23437770752 sectors
Disk model: ST12000NM0007-2A
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 5A49FB31-E385-4A61-87EC-E524F2FA4C72

Device     Start         End     Sectors  Size Type
/dev/sdc1   2048 23437768703 23437766656 10.9T Linux filesystem


Disk /dev/sdd: 7.28 TiB, 8001563222016 bytes, 15628053168 sectors
Disk model: ST8000VN0022-2EL
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sde: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EACS-00Z
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002a5b4

Device     Boot Start        End    Sectors   Size Id Type
/dev/sde1  *       63 1953520064 1953520002 931.5G 83 Linux


Disk /dev/loop8: 16 KiB, 16384 bytes, 32 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 16 KiB, 16384 bytes, 32 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 13.52 MiB, 14172160 bytes, 27680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 13.52 MiB, 14172160 bytes, 27680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 63.24 MiB, 66314240 bytes, 129520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


I  am able to boot up and use 22.04 just fine. I have an SSD that I run my  OS off of and all my day to day files, all of that appears to be  running just fine and is accessible. For my video media files I have  three additional drives. They are named 'Movies.and.More', 'TV', and 'TV  Backup'. If you look at the image I posted from my file manager you  will see all of those listed but with an X over the mini-picture of a  file. Those are the drives and files that are inaccessible. Then you  will see 'Movies.and.More1', 'TV1', and 'TV Backup1' listed. Those were  created automatically somehow during the upgrade. They are accessible  with all the media that were on there originally. 

The output for the ls -l /media/username command is as follows

> total 44
drwx------   2 root   root    4096 Nov  8 15:58  Movies.and.More
drwxr-xr-x  13 mrmilo mrmilo  4096 Aug 21  2020  Movies.and.More1
drwx------   2 root   root    4096 Nov  8 15:58  TV
drwxr-xr-x 301 mrmilo mrmilo 12288 Aug 27 17:08  TV1
drwx------   2 root   root    4096 Nov  8 15:59 'TV Backup'
drwx------ 301 mrmilo mrmilo 12288 Aug 27 17:10 'TV Backup1'
drwx------   2 root   root    4096 Mar 11  2021  windows



Thanks again.

---

### Post by BudworthTDog on 2022-11-11
> **halogen2 said:**
> In addition to the information yancek requested, please also post the output from running the following command in Terminal -
```
findmnt
```

The output for findmnt is as follows 

> TARGET                           SOURCE      FSTYPE  OPTIONS
/                                /dev/sdb2   ext4    rw,relatime,errors=remount-
&#9500;&#9472;/sys                           sysfs       sysfs   rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/kernel/security         securityfs  securit rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/fs/cgroup               cgroup2     cgroup2 rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/fs/pstore               pstore      pstore  rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/firmware/efi/efivars    efivarfs    efivarf rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/fs/bpf                  bpf         bpf     rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/kernel/debug            debugfs     debugfs rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/kernel/tracing          tracefs     tracefs rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/sys/fs/fuse/connections     fusectl     fusectl rw,nosuid,nodev,noexec,rela
&#9474; &#9492;&#9472;/sys/kernel/config           configfs    configf rw,nosuid,nodev,noexec,rela
&#9500;&#9472;/proc                          proc        proc    rw,nosuid,nodev,noexec,rela
&#9474; &#9492;&#9472;/proc/sys/fs/binfmt_misc     systemd-1   autofs  rw,relatime,fd=29,pgrp=1,ti
&#9474;   &#9492;&#9472;/proc/sys/fs/binfmt_misc   binfmt_misc binfmt_ rw,nosuid,nodev,noexec,rela
&#9500;&#9472;/dev                           udev        devtmpf rw,nosuid,relatime,size=163
&#9474; &#9500;&#9472;/dev/pts                     devpts      devpts  rw,nosuid,noexec,relatime,g
&#9474; &#9500;&#9472;/dev/shm                     tmpfs       tmpfs   rw,nosuid,nodev,inode64
&#9474; &#9500;&#9472;/dev/mqueue                  mqueue      mqueue  rw,nosuid,nodev,noexec,rela
&#9474; &#9492;&#9472;/dev/hugepages               hugetlbfs   hugetlb rw,relatime,pagesize=2M
&#9500;&#9472;/run                           tmpfs       tmpfs   rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/run/lock                    tmpfs       tmpfs   rw,nosuid,nodev,noexec,rela
&#9474; &#9500;&#9472;/run/credentials/systemd-sysusers.service
&#9474; &#9474;                              none        ramfs   ro,nosuid,nodev,noexec,rela
&#9474; &#9492;&#9472;/run/user/1000               tmpfs       tmpfs   rw,nosuid,nodev,relatime,si
&#9474;   &#9500;&#9472;/run/user/1000/gvfs        gvfsd-fuse  fuse.gv rw,nosuid,nodev,relatime,us
&#9474;   &#9492;&#9472;/run/user/1000/doc         portal      fuse.po rw,nosuid,nodev,relatime,us
&#9500;&#9472;/snap/bare/5                   /dev/loop2  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/core18/2566              /dev/loop0  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/core18/2620              /dev/loop1  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/core20/1634              /dev/loop4  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/gnome-3-38-2004/119      /dev/loop5  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/snapd/17336              /dev/loop7  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/software-boutique/54     /dev/loop8  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/snapd/17029              /dev/loop6  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/software-boutique/57     /dev/loop9  squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/ubuntu-mate-welcome/709  /dev/loop10 squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/snap/ubuntu-mate-welcome/714  /dev/loop11 squashf ro,nodev,relatime,errors=co
&#9500;&#9472;/boot/efi                      /dev/sdb1   vfat    rw,relatime,fmask=0077,dmas
&#9500;&#9472;/media/mrmilo/TV Backup1       /dev/sda1   ext4    rw,nosuid,nodev,relatime,er
&#9500;&#9472;/media/mrmilo/TV1              /dev/sdc1   ext4    rw,nosuid,nodev,relatime,er
&#9500;&#9472;/media/mrmilo/Movies.and.More1 /dev/sdd    ext4    rw,nosuid,nodev,relatime,er
&#9492;&#9472;/snap/core20/1695              /dev/loop12 squashf ro,nodev,relatime,errors=co


---

### Post by BudworthTDog on 2022-11-11
> **ActionParsnip said:**
> also what is the output of:
```

cat -n /etc/fstab

```

The output for cat -n /etc/fstab is as follows 

>  1    # /etc/fstab: static file system information.
     2    #
     3    # Use 'blkid' to print the universally unique identifier for a
     4    # device; this may be used with UUID= as a more robust way to name devices
     5    # that works even if disks are added and removed. See fstab(5).
     6    #
     7    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
     8    # / was on /dev/sda2 during installation
     9    UUID=4ec3185a-eb0d-46e3-ba16-5d01fcd25c65 /               ext4    errors=remount-ro 0       1
    10    # /boot/efi was on /dev/sda1 during installation
    11    UUID=20F2-FEBC  /boot/efi       vfat    umask=0077      0       1
    12    /swapfile                                 none            swap    sw              0       0


---

### Post by &amp;KyT$0P# on 2022-11-11
It is hard to read the outputs since they lost their proper formatting, which would have been preserved if you had posted them inside [noparse]```
[/noparse] tags instead of quote tags.  But I think you could try this -
[CODE]sudo rmdir -v "/media/mrmilo/TV Backup" "/media/mrmilo/TV" "/media/mrmilo/Movies.and.More"
```
Then unmount your drives and remount them.

Does that achieve what you're seeking?

---

### Post by BudworthTDog on 2022-11-12
> **halogen2 said:**
> It is hard to read the outputs since they lost their proper formatting, which would have been preserved if you had posted them inside [noparse]```
[/noparse] tags instead of quote tags.  But I think you could try this -
[CODE]sudo rmdir -v "/media/mrmilo/TV Backup" "/media/mrmilo/TV" "/media/mrmilo/Movies.and.More"
```
Then unmount your drives and remount them.

Does that achieve what you're seeking?

Yup, that fixed it! Thanks!

---

