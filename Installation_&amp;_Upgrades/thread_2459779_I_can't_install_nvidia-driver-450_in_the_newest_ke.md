---
title: "I can't install nvidia-driver-450 in the newest kernel"
date: 2021-03-25
forum: Installation &amp; Upgrades
---

### Post by mrpresident2020 on 2021-03-25
I'm trying to run Tensorflow for my deep learning classes. The problem is:

- In order to run Tensorflow properly, I need to install Cuda Toolkit 11.0.
- In order to install Cuda Toolkit 11.0, I need to install the nvidia-driver-450 (or higher).
- However, the nvidia-driver-450 is not compatible with my kernel (5.8). Apparently it's only compatible with the 5.4 kernel.
- I installed kernel 5.4, but when I booted with it, I couldn't connect to the wifi for some reason.

I'm very lost. What should I do to solve this problem?

---

### Post by CatKiller on 2021-03-25
> **mrpresident2020 said:**
> Apparently it's only compatible with the 5.4 kernel.

Says who?

Anyway, if you're using Nvidia's repository to get CUDA from, there's a metapackage that installs all the CUDA stuff, but *doesn't* install their driver. Which leaves you free to use whichever driver you like, such as the one from [the PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa), for example.

---

### Post by Bashing-om on 2021-03-25
mrpresident2020; Hello

^^ in addition to CatKiller's comments -

How do you (or we) know that your graphic's card supports a 450+ driver version ?

What returns:
```

lspci -k | grep -EA2 'VGA|3D'

```

Our repo has full support for CUDA:
See the output :
```

apt search cuda

```
partiularly: "nvidia-cuda-doc"

My notes include -
> 
Make sure to install nvidia-modprobe via apt to make CUDA and OpenCL work.


see also: [https://ubuntuforums.org/showthread.php?t=2439010#post13941395](https://ubuntuforums.org/showthread.php?t=2439010#post13941395)


[INDENT][INDENT]My bit to try and help
[/INDENT][/INDENT]

---

### Post by mrpresident2020 on 2021-03-26
I added the Nvidia's repository and then did an update (sudo apt-get update). After doing that, I search for cuda (apt-cache search cuda) and I still couldn't find the package that installs cuda without the driver. Do you happen to know which package I should look for? Thanks.

---

### Post by CatKiller on 2021-03-26
[https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#package-manager-metas](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#package-manager-metas)

The metapackage is called cuda-toolkit-11-2 for the latest version. If you're using the repository for an older version (I understand that they throw up another repository for each version) then it'll be a similar name with a different number.

---

### Post by mrpresident2020 on 2021-03-26
Apt can't find this package. That means I installed the wrong repository. Do you know which repository contains that package? Thanks.

---

### Post by CatKiller on 2021-03-26
> **mrpresident2020 said:**
> Apt can't find this package. 

Like I said, the version string will be different if you're trying to use a different version of CUDA.

It also sounds like you haven't yet discovered Tab-completion. Type in the first part of a command, option, or filename, and then press Tab. If there's a unique way to fill in the rest, the shell will do so; if there's more than one way to complete it the shell will do what it can and then pressing Tab twice will show a list of the options for the rest. Rinse and repeat.

So *sudo apt install cuda-toolkit*<Tab> will show you the CUDA Toolkit metapackage that's in whichever repository you're using.

---

