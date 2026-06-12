---
title: "eth0 After Upgrading Kernel"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by ajayre on 2007-10-27
I upgraded my kernel to 2.6.23 from kernel.org. Everything works except ethernet. The syslog looks fine. Comparing it to Gutsy's 2.6.22-14 bootup in syslog, the exact same driver (Davicom DM9xxx 1.36.4) is loaded. Here is what I did:

```
sudo apt-get update
sudo apt-get install build-essential libncurses5-dev kernel-package
cd /usr/src
wget -c http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.23.tar.gz
tar xzvf linux-2.6.23.tar.gz
mv linux-2.6.23 linux-vanilla-2.6.23
ln -s linux-vanilla-2.6.23 linux
cd linux
cp /boot/config-2.6.22-14-generic .config
sudo make-kpkg --initrd --revision=1 --append-to-version=-test kernel_image kernel_headers
cd ..
sudo dpkg -i linux-image-2.6.23-test_1_i386.deb

```

Any ideas? What can I do to debug this further? I get the exact same problem with version 2.6.22.9 from kernel.org. This is driving me nuts! Thanks. :)

Andy

---

