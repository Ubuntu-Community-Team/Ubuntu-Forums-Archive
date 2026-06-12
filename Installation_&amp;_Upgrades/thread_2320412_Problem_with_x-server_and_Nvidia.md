---
title: "Problem with x-server and Nvidia"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by Hadden89 on 2016-04-13
I've a pc with lubuntu 14.04 but now doesn't work well as I changed some things about I use it expecially as I'm on 32'' hdmi monitor and I've changed the videocard that was damaged (but it's always nvidia).
The resolution is set to native 1920x1080 but all the fonts are too small to be read (10pt seems to be 5pt).

How can I fix the font issues?
or, better,
How can I restore the default settings of x-server?
and how can I fully remove the nvidia driver? (I'm pretty sure it's outdated and part of my problems)
Thanks in advance^^

---

### Post by Bashing-om on 2016-04-13
Hadden89; Hello;

Let's look and see if the hardware is identified correctly, AND what driver is loaded for the video display .
Post back the result of terminal command:
```

sudo lshw -C display

```

As the place to start troubleshooting.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-13
Thanks,
For now, I workaround-ed the issue doubling the text in lxde settings (however some apps, as package installer uses the smaller ones).

```

*-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 610]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:47 memory:fd000000-fdffffff memory:e8000000-efffffff memory:e6000000-e7ffffff ioport:dc00(size=128) memory:fe900000-fe97ffff

```

---

### Post by Bashing-om on 2016-04-13
Hadden89; Well !

Nvidia recommends the 361 version driver for this card ...
[http://www.nvidia.com/download/driverResults.aspx/101423/en-us](http://www.nvidia.com/download/driverResults.aspx/101423/en-us)

Let's next look at what is installed:
```

dpkg -l | grep -i nvidia

```

see then were we go .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-13
I'll use this as my machine is x32 (forgot to mention)
[http://www.nvidia.it/download/driverResults.aspx/101435/it](http://www.nvidia.it/download/driverResults.aspx/101435/it)

The installer, after giving chmod +x, it asks me to exit x-server.
How install from there? (Sorry, I'm very noob out the gui)

I tried to do at root user in grub recovery mode but it says that can't make \tmp folder and tried to boot init 3 level (user, I think).
But the monitor start to blink and doesn't work, at that point (even in CLI).

mmh..two version of the same thing (and old ones)
```
hadden@hadden-box:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                               0.7-2ubuntu1                            i386         Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-340                                340.96-0ubuntu0.14.04.1                 i386         NVIDIA CUDA runtime library
ii  libcuda1-352                                352.63-0ubuntu0.14.04.1                 i386         NVIDIA CUDA runtime library
rc  nvidia-331                                  340.96-0ubuntu0.14.04.1                 i386         Transitional package for nvidia-331
rc  nvidia-340                                  340.96-0ubuntu0.14.04.1                 i386         NVIDIA binary driver - version 340.96
ii  nvidia-352                                  352.63-0ubuntu0.14.04.1                 i386         NVIDIA binary driver - version 352.63
rc  nvidia-libopencl1-340                       340.96-0ubuntu0.14.04.1                 i386         NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-340                       340.96-0ubuntu0.14.04.1                 i386         NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-352                       352.63-0ubuntu0.14.04.1                 i386         NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.2                                   i386         Tools to enable NVIDIA's Prime
ii  nvidia-settings                             331.20-0ubuntu8                         i386         Tool for configuring the NVIDIA graphics driver
```


"Funny" grub facts:
- Choosing main ubuntu boot, usually doesn't work (I think it uses last kernel)
- Using ubuntu 3.16.0.-70-generic, very often doesn't start
- Using ubuntu 3-16.0-38-generic, usually works
- Using ubuntu 3-16.0-30-generic, I see very big fonts (as I "doubled")

*edit*
I installed new driver from root prompt (grub screen)
I'd to take rw, as root was read only
```
mount -o remount, rw /
```
then I unlocked the file in /tmp
```
rm -rf .X0-lock
```
and run the installer
```
./NV*.run
```
Now the only one kernel which works, with issues and double fonts, is 30-generic. The other two doesn't.
If I open a terminal (GUI terminal) from LXDE, the screen start to blink and then disappear completely.

---

### Post by Bashing-om on 2016-04-14
Hadden89; Ouch !

I am not to sure what to make of not booting with newer kernels.
Let's see what the foundation of the system is.
Post back the outputs of terminal commands:
```

sudo apt update
sudo apt full-upgrade
sudo apt-get -f install
dpkg -l | grep linux-

```

Then we want to consider (RE-)installing the graphics driver from other than OEM. Maintenance with that type of driver installation "can be" a real head ache .

[INDENT][INDENT]back up 3 yards and punt
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-15
```
hadden@hadden-box:~$ sudo apt update
[sudo] password for hadden: 
Ign http://it.archive.ubuntu.com trusty InRelease
Trovato http://it.archive.ubuntu.com trusty-updates InRelease                  
Trovato http://security.ubuntu.com trusty-security InRelease                   
Ign http://archive.canonical.com trusty InRelease                              
Trovato http://it.archive.ubuntu.com trusty Release.gpg                        
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Trovato http://it.archive.ubuntu.com trusty-updates/main Sources               
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://security.ubuntu.com trusty-security/main Sources                
Trovato http://it.archive.ubuntu.com trusty-updates/restricted Sources         
Trovato http://extras.ubuntu.com trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://it.archive.ubuntu.com trusty-updates/universe Sources           
Trovato http://archive.canonical.com trusty Release                            
Trovato http://security.ubuntu.com trusty-security/restricted Sources          
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://it.archive.ubuntu.com trusty-updates/multiverse Sources         
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://security.ubuntu.com trusty-security/universe Sources            
Trovato http://it.archive.ubuntu.com trusty-updates/main i386 Packages         
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://extras.ubuntu.com trusty/main Sources                           
Trovato http://it.archive.ubuntu.com trusty-updates/restricted i386 Packages   
Trovato http://security.ubuntu.com trusty-security/multiverse Sources          
Trovato http://it.archive.ubuntu.com trusty-updates/universe i386 Packages     
Trovato http://archive.canonical.com trusty/partner Translation-en             
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Trovato http://it.archive.ubuntu.com trusty-updates/multiverse i386 Packages   
Trovato http://security.ubuntu.com trusty-security/main i386 Packages          
Trovato http://it.archive.ubuntu.com trusty-updates/main Translation-en        
Trovato http://security.ubuntu.com trusty-security/restricted i386 Packages    
Trovato http://it.archive.ubuntu.com trusty-updates/multiverse Translation-en  
Trovato http://it.archive.ubuntu.com trusty-updates/restricted Translation-en  
Trovato http://security.ubuntu.com trusty-security/universe i386 Packages      
Trovato http://it.archive.ubuntu.com trusty-updates/universe Translation-en    
Trovato http://security.ubuntu.com trusty-security/multiverse i386 Packages    
Trovato http://it.archive.ubuntu.com trusty Release                            
Trovato http://security.ubuntu.com trusty-security/main Translation-en         
Trovato http://it.archive.ubuntu.com trusty/main Sources                       
Trovato http://security.ubuntu.com trusty-security/multiverse Translation-en   
Trovato http://it.archive.ubuntu.com trusty/restricted Sources                 
Trovato http://security.ubuntu.com trusty-security/restricted Translation-en   
Trovato http://it.archive.ubuntu.com trusty/universe Sources                   
Trovato http://security.ubuntu.com trusty-security/universe Translation-en     
Trovato http://it.archive.ubuntu.com trusty/multiverse Sources                 
Trovato http://it.archive.ubuntu.com trusty/main i386 Packages                 
Trovato http://it.archive.ubuntu.com trusty/restricted i386 Packages      
Trovato http://it.archive.ubuntu.com trusty/universe i386 Packages        
Trovato http://it.archive.ubuntu.com trusty/multiverse i386 Packages      
Trovato http://it.archive.ubuntu.com trusty/main Translation-it           
Trovato http://it.archive.ubuntu.com trusty/main Translation-en                
Trovato http://it.archive.ubuntu.com trusty/multiverse Translation-it          
Trovato http://it.archive.ubuntu.com trusty/multiverse Translation-en          
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Trovato http://it.archive.ubuntu.com trusty/restricted Translation-it          
Trovato http://it.archive.ubuntu.com trusty/restricted Translation-en          
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://it.archive.ubuntu.com trusty/universe Translation-it            
Trovato http://it.archive.ubuntu.com trusty/universe Translation-en
Ign http://it.archive.ubuntu.com trusty/main Translation-it_IT
Ign http://it.archive.ubuntu.com trusty/multiverse Translation-it_IT
Ign http://it.archive.ubuntu.com trusty/restricted Translation-it_IT
Ign http://it.archive.ubuntu.com trusty/universe Translation-it_IT
Lettura elenco dei pacchetti... Fatto                                          
hadden@hadden-box:~$ sudo apt full-upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Eseguito
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  libavahi-compat-libdnssd1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno aggiornati:
  simple-scan
1 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
È necessario scaricare 134 kB di archivi.
Dopo quest'operazione, verranno occupati 4.096 B di spazio su disco.
Continuare? [S/n] s
Scaricamento di:1 http://it.archive.ubuntu.com/ubuntu/ trusty-updates/main simple-scan i386 3.12.3-0ubuntu1 [134 kB]
Recuperati 134 kB in 0s (516 kB/s)  
(Lettura del database... 168252 file e directory attualmente installati.)
Preparing to unpack .../simple-scan_3.12.3-0ubuntu1_i386.deb ...
Unpacking simple-scan (3.12.3-0ubuntu1) over (3.12.1-0ubuntu1) ...
Processing triggers for libglib2.0-0:i386 (2.40.2-0ubuntu1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Configurazione di simple-scan (3.12.3-0ubuntu1)...
hadden@hadden-box:~$ sudo apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  libavahi-compat-libdnssd1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
Usare "apt-get autoremove" per rimuoverli.
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
hadden@hadden-box:~$ dpkg -l | grep linux-
ii  linux-firmware                              1.127.20                                all          Firmware for Linux kernel drivers
ii  linux-generic-lts-utopic                    3.16.0.70.61                            i386         Complete Generic Linux kernel and headers
ii  linux-headers-3.16.0-30                     3.16.0-30.40~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-30-generic             3.16.0-30.40~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-38                     3.16.0-38.52~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-38-generic             3.16.0-38.52~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-3.16.0-70                     3.16.0-70.90~14.04.1                    all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-70-generic             3.16.0-70.90~14.04.1                    i386         Linux kernel headers for version 3.16.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-utopic            3.16.0.70.61                            i386         Generic Linux kernel headers
ii  linux-image-3.16.0-30-generic               3.16.0-30.40~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-38-generic               3.16.0-38.52~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-3.16.0-70-generic               3.16.0-70.90~14.04.1                    i386         Linux kernel image for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-30-generic         3.16.0-30.40~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-38-generic         3.16.0-38.52~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-extra-3.16.0-70-generic         3.16.0-70.90~14.04.1                    i386         Linux kernel extra modules for version 3.16.0 on 32 bit x86 SMP
ii  linux-image-generic-lts-utopic              3.16.0.70.61                            i386         Generic Linux kernel image
ii  linux-libc-dev:i386                         3.13.0-85.129                           i386         Linux Kernel Headers for development
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:4.05+dfsg-6+deb8u1                    all          collection of boot loaders (common files)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                    i386         Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                      12-3ubuntu0.14.04.1                     all          collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-wheezy               12-3ubuntu0.14.04.1                     all          collection of boot loaders (debian-wheezy theme)
hadden@hadden-box:~$ 


```

---

### Post by Bashing-om on 2016-04-15
Hadden89; Well,.

I see no cause for concern there ...all looks good to me.

Let's see if we can see what is going on by looking at the log file for X ( display layer).
```

cat /var/log/Xorg.0.log

```
and compare to the known hardware:
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display

```

Get a better idea of what we are going to do.

[INDENT][INDENT]there is that way that seems right
[INDENT][INDENT][INDENT]but leads to a broken system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-15
```
hadden@hadden-box:~$ cat /var/log/Xorg.0.log
[    24.596] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    24.596] X Protocol Version 11, Revision 0
[    24.596] Build Operating System: Linux 3.2.0-70-generic i686 Ubuntu
[    24.596] Current Operating System: Linux hadden-box 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686
[    24.596] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-30-generic root=UUID=4e619e66-caaf-4b36-992c-03c09dc1518e ro quiet splash
[    24.596] Build Date: 12 February 2015  11:11:29PM
[    24.596] xorg-server 2:1.16.0-1ubuntu1.2~trusty2 (For technical support please see http://www.ubuntu.com/support) 
[    24.596] Current version of pixman: 0.30.2
[    24.596]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.596] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.596] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 15 23:30:38 2016
[    24.613] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.666] (==) No Layout section.  Using the first Screen section.
[    24.666] (==) No screen section available. Using defaults.
[    24.666] (**) |-->Screen "Default Screen Section" (0)
[    24.666] (**) |   |-->Monitor "<default monitor>"
[    24.682] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.682] (==) Automatically adding devices
[    24.682] (==) Automatically enabling devices
[    24.682] (==) Automatically adding GPU devices
[    24.682] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.682]     Entry deleted from font path.
[    24.682] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    24.682] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.682] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.682] (II) Loader magic: 0xb7802660
[    24.682] (II) Module ABI versions:
[    24.682]     X.Org ANSI C Emulation: 0.4
[    24.682]     X.Org Video Driver: 18.0
[    24.682]     X.Org XInput driver : 21.0
[    24.682]     X.Org Server Extension : 8.0
[    24.682] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.684] (--) PCI:*(0:1:0:0) 10de:104a:1043:8408 rev 161, Mem @ 0xfd000000/16777216, 0xe8000000/134217728, 0xe6000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    24.692] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    24.692] (II) "glx" will be loaded by default.
[    24.692] (II) LoadModule: "glx"
[    24.692] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    25.358] (II) Module glx: vendor="NVIDIA Corporation"
[    25.358]     compiled for 4.0.2, module version = 1.0.0
[    25.358]     Module class: X.Org Server Extension
[    25.358] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:53:58 PST 2015
[    25.358] (==) Matched nvidia as autoconfigured driver 0
[    25.358] (==) Matched nouveau as autoconfigured driver 1
[    25.358] (==) Matched nvidia as autoconfigured driver 2
[    25.358] (==) Matched nouveau as autoconfigured driver 3
[    25.358] (==) Matched modesetting as autoconfigured driver 4
[    25.358] (==) Matched fbdev as autoconfigured driver 5
[    25.358] (==) Matched vesa as autoconfigured driver 6
[    25.358] (==) Assigned the driver to the xf86ConfigLayout
[    25.358] (II) LoadModule: "nvidia"
[    25.358] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    25.359] (II) Module nvidia: vendor="NVIDIA Corporation"
[    25.359]     compiled for 4.0.2, module version = 1.0.0
[    25.359]     Module class: X.Org Video Driver
[    25.359] (II) LoadModule: "nouveau"
[    25.372] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    25.387] (II) Module nouveau: vendor="X.Org Foundation"
[    25.387]     compiled for 1.16.0, module version = 1.0.11
[    25.387]     Module class: X.Org Video Driver
[    25.387]     ABI class: X.Org Video Driver, version 18.0
[    25.387] (II) LoadModule: "modesetting"
[    25.387] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.387] (II) Module modesetting: vendor="X.Org Foundation"
[    25.387]     compiled for 1.16.0, module version = 0.9.0
[    25.387]     Module class: X.Org Video Driver
[    25.387]     ABI class: X.Org Video Driver, version 18.0
[    25.387] (II) LoadModule: "fbdev"
[    25.388] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.388] (II) Module fbdev: vendor="X.Org Foundation"
[    25.388]     compiled for 1.16.0, module version = 0.4.4
[    25.388]     Module class: X.Org Video Driver
[    25.388]     ABI class: X.Org Video Driver, version 18.0
[    25.388] (II) LoadModule: "vesa"
[    25.388] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.388] (II) Module vesa: vendor="X.Org Foundation"
[    25.388]     compiled for 1.16.0, module version = 2.3.3
[    25.388]     Module class: X.Org Video Driver
[    25.389]     ABI class: X.Org Video Driver, version 18.0
[    25.389] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:12 PST 2015
[    25.389] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    25.389] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    25.389] (II) NOUVEAU driver for NVIDIA chipset families :
[    25.389]     RIVA TNT        (NV04)
[    25.389]     RIVA TNT2       (NV05)
[    25.389]     GeForce 256     (NV10)
[    25.389]     GeForce 2       (NV11, NV15)
[    25.389]     GeForce 4MX     (NV17, NV18)
[    25.389]     GeForce 3       (NV20)
[    25.389]     GeForce 4Ti     (NV25, NV28)
[    25.389]     GeForce FX      (NV3x)
[    25.389]     GeForce 6       (NV4x)
[    25.389]     GeForce 7       (G7x)
[    25.389]     GeForce 8       (G8x)
[    25.389]     GeForce GTX 200 (NVA0)
[    25.389]     GeForce GTX 400 (NVC0)
[    25.389] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.389] (II) FBDEV: driver for framebuffer: fbdev
[    25.389] (II) VESA: driver for VESA chipsets: vesa
[    25.389] (++) using VT number 7

