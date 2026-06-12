---
title: "CUDA 12.1.1 Nvidia 530 Ubu 22.04 LTS Package dependency problem on install"
date: 2024-01-27
forum: Installation &amp; Upgrades
---

### Post by rocky714 on 2024-01-27
Hi all,

My ultimate objective is to get cuda 12.1.1 (or 12.1) installed for use with Anaconda3's Python.  I have two qualified laptops (Core i7s w/32 GB, Quadro P2000s) that I've been ping-ponging between with clean installs of Ubuntu 22.04 LTS and have had various difficulties just getting the environment to work.  The order in which Anaconda and cuda are installed seems to affect which errors are manifest but I'll just focus on the current attempt with is to install cuda after Anaconda3.

It seems that to get cuda to work with python, the current limitation is version 12.1 for cuda (as opposed to 12.3 that is otherwise available) which comes with the 530 version of the video drivers for the Nvidia chip.  I know the computer should be cuda capable since an earlier attempt where I tried to install cuda first (but before I knew about the version limit for python), I installed cuda 12.3 first with the 545 video driver and it seemed to work okay.  At least, the cuda package installed, the video driver installed and was displayed in the "About" system setting and some of the cuda samples executed.  However, Anaconda didn't link in and I attribute it to Anaconda's python incompatibility with 12.3 cuda.

So, now to the current attempt.  I followed the instructions on 

[https://developer.nvidia.com/cuda-12-1-1-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local](https://developer.nvidia.com/cuda-12-1-1-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=22.04&target_type=deb_local)

Previously, I had followed the detailed instructions  in nvidia's detailed docs ([https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)) in the instructions but a) there are many extraneous features I don't think I need, at least yet, b) the instructions for 12.1 eventually feed you back to the instructions for 12.3 and c) once you've done this 2 or 6 times ](*,), you're apt to strip this down to the minimum to minimize the BS to "is this going to work or not" level.  Getting this down to the minimum for 12.1 after Anaconda3 has been installed, on the very last instruction, i.e.

sudo apt-get -y install cuda

the following results where the gist seems to be that package dependencies prevent the last package set (pasted in at the bottom) are prevented from being processed.  Various attempts at fixing this don't work so please don't suggest "apt --fix-broken install" as that won't work.  I've searched various fixes and they don't work and that's really not what I'm looking for.  I can strip this back to the bare bones and get back to the base install.  And I can use the other machine to get back to a bare install.  I'm looking for a way to get either cuda 12.1 to install and work with anaconda3 or do I need to backlevel to an earlier version of Ubunta, or cuda (or last option python).  I need to get to my ultimate objectve eventually.  Thanks to all in advance who can offer insight.

-Rocky714

dpkg: dependency problems prevent configuration of nvidia-driver-530:
 nvidia-driver-530 depends on nvidia-dkms-530 (= 530.30.02-0ubuntu1); however:
  Package nvidia-dkms-530 is not configured yet.

dpkg: error processing package nvidia-driver-530 (--configure):
 dependency problems - leaving unconfigured
