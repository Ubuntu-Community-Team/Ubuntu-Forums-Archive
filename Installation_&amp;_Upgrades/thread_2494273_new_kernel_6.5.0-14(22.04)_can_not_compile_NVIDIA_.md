---
title: "new kernel 6.5.0-14(22.04) can not compile NVIDIA display card driver"
date: 2024-01-10
forum: Installation &amp; Upgrades
---

### Post by sakalaboator on 2024-01-10
help!!! Today, after I update the kernel from 6.2.0-39 to 6.5.0-14, I find the latest NVIDIA display driver can not be installed by compile kernel errors. How can I solve this problem? wait NVIDIA to update drivers?

---

### Post by MAFoElffen on 2024-01-10
You didn't say which Nvidia driver, and if from the repo's (which work), or if a binary from Nvidia...

I can verify that the Nvidia drivers from the Ubuntu repo's work with 6.5.0-X kernels.

---

### Post by sakalaboator on 2024-01-10
> **MAFoElffen said:**
> You didn't say which Nvidia driver, and if from the repo's (which work), or if a binary from Nvidia...

I can verify that the Nvidia drivers from the Ubuntu repo's work with 6.5.0-X kernels.

Because I need to use GPU to do calculation jobs, so I didnot use ubuntu repo's drivers. I download the latest driver from Nvidia website, the lastest version: [COLOR=#000000][FONT=NVIDIA-APAC]535.146.02, [/FONT][/COLOR]Linux X64 (AMD64/EM64T) Display Driver, published date: [COLOR=#000000][FONT=NVIDIA-APAC]2023.12.7. When install, firstly, the drivers will be compiled into the kernel, than copy files to /usr/bin. Formerly, when use kernel 6.2.x, It's all right, but after update to 6.5.0-14 today, the compile failed, drivers cannot be installed.[/FONT][/COLOR]

---

### Post by sakalaboator on 2024-01-10
[COLOR=#333333][FONT=&quot]the NVIDIA driver error log promote: cc: error: unrecognized command-line option ‘-ftrivial-auto-var-init=zero’[/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-01-11
Compute?
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Wed Jan 10 22:35:37 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.129.03             Driver Version: 535.129.03   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   32C    P8               7W / 130W |    112MiB /  6144MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      4587      G   /usr/lib/xorg/Xorg                           66MiB |
|    0   N/A  N/A      5399      G   /usr/bin/gnome-shell                         43MiB |
+---------------------------------------------------------------------------------------+
mafoelffen@msi-ubuntu:~$ nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2021 NVIDIA Corporation
Built on Thu_Nov_18_09:45:30_PST_2021
Cuda compilation tools, release 11.5, V11.5.119
Build cuda_11.5.r11.5/compiler.30672275_0
mafoelffen@msi-ubuntu:~$ uname -r
6.5.0-14-generic

```
Like this?
```

mafoelffen@msi-ubuntu:~$ apt list nvidia-driver-535 nvidia-cuda-toolkit --installed
Listing... Done
nvidia-cuda-toolkit/jammy,now 11.5.1-1ubuntu1 amd64 [installed]
nvidia-driver-535/jammy-security,now 535.129.03-0ubuntu0.22.04.1 amd64 [installed,upgradable to: 535.146.02-0ubuntu0.22.04.1]

```

---

### Post by MAFoElffen on 2024-01-11
But I do hear that with NVidia binaries, if it has a compile problem, do this
```

mafoelffen@msi-ubuntu:~$ grep . /proc/version
Linux version 6.5.0-14-generic (buildd@lcy02-amd64-110) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2

```
See where the current running kernel was compiled with gcc-12?
```

gcc --version
apt -list gcc-1* --installed

```
It should be the same version as the running kernel... Or so i hear, that is what causes the error you are getting. If you install build essentials, then gcc-12, then temp set the sysmlink of gcc to gcc-12 (via update-alternatives, or manually)... then try that again, and see if it works. Afterwards, reset it back to gcc-11 or whatever it was originally.
Should be gcc-12

---

### Post by quotedotlad on 2024-01-11
I'm having the same issues, looks like the kernel update broke with the  Nvidia 535 drivers. I'm trying to fix it, as I'm stuck in a boot loop  and having to trouble shoot through the root shell prompt. Even tty  stopped behaving after purging the nvidia drivers.

I also see the error message being promoted: "[COLOR=#333333][FONT=&amp]unrecognized command-line option ‘-ftrivial-auto-var-init=zero’"[/FONT][/COLOR]

Currently have gcc11 and gcc12 installed

Current kernel version: 6.5.0-14-generic

running  grep . /proc/version gives:
"Linux version 6.5.0-14-generic (buildd@lcy02-amd64-110)  (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld  (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC  Mon Nov 20 18:15:30 UTC 2"

Using a Nvidia GeForce 3080Ti

I  was using 535 drivers from a "ubuntu-drivers install", but purged them in an attempt to get this  booting this morning. I'm gonna keep messing around with it, but any  fixes or tips would be appreciated.

---

### Post by #&amp;thj^% on 2024-01-11
I'm very close to yours:
```
inxi -Gxxz
Graphics:
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] vendor: Lenovo
    driver: nvidia v: 525.147.05 arch: Ampere pcie: speed: 2.5 GT/s lanes: 8

