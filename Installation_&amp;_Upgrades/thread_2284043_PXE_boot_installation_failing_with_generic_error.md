---
title: "PXE boot installation failing with generic error"
date: 2015-06-26
forum: Installation &amp; Upgrades
---

### Post by Locane on 2015-06-26
Hello, I'm hoping someone can point me to a logfile with more information than the generic error I'm getting.

I have a CentOS-based PXE server that hosts many different operating systems available for installation.  I would like Ubuntu Server 14.04.2 to be one of them.

I download [the most recent ISO]("http://releases.ubuntu.com/14.04.2/ubuntu-14.04.2-server-amd64.iso") from the website and copied its contents to an "iso" directory on the PXE server.  The PXE menu entry looks like this:

```
#TESTING UBUNTU 14.04 INSTALL
# Use the IPAPPEND command and set ksdevice=bootif
LABEL Ubuntu 14
    MENU LABEL UBUNTU 14 TEST
    KERNEL ubuntu/14.04.2/linux
    APPEND initrd=ubuntu/14.04.2/initrd.gz -- ks=http://<INTERNAL URL THAT WORKS>/ks/ubuntu_test.ks ksdevice=bootif biosdevname=0
    IPAPPEND 2

```

Which is mostly copied from a website on [kickstart compatibility and Ubuntu]("https://help.ubuntu.com/community/KickstartCompatibility").

In my kickstart, I have an entry pointed at the files in a directory named "iso", which is exactly what it sounds like:

```
url --url="http://<INTERNAL URL THAT WORKS>/ubuntu/14.04.2/iso/"
```

The installer works great - up until it goes to actually lay down the files.  This is after partitioning and disk detection, and it says "Installation step failed:  Install the system":

[IMG]http://s29.postimg.org/n7xcq7h87/ubuntu_error.jpg[/IMG]

Does anyone have any idea where I can find the logfile that will tell me more specifically what's wrong?  Or has anyone seen this error?

Thanks in advance.

---

