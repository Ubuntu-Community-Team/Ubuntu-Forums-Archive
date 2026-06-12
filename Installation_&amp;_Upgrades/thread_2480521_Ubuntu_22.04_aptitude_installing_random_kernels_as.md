---
title: "Ubuntu 22.04 aptitude installing random kernels as dependencies breaking the system"
date: 2022-11-01
forum: Installation &amp; Upgrades
---

### Post by egandt on 2022-11-01
Ubuntu 22.04 aptitude installing random kernels as dependencies breaking the system

```

root@fileserver:/etc/apt/apt.conf.d# apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 https://download.docker.com/linux/ubuntu jammy InRelease
Get:4 https://nvidia.github.io/libnvidia-container/stable/ubuntu18.04/amd64  InRelease [1,484 B]
Hit:5 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:6 http://us.archive.ubuntu.com/ubuntu jammy-security InRelease
Hit:7 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:8 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease
Fetched 1,484 B in 0s (3,551 B/s)
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
49 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@fileserver:/etc/apt/apt.conf.d# apt update^C
root@fileserver:/etc/apt/apt.conf.d# apt list --upgradable
Listing... Done
alsa-ucm-conf/jammy-updates 1.2.6.3-1ubuntu1.1 all [upgradable from: 1.2.6.3-1ubuntu1]
containerd.io/jammy 1.6.9-1 amd64 [upgradable from: 1.6.8-1]
docker-ce-cli/jammy 5:20.10.21~3-0~ubuntu-jammy amd64 [upgradable from: 5:20.10.19~3-0~ubuntu-jammy]
docker-ce-rootless-extras/jammy 5:20.10.21~3-0~ubuntu-jammy amd64 [upgradable from: 5:20.10.19~3-0~ubuntu-jammy]
docker-ce/jammy 5:20.10.21~3-0~ubuntu-jammy amd64 [upgradable from: 5:20.10.19~3-0~ubuntu-jammy]
docker-compose-plugin/jammy 2.12.2~ubuntu-jammy amd64 [upgradable from: 2.11.2~ubuntu-jammy]
docker-scan-plugin/jammy 0.21.0~ubuntu-jammy amd64 [upgradable from: 0.17.0~ubuntu-jammy]
fwupd/jammy-updates 1.7.9-1~22.04.1 amd64 [upgradable from: 1.7.5-3]
google-chrome-stable/stable 107.0.5304.87-1 amd64 [upgradable from: 106.0.5249.119-1]
grub-efi-amd64-bin/jammy-updates 2.06-2ubuntu10 amd64 [upgradable from: 2.06-2ubuntu7]
grub-efi-amd64-signed/jammy-updates 1.182~22.04.1+2.06-2ubuntu10 amd64 [upgradable from: 1.180+2.06-2ubuntu7]
grub-efi-amd64/jammy-updates 2.06-2ubuntu10 amd64 [upgradable from: 2.06-2ubuntu7]
libapache2-mod-php8.1/jammy-updates 8.1.2-1ubuntu2.6 amd64 [upgradable from: 8.1.2-1ubuntu2.5]
libfwupd2/jammy-updates 1.7.9-1~22.04.1 amd64 [upgradable from: 1.7.5-3]
libfwupdplugin5/jammy-updates 1.7.9-1~22.04.1 amd64 [upgradable from: 1.7.5-3]
libnvidia-cfg1-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-common-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 all [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-compute-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-decode-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-encode-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-extra-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-fbc1-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libnvidia-gl-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
libpulse-mainloop-glib0/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
libpulse0/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
libpulsedsp/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
linux-firmware/jammy-updates 20220329.git681281e4-0ubuntu3.6 all [upgradable from: 20220329.git681281e4-0ubuntu3.5]
nvidia-compute-utils-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
nvidia-dkms-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
nvidia-driver-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
nvidia-kernel-common-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
nvidia-kernel-source-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
nvidia-utils-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
php8.1-cli/jammy-updates 8.1.2-1ubuntu2.6 amd64 [upgradable from: 8.1.2-1ubuntu2.5]
php8.1-common/jammy-updates 8.1.2-1ubuntu2.6 amd64 [upgradable from: 8.1.2-1ubuntu2.5]
php8.1-opcache/jammy-updates 8.1.2-1ubuntu2.6 amd64 [upgradable from: 8.1.2-1ubuntu2.5]
php8.1-readline/jammy-updates 8.1.2-1ubuntu2.6 amd64 [upgradable from: 8.1.2-1ubuntu2.5]
php8.1/jammy-updates 8.1.2-1ubuntu2.6 all [upgradable from: 8.1.2-1ubuntu2.5]
pulseaudio-module-bluetooth/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
pulseaudio-utils/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
pulseaudio/jammy-updates 1:15.99.1+dfsg1-1ubuntu2 amd64 [upgradable from: 1:15.99.1+dfsg1-1ubuntu1]
snapd/jammy-updates 2.57.5+22.04 amd64 [upgradable from: 2.56.2+22.04ubuntu1]
sosreport/jammy-updates 4.4-1ubuntu1.22.04.1 amd64 [upgradable from: 4.3-1ubuntu2.1]
sudo/jammy-updates 1.9.9-1ubuntu2.1 amd64 [upgradable from: 1.9.9-1ubuntu2]
tzdata/jammy-updates 2022e-0ubuntu0.22.04.0 all [upgradable from: 2022c-0ubuntu0.22.04.0]
xserver-common/jammy-updates 2:21.1.3-2ubuntu2.2 all [upgradable from: 2:21.1.3-2ubuntu2.1]
xserver-xorg-core/jammy-updates 2:21.1.3-2ubuntu2.2 amd64 [upgradable from: 2:21.1.3-2ubuntu2.1]
xserver-xorg-legacy/jammy-updates 2:21.1.3-2ubuntu2.2 amd64 [upgradable from: 2:21.1.3-2ubuntu2.1]
xserver-xorg-video-nvidia-515/jammy-updates 515.76+really.515.65.01-0ubuntu0.22.04.1 amd64 [upgradable from: 515.76-0ubuntu0.22.04.1]
root@fileserver:/etc/apt/apt.conf.d#

```

