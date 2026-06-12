---
title: "Ububtu 8.04  gcc upgrade breaks VMWare"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by unixpaul on 2008-10-31
Hello,
I am on 8.04. I had VMware server running to keep my windows
system alive. But since applying software updates in Ubuntu, my
gcc has changed from 4.2.3 to 4.2.4 and VMware won't start. It
wants to recompile. Ugh. I know I could link gcc to a different 
major version number like  gcc --> gcc-4.1.0   but this change
is only in a minor version number of gcc.  

Is there a way to get back to gcc 4.2.3 ?

UnixPaul

---

### Post by slakkie on 2008-10-31
I think you just need to download some of the kernel headers files and run something like this (old script of mine to update VMWare server after kernel updates):

```

#!/usr/bin/env zsh

# Installing kernel header files
echo "Installing kernel header files"
sudo aptitude install linux-headers-`uname -r`

echo "Making sure vmware is happy, so lets reconfigure it, accept the defaults please"
sudo /path/to/vmware-config.pl

```

---

### Post by unixpaul on 2008-10-31
Thanks I installed kernel-headers, and it recompiled the module.
Seems to be working now.

---