```

I'm on the fence with Ubuntu Driver auto installer, I like my way much better with less breakage.
```
sudo apt install nvidia-driver-535 nvidia-dkms-535
```
Just be sure to remove and purge the broken driver first.

---

### Post by sakalaboator on 2024-01-11
[COLOR=#333333][FONT=serif]It seems none of the GCC version, because the 535 version driver can be compiled into 6.2 kernel with the same gcc version and parameters. Someone says the driver in Ubuntu repo can be installed and run well. So I think the latest binary driver provided by NVIDIA has not been tested for new kernel. We can only do: 1. wait NVIDIA for new driver update, 2, install driver from Ubuntu repo. 3. fallback the kernel to 6.2.0.[/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-01-11
> **sakalaboator said:**
> [COLOR=#333333][FONT=serif]It  seems none of the GCC version, because the 535 version driver can be  compiled into 6.2 kernel with the same gcc version and parameters.  Someone says the driver in Ubuntu repo can be installed and run well. So  I think the latest binary driver provided by NVIDIA has not been tested  for new kernel. We can only do: 1. wait NVIDIA for new driver update,  2, install driver from Ubuntu repo. 3. fallback the kernel to 6.2.0.[/FONT][/COLOR]
You seem to be set just on using the NVidia Binary drivers from Nvidia that are not working for you. You do not seem to want to try to compile it with gcc-12  to see if that works or not.

From what I read, it works if compiled with gcc-12...

I have an idea... Post on the NVidia Forum and see what they say... It's their driver = Third party non-free.

---

### Post by ubfan1 on 2024-01-12
The Nvidia 535.146.02 driver is being "phased", so is likely not to be upgraded with the 6.5 kernel.  You can check with apt policy nvidia-driver-535.
You can force the upgrade with sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade

---

### Post by sakalaboator on 2024-01-12
> **MAFoElffen said:**
> You seem to be set just on using the NVidia Binary drivers from Nvidia that are not working for you. You do not seem to want to try to compile it with gcc-12  to see if that works or not.

From what I read, it works if compiled with gcc-12...

I have an idea... Post on the NVidia Forum and see what they say... It's their driver = Third party non-free.

Thanks, I have post the problem on NV forum, some user also has the same problem. Now I am waiting for the NV driver update. Actually, gcc version is very important for other apps, so I will not try gcc12.

---

### Post by sakalaboator on 2024-01-12
> **ubfan1 said:**
> The Nvidia 535.146.02 driver is being "phased", so is likely not to be upgraded with the 6.5 kernel.  You can check with apt policy nvidia-driver-535.
You can force the upgrade with sudo apt -o APT::Get::Always-Include-Phased-Updates=true upgrade

Thanks, I decide to wait for new NV driver update, maybe 536, or 540 will come out in these days. :)

---

### Post by raphaelnnoe on 2024-01-12
I'm struggling with this same problem, after the kernel update the nvidia drive stopped working, and in trying to solve it I ended up breaking the system, I formatted it but the problem persisted.
This big **** from canonical and nvidia **** me all over. :(

---

### Post by MAFoElffen on 2024-01-12
Didn't some GPU's end support at 525, 535, & 540?

IDK.

Doing NVidia support is work. I admit. Usually someone tells me the GPU... Then you have to look at these
[https://forums.developer.nvidia.com/t/how-do-i-find-the-correct-gpu-driver-for-my-use-case/249977](https://forums.developer.nvidia.com/t/how-do-i-find-the-correct-gpu-driver-for-my-use-case/249977)
[https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)
[https://www.nvidia.com/en-us/drivers/unix/](https://www.nvidia.com/en-us/drivers/unix/)

To play sleuth to figure out which driver a GPU uses and where the support ended.

I wish there was "_a chart_" that just was by GPU, and listed the last Driver Version was for that GPU! But I guess that makes too much sense.

---

### Post by sakalaboator on 2024-01-14
[COLOR=#333333][FONT=&amp]Thanks Peshkopy in nvidia forum, Thanks for all. This error is resolved by gcc version update. Now it works well.[/FONT][/COLOR]

[LIST=1]
[*]gcc -v
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/gcc/x86_64-linux-gnu/12/lto-wrapper
OFFLOAD_TARGET_NAMES=nvptx-none:amdgcn-amdhsa
OFFLOAD_TARGET_DEFAULT=1
Target: x86_64-linux-gnu
Configured with: &#8230;/src/configure -v --with-pkgversion=&#8216;Ubuntu 12.3.0-1ubuntu1~22.04&#8217; --with-bugurl=file:///usr/share/doc/gcc-12/README.Bugs --enable-languages=c,ada,c++,go,d,fortran,objc,obj-c++,m2 --prefix=/usr --with-gcc-major-version-only --program-suffix=-12 --program-prefix=x86_64-linux-gnu- --enable-shared --enable-linker-build-id --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --libdir=/usr/lib --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --with-default-libstdcxx-abi=new --enable-gnu-unique-object --disable-vtable-verify --enable-plugin --enable-default-pie --with-system-zlib --enable-libphobos-checking=release --with-target-system-zlib=auto --enable-objc-gc=auto --enable-multiarch --disable-werror --enable-cet --with-arch-32=i686 --with-abi=m64 --with-multilib-list=m32,m64,mx32 --enable-multilib --with-tune=generic --enable-offload-targets=nvptx-none=/build/gcc-12-ALHxjy/gcc-12-12.3.0/debian/tmp-nvptx/usr,amdgcn-amdhsa=/build/gcc-12-ALHxjy/gcc-12-12.3.0/debian/tmp-gcn/usr --enable-offload-defaulted --without-cuda-driver --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
Supported LTO compression algorithms: zlib zstd
gcc version 12.3.0 (Ubuntu 12.3.0-1ubuntu1~22.04)
[*]nvidia-smi
Mon Jan 15 09:19:11 2024
±--------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.146.02 Driver Version: 535.146.02 CUDA Version: 12.2 |
[*]Some old drivers eg. 390, can not supported by GCC12.
[/LIST]

---

### Post by MAFoElffen on 2024-01-14
> **sakalaboator said:**
> [COLOR=#333333][FONT=&amp]Thanks Peshkopy in nvidia forum, Thanks for all. This error is resolved by gcc version update. Now it works well.[/FONT][/COLOR]

I said this in  [Post #6]("https://ubuntuforums.org/showthread.php?t=2494273&p=14174443#post14174443")... And explained "the why". That Kernel 6.5.0-14 was compiled with ggc-12, so that the drivers need to be matched to that... When I said that, a few here said they didn't want to go that way. LOL. I understand that. Mantic & Noble do not have a problem, but those are already using newer gcc-12 by default. I didn't realize then, that older legacy drivers (304, 390, 410) would still not build with Ubuntu 22.04 & gcc-12.

I now have one old laptop with nvidia-driver-390 with 6.5 removed and pinned to 6.2 for that machine. But my other machines are running fine with nvidia-driver-535... I can post those notes for those interested, and with old legacy drivers... I already have that posted elsewhere here on the forum.

My install of gcc-12 is a bit more complete than was posted back in that NVidia forums thread... If you want to see how I did that, I'll post it from my admin journal notes.

---

### Post by sakalaboator on 2024-01-14
> **MAFoElffen said:**
> I said this in  [Post #6]("https://ubuntuforums.org/showthread.php?t=2494273&p=14174443#post14174443")... And explained "the why". That Kernel 6.5.0-14 was compiled with ggc-12, so that the drivers need to be matched to that... When I said that, a few here said they didn't want to go that way. LOL. I understand that. Mantic & Noble do not have a problem, but those are already using newer gcc-12 by default. I didn't realize then, that older legacy drivers (304, 390, 410) would still not build with Ubuntu 22.04 & gcc-12.

I now have one old laptop with nvidia-driver-390 with 6.5 removed and pinned to 6.2 for that machine. But my other machines are running fine with nvidia-driver-535... I can post those notes for those interested, and with old legacy drivers... I already have that posted elsewhere here on the forum.

My install of gcc-12 is a bit more complete than was posted back in that NVidia forums thread... If you want to see how I did that, I'll post it from my admin journal notes.

You are right! Thanks!

---

### Post by MAFoElffen on 2024-01-15
If now solved: Please visit the "Thread Tools" link in the upper right of the page & mark this thread as "Solved"... So that other may find your solution to help them with resolving this problem.

I have a felling that within the next few years, with how this has been going with kernel series changes, and now the announcement that LTS versions are going to be getting longer support... I'm just going to post both my fixes in this post, so that other may be able to find a solution to their similar problem. Thank you for the opportunity to look into this and helping. That way, we both can share how to solve this for others. I'll get the Moderators to add the link to this post to Post #2 of my Graphics Resolution Sticky.

To check which Compiler the system is using and compare it to what the current kernel was compiled with:
```

