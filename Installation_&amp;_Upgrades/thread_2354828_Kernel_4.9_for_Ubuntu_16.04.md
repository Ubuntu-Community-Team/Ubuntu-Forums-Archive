---
title: "Kernel 4.9 for Ubuntu 16.04"
date: 2017-03-07
forum: Installation &amp; Upgrades
---

### Post by deepakdeshp on 2017-03-07
Hello, Ubuntu 16.04 desktop on AMD A8 processor. There are some changes to support AMD in Kernel 4.9. Can you guide regarding this please?
Is 4.9 an LTS version?

---

### Post by deadflowr on 2017-03-07
> **deepakdeshp said:**
> Hello, Ubuntu 16.04 desktop on AMD A8 processor. There are some changes to support AMD in Kernel 4.9. Can you guide regarding this please?
Is 4.9 an LTS version?

You would need to grab a mainline kernel.
It's long term support in terms of the linux developers, but not long term support in terms of Ubuntu.
Ubuntu mainline builds explained here: [https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

---

### Post by deepakdeshp on 2017-03-07
Thank you, Is there any way to verify that the Kernel code is correct? I had downloaded it from [http://ubuntuhandbook.org/index.php/2016/12/install-linux-kernel-4-9-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2016/12/install-linux-kernel-4-9-ubuntu-linux-mint/) . The 3 .deb packages for 64 bits.

---

### Post by deadflowr on 2017-03-07
> **deepakdeshp said:**
> Thank you, Is there any way to verify that the Kernel code is correct? I had downloaded it from [http://ubuntuhandbook.org/index.php/2016/12/install-linux-kernel-4-9-ubuntu-linux-mint/](http://ubuntuhandbook.org/index.php/2016/12/install-linux-kernel-4-9-ubuntu-linux-mint/) . The 3 .deb packages for 64 bits.

The link you grabbed the deb files from also lists the checksums.

What you can do for the simpler way is run
```
sha256sum /path/to/deb/file.deb
```
changing /path/to/dev/file.deb to the path where you downloaded the files.
then compare the output to what is listed.

A more advanced method is to verify using the gpg key method,
The gist of howto do that here:
[https://help.ubuntu.com/community/VerifyIsoHowto]("https://help.ubuntu.com/community/VerifyIsoHowto")

---

### Post by deepakdeshp on 2017-03-09
Thank you. It gave me some error like vmware machine not starting, hence I uninstalled it.

---

