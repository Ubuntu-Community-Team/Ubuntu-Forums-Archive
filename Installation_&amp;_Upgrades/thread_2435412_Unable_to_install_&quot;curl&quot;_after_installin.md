---
title: "Unable to install &quot;curl&quot; after installing Tensorflow"
date: 2020-01-20
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2020-01-20
Cannot install "curl":

$ sudo apt install curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
curl : Depends: libcurl4 (= 7.58.0-2ubuntu3.8) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

BUT --fix-broken says everything is OK:

$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libaccinj64-9.1 libasyncns0:i386 libatomic1:i386 libbsd0:i386 libcublas9.1 libcudart9.1 libcufft9.1 libcufftw9.1 libcuinj64-9.1 libcurand9.1 libcusolver9.1
libcusparse9.1 libdbus-1-3:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libedit2:i386 libelf1:i386
libexpat1:i386 libffi6:i386 libflac8:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0:i386 libglvnd0:i386 libglx-mesa0:i386
libglx0:i386 libicu60:i386 libllvm9:i386 libnppc9.1 libnppial9.1 libnppicc9.1 libnppicom9.1 libnppidei9.1 libnppif9.1 libnppig9.1 libnppim9.1 libnppist9.1
libnppisu9.1 libnppitc9.1 libnpps9.1 libnvblas9.1 libnvgraph9.1 libnvidia-common-435 libnvrtc9.1 libnvtoolsext1 libnvvm3 libogg0:i386 liborc-0.4-0:i386
libpciaccess0:i386 libpulse0:i386 libsensors4:i386 libsndfile1:i386 libthrust-dev libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386
libx11-xcb1:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxcb1:i386 libxdamage1:i386
libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxml2:i386 libxshmfence1:i386 libxxf86vm1:i386 nvidia-cuda-doc nvidia-cuda-gdb nvidia-opencl-dev
nvidia-profiler nvidia-visual-profiler ocl-icd-opencl-dev opencl-c-headers
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
john@Nagle-LTS:~/local/IDriveForLinux/scripts$

Synaptic says no broken packages. If I try to install "curl" via Synaptic, I get a "broken package" error.

I recently installed TensorFlow and CUDA, which have way too many specific package requirements. Some kind of version pinning problem?

---

### Post by ubfan1 on 2020-01-20
What does apt-cache policy libcurl4 say, and what ppas have you added?  Probably a later version pulled in from a ppa is causing problems.

---

### Post by CatKiller on 2020-01-20
> **John Nagle said:**
> ```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
<massive list of packages>
``` 

That is not the sign of a happy package manager. Letting those be autoremoved might give your package manager less to worry about. 

>  I recently installed TensorFlow and CUDA, which have way too many specific package requirements. Some kind of version pinning problem?

If you've done a bunch of manual version pinning that can easily cause significant problems for seemingly unrelated packages. Package management broadly falls into either the "works like magic" category or the "barely held together with gaffer tape" one; there's not a lot of in-between. Manually fiddling with it too much tends to put things in the latter category.

---

### Post by John Nagle on 2020-01-20
Only non-Ubuntu PPA is from NVidia:

600 [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64)  Packages
     release o=NVIDIA,l=NVIDIA CUDA,c=
     origin developer.download.nvidia.com

That's the GPU driver with the CUDA tools for number-crunching in the GPU. 


$ apt-cache policy libcurl4
libcurl4:
  Installed: (none)
  Candidate: 7.58.0-2ubuntu3.8
  Version table:
     7.58.0-2ubuntu3.8 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
     7.58.0-2ubuntu3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages

I haven't pinned any versions manually, but the installs for NVidia, CUDA, Tensorflow, or Rasa may have.

So what's causing a problem for curl?

---

### Post by John Nagle on 2020-01-20
The Firestorm viewer for Second Life requires some old libraries.
But none of them are version-pinned. I'd previously installed the ones listed here,
back in 16.04 LTS.

