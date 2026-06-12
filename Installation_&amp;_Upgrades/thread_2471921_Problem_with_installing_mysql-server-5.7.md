---
title: "Problem with installing mysql-server-5.7"
date: 2022-02-12
forum: Installation &amp; Upgrades
---

### Post by zak100 on 2022-02-12
Hi,
I am trying to install mysql server on ubuntu 18.04. I am getting following error:

```
$ sudo apt dist-upgrade
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-10-1 cuda-command-line-tools-11-2 cuda-compiler-10-1 cuda-compiler-11-2 cuda-cudart-10-1 cuda-cudart-11-2 cuda-cudart-dev-10-1 cuda-cudart-dev-11-2
  cuda-cufft-10-1 cuda-cufft-dev-10-1 cuda-cuobjdump-10-1 cuda-cuobjdump-11-2 cuda-cupti-10-1 cuda-cupti-11-2 cuda-cupti-dev-11-2 cuda-curand-10-1 cuda-curand-dev-10-1
  cuda-cusolver-10-1 cuda-cusolver-dev-10-1 cuda-cusparse-10-1 cuda-cusparse-dev-10-1 cuda-cuxxfilt-11-2 cuda-documentation-10-1 cuda-documentation-11-2 cuda-driver-dev-10-1
  cuda-driver-dev-11-2 cuda-drivers-460 cuda-gdb-10-1 cuda-gdb-11-2 cuda-gpu-library-advisor-10-1 cuda-libraries-10-1 cuda-libraries-11-2 cuda-libraries-dev-10-1
  cuda-libraries-dev-11-2 cuda-license-10-1 cuda-memcheck-10-1 cuda-memcheck-11-2 cuda-misc-headers-10-1 cuda-npp-10-1 cuda-npp-dev-10-1 cuda-nsight-10-1 cuda-nsight-11-2
  cuda-nsight-compute-10-1 cuda-nsight-compute-11-2 cuda-nsight-systems-10-1 cuda-nsight-systems-11-2 cuda-nvcc-10-1 cuda-nvcc-11-2 cuda-nvdisasm-10-1 cuda-nvdisasm-11-2
  cuda-nvgraph-10-1 cuda-nvgraph-dev-10-1 cuda-nvjpeg-10-1 cuda-nvjpeg-dev-10-1 cuda-nvml-dev-10-1 cuda-nvml-dev-11-2 cuda-nvprof-10-1 cuda-nvprof-11-2 cuda-nvprune-10-1
  cuda-nvprune-11-2 cuda-nvrtc-10-1 cuda-nvrtc-11-2 cuda-nvrtc-dev-10-1 cuda-nvrtc-dev-11-2 cuda-nvtx-10-1 cuda-nvtx-11-2 cuda-nvvp-10-1 cuda-nvvp-11-2 cuda-samples-10-1
  cuda-samples-11-2 cuda-sanitizer-11-2 cuda-sanitizer-api-10-1 cuda-toolkit-10-1 cuda-toolkit-11-2 cuda-tools-10-1 cuda-tools-11-2 cuda-visual-tools-10-1
  cuda-visual-tools-11-2 freeglut3 freeglut3-dev libcublas-11-2 libcublas-dev libcublas-dev-11-2 libcublas10 libcufft-11-2 libcufft-dev-11-2 libcurand-11-2 libcurand-dev-11-2
  libcusolver-11-2 libcusolver-dev-11-2 libcusparse-11-2 libcusparse-dev-11-2 libnpp-11-2 libnpp-dev-11-2 libnvidia-cfg1-460 libnvidia-common-460 libnvidia-compute-460
  libnvidia-decode-460 libnvidia-encode-460 libnvidia-extra-460 libnvidia-fbc1-460 libnvidia-gl-460 libnvidia-ifr1-460 libnvjpeg-11-2 libnvjpeg-dev-11-2 libqt5positioning5
  libqt5sensors5 libqt5webchannel5 libqt5webkit5 libxi-dev libxmu-dev libxmu-headers linux-headers-4.15.0-143 linux-headers-4.15.0-143-generic linux-modules-4.15.0-143-generic
  nsight-compute-2020.3.0 nsight-compute-2020.3.1 nsight-compute-2022.1.0 nsight-systems-2020.4.3 nsight-systems-2021.5.2 nvidia-compute-utils-460 nvidia-dkms-460
  nvidia-kernel-common-460 nvidia-kernel-source-460 nvidia-modprobe nvidia-utils-460 qml-module-qtgraphicaleffects qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-window2 qml-module-qtquick2 shim xserver-xorg-video-nvidia-460
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 206: /usr/share/mysql-common/configure-symlinks: No such file or directory
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 127
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
zulfi@lc2530hz:~$ 



```
$ sudo apt install mysql-server-5.7
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.7 is already the newest version (5.7.37-0ubuntu0.18.04.1).
mysql-server-5.7 set to manually installed.
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-10-1 cuda-command-line-tools-11-2 cuda-compiler-10-1 cuda-compiler-11-2 cuda-cudart-10-1 cuda-cudart-11-2 cuda-cudart-dev-10-1 cuda-cudart-dev-11-2
  cuda-cufft-10-1 cuda-cufft-dev-10-1 cuda-cuobjdump-10-1 cuda-cuobjdump-11-2 cuda-cupti-10-1 cuda-cupti-11-2 cuda-cupti-dev-11-2 cuda-curand-10-1 cuda-curand-dev-10-1
  cuda-cusolver-10-1 cuda-cusolver-dev-10-1 cuda-cusparse-10-1 cuda-cusparse-dev-10-1 cuda-cuxxfilt-11-2 cuda-documentation-10-1 cuda-documentation-11-2 cuda-driver-dev-10-1
  cuda-driver-dev-11-2 cuda-drivers-460 cuda-gdb-10-1 cuda-gdb-11-2 cuda-gpu-library-advisor-10-1 cuda-libraries-10-1 cuda-libraries-11-2 cuda-libraries-dev-10-1
  cuda-libraries-dev-11-2 cuda-license-10-1 cuda-memcheck-10-1 cuda-memcheck-11-2 cuda-misc-headers-10-1 cuda-npp-10-1 cuda-npp-dev-10-1 cuda-nsight-10-1 cuda-nsight-11-2
  cuda-nsight-compute-10-1 cuda-nsight-compute-11-2 cuda-nsight-systems-10-1 cuda-nsight-systems-11-2 cuda-nvcc-10-1 cuda-nvcc-11-2 cuda-nvdisasm-10-1 cuda-nvdisasm-11-2
  cuda-nvgraph-10-1 cuda-nvgraph-dev-10-1 cuda-nvjpeg-10-1 cuda-nvjpeg-dev-10-1 cuda-nvml-dev-10-1 cuda-nvml-dev-11-2 cuda-nvprof-10-1 cuda-nvprof-11-2 cuda-nvprune-10-1
  cuda-nvprune-11-2 cuda-nvrtc-10-1 cuda-nvrtc-11-2 cuda-nvrtc-dev-10-1 cuda-nvrtc-dev-11-2 cuda-nvtx-10-1 cuda-nvtx-11-2 cuda-nvvp-10-1 cuda-nvvp-11-2 cuda-samples-10-1
  cuda-samples-11-2 cuda-sanitizer-11-2 cuda-sanitizer-api-10-1 cuda-toolkit-10-1 cuda-toolkit-11-2 cuda-tools-10-1 cuda-tools-11-2 cuda-visual-tools-10-1
  cuda-visual-tools-11-2 freeglut3 freeglut3-dev libcublas-11-2 libcublas-dev libcublas-dev-11-2 libcublas10 libcufft-11-2 libcufft-dev-11-2 libcurand-11-2 libcurand-dev-11-2
  libcusolver-11-2 libcusolver-dev-11-2 libcusparse-11-2 libcusparse-dev-11-2 libnpp-11-2 libnpp-dev-11-2 libnvidia-cfg1-460 libnvidia-common-460 libnvidia-compute-460
  libnvidia-decode-460 libnvidia-encode-460 libnvidia-extra-460 libnvidia-fbc1-460 libnvidia-gl-460 libnvidia-ifr1-460 libnvjpeg-11-2 libnvjpeg-dev-11-2 libqt5positioning5
  libqt5sensors5 libqt5webchannel5 libqt5webkit5 libxi-dev libxmu-dev libxmu-headers linux-headers-4.15.0-143 linux-headers-4.15.0-143-generic linux-modules-4.15.0-143-generic
  nsight-compute-2020.3.0 nsight-compute-2020.3.1 nsight-compute-2022.1.0 nsight-systems-2020.4.3 nsight-systems-2021.5.2 nvidia-compute-utils-460 nvidia-dkms-460
  nvidia-kernel-common-460 nvidia-kernel-source-460 nvidia-modprobe nvidia-utils-460 qml-module-qtgraphicaleffects qml-module-qtquick-controls qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-window2 qml-module-qtquick2 shim xserver-xorg-video-nvidia-460
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 206: /usr/share/mysql-common/configure-symlinks: No such file or directory
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 127
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
zulfi@lc2530hz:~$