Setting up libcublas-dev-12-1 (12.1.3.1-1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
               dpkg: dependency problems prevent configuration of cuda-drivers:
 cuda-drivers depends on cuda-drivers-530 (= 530.30.02-1); however:
  Package cuda-drivers-530 is not configured yet.

dpkg: error processing package cuda-drivers (--configure):
 dependency problems - leaving unconfigured
Setting up cuda-opencl-dev-12-1 (12.1.105-1) ...
No apport report written because MaxReports is reached already
                                                              Setting up cuda-libraries-dev-12-1 (12.1.1-1) ...
dpkg: dependency problems prevent configuration of cuda-runtime-12-1:
 cuda-runtime-12-1 depends on cuda-drivers (>= 530.30.02); however:
  Package cuda-drivers is not configured yet.

dpkg: error processing package cuda-runtime-12-1 (--configure):
 dependency problems - leaving unconfigured
Setting up cuda-visual-tools-12-1 (12.1.1-1) ...
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of cuda-12-1:
 cuda-12-1 depends on cuda-runtime-12-1 (>= 12.1.1); however:
  Package cuda-runtime-12-1 is not configured yet.

dpkg: error processing package cuda-12-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cuda:
 cuda depends on cuda-12-1 (>= 12.1.1); however:
  Package cuda-12-1 is not configured yet.

dpkg: error processing package cuda (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cuda-demo-suite-12-1:
 cuda-demo-suite-12-1 depends on cuda-runtime-12-1; however:
  Package cuda-runtime-12-1 is not configured yet.

dpkg: error processing package cuda-demo-suite-12-1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
    Setting up cuda-tools-12-1 (12.1.1-1) ...
Setting up cuda-toolkit-12-1 (12.1.1-1) ...
Processing triggers for desktop-file-utils (0.26-1ubuntu3) ...
Processing triggers for gnome-menus (3.36.0-1ubuntu3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.6) ...
Processing triggers for man-db (2.10.2-1) ...
Processing triggers for mailcap (3.70+nmu1ubuntu1) ...
Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-15-generic
Errors were encountered while processing:
 nvidia-dkms-530
 cuda-drivers-530
 nvidia-driver-530
 cuda-drivers
 cuda-runtime-12-1
 cuda-12-1
 cuda
 cuda-demo-suite-12-1
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by MAFoElffen on 2024-01-27
I skimmed though it. TL;DR. At least not all the details.

Why not try with nvidia-driver-535? I feel like that would satisfy a lot of those dependency issues. 

545 is not stable yet for Linux. I have a friend who is helping test the Linux patches for 545... So I have sort of an inside track on that. 530 is not used much. 535 is stable and working great, especially with Cuda 12 and newer. 

More important, look at this post for upgrading your gcc and g++ compilers to version 12. If on 22.04.3, the compiler is gcc-11.4 and the kernel for 6.5.0-14 was compiled with gcc-12. I'm surprised you haven't hit that error yet as explicitly named, but that is part of that eror.
RE: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)

Just saying.

---

### Post by rocky714 on 2024-01-28
I tried 535 after getting the above posted result hoping that it would bypass too-old revisions.  It didn't fix anything.  I'm not sure how to install 535 with 12.1 CUDA independently since the package (.deb) comes with 530 as part of the package.

I'll check the versions of the compilers but updates were part of the install process so I'm pretty sure they're up-to-date.  But I'll double check.

-Rocky714

---

### Post by MAFoElffen on 2024-01-28
I started this thread: [https://ubuntuforums.org/showthread.php?t=2494834](https://ubuntuforums.org/showthread.php?t=2494834)

And filed this bug report: [https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/2051457)

...to try to get a fix pushed through the normal updates channel with this. I would appreciate and I think it would be in all of our best interest to join that bug "I am also affected" so we can add some weight to getting this resolved.

I agree that we shouldn't need a "work-around" to make make this work.
```

mafoelffen@msi-ubuntu:~$ nvidia-smi
Sun Jan 28 12:19:44 2024       
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.154.05             Driver Version: 535.154.05   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA GeForce GTX 1660 Ti     Off | 00000000:01:00.0  On |                  N/A |
|  0%   32C    P8               8W / 130W |    125MiB /  6144MiB |      2%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A      4568      G   /usr/lib/xorg/Xorg                           84MiB |
|    0   N/A  N/A      5366      G   /usr/bin/gnome-shell                         29MiB |
|    0   N/A  N/A     12469      G   ...irefox/3728/usr/lib/firefox/firefox        8MiB |
+---------------------------------------------------------------------------------------+

```
Cuda, with mine, I already had the 535 driver installed before I installed Cuda. So it already saw that the driver version or newer was there. Once it saw that was there, it didn't try to reinstall the video driver = it skipped that step. But the Cuda version of mine is 12.2...

---

### Post by ubfan1 on 2024-01-28
I gave up on Nvidia's CUDA deb installation awhile back -- when a normal video driver update wanted to delete all the CUDA files! Totally messed up dependencies.  Get your system running with your (latest?) selected video driver, then use Nvidia's .run script.  Now a 1GB+ script is not something I can look at nor would run as root, and since the only functionality I want is to copy some files around, I run it as a user, and see where it fails.  It wants to write into /usr/local/cudaxxx, but even if I make the directory owned and writable by a user, it still fails trying to unnecessarily create the dir. OK as root, change the ownership of /usr/local to the user, then the script is happy (remember to change it back).  Reject the offer of the unwanted version of the video driver, which should already be installed and working. Under the options, override all the system areas the script thinks it needs to write into -- use the /usr/local/cudaxxx/lib and /usr/local/cudaxxx/bin areas instead. I ignore the icons the script wants to write into /usr/share too -- never needed them. The full CUDA install for you selected version will now be under /usr/local/cuda-12.1 (or whatever version you selected).  Other CUDA versions may also be installed without problems.  The PATH and LD_LIBRARY_PATH modifications will select which CUDA version you are working with. See:
[https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063)
[https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010](https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010)

The standard repos have a CUDA install, but you cannot pick a specific version.  I've never actually used that method since I generally had version requirements imposed by other software.

---

### Post by rocky714 on 2024-01-28
Thanks,  				 					[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=1044547") 				 				 					 						 	[**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1044547"). I'd be happy to add my name to support the urgency of addressing this  bug.  In the interest of expediency, however, (and I'm sorry if this is a stupid question), but based on your experience, is your expectation that installing the 535 drivers first will allow cuda 12.1 toolkit to install and  setup properly?  I know you can't be certain but a guess is acceptable at this point.  I can't use cuda 12.2 because python and pytorch and torchvision is not yet compatible with those versions.  Thanks.

-rocky714

---

### Post by rocky714 on 2024-01-28
Thanks, ubfan1.  I'll try your solution if I can't get MAFoElffen's suggestion to work.  (Man, I've got alot *more* work to do.  This is way harder than it ought to be).

