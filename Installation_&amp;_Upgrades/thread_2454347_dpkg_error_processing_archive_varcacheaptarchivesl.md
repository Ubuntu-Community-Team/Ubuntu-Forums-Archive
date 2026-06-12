---
title: "dpkg: error processing archive /var/cache/apt/archives/libnvidia-compute-440_440.118."
date: 2020-11-27
forum: Installation &amp; Upgrades
---

### Post by takanotume24 on 2020-11-27
Is there anyone else who is in the same situation as me?

```

takuya@takuya-HP-ZBook-Studio-G3:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libnvidia-decode-440 : Depends: libnvidia-compute-440 (= 440.118.02-0ubuntu1) but 440.100-0ubuntu0.18.04.1 is installed
 nvidia-driver-440 : Depends: libnvidia-compute-440 (= 440.118.02-0ubuntu1) but 440.100-0ubuntu0.18.04.1 is installed
                     Recommends: libnvidia-compute-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-decode-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-encode-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-ifr1-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-fbc1-440:i386 (= 440.118.02-0ubuntu1)
                     Recommends: libnvidia-gl-440:i386 (= 440.118.02-0ubuntu1)
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).



```

```

takuya@takuya-HP-ZBook-Studio-G3:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  cuda-command-line-tools-11-1 cuda-compiler-11-1 cuda-cudart-11-1
  cuda-cudart-dev-11-1 cuda-cuobjdump-11-1 cuda-cupti-11-1 cuda-cupti-dev-11-1
  cuda-documentation-11-1 cuda-driver-dev-11-1 cuda-gdb-11-1
  cuda-libraries-11-1 cuda-libraries-dev-11-1 cuda-memcheck-11-1
  cuda-nsight-11-1 cuda-nsight-compute-11-1 cuda-nsight-systems-11-1
  cuda-nvcc-11-1 cuda-nvdisasm-11-1 cuda-nvml-dev-11-1 cuda-nvprof-11-1
  cuda-nvprune-11-1 cuda-nvrtc-11-1 cuda-nvrtc-dev-11-1 cuda-nvtx-11-1
  cuda-nvvp-11-1 cuda-samples-11-1 cuda-sanitizer-11-1 cuda-toolkit-11-1
  cuda-tools-11-1 cuda-visual-tools-11-1 libcublas-11-1 libcublas-dev-11-1
  libcufft-11-1 libcufft-dev-11-1 libcurand-11-1 libcurand-dev-11-1
  libcusolver-11-1 libcusolver-dev-11-1 libcusparse-11-1 libcusparse-dev-11-1
  libfwup1 libllvm9 libnpp-11-1 libnpp-dev-11-1 libnvidia-common-455
  libnvidia-extra-440 libnvidia-extra-450 libnvjpeg-11-1 libnvjpeg-dev-11-1
  libpython3.8-minimal libpython3.8-stdlib linux-hwe-5.4-headers-5.4.0-42
  linux-hwe-5.4-headers-5.4.0-48 linux-hwe-5.4-headers-5.4.0-52
  nsight-compute-2019.5.0 python3-wheel python3.8-minimal
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libnvidia-compute-440
The following packages will be upgraded:
  libnvidia-compute-440
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0 B/20.9 MB of archives.
After this operation, 85.0 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 376632 files and directories currently installed.)
Preparing to unpack .../libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb ...
Unpacking libnvidia-compute-440:amd64 (440.118.02-0ubuntu1) over (440.100-0ubuntu0.18.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libnvidia-allocator.so', which is also in package libnvidia-extra-450:amd64 450.80.02-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-compute-440_440.118.02-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Bashing-om on 2020-11-27
takanotume24; Hello - Welcome to the forum.

Broken graphic's driver ?
Conflict in driver ?
DKMS issue with an OEM driver install ?

Let's get some diagnostic info - see then where it leads us:
Post back the results of terminal commands:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
dkms status
apt policy libnvidia-compute-440
sudo find / -name "NVIDIA-Linux-*"

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

round and around it goes
[INDENT][INDENT]with these we should know
[/INDENT][/INDENT]

---

### Post by takanotume24 on 2020-11-27
Hi Bashing-om, thanks for the reply!

As it turns out, I deleted all the associated packages and reinstalled them all according to the installation instructions provided by nvidia.
That solved the problem and my cuda program worked.

```

$ sudo apt remove --purge "nvidia-*" -y && sudo apt autoremove
$ sudo apt remove --purge "cuda-*" -y && sudo apt autoremove
$ sudo apt remove --purge "libcudnn*" -y && sudo apt autoremove
$ sudo apt remove --purge "libnvidia-*" -y && sudo apt autoremove

```

The following is the installation procedure.
[https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork)


This happened when I did sudo apt update and apt upgrade of the machine where cuda was installed. I've upgraded many times before, so this is the first time.
What is different is that I usually run apt from the terminal, but this time I ran the update from the GUI updater (Software Updater).
This time the problem has been solved so that's OK, but the next time I have a similar problem again, I will run the program you showed me and post on the forum with more information! Thank you!

---

### Post by Bashing-om on 2020-11-27
takanotume24; Good deal -

You do good work :D

[INDENT]if you work it, it works[/INDENT]

---

