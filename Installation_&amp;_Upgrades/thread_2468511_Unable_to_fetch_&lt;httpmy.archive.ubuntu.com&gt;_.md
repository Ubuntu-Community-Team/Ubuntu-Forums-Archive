---
title: "Unable to fetch &lt;http://my.archive.ubuntu.com&gt; library"
date: 2021-11-01
forum: Installation &amp; Upgrades
---

### Post by drayzcck on 2021-11-01
Recently I've find an issue when performing **apt update / apt upgrade**. Error 404 when fetching all [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) library.
I could reproduce in across several PC ( ubuntu 18.04 & ubuntu 20.03 ) & network environment. 
May I know whats wrong with this?

```

E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-mainloop-glib0_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulsedsp_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-bluetooth_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_13.99.1-1ubuntu3.12_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/n/netplan.io/libnetplan0_0.103-0ubuntu5~20.04.2_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/n/netplan.io/netplan.io_0.103-0ubuntu5~20.04.2_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/a/alsa-ucm-conf/alsa-ucm-conf_1.2.2-1ubuntu0.11_all.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-driver-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-extra-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-common-470_470.74-0ubuntu0.20.04.1_all.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-gl-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-gl-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-dkms-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-kernel-source-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-kernel-common-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-decode-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-decode-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-compute-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-compute-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-compute-utils-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-encode-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-encode-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/nvidia-utils-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/xserver-xorg-video-nvidia-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-ifr1-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-ifr1-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-fbc1-470_470.74-0ubuntu0.20.04.1_i386.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-fbc1-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-470/libnvidia-cfg1-470_470.74-0ubuntu0.20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/libq/libqmi/libqmi-proxy_1.28.6-1~20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Failed to fetch http://my.archive.ubuntu.com/ubuntu/pool/main/libq/libqmi/libqmi-glib5_1.28.6-1~20.04.1_amd64.deb  404  Not Found [IP: 202.79.184.254 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by deadflowr on 2021-11-01
Another users has the same issue with the same server here: [https://ubuntuforums.org/showthread.php?t=2468444]("https://ubuntuforums.org/showthread.php?t=2468444")

My guess is a bad Mirror.
I would suggest to try to change Mirrors.

See a listing of currently supported mirrors here: [https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

Some basic info on How to change mirror servers on Ubuntu Desktop here: [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server]("https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server")

---

### Post by ActionParsnip on 2021-11-02
+1 for switch mirror

---

