---
title: "Installing nvidia drivers and using nvidia graphic card"
date: 2020-11-06
forum: Installation &amp; Upgrades
---

### Post by marcb2 on 2020-11-06
Hi,

I have a Dell Precision 7750 under ubuntu 18 and a Quadro T1000 Mobile. 

I realized that nouveau drivers were used by default, and activating the second (intel) graphic card (see lshw outcome below) which is much less efficient. 

I tried uninstalling the nouveau drivers and blacklising them (see /etc/modprobe.d/blacklist-nvidia-nouveau.conf below) then installing nvidia driver from aptitude : didn't work, then by compiling the driver using NVIDIA-Linux-x86_64-450.80.02.run : didn't work either, at reboot, it is still the intel graphic card which is on with intel driver (see modinfo below). The secure boot mode option is not enabled in the bios and i tried prime-select nvidia with no result... And yet, prime-select pretends nvidia is selected :

(ST-2019003060 Bureau) > prime-select query
nvidia


Also, I work under xfce and many setting menus are just not working...

Would anyone know how to install nvidia driver and switch to nvidia graphic card ? Any help would be greatly appreciated, even if only moral one ;-)

Have a great day,

Marc

 lshw -numeric -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED
       description: VGA compatible controller
       product: TU117GLM [Quadro T1000 Mobile] [10DE:1FB9]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:70000000-7fffffff memory:80000000-81ffffff ioport:3000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation [8086:9BF6]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:151 memory:604a000000-604affffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff





 more /etc/modprobe.d/blacklist-nvidia-nouveau.conf
      1 blacklist nouveau
      2 blacklist vga16fb
      3 blacklist rivafb
      4 blacklist nvidiafb
      5 blacklist rivatv
      6 alias nouveau off
      7 alias lbm-nouveau off
      8 options nouveau modeset=0




(11:30 bletry@ST-2019003060 Bureau) > modinfo i915
filename:       /lib/modules/5.0.0-1070-oem-osp1/kernel/drivers/gpu/drm/i915/i915.ko
license:        GPL and additional rights
description:    Intel Graphics
author:         Intel Corporation
author:         Tungsten Graphics, Inc.

---

### Post by mikewhatever on 2020-11-06
Just use the Additiona Drivers utility, or its CLI alternative, <ubuntu-drivers>.
There is no need to download anything from nvidia.com.

---

### Post by marcb2 on 2020-11-06
Thanks for your answer ! To be honest, I am new to ubuntu (used to work with fedora) : do you mean to use the graphical interfaces to add drivers ? I already tried that solution. And I really need the nvidia proprietary drivers as, apparently, Scilab won't work with the open source drivers... :-(

---

### Post by mikewhatever on 2020-11-06
Yes, the Additional Drivers utility is preinstalled in all of *buntus. It is usually used to install Nvidia's graphics or Broadcom's wireless proprietary drivers.

---

### Post by T6&amp;sfpER35% on 2020-11-06
i'm also on xfce ,and my additional drivers GUI shows this option

[ATTACH=CONFIG]287321[/ATTACH]

the selected one works just great

---

### Post by marcb2 on 2020-11-07
Thanks a lot for your answers ! How do you start the additional drivers GUI ? Seems to me I tried that with no success, already...

---

### Post by T6&amp;sfpER35% on 2020-11-07
well what desktop environment u on? i'm on xubuntu which is a xfce like u said u on.
i click on the little mouse icon on toolbar and start typing "additional drivers"...

---

### Post by marcb2 on 2020-11-07
OK, thanks for the tip ! That's what I already tried... I am going to give another shot as I changed a bunch of things since then.

Hi,
So, I am on xubuntu as well (18). I retried the GUI install as you suggested and it came back to my mind : problem of broken dependencies which is why I tried to install from the nvidia shell in the second place. After running the GUI, it does not work and aptitude upgrade says this :

