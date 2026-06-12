---
title: "Installation WITHOUT burning CD image, NetInstall (long)"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Ginzel on 2008-02-04
Hello!

   I would to install Ubuntu GNU/Linux to a free partition on my hard
disk in my PC already running a GNU/Linux system WITHOUT any boot from
CD. I also don't want to setup a dhcp-boot/tftp server as described in
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot).
I can imagine more scenarios:

Scenario KERNEL.
  - Download special kernel/initrd with dhcp, network root, ...
    to the /boot/ directory of the running GNU/Linux system.
  - Update grub or lilo (because of xfs e.g.) configuration
    (or use proper grub prompt commands).
  - reboot
  - New kernel will boot with network root file system on the Internet
    somewhere. Does anybody provide this?
  - Some light terminal (ncurses) installation will start, ask for
    distribution (Feisty/Gutsy/... or Ubuntu/Debian/...),
    language, partitions, ... and start copying base file system from
    the Internet. After base+grub/lilo configuration and reboot
    rest packages will be installed as usual.

Scenario BASE FS.
  - From the running GNU/Linux system prepare (format) the new
    partition.
  - Download some (Which one?) file. Unpack+untar it to the new
    partition.
  - Set up grub/lilo.
  - Mount and chroot to the new partition OR reboot and do base
    configuration.
  - Continue with installing packages.

Scenario (CD)IMAGE MINING.
  - From the running GNU/Linux system prepare (format) the new
    partition.
  - Download some minimal CD/USB FlashDisk/NetInstall image.
    Which one? Where from?
  - Mount the image using loop device.
  - Copy/unpack/untar something (What?) from the mounted image
    to the new partition and continue as in previous scenario.

Scenario CLONE.
  - From the running GNU/Linux system prepare (format) the new
    partition.
  - Mount formated partition.
  - Copy current system (cp -a --one-file-system / /mnt/new_part).
  - Reboot or chroot.
  - Change repositories in sources.list.
  - update/upgrade
  - Only usable for e.g. newer (alpha/beta) version of same system.

Scenario BOOT IMAGE.
  - Download some minimal image to current file system. (Which ?)
  - Boot it using current grub/lilo.
  - Continue with standard installation (probably text mode).

  Can anyone help me, please, to bring one of the scenario to the
reality? I would like to download image not greater than say 100MB.

  Why to burn CD images? Is there an universal image which to boot and
continue booting from hard disk with downloaded image? Can this image
lay on NTFS or vfat? Moreover, can the image be booted by NT/Vista loader?
Is there a way to boot CD image from grub/lilo not burn it and boot
from CD? Can Debian installer be used to install Ubuntu 8.04 Alpha ([http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/)?](http://ftp.nl.debian.org/debian/dists/etch/main/installer-i386/current/images/hd-media/)?)

	Thanks
	Hans Ginzel

---

### Post by logos34 on 2008-02-04
> **Ginzel said:**
> Hello!

   I would to install Ubuntu GNU/Linux to a free partition on my hard
disk in my PC already running a GNU/Linux system WITHOUT any boot from
CD. I also don't want to setup a dhcp-boot/tftp server as described in
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot).

 ...

Scenario BOOT IMAGE.
  - Download some minimal image to current file system. (Which ?)
  - Boot it using current grub/lilo.
  - Continue with standard installation (probably text mode).

  Can anyone help me, please, to bring one of the scenario to the
reality? I would like to download image not greater than say 100MB.

try this:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)
(--> 'Alternate CD' instructions)

but substitute the '[minimal CD image]("https://help.ubuntu.com/community/Installation/MinimalCD")' (~10 mb)

---