[https://wiki.firestormviewer.org/firestorm_in_64-bit_ubuntu_1804](https://wiki.firestormviewer.org/firestorm_in_64-bit_ubuntu_1804)

I just let the upgrade to 18.04 LTS deal with those, which it did OK.

---

### Post by ubfan1 on 2020-01-21
Your policy for libcurl4 is the same as mine.  Dropped firestorm awhile back in favor of kokua (64 bit and voice not tied to the 32 slvoice files).  Don't have enough GPU to run dnn or Tensorflow, but CUDA 8.0 causes me no problems.  I don't use any Nvidia ppa since the default 390 driver works for me. Which Nvidia driver are you using?  Which kernel are you using?  Which Nvidia driver is supplied by default for your kernel? (I still use the 4.15 kernel, and the Nvidia 390 driver, but later kernels may take/default to later drivers).

---

### Post by John Nagle on 2020-01-21
Linux kernel: Linux 4.15.0-74-generic x86_64

NVidia driver and CUDA:

[FONT=courier new]$ nvidia-smi
Mon Jan 20 23:04:10 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.33.01    Driver Version: 440.33.01    CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 640      On   | 00000000:01:00.0 N/A |                  N/A |
| 30%   32C    P8    N/A /  N/A |    305MiB /  1996MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

This is the NVidia driver the CUDA install installed, not the default Ubuntu driver.
However, it seems to run OpenGL programs just fine, from Google Earth to Firestorm.[/FONT]

---

### Post by John Nagle on 2020-01-21
This may be related:

[B]       Make TensorFlow build libcurl from scratch     
[/B]
[B]Google Cloud Platform support is now available for everyone by default. 
[/B]
[https://github.com/tensorflow/tensorflow/commit/bb890ea5fa4c8a2100a295e93c5bf37b3c88b55a]("http://https://github.com/tensorflow/tensorflow/commit/bb890ea5fa4c8a2100a295e93c5bf37b3c88b55a")

The Tensorflow install apparently modifies Curl to add some Google features. They want it to know about "Google Cloud" files.

This may be what mucked up the dependencies of Curl.

That's seriously annoying. Google is not supposed to be modifying core Ubuntu.

This breaks things which use "curl", including the iDrive backup system.

---

### Post by John Nagle on 2020-01-21
Tensorflow definitely builds "curl". plus quite a lot of other basic Ubuntu utilities. See

[https://github.com/tensorflow/tensorflow/blob/bf94600681e3d6b9e0a62506f9760abccdc3c7ef/tensorflow/workspace.bzl](https://github.com/tensorflow/tensorflow/blob/bf94600681e3d6b9e0a62506f9760abccdc3c7ef/tensorflow/workspace.bzl)

around line 500. That's Google's "bazel" build system. It apparently does not play well with others.

It's quite possible that there's a way to install Tensorflow without mucking up Ubuntu. But following the directions led here.

---

### Post by ubfan1 on 2020-01-21
I expect to be getting a GT 640 later this week, so I'll soon be trying this also, after I iron out any expresscard/PCIe adapter issues on running an external GPU on an old laptop.

---

### Post by John Nagle on 2020-01-21
Reported this as a Tensorflow issue:

[https://github.com/tensorflow/tensorflow/issues/36107](https://github.com/tensorflow/tensorflow/issues/36107)

Linked that to here.

(Yeah, I know, "just use a Docker container on a virtual machine". Which a lot of people do with Tensorflow to avoid stuff like this. I may deploy that way, but I'm trying to develop on desktop right now.)

---

### Post by John Nagle on 2020-01-21
Let me know how that works out. A procedure for installing Rasa, CUDA, and Tensorflow locally without mucking up Ubuntu package management would be a win for a lot of people. 

An NVidia 640 isn't really enough to do much with Tensorflow. I can't use it with Rasa. It has only "compute power 3.0", and Rasa needs at least "Compute performance 3.5". (Compute performance here means what features are in the hardware, not speed. Latest GPUs are at 7.5 or so.)

---

### Post by John Nagle on 2020-01-29
Filed as Tensorflow bug: [https://github.com/tensorflow/tensorflow/issues/36107](https://github.com/tensorflow/tensorflow/issues/36107)

Tensorflow, Ubuntu, and Rasa all have bugs filed now, so they can try to blame each other for breaking "curl" and the package manager.

The real problem is Tensorflow installing their own modded version of "curl" to support Google's remote file service.

---

### Post by ubfan1 on 2020-01-29
Right, the GT 640 was to confirm my adapter (expresscard to PCIe) worked with an external GPU before I get a better one. (Worked perfectly, plug in and run).    A compute Capability of 3.0 does get me to DNN, which is more than I had before (CC of 2.1, which only allowed CUDA 8.0). It'll probably awhile before I iron out the PCI memory issues on the new card anyway -- moving the buffers out of the lower 4G. The laptop vendor is refusing to acknowledge it's a 64 bit machine, and making nasty BIOS updates squeezing the top of the 4G limit.

---

### Post by ubfan1 on 2020-08-05
Got a 4G GTX970, and had no issues with using the expresscard adapter.  Its  compute capability of 5.2 allowed the installation and running of Deep Neural Networking (DNN) and Tensorflow with CUDA10.1 (at the time).  The  .deb install stuck in an old Nvidia driver and make all the CUDA packages depend upon it, so an update of the Nvidia driver caused all the cuda files to be deleted. Restored the CUDA files from backup, cleaned up the CUDA package mess that was left, and it did work, but thought I'd try another way (which was easy for CUDA8, but has since gotten more complicated)   I did another CUDA install of 10.2, avoiding the package manager by simply downloading and  unpacking (repetetdly) the deb file in my chosen location.  This worked, allowing the DNN samples to run and at least the Tensorflow "Is-It-Installed?" test to succeed.  See my answer to [https://askubuntu.com/questions/1256378/question-about-installing-cuda-10-1-on-ubuntu-20-04-the-root-folder-is-empty/1256583#1256583](https://askubuntu.com/questions/1256378/question-about-installing-cuda-10-1-on-ubuntu-20-04-the-root-folder-is-empty/1256583#1256583)  for details.  The way to use old versions of the compiler or changed tools like curl would be to install the old/changed versions into the cuda/bin directory (or just links to the system-installed versions of old compilers if they are offered).  Since the cuda/bin is put at the beginning of the PATH for doing CUDA work, that solves the problem of not wanting to clobber the standard system programs/configuration.

---

