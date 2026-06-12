---
title: "Recover grub after windows install with fakeraid"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by ephemerian on 2009-12-20
My system has Ubuntu 9.10 dual-booting with vista, and everything has been running fine. I have a two disks in raid 1 configuration (via the bios, so it's a fakeraid) and even that was no problem to set up. 

Then I upgraded vista to windows7. As expected, that overwrote the MBR so my grub boot menu doesn't appear any more. The problem I have is that the many recipes on the 'net for restoring grub don't work on my system. I'm not sure if it's the fakeraid (likely), grub2, the fact that my system is amd64 or what, but anyway I've so far failed to restore grub.

I have managed to boot back into linux using [super grub disk]("http://www.supergrubdisk.org/"). Generally, instructions for restoring grub say something like 'grub-install /dev/sda', but my fakeraid hides the physical disks behind LVM (in my so-far limited understanding) so I see /dev/mapper/whatever. If I list the current mount points, I get:

```
#> sudo mount
/dev/mapper/pdc_beidbcaig5 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/ian/.Private on /home/ian type ecryptfs (ecryptfs_sig=219a12a04ed0f1bd,ecryptfs_fnek_sig=fe6d86c372bc2a1e,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/ian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ian)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=ian)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```When booted up via SGD, my old /boot/grub/menu.lst is still there. So I guess what I need is the right incantation to restore grub to the MBR on the appropriate bit of the LVM mapping?

Any suggestions most welcome.

Thanks,
Ian

---

### Post by darkod on 2009-12-20
Can this help you?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Scroll down to Live CD Installation. The instructions are for full ubuntu install but you can look around and only use the part for reinstalling grub bootloader. The main thing seems to be installing dmraid package so it can see your raid devices properly. Maybe that's the problem.

---

### Post by ephemerian on 2009-12-20
Thanks for the pointer darkod. I didn't need to install dmraid, since that was working before I did the win7 upgrade. However, the fakeraid howto was a great place to look to find the solution. In the end, it was fairly straightforward:

```
b$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/pdc_beidbcaig
device (hd0) /dev/mapper/pdc_beidbcaig
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,4)
 (hd1,4)
grub> root (hd0,4)
root (hd0,4)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,4)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 
```Since I previously had a working raid system, I didn't need to re-generate menu.lst with grub-setup.

---

