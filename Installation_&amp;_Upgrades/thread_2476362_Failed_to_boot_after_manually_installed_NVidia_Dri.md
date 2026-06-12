---
title: "Failed to boot after manually installed NVidia Driver on Ubuntu 22.04 ."
date: 2022-06-23
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2022-06-23
[LIST]
[*]Firstly installed Ubuntu 22.04
[*]Then, I installed Official NVidia Driver downloaded from NVidia website, but NOT from Ubuntu repo
[/LIST]

Now, Ubuntu 22.04 hangs at booting.... This is so weird .....

I'm guessing it's because there are 2 video cards?

```

:~$ lspci | grep VGA
0000:00:02.0 VGA compatible controller: Intel Corporation Alder Lake-P Integrated Graphics Controller (rev 0c)
0000:01:00.0 VGA compatible controller: NVIDIA Corporation GA103M [GeForce RTX 3080 Ti Mobile] (rev a1)
:~$ glxinfo | egrep -i "device|memory"
    Device: Mesa Intel(R) Graphics (ADL GT2) (0x46a6)
    Video memory: 29872MB
    Unified memory: yes
    GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_EXT_framebuffer_object, GL_EXT_framebuffer_sRGB, GL_EXT_memory_object, 
    GL_EXT_memory_object_fd, GL_EXT_packed_depth_stencil, GL_EXT_packed_float, 
    GL_AMD_pinned_memory, GL_AMD_query_buffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_gpu_shader4, GL_EXT_memory_object, 
    GL_EXT_memory_object_fd, GL_EXT_multi_draw_arrays, 
    GL_EXT_memory_object, GL_EXT_memory_object_fd, GL_EXT_multi_draw_arrays, 
:~$ nvidia-smi
Command 'nvidia-smi' not found, but can be installed with:
sudo apt install nvidia-utils-418-server  # version 418.226.00-0ubuntu4, or
sudo apt install nvidia-utils-390         # version 390.151-0ubuntu0.22.04.1
sudo apt install nvidia-utils-450-server  # version 450.191.01-0ubuntu0.22.04.1
sudo apt install nvidia-utils-470         # version 470.129.06-0ubuntu0.22.04.1
sudo apt install nvidia-utils-470-server  # version 470.129.06-0ubuntu0.22.04.1
sudo apt install nvidia-utils-510         # version 510.73.05-0ubuntu0.22.04.1
sudo apt install nvidia-utils-510-server  # version 510.73.08-0ubuntu0.22.04.1

```

It looks like currently **ONLY Intel video card** is running for display, but **NVidia video card** is NOT running at all. That is also acceptable for me. I actually **ONLY** use **NVidia video card** as heavy computation, but **NOT** for display purpose.
However, in any case, I do need to have **NVidia driver** installed, either for **CUDA computation**, or for **display (not supposed to, but may have to)** .

And, I also realize that after [NVidia driver NVIDIA-Linux-x86_64-515.48.07.run]("https://www.nvidia.com/download/index.aspx") is installed manually , 
[LIST=1]
[*]Ubuntu 22.04 won't be able to boot into XMode; and some times it just hangs before that flashing page, even without letting me switch to Text Model.
[*]I remember I happened to boot into X Mode a couple of times, and it seems the running driver is NOT Intel, but NVidia. I can clearly tell NVidia GPU memory was partially used.
[/LIST]


What's more, **NVidia driver 510.73.05** from **Ubuntu 22.04 repo** is working properly...


Can anybody give me a hint? How to correctly boot into X Model with Ubuntu 22.04 ? Is there any possibility that I use Intel GPU for display, and NVidia GPU for computation ONLY?
Must I install **nvidia-utils-510** from Ubuntu 22.04 repo??


Cheers
Pei

---

### Post by #&amp;thj^% on 2022-06-23
As a older user, from your Join Date
    Jul 2006 I would have thought you would have installed it through 
```
ubuntu-drivers autoinstall
```
downloading and installing from outside the repos can prove problematic.

---

