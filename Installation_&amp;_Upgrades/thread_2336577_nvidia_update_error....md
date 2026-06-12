---
title: "nvidia update error..."
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by pablosquared on 2016-09-09
... I think. I'm seeing this error from an apt-get dist-upgrade, it appears every time.

```

The following package was automatically installed and is no longer required:
  nvidia-opencl-icd-361
Use 'sudo apt autoremove' to remove it.
The following NEW packages will be installed
  nvidia-opencl-icd-367
The following packages will be upgraded:
  nvidia-opencl-icd-361
1 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/2,833 kB of archives.
After this operation, 18.9 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 446004 files and directories currently installed.)
Preparing to unpack .../nvidia-opencl-icd-361_367.44-0ubuntu0.16.04.1_amd64.deb ...
**Failed to stop var-lib-snapd-lib-gl.mount: Unit var-lib-snapd-lib-gl.mount not loaded.**
[B]dpkg: warning: subprocess old pre-removal script returned error exit status 5
dpkg: trying script from the new package instead ...
dpkg: error processing archive /var/cache/apt/archives/nvidia-opencl-icd-361_367.44-0ubuntu0.16.04.1_amd64.deb (--unpack):
 there is no script in the new version of the package - giving up[/B]
Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it.
dpkg: regarding .../nvidia-opencl-icd-367_367.44-0ubuntu0.16.04.1_amd64.deb containing nvidia-opencl-icd-367:
 [B]nvidia-opencl-icd-367 conflicts with nvidia-opencl-icd
  nvidia-opencl-icd-361 provides nvidia-opencl-icd and is present and installed.[/B]

dpkg: error processing archive /var/cache/apt/archives/nvidia-opencl-icd-367_367.44-0ubuntu0.16.04.1_amd64.deb (--unpack):
 conflicting packages - not installing nvidia-opencl-icd-367
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-opencl-icd-361_367.44-0ubuntu0.16.04.1_amd64.deb
 /var/cache/apt/archives/nvidia-opencl-icd-367_367.44-0ubuntu0.16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any ideas? Should I purge the installed nvidia driver and re-apply the update?

TIA

PP

---

### Post by pablosquared on 2016-09-09
Forgot to mention - ubuntu 16.04, GTX750Ti, 8GB. 

All is well with the desktop otherwise.

---

### Post by Bashing-om on 2016-09-09
pablosquared; Well;

As a 1st look, appears there is a driver conflict between 361 and 367.
Let's look at what is installed, then see what needs to be done to get only one - there can be only 1 .
```

dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia

```

a clean system
[INDENT][INDENT]is a happy system
[/INDENT][/INDENT]

---

### Post by pablosquared on 2016-09-09
Here goes:

```

pablo@Ubuntu-Wily:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                 0.8-3ubuntu1                                                amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-367                                  367.44-0ubuntu0.16.04.1                                     amd64        NVIDIA CUDA runtime library
ii  nvidia-352                                    361.45.11-0ubuntu0.16.04.1                                  amd64        Transitional package for nvidia-361
ii  nvidia-361                                    367.44-0ubuntu0.16.04.1                                     amd64        Transitional package for nvidia-367
ii  nvidia-367                                    367.44-0ubuntu0.16.04.1                                     amd64        NVIDIA binary driver - version 367.44
ii  nvidia-opencl-icd-361                         361.45.11-0ubuntu0.16.04.1                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                  0.8.2                                                       amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                               361.42-0ubuntu1                                             amd64        Tool for configuring the NVIDIA graphics driver
pablo@Ubuntu-Wily:~$
 
pablo@Ubuntu-Wily:~$ dkms status
bbswitch, 0.8, 4.4.0-37-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-38-generic, x86_64: installed
nvidia-367, 367.44, 4.4.0-38-generic, x86_64: installed
pablo@Ubuntu-Wily:~$

 
pablo@Ubuntu-Wily:~$ lsmod | grep nvidia
nvidia_uvm            745472  0
nvidia_drm             45056  1
nvidia_modeset        765952  5 nvidia_drm
drm_kms_helper        147456  2 i915_bpo,nvidia_drm
drm                   364544  5 i915_bpo,drm_kms_helper,nvidia_drm
nvidia              11476992  92 nvidia_modeset,nvidia_uvm
pablo@Ubuntu-Wily:~$ 

```

nvidia-settings reports v.367.44

---

### Post by Bashing-om on 2016-09-10
pablosquared; Hello;

Sorry for the delay ... life has a way of intruding.

Anyway, as you can see we do have driver conflicts ( that ii as the first field in the dpkg output ).
Let's clean things up, as there can be but one control for one particular graphic set - I do note that this is in all likely hood hybrid graphics .
```

sudo apt purge nvidia*
sudo rm /etc/X11/Xorg.conf

```

And now we install the driver. 
```

sudo apt update
sudo ubuntu-drivers autoinstall
sudo apt upgrade

```
where we allow the system to install what it thinks best - from what it has to choose from.
As you have installed version 367, I bet that :
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
is the source, as that one is the preferred means to obtain the 367 version driver.
For now, we accept what the system thinks .. and IF there is a problem then we re-address it .

Reboot the system for the change in driver(s) to take effect:
```

sudo shutdown -r now

```
Advise when rebooted what the situation is.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by pablosquared on 2016-09-12
Thanks so much, [**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508"), appreciate your help. Life does have a way of knocking plans for 6..

I purged the nvidia driver and rebooted back (into low graphics mode). My system doesn't have an xorg.conf. 

I re-installed the 367 driver per your instruction, screens etc. returned to normal arrangements. Still getting the same error when updating, however. I don't have any non-std repositories for nvidia drivers installed - I've spent way too long trying to fix fix / upgrade nvidia drivers over many years / systems, content for a quieter life now.:)

From looking at synaptic:

```

nvidia-opencl-icd-361
Transitional package for nvidia-opencl-icd-367

```

This issue isn't presenting a problem, but it is an annoyance. Any further suggestions?

TIA
PP

---

### Post by oldfred on 2016-09-12
You also showed bbswitch.
> bbswitch is a kernel module which automatically detects the required ACPI
calls for two kinds of Optimus laptops. It has been verified to work with
"real" Optimus and "legacy" Optimus laptops (at least, that is what the
author Lekensteyn calls those).


Is your system Optimus?

---

### Post by pablosquared on 2016-09-12
Hi oldfred. No, my system is a custom desktop, not a laptop, Optimus or otherwise.

---

### Post by pablosquared on 2016-09-12
And that was the problem - I un-installed bbswitch-dkms, rebooted, updated (which reinstalled the nvidia 367 driver)- no errors. 

I vaguely remember installing bbswitch a while ago for what seemed a good reason - guess I got that wrong.

Thanks so much for your help, both - much appreciated.

---

### Post by Bashing-om on 2016-09-12
pablosquared; Outstanding !

You do good work !

Glad it all worked out .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

