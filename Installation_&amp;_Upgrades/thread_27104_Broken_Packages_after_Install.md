---
title: "Broken Packages after Install"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by ate50eggs on 2005-04-14
noob question:

I just installed Hoary on my machine. At the end of the install it told me that some packages were broken and promted me to use Aptitude to try re-installing them.

I'm not exactly sure how to use Aptitude, but trial and error hasn't gotten me very far. when I try to install selected packages, i get ton of errors and eventually it dies. I think a lot of them say something like "device is full." Is it possible my / partition is too small? (it's 100mb)

Also, Symantic doesn't work. I guess it needs some packages that aren't there.

---

### Post by Gary Powers on 2005-04-14
I've done several Hoary installs, "eggs", and it does sound like maybe you got a bad one.  Did you run MD%SUM on the download to make sure it was OK?

Gary

---

### Post by speedman on 2005-04-14
df -h will tell you how much space is free on each of your partitions.


Regards,

SM

---

### Post by ate50eggs on 2005-04-14
it was downloaded with bittorrent. doesn't that checksum automatically?


the sum I got with WinMd5Sum:
f6b3f164c99761234858a4d2c12d0840

not sure where to get the correct value

---

### Post by speedman on 2005-04-14
The md5sum you posted matches the entry for the i386 ISO from here:

[http://us.releases.ubuntu.com/releases/5.04/MD5SUMS](http://us.releases.ubuntu.com/releases/5.04/MD5SUMS)

Based on your previous comments it sounds like your filesystem is not laid out properly and that you're out of space on the root partition without having appropriate partitions set up for /usr and/or /var.


Regards,

SM


EDIT - fixed a typo.

---

### Post by ate50eggs on 2005-04-14
ok so the answer to that one was right in front of me

f6b3f164c99761234858a4d2c12d0840 from sumcheck
f6b3f164c99761234858a4d2c12d0840 from ubuntu US mirror 

looks right to me

---

### Post by ate50eggs on 2005-04-14
[QUOTE=speedman]
Based on your previous comments it sounds like your filesystem is not laid out properly and that you're out of space on the root partition without having appropriate partitions set up for /usr and/or /var.
[/QUOTE]


Here are my partitions from hitting df -h


                    size      used   available  mount
/dev/hdc1.....89M.....89M.......0............./
tmpfs............237M....0..........237M......./dev/shm
/dev/hdc9.....20G......33M......19g........./home
/dev/hdc6.....897M....8.1M......841M....../tmp
/dev/hdc8.....4.6G.....1.1G......3.3G....... /usr
/dev/hdc7.....4.6G.....553M.....3.9G......../var
/dev..............89M......89M.......0............/.dev
none.............5M........2.8........2.3M......./dev

I'm using ext3

looks like / *is* full. re-partition? any guess as to what wrong with my filesystem? (btw feel free to comment on my hd space allocation. I only had a vague idea of how much space each of these mounts would need)

---

### Post by speedman on 2005-04-14
Yes, your root partition has no free space left.  You will either have to resize the partition, or reinstall with more space allocated for /.

There is a benefit to having /home, /usr and /var on their own because it makes it much faster to recover the root filesystem in the event of corruption, but for most desktop systems a swap partition and single root partition will usually suffice.  I suppose there is also a slight benefit to having /home on it's own for upgrade purposes when using RPM based distros, but "apt-get dist-upgrade" is so powerful in Debian (and Ubuntu by extension) that it is largely an unnecessary option.

If you wish to keep /home, /usr and /var seperate you should probably set aside 500MB to 1GB for /, ~2GB for /var, 5-10GB for /usr and the balance for /home.


Regards,

SM

---

### Post by ate50eggs on 2005-04-15
it works. speedman is my hero.

---

