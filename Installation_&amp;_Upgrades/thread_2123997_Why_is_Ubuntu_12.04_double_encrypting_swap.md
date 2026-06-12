---
title: "Why is Ubuntu 12.04 double encrypting swap?"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by p_code on 2013-03-09
Just completed an installation of 12.04 using the standard installer to configure LUKS/LVM full disk encryption and noticed something that doesn't look right...

While verifying that the selected encryption is actually being encrypted I noticed that the 12.04 configuration script is mounting swap on a separate dm-crypt device mapper encrypted mount point, with the underlying device being one of the two virtual LVM partitions that are ALREADY ENCRYPTED INSIDE THE MAIN LUKS/LVM 'full disk' Volume!

For my 'tux_test' test user there the 12.04 installer created FOUR /dev/mapper virtually mapped devices.
(which Looks to be one too many).


"sudo dmsetup ls"  lists 4 mapped devices (pretty sure there should only be three)

sda5_crypt   -  the main LUKS encrypted master volume which contains the master LVM partition.

tux-root  - one of two LVM sub-partitions made available by the LVM device mapper inside sda5_crypt

tux-swap - the second of two sub-partitions made available by the LVM device mapper inside sda5_crypt

cryptswap1 - ANOTHER (second) encryption of swap created by mounting the already encrypted tux-swap in /etc/crypttab using a random session password from /dev/urandom


I understand that the boot partition is NOT encrypted (due to the limitations of the crappy GRUB2 boot loader) but doubly encrypting swap to make up for that is not really necessary.

Even singly encrypted swap makes the system noticeably slower, and doubly encrypting REALLY SLOWS THINGS DOWN.

I'm pretty sure that I just went with the defaults for the LUKS/LVM setup during installation, so I'm not sure how this happened.

Any thoughts how this happened??? :confused:

---

### Post by sudodus on 2013-03-09
Just my 2 cents:

My experience is that when you select 'encrypted home' at the installation and when creating a new user with encrypted home, you also initiate encrypted swap. But if you have a completely encrypted disk, you need not use 'encrypted home'.

Is or was any of your user's home directory encrypted?

---

### Post by p_code on 2013-03-09
> **sudodus said:**
> Just my 2 cents:

My experience is that when you select 'encrypted home' at the installation and when creating a new user with encrypted home, you also initiate encrypted swap. But if you have a completely encrypted disk, you need not use 'encrypted home'.

Is or was any of your user's home directory encrypted?

Yes, it looks like that's the case - I was waffling between user-home-only encryption, and the quasi full-disk-encryption (except root), and must have left both enabled.

I didn't realize that this would cause the simple minded installer to double encrypt swap.

For me, having the home folder double encrypted wasn't much of a performance hit, because I typically don't run large binaries or multimedia files out of home.  So I didn't even notice, but with only a Gig of RAM, when memory gets tight and starts to swap, the slowdown from swap being doubly encrypted is REALLY noticeable.

I have heard that you can't resume from hibernation with a swap partition using a random swap password, but does anyone know if resuming from swap partition embedded within an outer LUKS encrypted LVM main container works?

---

