---
title: "grub configuration for 9.10"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by akashiraffee on 2009-12-02
When I installed, I choose not to install the bootloader because I already have one.  So I added this to my existing grub.conf based on what I found in the ubuntu partition:

```

title ubuntu (original) 
        root (hd0,4)
        kernel /boot/vmlinuz-2.6.31-14-generic ro root=/dev/sda5
        initrd /boot/initrd.img-2.6.31-14-generic

```
There was no grub.config there to look at, I guess because I didn't install it.

However, this does not work, I just get a perpetual black screen.  AFAICT, hd(0,4) should be /dev/sda5 (first logical partition on an extended partition) altho I don't normally boot from (or use) extended partitions.  But I don't think that's the issue.

Can someone post the relevant lines from their grub.conf for 9.10?

---

### Post by phillw on 2009-12-02
If you're on 9.10 - and you didn't move to Grub2 - you're running something very different -- the info on grub2 is over here --> [http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305](http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305)

If you have a dual boot system with Grub Legacy or Grub2, head this way --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

But, you'd be better off moving over to Grub2, as that is the supported one for 9.10 & you will spend your life having to tell people you are running a different boot-loader to the default, which we will have little or experience of !!

Regards,

Phill.

---

