---
title: "&quot;libgcrypt.so not found&quot; error at boot"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by mzycdth on 2011-07-20
Hi guys,

I'm running an ubuntu based OS on an encrypted external hdd drive and recently ran "apt-get autoremove" which has damaged my ability to boot the drive.

The kernel boots to the passphrase login point but then gives an error that reads something like "error loading shared library - /sbin/cryptsetup/libgcrypt.so.11 file/directory does not exist". It does let me enter the passphrase but gives an error when I submit it - "crypsetup failed: options or bad password"

So I've mounted the drive in my normal ubuntu 11.04 environment and copied the libgcrypt.so.11 from "/lib/i386-linux-gnu/libgcrypt.so.11" to: 

/media/"boot partition volume identifier"/tmp/sbin
/media/"bpvi"/tmp/lib
/media/"bpvi"/tmp/lib/cryptsetup
/media/"bpvi"/tmp/usr/lib

the same error still occurs.

Any ideas? I have some vital and sensitive information on the disk so urgent help would be greatly appreciated.

Thanks in advance

---

### Post by mzycdth on 2011-07-20
Just to add,

I can mount the encrypted filesystem in ubuntu with the passphrase - so it's definitely not a bad pass issue.

I have tried chrooting into the mounted filesystem from a BT5 live cd and doing the same work, but to no avail. The below work in terminal just announces that all programs are present and up to date.

> apt-get update
apt-get install cryptsetup ecryptfs-utils keyutils hashalot lvm2
cryptsetup luksOpen /dev/[your logical partition] pvcrypt
mkdir /mnt/backtrack5
mount /dev/mapper/vg-root /mnt/backtrack5
mount /dev/[boot partition] /mnt/backtrack5/boot
chroot /mnt/backtrack5
mount -t proc proc /proc
mount -t sysfs sys /sys
mount -t devpts devpts /dev/pts
apt-get install cryptsetup ecryptfs-utils keyutils hashalot lvm2

Basically I have done this:

> SUPER IMPORTANT

Do not run aptitude safe-upgrade! It will remove some vital tools. Run apt-get upgrade instead which appears to leave things installed that need to be installed. If  you should happen to run aptitude safe-upgrade, ignore the warning about removing packages, type 'Y' and let it do its thing, you will need to run the following command before you reboot or your install will be broken.

apt-get install cryptsetup ecryptfs-utils keyutils

If you have problems, you can use the troubleshooting directions below to get back to the state where you can try to figure out how what went wrong.

[http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/](http://www.infosecramblings.com/backtrack/backtrack-5-bootable-usb-thumb-drive-with-full-disk-encryption/)

Any solutions?

---

