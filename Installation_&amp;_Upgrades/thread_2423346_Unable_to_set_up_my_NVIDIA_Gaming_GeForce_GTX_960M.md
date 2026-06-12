---
title: "Unable to set up my NVIDIA Gaming GeForce GTX 960M graphics card."
date: 2019-07-21
forum: Installation &amp; Upgrades
---

### Post by jdosio on 2019-07-21
Greetings, 
i have recently made a full switch to Ubuntu and have been having some difficulties installing my NVIDIA gpu. i have tried to install the gpu drivers in many different ways but alas have no results. to check what gpu i am using i go to SETTINGS>ABOUT (see Thumbnail"myabout.png")
However if i go to my software-properties i find that i am using the correct driver(see Thumbnail"addiDrivers.png"). Currently the recommended driver is version 430.34 released Jul 09,2019.

```

jdosio@2io-01:~$ sudo lshw -c display
[sudo] password for jdosio: 
  *-display UNCLAIMED       
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff



```

for some reason the gpu is labled "UNCLAIMED",how should i go about claiming it and installing it?
any direction to help would be greatly appreciated.

Kindest Regards,
JD

---

### Post by oldfred on 2019-07-21
> i have tried to install the gpu drivers in many different ways

If not careful that can lead to more issues. You must thoroughly purge before installing any new driver. New install does not purge old and leads to conflicts. Also if you installed directly from nVidia with a .run file, you need to purge that with whatever their procedure is.

First know which is correct driver. I may be that Ubuntu repository has only one or two versions older depending on version of Ubuntu. But now ppa will have all the current versions, so you can install the correct one.
       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
    

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by jdosio on 2019-07-21
i have purged all nvidia drivers with $ sudo apt-get remove nvidia-*
and now software-properties shows (Thumbnail "newAddiDriver.png")
if i do $ sudo apt-get remove nvidia-*
i am shown...```

jdosio@2io-01:~$ sudo ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.1/0000:02:00.0 ==
modalias : pci:v000010DEd0000139Bsv00001028sd00000706bc03sc02i00
vendor   : NVIDIA Corporation
model    : GM107M [GeForce GTX 960M]
driver   : nvidia-driver-418 - third-party free
driver   : nvidia-driver-396 - third-party free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-430 - third-party free recommended
driver   : nvidia-driver-410 - third-party free
driver   : nvidia-driver-415 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

 however if i use ~$ sudo lshw -c display

```

jdosio@2io-01:~$ sudo lshw -c display
  *-display UNCLAIMED       
       description: 3D controller
       product: GM107M [GeForce GTX 960M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
  *-display
       description: VGA compatible controller
       product: HD Graphics 530
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:dd000000-ddffffff memory:b0000000-bfffffff ioport:f000(size=64) memory:c0000-dffff

```

the driver still shows up as unclaimed. is there a way to claim or assign graphics cards?
-JD

---

### Post by oldfred on 2019-07-21
The devices list only shows what is available to install.

If you have added ppa already, usually best to install recommended.
       
# should show newest versions available in addition with ppa added
ubuntu-drivers devices
#You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

Once installed, you should get something like this using dkms showing kernel and that driver is installed into it:
fred@bionic-z97:~$ dkms status
nvidia, 390.116, 4.15.0-52-generic, x86_64: installed
nvidia, 390.116, 4.15.0-54-generic, x86_64: installed

---

### Post by jdosio on 2019-08-12
hey so the driver seems to be installed however im pretty sure it is not running...
```

jdosio@2io-01:~$ dkms status
nvidia, 430.40, 4.18.0-25-generic, x86_64: installed
nvidia, 430.40, 5.0.0-23-generic, x86_64: installed

```

infact most things hint at the driver running, for example.

```

jdosio@2io-01:~$ sudo prime-select nvidia
[sudo] password for jdosio: 
Info: the nvidia profile is already set

```
however if i look at my >About in Settings i am shown that my running GPU is something by the name of llvmpipe (LLVM 8.0, 256 bits)(see pic)

any idea as to what might be causing this and how i might get my nvidia card to start running instead ?
-Kindest Regards,
JD

---

### Post by oldfred on 2019-08-13
See post #21.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938)

This related bug was supposedly fixed a year ago.
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/1768610](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/1768610)

---

### Post by jdosio on 2019-08-13
so is there a fix for the bug ? dont see any instructions as to detecting or fixing the bug in your links, maybe im missing something?

---

### Post by mastablasta on 2019-08-13
are you using bumblebee? [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

though in this case usually intel GPU got disabled when nvidia drivers were installed.

---

### Post by oldfred on 2019-08-13
For bugs.
If fixed, The fix is in the distribution. Details at top on which distributions include fix.  
If nothing shown about all you can do is see if someone has posted a work around. I usually start reading from bottom as often someone will post that  fix in post xx worked or did not work for them.

---

### Post by jdosio on 2019-08-14
i am not currently using Bumblebee, however having read the description i figured it met my needs. in trying to install it i was met with an error.
```

jdosio@2io-01:~$ sudo apt-get install bumblebee bumblebee-nvidia primus linux-headers-generic
[sudo] password for jdosio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 bumblebee : Depends: xserver-xorg-core (>= 2:1.18)
 primus : Depends: xserver-xorg-core (>= 2:1.18.3-2) or
                   xserver-xorg-video-intel (>= 2:2.99.917)
E: Unable to correct problems, you have held broken packages.
jdosio@2io-01:~$ 



```

any clue if this is related to the same issue ? also how would i go about re-enabling the intel graphics card that you mentioned might have been disabled by the installation of the Nvidia driver.

---

### Post by oldfred on 2019-08-14
I thought bumblebee was depreciated with the newer nVidia prime drivers. So that may now be a conflict?

And usually the newer systems have a setting in UEFI on using internal video or not.  My desktop has internal video port out and then nVidia, so I have to specify in UEFI which I am using. It is not switchable like many laptops.

---

### Post by jdosio on 2019-08-18
bump

---

