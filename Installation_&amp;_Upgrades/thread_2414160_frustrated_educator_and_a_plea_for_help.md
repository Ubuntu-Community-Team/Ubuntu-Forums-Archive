---
title: "frustrated educator and a plea for help"
date: 2019-03-06
forum: Installation &amp; Upgrades
---

### Post by andrewdahl on 2019-03-06
At out high school we are working on building a Augmented reality sandbox to use in our science classes

the problems that we are having are installing the nvidia drivers for the Geforce RTX 2070 card that we purchased 

we start with a fresh install of 18.4.2 Ubuntu

went to software and updates --- then additional driver ------  "no additional divers"

sudo ubuntu-drivers devices   -----gives "command not found"
sudo lshw -c display ----- tells me 
     *-display unclaimed
      product NVIDIA corporation
      vendor NVIDIA corporation
     physical id: 0
     bus info: pci:@0000:01:00.0
    version: a1
    width: 64 bits
    clock 33mhz
    capabilities: pm msi pciexpress vga_controller bu_master cap_list
    configuration: latency=0
    resources: memory: fd000000-fdffffff  memory: c0000000-cfffffff memory:d0000000-d1fffffff ioport:e000(size128) memory:c0000-dffff

sudo apt-get-repository ppa:graphics-drivers/ppa    give me apt-get-repository : command not found
also tried
sudo add-apt-repository ppa:grpahics-drivers/ppa  "graphics-drivers"  user or team does not existy
  
tried sudo apt-get install software-properties-common    --- tells me that it is already the news version available


I am at a total loss, any hints/help
thanks in advance

---

### Post by #&amp;thj^% on 2019-03-06
I'm trying to make sense of this, please copy and paste one line at a time, and post the return here:
```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
```
NVIDIA 410.66 Linux Driver Released With RTX 2070 Support, Vulkan Ray-Tracing, Etc.

---

### Post by kc1di on 2019-03-06
The correct command for adding the ppa is ```
sudo add-apt-repository ppa:graphics-drivers
``` 
Simply copy and paste it in a terminal. 
then issue this command  ```
sudo apt update
```
and install the driver you want. 

Also if this machine has secure boot enabled it must be disabled for Nvidia driver to work. 
Good Luck.

---

### Post by andrewdahl on 2019-03-06
```
Cannot add PPA: 'ppa:~graphics-drivers/ubuntu/ppa'.
ERROR: '~graphics-drivers' user or team does not exist.
```

when I did a complete shutdown and reboot 

sudo ubuntu-drivers devices   --- i get

```
== /sys/devices/pci0000:00/0000:00:02.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001F07sv00001458sd000037ADbc03sc00i00
vendor   : NVIDIA Corporation
driver   : nvidia-driver-418 - third-party free recommended
driver   : xserver-xorg-video-nouveau - distro free builtin

i then enter sudo ubuntu-drivers autoinstall and get
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-driver-418 : Depends: xserver-xorg-video-nvidia-418 (= 418.39-0ubuntu1) but it is not going to be installed
                     Recommends: libnvidia-compute-418:i386 (= 418.39-0ubuntu1) but it is not installable
                     Recommends: libnvidia-decode-418:i386 (= 418.39-0ubuntu1) but it is not installable
                     Recommends: libnvidia-encode-418:i386 (= 418.39-0ubuntu1) but it is not installable
                     Recommends: libnvidia-ifr1-418:i386 (= 418.39-0ubuntu1) but it is not installable
                     Recommends: libnvidia-fbc1-418:i386 (= 418.39-0ubuntu1) but it is not installable
                     Recommends: libnvidia-gl-418:i386 (= 418.39-0ubuntu1) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by howefield on 2019-03-06
> **andrewdahl said:**
> Cannot add PPA: 'ppa:~graphics-drivers/ubuntu/ppa'.
ERROR: '~graphics-drivers' user or team does not exist.

Usually best to post the actual and complete input/output from the terminal, placed between code tags.

Try ..

```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

---

### Post by #&amp;thj^% on 2019-03-06
Interesting....are you behind a proxy?
Also try kc1di suggestion with:"sudo add-apt-repository ppa:graphics-drivers"

