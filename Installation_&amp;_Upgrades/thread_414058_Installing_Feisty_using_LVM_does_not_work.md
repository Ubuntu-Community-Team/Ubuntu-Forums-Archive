---
title: "Installing Feisty using LVM does not work"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by xlnt01 on 2007-04-19
What the hell happened with the final release of feisty?
Now I'm not able to install it with the alternate cd using LVM or even worse reinstall my computer and reuse my LVM partitions. When I get to the part of configuring LVM in partman it hungs.

This is not good.
We are going to need a new install cd with a working LVM install.

Does anybody else have some input on the subject?

---

### Post by linuxer_de on 2007-04-19
yep, same here.

feisty final does now detect software raid (this was broken until beta) but now freezes on configuring lvm.

error msg: 
invalid argument, /dev/md1p1...

then after choosing ignore:
logical volume group found, activate?
yes -> partman dies

---

### Post by 98xj on 2007-04-19
lvm looked hung for a long time for me ...but it did finish, lvm setup being slow is in the release notes

---

### Post by raidensix on 2007-04-19
That's correct. I must have waited more than 30mins before it activated the existing LVM it found on my hard drive.

---

### Post by linuxer_de on 2007-04-20
ok waiting does the trick but after 5% of installing partman fails.

On the console I get the following error:

"mdadm depends on udev"

As I said previously, in the partitioning menu I get:

"Error informing the kernel about modifications to /dev/md1p1 -- Inv. argument"

---

### Post by wgrant on 2007-04-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The mdadm+LVM issue is probably different, but the hang is the bug filed at [https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623](https://bugs.launchpad.net/ubuntu/+source/devmapper/+bug/105623). It is mentioned in the release notes that you just have to wait, and there is no fix at this time.

---

