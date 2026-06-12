---
title: "After do-release-upgrade, Ubuntu won't boot or reload GRUB"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by damian_ on 2014-07-30
Ran a do-release-upgrade last night (can't remember what version it came from, but I assume only one or two versions ago) and Ubuntu no longer boots. I don't remember seeing any errors through the upgrade.

When I boot normally, I get the following:
```
error: invalid arch-independant ELF magic.
Entering rescue mode...
grub rescue>
```

I boot from 14.04 server install disc; I believe I've selected the correct mount points, /boot contents look right:
```
/dev/mapper/leonardo-root  36G  21G  14G  61%  /
/dev/sda1  228M  64M  152M  30%  /boot
```

When I try and reinstall GRUB I get this:
```
# sudo grub-install /dev/sda1
Installing for i386-pc platform.
grub-install: error: cannot delete `/boot/grub/i386-pc/gcry_rsa.mod': Input/output error.
```

Some of the guys in #ubuntu/freenode said to run the bootinfoscript, this is the output: [http://pastebin.com/dSqtVDHj](http://pastebin.com/dSqtVDHj)

Any assistance would be great, I really don't want to have to reinstall the OS just because boot is warped :\

Thanks,

---

### Post by damian_ on 2014-07-30
Just an update (and after me buggering around for a while), I figured I could simply wipe the /boot partition and start over. So I've jumped into fdisk, (d)eleted the /dev/sda1 partition; created a (n)ew partition in the space; wrote the changes.

When rebooting, naturally it has come up with 'error: unknown filesystem.'.
- Boot back up into rescue mode and mkfs -t ext2 /dev/sda1
- Booted again into rescue mode and ran a grub-install:
```
# grub-install /dev/sda1
Installing for i386-pc platform.
grub-install: warning: File system 'ext2' doesn't support embedding.
grub-install: error: embedding is not possible, but this is required for RAID and LVM install.
```

In my old /etc/fstab I have this:
```
UUID=886a842c-b2f7-4341-b53b-c03d1df53855 /boot
```

So I attempted to grub-install to the UUID, no dice.

Any additional information would be fantastic.

---

### Post by damian_ on 2014-07-31
Just another update, I have found that I can install grub to /dev/sda (not /dev/sda1), which made grub boot and put me to the grub> prompt.

From there, I rebooted and booted into the recovery mode again, then ran the following:
```
apt-get install --reinstall linux-image-3.13.0-32-generic

update-grub
```

These seemed to have rebuilt my linux kernel to the latest version and updated the grub.cfg so it boots the image. So now when I boot, I am getting THIS:

```
error: diskfilter writes are not supported.

Press any key to continue...
```

After which the system crashes, does a dump stack, panic, mount block and rest init and freezes.

---

### Post by damian_ on 2014-07-31
So just so this job can be rounded up and for anyone else with a similar issue, TJ- in #ubuntu ended up helping me out with this and gave me the following:

```
update-initramfs -uvk all; update-grub
```

This ran through it's shizzle and now the system boots - with quite a few errors, but she boots and works.

Thanks again to TJ-!

---

