---
title: "Nvidia gtx 670 (msi 670pe/oc) driver install/repeated log outs"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by cr33p1 on 2013-03-28
Hy everyone
I just installed ubuntu 12.10 on my machine, but i'm having problems right from the start.

First of all, i can't open any browser or any program except options and terminal, or else my computer loggs off instantly.
I read that the problem is the nvidia drivers, i'm having a msi 670 pe/oc graphics card, i tried to install the drivers with the following commands
```

sudo apt-get install nvidia-current
```

that did nothing

i tried also
```
[COLOR=red]

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/COLOR][COLOR=red]
sudo apt-get update[/COLOR][COLOR=red]
sudo apt-get install nvidia-current[/COLOR]

```

That messed up everything, i got just the desktop without the unity bar, i uninstalled and i'm currently searching for an answer.

Also at first in overview, graphics was unkwnown, now after ```
sudo apt-get install mesa-utils
``` it shows **gallium 0.4 on llvmpipe (llvm 0x301)**

Thanks

---

### Post by JLeon85 on 2013-03-28
What does it show when you go to the "additional drivers" tab of software & updates in settings? For me, it detected my Nvidia GTS 260 but the current driver didn't work properly. I had to try each of the other Nvidia drivers listed there until I found one that worked.

---

### Post by cr33p1 on 2013-03-28
> **JLeon85 said:**
> What does it show when you go to the "additional drivers" tab of software & updates in settings? For me, it detected my Nvidia GTS 260 but the current driver didn't work properly. I had to try each of the other Nvidia drivers listed there until I found one that worked.

I did a fresh reinstal, at the software sources it shows now **Nvidia Corporation :GK104[GeForce Gtx 670] **but the problem persists, i get logg outs and error messages when i start any program.
I tried changing the driver settings but all the other ones make the resolution to drop and the unity bar and top bar to dissapear, the one that is working (when  i say working i mean it supports the native resolution and the unity barr is present)  is the **X.ORg X server **but it's verry verry laggy

---

### Post by MAFoElffen on 2013-03-29
Please psot the results of:
```

lspci -vnn | grep -i VGA
dpkg -l | grep -i nvidia

```

---

### Post by cr33p1 on 2013-03-29
> **MAFoElffen said:**
> Please psot the results of:
```

lspci -vnn | grep -i VGA
dpkg -l | grep -i nvidia

```

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 670] [10de:1189] (rev a1) (prog-if 00 [VGA controller])


```

```
rc  nvidia-current                            304.51.really.304.43-0ubuntu1             amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-current-updates                    304.51-0ubuntu1                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-experimental-304                   304.48-0ubuntu1                           amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-experimental-310                   310.14-0ubuntu1                           amd64        Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.51-0ubuntu2                           amd64        Tool for configuring the NVIDIA graphics driver


```

---

### Post by MAFoElffen on 2013-03-29
Hint- You did not uninstall the first driver before installing the second...

---

### Post by cr33p1 on 2013-03-29
the results are from a clean install, i did not modiffied anything this time

---

### Post by MAFoElffen on 2013-03-29
And yet it shows multiple versions of drivers installed at the same time. You have the ppa installed right?

First, make sure that everything is removed and cleaned up.
```

sudo apt-get remove --purge nvidia-current
sudo apt-get remove --purge [COLOR=#000000][FONT=Ubuntu Mono]nvidia-current-updates[/FONT][/COLOR]
sudo apt-get remove --purge nvidia-experimental-304
sudo apt-get remove --purge nvidia-experimental-310
sudo apt-get remove --purge nvidia-settings
sudo apt-get autoremove
sudo apt-get clean

```
You used to be able to do this with one global command, but apt-get doesn't take globals anymore...

Update the cache and install your driver. You assumed right that the 670 is too new to be covered by the driver in main, so either use the driver in the ppa or straight from nvidia. I would say that the ppa would be easier for you to install.
```

sudo apt-get update
sudo apt-get install nvidia-current-updates
sudo nvidia-xconfig

```

---

### Post by cr33p1 on 2013-03-29
bloody hell that worked :D
no more freezing and no more log offs
I'l keep it as unresolved until midnight, just in case.

@MAFoElffen thank you very much

---

