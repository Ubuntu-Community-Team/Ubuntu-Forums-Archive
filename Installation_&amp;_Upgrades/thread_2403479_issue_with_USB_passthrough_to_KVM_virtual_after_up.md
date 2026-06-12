---
title: "issue with USB passthrough to KVM virtual after updates Ubuntu Server 16.04"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by mishuk on 2018-10-11
Hi all,

So I did my usual apt update and upgrade on my KVM host. This last upgrade seems to have upgraded a few qemu-* packages. I had a USB device set to be passed through to the guest. Worked fine before the upgrade, lsusb would show the correct device and no issues in accessing it. After upgrade it's like the device was not passed to the guest any more, I did not change any settings in the virtual machine configs.

After some googling I managed to do a rollback of the updates with this:
```
apt install qemu-system-x86=1:2.5+dfsg-5ubuntu10.30 qemu-utils=1:2.5+dfsg-5ubuntu10.30 qemu-kvm=1:2.5+dfsg-5ubuntu10.30 qemu-block-extra=1:2.5+dfsg-5ubuntu10.30 qemu-system-common=1:2.5+dfsg-5ubuntu10.30
```
Now my USB device is being passed through again to the guest.

The upgrade log showed package upgrades like this:
qemu-system-x86:amd64 (1:2.5+dfsg-5ubuntu10.31, 1:2.5+dfsg-5ubuntu10.32),
qemu-utils:amd64 (1:2.5+dfsg-5ubuntu10.31, 1:2.5+dfsg-5ubuntu10.32),
qemu-kvm:amd64 (1:2.5+dfsg-5ubuntu10.31, 1:2.5+dfsg-5ubuntu10.32),
qemu-block-extra:amd64 (1:2.5+dfsg-5ubuntu10.31, 1:2.5+dfsg-5ubuntu10.32),
qemu-system-common:amd64 (1:2.5+dfsg-5ubuntu10.31, 1:2.5+dfsg-5ubuntu10.32),

Did anything change with the upgrade that I and not finding info on? Could this be a potential bug?

Both host and guest are Ubuntu server 16.04 amd64.

Any info is appreciated,
Mihai

---

