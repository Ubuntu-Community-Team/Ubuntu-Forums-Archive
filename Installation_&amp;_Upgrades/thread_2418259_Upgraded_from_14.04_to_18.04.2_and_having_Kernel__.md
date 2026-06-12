---
title: "Upgraded from 14.04 to 18.04.2 and having Kernel / Compiler version issues."
date: 2019-05-04
forum: Installation &amp; Upgrades
---

### Post by nto1381 on 2019-05-04
Upgraded from 14.04 with do-release-upgrade to 18.04.2.

Performed the usual apt-get update, upgrade, and dist-upgrade..

I attempted to install the latest nvidia driver 418 and DKMS failed to compile..

"The kernel was built with gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3), but the current compiler version is cc (Ubuntu 7.4.0-1ubuntu1~18.04) 7.4.0."

$ uname -r 
4.15.0-48-generic

$ cat /proc/version
Linux version 4.15.0-48-generic (buildd@lgw01-amd64-036) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) #51-Ubuntu SMP Wed Apr 3 08:28:49 UTC 2019

$ gcc --version
gcc (Ubuntu 7.4.0-1ubuntu1~18.04) 7.4.0
Copyright (C) 2017 Free Software Foundation, Inc.



I don't know how to recover from this error...
Any assistance is appreciated..
Thanks,
-Michael

---

### Post by ubfan1 on 2019-05-04
That gcc kernel/current version difference is normal.  What are the compiler errors?  Ubuntu 18.04 enforces more strictly the need to sign modules, so if you have secure boot enabled, Nvidia won't run without you signing the module.  Did you leave secure boot on?

---

### Post by dino99 on 2019-05-04
Always install the required driver (passibly not the latest published) for your nidia card. Purge the old one first; and after a dist-upgrade, also run gtkorphan and bleachbit (as root, carefully select options) to get a cleaned system.
[http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux)

---

### Post by nto1381 on 2019-05-04
Currently it is DKMS build that is failing.  I get the following from the make log.

*"/var/lib/dkms/nvidia/418.56/build/Kbuild:181: recipe for target 'cc_version_check' failed"*

They have the following, can't figure out haw to have 7.3 and 7.4 installed at the same time...

*"It is recommended to set the CC environment variable to the compiler that was used to compile the kernel."*

They also mention that there is a way to bypass check, but not sure if that will cause more problem than less.   Thoughts.?

*"The compiler version check can be disabled by setting the IGNORE_CC_MISMATCH environment variable to "1".  However, mixing compiler versions between the kernel and kernel modules can result in subtle bugs that are difficult to diagnose."*

This necessarily not an Nvidia version issue as it is a DKMS and Kernel Modules issue..

I need to make some mods to the USB and UVC modules, thus i'd like to correct rather than run into bigger issues later..

---

### Post by rlomba on 2019-05-18
I was able to get past this step by running the NVIDIA installer as follows:

```
CC=gcc-7.3.0 ./NVIDIA-Linux-x86_64-418.56.run
```

This allowed me to get past the error, but I got another exception:

*ERROR: Unable to determine the version of the kernel sources located in '/lib/modules/4.15.0-48-generic/build'. Please make sure you have installed the kernel source files for your kernel and that they are properly configured [...] you may specify the kernel source path with the '--kernel-source-path' command line option*

At this point, given that I know where the Kernel Source is located, I wanted to try the following as well:

```
CC=gcc-7.3.0 ./NVIDIA-Linux-x86_64-418.56.run --kernel-source-path=/usr/src/linux-headers-4.15.0-48-generic

```
Nevertheless I got the same error as above. So I tried with:

 ```
CC=gcc-7.3.0 ./NVIDIA-Linux-x86_64-418.56.run --kernel-source-path=/usr/src/linux-headers-4.15.0-48-generic/include
```

And got to a different error:

[I]ERROR: The kernel header file '/usr/src/linux-headers-4.15.0-48-generic/include/include/linux/kernel.h' does not exist. The most likely reason for this is that the kernel source path '/usr/src/linux-headers-4.15.0-48-generic/include/include' is incorrect. [...]
[/I]
I have tried different other paths, but now I'm stuck and got out of options. The fact is that I'm not even able to install older NVIDIA Drivers now, so the whole system is now as useful as a paperweight

Did you manage to get past the issue somehow?

---

### Post by rlomba on 2019-05-20
In case somebody else will get stuck with this:

```
sudo apt-get update
sudo apt-get upgrade
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get upgrade
ubuntu-drivers list
sudo apt-get install nvidia-driver-430
reboot
```

That was it. Actually, using the ppa repo for the NVIDIA Drivers is obviously the recommended way to install them. I had to switch to ./NVIDIA.run because for some reasons, in my case, the recommended procedure just did not work in the past

After having hit this issue, I wanted to try if the problem got fixed along the way, given the large amount of OS updates having been released during the last months. It did work, luckily, and now I have my system back and working

---

