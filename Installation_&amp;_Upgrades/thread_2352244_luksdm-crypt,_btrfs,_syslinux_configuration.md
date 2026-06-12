---
title: "luks/dm-crypt, btrfs, syslinux configuration"
date: 2017-02-10
forum: Installation &amp; Upgrades
---

### Post by jwhendy on 2017-02-10
I'm trying to setup a dual boot system and wanted to try using btrfs subvols for "partitions" rather than have to manually partition the disk. The gist is this:

- /dev/sdb1: ext4 /boot partition
- /dev/sdb2: luks/dm-crypt container formatted with btrfs

I already created subvolumes for arch and ubuntu. Since Arch was already installed, none of the ubuntu installer options fit for me. There was no ability to use cryptsetup to open the container and mount the desired subvol to an installation mount point. After googling around, it seemed that debootstrap was the only way to accomplish this. I can't seem to get it to prompt me for my encryption password at boot and the wiki seems to be a mess with almost 10 version of disk encryption articles! Here's my working arch syslinux entry for reference, though arch is using systemd for init:

```
LABEL arch-bigD
    MENU LABEL arch-bigD
    LINUX ../vmlinuz-linux
    APPEND luks.uuid=bcacb6d5-2874-4652-a25d-88b0bf3bbce8 root=UUID=e1284231-c264-4944-807d-5fcb1832ce47 rootflags=ssd,discard,compress=lzo,subvol=arch luks.allow-discards rw
    INITRD ../intel-ucode.img,../initramfs-linux.img

```

I've tried various incantations of this for ubuntu, but being a long time user of arch I don't know what sort of APPEND line the system would be looking for. I don't want to use grub as I already have syslinux but the information about syslinux seems sparse. There's also various suggestions regarding how to get modules built into the initramfs, which is where I suspect the issue might be occurring. Something loads, but then it repeatedly says it's running the local-block (or something like that...) and eventually I'm dropped into an emergency shell.

The critical details are:

- I want /dev/sdb2 opened by UUID with cryptsetup
- the opened container should be mounted to / using the subvol labeled "ubu"
- I want to accomplish this using syslinux

Here's an attempt at an ubuntu syslinux entry with three versions of the APPEND line based on different things arch expected over time:
```

LABEL ubu-bigD
    MENU LABEL ubu-bigD
    LINUX ../vmlinuz-4.4.0-21-generic
#    APPEND root=/dev/mapper/root cryptdevice=UUID=bcacb6d5-2874-4652-a25d-88b0bf3bbce8:root:allow-discards rootflags=ssd,discard,compress=lzo,subvol=ubu crypto=sha512:aes-xts-plain64:512:: rw
#    APPEND rd.luks.uuid=bcacb6d5-2874-4652-a25d-88b0bf3bbce8 root=UUID=e1284231-c264-4944-807d-5fcb1832ce47 crypto=sha512:aes-xts-plain64:512:: rootflags=ssd,discard,compress=lzo,subvol=ubu rd.luks.allow-discards rw
    APPEND luks.uuid=bcacb6d5-2874-4652-a25d-88b0bf3bbce8 root=UUID=e1284231-c264-4944-807d-5fcb1832ce47 rootflags=ssd,discard,compress=lzo,subvol=ubu luks.allow-discards rw
    INITRD ../initrd.img-4.4.0-21-generic
```

What I did was let debootstrap put the the initrd and vmlinuz in /mnt/install-dir/boot and then I manually put them in my separate /dev/sdb1 /boot top level directory, so the ../ links should be accurate above. As mentioned, it runs through a startup process... it just hangs saying that the UUID=e128... doesn't exist (which it wouldn't as cryptsetup never opens UUID=bcac...).

Thanks for any suggestions. I've been using arch for a long time, but trying a different distro has me feeling like a complete noob!

---