---

### Post by Xian on 2022-02-13
Try using a couple of commands to verify the config and install status:

$ sudo systemctl enable mysql.service 
$ sudo apt-get install -f

---

### Post by zak100 on 2022-02-13
Hi,
Thanks for your response. I got following output:

```
**$ sudo systemctl enable mysql.service**
```

[sudo] password for zulfi: 
Synchronizing state of mysql.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable mysql

```
**@lc2530hz:~$ sudo apt-get install -f**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-10-1 cuda-command-line-tools-11-2 cuda-compiler-10-1
  cuda-compiler-11-2 cuda-cudart-10-1 cuda-cudart-11-2 cuda-cudart-dev-10-1
  cuda-cudart-dev-11-2 cuda-cufft-10-1 cuda-cufft-dev-10-1 cuda-cuobjdump-10-1
  cuda-cuobjdump-11-2 cuda-cupti-10-1 cuda-cupti-11-2 cuda-cupti-dev-11-2
  cuda-curand-10-1 cuda-curand-dev-10-1 cuda-cusolver-10-1
  cuda-cusolver-dev-10-1 cuda-cusparse-10-1 cuda-cusparse-dev-10-1
  cuda-cuxxfilt-11-2 cuda-documentation-10-1 cuda-documentation-11-2
  cuda-driver-dev-10-1 cuda-driver-dev-11-2 cuda-drivers-460 cuda-gdb-10-1
  cuda-gdb-11-2 cuda-gpu-library-advisor-10-1 cuda-libraries-10-1
  cuda-libraries-11-2 cuda-libraries-dev-10-1 cuda-libraries-dev-11-2
  cuda-license-10-1 cuda-memcheck-10-1 cuda-memcheck-11-2
  cuda-misc-headers-10-1 cuda-npp-10-1 cuda-npp-dev-10-1 cuda-nsight-10-1
  cuda-nsight-11-2 cuda-nsight-compute-10-1 cuda-nsight-compute-11-2
  cuda-nsight-systems-10-1 cuda-nsight-systems-11-2 cuda-nvcc-10-1
  cuda-nvcc-11-2 cuda-nvdisasm-10-1 cuda-nvdisasm-11-2 cuda-nvgraph-10-1
  cuda-nvgraph-dev-10-1 cuda-nvjpeg-10-1 cuda-nvjpeg-dev-10-1
  cuda-nvml-dev-10-1 cuda-nvml-dev-11-2 cuda-nvprof-10-1 cuda-nvprof-11-2
  cuda-nvprune-10-1 cuda-nvprune-11-2 cuda-nvrtc-10-1 cuda-nvrtc-11-2
  cuda-nvrtc-dev-10-1 cuda-nvrtc-dev-11-2 cuda-nvtx-10-1 cuda-nvtx-11-2
  cuda-nvvp-10-1 cuda-nvvp-11-2 cuda-samples-10-1 cuda-samples-11-2
  cuda-sanitizer-11-2 cuda-sanitizer-api-10-1 cuda-toolkit-10-1
  cuda-toolkit-11-2 cuda-tools-10-1 cuda-tools-11-2 cuda-visual-tools-10-1
  cuda-visual-tools-11-2 freeglut3 freeglut3-dev libcublas-11-2 libcublas-dev
  libcublas-dev-11-2 libcublas10 libcufft-11-2 libcufft-dev-11-2
  libcurand-11-2 libcurand-dev-11-2 libcusolver-11-2 libcusolver-dev-11-2
  libcusparse-11-2 libcusparse-dev-11-2 libnpp-11-2 libnpp-dev-11-2
  libnvidia-cfg1-460 libnvidia-common-460 libnvidia-compute-460
  libnvidia-decode-460 libnvidia-encode-460 libnvidia-extra-460
  libnvidia-fbc1-460 libnvidia-gl-460 libnvidia-ifr1-460 libnvjpeg-11-2
  libnvjpeg-dev-11-2 libqt5positioning5 libqt5sensors5 libqt5webchannel5
  libqt5webkit5 libxi-dev libxmu-dev libxmu-headers linux-headers-4.15.0-143
  linux-modules-4.15.0-143-generic nsight-compute-2020.3.0
  nsight-compute-2020.3.1 nsight-compute-2022.1.0 nsight-systems-2020.4.3
  nsight-systems-2021.5.2 nvidia-compute-utils-460 nvidia-dkms-460
  nvidia-kernel-common-460 nvidia-kernel-source-460 nvidia-modprobe
  nvidia-utils-460 qml-module-qtgraphicaleffects qml-module-qtquick-controls
  qml-module-qtquick-dialogs qml-module-qtquick-layouts
  qml-module-qtquick-privatewidgets qml-module-qtquick-window2
  qml-module-qtquick2 shim xserver-xorg-video-nvidia-460
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.7 (5.7.37-0ubuntu0.18.04.1) ...
/var/lib/dpkg/info/mysql-server-5.7.postinst: line 206: /usr/share/mysql-common/configure-symlinks: No such file or directory
dpkg: error processing package mysql-server-5.7 (--configure):
 installed mysql-server-5.7 package post-installation script subprocess returned error exit status 127
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.

dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


Kindly guide me.

Zulfi.

---

### Post by zak100 on 2022-02-14
@Xian, hi kindly guide me.

Zulfi.

---

