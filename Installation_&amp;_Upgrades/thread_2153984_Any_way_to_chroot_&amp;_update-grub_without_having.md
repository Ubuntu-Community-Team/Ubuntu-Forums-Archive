---
title: "Any way to chroot &amp; update-grub without having grub scan drives outside the chroot?"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by User4519 on 2013-06-13
Hi :)

I'm replacing a dying drive from my father's laptop. I've cloned it to a new one, which is native 4k as opposed to the old one being 512B, so I needed to repartition the target drive to align the partitions correctly.

Thus, I need to update grub on the new drive. I don't have the laptop (my father lives in another region of the country), so I'm trying to chroot into it and just run update-grub from there.

My Ubuntu box has some iSCSI volumes and of course its own Ubuntu installation. All of these are scanned by [FONT=courier new]**update-grub**[/FONT], even though none of them appear if I do a **[FONT=courier new]df[/FONT]** inside the chroot env:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-31-generic
Found initrd image: /boot/initrd.img-3.5.0-31-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdv1
Found Windows Vista (loader) on /dev/sdw1
Found Ubuntu 13.04 (13.04) on /dev/sdw3
Found Windows 7 (loader) on /dev/zd0p1
Found Windows 7 (loader) on /dev/zd64p1
Found Windows Vista (loader) on /dev/zd80p1
done
```

/dev/z* ones are my iSCSI volumes. The /dev/sdv1 is an Acer Windows recovery partition on my father's drive. The actual Linux (Ubuntu 13.04) installation I'm chrooting into is on an iSCSI volume under /dev/zvol/ &#8212; also seen by the prober here as /dev/zd80 (/dev/sdw is the actual drive I'm going to return to my pa), and I find it a bit interesting that [FONT=courier new]**update-grub**[/FONT] finds all partitions outside the chroot env, but not the actual chrooted installation itself, which in that env is /dev/sda3:


```
# df -h
df: &#8216;/run/user&#8217;: No such file or directory
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        19G  4.9G   13G  28% /
```

Am I just doing this wrong, or is there some trick to update grub with scanning just the chrooted drive?

TIA,
Daniel :)

---

### Post by User4519 on 2013-06-13
Okay, as it turns out, I'm not gonna need to do it anyway — the drive booted fine as-is, and it's now in the mail heading for my dad :)

Still curious, though, if anyone knows.

---