```
root@ST-2019003060:~# aptitude upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libnvidia-gl-450-server{a} 
The following partially installed packages will be configured:
  libnvidia-ifr1-450-server nvidia-driver-450-server 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/60.5 MB of archives. After unpacking 217 MB will be used.
Do you want to continue? [Y/n/?] Y
(Reading database ... 413682 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-450-server'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb (--unpack):
 new libnvidia-gl-450-server:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of libnvidia-ifr1-450-server:amd64:
 libnvidia-ifr1-450-server:amd64 depends on libnvidia-gl-450-server; however:
  Package libnvidia-gl-450-server:amd64 is not installed.

dpkg: error processing package libnvidia-ifr1-450-server:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nvidia-driver-450-server:
 nvidia-driver-450-server depends on libnvidia-gl-450-server (= 450.80.02-0ubuntu0.18.04.3); however:
  Package libnvidia-gl-450-server:amd64 is not installed.
 nvidia-driver-450-server depends on libnvidia-ifr1-450-server (= 450.80.02-0ubuntu0.18.04.3); however:
  Package libnvidia-ifr1-450-server:amd64 is not configured yet.

dpkg: error processing package nvidia-driver-450-server (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin (2.27-3ubuntu1.3) ...
Errors were encountered while processing:
 libnvidia-ifr1-450-server:amd64
 nvidia-driver-450-server
```

From there, I don't know what to do...

---

### Post by CelticWarrior on 2020-11-08
What a mess...

First uninstall what you have installed with the Nvidia binary. Some procedure as installing but add the '--uninstall' parameter. 
Next try to clean everything installed from the repositories:
```
sudo apt-get purge nvidia*
```

Now - very important - do NOT try to install anything else before correcting the "broken" packages. You may want to try the usual commands:
```
sudo apt install -f
sudo dpkg --configure -a
```
and lastly make sure the system is fully updated: ```
sudo apt update && sudo apt full-upgrade
```

Assuming that now the system is fine and fully updated, then proceed with the previous instructions to install the drivers with Additional Drivers.

---

### Post by marcb2 on 2020-11-08
Thanks a lot for your help ! Unfortunately I had also already tried along those lines and just did it again to be sure, removing all nvidia* and with --uninstall from the shell installation, and get this (that is quite a mess...) :

```
root@ST-2019003060:~# apt install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libnvidia-gl-450-server
The following NEW packages will be installed:
  libnvidia-gl-450-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/60.5 MB of archives.
After this operation, 217 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 413682 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-450-server'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb (--unpack):
 new libnvidia-gl-450-server:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-450-server_450.80.02-0ubuntu0.18.04.3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

OK, I already tried that approach and had some broken dependencies... I tried following this :

[https://askubuntu.com/questions/1035409/installing-nvidia-drivers-on-18-04](https://askubuntu.com/questions/1035409/installing-nvidia-drivers-on-18-04)

which looks very similar to my situation. So I tried 

```
apt-get purge *nvidia*
apt-get update
apt-get upgrade
apt autoremove
dpkg-divert --list '*nvidia-340*' | sed -nre 's/^diversion of (.*) to .*/\1/p' | xargs -rd'\n' -n1 -- sudo dpkg-divert --remove
ubuntu-drivers devices
apt install nvidia-driver-450-server (=> which ran smoothly for the first time)
```

I get :

```
root@ST-2019003060:~# prime-select query
nvidia

lshw -numeric -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: TU117GLM [Quadro T1000 Mobile] [10DE:1FB9]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:70000000-7fffffff memory:80000000-81ffffff ioport:3000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation [8086:9BF6]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:151 memory:604a000000-604affffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
```

so nvidia-settings tells me nvidia card is on but lshw thinks differently...

---

### Post by CelticWarrior on 2020-11-08
Again,

```
**sudo apt-get purge nvidia***
```
Only one * at the end. The command you actually ran does nothing. And AGAIN, you need to clean everything "nvidia" before taking care of the broken packages.

---

### Post by marcb2 on 2020-11-08
It gets even worse : I guess I made a mess by using apt, apt-get and aptitude alternatively... sorry, newbie from Fedora is quite lost in terms of package management !!!

[https://paste.ubuntu.com/p/qtk5mT6GtK/](https://paste.ubuntu.com/p/qtk5mT6GtK/)

Sorry, I didn't see your message : I did the purge, it got rid of 550 and 450 versions of the driver, apparently...

I did 

apt autoremove 

which removed a whole bunch of other things...

---

### Post by CelticWarrior on 2020-11-08
Yes, you did.

Just get back a few posts and follow the order I mentioned there.
Must I repeat for the third time that you MUST clean everything "nvidia" BEFORE running the other commands?

---

### Post by marcb2 on 2020-11-08
Now I have :

```
root@ST-2019003060:~# aptitude install -f
The following NEW packages will be installed:
  libnvidia-gl-435:i386{b} nvidia-340{b} 