-rocky714

---

### Post by ubfan1 on 2024-01-28
Yes, my current latest CUDA is 12.1, and it was installed after the Nvidia driver which was current at the time.  Every few releases I install the latest CUDA, and maybe delete an old one, keeping a few cuda releases around.  The CUDA installs with all the CUDA files collected under the /usr/local/cudaxxx always work.  The only issue with running CUDA is the occasional mixup of the laptop source/sink providers (xrandr --listproviders).  When that happens, and I'm not sure why it does sometimes, the manual fix is to set two env variables before running a program:
__NV_PRIME_RENDER_OFFLOAD=1 __GLX_VENDOR_LIBRARY_NAME=nvidia <progtorun>

---

### Post by MAFoElffen on 2024-01-29
Yes, follow ubfan1's suggestions. Same as mine, as i had the video driver installed first. I have Cuda 12.2 on mine. His is running 12.1, which is what you want to run.

---

### Post by rocky714 on 2024-01-29
This may be alarmist but I don't think it because I remember this as an error that came up prior to a cascade of problems that followed.  This was the simple set of steps followed: a fresh install of Ubuntu 22.04 LTS with an update as prompted since "there have been updates since this install".  The only other step taken was customizing FIrefox.  Then, I installed nvidia driver 535 with the command 

[B]sudo apt install nvidia-driver-535 nvidia-dkms-535

