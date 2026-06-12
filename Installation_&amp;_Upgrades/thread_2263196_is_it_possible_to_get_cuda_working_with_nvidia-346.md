---
title: "is it possible to get cuda working with nvidia-346 driver on gt750ti"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by b-woznicki on 2015-01-30
While working with blender I really need cuda otherwise it like watching the paint dry. Graphics nvidia gt750ti with a driver version 340 works fine with cuda however I am experiencing this annoying screen flickering every now and then compiz does help a bit but is heavy on resources. When i update the driver to 346 from ppa cuda is force removed and when I'm trying to get cuda installed its forcing the nvidia 340 driver to be installed is there a workaround this problem or just have to wait for an update ?

ubuntu
3.13.0-44-generic
gt750ti

thank u in advance for any sugestions.

---

### Post by shriekingpanda on 2015-03-12
On the chance that you're still looking for a solution, I managed to install the nvidia-346 driver alongside cuda from the nvidia ppa. I'm running Linux Mint 17.1 3.13.0-46-generic with a GTX770.

The reason that the cuda package forces the 340 driver is the dependencies of cuda-drivers:
```
Depends: nvidia-340 (>=340.29), nvidia-340-uvm (>=340.29), nvidia-340-dev (>=340.29), nvidia-modprobe (>=340.29), nvidia-settings (>=340.29), libcuda1-340 (>=340.29), nvidia-libopencl1-340 (>=340.29), nvidia-opencl-icd-340 (>=340.29)
```

I got around this by making my own cuda-drivers package with dependencies changed to the 346 equivalents.

```
wget http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1404/x86_64/cuda-drivers_340.29-1_amd64.deb
mkdir cuda-drivers && cd cuda-drivers
dpkg-deb -x ../cuda-drivers_340.29-1_amd64.deb .
dpkg-deb -e ../cuda-drivers_340.29-1_amd64.deb
```

Now edit DEBIAN/control to change everything to the 346 version, except nvidia-modprobe. Note that I also changed the version of the package on the second line.

```

Package: cuda-drivers
Version: 346.47-1
Maintainer: cudatools <cudatools@nvidia.com>
Architecture: amd64
Section: devel
Priority: optional
Installed-Size: 8
Depends: nvidia-346 (>=346.47), nvidia-346-uvm (>=346.47), nvidia-346-dev (>=346.47), nvidia-modprobe (>=340.29), nvidia-settings (>=346.47), libcuda1-346 (>=346.47), nvidia-libopencl1-346 (>=346.47), nvidia-opencl-icd-346 (>=346.47)
Description: CUDA Driver meta-package
 Meta-package containing all the available packages related to the NVIDIA driver.
```

Make the new package:

```
dpkg-deb -b . ../cuda-drivers_346.47-1_amd64.deb
```

Install this package first and then installing cuda from the nvidia ppa should install correctly.

---

