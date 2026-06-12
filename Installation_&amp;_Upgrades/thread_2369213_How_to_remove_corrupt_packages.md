---
title: "How to remove corrupt packages"
date: 2017-08-20
forum: Installation &amp; Upgrades
---

### Post by bnilsson on 2017-08-20
Since about one year, I have been suffering from a bug in the nvidia packages.
I have absolutely no hope that this will be solved the normal way (bug fixed upstream) any time soon.

I get "there are updates" from the update manager every 5 minutes,about

 - NVIDIA OpenCL Driver and ICD Loader library
 - NVIDIA OpenCL ICD
 - Transitional package for nvidia-340
 - Transitional package for nvidia-340

and performing the update always fails.
Apparently, the installer packages include scripts that controls the installation process, and either something is missing or is corrupt in these scripts.
Any attempt to re-install or remove these packages gives an error:

"[COLOR=#000000][FONT=Menlo]dpkg: error in handling of archive /var/cache/apt/archives/nvidia-opencl-icd-340_340.102-0ubuntu3_amd64.deb (--unpack):[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] there is no script in the new version of the package - giving up"[/FONT][/COLOR]

I see also:
"
[COLOR=#000000][FONT=Menlo]"Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it."
[/FONT][/COLOR]
This bug is reported several times, but nothing happens.
Is there any way to manually remove these packages?

Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

Bengt

---

### Post by vocx on 2017-08-20
First of all, when you post in this forum, you could try putting the terminal output inside CODE tags, so it looks nicely formatted. Example,
```

p   nvidia-opencl-icd-340                                       - NVIDIA OpenCL ICD                                                     
p   nvidia-opencl-icd-340:i386                                  - NVIDIA OpenCL ICD                                                     
p   nvidia-opencl-icd-340-updates                               - Transitional package for nvidia-opencl-icd-340                        
p   nvidia-opencl-icd-340-updates:i386                          - Transitional package for nvidia-opencl-icd-340                        
p   nvidia-opencl-icd-346                                       - Transitional package for nvidia-opencl-icd-352                        
p   nvidia-opencl-icd-346:i386                                  - Transitional package for nvidia-opencl-icd-352                        
p   nvidia-opencl-icd-346-updates                               - Transitional package for nvidia-opencl-icd-352-updates                
p   nvidia-opencl-icd-346-updates:i386                          - Transitional package for nvidia-opencl-icd-352-updates

```

> **bnilsson said:**
> 
Apparently, the installer packages include scripts that controls the installation process, and either something is missing or is corrupt in these scripts.
Any attempt to re-install or remove these packages gives an error:

"[COLOR=#000000][FONT=Menlo]dpkg: error in handling of archive /var/cache/apt/archives/nvidia-opencl-icd-340_340.102-0ubuntu3_amd64.deb (--unpack):[/FONT][/COLOR][COLOR=#000000][FONT=Menlo] there is no script in the new version of the package - giving up"[/FONT][/COLOR]

I see also:
"
[COLOR=#000000][FONT=Menlo]"Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it."
[/FONT][/COLOR]&#8203;
The packages inside "/var/cache/apt/archives" are downloaded when you "update" and "upgrade" your system. They are left there in case you want to reinstall them. But you can also clean them.
```

# updates the list of packages
sudo apt update

# downloads and installs new packages
sudo apt upgrade

# erases all older packages in /var/cache
sudo apt clean

```

I would probably try to reinstall that package that is giving you problems.
```

sudo apt install --reinstall nvidia-opencl-icd-340

```

I am also suspecting it could be a problem with your "/etc/apt/sources.list" file.

Did you add any strange repository to it? Maybe it's confusing the package manager about the correct nvidia package to download and unpack.

> 
This bug is reported several times, but nothing happens.
Is there any way to manually remove these packages?

Bengt
Where are these reports? You should link them here so people can read about them and see if there is an obvious problem.

You can remove all packages that you don't want, however, since you have that nvidia package, I assume you need it for your video card. So I am unsure what you want. Do you want to remove the error, and keep the nvidia package, or remove the nvidia package altogether, or what?

---

### Post by bnilsson on 2017-08-21
Here is the link to the bug:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1687883](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-340/+bug/1687883)
The problem is that this bug prevents both install and uninstall.
I have tried to remove the packages from [COLOR=#000000][FONT=Ubuntu Mono]/var/cache, but they keep returning.

I will try the commands you suggested.


[/FONT][/COLOR]

---

### Post by bnilsson on 2017-08-21
I found the solution myself on this page:
[https://askubuntu.com/questions/783093/installing-nvidia-opencl-icd-367-breaks-the-package-manager](https://askubuntu.com/questions/783093/installing-nvidia-opencl-icd-367-breaks-the-package-manager)
This issue is solved for me now, thanks for the attention.

---

