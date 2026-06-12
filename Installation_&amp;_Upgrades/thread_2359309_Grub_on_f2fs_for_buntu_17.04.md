---
title: "Grub on f2fs for *buntu 17.04"
date: 2017-04-22
forum: Installation &amp; Upgrades
---

### Post by alexan on 2017-04-22
Using grub on f2fs works just about fine on 16.10 with this ppa: [https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs](https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs)

but this ppa doesn't look maintained anymore and doesn't work on 17.04. There are any alternative?

I saw the old patch is here: [https://github.com/frap129/grub-f2fs/](https://github.com/frap129/grub-f2fs/)

but I see no instruction on how to apply+compile :/

---

### Post by alexan on 2017-04-24
still looking for this :)

---

### Post by alexan on 2017-05-06
Still looking for possible way to solve this.

---

### Post by LostFarmer on 2017-05-06
[https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs](https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs) posted by you, leads to [https://launchpad.net/ubuntu/+source/grub2/2.02~beta3-4ubuntu2](https://launchpad.net/ubuntu/+source/grub2/2.02~beta3-4ubuntu2)  . that says that the current updated grub in 17.04 that can be updated does have the patch included.  no time to post much

---

### Post by alexan on 2017-05-19
@LostFarmer: No, it doesn't. The current update grub doesn't have that patch.


moving onward (also for those who may run in same issue throug google search), I was able to download the ppa packages with this:

```
wget https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs/+build/12116824/+files/grub-common_2.02~beta3-4ubuntu2~depaulicious~f2fs1_amd64.deb
wget https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs/+build/12116824/+files/grub-pc_2.02~beta3-4ubuntu2~depaulicious~f2fs1_amd64.deb
wget https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs/+build/12116824/+files/grub-pc-bin_2.02~beta3-4ubuntu2~depaulicious~f2fs1_amd64.deb
wget https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs/+build/12116824/+files/grub2_2.02~beta3-4ubuntu2~depaulicious~f2fs1_amd64.deb
wget https://launchpad.net/~depaulicious/+archive/ubuntu/grub2-f2fs/+build/12116824/+files/grub2-common_2.02~beta3-4ubuntu2~depaulicious~f2fs1_amd64.deb
```


...and force the install with sudo dpkg -i *.deb. The (64bit) system with these packages is now able to boot grub from f2fs.

Then, to migrate the system, I do use "cp -a" and chroot to set up everything up: but still seems not work yet; I am yet trying to figure to correct procedure to have grub to boot ubuntu run from, and on, a f2fs partition. I'll post here whenever I'll finally find a solution.

---

