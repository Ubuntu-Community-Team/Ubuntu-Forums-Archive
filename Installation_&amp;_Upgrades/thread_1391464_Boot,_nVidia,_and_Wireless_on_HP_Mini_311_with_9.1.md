---
title: "Boot, nVidia, and Wireless on HP Mini 311 with 9.10 Karmic"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by amaroKer on 2010-01-26
So here's how I got 9.10 to work on my HP Mini 311.  I followed instructions [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479597"), [here]("http://ubuntuforums.org/showthread.php?t=1287896&page=10"), and [here]("http://www.debuntu.org/how-to-customize-your-ubuntu-live-cd") to get 'er dun.  Hope this works for you.

My LiveUSB (didn't try unetbootin) would only give me black screen after grub until i selected noapic and nolapic from the F6 menu.  Sweet, now we can install.

After install, go for a restart and BAM another black screen.  Here's how I got around that.  (Thanks, bigup from launchpad)

1) Boot into Live mode or stay there after install I guess.

2) Mount Ubuntu partition through Places menu

3) Into terminal ```
sudo chroot /media/*yourdisk*
```

4) Blacklist the culprit drivers with (separately) ```
echo "blacklist b43" > /etc/modprobe.d/blacklist.conf
echo "blacklist ssd" > /etc/modprobe.d/blacklist.conf
echo "blacklist b43-pci-bridge" > /etc/modprobe.d/blacklist.conf
``` to add those lines to that file (not so elegant but...)

5) Mount /proc and /sys with ```
mount -t proc none /proc/
mount -t sysfs none /sys/
```

6) Then run ```
update-initramfs -u
```
If you have errors (I did), go ```
mv /dev/null /dev/null.old
update-initramfs -u
mv /dev/null.old /dev/null
```

And there you have it.  I actually managed to get Ubuntu to boot after I installed and did an update before I got to step one.  I don't think that should change anything, though.  I hope this helps.

---

### Post by laloruelas on 2010-02-07
Thanks for the useful info, now i can boot my netbook.

---

### Post by istoff on 2010-02-12
Just a possible correction which worked for me.

Instead of blacklisting ssd, I blacklisted ssb instead.

I got this after reading the blacklist.conf that ships on the iso of the Mint8 livecd.

Blacklisting ssd did not work for me.

I *was* able to activate wireless using the proprietary hardware drivers tool.

HTH

---

### Post by doctorscholz on 2013-02-20
Thanks for the very useful writeup! This was key for me getting my 311 up and running.

---

