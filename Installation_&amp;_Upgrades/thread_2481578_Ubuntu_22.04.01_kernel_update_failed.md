---
title: "Ubuntu 22.04.01 kernel update failed"
date: 2022-12-03
forum: Installation &amp; Upgrades
---

### Post by Kova78 on 2022-12-03
Hi all,

I just want to share what happened to me yesterday on Ubuntu 22.04.01 (desktop)
"Software Update" installed this kernel version: "**linux-image-5.15.0-1025-oracle**" on top of "**linux-image-5.15.0-56-generic**".

This update messed up everything (especially the graphic card and the Nvidia drivers).
Does someone know why Software update tried to install "**0-1025-oracle**"?

Also I have a question about the kernel versions that are downloaded and installed on my system
These are the kernels that were installed recently:
```
dpkg -l | grep linux-image
rc  linux-image-5.15.0-50-generic                 5.15.0-50.56                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-52-generic                 5.15.0-52.58                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-52-lowlatency              5.15.0-52.58                               amd64        Signed kernel image lowlatency
rc  linux-image-5.15.0-53-generic                 5.15.0-53.59                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-53-lowlatency              5.15.0-53.59                               amd64        Signed kernel image lowlatency
ii  linux-image-5.15.0-56-generic                 5.15.0-56.62                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-56-lowlatency              5.15.0-56.62                               amd64        Signed kernel image lowlatency
ii  linux-image-generic                           5.15.0.56.54                               amd64        Generic Linux kernel image

```

I noticed that sometimes, after the update, Ubuntu runs with the "lowlatency" version instead of "generic".
Why? What's the difference?

Thank you

---

### Post by philhughes on 2022-12-03
There are a few reports of this in the Ubuntu subreddit. Seems to be associated with the latest nvidia drivers. Likely a bug.

---

### Post by ctheroux on 2022-12-04
Hi, I had the same issue.  the Oracle, Intel and lowlatency prevents my machine from booting.

---

### Post by Herman on 2022-12-04
I got that update too and was back to only one monitor and 1020 x 765 resolution for a while and no sound. 
Installing the matching kernel headers and kernel modules extra fixed things again for me.
I'm using 22.04.1 Jammy Jellyfish and I have been using LTS releases for years now and Ubuntu has been great for me until this little hiccup.
I'm curious too about the different kernel names.
```
uname -r
5.15.0-1025-oracle
```

```
dpkg -l | grep linux-image
ii  linux-image-5.15.0-1021-intel-iotg              5.15.0-1021.26                             amd64        Signed kernel image intel-iotg
ii  linux-image-5.15.0-1025-oracle                  5.15.0-1025.31                             amd64        Signed kernel image oracle
rc  linux-image-5.15.0-43-generic                   5.15.0-43.46                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-47-generic                   5.15.0-47.51                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-48-generic                   5.15.0-48.54                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-50-generic                   5.15.0-50.56                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-52-generic                   5.15.0-52.58                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-53-generic                   5.15.0-53.59                               amd64        Signed kernel image generic
ii  linux-image-5.15.0-56-generic                   5.15.0-56.62                               amd64        Signed kernel image generic
rc  linux-image-5.15.0-56-lowlatency                5.15.0-56.62                               amd64        Signed kernel image lowlatency
ii  linux-image-generic                             5.15.0.56.54                               amd64        Generic Linux kernel image

```

---