[/B]The driver seemed to install (i.e., it went through the motions) but did not come up ("About" still shows "llvmpipe (LLVM 15.0.7 256 bits)" install of the Nvidia driver.  Issuing the "sudo apt-get upgrade" command yields the below message.  A couple of packages are held back.  Numerous errors follow when I've seen that before.  Autoremove doesn't do anything either, but problems will follow, I assure you.  Any recommendations?  Again, thanks in advance for the help.

-Rocky714

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gjs libgjs0g
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by ubfan1 on 2024-01-30
I have 29 packages with nvidia and 535 in the dpkg -l output (half 32 bit versions). Still, I'm not sure you got everything you need just installing the two packages you mention.  Try ubuntu-drivers install or the Software & Updates/Additional Drivers tab and select the driver you want.

---

### Post by MAFoElffen on 2024-01-30
> **rocky714 said:**
> This may be alarmist but I don't think it because I remember this as an error that came up prior to a cascade of problems that followed.  This was the simple set of steps followed: a fresh install of Ubuntu 22.04 LTS with an update as prompted since "there have been updates since this install".  The only other step taken was customizing FIrefox.  Then, I installed nvidia driver 535 with the command 

[B]sudo apt install nvidia-driver-535 nvidia-dkms-535

[/B]The driver seemed to install (i.e., it went through the motions) but did not come up ("About" still shows "llvmpipe (LLVM 15.0.7 256 bits)" install of the Nvidia driver.  Issuing the "sudo apt-get upgrade" command yields the below message.  A couple of packages are held back.  Numerous errors follow when I've seen that before.  Autoremove doesn't do anything either, but problems will follow, I assure you.  Any recommendations?  Again, thanks in advance for the help.

-Rocky714

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  [COLOR=#ff0000]gjs libgjs0g[/COLOR]
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

There has been some reported problems with those two packages. That is why they are being held back. (Until they sort that out.)

---

### Post by rocky714 on 2024-01-30
I tried:

sudo ubuntu-drivers install nvidia:535

and the response is "All the available drivers are already installed".  If that's the case, and the 535 drivers need to be installed before I can install CUDA 12.1, I guess that means I'm stuck.  Is there any other conclusion to reach.  I mean, I think I see others with that setup and somehow got it to work or maybe it's an illusion.  How could it have passed testing have on Nvidia's part?

Anyway, I'll add my "I have this problem too" to the reference.

-Rocky714

---

### Post by ubfan1 on 2024-01-30
$ ubuntu-drivers install foo:bar
All the available drivers are already installed.

Names are critical, try sudo ubuntu-drivers install nvidia-driver-535

Get the available drivers from ubuntu-drivers list

---

### Post by rocky714 on 2024-02-11
(Sorry for the delay, I've been on travel.)  I first did a 

"sudo ubuntu-drivers list"

the result of which was 

"nvidia-driver-535-server, (kernel modules provided by linux-modules-nvidia-535-server-generic-hwe-22.04)
nvidia-driver-450-server, (kernel modules provided by nvidia-dkms-450-server)
nvidia-driver-470, (kernel modules provided by linux-modules-nvidia-470-generic-hwe-22.04)
nvidia-driver-525, (kernel modules provided by linux-modules-nvidia-525-generic-hwe-22.04)
nvidia-driver-390, (kernel modules provided by nvidia-dkms-390)
nvidia-driver-418-server, (kernel modules provided by nvidia-dkms-418-server)
nvidia-driver-545, (kernel modules provided by linux-modules-nvidia-545-generic-hwe-22.04)
nvidia-driver-525-server, (kernel modules provided by linux-modules-nvidia-525-server-generic-hwe-22.04)
nvidia-driver-470-server, (kernel modules provided by linux-modules-nvidia-470-server-generic-hwe-22.04)
nvidia-driver-535, (kernel modules provided by linux-modules-nvidia-535-generic-hwe-22.04)"

It appears then that I have all the drivers I needed available to me.  I executed the recommended command:

"sudo ubuntu-drivers install nvidia-driver-535"

and the response was

"All the available drivers are already installed."

Yet, in the "About" box in the settings still shows

"llvmpipe (LLVM 15.0.7, 256 bits)"

for the graphics driver.  Am I interpreting this correctly?  I'm not sure why I can't get Nvidia's 535 driver installed.

-Rocky714

---

### Post by ubfan1 on 2024-02-11
There was a recent fix on getting the gcc-12 compiler for the compilation of the Nvidia module (assuming you are running a 6.5 kernel). If you are running 6.5, (cat /proc/version to see which gcc was used, gcc-12).  Check the existing nvidia module for your kernel (mine is 6.5.0-17, yours may be 14 or 15) strings /usr/lib/modules/6.5.0-17-generic/updates/dkms/nvidia.ko |grep gc  and see what gcc was used (should match gcc-12).  If not, purge the nvidia packages and (update, upgrade) reinstall nvidia packages, that should be all that's necessary -- the gcc-12 should be automatically downloaded and used.

---

### Post by rocky714 on 2024-02-12
The kernel version is the same as yours (6.5.0-17) but gcc was only at 11.3.  So, I uninstalled and fully purged (including 'autoremove' of the leftover libs) the Nvidia drivers.  I updated gcc to 12.3.0 and made it default (gcc --version yields 'gcc (Ubuntu 12.3.0-1ubuntu1~22.04) 12.3.0'.  I then issued the following command

sudo apt install nvidia-driver-535 nvidia-dkms-535

to install the 535 Nvidia drivers.  I originally got the impression that it installed only binaries and didn't use gcc but after a second attempt, I saw building for 6.5.0-17-generic and building for x86_64.  In any case, it seemed to proceed normally but the result was that it didn't result in the Nvidia drivers being installed.  However, I did notice something similar to when I tried to install CUDA directly.  In the act of removing, updating and upgrading to clean up Ubuntu for another attempt to install Nvidia's 535 drivers, when trying to sudo apt upgrade, the following packages were listed as 'kept back':

coreutils gdm3 gir1.2-gdm-1.0 gjs iptables libgdm1 libgjs0g libip4tc2 libip6tc2 libxtables12

These look like the same packages that caused problems when I tried to install CUDA directly but please note, I had not yet tried to install CUDA yet here (I was trying to install Nvidia 535 drivers to avoid CUDA 12.1's problems with the 530 drivers).  This suggests I've already induced the problems I've been trying to avoid but how?  It's almost like I have to go back to a fresh install again.  This is very frustrating.

Thanks again for your continuing help.

-Rocky714

---

### Post by ubfan1 on 2024-02-13
A recent fix seems to have let the nvidia module build for kernel 6.5 succeed without having to have the /bin/gcc link changed from the default of gcc-11 (as long as gcc-12 is present).  Those held back packages do not involve nvidia (this time), so should not be your problem.  CUDA installs that get a new/old video driver will cause problems when acutual Ubuntu updates for kernels or video drivers occur, so just get your video set up before CUDA, and reject any offers of video drivers (from the Nvidia .run script). A purge of all nvidia packages, then apt update/upgrade just to ensure current packages, then use the Software & Updates/Additional Drivers tab to select your Nvidia driver should work.  I just did this for a fresh Ubuntu 22.04.1 Desktop ISO -- The 5.15 kernel before any upgrades after a build-essential install used the gcc-11 for the nvidia install, and after the update/upgrade, with a 6.5 kernel present, the nvidia build used the gcc-12 (which downloaded automatically).

---

### Post by rocky714 on 2024-02-16
To make a long story short, it took two attempts that were nearly identical but not perfectly so.  I can't be positive whether it was the big process difference that made it work or the little one.  Here are the steps that were in common:

[FONT=courier new]sudo apt remove --purge nvidia-*
sudo apt autoremove --purge
sudo apt clean
sudo apt upgrade[/FONT]  [There were a number of packages to upgrade in the first pass]

After rebooting, I checked to make sure all was correct.  Doing an "lsmod | grep nouveau" yielded:

[FONT=courier new]nouveau              2842624  6
mxm_wmi                12288  1 nouveau
drm_ttm_helper         12288  1 nouveau
ttm                   110592  2 drm_ttm_helper,nouveau
drm_display_helper    241664  1 nouveau
drm_kms_helper        270336  4 drm_display_helper,nouveau
i2c_algo_bit           16384  1 nouveau
drm                   761856  9 drm_kms_helper,drm_display_helper,drm_ttm_helper,ttm,nouveau
video                  73728  1 nouveau
wmi                    40960  6 hp_wmi,video,intel_wmi_thunderbolt,wmi_bmof,mxm_wmi,nouveau[/FONT]

The first attempt neglected an update (sudo apt update) after the "clean" and before the "upgrade" so it's possible that something got updated in the second attempt that was missed in the first attempt but I don't think that was it  The first attempt tried to do a command line install of the Nvidia drivers with

[FONT=courier new]sudo apt install nvidia-driver-535[/FONT]

which included a UEFI password setting process.  The second attempt used the Software & Updates/Additional Drivers recommendation which did not do anything w/respect to UEFI.  In any case, the second attempt succeeded and the 535 drivers are now installed and active. Insight as to why is welcomed but all the help is appreciated.

I still have to install CUDA 12.1 so I'd like to keep this thread open for a bit but I can't get to it right now. I'll report on progress in a day or two.

Thanks all!

-Rocky714

---

### Post by ubfan1 on 2024-02-17
Good to see you got the video set up. The 6.5 Nvidia/gcc-12 problem was probably just a forgotten dependency on the old dkms package 22.04 is using.  The newer dkms packages seem to have all the necessary dependencies, even for gcc-13 for the 6.8 kernel.

I generally keep multiple CUDA installs around, using Nvidia's .run script to install, reject any video driver offer, and use options to put all the lib and bin files into the cuda install lib and bin directories instead of the system ones.  See [https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu/1077063#1077063) and
[https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010](https://askubuntu.com/questions/1219761/cuda-10-2-different-installation-paths/1244010#1244010)

---

### Post by rocky714 on 2024-02-17
Next step in the ongoing saga ... I installed from the 12.1 runfile of CUDA.  I made sure the MD5s matched and the install seemed to go smoothly.  I wanted to verify the install and followed the instructions in the Nvidia guide.  I used git to clone the samples at [https://github.com/nvidia/cuda-samples](https://github.com/nvidia/cuda-samples).  While some of the samples might be newer and closer to 12.3 compatibility, I thought at least some of the simpler samples (device_query, at least) should demonstrate that the CUDA install is in an operable state.

I ran the make and at the bottom of a long output stream was the error pasted at the bottom.  I don't recall mentioning but gcc is at 12.3.0.  I think it should be recent enough, no?  The original and eventual intent is to get a python usage of CUDA with Anaconda so I might consider bypassing gcc use but I'd be hesitant.  If I can't get Python linked to CUDA, is it because the CUDA install didn't really work, or is it because the Python link or install is bad? Besides, it would be a confidence builder to verify that CUDA is not just installed but working. This has been quite an adventure - like a hurdle race.  Every step requires jumping a hurdle before proceeding to the next.  Any thoughts?  Thanks, again, I appreciate it.

-Rocky714

/usr/local/cuda/bin/nvcc -ccbin g++ -I../../../Common -m64 --std=c++11 --threads 0 -gencode arch=compute_70,code=sm_70 -gencode arch=compute_75,code=sm_75 -gencode arch=compute_80,code=sm_80 -gencode arch=compute_86,code=sm_86 -gencode arch=compute_89,code=sm_89 -gencode arch=compute_90,code=sm_90 -gencode arch=compute_90,code=compute_90 -o simpleAWBarrier.o -c simpleAWBarrier.cu
/usr/local/cuda/bin/../targets/x86_64-linux/include/cuda/std/barrier(144): error: function "operator new" cannot be called with the given argument list
            argument types are: (unsigned long, cuda::std::__4::__barrier_base<cuda::std::__4::__empty_completion, 2> *)
         new (&__b->__barrier) __barrier_base(__expected); 
         ^

1 error detected in the compilation of "simpleAWBarrier.cu".
make[1]: *** [Makefile:368: simpleAWBarrier.o] Error 255
make[1]: Leaving directory '/home/michael/Downloads/CUDA/cuda-samples/Samples/0_Introduction/simpleAWBarrier'
make: *** [Makefile:45: Samples/0_Introduction/simpleAWBarrier/Makefile.ph_build] Error 2

---

### Post by ubfan1 on 2024-02-17
Ubuntu 22.04 uses gcc 11.3 for building the system libraries. gcc-12 may be needed to build modules for kernel 6.5, which used the gcc-12, but not for CUDA samples, which will pick up the system libraries.  Don't change the /bin/gcc link!   Did you set PATH and LD_LIBRARY_PATH so the ...cuda/bin and ...cuda/lib are before the system areas?

---

### Post by rocky714 on 2024-02-18
I did set the PATH and LD_LIBRARY_PATH and had it set properly at the time I tried the MAKE:

$ echo $LD_LIBRARY_PATH
/usr/local/cuda-12.1/lib64

and the path

$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/usr/local/cuda-12.1/bin:/snap/bin

My gcc is at 12.3 as we updated earlier (you instructed in post #16 and others did elsewhere and I acknowledged and performed on post #17).  The question becomes 'What do I do now?"  If I backlevel gcc so I can compile the CUDA samples, I imagine I have some serious incompatibility risks.  If I keep, I can't compile the CUDA samples?  Seems like an intractable problem.  Are there CUDA binaries for the combination of x86_64/CUDA/Nvidia_535/XXX ?

I'm not sure what else might work.

-Rocky714

---

### Post by rocky714 on 2024-02-18
Just a follow up question but because I've been having so much trouble with this install (on my preferred platform), I initiated another attempt with a Windows box.  I have an identically configured laptop on which I'm trying to install CUDA/Python of the same vintage and it gave me this idea.  I'm having similar trouble there.  I don't know diddly about Visual Studio but I want to verify the install there which I finally got through.  I cloned the Nvidia samples git repository to the machine and tried to build the apps there according to Nvidia's instructions for CUDA 12.1.1.  From what I could tell, the instructions direct you to build the entire the entire library of apps.  That failed with an unrecognizable error.  I then tried to build just the device-query app and the error said some things from CUDA 12.3 was missing.  That suggests that I'm not going to succeed building from the current repository which is 12.3 focused if version 12.1.1 is my target.

Can't I get the repository as it existed at the time of 12.1/12.1.1?  That is what these repositories are designed for, isn't it?  Incremental updates and versioning?  I'm not that familiar with git to register that I want to clone the locked version of 12.1/12.1.1.  How can I do that?  That should solve the problem of both the Linux and Windows installations for at least the samples/verification step.  Thanks in advance ... again.

-Rocky714

---

### Post by ubfan1 on 2024-02-18
The Nvidia instructions say to put the .../cuda/bin at the beginning of the PATH, not the end. At the beginning, you could easily select to override gcc with a link to whatever you wanted, but that should not be necessary in this case.  I have the CUDA 12.3 + samples installed and compiled with gcc-11 (/bin/gcc), the default for Ubuntu 22.04.  I don't bother with CUDA incremental updates, I periodically just install the latest version, but I really am not doing much with CUDA. The top level make for the samples may bump into a few samples that need a special library, or may require a lot of memory I don't have.  The individual sample makefiles run just fine.

---

### Post by rocky714 on 2024-02-19
OK, I buy that I don't need to get the 12.1 version of the samples and that the current 12.3 samples should work.  And I'll move the .../cuda/bin directory at the beginning of the path.  But now that I've updated gcc to 12.3 which I needed to install the Nvidia drivers, how do I compile it with gcc-11?  Do I backlevel to 11.x since I only needed 12 for the unitary purpose of the video drivers? Or is there a way to temporarily utilize gcc-11 on the samples and otherwise keeping gcc-12 on the expectation that it will be needed going forward?

Sorry, but this is kind of uncharted territory for me.  Thanks for the help.

-Rocky714

---

### Post by ubfan1 on 2024-02-19
Do not change your gcc (and g++) system defaults.  For Ubuntu 22.04, /bin/gcc (and /bin/g++) should be links to the 11 version(s). The Nvidia module will use the correct version needed as long as the 12 versions are install (NOT as defaults).  For a couple of weeks after the 6.5 kernel was released to the hwe packages, the dkms package for 22.04 didn't have a dependency on the gcc-12, so did not bring it in when needed.  Without the 12 version, the module build would fail, but if the 12 version just happened to have been installed, the Nvidia module build would have worked.  I can't speak for any other modules that might be needed since I don't use any.  Simply reset the links, /bin/gcc and /bin/g++ to the 11 veresions.  Then for CUDA do a make clean, to remove the 12 pollution, and then make should build working CUDA samples, using the default 11 versions.  gcc-12 will be needed from this point forward to rebuild the Nvidia module for every kernel update (or video driver update). The 6.8 kernel will need gcc-13, so I hope by the time 6.8 hits the hwe packages, these little kinks will be ironed out.

---

### Post by rocky714 on 2024-02-21
I think I have a measure of success here.  I fixed my path statement, adjusted the pointer of the compiler back to 11.4 (instead of having the default be 12.3 to build the Nvidia drivers).  I compiled the "deviceQuery" function in the CUDA samples distribution and got the following when running it:

[FONT=courier new]CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "Quadro P2000"
  CUDA Driver Version / Runtime Version          12.2 / 12.1
  CUDA Capability Major/Minor version number:    6.1
  Total amount of global memory:                 4005 MBytes (4199677952 bytes)
  (006) Multiprocessors, (128) CUDA Cores/MP:    768 CUDA Cores
  GPU Max Clock rate:                            1607 MHz (1.61 GHz)
  Memory Clock rate:                             3004 Mhz
  Memory Bus Width:                              128-bit
  L2 Cache Size:                                 1048576 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(131072), 2D=(131072, 65536), 3D=(16384, 16384, 16384)
  Maximum Layered 1D Texture Size, (num) layers  1D=(32768), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(32768, 32768), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total shared memory per multiprocessor:        98304 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 2 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device supports Managed Memory:                Yes
  Device supports Compute Preemption:            Yes
  Supports Cooperative Kernel Launch:            Yes
  Supports MultiDevice Co-op Kernel Launch:      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 12.2, CUDA Runtime Version = 12.1, NumDevs = 1
Result = PASS[/FONT]

I think CUDA and the Nvidia video driver are installed and compiled properly (mild HOORAHs are inside my brain after quite the struggle).  Thanks all.  The next step for me (other than follow any other recommendations suggested) is to try and get Anaconda and the required linkages needed to make sure Python can access CUDA.  Any suggestions there are welcome as well.

Thanks to all for all the help I was given.  It was a battle for me (not a native programmer or Linuxer) but thanks for hanging in there with me.

-Rocky714

---

### Post by ubfan1 on 2024-02-22
You can use the thread tools at the top of the page to mark this as SOLVED.  Good to see you got this working.

---

