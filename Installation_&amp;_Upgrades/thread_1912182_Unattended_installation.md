---
title: "Unattended installation"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by wembleyford on 2012-01-20
I'm trying to get create an unattended installation of Ubuntu 10.04. 

What I wan to achieve is a bootable CDROM which uses a preseed file stored on our local webservers. 

I've tried following the documentation here:
 [https://help.ubuntu.com/community/Installation/UnattendedCD](https://help.ubuntu.com/community/Installation/UnattendedCD)

But following these instructions left me with a boot option which stopped with a "Gave up waiting for a root device"

Looking at the default text.cfg entries, I tried adding 'boot=casper' which at least booted into the desktop, but with no sign the preseed file was being used. 

My text.cfg now starts with:

```
default unattended
label unattended
  menu label ^Unattended Installation
  kernel /casper/vmlinuz
  append preseed/url=http://myserver/url/ubuntu-10.04.seed debian-installer/locale=en_GB netcfg/choose_interface=auto initrd=/casper/initrd.lz priority=critical --
```

As I said, this doesn't boot. If I add 'boot=casper' it appears to boot the liveCD but nothing else.

Not sure what to do at this point, or what part of the documentation I've mis-read - can someone please advise?

Thanks
Dave

---