---

### Post by andrewdahl on 2019-03-06
```

sandbox@sandbox:~$ sudo add-apt-repository ppa:graphics-drivers/ppa
Cannot add PPA: 'ppa:~graphics-drivers/ubuntu/ppa'.
ERROR: '~graphics-drivers' user or team does not exist.
sandbox@sandbox:~$

```

not behind a proxy

---

### Post by deadflowr on 2019-03-06
[s]Looks like a proxy issue.
See if 
```
sudo add-apt-repository -E ppa:gpu-drivers/ppa
```
works
From here:
[https://askubuntu.com/questions/971877/cannot-add-ppa-user-or-team-does-not-exist/1036627]("https://askubuntu.com/questions/971877/cannot-add-ppa-user-or-team-does-not-exist/1036627")[/s]

also it is best to run a system update first
```
sudo apt update
sudo apt full-upgrade
```
doing so helps keep all things in line.

With that run these in order
```
sudo apt update
sudo apt full-upgrade
[s]sudo add-apt-repository -E ppa:gpu-drivers/ppa[/s]
```

Edit. missed the post on not behind a proxy.
But still, run the update and full upgrade commands and post back the output.

---

### Post by andrewdahl on 2019-03-06
this is what i get back
```

sandbox@sandbox:~$ sudo apt update
Get:1 file:/var/cuda-repo-10-1-local-10.1.105-418.39  InRelease
Ign:1 file:/var/cuda-repo-10-1-local-10.1.105-418.39  InRelease
Get:2 file:/var/cuda-repo-10-1-local-10.1.105-418.39  Release [574 B]
Get:2 file:/var/cuda-repo-10-1-local-10.1.105-418.39  Release [574 B]
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease   
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease
Get:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Fetched 163 kB in 1s (245 kB/s)                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
sandbox@sandbox:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by #&amp;thj^% on 2019-03-06
The plot thickens: :)
It has been my experience that nvidia-driver-418 is not ready for prime-time(Not tested thoroughly yet)
Can we see this please:
```
cat /etc/apt/sources.list
```

---

### Post by monkeybrain20122 on 2019-03-06
I see you have Nvidia's cuda repo form [nvidia]("https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804"), that should supply the driver (so you don't need driver ppa) But you apparently have the wrong .deb file. You should have gotten the .deb (network) rather than .deb(local). The latest driver is 418.39 (package is called nvidia-418) , works well on my system but it is Ubuntu16.04.6. Some people reported problems for 18.04 though, see[ here]("https://devtalk.nvidia.com/default/topic/1047430/cuda-setup-and-installation/issues-with-cuda-10-0-install-on-ubuntu-18-04-lts/"), though these people didn't say which driver (you can install a driver without installing cuda) You can probably try nvidia-410. If you have synaptic you can see which driver are available at a glance instead of doing those sudo apt install /I/misspelled/package_name_and/or_version/ commands

If you plan on installing cuda, I would suggest cuda-10.0 instead of cuda 10.1, you can use the same cuda repo though, just don't install the cuda meta-package and go for the cuda-10-0  meta-package instead, see[ here]("https://ubuntuforums.org/showthread.php?t=2414082&p=13842461#post13842461").

---

### Post by andrewdahl on 2019-03-06
as per request
```

#deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

---

### Post by monkeybrain20122 on 2019-03-06
Third party repos often end up in /etc/apt/sources.list.d as separate files rather than entries in /etc/apt/sources.list. I saw cuda in your sudo apt update outputs, it is probably in /etc/apt/sources.list.d as cuda-list or something like that.

---

### Post by #&amp;thj^% on 2019-03-06
before we go on, will you answer this, Is this (CUDA) needed by you/classroom.
> 
The Compute Unified Device Architecture (CUDA) enables NVIDIA
 graphics processing units (GPUs) to be used for massively parallel
 general purpose computation.
 .
 This package contains the nvcc compiler and other tools needed for building
 CUDA applications.
 .
 Running CUDA applications requires a supported NVIDIA GPU and the NVIDIA
 driver kernel module.
I have to dash-off to work now, I'll check back to see how you are getting along Good Luck.

---

### Post by monkeybrain20122 on 2019-03-06
BTW, in view of 1fallen's last post I should clarify, you can get the driver from Nvidia's ubuntu repo whether you choose to install cuda or not. If you install cuda (there are several versions available, better use synaptic to see which are available), if you install cuda then it will pull in the corresponding driver. but you can just install the driver without cuda if you don't want it (there are several drivers available)

You apparently have already added the repo but the driver doesn't show up because you have installed the wrong .deb see #11. The .deb you downloaded from Nvidia does not install anything, it just adds a repo file to /etc/apt/source.list.d (you have to add the gpg key of course, see Nvidia's install guide, and do sudo apt update afterwards)