[    25.392] (II) Loading sub module "fb"
[    25.392] (II) LoadModule: "fb"
[    25.392] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.392] (II) Module fb: vendor="X.Org Foundation"
[    25.392]     compiled for 1.16.0, module version = 1.0.0
[    25.392]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.392] (II) Loading sub module "wfb"
[    25.392] (II) LoadModule: "wfb"
[    25.393] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    25.393] (II) Module wfb: vendor="X.Org Foundation"
[    25.393]     compiled for 1.16.0, module version = 1.0.0
[    25.393]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.393] (II) Loading sub module "ramdac"
[    25.393] (II) LoadModule: "ramdac"
[    25.393] (II) Module "ramdac" already built-in
[    25.394] (WW) Falling back to old probe method for modesetting
[    25.394] (WW) Falling back to old probe method for fbdev
[    25.394] (II) Loading sub module "fbdevhw"
[    25.394] (II) LoadModule: "fbdevhw"
[    25.394] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.394] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.394]     compiled for 1.16.0, module version = 0.0.2
[    25.394]     ABI class: X.Org Video Driver, version 18.0
[    25.394] (EE) open /dev/fb0: No such file or directory
[    25.394] (WW) Falling back to old probe method for vesa
[    25.395] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.395] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    25.395] (==) NVIDIA(0): RGB weight 888
[    25.395] (==) NVIDIA(0): Default visual is TrueColor
[    25.395] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.395] (**) NVIDIA(0): Enabling 2D acceleration
[    26.282] (II) NVIDIA: Allocated GPU:0 (GPU-beabe3d9-56a3-6d0b-cc50-d222afe9050c) @
[    26.282] (II) NVIDIA:     PCI:0000:01:00.0
[    26.300] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    26.300] (--) NVIDIA(0):     CRT-0
[    26.300] (--) NVIDIA(0):     CRT-1
[    26.300] (--) NVIDIA(0):     DFP-0
[    26.300] (--) NVIDIA(0):     DFP-1 (boot)
[    26.302] (--) NVIDIA(0): CRT-0: disconnected
[    26.303] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    26.303] (--) NVIDIA(0): 
[    26.304] (--) NVIDIA(0): CRT-1: disconnected
[    26.304] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    26.304] (--) NVIDIA(0): 
[    26.306] (--) NVIDIA(0): DFP-0: disconnected
[    26.306] (--) NVIDIA(0): DFP-0: Internal TMDS
[    26.306] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    26.307] (--) NVIDIA(0): 
[    26.319] (--) NVIDIA(0): LG Electronics LG TV (DFP-1): connected
[    26.319] (--) NVIDIA(0): LG Electronics LG TV (DFP-1): Internal TMDS
[    26.319] (--) NVIDIA(0): LG Electronics LG TV (DFP-1): 165.0 MHz maximum pixel clock
[    26.319] (--) NVIDIA(0): 
[    26.319] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20150116)
[    26.320] (II) NVIDIA(0): NVIDIA GPU GeForce GT 610 (GF119) at PCI:1:0:0 (GPU-0)
[    26.320] (--) NVIDIA(0): Memory: 2097152 kBytes
[    26.320] (--) NVIDIA(0): VideoBIOS: 75.19.55.00.02
[    26.320] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    26.329] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    26.329] (**) NVIDIA(0):     device LG Electronics LG TV (DFP-1) (Using EDID
[    26.329] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[    26.335] (==) NVIDIA(0): 
[    26.335] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    26.335] (==) NVIDIA(0):     will be used as the requested mode.
[    26.335] (==) NVIDIA(0): 
[    26.335] (II) NVIDIA(0): Validated MetaModes:
[    26.336] (II) NVIDIA(0):     "DFP-1:nvidia-auto-select"
[    26.336] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    26.355] (--) NVIDIA(0): DPI set to (30, 30); computed from "UseEdidDpi" X config
[    26.355] (--) NVIDIA(0):     option
[    26.355] (II) UnloadModule: "nouveau"
[    26.355] (II) Unloading nouveau
[    26.355] (II) UnloadModule: "modesetting"
[    26.355] (II) Unloading modesetting
[    26.355] (II) UnloadModule: "fbdev"
[    26.355] (II) Unloading fbdev
[    26.355] (II) UnloadSubModule: "fbdevhw"
[    26.355] (II) Unloading fbdevhw
[    26.355] (II) UnloadModule: "vesa"
[    26.355] (II) Unloading vesa
[    26.355] (--) Depth 24 pixmap format is 32 bpp
[    26.356] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    26.356] (II) NVIDIA:     access.
[    26.415] (II) NVIDIA(0): Setting mode "DFP-1:nvidia-auto-select"
[    26.500] (==) NVIDIA(0): Disabling shared memory pixmaps
[    26.500] (==) NVIDIA(0): Backing store enabled
[    26.500] (==) NVIDIA(0): Silken mouse enabled
[    26.504] (==) NVIDIA(0): DPMS enabled
[    26.504] (II) Loading sub module "dri2"
[    26.504] (II) LoadModule: "dri2"
[    26.504] (II) Module "dri2" already built-in
[    26.504] (II) NVIDIA(0): [DRI2] Setup complete
[    26.504] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    26.504] (--) RandR disabled
[    26.533] (II) Initializing extension GLX
[    26.554] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.559] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.559] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.559] (II) LoadModule: "evdev"
[    26.559] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.579] (II) Module evdev: vendor="X.Org Foundation"
[    26.579]     compiled for 1.16.0, module version = 2.9.0
[    26.579]     Module class: X.Org XInput Driver
[    26.579]     ABI class: X.Org XInput driver, version 21.0
[    26.579] (II) Using input driver 'evdev' for 'Power Button'
[    26.579] (**) Power Button: always reports core events
[    26.579] (**) evdev: Power Button: Device: "/dev/input/event1"
[    26.580] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.580] (--) evdev: Power Button: Found keys
[    26.580] (II) evdev: Power Button: Configuring as keyboard
[    26.580] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    26.580] (**) Option "xkb_rules" "evdev"
[    26.580] (**) Option "xkb_model" "pc105"
[    26.580] (**) Option "xkb_layout" "it"
[    26.583] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    26.584] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.584] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.584] (II) Using input driver 'evdev' for 'Power Button'
[    26.584] (**) Power Button: always reports core events
[    26.584] (**) evdev: Power Button: Device: "/dev/input/event0"
[    26.584] (--) evdev: Power Button: Vendor 0 Product 0x1
[    26.585] (--) evdev: Power Button: Found keys
[    26.585] (II) evdev: Power Button: Configuring as keyboard
[    26.585] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    26.585] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    26.585] (**) Option "xkb_rules" "evdev"
[    26.585] (**) Option "xkb_model" "pc105"
[    26.585] (**) Option "xkb_layout" "it"
[    26.586] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event8)
[    26.586] (II) No input driver specified, ignoring this device.
[    26.586] (II) This device may have been added with another device file.
[    26.586] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event9)
[    26.586] (II) No input driver specified, ignoring this device.
[    26.586] (II) This device may have been added with another device file.
[    26.586] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[    26.586] (II) No input driver specified, ignoring this device.
[    26.586] (II) This device may have been added with another device file.
[    26.587] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event5)
[    26.587] (II) No input driver specified, ignoring this device.
[    26.587] (II) This device may have been added with another device file.
[    26.587] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[    26.587] (II) No input driver specified, ignoring this device.
[    26.587] (II) This device may have been added with another device file.
[    26.588] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event2)
[    26.588] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    26.588] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    26.588] (**) Microsoft Wired Keyboard 600: always reports core events
[    26.588] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event2"
[    26.588] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[    26.588] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    26.588] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    26.588] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/0003:045E:0750.0001/input/input5/event2"
[    26.588] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 8)
[    26.588] (**) Option "xkb_rules" "evdev"
[    26.588] (**) Option "xkb_model" "pc105"
[    26.588] (**) Option "xkb_layout" "it"
[    26.589] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/event3)
[    26.589] (**) Microsoft Wired Keyboard 600: Applying InputClass "evdev keyboard catchall"
[    26.589] (II) Using input driver 'evdev' for 'Microsoft Wired Keyboard 600'
[    26.589] (**) Microsoft Wired Keyboard 600: always reports core events
[    26.590] (**) evdev: Microsoft Wired Keyboard 600: Device: "/dev/input/event3"
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Vendor 0x45e Product 0x750
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found 1 mouse buttons
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found scroll wheel(s)
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found relative axes
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found absolute axes
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found absolute multitouch axes
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found x and y absolute axes
[    26.590] (--) evdev: Microsoft Wired Keyboard 600: Found keys
[    26.590] (II) evdev: Microsoft Wired Keyboard 600: Forcing relative x/y axes to exist.
[    26.590] (II) evdev: Microsoft Wired Keyboard 600: Configuring as mouse
[    26.590] (II) evdev: Microsoft Wired Keyboard 600: Configuring as keyboard
[    26.590] (II) evdev: Microsoft Wired Keyboard 600: Adding scrollwheel support
[    26.590] (**) evdev: Microsoft Wired Keyboard 600: YAxisMapping: buttons 4 and 5
[    26.590] (**) evdev: Microsoft Wired Keyboard 600: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.590] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/0003:045E:0750.0002/input/input6/event3"
[    26.590] (II) XINPUT: Adding extended input device "Microsoft Wired Keyboard 600" (type: KEYBOARD, id 9)
[    26.590] (**) Option "xkb_rules" "evdev"
[    26.590] (**) Option "xkb_model" "pc105"
[    26.590] (**) Option "xkb_layout" "it"
[    26.590] (II) evdev: Microsoft Wired Keyboard 600: initialized for relative axes.
[    26.590] (WW) evdev: Microsoft Wired Keyboard 600: ignoring absolute axes.
[    26.591] (**) Microsoft Wired Keyboard 600: (accel) keeping acceleration scheme 1
[    26.591] (**) Microsoft Wired Keyboard 600: (accel) acceleration profile 0
[    26.591] (**) Microsoft Wired Keyboard 600: (accel) acceleration factor: 2.000
[    26.591] (**) Microsoft Wired Keyboard 600: (accel) acceleration threshold: 4
[    26.592] (II) config/udev: Adding input device Microsoft Wired Keyboard 600 (/dev/input/js0)
[    26.592] (II) No input driver specified, ignoring this device.
[    26.592] (II) This device may have been added with another device file.
[    26.593] (II) config/udev: Adding input device USB Mouse (/dev/input/event4)
[    26.593] (**) USB Mouse: Applying InputClass "evdev pointer catchall"
[    26.593] (II) Using input driver 'evdev' for 'USB Mouse'
[    26.593] (**) USB Mouse: always reports core events
[    26.593] (**) evdev: USB Mouse: Device: "/dev/input/event4"
[    26.593] (--) evdev: USB Mouse: Vendor 0x1b1a Product 0
[    26.593] (--) evdev: USB Mouse: Found 3 mouse buttons
[    26.593] (--) evdev: USB Mouse: Found scroll wheel(s)
[    26.593] (--) evdev: USB Mouse: Found relative axes
[    26.593] (--) evdev: USB Mouse: Found x and y relative axes
[    26.593] (II) evdev: USB Mouse: Configuring as mouse
[    26.593] (II) evdev: USB Mouse: Adding scrollwheel support
[    26.593] (**) evdev: USB Mouse: YAxisMapping: buttons 4 and 5
[    26.593] (**) evdev: USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.593] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/0003:1B1A:0000.0003/input/input7/event4"
[    26.593] (II) XINPUT: Adding extended input device "USB Mouse" (type: MOUSE, id 10)
[    26.593] (II) evdev: USB Mouse: initialized for relative axes.
[    26.593] (**) USB Mouse: (accel) keeping acceleration scheme 1
[    26.593] (**) USB Mouse: (accel) acceleration profile 0
[    26.593] (**) USB Mouse: (accel) acceleration factor: 2.000
[    26.593] (**) USB Mouse: (accel) acceleration threshold: 4
[    26.594] (II) config/udev: Adding input device USB Mouse (/dev/input/mouse0)
[    26.594] (II) No input driver specified, ignoring this device.
[    26.594] (II) This device may have been added with another device file.
[    26.777] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): connected
[    26.777] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): Internal TMDS
[    26.777] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): 230.0 MHz maximum pixel clock
[    26.777] (--) NVIDIA(GPU-0): 
[    26.789] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): connected
[    26.798] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): Internal TMDS
[    26.798] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): 230.0 MHz maximum pixel clock
[    26.798] (--) NVIDIA(GPU-0): 
[    37.245] (--) NVIDIA(GPU-0): CRT-0: disconnected
[    37.245] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[    37.245] (--) NVIDIA(GPU-0): 
[    37.246] (--) NVIDIA(GPU-0): CRT-1: disconnected
[    37.246] (--) NVIDIA(GPU-0): CRT-1: 400.0 MHz maximum pixel clock
[    37.246] (--) NVIDIA(GPU-0): 
[    37.249] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    37.249] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    37.249] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    37.249] (--) NVIDIA(GPU-0): 
[    37.261] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): connected
[    37.261] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): Internal TMDS
[    37.261] (--) NVIDIA(GPU-0): LG Electronics LG TV (DFP-1): 230.0 MHz maximum pixel clock
[    37.261] (--) NVIDIA(GPU-0): 
hadden@hadden-box:~$ 

