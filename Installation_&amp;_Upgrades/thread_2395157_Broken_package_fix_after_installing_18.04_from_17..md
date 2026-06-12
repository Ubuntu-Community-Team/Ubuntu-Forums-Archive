---
title: "Broken package fix after installing 18.04 from 17.10"
date: 2018-06-27
forum: Installation &amp; Upgrades
---

### Post by manjush.kochi on 2018-06-27
After upgrading from 17.10 to 18.04 I got a black screen, then from the terminal, I tried to uninstall Nvidia.


From Grub, I pressed 'e' and added nouveau.modeset=0.


I am able to successfully log in, but if I try to fix the broken packages


    sudo dpkg --configure -a


Terminal get stuck in `Building initial module for 4.15.0-24-generic`


The complete output after sudo dpkg --configure -a


    Processing triggers for initramfs-tools (0.130ubuntu3.2) ...
    update-initramfs: Generating /boot/initrd.img-4.15.0-24-generic
    /sbin/ldconfig.real: Warning: ignoring configuration file that cannot be opened: /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf: No such file or directory
    Setting up nvidia-dkms-390 (390.67-0ubuntu0~gpu18.04.1) ...
    update-initramfs: deferring update (trigger activated)
    INFO:Enable nvidia
    DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
    DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
    DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
    Removing old nvidia-390.67 DKMS files...
    
    -------- Uninstall Beginning --------
    Module:  nvidia
    Version: 390.67
    Kernel:  4.15.0-24-generic (x86_64)
    -------------------------------------
    
    Status: This module version was INACTIVE for this kernel.
    depmod......
    
    DKMS: uninstall completed.
    
    ------------------------------
    Deleting module version: 390.67
    completely from the DKMS tree.
    ------------------------------
    Done.
    Loading new nvidia-390.67 DKMS files...
    Building for 4.15.0-24-generic
    Building for architecture x86_64
    Building initial module for 4.15.0-24-generic

---

### Post by deadflowr on 2018-06-27
*Thread moved to **Installation and Upgrades***
18.04 is out of development

---

### Post by troywolf on 2018-07-02
I am in same boat after trying to re-install virtualbox-dkms. It hung, and after giving it more than 10 minutes on my 8 core gen8 I7, I killed it. Now if I try to install anything, I get:

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

```

When I do that, it hangs with the below output:

```

root@foo:~# dpkg --configure -a
Setting up virtualbox-dkms (5.2.10-dfsg-6ubuntu18.04.1) ...
Removing old virtualbox-5.2.10 DKMS files...


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.2.10
Kernel:  4.15.0-24-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-24-generic
Building initial module for 4.15.0-24-generic

```

---

### Post by manjush.kochi on 2018-07-03
I was able to resolve this issue, after doing the update through Software and Updates

---

### Post by Slider-Override on 2018-07-04
I have exact the same, did you get the Virtual Box running again ? I stuck all the time on "Building initial module for 4.15.0-24-generic"

---

### Post by caclratm on 2018-07-05
> **manjush.kochi said:**
> I was able to resolve this issue, after doing the update through Software and Updates

I'm sorry, but can you tell me how exactly did you do that? I am also stuck at 

```

------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-24-generic
Building initial module for 4.15.0-24-generic

```

Thanks in advance!

---

### Post by Slider-Override on 2018-07-05
I stock 4hours on "Building initial module for 4.15.0-24-generic"  But i was able to solve the issue simple by disable secure boot in the UEFI, all is working now thanks   > **caclratm said:**
> I'm sorry, but can you tell me how exactly did you do that? I am also stuck at   ```
 ------------------------------ Deleting module version: 5.2.10 completely from the DKMS tree. ------------------------------ Done. Loading new virtualbox-5.2.10 DKMS files... Building for 4.15.0-24-generic Building initial module for 4.15.0-24-generic 
```  Thanks in advance!

---

### Post by caclratm on 2018-07-06
> **Slider-Override said:**
> I stock 4hours on "Building initial module for 4.15.0-24-generic"  But i was able to solve the issue simple by disable secure boot in the UEFI, all is working now thanks

Thanks! That was it, I had to disable secure boot in BIOS (I kept UEFI on, fwiw).

Having to change BIOS settings in order to install APT packages is fun, to say the least :neutral:

---

### Post by micek2 on 2018-07-11
I had this same problem, trying to install nvidia-dkms-390 on Ubuntu 18.04, and disabling Secure Boot worked for me too!
Thanks!

---

