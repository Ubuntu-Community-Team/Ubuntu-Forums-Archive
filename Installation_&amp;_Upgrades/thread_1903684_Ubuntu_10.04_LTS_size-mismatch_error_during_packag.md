---
title: "Ubuntu 10.04 LTS size-mismatch error during package installation"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by blacFerrari on 2012-01-03
Hi,
I have installed ubuntu10.04 LTS 64-bit version two weeks back and tried to install packages using apt. Whenever I tried, I got the same error saying size mismatch. I am connected to internet via college intranet and have configured proxy settings in Preference>Network Proxy. Please help.

I was trying to install openfoam.
########
The detailed error info:
...
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libi/libice/libice-dev_1.0.6-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libi/libice/libice-dev_1.0.6-1_amd64.deb) Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.5-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxau/libxau-dev_1.0.5-1_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.3-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxdmcp/libxdmcp-dev_1.0.3-1_amd64.deb) Size mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.0-2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-input/x11proto-input-dev_2.0-2_all.deb) Size mismatch
.
.
.
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsm/libsm-dev_1.1.1-1_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxt/libxt-dev_1.0.7-1_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/universe/libi/libibverbs/libibverbs1_1.1.3-2ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libi/libibverbs/libibverbs1_1.1.3-2ubuntu1_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/universe/o/openmpi/libopenmpi1.3_1.4.1-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/openmpi/libopenmpi1.3_1.4.1-2_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/universe/s/scotch/libscotch-5.1_5.1.6.dfsg-3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/s/scotch/libscotch-5.1_5.1.6.dfsg-3_amd64.deb) Size mismatch
Failed to fetch  [http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-dev_2.20.1-3ubuntu7.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-dev_2.20.1-3ubuntu7.1_amd64.deb) Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
############

---