```

```
hadden@hadden-box:~$ lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 8408
    Kernel driver in use: nvidia
hadden@hadden-box:~$ 

```

```
hadden@hadden-box:~$ sudo lshw -C display
[sudo] password for hadden: 
  *-display               
       description: VGA compatible controller
       product: GF119 [GeForce GT 610]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:47 memory:fd000000-fdffffff memory:e8000000-efffffff memory:e6000000-e7ffffff ioport:dc00(size=128) memory:fe900000-fe97ffff
hadden@hadden-box:~$ 

```

---

### Post by Bashing-om on 2016-04-15
Hadden89; Humm ...

Log file says there is no problem, and everything matches hardware wise.....

Does this file exist ?
```

la -al /etc/X11/Xorg.conf

```
The use of that file with a single GPU is depreciated, and will I not be surprised if it does not exist.

Do we have any hints in the display file ? :
```

cat .xsession-errors

```

To this time I can not point a finger at anything to cause the display or the booting problem .

[INDENT][INDENT]still, just do not know
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-15
xorg.conf not found

```
hadden@hadden-box:~$ cat .xsession-errors
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
hadden@hadden-box:~$ 

```

---

### Post by Bashing-om on 2016-04-15
Hadden89; Hey ...

I am stuck .. lemme ponder a bit . See what I can come up with .

[INDENT][INDENT]nothing from nothing leaves nothing
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-16
Ok, thanks,
For now I've installed .361 from an external PPA and seems to work quite well.
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
The underscan function now works. (Desktop doesn't go outside the borders).
Fonts are small, so I still using the text x2 workaround for that.

---

### Post by Bashing-om on 2016-04-16
Hadden89; Good show !

I had also considered the PPA for the 361 version.

Let's insure there is no driver conflict.
What now returns :
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-16
```
hadden@hadden-box:~$ dpkg -l | grep -i nvidia
ii  bbswitch-dkms                       0.7-2ubuntu1                             i386         Interface for toggling the power on nVidia Optimus video cards
rc  libcuda1-304-updates                304.131-0ubuntu0.15.10.1                 i386         NVIDIA CUDA runtime library
rc  libcuda1-352                        352.63-0ubuntu0.15.10.1                  i386         NVIDIA CUDA runtime library
rc  libcuda1-352-updates                352.63-0ubuntu0.15.10.1                  i386         NVIDIA CUDA runtime library
ii  libcuda1-361                        361.42-0ubuntu0~gpu15.10.1               i386         NVIDIA CUDA runtime library
rc  nvidia-304-updates                  304.131-0ubuntu0.15.10.1                 i386         NVIDIA legacy binary driver - version 304.131
rc  nvidia-352                          352.63-0ubuntu0.15.10.1                  i386         NVIDIA binary driver - version 352.63
rc  nvidia-352-updates                  352.63-0ubuntu0.15.10.1                  i386         NVIDIA binary driver - version 352.63
ii  nvidia-361                          361.42-0ubuntu0~gpu15.10.1               i386         NVIDIA binary driver - version 361.42
ii  nvidia-libopencl1-361               361.42-0ubuntu0~gpu15.10.1               i386         NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-opencl-icd-304-updates       304.131-0ubuntu0.15.10.1                 i386         NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-352               352.63-0ubuntu0.15.10.1                  i386         NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-352-updates       352.63-0ubuntu0.15.10.1                  i386         NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-361               361.42-0ubuntu0~gpu15.10.1               i386         NVIDIA OpenCL ICD
ii  nvidia-prime                        0.8.1                                    i386         Tools to enable NVIDIA's Prime
ii  nvidia-settings                     364.15-0ubuntu0~gpu15.10.1               i386         Tool for configuring the NVIDIA graphics driver
hadden@hadden-box:~$ 

