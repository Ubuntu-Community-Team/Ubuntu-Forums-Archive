---
title: "Nvida driver isntall crash for Tesla K20"
date: 2017-11-14
forum: Installation &amp; Upgrades
---

### Post by wand3r3r on 2017-11-14
I am trying to upgrade my nvidia driver from version 375 to 384 on an Ubuntu 16.04 workstation.  However every time I try I keep getting errors.  Its always seems be that the driver couldn't be configured because a dependency problem

```
dpkg: dependency problems prevent configuration of nvidia-cuda-dev:
 nvidia-cuda-dev depends on libcuinj64-7.5 (= 7.5.18-0ubuntu1); however:
  Package libcuinj64-7.5:amd64 is not configured yet.

dpkg: error processing package nvidia-cuda-dev (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-cuda-doc (7.5.18-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              Setting up nvidia-cuda-gdb (7.5.18-0ubuntu1) ...
dpkg: dependency problems prevent configuration of nvidia-profiler:
 nvidia-profiler depends on libcuinj64-7.5; however:
  Package libcuinj64-7.5:amd64 is not configured yet.

dpkg: error processing package nvidia-profiler (--configure):
 dependency problems - leaving unconfigured
Setting up opencl-headers (2.0~svn32091-2) ...
No apport report written because MaxReports is reached already
                                                              Setting up nvidia-opencl-dev:amd64 (7.5.18-0ubuntu1) ...
dpkg: dependency problems prevent configuration of nvidia-cuda-toolkit:
 nvidia-cuda-toolkit depends on nvidia-profiler (= 7.5.18-0ubuntu1); however:
  Package nvidia-profiler is not configured yet.
 nvidia-cuda-toolkit depends on nvidia-cuda-dev (= 7.5.18-0ubuntu1); however:
  Package nvidia-cuda-dev is not configured yet.

dpkg: error processing package nvidia-cuda-toolkit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-visual-profiler:
 nvidia-visual-profiler depends on nvidia-profiler (= 7.5.18-0ubuntu1); however:
  Package nvidia-profiler is not configured yet.

dpkg: error processing package nvidia-visual-profiler (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
       Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for initramfs-tools (0.122ubuntu8.9) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-98-generic
Errors were encountered while processing:       
 nvidia-384
 libcuda1-384
 nvidia-384-dev
 nvidia-opencl-icd-384
 bbswitch-dkms
 nvidia-prime
 libcuinj64-7.5:amd64
 nvidia-cuda-dev
 nvidia-profiler
 nvidia-cuda-toolkit
 nvidia-visual-profiler
```


I've tried purging and reinstalling using both Ubuntu repositories and downloads from nvidia's website.  No luck.  Any help is appreciated.

---

