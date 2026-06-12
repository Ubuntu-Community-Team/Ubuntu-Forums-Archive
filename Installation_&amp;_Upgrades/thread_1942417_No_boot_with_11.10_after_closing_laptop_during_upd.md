---
title: "No boot with 11.10 after closing laptop during update"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by Batnastard on 2012-03-17
Hi all,
My wife thought my netbook was asleep during an update and closed the lid - now it won't boot. If I run recovery mode I get kernel panic, failed to mount root fs. I can boot to a previous version in a shell, and fsck gives a code 6. I tried running it with -r but same thing. I tried the nomodset trick and got just the blinking cursor. It's been a while since I've done this sort of thing but I'm guessing the kernel didn't build or get installed properly. 

It's a netbook, so I can't boot from CD, but I could try a thumb drive. Is there a way to complete/rerun the install from a shell? Or, is there anything else I could try?

Thanks!

---

### Post by 2F4U on 2012-03-17
If you are able to boot at least in a console you may be able to finish the upgrade:

[http://www.opensourcetips.org/linux/ubuntu/550-how-to-recover-ubuntu-after-a-partial-upgrade](http://www.opensourcetips.org/linux/ubuntu/550-how-to-recover-ubuntu-after-a-partial-upgrade)

---

### Post by Batnastard on 2012-03-17
Thanks! I don't think I have dpkg-reconfigure, but I ran dpkg --configure -a and it ran for a bit but crashed on the firewall. I booted it up and it's definitely getting farther, but it hangs on mount.nfs and mountall.

Ah, but now I can boot into recovery mode on the new kernel. Running dpkg-reconfigure now, we'll see. Thanks again!

---

### Post by Batnastard on 2012-03-17
Ok, when I run dpkg-reconfigure it says:

Update-rc.d: warning: [stuff] missing LSB support

Since the script you are  attempting to invoke has been converted to an Upstart job you may also use the start(8) utility etc.

Does this several times and finishes. Reboot is same as before. Any ideas?

---

