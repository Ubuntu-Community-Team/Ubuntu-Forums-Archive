---
title: "multilib conflict on Ubuntu"
date: 2016-09-22
forum: Installation &amp; Upgrades
---

### Post by ele2 on 2016-09-22
Hi,
i am using Ubuntu 10.04 (i cannot update, required by toolchain)

I have a 32 bit quest Ubuntu in VirtualBox and i am trying to install multilib:

```
sudo dpkg -i gcc-4.4-multilib_4.4.3-4ubuntu5_i386.deb
```

Which results in the following:
```
gcc-4.4-multilib depends on libc6-dev-amd64 (>= 2.5); however:
  Package libc6-dev-amd64 is not installed.

```

But i cannot install libc6-dev-amd64:
```
sudo dpkg -i libc6-dev-amd64_2.19-0ubuntu6.9_i386.deb 
dpkg: regarding libc6-dev-amd64_2.19-0ubuntu6.9_i386.deb containing libc6-dev-amd64:
 libc6-dev-amd64 conflicts with libc6-dev (<< 2.13-14)
  libc6-dev (version 2.11.1-0ubuntu7.8) is present and installed.

```

Is is possible to resolve this situation somehow? It seems that the amd64 version of libc cannot coexist with normal libc. 

Thanks

---

### Post by steeldriver on 2016-09-22
Isn't it telling you that libc6-dev-amd64_**2.19**-0ubuntu6.9 is too new for your system?

You should probably be trying to install the appropriate deb for lucid (maybe 2.11.1-0ubuntu7.21 ?)

Or - better - instead of trying to install deb packages directly, change your apt sources to pick up the old-releases repo as described here: 

[How to install software or upgrade from an old unsupported release?]("http://askubuntu.com/a/91821/178692")

so that you can install multilib with all the necessary dependencies using apt-get.

---

### Post by ele2 on 2016-09-22
Thanks for the help, i did not know about the old-releases repos. I was quickly able to resolve the issue with apt-get which found all the proper dependencies.

---

