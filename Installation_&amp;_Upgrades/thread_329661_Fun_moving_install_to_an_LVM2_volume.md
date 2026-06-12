---
title: "Fun moving install to an LVM2 volume"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by regeya on 2007-01-02
Not a support request, not a howto (not by a long shot ;-) ) but rather documenting the fun I had moving a standard install over to a new drive set up with an LVM2 volume destined to be the root partition.

So anyway, I had a bit of cash after Christmas, enough to buy a 250GB drive that was on an awesome sale.  While I was contemplating doing a cp -ax off my old 100GB drive onto the new, I thought two things:  First, waiting for a cp -ax to finish sucks, and second, it'd be nice to pool the 100GB drive into the available space.  Rather than just making the drive /opt or /home or whatever, I wanted a big ol' / partition and pool 'em together.  LVM2 it is, eh?  And later on, if I get another drive, I can add it to the pool and/or remove a drive or drives from the pool.  Very slick.

Setting up LVM2 isn't hard but it's beyond the scope of this discussion, so I'll refer you to the [LVM HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO/").  I set up a group named 'ubuntu' and a volume named 'root', so in /etc/fstab, that'd be:

```

/dev/ubuntu/root / ext3 defaults,errors=remount-ro,noatime,data=writeback,commit=600 0 1

```

Of course I also set up a swap partition and a separate ext2 partition for /boot.

So, I did this all from the install LiveCD for a minimum of fuss.  The setup went great, the copying went fine, I set up /etc/fstab and rebooted...

...nothing.  Not even an error message.

After much searching I found a suggestion that initramfs-tools' support for lvm2 might be b0rked and to give yaird a try.  So I booted the LiveCD again, fired up a Terminal, and typed the following to get a good-enough chroot env*:

```

mkdir /media/new
mount -t ext3 /dev/ubuntu/root /media/new
mount -t ext2 /dev/hda2 /media/new/boot
for i in "proc" "sys" dev"
do
mount -o bind /$i /media/new/$i
done
chroot /media/new /bin/bash

```

*I left out some trial-and-error stuff.

So I ran 'apt-get install yaird', read the manpage, removed my old initrd, and added this line to /etc/yaird/Default.cfg:

```

                MOUNTDEV "/dev/ubuntu/root" "/mnt"

```

then I ran yaird:

```
yaird -o /boot/initrd.img-2.6.17.7-ck1 2.6.17.7-ck1
```

and rebooted.

It worked...sort of.  I'd added /boot into the /fstab and had gotten an error message that /dev/hda2 was mounted or busy, and that swap couldn't be turned on.  Swap turned out to be an invalid /etc/fstab entry, but upon further inspection a script on the initrd was trying to load EVMS stuff which needed /lib/libgcc_s.so.1.  So okay, fine, I booted the CD, set up my chroot env again (I really should have saved a script on a USB disk or something) and edited /etc/yaird/Template.cfg, this time adding this line to the TEMPLATE evms_activate section:

```

FILE "/lib/libgcc_s.so.1"

```

removed the old initrd, reran yaird, and rebooted.  Everything's golden.

Once again I boot the LiveCD, rewrote the partition table on my old drive, set it up for LVM2, added that space to my root volume, and resized the root filesystem.  Again, beyond the scope of this discussion, check the HOWTO listed above.

Mounted it...excellent.  Reboot...

...more error messages.  This time evms tells me that the LVM volume 'root' couldn't be found.

Uh...excellent.

Boot the LiveCD, verify it's OK.  Then on a wild hunch, I tried running evmsn, which cheerfully pointed out that the volume settings for root were inconsistent and cheerfully offered to fix the problem.  Great!  Rebooted off the CD again **sigh** and verified that everything was in working order.  Wonderful!  Reboot, and...

...all sorts of missing evms libs.  Apparently I added a new dependency wrinkle when I allowed evmsn to set things right.  Yippie.

So once again I booted off the LiveCD ****sigh****, set up my chroot env again, and edited the TEMPLATE evms_activate section of /etc/yaird/Templates.cfg again, this time editing and adding:

```

TREE "/lib/evms/"
FILE "/lib/libevms*"

```

and did the delete initrd/run yaird two-step again.

Et viola!  **Finally** I have a system working right.

Now...anyone have any idea what's b0rked in initramfs-tools? ](*,)

OTOH...

```

/dev/ubuntu/root      317G   67G  238G  22% /

```

:D

---

