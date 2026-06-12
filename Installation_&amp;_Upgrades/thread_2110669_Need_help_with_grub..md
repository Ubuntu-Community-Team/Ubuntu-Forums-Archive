---
title: "Need help with grub."
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by dlw on 2013-01-30
Need to change boot from sda to sdb.
boot-repair returns this:
Please write on a paper the following URL:
[http://paste.ubuntu.com/1591894/](http://paste.ubuntu.com/1591894/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

No change has been performed on your computer. See you soon!

---

### Post by oldfred on 2013-01-31
Did you copy some files? Your fstab in sda1 looks to be the same as the new install in sdb5, so are you actually booting the new install from the old?

If you can boot new install.

       sudo grub-install /dev/sdb
    
But I might do this as it does a few more things.

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

    
Does system boot ok with new install in sdb? Some BIOS (or grub) do not boot from very large / (root) partitions. Generally better to have a smaller / of about 25GB and separate /home.

---

