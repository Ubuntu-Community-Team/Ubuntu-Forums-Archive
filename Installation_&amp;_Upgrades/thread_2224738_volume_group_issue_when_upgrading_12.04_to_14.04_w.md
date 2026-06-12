---
title: "volume group issue when upgrading 12.04 to 14.04 with encrypted lvm"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by bakinsoda on 2014-05-17
Hi everyone,

I've had an encrypted LVM on my ubuntu laptop since version 10.04.  I upgraded from 10.04 to 12.04 in the past, and didn't have any issues; ie, when my computer turns on, it asks me for my passphrase, and i just enter it and the computer loads normally.  I upgraded from 12.04 to 14.04 two weeks ago, and I was unable to boot since.  I've chroot'ed using a live disk, uninstalled mdadm (I don't have RAID, and it appears this was installed as part of the upgrade and was the source of initial errors).  I upgraded all the packages as well, but had an LVM issue.  I re-installed lvm2, and that LVM issue went away.  Now, my issue is that I'm not prompted for a passphrase when I turn on my computer. I followed the second half of [this]("http://www.joh.fi/posts/2014/03/18/install-ubuntu-1310-on-top-of-encrypted-lvm/") post, and modified the files /etc/crypttab, /etc/initramfs-tools/conf.d/cryptroot (new file, was not there before), and /etc/default/grub.  I ran update-grub and update-initramfs.  However, I still don't get a passphrase prompt.

When I boot in recovery from grub, I see the message:

"no volume group found"

I used commands such as

```
vgscan        ## scan for volume groups
vgchange -a y ## activates the volume groups
ls /dev/mapper  ## see what the names are
```

to identify my volume group name (vg01), etc, so I think my modifations of the previous files were correct.

I'm pretty much stumped at this point.  I hope to get help so my computer asks for a passphrase when I turn on the computer, and that things work again.  Thank you in advance.

---