The following packages are RECOMMENDED but will NOT be installed:
  libcuda1-340 nvidia-opencl-icd-340 nvidia-settings 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/69.3 MB of archives. After unpacking 347 MB will be used.
The following packages have unmet dependencies:
 libnvidia-gl-435:i386 : Depends: libnvidia-common-435:i386 which is a virtual package, provided by:
                                  - libnvidia-common-435 (435.21-0ubuntu0.18.04.3), but it is not going to be installed

                         Conflicts: libnvidia-gl which is a virtual package, provided by:
                                    - libnvidia-gl-418 (418.56-0ubuntu1), but it is not going to be installed
                                    - libnvidia-gl-440 (440.100-0ubuntu0.18.04.1), but it is not going to be installed
                                    - libnvidia-gl-450-server (450.80.02-0ubuntu0.18.04.3), but it is not going to be installed
                                    - libnvidia-gl-440-server (440.95.01-0ubuntu0.18.04.1), but it is not going to be installed
                                    - libnvidia-gl-418-server (418.152.00-0ubuntu0.18.04.1), but it is not going to be installed
                                    - nvidia-340 (340.108-0ubuntu0.18.04.1), but 340.108-0ubuntu0.18.04.1 is to be installed
                                    - libnvidia-gl-450 (450.80.02-0ubuntu0.18.04.2), but it is not going to be installed
                                    - libnvidia-gl-435 (435.21-0ubuntu0.18.04.3), but it is not going to be installed
                                    - libnvidia-gl-390 (390.138-0ubuntu0.18.04.1), but it is not going to be installed
                                    - nvidia-340 (340.106-0ubuntu3), but 340.108-0ubuntu0.18.04.1 is to be installed
                                    - libnvidia-gl-390 (390.48-0ubuntu3), but it is not going to be installed

 nvidia-340 : Depends: lib32gcc1 but it is not going to be installed
              Depends: libc6-i386 but it is not going to be installed
              Conflicts: libnvidia-gl:i386 which is a virtual package, provided by:
                         - libnvidia-gl-418:i386 (418.56-0ubuntu1), but it is not going to be installed
                         - libnvidia-gl-440:i386 (440.100-0ubuntu0.18.04.1), but it is not going to be installed
                         - libnvidia-gl-450-server:i386 (450.80.02-0ubuntu0.18.04.3), but it is not going to be installed
                         - libnvidia-gl-418-server:i386 (418.152.00-0ubuntu0.18.04.1), but it is not going to be installed
                         - nvidia-340:i386 (340.108-0ubuntu0.18.04.1), but it is not going to be installed
                         - libnvidia-gl-450:i386 (450.80.02-0ubuntu0.18.04.2), but it is not going to be installed
                         - libnvidia-gl-435:i386 (435.21-0ubuntu0.18.04.3), but 435.21-0ubuntu0.18.04.3 is to be installed
                         - libnvidia-gl-390:i386 (390.138-0ubuntu0.18.04.1), but it is not going to be installed
                         - nvidia-340:i386 (340.106-0ubuntu3), but it is not going to be installed
                         - libnvidia-gl-390:i386 (390.48-0ubuntu3), but it is not going to be installed

The following actions will resolve these dependencies:

     Install the following packages:                                       
1)     lib32gcc1 [1:8.4.0-1ubuntu1~18.04 (bionic-security, bionic-updates)]
2)     libc6-i386 [2.27-3ubuntu1.3 (bionic-updates, now)]                  

     Keep the following packages at their current version:                 
