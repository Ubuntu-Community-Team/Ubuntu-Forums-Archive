---
title: "Encrypting Using Keyfile on root"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by lasitus on 2013-01-13
I have a setup with a lot of encrypted volumes.  Rather than typing the password over and over again, I'm trying to setup a keyfile for all but root and a passphrase for root.  I have several encrypted partitions that are LVMed together.  Everything except the boot and root and swap partitions are in logical volumes, inside several encrypted raid arrays.

I have:

* Created the keyfile and put it on root
* Added the keyfile to the volumes
* Updated crypttab to use a keyfile for all volumes but root
* Ran update-initramfs -u and update-grub
* Rebooted

When I boot, I get a request for a passphrase for root.  This is successful, but it times out waiting for /tmp, which is a logical volume.  When I go to manage, all encrypted volumes show up but no lvm volumes.  If I do a vgscan/vgchange -a y, they all show up and are mountable.

So... it seems to me like it is trying to start up lvm before the encrypted devices show up.  Any ideas?

This is xubuntu 12.04

---

### Post by lasitus on 2013-01-13
A few more details about my setup.

sda1 - unencrypted boot
sda2 - encrypted swap using keyfile on root
sda3 - encrypted using passphrase
md0 - encrypted using keyfile on root (lvm physical volume)
md1 - encrypted using keyfile on root (lvm physical volume)
md2 - encrypted using keyfile on root (lvm physical volume)

/home, /var, /tmp are logical volumes on md0-2

Everything works fine if I don't use the key-file and enter the password a bunch of times.  When I'm dumped to a console, all of my logical volumes are inactive and none of them can mount.

Manually entering:

vgchange -a y
mount /home ...

is successful

I have been reading about a similar issue here:
[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Notes_for_making_it_work_in_Ubuntu_12.04_.22Precise_Pangolin.22_amd64](https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Notes_for_making_it_work_in_Ubuntu_12.04_.22Precise_Pangolin.22_amd64)

However, my root isn't in lvm... so, I'm thinking the stuff in the following line is for root, not other folders like home, var, and tmp.
GRUB_CMDLINE_LINUX_DEFAULT="cryptopts=target=pvcrypt,source=/dev/sda5,lvm=vg-root quiet splash"

My crypttab:

sda3_crypt UUID=94d620f1-1251-4f73-917a-e59cfb663a84 none luks
sda2_crypt UUID=c1675796-5e32-4afb-9d71-3519cd33c1ad /etc/keys/hd.key luks,swap,retry=1
md0_crypt UUID=1b3d24b1-067a-496f-ac96-403e7afc1210 /etc/keys/hd.key luks,retry=1
md1_crypt UUID=577b3be9-5a8d-4837-a9f1-2271c0a805fb /etc/keys/hd.key luks,retry=1
md2_crypt UUID=0120ccfb-28b3-4801-abd2-ab5d42c8a7c8 /etc/keys/hd.key luks,retry=1

---

