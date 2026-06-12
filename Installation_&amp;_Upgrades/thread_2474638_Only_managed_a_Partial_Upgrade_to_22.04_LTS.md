---
title: "Only managed a Partial Upgrade to 22.04 LTS"
date: 2022-05-04
forum: Installation &amp; Upgrades
---

### Post by iwaddo on 2022-05-04
Hi

I upgraded to 22.04 LTS but it was only partially successful.

Now every time I update I am told that the previous upgrade as only partial and to run the update to address the issue. When I run the upgrade I get the following error.

installed linux-image-5.13.0-39-generic package post-removal script subprocess returned error exit status 1

Any guidance appreciated.

regards

---

### Post by ubfan1 on 2022-05-04
Assuming your are booting on the 22.04 release's 5.15 kernel, (uname -a), in a terminal run the purge on the 5.13 packages and see what complaints arise.  I get all the 5.13 packages and try the purge on all of them:
sudo apt-cache pkgnames |grep 5.13.0-39
sudo apt-get purge `!!`

Or just list them yourself on the purge.  Then, most likely, a file is missing (got deleted manually).  You can make directories, touch missing files, and make the package manager happy, then the purge will succeed, and be done with the errors.

---

### Post by iwaddo on 2022-05-05
Thank you for trying to help, this is the result I got

mycomp@mycomp-Latitude-E7240:~$ sudo apt-cache pkgnames lgrep 5.13.0-39
mycomp@mycomp-Latitude-E7240:~$ sudo apt-get purge '!!'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package !!
E: Couldn't find any package by glob '!!'

Then I tried
mycomp@mycomp-Latitude-E7240:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED
  linux-image-5.13.0-39-generic
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 10.3 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 150367 files and directories currently installed.)
Removing linux-image-5.13.0-39-generic (5.13.0-39.44) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.13.0-39-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.13.0-39-generic (--remove):
 installed linux-image-5.13.0-39-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.13.0-39-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any further guidance appreciated

Regards

---

### Post by bp-qd on 2022-05-05
Hi, I had the same problem and I've found the solution here: 
 [https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken](https://askubuntu.com/questions/1403778/upgrading-to-ubuntu-22-04-causes-libcrypto-errors-apt-dpkg-broken)

```
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb

sudo dpkg -i libssl1.1_1.1.1l-1ubuntu1.2_amd64.deb
```

---

### Post by ubfan1 on 2022-05-05
Try cut and paste for the code I supplied, which contained:  pipe symbol  grep (|grep), not lowercaseL grep (lgrep)

---

### Post by kd6ftr on 2022-05-22
This one worked for me. I ws having the same issue. Once I installed the libssl library file, the apt dist-upgrade command completed successfully.

Thx @bp-qd

---