### Post by MAFoElffen on 2022-06-23
_I would suggest running XServer as your Linux Graphics Layer graphics engine_, then using an xorg.conf file to specify where each GPU is (bus:slot), and which drivers to use for each... That is the detailed helper for those. Though is usually not needed and is overkill.

If your manually installed NVidia drivers (with Cuda support) does not display, are you sure you installed the correct driver for your specific NVidia GPU? Mine all work with multiple, varied GPU's in the same box... That used to be a problem about a decade ago, but hasn't been a problem in at least the last 4 years... (GPU driver conflict between different GPU makes.)

---

### Post by tea for one on 2022-06-23
Also, Ubuntu defaults to a Wayland session.
There have been reports of less-than-perfect performance with Nvidia cards in Wayland.
You can select a Xorg session when logging in via the gear wheel (lower right).

---

### Post by MAFoElffen on 2022-06-23
> **tea for one said:**
> Also, Ubuntu defaults to a Wayland session.
There have been reports of less-than-perfect performance with Nvidia cards in Wayland.
You can select a Xorg session when logging in via the gear wheel (lower right).
Agreed +1 with running XServer instead of Wayland for NVidia GPU's. That's what I do for all my NVidia GPU machines.

---

### Post by #&amp;thj^% on 2022-06-23
Agreed +2 running XServer instead of Wayland

---

### Post by jiapei100 on 2022-06-28
Yeah... You are correct.
By using Ubuntu repos's **NVidia driver 510.73.05**, it suppots **CUDA 11.6 ONLY**. 
I actually happened to have installed **CUDA 11.7** .

Everything went on well (**NVidia driver 510.73.05** + **CUDA 11.7**), until yesterday, I noticed the incompatibility... sorry, didn't take a snapshot but my **nvidia-smi** clearly shows:



```
&#10140;  ~ nvidia-smi
Tue Jun 28 06:07:30 2022       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 510.73.05    Driver Version: 510.73.05    CUDA Version: 11.6     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
......
```




However, when I run a **cuda-sample** after building it:



```
&#10140;  release git:(master) &#10007; ./deviceQuery
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "NVIDIA GeForce RTX 2080 Ti"
  CUDA Driver Version / Runtime Version          11.6 / 11.7
  CUDA Capability Major/Minor version number:    7.5
  Total amount of global memory:                 10986 MBytes (11519590400 bytes)
  (068) Multiprocessors, (064) CUDA Cores/MP:    4352 CUDA Cores
  GPU Max Clock rate:                            1755 MHz (1.75 GHz)
  Memory Clock rate:                             7000 Mhz
......
deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 11.6, CUDA Runtime Version = 11.7, NumDevs = 1
Result = PASS
```



I clearly had **CUDA 11.7** installed.. 

***It's better to have a Driver compatible to CUDA 11.7 ...***

---

### Post by jiapei100 on 2022-06-28
God save me... it looks **nvidia-driver-515** supporting **CUDA-11.7** is just out  ....

my gosh....


Thank Ubuntu ... ^_^ 

Thank you ...

---

### Post by jiapei-nexera on 2022-06-29
Problem continues...

At home, my desktop only has a a single GPU that's why a simple ```
sudo ubuntu-driver autoinstall
``` will do.
However, in the office, this laptop comes with 2 GPUS as mentioned above, quoted again: 

```
&#10140;  ~ lspci | grep VGA00:02.0 VGA compatible controller: Intel Corporation Alder Lake-P Integrated Graphics Controller (rev 0c)
01:00.0 VGA compatible controller: NVIDIA Corporation GA103M [GeForce RTX 3080 Ti Mobile] (rev a1)

```

Current status:

1. How I'm now able to login GUI ?
```

sudo apt purge gdm gdm3
sudo apt install gdm3 ubuntu-desktop
sudo systemctl restart gdm3

