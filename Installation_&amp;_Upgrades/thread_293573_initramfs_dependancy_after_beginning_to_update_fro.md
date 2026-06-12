---
title: "initramfs dependancy after beginning to update from breezy to edgy"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by cesine on 2006-11-05
i havent done a linux upgrade or configured my own packages in a long time (probably since 1996), i genneraly give up and find a new distro.. since my laptop is a tricky bastard (Averatec 6240) with wireless, overheating, and video problems galore i dont want to re-figure everything out so i figured it was time to suck it up and deal with dependancies...

i tried to update my kbuntu from breezy to edgy by following the commandline instructions 
[http://kubuntu.org/announcements/6.10-release.php](http://kubuntu.org/announcements/6.10-release.php)

i got a dependancy problem:

The following packages have unmet dependencies:
  initramfs-tools: Depends: volumeid but it is not installable

i found a number of unappetizing posts from people who tried to upgrade to edgy, so i changed my sources, updated them and tried to update to dapper instead
[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

but the same dependancy problem is appearing again. so i tried to figure out how to fix the dependancy problem:
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

here is what it proposed to remove:
The following packages will be REMOVED:
  initramfs-tools linux-386 linux-image-2.6.12-10-386
  linux-image-2.6.12-9-386 linux-image-386
  linux-restricted-modules-2.6.12-10-386
  linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-386
  ubuntu-desktop usplash

It wants to remove my linux: ubuntu_demon says on the forum:
"Don't remove apt / linux-386 / linux-686 / linux-k7 / ubuntu-minimal / grub. If it wants to remove any of those packages tell us all packages that it wants to remove. There's information about other important packages below. Please be careful."

is there someway to put initramfs back the way it was before i tried to upgrade to edgy...

i have a hunch i shouldn't reboot until i fix this since initramfs might have something to do with mounting disks:
[http://packages.debian.org/unstable/utils/initramfs-tools](http://packages.debian.org/unstable/utils/initramfs-tools)
"This package contains tools to create and boot an initramfs for packaged 2.6 Linux kernel. The initramfs is a gzipped cpio archive. At boot time, the kernel unpacks that archive into RAM, mounts and uses it as initial root file system. The mounting of the real root file system occurs in early user space. klibc provides utilities to setup root. Having the root on EVMS, MD, LVM2, LUKS or NFS is also supported. Any boot loader with initrd support is able to load an initramfs archive."

---

