---
title: "Ubuntu 10.04 will include -openvz kernels?"
date: 2009-11-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by narcisgarcia on 2009-11-30
The last LTS server version included these packages already compiled:
linux-image-openvz linux-openvz linux-restricted-modules-openvz

Note that OpenVZ is the virtualization technology supported in all computers.

---

### Post by Dorowan on 2010-03-24
Just [some hours ago]("http://git.openvz.org/?p=linux-2.6.32-openvz;a=log;h=2.6.32-afanasyev") OpenVZ released a [2.6.32 Kernel with OpenVZ support]("http://wiki.openvz.org/Download/kernel/2.6.32/2.6.32-afanasyev.1"). I think the release is to late for the official Ubuntu sources but there is a good chance that OpenVZ will provide the kernel in their own repository. At the moment the only prebuild packages are for rpm-based distros. Another chance would be a launchpad projekt for the kernel. We will see.

---

### Post by narcisgarcia on 2010-03-24
As commented by Dorowan OpenVZ released a 2.6.32 Kernel with OpenVZ support. At the moment the only prebuild packages are for rpm-based distros, but server administrators need a reliable way to upgrade our LTS host servers, and LXC sowftare+docummentation is not ready for OpenVZ migration.

---

