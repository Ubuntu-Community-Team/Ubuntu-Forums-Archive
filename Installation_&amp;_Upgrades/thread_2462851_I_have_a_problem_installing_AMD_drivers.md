---
title: "I have a problem installing AMD drivers"
date: 2021-05-28
forum: Installation &amp; Upgrades
---

### Post by serb1312 on 2021-05-28
I'm using Ubuntu 20.04 i have amd r7 260 so i used 
[h=3]Radeon&#8482; Software for Linux® 18.10[/h]Here's what it says:



```
./amdgpu-pro-install -y
deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./
Get:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Ign:1 file:/var/opt/amdgpu-pro-local ./ InRelease
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:2 file:/var/opt/amdgpu-pro-local ./ Release [816 B]
Get:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Ign:3 file:/var/opt/amdgpu-pro-local ./ Release.gpg
Hit:4 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal InRelease   
Get:5 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:6 [http://rs.archive.ubuntu.com/ubuntu](http://rs.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Fetched 328 kB in 6s (56,2 kB/s)      
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
amdgpu-pro-pin is already the newest version (19.10-785425).
Selected version '19.10-785425' (localhost [all]) for 'amdgpu-pro-pin'
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 amdgpu : Depends: amdgpu-lib (= 19.10-785425) but it is not going to be installed
 amdgpu-lib32 : Depends: amdgpu-lib (= 19.10-785425) but it is not going to be installed or
                         amdgpu-lib-hwe (= 19.10-785425) but it is not going to be installed
                Depends: libwayland-amdgpu-client0:i386 (= 1.15.0-785425)
                Depends: libwayland-amdgpu-server0:i386 (= 1.15.0-785425)
                Depends: libgbm1-amdgpu:i386 (= 1:18.3.0-785425)
                Depends: libegl1-amdgpu-mesa:i386 (= 1:18.3.0-785425)
                Depends: libegl1-amdgpu-mesa-drivers:i386 (= 1:18.3.0-785425)
 amdgpu-pro : Depends: libgl1-amdgpu-pro-glx (= 19.10-785425) but it is not going to be installed
              Depends: libegl1-amdgpu-pro (= 19.10-785425) but it is not going to be installed
              Depends: libgles2-amdgpu-pro (= 19.10-785425) but it is not going to be installed
              Depends: libglapi1-amdgpu-pro (= 19.10-785425) but it is not going to be installed
              Depends: libgl1-amdgpu-pro-ext (= 19.10-785425) but it is not going to be installed
              Depends: libgl1-amdgpu-pro-dri (= 19.10-785425) but it is not going to be installed
 amdgpu-pro-lib32 : Depends: libgl1-amdgpu-pro-glx:i386 (= 19.10-785425)
                    Depends: libegl1-amdgpu-pro:i386 (= 19.10-785425)
                    Depends: libgles2-amdgpu-pro:i386 (= 19.10-785425)
                    Depends: libglapi1-amdgpu-pro:i386 (= 19.10-785425)
                    Depends: libgl1-amdgpu-pro-dri:i386 (= 19.10-785425)
 vulkan-amdgpu-pro : Depends: wsa-amdgpu but it is not going to be installed
 vulkan-amdgpu-pro:i386 : Depends: wsa-amdgpu:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

---

### Post by mikewhatever on 2021-05-28
Why haven't you used a driver for 20.04?

---

### Post by serb1312 on 2021-05-28
My GPU isnt supported

---

### Post by grahammechanical on 2021-05-28
As a double check please run

```
lshw -C video
```

and post the output in this thread using the quotes icon. would you also run

```
ubuntu-drivers devices
```

```
ubuntu-drivers list
```

I assume that you are looking for a proprietary video driver. Software & Updates>Additional Drivers tab will list available proprietary video drivers. We must be connected to the internet at the time.

Regards

---

### Post by serb1312 on 2021-05-28
> **grahammechanical said:**
> As a double check please run

```
lshw -C video
```

and post the output in this thread using the quotes icon. would you also run

```
ubuntu-drivers devices
```

```
ubuntu-drivers list
```

I assume that you are looking for a proprietary video driver. Software & Updates>Additional Drivers tab will list available proprietary video drivers. We must be connected to the internet at the time.

Regards

```
serb@serb-System-Product-Name:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: Bonaire [Radeon R7 200 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:28 memory:d0000000-dfffffff memory:cf800000-cfffffff ioport:d000(size=256) memory:feb80000-febbffff memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```
```
serb@serb-System-Product-Name:~$ ubuntu-drivers devices

```
```
serb@serb-System-Product-Name:~$ ubuntu-drivers list

```
It says there are no available proprietary video drivers

---

### Post by GhX6GZMB on 2021-05-28
I don't understand why you're mucking around with this. The AMD/Radeon drivers are free and normally present no problems.
Is this a new install?
In that case redo it and trust the installer. Messing around with video drivers is a Windows/NVidia thing. There no reason at all to find your own drivers.

---

### Post by QIII on 2021-05-28
The radeon module appears to be in use already.  To confirm, you can issue the following in the terminal:

```
lsmod | grep radeon
```

There are currently two AMD drivers for Linux: radeon and amdgpu.  The appropriate driver for whichever hardware is supported is installed (more accurately, the appropriate module is activated in the kernel) during installation.  

amdgpu-pro is a proprietary overlay for amdgpu.  If your device is not supported by amdgpu and amdgpu is not active, you simply cannot install amdgpu-pro.

There is nothing further for you to do.  The correct module is active.

---

### Post by serb1312 on 2021-05-29
> **QIII said:**
> The radeon module appears to be in use already.  To confirm, you can issue the following in the terminal:

```
lsmod | grep radeon
```

There are currently two AMD drivers for Linux: radeon and amdgpu.  The appropriate driver for whichever hardware is supported is installed (more accurately, the appropriate module is activated in the kernel) during installation.  

amdgpu-pro is a proprietary overlay for amdgpu.  If your device is not supported by amdgpu and amdgpu is not active, you simply cannot install amdgpu-pro.

There is nothing further for you to do.  The correct module is active.

Okay but my resolution cant go more than 1024x768/60Hz

---

