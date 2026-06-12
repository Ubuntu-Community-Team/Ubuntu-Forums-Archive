---
title: "3 Ubuntu distros go from fast reboot to SLOW after installing nVidia drivers"
date: 2016-09-24
forum: Installation &amp; Upgrades
---

### Post by finny388 on 2016-09-24
Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz
8GB ram
gtx 970

boot-repair info:
[URL="http://paste.ubuntu.com/23223011/"]http://paste.ubuntu.com/23223011/
[/URL]
[B]
Ubuntu Mate 16.04, Kubuntu 16.04, KDE Neon 5.7 (16.04)

Fresh installs and in all 3 cases they went from ~15 sec reboots to 2:30 to over 3 min after installing nVidia drivers. I'm currently on Neon and the driver is 361.42.[/B]

```
$ systemd-analyze blame
           288ms dev-sdc2.device
           283ms plymouth-start.service
           192ms setvtrgb.service
           155ms systemd-fsck@dev-disk-by\x2duuid-75d98f5c\x2d71f9\x2d4a25\x2dab69\x2d219e516f4e0b.service
           150ms upower.service
           135ms networking.service
           108ms ModemManager.service
            89ms apport.service
            88ms systemd-logind.service
            84ms accounts-daemon.service
            80ms apparmor.service
            80ms thermald.service
            69ms NetworkManager.service
            69ms ondemand.service
            66ms systemd-fsck@dev-disk-by\x2duuid-A4E0\x2d0DEF.service
            65ms grub-common.service
            63ms snapd.firstboot.service
            56ms console-setup.service
            50ms irqbalance.service
            49ms plymouth-read-write.service
            48ms systemd-udev-trigger.service
            47ms gpu-manager.service
            37ms mnt-FH_WD_BLACK_FILES.mount
            35ms iio-sensor-proxy.service
            35ms keyboard-setup.service
            30ms systemd-journald.service
            28ms packagekit.service
            26ms udisks2.service
            25ms systemd-udevd.service
            24ms systemd-user-sessions.service
            22ms systemd-tmpfiles-setup.service
            22ms plymouth-quit.service

```
(there's more but just more milliseconds)

Any help or insights so appreciated.
Thanks

---

### Post by QIII on 2016-09-24
Hello!

If you are running Neon currently, this thread should be moved to the ***Ubuntu/Debian BASED*** forum.

If you would prefer that I don't move it from the Ubuntu Official Flavours Support area, please reboot to an official Ubuntu flavor and re-post the results given above.

---

### Post by oldfred on 2016-09-24
Do not know Neon.

Did you have the Neon drive as sda when you installed it? 
With Ubuntu grub in UEFI mode only installs to drive seen as sda. But your ESP is sdc5.

Errors from systemd seem to be related to fsck on sdc2 and plymouth start?
Do not know plymouth issues.

But you may want to run a full fsck on sdc5 and perhaps other ext4 partitions.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by finny388 on 2016-09-24
Okay, I'm logged into Kubuntu 16.04 with nVidia driver 364.19

Neon was always sdc. sdc is the main while sda is alternate (used to be main and pre-existed)
ESP?

UEFI confuses me.

Here's the systemd blame:
```
$ systemd-analyze blame
         37.713s apt-daily.service
           376ms accounts-daemon.service
           345ms networking.service
           321ms dev-sdc1.device
           319ms thermald.service
           316ms bluetooth.service
           311ms avahi-daemon.service
           307ms systemd-logind.service
           307ms NetworkManager.service
           301ms irqbalance.service
           298ms grub-common.service
           292ms iio-sensor-proxy.service
           200ms wpa_supplicant.service
           151ms upower.service
           138ms systemd-fsck@dev-disk-by\x2duuid-A4E0\x2d0DEF.service
            63ms systemd-rfkill.service
            58ms apparmor.service
            55ms snapd.firstboot.service
            54ms console-setup.service
            46ms systemd-udev-trigger.service
            42ms apport.service
            37ms ondemand.service
            36ms systemd-journald.service
            34ms keyboard-setup.service
            30ms rsyslog.service
            30ms systemd-modules-load.service
            29ms systemd-udevd.service
            26ms udisks2.service

```

---

### Post by finny388 on 2016-09-24
Is there a tutorial for reading boot-info?

Seems there are instructions everywhere on how to create it and it ends there.

---

### Post by oldfred on 2016-09-24
Almost all of the Boot-Repair summary report is many standard terminal command's output. 
Experience helps. Especially when it is something missing that should be there.
And good eyes, I still miss things that otherwise should be obvious.

I just ran this from my main working install of 16.04 on SSD:
 fred@Asusz97:~$ systemd-analyze blame

   8.936s NetworkManager-wait-online.service
  3.771s apt-daily.service
   520ms snapd.refresh.service
   328ms systemd-fsck@dev-disk-by\x2duuid-a0c1c99f\x2d0f09\x2d4787\x2da7 

And noticed my /mnt/data partition seemed to have issues. Rebooted into my Yakkety install which is on HDD and it loaded a lot slower. So ran fsck and this was new result on reboot. Only top output shown.

 fred@Asusz97:~$ systemd-analyze blame

   8.727s NetworkManager-wait-online.service
   271ms dev-sda6.device
   266ms dev-disk-by\x2duuid-493a8696\x2d5fa7\x2d48d7\x2d9ebb\x2d4c9ef24
   146ms ModemManager.service 
 		   136ms systemd-fsck@dev-disk-by\x2duuid-a0c1c99f\x2d0f09\x2d4787\x2da7

---

### Post by finny388 on 2016-09-24
Here's a scrape of the headings in boot-info:

Boot Info Summary: 
Drive/Partition Info: 
"ls -l /dev/disk/by-id" output: 
Mount points: 
 
sda1/boot/grub/grub.cfg: 
 	sda1/etc/fstab: 
 
sda8/boot/grub/grub.cfg: 
 	sda8/etc/fstab: 
 
sdc1/boot/grub/grub.cfg: 
 	sdc1/etc/fstab: 
 
sdc2/boot/grub/grub.cfg: 
 	sdc2/etc/fstab: 
 
sdd1/boot/grub/grub.cfg: 
 sdd1/syslinux.cfg: 
 sdd1: Version of COM32(R) files used by Syslinux: 
 
StdErr Messages: 
log of boot-repair 2016-09-24__03h37 
os-prober:
blkid:

sdc1/etc/grub.d/ :
sdc1/etc/default/grub :
sdc2/etc/grub.d/ :
sdc2/etc/default/grub :
sda1/etc/grub.d/ :
sda1/etc/grub.d/40_custom :
sda1/etc/default/grub :
sda8/etc/grub.d/ :
sda8/etc/default/grub :

UEFI/Legacy mode:

PARTITIONS & DISKS:
parted -l:
parted -lm:
mount:
ls:
hexdump -n512 -C /dev/sdc4
hexdump -n512 -C /dev/sdc5
hexdump -n512 -C /dev/sdc6
df -Th:
fdisk -l:

Recommended repair

---

### Post by oldfred on 2016-09-24
So is there a question there?
Boot-Repair shows most of the commands, if you run them you need sudo for most. fdisk, parted, df, hexdump, blkid, etc all are commands, if you want more info and what parameters are use man pages
man parted
man df
i.e.
sudo fdisk -lu
sudo parted -l


Did you run the e2fsck and see if that made a difference?

---

### Post by finny388 on 2016-09-24
I'll try es2fsck.

Stay tuned...

---

### Post by finny388 on 2016-09-24
Running from the boot repair iso, command failed:
```
@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdc5
e2fsck: Bad magic number in super-block while trying to open /dev/sdc5
/dev/sdc5: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

---

### Post by oldfred on 2016-09-24
If sdc5 and the ESP, that is FAT32 and you have to use dosfsck.

       dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdc5
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by finny388 on 2016-09-25
seemed to run okay with no errors.
no noticeable change though

return code:```
fsck.fat 3.0.26 (2014-03-07)
/dev/scd5: 371 files, 55188/98304 clusters 
```

---

### Post by oldfred on 2016-09-25
Did you use the -a parameter in dosfsck to clear the dirty bit?

---

### Post by finny388 on 2016-09-25
yes```
sudo dosfsck -t -a -w /dev/sdc5
```

---

### Post by finny388 on 2016-09-25
Switched back to nouveau driver and now it's fast again.
8 s for desktop to close, 6 sec more to POST, then about 30 s to get to desktop.

Old numbers were about 1:45 to POST and another 1 minute to get to desktop.


but I want to use nvidia, (nvidia works fine in Kubuntu 14.10)

---