3)     libnvidia-gl-435:i386 [Not Installed]                               



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
```

To the best of my understanding, I thought that's what I had done...

---

### Post by CelticWarrior on 2020-11-08
Please explain exactly what part of "[COLOR=#000000]MUST clean everything "nvidia" BEFORE running the other commands" YOU DON'T UNDERSTAND?
Why are you running aptitude - no need - before cleaning up the nvidia drivers?[/COLOR]

---

### Post by marcb2 on 2020-11-08
OK, so I followed all the commands you provided but then I still have the mess with aptitude install -f (see above). I guess it would be bad to try installing anything until that thing is settled too, no ?

Once again : I did ! I just tried aptitude install -f to see its status and that's what it gives me : apparently, stuff have not been uninstalled... is there another commandline to get rid of these ?
BTW, if I can offer you a coffee or anything, let me know how !! I owe you !!

Or maybe I don't understand what aptitude install -f means ? 
Sorry, but I really am used to dnf and all this is quite new...

---

### Post by CelticWarrior on 2020-11-08
Your understanding is insufficient here...

'apt autoremove' removes orphaned packages, it doesn't remove packages that are still in use. You need to 1) uninstall the drivers installed by the Nvidia binary and 2) uninstall the ones installed from the repositories - **sudo apt-get purge nvidia*** -, not 'apt' or 'aptitude' ('aptitude' generally isn't used and hasn't been for many years and 'apt' doesn't support gobbling, reason why I EXPLICITLY and twice in bold wrote 'apt-get').

---

### Post by marcb2 on 2020-11-08
OK, I won't use aptitude anymore, I promise.
Other than that, I did all of this :
[B]apt-get purge nvidia* 
[/B]has nothing to remove and I had already removed the shell version with --uninstall...
is there something to do to check if it's all good ?

---

### Post by CelticWarrior on 2020-11-08
Proceed to fully update the system. Post back any errors.

---

### Post by marcb2 on 2020-11-08
I get this :

```
root@ST-2019003060:~# sudo apt update && sudo apt full-upgrade
Hit:1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease                                                                                                
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                      
Hit:4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease                                                                        
Hit:5 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease                                                                                                                            
Ign:6 [http://oem.archive.canonical.com/updates](http://oem.archive.canonical.com/updates) bionic-oem InRelease                                                                                                                           
Ign:7 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) bionic-dell-beaver-osp1-gendry InRelease       
Hit:8 [http://oem.archive.canonical.com/updates](http://oem.archive.canonical.com/updates) bionic-oem Release                              
Ign:9 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) bionic-dell-service InRelease                  
Hit:10 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) bionic-dell InRelease   
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Hit:12 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) bionic-dell-beaver-osp1-gendry Release
Hit:13 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) bionic-dell-service Release       
Fetched 88.7 kB in 1s (71.1 kB/s)                                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by CelticWarrior on 2020-11-08
Ok, seems fine.

Now you can open Additional Drivers and select and install the recommended driver version. Reboot and make sure Secure Boot is disabled.

---

### Post by marcb2 on 2020-11-08
OK, so I did, and it asked for passwd, worked for a while, I restarted, and I get this, seems nvidia card is still not in use, or am I missing something ?

