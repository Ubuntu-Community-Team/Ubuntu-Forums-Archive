---
title: "Missing kernel package preventing Hardy network install"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by fiendish on 2011-04-14
Hey everyone,

I was hoping for some assistance, I am not sure exactly how to go about troubleshooting this issue.

I have an apt-mirror mirror of ubuntu archives syncing with archive us.archive.ubuntu.com. I have a tftp server, etc for booting via PXE and installing ubuntu over the network (using the local mirror for packages). All of the Ubuntu versions install without any problems except Hardy. I have lucid, maverick and karmic all installing fine.

When I try to install hardy, I get the following error message:

```

[!!] Download installer components
No kernel modules were found. This is probably due to a mismatch between the kernel
 used by this version of the installer and the kernel version available in the archive. 

If you're installing from a mirror, you can work around this problem by choosing to 
install a different version of ubuntu. The install will probably fail to work, if you continue 
without kernel modules.
```In the syslog, the last few entries are as follows:

```
anna[6995]: wget:
anna[6995]: security.ubuntu.com
anna[6995]: :
anna[6995]: Host name lookup failure
anna[6995]: WARNING **: No packages for kernel in archive
```Why is it looking for security.ubuntu.com anyway? I am using a local mirror and do not have updates set to automatic. I do not see why public network access would be required for this install to finish. I should be able to do this all over the private network using the local mirror.

I am grabbing the netboot installer files from [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/) and my mirror is synced daily. I can't understand why all other versions work except hardy. I have tried all netboot installer files (older ones) from us.archive.ubuntu.com but run into the exact same error message every time.

Can anyone else replicate this issue with installing hardy over the network using a local mirror set up with apt-mirror? What files can I look at and compare with the working versions to find out whats missing or incorrect? Let me know if I can provide you with any more details like the preseed file I am using and/or the syslinux kernel parameters.

Regards,
fiendish

---

### Post by mörgæs on 2011-04-14
Hi, welcome to the fora.

Are you aware that support for 8.04 (desktop) is running out in middle of May?

---

### Post by fiendish on 2011-04-14
Yes, I am aware. Just trying to get all OS versions we offer installed over the network and got stuck on 8.04.

Anyway I got it to work with the following installer images:
[http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/20070308ubuntu38/images/netboot/ubuntu-installer/i386/](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/20070308ubuntu38/images/netboot/ubuntu-installer/i386/)

The oldest installer had the same kernel as the packages list in apt-mirror. Not sure why apt-mirror has an outdated packages list for hardy...

Thanks,
fiendish

---

### Post by mörgæs on 2011-04-14
Good. Please mark the thread 'solved'.

---

