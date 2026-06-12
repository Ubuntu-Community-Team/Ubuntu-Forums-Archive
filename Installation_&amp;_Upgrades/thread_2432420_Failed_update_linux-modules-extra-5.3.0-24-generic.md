---
title: "Failed update: linux-modules-extra-5.3.0-24-generic_5.3.0-24"
date: 2019-12-02
forum: Installation &amp; Upgrades
---

### Post by yaminb on 2019-12-02
I got an update this morning for ubuntu 19.10 and it has failed.
I can't seem to resolve it as I did in the past. Can anyone assist?

It appears to be struggling to install linux-modules-extra-5.3.0-24-generic_5.3.0-24.
The 'unable to open '/lib/modules/5.3.0-24-generic/kernel/drivers/tty/ipwireless/ipw' error part seems to change each time I run it.

```

sudo apt install --reinstall linux-modules-extra-5.3.0-24-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.3.0-19 linux-headers-5.3.0-19-generic
  linux-image-5.3.0-19-generic linux-image-5.3.0-22-generic
  linux-modules-5.3.0-19-generic linux-modules-5.3.0-22-generic
  linux-modules-extra-5.3.0-19-generic
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  linux-modules-extra-5.3.0-24-generic
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0 B/38.1 MB of archives.
After this operation, 188 MB of additional disk space will be used.
(Reading database ... 238411 files and directories currently installed.)
Preparing to unpack .../linux-modules-extra-5.3.0-24-generic_5.3.0-24.26_amd64.d
eb ...
Unpacking linux-modules-extra-5.3.0-24-generic (5.3.0-24.26) ...
dpkg: error processing archive /var/cache/apt/archives/linux-modules-extra-5.3.0
-24-generic_5.3.0-24.26_amd64.deb (--unpack):
 unable to open '/lib/modules/5.3.0-24-generic/kernel/drivers/tty/ipwireless/ipw
ireless.ko.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-extra-5.3.0-24-generic_5.3.0-24.26_amd64.
deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I have tried the following as well:
> 
sudo apt --fix-broken install
sudo apt autoremove
sudo apt autoclean
sudo apt-get update &#8211;fix-missing
sudo dpkg --configure -a
sudo apt-get install -f



Edit: I'm afraid to reboot as this could stop me from logging in or something.

Any ideas?

---

### Post by yaminb on 2019-12-02
I just tried a reboot to see if that solved it, it didn't

But I can get into advanced Ubuntu boot options and can boot into the 5.3.0-23 kernel, so that's a workaround for now.

---

### Post by yaminb on 2019-12-02
Not sure what fixed it. I just kept doing the same steps of reinstalling the headers. But eventually it all worked.
I was in the .23 kernel when doing the work.

---

