---
title: "Can't install CUDA"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by py-ohayo on 2020-03-31
Hello,

I tried to install CUDA using instructions from this link:
[https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal](https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal)

The last instruction sudo apt-get -y install cudagets this:

```
pavel@ALABAMA:~/installers$ sudo apt-get -y install cuda
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cuda
```

I addressed this problem to the NVIDIA forum, but based on my experience, a response can be expected in a few days.

Thanks in advance for any suggestion

---

### Post by CelticWarrior on 2020-03-31
In your other thread, specifically in [post #18]("https://ubuntuforums.org/showthread.php?t=2439616&page=2&p=13942796#post13942796")  , it shows 3 different driver versions installed: 390, 418 and 440. This is, in a nutshell, a horrible mess. 

As CatKiller correctly pointed out: > **The Nvidia driver doesn't switch between branches cleanly**, so the first  thing to do is to **remove whichever version you've got before you install  the new one**. 

Removing previous versions is typically done by running ```
sudo apt-get purge nvidia*
``` before installing the new version.

So, in summary, what's happening now with the (very confusing) Nvidia's instructions is anyone's guess.

---

### Post by py-ohayo on 2020-03-31
[I]sudo apt-get purge nvidia*
[/I]
Sure, it was done before installation.
Probably it doesn't matter, in /var folder I still see this:
[IMG]https://i.postimg.cc/hGLWM4w0/var-folder.png[/IMG]

---

### Post by CelticWarrior on 2020-03-31
> **py-ohayo said:**
> [I]sudo apt-get purge nvidia*
[/I]
Sure, it was done before installation.

Once again you're asserting things that are disproved by the results. If you had purged the older drivers only 440 version would show up but this is what you posted before (in bold what shouldn't or probably shouldn't be there):

```
rc  cuda-nvtx-10-1                                     10.1.243-1                                       amd64        NVIDIA Tools Extension
**rc  cuda-nvtx-10-2                                     10.2.89-1                                        amd64        NVIDIA Tools Extension**
ii  libnvidia-cfg1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA binary OpenGL/GLX configuration library
**ii  libnvidia-common-418                               418.87.00-0ubuntu1                               all          Shared files used by the NVIDIA libraries**
ii  libnvidia-common-440                               440.33.01-0ubuntu1                               all          Shared files used by the NVIDIA libraries
**rc  libnvidia-compute-390:i386                         390.116-0ubuntu0.18.04.1                         i386         NVIDIA libcompute package**
**rc  libnvidia-compute-418:amd64                        418.87.00-0ubuntu1                               amd64        NVIDIA libcompute package**
ii  libnvidia-compute-440:amd64                        440.33.01-0ubuntu1                               amd64        NVIDIA libcompute package
ii  libnvidia-decode-440:amd64                         440.33.01-0ubuntu1                               amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-440:amd64                         440.33.01-0ubuntu1                               amd64        NVENC Video Encoding runtime library
ii  libnvidia-fbc1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-440:amd64                             440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-ifr1-440:amd64                           440.33.01-0ubuntu1                               amd64        NVIDIA OpenGL-based Inband Frame Readback runtime library
**rc  nvidia-compute-utils-418                           418.87.00-0ubuntu1                               amd64        NVIDIA compute utilities**
ii  nvidia-compute-utils-440                           440.33.01-0ubuntu1                               amd64        NVIDIA compute utilities
**rc  nvidia-dkms-418                                    418.87.00-0ubuntu1                               amd64        NVIDIA DKMS package**
ii  nvidia-dkms-440                                    440.33.01-0ubuntu1                               amd64        NVIDIA DKMS package
ii  nvidia-driver-440                                  440.33.01-0ubuntu1                               amd64        NVIDIA driver metapackage
**rc  nvidia-kernel-common-418                           418.87.00-0ubuntu1                               amd64        Shared files used with the kernel module**
ii  nvidia-kernel-common-440                           440.33.01-0ubuntu1                               amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-440                           440.33.01-0ubuntu1                               amd64        NVIDIA kernel source package
ii  nvidia-prime                                       0.8.8.2                                          all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                    440.33.01-0ubuntu1                               amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-440                                   440.33.01-0ubuntu1                               amd64        NVIDIA driver support binaries
ii  xserver-xorg-video-nvidia-440                      440.33.01-0ubuntu1                               amd64        NVIDIA binary Xorg driver
```

Please note that CUDA 10.2 is in bold here only because you explicitly said you want 10.1 for compatibility reasons. In itself not a problem, unlike the presence of older Nvidia drivers presence.

---

### Post by py-ohayo on 2020-03-31
The screenshot you posted correspond to the beginning of my troubles with driver problem.
Then, when the problem with drivers was resolved, I tried to install CUDA.
In one post that I've found on the web, indeed, someone proposed to purge nvidia*.
But I didn't realize that it remove also drivers.
Well, I have to restart with driver installation ... indeed command nvidia-smi isn't found.
One question nevertheless: assuming that driver is correctly installed, should I remove 2 cuda-related folders in /var ?
Thanks.

---

### Post by py-ohayo on 2020-04-01
I reinstalled NVIDIA drivers, nvidia-smi get proper result, but I still can't install CUDA using the official NVIDIA tutorial:
[URL="https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal"]https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal
[/URL]The last instruction [FONT=courier new]sudo apt-get -y install cuda[/FONT] gets this:
**E: Unable to locate package cuda**
It starts to annoy me. Has anyone successfully installed this CUDA ???
I posted my quest on the NVIDIA forum, but it is unlikely that I will be able to get an answer in the near future.
Thanks.
[TABLE]
 	 	[TR]
 		 	
[/TR]
 [/TABLE]
    [TABLE]
 	 	[TR]
 		[TD="align: left"][/TD]
 	[/TR]
 [/TABLE]

---

### Post by CatKiller on 2020-04-01
Those instructions are awful. There are more thorough, but no less confusing - the Nvidia site really is terrible - instructions elsewhere on the same site. Using wget to download some random file and running it is simply terrible, terrible advice. Don't do that. 

Aside from that, the method that you've followed of cloning a snapshot of the whole CUDA repository (twice, in your case) is a pretty wasteful plan. Both in terms of bandwidth and hard drive space. And it makes your sources.list look all manky. You'd do that if you were doing CUDA stuff with a bunch of computers, not just checking it out with a single computer, and it would be part of a specific plan. 

There's a much more standard way of simply adding a new repository entry to your sources.list - although Nvidia insist on distributing *that* through a .deb file, too, because Nvidia. Then it's just part of your standard package management. I forget what they call the option - it's something like "network install," which would mean something else to everyone that isn't Nvidia - and I'm not about to browse their abomination of a site on my phone to check. 

You also don't want to install the *cuda* metapackage for all the reasons we discussed in your other thread. I believe it's the *cuda-toolkit-10-1* metapackage that you're after.

Don't forget to run *apt update* after you've made changes to your repository lists if you want new packages and new versions of packages to be available to your package manager.

---

### Post by py-ohayo on 2020-04-01
Thanks.
> 
Aside from that, the method that you've followed of cloning a snapshot  of the whole CUDA repository (twice, in your case) is a pretty wasteful  plan 
[COLOR=#ff0000]*twice, in your case*[/COLOR] ... You mean 2 cuda-related folders in var (sorry I'm not strong in Linux) ?
Should I remove them before starting new attempt of install CUDA once a reliable approach is found ?

There is another approach that uses run file. I'll try it now:
[https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal](https://developer.nvidia.com/cuda-10.1-download-archive-update2?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=runfilelocal)

---

### Post by CatKiller on 2020-04-01
Never use the run file.

It makes sense to clear out all your previous attempts before you do another one. You'd need to remove the entries in sources.list.d that refer to those local repositories, too.

---

### Post by py-ohayo on 2020-04-01
[COLOR=#ff0000]*Never use the run file.*[/COLOR]

But what can I do now? Continue to search on the web for some reliable manual ?
Here is another quite exhaustive manual on how to install whole **TensorFlow** related staff.
[https://www.pyimagesearch.com/2019/12/09/how-to-install-tensorflow-2-0-on-ubuntu/](https://www.pyimagesearch.com/2019/12/09/how-to-install-tensorflow-2-0-on-ubuntu/)
Although already outdated, the section on CUDA install uses approach, based on run file.

[COLOR=#ff0000]*It makes sense to clear out all your previous attempts before you do  another one. You'd need to remove the entries in sources.list.d that  refer to those local repositories, to*[/COLOR]
So, I remove the folders **cuda-repo-10-1-local-10.1.243-418.87.00** and **cuda-repo-10-2-local-10.2.89-440.33.01** from **/var**
In **sources.list.d** I remove this files:
```
pavel@ALABAMA:/etc/apt/sources.list.d$ ls
graphics-drivers-ubuntu-ppa-bionic.list
graphics-drivers-ubuntu-ppa-bionic.list.save

```
Correct ?

---

### Post by CatKiller on 2020-04-01
> **py-ohayo said:**
> Correct ?
No, you want to keep the entries for the graphics drivers PPA. It's the entries that point to those local CUDA repositories that you'd want to remove. And if you already don't have those entries, that would be why your package manager has no knowledge of a package called *cuda*.

Don't just blindly follow random instructions that you found somewhere on the Internet. It will only ever end in tears.

You've got the driver installed and working. The Nvidia site has a wizard thing where you say which distro you're using and so on. You just go through that and at the end select the .deb file that *doesn't* dump the whole CUDA repository on your hard drive. That will just be a tiny file that packages up the sources.list entries. Run the update then install the metapackage that doesn't mess up your drivers.

---

### Post by py-ohayo on 2020-04-01
[COLOR=#ff0000]*And if you already don't have those entries, that would be why your package manager has no knowledge of a package called cuda.*[/COLOR]
Is it possible to add it manually in some way ... otherwise for the moment I don't see any possibility to advance since you don't recommend using run file.
[COLOR=#ff0000][I]
You've got the driver installed and working. The Nvidia site has a  wizard thing where you say which distro you're using and so on.[/I][/COLOR]
Here is this wizard:
[IMG]https://i.postimg.cc/43P9RXPT/Screenshot-from-2020-04-01-14-42-53.png[/IMG]

There are 4 options, among them  two (deb) one of which I've already tried.
Should I try deb network ?

---

### Post by CatKiller on 2020-04-01
> **py-ohayo said:**
> Should I try deb network ?

> **CatKiller said:**
> There's a much more standard way of simply adding a new repository entry to your sources.list - although **Nvidia insist on distributing *that* through a .deb file**, too, because Nvidia. Then it's just part of your standard package management. I forget what they call the option - **it's something like "network install,"** which would mean something else to everyone that isn't Nvidia - and I'm not about to browse their abomination of a site on my phone to check. 

Yes.

---

### Post by py-ohayo on 2020-04-01
Tried 3rd option (i.e. deb network).
Here is outcome:
```
pavel@ALABAMA:~/installers$ sudo apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
[sudo] password for pavel: 
Executing: /tmp/apt-key-gpghome.AwgcOp9oRL/gpg.1.sh --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub
gpg: requesting key from 'https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub'
gpg: key F60F4B3D7FA2AF80: "cudatools <cudatools@nvidia.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
pavel@ALABAMA:~/installers$ sudo add-apt-repository "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/ /"
Hit:1 http://fr.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                           
Hit:3 http://fr.archive.ubuntu.com/ubuntu bionic-updates InRelease                                    
Hit:4 http://fr.archive.ubuntu.com/ubuntu bionic-backports InRelease                          
Ign:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease
Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]
Get:7 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release [564 B]
Get:8 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release.gpg [819 B]
Get:9 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Packages [141 kB]
Fetched 231 kB in 1s (263 kB/s)                               
Reading package lists... Done
pavel@ALABAMA:~/installers$ sudo apt-get update
Hit:1 http://fr.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://fr.archive.ubuntu.com/ubuntu bionic-updates InRelease                                                                                    
Hit:3 http://fr.archive.ubuntu.com/ubuntu bionic-backports InRelease                                                                                  
Hit:4 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                                                     
Ign:5 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease    
Hit:6 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  Release
Get:7 http://security.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]
Fetched 88,7 kB in 1s (79,4 kB/s)                               
Reading package lists... Done
pavel@ALABAMA:~/installers$ sudo apt-get -y install cuda
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cuda : Depends: cuda-10-2 (>= 10.2.89) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by Frogs Hair on 2020-04-01
A tutorial suggested installing the following dependencies. I don't know if it applies to the instructions you are using.
 
```
sudo apt-get install freeglut3 freeglut3-dev libxi-dev libxmu-dev

```

---

### Post by py-ohayo on 2020-04-01
All prerequisites were already installed.
Something went through my mind ... the version of CUDA 10.2 that I'm trying to install is actually **CUDA Toolkit 10.1 update2**.
And there is no any notion that one should install **original release** ... and then probably **update1**.... before proceeding with **update2**.
As it wasn't specified at all (!!!) I considered **CUDA Toolkit 10.1 update2** as independent version.
He was probably wrong.
So, I will now try to install the original 10.1 first.

---

### Post by py-ohayo on 2020-04-01
Tried original. The same !!!

---

### Post by py-ohayo on 2020-04-01
Well ... seems the problem comes from the fact that I installed driver from **Software & Update**.
This way it installs along wit driver some kind of CUDA..
I don't know exactly what this *kind of CUDA* is, but a guy from NVIDIA I talked to in a chat called it "default CUDA".
Probably some kind of runtime module ... I don't know.
And the version of kind of CUDA being installed along with drivers is the last one, i.e. 10.2.
As you see when I execute [FONT=courier new]nvidia-smi[/FONT], CUDA 10,2 is displayed.

```
pavel@ALABAMA:~/installers$ nvidia-smi
Wed Apr  1 17:27:57 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.64       Driver Version: 440.64       **CUDA Version: 10.2**     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1050    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   43C    P0    N/A /  N/A |    381MiB /  2002MiB |      2%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1078      G   /usr/lib/xorg/Xorg                           253MiB |
|    0      1343      G   /usr/bin/gnome-shell                         125MiB |
|    0      9298      G   /usr/lib/firefox/firefox                       1MiB |
+-----------------------------------------------------------------------------+
```

As I need CUDA 10.1, this method doesn't match my needs, so I purged NVIDIA staff and install drivers with apt-get.
But before continuing, I need to solve a problem that I will describe in a separate post.

---

### Post by CatKiller on 2020-04-01
> **py-ohayo said:**
> ```

pavel@ALABAMA:~/installers$ sudo apt-get -y install cuda
```

Do you even read the things that people write to help you?

---

### Post by py-ohayo on 2020-04-02
> **CatKiller said:**
> Do you even read the things that people write to help you?

Yes, always.
Don't understand what you mean ... sorry.

---