grep -e 'linux-gnu-gcc-' /proc/version
uname -r
gcc --version | grep -e 'gcc'

```
To install and change gcc compilers:

NVidia drivers sometime have a problem compiling the drivers if there is too much of a difference between the installed compiler and the version of compiler the running kernel was compiled with... Solution- install that compiler. This works right now for recently supported drivers (with kernel 6.5.0), but not currently for legacy drivers. For that work-around, skip this, and see below to run the working kernel...

Install the matching compiler:
```

sudo apt update
sudo apt install gcc-12 g++-12

```
Look to see which compiler pieces are installed
```

apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed

```
For example, mine:
```

mafoelffen@msi-ubuntu:~$ apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed
Listing... Done
g++-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
g++-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed]
gcc-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
gcc-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed,automatic]

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name gcc-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-12 -> x86_64-linux-gnu-gcc-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-11 -> x86_64-linux-gnu-gcc-11

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name g++-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-12 -> x86_64-linux-gnu-g++-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-11 -> x86_64-linux-gnu-g++-11

```
Add them to an update-alternatives group
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12

```
Temporarily pick gcc-12
 ```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc

There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
  2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 2

```
Reinstall my driver
```

sudo apt install --yes nvidia-driver-535 nvidia-dkms-535

```
Optionally, install Nvidia Cuda
```

sudo apt install --yes nvidia-cuda-toolkit

```
Reboot to test