```

2. After that I had theh GUI popped up, but:
- Selecting **Ubuntu** (This is clearly **Wayland**) is working
- Selecting **Ubuntu X** .... (This should be Xorg ) is NOT **working** with a black screen

3. With the GUI, I'm now replying this message:

```
&#10140;  ~ nvidia-smi
Failed to initialize NVML: Driver/library version mismatch
&#10140;  ~ echo $XDG_SESSION_TYPE
wayland

```

Let's forget **NVidia driver** for a bit, but come back to the key part:

**- Is there a way to select by ourselves: which display card is used for display (with its particular driver), and the other display card is NOT for display but with a prepared driver for CUDA application?**
- It looks to be when we installed **NVidia driver**, it builds into the kernel automatically, which seems to drive for display automatically. That is also acceptable, although that will directly disable Intel integrated display card... However, is it guaranteed that **NVidia driver **is able to find the correct graphic card for display? Not 100% sure about this... For instance, I already have **NVidia driver **installed, 

```
&#10140;  ~ apt list --installed | grep nvidia


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


libnvidia-cfg1-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-common-515/jammy-updates,jammy-updates,jammy-security,jammy-security,now 515.48.07-0ubuntu0.22.04.2 all [installed,automatic]
libnvidia-compute-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-compute-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-decode-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-decode-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-egl-wayland1/jammy,now 1:1.1.9-1.1 amd64 [installed,automatic]
libnvidia-encode-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-encode-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-extra-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-fbc1-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-fbc1-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 i386 [installed,automatic]
libnvidia-gl-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
libnvidia-gl-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 i386 [installed,automatic]
linux-modules-nvidia-515-5.15.0-40-generic/jammy-updates,now 5.15.0-40.43+1 amd64 [installed,automatic]
linux-modules-nvidia-515-generic-hwe-22.04/jammy-updates,now 5.15.0-40.43+1 amd64 [installed]
linux-objects-nvidia-510-5.15.0-40-generic/jammy-updates,now 5.15.0-40.43+1 amd64 [installed,automatic]
linux-objects-nvidia-515-5.15.0-40-generic/jammy-updates,now 5.15.0-40.43+1 amd64 [installed,automatic]
linux-signatures-nvidia-5.15.0-40-generic/jammy-updates,now 5.15.0-40.43+1 amd64 [installed,automatic]
nvidia-compute-utils-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-driver-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed]
nvidia-kernel-common-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-kernel-source-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
nvidia-prime/jammy,jammy,now 0.8.17.1 all [installed,automatic]
nvidia-settings/jammy,now 510.47.03-0ubuntu1 amd64 [installed,automatic]
nvidia-utils-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
xserver-xorg-video-nvidia-515/jammy-updates,jammy-security,now 515.48.07-0ubuntu0.22.04.2 amd64 [installed,automatic]
&#10140;  ~ 

```
But why there is  

```

&#10140;  ~ nvidia-smi
Failed to initialize NVML: Driver/library version mismatch

```



Anyway, I'm going to **remove ALL default nvidia packages from Ubuntu**, and try this way out:

[https://stackoverflow.com/questions/43022843/nvidia-nvml-driver-library-version-mismatch](https://stackoverflow.com/questions/43022843/nvidia-nvml-driver-library-version-mismatch)
[https://stackoverflow.com/questions/43022843/nvidia-nvml-driver-library-version-mismatch#comment73133147_43022843](https://stackoverflow.com/questions/43022843/nvidia-nvml-driver-library-version-mismatch#comment73133147_43022843)


4. Finally, by the way, I'm using this laptop: [https://rog.asus.com/ca-en/laptops/rog-zephyrus/rog-zephyrus-m16-2022-series/](https://rog.asus.com/ca-en/laptops/rog-zephyrus/rog-zephyrus-m16-2022-series/)

---

### Post by jiapei-nexera on 2022-06-29
It seems I solved it...  Make sure you always have 1 single version of NVidia driver installed ...
I just uninstalled my manually installed NVidia driver, and the Ubuntu NVidia driver, EVERYTHING...
And now I can log in Xorg, with nvidia-driver enabled...

Finally... my god...

---