---

### Post by CatKiller on 2019-03-06
> **monkeybrain20122 said:**
> if you install cuda then it will pull in the corresponding driver.

I'm going to chime in here, too, to point out that this isn't strictly accurate.

The Nvidia CUDA repository has [a whole bunch of different metapackages]("https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#package-manager-metas") for installing whichever particular bits that you want.

It's perfectly fine to install the CUDA toolkit from Nvidia and the driver from the graphics-drivers PPA, and that is what I would recommend doing.

So, purge all the nvidia and cuda stuff from the local Nvidia repository, and remove that. I can't remember if you'll also need to manually remove the files that make up the local repository (the /var/cuda-repo stuff). Apt update. Add the PPA. Apt update. Install the driver. Probably reboot. Then install the .deb for Nvidia's network repository (which is essentially an entry in sources.list.d). Apt update. Install the cuda-toolkit metapackage.

Assuming the OP wants CUDA for the classes, anyway. If not, just purge the Nvidia stuff and use the driver from the PPA.

---

### Post by monkeybrain20122 on 2019-03-06
> **CatKiller said:**
> I'm going to chime in here, too, to point out that this isn't strictly accurate.

The Nvidia CUDA repository has [a whole bunch of different metapackages]("https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#package-manager-metas") for installing whichever particular bits that you want.



If you install cuda blah blah then yes, e.g "cuda-driver" probably pulls in a bunch of other stuffs AND the driver (and cuda?) but if you just install "nvidia-410", for example, then no.


> It's perfectly fine to install the CUDA toolkit from Nvidia and the driver from the graphics-drivers PPA, and that is what I would recommend doing.

I don't know about that. Maybe that is ok as long as you never plan to upgrade cuda or your driver, otherwise they may get out of sync, and as you said cuda-driver would bring in other stuffs in addition to the driver, the other things may or may not be compatible with the driver from driver ppa. Personally I try to install related components from the same repo. So my suggestion would be: if don't use cuda then either driver ppa or nvidia repo should be ok for just the driver, if use cuda then use nvidia's (network) repo.

P.S As a somewhat unusual combination, one can install driver from driver ppa and install cuda and cudnn with the .run  file in $HOME , that way you can test multiple versions of cuda (need to initialise environmental variables appropriately for each version of course) I install cuda system wide with Nvidia's repo, but before each cuda upgrade I would install the new version in my $HOME with the .run file and do a lot of tests. Only if all work would I upgrade cuda with apt.

---

### Post by andrewdahl on 2019-03-07
first of all- thanks for the help!
I am trying to keep up with the information coming in 
(this is my first real in depth interaction with Ubuntu)

what would be the most painless straightforward process to install the drivers?

---

### Post by CatKiller on 2019-03-07
> **andrewdahl said:**
> what would be the most painless straightforward process to install the drivers?

Do you need/want CUDA?

---

### Post by andrewdahl on 2019-03-07
i would hazard the guess that I do not need it-
thanks

and the one thing that I just realized is that upper and lower cases matters in this.

and in seeing that issue as a problem on my end-
 I was able to install the drivers and it worked flawlessly-

again thanks to all that were able to chime in and help me out
It is very much appreciated

---

### Post by monkeybrain20122 on 2019-03-07
> and the one thing that I just realized is that upper and lower cases matters in this.

That's why I said
> If you have synaptic you can see which driver are available at a glance  instead of doing those sudo apt install  /I/misspelled/package_name_and/or_version/ commands

Install synaptic.

---