```

I only to fix font thing.. Could be related to DPI, maybe?

*edit* 
The default DPI I had was >50x50. (from xdpyinfo|grep res command)
Followed this, now dpi seems to be fixed (and font also)[URL="http://ubuntuforums.org/showthread.php?t=1896206"]
[http://ubuntuforums.org/showthread.php?t=1896206](http://ubuntuforums.org/showthread.php?t=1896206)
I'll test for a while and then I'll mark as solved :)
Thanks.

[/URL]

---

### Post by Bashing-om on 2016-04-16
Hadden89' Maybe;

make nvidia-settings:
> 
ii  nvidia-settings                     364.15-0ubuntu0~gpu15.10.1

match:
> 
ii  nvidia-361                          361.42-0ubuntu0~gpu15.10.1



[INDENT][INDENT]is a thought ...
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-16
Probably it's better use .361. In first istance I used that.
Then the PPA told me to update to the newer .364 and so I tried.
However both seems to work in any case.
If I notice some strange I'll back to .361.
If you mean is better for "version coherence", I'll put it back.

---

### Post by Bashing-om on 2016-04-16
Hadden89; K.

When you are stable and satisfied .. to clean up all the old installs ( marked as 'rc' - packages removed but config files remain) run:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

[INDENT][INDENT]I like clean behind me
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-17
Ok, also cleaned and marked as solved.
Thank you a lot :D

---

### Post by Bashing-om on 2016-04-17
Hadden89; Good deal;

We like "solved" . You did all the work, all I did was look over your shoulder.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Hadden89 on 2016-04-18
Blank screen happen only launching lxterm which probably does something wrong with x-Nvidia and HDMI output.
Switched to roxterm, everything's perfect.
Thanks again =)

---

### Post by Bashing-om on 2016-04-18
Hadden89; Well !

Good show ... but, still like to learn what is not going on .. that the Nvidia driver will not build and load .

Real real strange that this boils down to a terminal issue - or perhaps a Desktop Environment thing.

[INDENT][INDENT]just goes to show
[/INDENT][/INDENT]

---