After you are through, rest the compiler back to what it was...
```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc
There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
* 2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 1
update-alternatives: using /usr/bin/gcc-11 to provide /usr/bin/gcc (gcc) in manual mode

```
If this work-around helped, then join this Bug Report as "Also Affects Me": [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

[HR][/HR]Updated: For NVidia legacy driver 390 for Jammy and Mantic, use this PPA (credit Yellow Pasque): [https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages](https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages)
Tested. Works with 6.5.0 series kernels.

Old outdated work-around
Legacy Drivers: Use 6.2.0 series kernels...
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
When they come up with a fix to compile NVidia Legacy drivers with Linux kernel 6.5 series kernels, then you can re-add that kernel series by unpinning the kernels via
```

sudo apt-mark unhold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt update && sudo apt upgrade

```

---

### Post by johndpope on 2024-01-17
almost helpful - but hit a snag - need step 0 to be remove existing alternatives.

[COLOR=#ECECF1][FONT=Söhne]error - sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12 -(torch2) &#10140;  ~ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12update-alternatives: error: alternative g++ can't be slave of gcc: it is a master alternative

[/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=&quot]sudo update-alternatives --remove gcc /usr/bin/gcc-11sudo update-alternatives --remove gcc /usr/bin/gcc-12sudo update-alternatives --remove g++ /usr/bin/g++-11sudo update-alternatives --remove g++ /usr/bin/g++-12[/FONT][/COLOR]



> **MAFoElffen said:**
> If now solved: Please visit the "Thread Tools" link in the upper right of the page & mark this thread as "Solved"... So that other may find your solution to help them with resolving this problem.

I have a felling that within the next few years, with how this has been going with kernel series changes, and now the announcement that LTS versions are going to be getting longer support... I'm just going to post both my fixes in this post, so that other may be able to find a solution to their similar problem. Thank you for the opportunity to look into this and helping. That way, we both can share how to solve this for others. I'll get the Moderators to add the link to this post to Post #2 of my Graphics Resolution Sticky.

To check which Compiler the system is using and compare it to what the current kernel was compiled with:
```

grep -e 'linux-gnu-gcc-' /proc/version
uname -r
gcc --version | grep -e 'gcc'

```
To install and change gcc compilers:

NVidia drivers sometime have a problem compiling the drivers if there is too much of a difference between the installed compiler and the version of compiler the running kernel was compiled with... Solution- install that compiler. This works right now for recently supported drivers (with kernel 6.5.0), but not currently for legacy drivers. For that work-around, skip this, and see below to run the working kernel...

Install the matching compiler:
```

sudo apt update
sudo apt install gcc-12 g++-12

```
Look to see which compiler pieces are installed
```

apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed

```
For example, mine:
```

mafoelffen@msi-ubuntu:~$ apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed
Listing... Done
g++-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
g++-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed]
gcc-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
gcc-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed,automatic]

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name gcc-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-12 -> x86_64-linux-gnu-gcc-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-11 -> x86_64-linux-gnu-gcc-11

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name g++-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-12 -> x86_64-linux-gnu-g++-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-11 -> x86_64-linux-gnu-g++-11

```
Add them to an update-alternatives group
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12

```
Temporarily pick gcc-12
 ```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc

There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
  2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 2

```
Reinstall my driver
```

sudo apt install --yes nvidia-driver-535 nvidia-dkms-535

```
Optionally, install Nvidia Cuda
```

sudo apt install --yes nvidia-cuda-toolkit

```
Reboot to test

After you are through, rest the compiler back to what it was...
```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc
There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
* 2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 1
update-alternatives: using /usr/bin/gcc-11 to provide /usr/bin/gcc (gcc) in manual mode

```
Legacy Drivers: Use 6.2.0 series kernels...
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
When they come up with a fix to compile NVidia Legacy drivers with Linux kernel 6.5 series kernels, then you can re-add that kernel series by unpinning the kernels via
```

sudo apt-mark unhold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt update && sudo apt upgrade

```

---

### Post by MAFoElffen on 2024-01-17
> **johndpope said:**
> almost helpful - but hit a snag - need step 0 to be remove existing alternatives.
```

error - sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12 -(torch2) &#10140;  ~ sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12update-alternatives: error: alternative g++ can't be slave of gcc: it is a master alternative

sudo update-alternatives --remove gcc /usr/bin/gcc-11sudo update-alternatives --remove gcc /usr/bin/gcc-12sudo update-alternatives --remove g++ /usr/bin/g++-11sudo update-alternatives --remove g++ /usr/bin/g++-12
```

A few different ways...

The correct way for most people...

List what is there in that section:
```

$ sudo update-alternatives --list gcc
/usr/bin/gcc-10
/usr/bin/gcc-11
/usr/bin/gcc-12

```
Remove one
```

$ sudo update-alternatives --remove gcc /usr/bin/gcc-10
$ sudo update-alternatives --list 
/usr/bin/gcc-11
/usr/bin/gcc-12

```
Remove all... in gcc
```

$ sudo update-alternatives --remove-all gcc

```
Removes all

The alternate methods
```

$ grep . /var/lib/dpkg/alternatives/gcc
manual
/usr/bin/gcc
g++
/usr/bin/g++
gcov
/usr/bin/gcov
/usr/bin/gcc-11
10
/usr/bin/g++-10
/usr/bin/gcov-10
11
/usr/bin/g++-11
/usr/bin/gcov-11
/usr/bin/gcc-12
12
/usr/bin/g++-12
/usr/bin/gcov-12

```
Open & edit the file to remove one...
```

sudo nano /var/lib/dpkg/alternatives/gcc

```
Remove one (manually)
```

manual
/usr/bin/gcc
g++
/usr/bin/g++
gcov
/usr/bin/gcov
/usr/bin/gcc-11
10
/usr/bin/g++-10
/usr/bin/gcov-10
11
/usr/bin/g++-11
/usr/bin/gcov-11
/usr/bin/gcc-12
12
/usr/bin/g++-12
/usr/bin/gcov-12

```
Remove all (manually)
```

sudo rm /var/lib/dpkg/alternatives/gcc

```
With manually, one typo and it's toast. Keep a backup to restore, or delete and start over.

EDIT: For FYI... If you do this, that is all the sections within update-alternatives.
```

ls /var/lib/dpkg/alternatives/

```

---

### Post by habahnow on 2024-01-18
> **MAFoElffen said:**
>  
...
NVidia drivers sometime have a problem compiling the drivers if there is too much of a difference between the installed compiler and the version of compiler the running kernel was compiled with... Solution- install that compiler. This works right now for recently supported drivers (with kernel 6.5.0), but not currently for legacy drivers. For that work-around, skip this, and see below to run the working kernel...
...


What would you define as a legacy driver? I looked it up and found the following link from Nvidia that mention legacy cards: [https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)
Yet my graphics card wasn't listed (GTX 960). 
Doing the non-legacy card steps didn't resolve the issues I encountered (FPS drops while gaming), but doing your legacy steps did resolve my issues. 
In order to help other people that come across this thread, is the link I provided a good but incomplete list of legacy cards? or is there a more comprehensive list or rule to establish this? 

Thanks for all of your help!

---

### Post by MAFoElffen on 2024-01-18
If you did
```

sudo lspci -nnnk | grep -A3 -E 'VGA|Display|3D'

```
By the chip ID, looked up here: [http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/supportedchips.html)

You will see that that card is still supported by the 535.154.05 driver...

I go the the Nvidia Driver support page and look up the GPU, then look at the readme's to see what is supported.
I often visit these two links first:
[https://www.nvidia.com/en-us/drivers/unix/](https://www.nvidia.com/en-us/drivers/unix/)
[https://www.nvidia.com/download/find.aspx](https://www.nvidia.com/download/find.aspx)

---

### Post by BicyclerBoy on 2024-01-18
Near future crystal ball gazing:
The Nvidia Maxwell 900s & Pascal 1000 will not be supported by the new open source kernel module because they do not have the GSP processor.
Both nouveau & Nvidia will use the new module.
The Maxwell & Pascal cards have very bad support in nouveau because the firmware is not available or not distributable..
So It is possible both of these will be dropped into another legacy version when the open source kernel module is deemed to be stable/feature set complete.

Cards prior to Maxwell were the sweet-spot for performance with nouveau which is a shame as the 960/970 were a big generational step in the day.

---

### Post by MAFoElffen on 2024-01-19
> **BicyclerBoy said:**
> Near future crystal ball gazing:
[COLOR=#ff0000]The Nvidia Maxwell 900s & Pascal 1000 will not be supported by the new open source kernel module because they do not have the GSP processor.[/COLOR]
Both nouveau & Nvidia will use the new module.
The Maxwell & Pascal cards have very bad support in nouveau because the firmware is not available or not distributable..
So It is possible both of these will be dropped into another legacy version when the open source kernel module is deemed to be stable/feature set complete.

Cards prior to Maxwell were the sweet-spot for performance with nouveau which is a shame as the 960/970 were a big generational step in the day.
Nouveau = the Opensource driver... Which does not support "compute" or GSP...

What are you trying to say? Do you even know what the GPU System Processor is and what they are on? An RTX 4090 does not have GSP turned on by default... Nor will the RTX 5090 when it is released. It takes the non-free firmware to support that, and some other things turned on in non-free modules

From: [http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/gsp.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/535.154.05/README/gsp.html)
> 
Turing and later GPUs [COLOR=#FF0000]are capable[/COLOR] of using the GSP firmware by setting the kernel module parameter NVreg_EnableGpuFirmware=1. However, note feature and GPU support limitations below.

The following GPUs default to using the GSP firmware: 
[TABLE="class: grid, width: 500, align: left"]
[TR]
[TD]NVIDIA GPU product[/TD]
[TD]Device PCI ID[/TD]
[/TR]
[TR]
[TD]Tesla T10[/TD]
[TD]1E37 10DE 1370[/TD]
[/TR]
[TR]
[TD]NVIDIA T4G[/TD]
[TD]1EB4 10DE 157D[/TD]
[/TR]
[TR]
[TD]Tesla T4[/TD]
[TD]1EB8[/TD]
[/TR]
[TR]
[TD]NVIDIA T4 32GB[/TD]
[TD]1EB9[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PG509-200[/TD]
[TD]20B0 10DE 1450[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-SXM4-40GB[/TD]
[TD]20B0[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PCIE-40GB[/TD]
[TD]20B1 10DE 145F[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-SXM4-80GB[/TD]
[TD]20B2 10DE 1463[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-SXM4-80GB[/TD]
[TD]20B2 10DE 147F[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-SXM4-80GB[/TD]
[TD]20B2 10DE 1484[/TD]
[/TR]
[TR]
[TD]NVIDIA PG506-242[/TD]
[TD]20B3 10DE 14A7[/TD]
[/TR]
[TR]
[TD]NVIDIA PG506-243[/TD]
[TD]20B3 10DE 14A8[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PCIE-80GB[/TD]
[TD]20B5 10DE 1533[/TD]
[/TR]
[TR]
[TD]NVIDIA PG506-230[/TD]
[TD]20B6 10DE 1491[/TD]
[/TR]
[TR]
[TD]NVIDIA PG506-232[/TD]
[TD]20B6 10DE 1492[/TD]
[/TR]
[TR]
[TD]NVIDIA A30[/TD]
[TD]20B7 10DE 1532[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PG506-207[/TD]
[TD]20F0 10DE 1583[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PCIE-40GB[/TD]
[TD]20F1 10DE 145F[/TD]
[/TR]
[TR]
[TD]NVIDIA A100-PG506-217[/TD]
[TD]20F2 10DE 1584[/TD]
[/TR]
[TR]
[TD]NVIDIA A40[/TD]
[TD]2235 10DE 145A[/TD]
[/TR]
[TR]
[TD]NVIDIA A10[/TD]
[TD]2236[/TD]
[/TR]
[TR]
[TD]NVIDIA A10G[/TD]
[TD]2237[/TD]
[/TR]
[TR]
[TD]NVIDIA A16[/TD]
[TD]25B6 10DE 14A9[/TD]
[/TR]
[TR]
[TD]NVIDIA A2[/TD]
[TD]25B6 10DE 157E[/TD]
[/TR]
[TR]
[TD]NVIDIA A800-80[/TD]
[TD]20F5[/TD]
[/TR]
[TR]
[TD]NVIDIA A800-40[/TD]
[TD]20F6[/TD]
[/TR]
[TR]
[TD]NVIDIA L40[/TD]
[TD]26B5[/TD]
[/TR]
[TR]
[TD]NVIDIA L40G[/TD]
[TD]26B8[/TD]
[/TR]
[TR]
[TD]NVIDIA L4[/TD]
[TD]27B8[/TD]
[/TR]
[/TABLE]

But those are all compute modules...

As for Nouveau. things are well supported (albeit being tragically freaking buggy for a bit last year in the newer kernels for the RTX2060's):
[https://nouveau.freedesktop.org/FeatureMatrix.html](https://nouveau.freedesktop.org/FeatureMatrix.html)
[https://nouveau.freedesktop.org/CodeNames.html](https://nouveau.freedesktop.org/CodeNames.html)

I don't know. Are you bored? It seems like I spend a lot of time clearing up things that you bring up, to clarify what you mention off-hand which confuses people with their problems... Instead of making things more clear. Are you not here to help and assist people?

Maybe I should not spend so much time explaining these things to you. I and a few others here help test the Dev systems and drivers. Maybe you should help spend some time helping with that testing so you can see for yourself and what it takes to make them work, and how to fix them when they are not.

I am really trying my best to be polite.

---

### Post by BicyclerBoy on 2024-01-19
Truly sorry to offend.
There was discussion around what was legacy.
What I said was Near future crystal ball gazing .
I can now see this was not clear enough.
I was only guessing about the future legacy plans for the Maxwell & Pascal cards.

As far as I understand none of the newer cards can work well without the GSP support, GTX1650 & later.
But nouveau is working on this.

---

### Post by MAFoElffen on 2024-01-20
@BicyclerBoy

No offense taken at all. 

Maybe we should PM, and clear some things up? If a good idea, please PM me. 

That way we don't muddy us this Thread.

---

### Post by looki901 on 2024-02-09
> **MAFoElffen said:**
> If now solved: Please visit the "Thread Tools" link in the upper right of the page & mark this thread as "Solved"... So that other may find your solution to help them with resolving this problem.

I have a felling that within the next few years, with how this has been going with kernel series changes, and now the announcement that LTS versions are going to be getting longer support... I'm just going to post both my fixes in this post, so that other may be able to find a solution to their similar problem. Thank you for the opportunity to look into this and helping. That way, we both can share how to solve this for others. I'll get the Moderators to add the link to this post to Post #2 of my Graphics Resolution Sticky.

To check which Compiler the system is using and compare it to what the current kernel was compiled with:
```

grep -e 'linux-gnu-gcc-' /proc/version
uname -r
gcc --version | grep -e 'gcc'

```
To install and change gcc compilers:

NVidia drivers sometime have a problem compiling the drivers if there is too much of a difference between the installed compiler and the version of compiler the running kernel was compiled with... Solution- install that compiler. This works right now for recently supported drivers (with kernel 6.5.0), but not currently for legacy drivers. For that work-around, skip this, and see below to run the working kernel...

Install the matching compiler:
```

sudo apt update
sudo apt install gcc-12 g++-12

```
Look to see which compiler pieces are installed
```

apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed

```
For example, mine:
```

mafoelffen@msi-ubuntu:~$ apt list g{cc,++}-*{0,1,2,3,4,5,6,7,8,9} --installed
Listing... Done
g++-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
g++-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed]
gcc-11/jammy-updates,jammy-security,now 11.4.0-1ubuntu1~22.04 amd64 [installed,automatic]
gcc-12/jammy-updates,jammy-security,now 12.3.0-1ubuntu1~22.04 amd64 [installed,automatic]

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name gcc-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-12 -> x86_64-linux-gnu-gcc-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/gcc-11 -> x86_64-linux-gnu-gcc-11

mafoelffen@msi-ubuntu:~$ ls -larth `find /usr/bin/ -name g++-*` | grep -v 'nm\|ar\|ra'
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-12 -> x86_64-linux-gnu-g++-12
lrwxrwxrwx 1 root root 23 May 13  2023 /usr/bin/g++-11 -> x86_64-linux-gnu-g++-11

```
Add them to an update-alternatives group
```

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-11 11 --slave /usr/bin/g++ g++ /usr/bin/g++-11 --slave /usr/bin/gcov gcov /usr/bin/gcov-11
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 12 --slave /usr/bin/g++ g++ /usr/bin/g++-12 --slave /usr/bin/gcov gcov /usr/bin/gcov-12

```
Temporarily pick gcc-12
 ```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc

There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
  2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 2

```
Reinstall my driver
```

sudo apt install --yes nvidia-driver-535 nvidia-dkms-535

```
Optionally, install Nvidia Cuda
```

sudo apt install --yes nvidia-cuda-toolkit

```
Reboot to test

After you are through, rest the compiler back to what it was...
```

mafoelffen@msi-ubuntu:~$ sudo update-alternatives --config gcc
There are 2 choices for the alternative gcc (providing /usr/bin/gcc).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/gcc-12   12        auto mode
  1            /usr/bin/gcc-11   11        manual mode
* 2            /usr/bin/gcc-12   12        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 1
update-alternatives: using /usr/bin/gcc-11 to provide /usr/bin/gcc (gcc) in manual mode

```
If this work-around helped, then join this Bug Report as "Also Affects Me": [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

[HR][/HR]
Legacy Drivers: Use 6.2.0 series kernels...
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
When they come up with a fix to compile NVidia Legacy drivers with Linux kernel 6.5 series kernels, then you can re-add that kernel series by unpinning the kernels via
```

sudo apt-mark unhold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt update && sudo apt upgrade

```

Hello, 

I would not say that this issue is solved!

My Ubuntu is 22.04, and I installed the kernel 6.5 recently, at first it worked with the driver 535 from Nvidia in the first try, after I installed kernel 6.5 from Ubuntu Mainline Kernel Installer, but then, 2 days later my Ubuntu was failling to boot, after an automatic update. Then, looking in the foruns and reading about why nvidia driver would fail, I went to look about the version this kernel used from GCC, and there was version 13!

Why it would automatically update the kernel to a version that is compiled with an umcompatible version of GCC? 

Then, that is the reason that I cant use the nvidia driver (535), even trying to follow the steps of this tutorial. 

So, what solution I have to fix this issue and be able to install nvidia driver?

---

### Post by ubfan1 on 2024-02-09
It is not clear to me where you got the 6.5 kernel you mention compiled with gcc-13, but the kernel 6.5 from the hwe packages uses the gcc-12 compiler.
$ sudo strings vmlinuz-6.5.0-15-generic |grep gcc
Agcc,
6.5.0-15-generic (buildd@bos03-amd64-040) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #15~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Jan 12 18:54:30 UTC 2

The dependencies have been added to make the gcc-12 download also with the 6.5 kernel, and it gets used to build the nvidia.ko module automatically, no /bin/gcc link changes needed. Select the nvidia driver from the Software & Updates/Additional Drivers tab, apply changes, and the progress bar should complete without errors, automatically using the gcc-12.

---

### Post by looki901 on 2024-02-10
> **ubfan1 said:**
> It is not clear to me where you got the 6.5 kernel you mention compiled with gcc-13, but the kernel 6.5 from the hwe packages uses the gcc-12 compiler.
$ sudo strings vmlinuz-6.5.0-15-generic |grep gcc
Agcc,
6.5.0-15-generic (buildd@bos03-amd64-040) (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #15~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Fri Jan 12 18:54:30 UTC 2

The dependencies have been added to make the gcc-12 download also with the 6.5 kernel, and it gets used to build the nvidia.ko module automatically, no /bin/gcc link changes needed. Select the nvidia driver from the Software & Updates/Additional Drivers tab, apply changes, and the progress bar should complete without errors, automatically using the gcc-12.

When typing 
```
cat /proc/version
```
This is what I get 
```
Linux version 6.5.0-060500-generic (kernel@kathleen) (x86_64-linux-gnu-gcc-13 (Ubuntu 13.2.0-6ubuntu1) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.41) #202308271831 SMP PREEMPT_DYNAMIC Thu Nov 16 11:17:07 UTC 2023
```

---

### Post by MAFoElffen on 2024-02-10
@looki901 ---

Darn --- Look at this in your output:
```

    **[COLOR=#ff0000]Linux version 6.5.0-060500-generic (kernel@kathleen)[/COLOR]**     (x86_64-linux-gnu-[COLOR=#ff0000]gcc-13[/COLOR] 
    (Ubuntu 13.2.0-6ubuntu1) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.41) 
    #202308271831 SMP PREEMPT_DYNAMIC Thu Nov 16 11:17:07 UTC 2023

```

So do tell--> 6.5.0 Kernels from the 22.04.X HWE series were 6.5.0-14-generic & 6.5.0-15-generic. There were compiled with ggc-12. Where and how do you have kernel 6.5.0-060500-generic??? I don't see that kernel in any Ubuntu repo's.

What is the output of this please... Posted only within CODE Tags:
```

apt-cache policy linux-image-6.5.0-060500-generic

```
I'm thinking that will come back as blank, because I don't recognize it as an Ubuntu (compiled) Kernel through the normal channels. It didn't happen during a normal update for the HWE Series kernels channel. So saying "it is not fixed", is a misnomer in your case, because it falls outside of those channels. Right? If not, then you still have "something else" going on, causing you to have that OOT kernel, and then should be investigated.

If you look at the format of /proc/version, the field in the first parentheses is the User who built the kernel...

For mine:
```

mafoelffen@msi-ubuntu:~$ grep . /proc/version
Linux version 6.5.0-14-generic [COLOR=#ff0000](buildd@lcy02-amd64-110)[/COLOR] (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2

```
That tells me mine were built by Ubuntu, through the normal launchpad built channels. Your's being "kernel@kathleen" tells me, that was a home-brew compiled kernel that was self-compiled outside the normal channels. 

So, if I compile a kernel myself, I understand that is outside of the blame of Ubuntu... and that I am responsible for what was my own self-inflicted problem. You understand that right? This is where "third-party" [COLOR=#ff0000]pieces[/COLOR], make things complicated, when it comes to updates.

But following the same logic, building a kernel module for that would need the same compiler as that target kernel was compiled with, in your case gcc-13.

---

### Post by looki901 on 2024-02-10
> **MAFoElffen said:**
> @looki901 ---

Darn --- Look at this in your output:
```

    **[COLOR=#ff0000]Linux version 6.5.0-060500-generic (kernel@kathleen)[/COLOR]**     (x86_64-linux-gnu-[COLOR=#ff0000]gcc-13[/COLOR] 
    (Ubuntu 13.2.0-6ubuntu1) 13.2.0, GNU ld (GNU Binutils for Ubuntu) 2.41) 
    #202308271831 SMP PREEMPT_DYNAMIC Thu Nov 16 11:17:07 UTC 2023

```

So do tell--> 6.5.0 Kernels from the 22.04.X HWE series were 6.5.0-14-generic & 6.5.0-15-generic. There were compiled with ggc-12. Where and how do you have kernel 6.5.0-060500-generic??? I don't see that kernel in any Ubuntu repo's.

What is the output of this please... Posted only within CODE Tags:
```

apt-cache policy linux-image-6.5.0-060500-generic

```
I'm thinking that will come back as blank, because I don't recognize it as an Ubuntu (compiled) Kernel through the normal channels. It didn't happen during a normal update for the HWE Series kernels channel. So saying "it is not fixed", is a misnomer in your case, because it falls outside of those channels. Right? If not, then you still have "something else" going on, causing you to have that OOT kernel, and then should be investigated.

If you look at the format of /proc/version, the field in the first parentheses is the User who built the kernel...

For mine:
```

mafoelffen@msi-ubuntu:~$ grep . /proc/version
Linux version 6.5.0-14-generic [COLOR=#ff0000](buildd@lcy02-amd64-110)[/COLOR] (x86_64-linux-gnu-gcc-12 (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0, GNU ld (GNU Binutils for Ubuntu) 2.38) #14~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Mon Nov 20 18:15:30 UTC 2

```
That tells me mine were built by Ubuntu, through the normal launchpad built channels. Your's being "kernel@kathleen" tells me, that was a home-brew compiled kernel that was self-compiled outside the normal channels. 

So, if I compile a kernel myself, I understand that is outside of the blame of Ubuntu... and that I am responsible for what was my own self-inflicted problem. You understand that right? This is where "third-party" [COLOR=#ff0000]pieces[/COLOR], make things complicated, when it comes to updates.

But following the same logic, building a kernel module for that would need the same compiler as that target kernel was compiled with, in your case gcc-13.

You are right about the output of that command, it came out blank. And you are also right about that something is going on, and I have no idea about what is going on, I did not choose that kernel version and "source" on purpose.

I clicked to see what is the PPA from the Mainline Kernels (the app from the screenshot), and it directs me to the Ubuntu Repo ([https://kernel.ubuntu.com/mainline/](https://kernel.ubuntu.com/mainline/)), and that is what I was expecting, it to be from the Ubuntu Repo, and that is why I thought the issue with the Nvidia drivers was not fixed for this kernel version.

I need some help to get the right kernel installed in my Ubuntu 22.04, and remove the current wrong one. What you would recommend?

---

### Post by MAFoElffen on 2024-02-10
So yes, you added a kernel from outside the normal channels. The Mainline PPA kernels are not Ubuntu Prep'ed, tweaked, and optimized. They also [COLOR=#ff0000]do not contained any security patches[/COLOR].

The Mainline kernel PPA is for testing kernels from the kernel.org git repo's. At launchpad, often times when there is a suspected kernel problem, they will recommend trying a certain version (directed) of that PPA, to see if that kernel resolves the problem... 

They were never meant for everyday use by users... Especially since, like I said, they do not receive any security patches.

But in saying that, that tells them if it was something they did in their set compile options with their Ubuntu specific tweaks, or how the kernel was compiled as generic options from kernel.org. That will tell them if it is an Ubuntu problem  or an upstream kernel problem.

If you do this
```

apt list linux-*-6.5.0-060500-* --installed

```
That will tell you what package names you need to use to remove them, in the format of
```

sudo apt remove --purge <package_name> [<other package names>]

```

---

### Post by looki901 on 2024-02-10
Thank you for the help!

That solved the issue, and I got back to the old kernel at boot, then I used this command to get the right official kernel.

sudo apt install linux-image-generic-hwe-22.04

---

### Post by father_ted on 2024-02-15
I'm using vanilla LTS with HWE. I've started to get :
NVRM: loading NVIDIA UNIX x86_64 Kernel Module  535.154.05  Thu Dec 28 15:37:48 UTC 2023
nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  535.154.05  Thu Dec 28 15:51:29 UTC 2023
So it looks like something has been done about this in the last few updates.

---

### Post by scottbomb on 2024-02-19
> If this work-around helped, then join this Bug Report as "Also Affects Me": [https://ubuntuforums.org/showthread....4#post14175164](https://ubuntuforums.org/showthread....4#post14175164)

That link brings us back to this page, not a launchpad bug report.

---

### Post by ubfan1 on 2024-02-19
Oops that should be [https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457) for the bug report.

---

### Post by MAFoElffen on 2024-02-19
New work-around for Jammy and Mantic for nvidia-drivers-390, for Jammy and Mantic with kernels 6.5.0 and newer: [https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457/comments/15](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457/comments/15)

---

### Post by robaol on 2024-03-20
Hi
Thank you very much for posting so much helpful info. I am following your post #19 [ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164]("http://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164") .
My graphics card needs the 390 driver. I tried ```
sudo add-apt-repository https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages
``` , which seemed to work. When I tried ```
sudo update
``` I got a warning because it was not signed, so I added ```
--allowUnathenticated
``` and then I got a files not found error. AFA you know, do think this PPA still works? Could you please tell me what should I have done to make it work?

**** I have now seen your post on how to install nvidiaexp ppa so I will give it a try. I assume there were no problems with missing signatures.

In the meantime, I followed your previous instructions, extending them to remove all the 6.5.0-nn intervening kernel versions and that has got me going, so thanks again for your clear instructions.

On a slightly wider topic, why does the compiler version used to build the kernel impact which kernel modules can be used? I could understand if there was linkage to a newer libc and dependencies on symbol signature/call argument versions, but that doesn't seem likely in this situation?

Thanks
R

> **MAFoElffen said:**
> If now solved: Please visit the "Thread Tools" link in the upper right of the page & mark this thread as "Solved"... So that other may find your solution to help them with resolving this problem.
....

[HR][/HR]Updated: For NVidia legacy driver 390 for Jammy and Mantic, use this PPA (credit Yellow Pasque): [https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages](https://launchpad.net/~dtl131/+archive/ubuntu/nvidiaexp/+packages)
Tested. Works with 6.5.0 series kernels.

Old outdated work-around
Legacy Drivers: Use 6.2.0 series kernels...
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
When they come up with a fix to compile NVidia Legacy drivers with Linux kernel 6.5 series kernels, then you can re-add that kernel series by unpinning the kernels via
```

sudo apt-mark unhold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt update && sudo apt upgrade

```

---

### Post by MAFoElffen on 2024-03-21
> **robaol said:**
> 
On a slightly wider topic, why does the compiler version used to build the kernel impact which kernel modules can be used? I could understand if there was linkage to a newer libc and dependencies on symbol signature/call argument versions, but that doesn't seem likely in this situation?

In the NV code, in one place it uses a compiler option that is in gcc-12, but not in gcc-11 (-ftrivial-auto-var-init=zero)... But in another area, NV code checks for the version of compiler that the kernel was compiled with...

That is documented in NVidia's Doc's for "Common Problems": [https://download.nvidia.com/XFree86/Linux-x86_64/390.48/README/commonproblems.html](https://download.nvidia.com/XFree86/Linux-x86_64/390.48/README/commonproblems.html)
```

Compiling the NVIDIA kernel module gives this error:

You appear to be compiling the NVIDIA kernel module with
a compiler different from the one that was used to compile
the running kernel. This may be perfectly fine, but there
are cases where this can lead to unexpected behavior and
system crashes.

If you know what you are doing and want to override this
check, you can do so by setting IGNORE_CC_MISMATCH.

In any other case, set the CC environment variable to the
name of the compiler that was used to compile the kernel.

    

You should compile the NVIDIA kernel module with the same compiler version that was 
used to compile your kernel. Some Linux kernel data structures are dependent on the 
version of gcc used to compile it; for example, in include/linux/spinlock.h:

        ...
        * Most gcc versions have a nasty bug with empty initializers.
        */
        #if (__GNUC__ > 2)
          typedef struct { } rwlock_t;
          #define RW_LOCK_UNLOCKED (rwlock_t) { }
        #else
          typedef struct { int gcc_is_buggy; } rwlock_t;
          #define RW_LOCK_UNLOCKED (rwlock_t) { 0 }
        #endif

If the kernel is compiled with gcc 2.x, but gcc 3.x is used when the kernel interface is compiled (or vice versa), the size of rwlock_t will vary, and things like ioremap will fail. To check what version of gcc was used to compile your kernel, you can examine the output of:

    % cat /proc/version

To check what version of gcc is currently in your $PATH, you can examine the output of:

    % gcc -v

```
You'll notice they were talking about gcc-versions gcc-2.x, and gcc-3.x... That has been their practice for a very, very, very long time. gcc-3.0 was released in 2001.

---

### Post by yuralamov on 2024-03-28
Ubuntu 22.04.3, remove 6.5** + hwe. Kernel 6.2.0.26. Add nvidia repo & install cuda. Nvidia 1650 (550.54.15) Ok.

---

