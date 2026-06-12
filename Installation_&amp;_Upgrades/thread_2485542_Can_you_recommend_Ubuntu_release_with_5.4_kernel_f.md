---
title: "Can you recommend Ubuntu release with 5.4 kernel for NVIDIA 340 legacy drivers?"
date: 2023-04-01
forum: Installation &amp; Upgrades
---

### Post by escudero380 on 2023-04-01
I'm not experienced Linux user. I merely need it to compose Docker images for my projects and run integration tests with Testcontainers on IntelliJ IDEA. For now, I installed Ubuntu 22.04 next to Windows 10 and switch-boot between them when needed. The only problem is that my legacy NVIDIA GeForce 9600 GT card, which still works perfectly on Windows 10, is completely useless on Ubuntu 22.04 (well, at least not with its current 5.19 kernel). NVIDIA officials say 340.108 drivers are supported only for Linux kernels up to Linux 5.4. 

So, I'm wondering, is there any archive repository or something like that from where I can get a descent Desktop Ubuntu release running on that 5.4 kernel as the default, so that I can replace Ubuntu 22.04 with it? Can you recommend which version of Ubuntu with 5.4 kernel should I use for that reason?


P.S.
I also tried to install NVIDIA 340.108 patched drivers on Ubuntu 22.04 (from ppa:kelebek333/nvidia-legacy and the like) - but with no success.

---

### Post by Bashing-om on 2023-04-01
Hello  escudero380 - Welcome to the Forums :D

In direct response to the request for a supported 5.4 kernel - the 20.04.1 release will buy you some time.
> 
focal (20.04LTS) (kernel): Generic Linux kernel image
5.4.0.146.144 [security]: amd64

