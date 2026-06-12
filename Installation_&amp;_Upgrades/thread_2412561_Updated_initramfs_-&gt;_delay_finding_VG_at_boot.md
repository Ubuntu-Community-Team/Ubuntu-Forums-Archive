---
title: "Updated initramfs -&gt; delay finding VG at boot"
date: 2019-02-14
forum: Installation &amp; Upgrades
---

### Post by alphaniner2 on 2019-02-14
Edit: It seems the tag didn't get added, so I should mention I'm running 18.04 LTS.

-----

I modified and added some files in /etc (modprobe.d/ and udev/rules.d/) that need to be in the initramfs and, after backing up my existing initramfs, ran 'update-initramfs -u'. I had previously modified /etc/default/grub so I get console output during boot.

When I boot using the new initramfs I see a message that my LVM2 VG (which contains LVs for / and /home) is not found, which results in a ~30 sec increase in boot time. Since I backed up my old initrd, I restored it and rebooted several times and confirmed that this issue didn't occur when it is used.

So I reverted all my changes and ran 'update-initramfs -u' again. Once again, the new initramfs resulted in the delay in detecting the VG.

I extracted the good initramfs and the latest initramfs to separate directories using unmkinitramfs and used 'diff -rq' to compare the two. The only difference between the two is main/var/cache/ldconfig/aux-cache. I don't know how to inspect or debug the aux-cache aside from a hexdump, nor how to inject the aux-cache from the good initramfs into a newer one to see if it solves the problem. But it seems to be the only possible cause of the issue I'm having.

Any help would be greatly appreciated.

---