```
lshw -numeric -C display
WARNING: you should run this program as super-user.
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: TU117GLM [Quadro T1000 Mobile] [10DE:1FB9]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:70000000-7fffffff memory:80000000-81ffffff ioport:3000(size=128) memory:b4000000-b407ffff
  *-display
       description: VGA compatible controller
       product: Intel Corporation [8086:9BF6]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:151 memory:604a000000-604affffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

---

### Post by CelticWarrior on 2020-11-08
Are you absolutely sure Secure Boot is disabled?

---

### Post by marcb2 on 2020-11-08
However, the driver seems to be present and (properly ?) installed
```
modinfo nvidia
filename:       /lib/modules/5.0.0-1070-oem-osp1/updates/dkms/nvidia.ko
alias:          char-major-195-*
version:        450.80.02
supported:      external
license:        NVIDIA
srcversion:     2132A76E28730AB295AF17B
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        
retpoline:      Y
name:           nvidia
vermagic:       5.0.0-1070-oem-osp1 SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           NvSwitchRegDwords:NvSwitch regkey (charp)
parm:           NvSwitchBlacklist:NvSwitchBlacklist=uuid[,uuid...] (charp)
parm:           nv_cap_enable_devfs:Enable (1) or disable (0) nv-caps devfs support. Default: 1 (int)
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_EnableStreamMemOPs:int
parm:           NVreg_EnableBacklightHandler:int
parm:           NVreg_RestrictProfilingToAdminUsers:int
parm:           NVreg_PreserveVideoMemoryAllocations:int
parm:           NVreg_DynamicPowerManagement:int
parm:           NVreg_DynamicPowerManagementVideoMemoryThreshold:int
parm:           NVreg_EnableUserNUMAManagement:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_KMallocHeapMaxSize:int
parm:           NVreg_VMallocHeapMaxSize:int
parm:           NVreg_IgnoreMMIOCheck:int
parm:           NVreg_NvLinkDisable:int
parm:           NVreg_EnablePCIERelaxedOrderingMode:int
parm:           NVreg_RegisterPCIDriver:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RegistryDwordsPerDevice:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_GpuBlacklist:charp
parm:           NVreg_TemporaryFilePath:charp
parm:           NVreg_AssignGpus:charp
```

Yes, I checked that Friday with the computer service of my university (I don't have the bios paswd) : secure boot mode was disabled...

However, could there be other bios options that get in the way ? I am starting to wonder, because I really don't understand what's going on...

---

### Post by CelticWarrior on 2020-11-08
Not having the password doesn't help, at all...

There are other settings that you may need to check/change. Namely, the dGPU could be disabled which perhaps would explain the unclaimed status.
But try opening Nvidia X Server Settings and select the Nvidia profile and reboot. Maybe that changes it.

---

### Post by marcb2 on 2020-11-08
```
sudo prime-select nvidia
Info: the nvidia profile is already set
```

Yes, I am starting to think something along the lines of bios  settings... there is a switchable graphics option that can be a nuisance  it seems.
not having bios passwd is a pain... i hate that.
Anyways, thanks a ton for your help : at least the situation seems more sane...

If that is a bios problem and I correct it, though, could there be other things to change or should I re-install after modifying the bios, in your opinion ?

---

### Post by howefield on 2020-11-08
marcb2, please use code tags in preference to quote tags when posting terminal output. It will better maintain the readability of your posts, also feel free to edit previous posts should you wish to add information before a respondent posts again. Thank you.

---

### Post by marcb2 on 2020-11-08
Oh, sorry for the disturbance ! Thanks a lot for your indications ! I will, as of now...

---

### Post by marcb2 on 2020-11-13
OK, so I finally got the BIOS passwd removed and can play with it at will... I disabled Switchable graphics in the bios, took all the steps again as indicated above and re-installed nvidia driver, and now I get this :

```

sudo lshw -numeric -C display

  *-display UNCLAIMED       
       description: VGA compatible controller
       product: TU117GLM [Quadro T1000 Mobile] [10DE:1FB9]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:70000000-7fffffff memory:80000000-81ffffff ioport:3000(size=128) memory:c0000-dffff
```

which is weird : the intel card is gone and the nvidia unclaimed... what the heck is going on ? Would anyone have any idea how to deal with this ?

And I get this :
```

 >  lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation TU117GLM [Quadro T1000 Mobile] (rev a1)
```
This looks like nvidia finally took over, didn't it ?

However, nvidia-settings does not even work and says something nasty :
```

nvidia-settings 
[sudo] password for bletry: 

ERROR: NVIDIA driver is not loaded


ERROR: Unable to load info from any available system
```

Digging a bit more :

```
inxi -G
Graphics:  Card: NVIDIA TU117GLM [Quadro T1000 Mobile]
           Display Server: x11 (X.Org 1.20.8 ) drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 1920x1080@77.00hz
           OpenGL: renderer: llvmpipe (LLVM 10.0.0, 256 bits) version: 3.3 Mesa 20.0.8

```

So it looks like in spite of installing nvidia driver... it just didn't install at all and drivers that are supposedly blacklisted are used nonetheless... What is going on here ?? Any help would be much appreciated...

---

### Post by CelticWarrior on 2020-11-13
It really looks like Secure Boot is still enabled.

---

### Post by MartyBuntu on 2020-11-13
> **CelticWarrior said:**
> It really looks like Secure Boot is still enabled.

It would appear so.

---

### Post by marcb2 on 2020-11-14
Thanks for your answers !
I just re-checked : secure boot is disabled, as well as switchable graphics...
I am on the verge of re-trying shell installation using nvidia's system...

OK, so I finally solved the issue : nvidia drivers were blacklisted in /lib/modeprob.d/... so had to get rid of that. Realized that when trying to install from nvidia's shell installer thanks to its error message, so I let it run like that rather than trying to re-install everything using the ubuntu interface... I write this here in case it turns out to be useful to someone. And thanks again for all the help !

---