per: [https://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=focal&section=all)

Keep in mind you will have to use that ist point release to have that Generally Available kernel as later point releases go with the HardWare Enablement Stack (5.15 kernel).

[INDENT]my bit to try and help
[/INDENT]

---

### Post by MAFoElffen on 2023-04-02
> **escudero380 said:**
> The only problem is that my legacy NVIDIA GeForce 9600 GT card, which still works perfectly on Windows 10, is completely useless on Ubuntu 22.04 (well, at least not with its current 5.19 kernel). 
But that is not necessarily true. That is true for the proprietary driver...

The NVIDIA GeForce 9600 GT is in the NV50 family (Tesla): CodeName NV92 (G92).

It is fully supported by the Nouveau (opensource) driver from FreeDesktop.org and is available for all Linux Distro's, in their own respective Repo's. Using that, you could be running Linux Kernel 6.2, or at least 5.19 with 22.04.2.

RE: [https://manpages.ubuntu.com/manpages/jammy/man4/nouveau.4.html](https://manpages.ubuntu.com/manpages/jammy/man4/nouveau.4.html)

---

### Post by guiverc on 2023-04-02
This was also asked at [https://askubuntu.com/questions/1461933/which-ubuntu-release-with-5-4-kernel-should-i-use-for-nvidia-340-legacy-drivers](https://askubuntu.com/questions/1461933/which-ubuntu-release-with-5-4-kernel-should-i-use-for-nvidia-340-legacy-drivers)

A quick CLI enquiry on my *non-focal *or *non-bionic* system revealed the following packages still *supported* on current releases

```

linux-generic-hwe-18.04 | 5.4.0.146.163~18.04.117 | bionic-security | amd64, arm64, armhf, i386, ppc64el, s390x
linux-generic | 5.4.0.146.144          | focal-security   | amd64, arm64, armhf, ppc64el, s390x

```

As I wrote at askubuntu, I'd for sure use Ubuntu 20.04 LTS.  Media still exists that will install the GA kernel stack, alas most of the default ISOs offered at cdimage.ubuntu.com on searches are always the latest (*meaning HWE kernel is far more likely for anything desktop related*), but if you should find them.

*Installing with any media maybe easiest & using `nomodeset`, then post-install adding the GA kernel stack.. But there are many ways to get what I suspect you want.*

---

### Post by escudero380 on 2023-04-02
> **MAFoElffen said:**
> The NVIDIA GeForce 9600 GT is in the NV50 family (Tesla): CodeName NV92 (G92).

Unfortunately, Nouveau driver gives a very low blurry screen resolution which is no match to my 1920x1080 monitor.

---

### Post by oldfred on 2023-04-02
What CPU?

I used to have the 9600. Upgraded to GT620, but in newer system found that old card was slower than the CPU's graphics.

Low end video & other Hardware comparisons, performance: 
[https://www.videocardbenchmark.net/low_end_gpus.html](https://www.videocardbenchmark.net/low_end_gpus.html) 
```

GeForce GT 620              430
 Intel® HD Graphics 4600    712  Haswell
Intel HD Graphics 620       927   Skylake
```

---

### Post by escudero380 on 2023-04-10
Thank you, guys, for your comments. Installation of nvidia-340 drivers on Ubuntu 18.04 running with older kernels up to 5.4.0-146-generic can be as trivial as executing [COLOR=#696969][FONT=courier new]$ sudo ubuntu-drivers install[/FONT][/COLOR] command from your terminal. Therefore, for those who are curious, I'll share my experience of setting up nvidia-340 drivers for systems that at the time of writing are not considered to be outdated (such as Ubuntu 20.04.6 with further promotion to Ubuntu 22.04.2). 

** 1. Ubuntu installation.**

I started with bare minimum installation of ubuntu-20.04.6-desktop-amd64 distributive, which comes with 5.15.0-69-generic kernel. 

*Note: if in the process your monitor turns off with the message like "input signal out of range", you need to restart with "nomodeset" option activated (just after restart press F6 + F6 --> choose "nomodest" --> then press ESC and proceed with the installation).*
    
After installation is complete, you may double-check your kernel version from terminal with the following command:
    
```

$ uname -r

```
    
** 2. Installation of NVIDIA-340 drivers.**

In order to install nvidia-340 drivers on Ubuntu systems running with kernels up to 5.18.x you may use ppa:kelebek333/nvidia-legacy repository:

```

 $ sudo add-apt-repository ppa:kelebek333/nvidia-legacy
 $ sudo apt-get update
 $ sudo apt install nvidia-340
 $ sudo apt install xorg-modulepath-fix
 $ sudo reboot

```
Note: the line with [COLOR=#696969][FONT=century gothic]xorg-modulepath-fix[/FONT][/COLOR] is needed only for kernels 5.11.x and higher, as it's [explained]("https://launchpad.net/~kelebek333/+archive/ubuntu/nvidia-legacy") here.

** 3. Fixing screen resolution.**

After reboot I noticed that the image was a little blurry and the maximum available screen resolution was still 1600x900 (whereas Windows 10 produces 1920x1080 with the same combination of monitor and hardware). So, it required some additional effort to get the same result on Ubuntu:
    
    3.1 Go to NVIDIA X Server Settings --> X Server Display Configuration.
    3.2 Save you current configuration to /etc/X11/xorg.conf by clicking "Save to X configuration" button.
    3.3 Then open this file (by executing [FONT=century gothic][COLOR=#696969]$ sudo gedit /etc/X11/xorg.conf[/COLOR][/FONT] from your terminal) and change the following parameters:
        
    ```

Before -->
       
   HorizSync 28.0 - 55.0
   VertRefresh 43.0 - 72.0
    
After -->
    
   HorizSync 30.0 - 83.0
   VertRefresh 56.0 - 75.0
```
    
     (check the correct diapason in the documentation for your monitor)
    
Note: for kernels 5.11.x and higher also make sure to add the following lines in the "Files" section: 

        ```

Section "Files"
   ModulePath "/usr/lib/nvidia-340/xorg"
   ModulePath "/usr/lib/xorg/modules"
EndSection
```

    3.4 Save changes and reboot. 
    
    This little trick gave me the possibility to choose the maximum screen resolution 1920x1080(16:9) instead of 1600x900.
    
You may choose to stop at this point having your Ubuntu 20.04.6 LTS running with 5.15.0-69-generic kernel and 340-drivers fully operational, but it's also possible to accept upgrade to Ubuntu-22.04.2. However, it's very likely that your nvidia-340 drivers will be wiped out after upgrade and you will have to re-install them as it was described in steps 2 and 3, but only ON CONDITION THAT your kernel didn't switch after upgrade. 

It is very important to follow this advice (don't switch to the higher kernels), because when I experienced with bare native installation of Ubuntu-22.04.2, which is distributed with 5.19.0-38-generic kernel, the above instructions didn't work. So, the only reasonable solution I've discovered so far, is to start with installation of ubuntu-20.04.6-desktop-amd64, followed by immediate upgrade to 22.04.2. This would preserve your 5.15.0-69-generic kernel and still make it possible to install the drivers as it was described in steps 2 and 3.

*Note: if you eventually end up with the black screen after upgrade - don't panic! Just restart Ubuntu in recovery mode, go to root (Drop to root shell prompt), delete /etc/X11/xorg.conf (by executing *[COLOR=#696969][FONT=courier new]$ rm /etc/X11/xorg.conf[/FONT][/COLOR]*), then reboot and reinstall the drivers. In the worst scenario, try to choose dpkg (Repair broken packages) option in recovery mode.*

UPD: 

Although, it's reported by many that you can install NVIDIA legacy drivers on Ubuntu running with the higher kernels (such as 5.19, 6.0, 6.1, 6.2), I can't personally confirm that, because I tested those patches with 5.19.0-38-generic kernel - with no success! If you are interested, though, you may give it a try following [this instruction]("https://www.if-not-true-then-false.com/2021/debian-ubuntu-linux-mint-nvidia-guide/").

---