So this looks fine in aptitude I see:
Numerous random oem and backport kernels being added as dependences (but for what I can not figure out), might mention completely breaks Nvidia in the process.  I need to figure out where these dependences are from and how to stop them from being automatically added, as the last update I did with these took me over 4 hours to fully repair, seemed fine, then now 15 days later they are all back again.
[ATTACH=CONFIG]291210[/ATTACH]
Now also odd if I remove all of these bad kernels nothing is marked as blocked, so I have no ide why they are getting included.
[ATTACH=CONFIG]291211[/ATTACH]

Suggestions,
ERIC

---

### Post by ian-weisser on 2022-11-01
How to figure out where they are from: ```
apt-cache policy <package_name>
```

---

### Post by egandt on 2022-11-01
```

``````

```I checked a few all look similar to:
```
root@fileserver:~# apt-cache policy linux-base-sgx
linux-base-sgx:
  Installed: (none)
  Candidate: 4.5ubuntu9
  Version table:
     4.5ubuntu9 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status
root@fileserver:~# apt-cache policy linux-image-6.0.0-1006-oem
linux-image-6.0.0-1006-oem:
  Installed: (none)
  Candidate: 6.0.0-1006.6
  Version table:
     6.0.0-1006.6 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
root@fileserver:~# apt-cache policy linux-image-5.17.0-1020-oem
linux-image-5.17.0-1020-oem:
  Installed: (none)
  Candidate: 5.17.0-1020.21
  Version table:
     5.17.0-1020.21 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security/main amd64 Packages

```

So none explain what is pulling them in.  I have the following extra sources:
docker.list  - for docker-ce
google-chrome.list  - for chrome
mozillateam-ubuntu-ppa-jammy.list - for real native firefox
nvidia-container-toolkit.list - Needed for using Nvida Cuda in a container (wish there was a better way).

so still lost.


So I tried upgrading ever single package (well started with groups then sub groups ...), until I had a good list, then started adding until I got the issue again:
[ATTACH=CONFIG]291212[/ATTACH]
So seems like it is the nvidia-driver-515 that is the cause, which makes no sense sine the 515 drive does not work with these kernels in the first place.

```

root@fileserver:~# apt-cache policy nvidia-driver-515
nvidia-driver-515:
  Installed: 515.76-0ubuntu0.22.04.1
  Candidate: 515.76+really.515.65.01-0ubuntu0.22.04.1
  Version table:
     515.76+really.515.65.01-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/restricted amd64 Packages
 *** 515.76-0ubuntu0.22.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/restricted amd64 Packages
        100 /var/lib/dpkg/status

```
Also not coming from Nvidia's repo but from a "restricted amd64 Packages"


ERIC

---

### Post by egandt on 2022-11-01
So I think the issue is with nvidia-dkms-515:
[ATTACH=CONFIG]291215[/ATTACH]


```
root@fileserver:~# apt remove -s nvidia-dkms-515
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnvidia-cfg1-515 libnvidia-common-515 libnvidia-decode-515 libnvidia-egl-wayland1 libnvidia-encode-515 libnvidia-extra-515 libnvidia-fbc1-515 libnvidia-gl-515 nvidia-compute-utils-515 nvidia-kernel-source-515 nvidia-prime nvidia-settings nvidia-utils-515 pkg-config
  screen-resolution-extra xserver-xorg-video-nvidia-515
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-gl-515
The following packages will be REMOVED:
  nvidia-dkms-515 nvidia-driver-515
The following packages will be upgraded:
  libnvidia-gl-515
1 upgraded, 0 newly installed, 2 to remove and 48 not upgraded.
Remv nvidia-driver-515 [515.76-0ubuntu0.22.04.1]
Remv nvidia-dkms-515 [515.76-0ubuntu0.22.04.1]
Inst libnvidia-gl-515 [515.76-0ubuntu0.22.04.1] (515.76+really.515.65.01-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
Conf libnvidia-gl-515 (515.76+really.515.65.01-0ubuntu0.22.04.1 Ubuntu:22.04/jammy-updates [amd64])
```

However I can not remove this as it then removes all of Nvidia's software, makes sense as dkms is important.


```
root@fileserver:~# apt-cache depends nvidia-dkms-515
nvidia-dkms-515
  Depends: dkms
  Depends: nvidia-kernel-source-515
  Depends: nvidia-kernel-source-515
  Depends: nvidia-kernel-common-515
  Depends: nvidia-kernel-common-515
  Conflicts: <nvidia-dkms-kernel>
    nvidia-dkms-390
    nvidia-dkms-418-server
    nvidia-dkms-450-server
    nvidia-dkms-470
    nvidia-dkms-470-server
    nvidia-dkms-510
    nvidia-dkms-510-server
    nvidia-dkms-515-open
    nvidia-dkms-515-server
    nvidia-dkms-520
    nvidia-dkms-520-open
  Breaks: nvidia-kernel-source-515
  Replaces: nvidia-384
  Replaces: <nvidia-dkms-kernel>
    nvidia-dkms-390
    nvidia-dkms-418-server
    nvidia-dkms-450-server
    nvidia-dkms-470
    nvidia-dkms-470-server
    nvidia-dkms-510
    nvidia-dkms-510-server
    nvidia-dkms-515
    nvidia-dkms-515-open
    nvidia-dkms-515-server
    nvidia-dkms-520
    nvidia-dkms-520-open
  Replaces: nvidia-kernel-source-515
```

I do not see where these dependencies for things like aws or azure or oracle come from?

---

### Post by ubfan1 on 2022-11-01
Looks like the 515.76 is the one in your  100 /var/lib/dpkg/status -- that line is under the 515.76+really.515.65.01-0ubuntu0.22.04.1 500 line on my system.  My system was once using the .76 driver, but seemed to automatically drop back to the 76+really.515.65 one.  mybe an uninstall and reinstall would fix it?
CUDA dependencies are a known problem.  I recommend getting your system working without any CUDA packages (fix the Nvidia drivers), then install CUDA from the Nvidia .run script, skipping the Nvidia driver offered, and overridding all system location for libs with the /usr/local/cudaxxx/lib location.  You should be able to temporarily change permissions on the /usr/local dir and run the .run script as a user instead of root, guaranteeing no system area will be touched.There are answers on askubuntu detailing the procedure.

---

### Post by egandt on 2022-11-02
I tried that last time did not work.  Also while I can get CUDA working in the host with a manual install, I need the Nvidia to get it working in containers which does not work well.  Thinking of using holds on all packages and then just manually compiling for new kernels but that is a hack at best.

ERIC

---

