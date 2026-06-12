---
title: "Fatal server error: (EE) no screens found(EE)"
date: 2024-10-17
forum: Installation &amp; Upgrades
---

### Post by Xpdin on 2024-10-17
[COLOR=#0C0D0E][FONT=-apple-system]Excuse me please, I am not so advanced. It is about Hostinger vps, Firstly I chose to install on the vps one of their predefined os, availed o their web site, Ubuntu 22.04, and then I accessed their terminal, and then I [/FONT][/COLOR]```
sudo apt install ubuntu-desktop
```[COLOR=#0C0D0E][FONT=-apple-system] in order to access the gui version of Ubuntu.[/FONT][/COLOR]```
startx
```[COLOR=#0C0D0E][FONT=-apple-system] Have I done something wrong? Thank you.[/FONT][/COLOR]

New installed Ubuntu 22.04, on vps. It has never worked.

    ```
root@srv621632:~# startx
    
    
    X.Org X Server 1.21.1.11
    X Protocol Version 11, Revision 0
    Current Operating System: Linux srv621632 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64
    Kernel command line: BOOT_IMAGE=/vmlinuz-6.8.0-47-generic root=UUID=ff94d49d-0bcd-4b6f-827e-4f16266b0bf6 ro console=tty0 console=ttyS0,115200 earlyprintk=ttyS0,115200 consoleblank=0 memhp_default_state=online console=tty1 console=ttyS0
    xorg-server 2:21.1.12-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
    Current version of pixman: 0.42.2
            Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
            to make sure that you have the latest version.
    Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    (==) Log file: "/var/log/Xorg.1.log", Time: Thu Oct 17 18:25:51 2024
    (==) Using system config directory "/usr/share/X11/xorg.conf.d"
    (EE) 
    Fatal server error:
    (EE) no screens found(EE) 
    (EE) 
    Please consult the The X.Org Foundation support 
             at [http://wiki.x.org](http://wiki.x.org)
     for help. 
    (EE) Please also check the log file at "/var/log/Xorg.1.log" for additional information.
    (EE) 
    (EE) Server terminated with error (1). Closing log file.
    xinit: giving up
    xinit: unable to connect to X server: Connection refused
    xinit: server error
    root@srv621632:~# 

```

/etc/X11/xorg.conf:


  


    ```
GNU nano 7.2                                                                                          /var/log/Xorg.0.log                                                                                                   
    [ 64366.983]
    X.Org X Server 1.21.1.11
    X Protocol Version 11, Revision 0
    [ 64366.983] Current Operating System: Linux srv621632 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64
    [ 64366.984] Kernel command line: BOOT_IMAGE=/vmlinuz-6.8.0-47-generic root=UUID=ff94d49d-0bcd-4b6f-827e-4f16266b0bf6 ro console=tty0 console=ttyS0,115200 earlyprintk=ttyS0,115200 consoleblank=0 memhp_default_state=online>
    [ 64366.984] xorg-server 2:21.1.12-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
    [ 64366.984] Current version of pixman: 0.42.2
    [ 64366.984]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
            to make sure that you have the latest version.
    [ 64366.984] Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    [ 64366.984] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 17 18:24:29 2024
    [ 64366.984] (II) Loader magic: 0x637e37196020
    [ 64366.984] (II) Module ABI versions:
    [ 64366.984]    X.Org ANSI C Emulation: 0.4
    [ 64366.984]    X.Org Video Driver: 25.2
    [ 64366.984]    X.Org XInput driver : 24.4
    [ 64366.984]    X.Org Server Extension : 10.0
    [ 64366.984] (--) using VT number 2
    
    [ 64366.984] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
    [ 64366.987] List of video drivers:
    [ 64366.987]    amdgpu
    [ 64366.987]    ati
    [ 64366.987]    intel
    [ 64366.987]    nouveau
    [ 64366.987]    qxl
    [ 64366.987]    radeon
    [ 64366.987]    vmware
    [ 64366.987]    modesetting
    [ 64366.987]    fbdev
    [ 64366.987]    vesa
    [ 64366.987] (II) LoadModule: "amdgpu"
    [ 64366.987] (II) Loading /usr/lib/xorg/modules/drivers/amdgpu_drv.so
    [ 64366.992] (II) Module amdgpu: vendor="X.Org Foundation"
    [ 64366.992]    compiled for 1.21.1.11, module version = 23.0.0
    [ 64366.992]    Module class: X.Org Video Driver
    [ 64366.992]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.992] (II) LoadModule: "ati"
    [ 64366.992] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
    [ 64366.992] (II) Module ati: vendor="X.Org Foundation"
    [ 64366.992]    compiled for 1.21.1.11, module version = 22.0.0
    [ 64366.992]    Module class: X.Org Video Driver
    [ 64366.992]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.992] (II) LoadModule: "intel"
    [ 64366.992] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
    [ 64366.995] (II) Module intel: vendor="X.Org Foundation"
    [ 64366.995]    compiled for 1.21.1.11, module version = 2.99.917
    [ 64366.995]    Module class: X.Org Video Driver
    [ 64366.995]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.995] (II) LoadModule: "nouveau"
    [ 64366.995] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
    [ 64366.996] (II) Module nouveau: vendor="X.Org Foundation"
    [ 64366.996]    compiled for 1.21.1.3, module version = 1.0.17
    [ 64366.996]    Module class: X.Org Video Driver
    [ 64366.996]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.996] (II) LoadModule: "qxl"
    [ 64366.996] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
    [ 64366.997] (II) Module qxl: vendor="X.Org Foundation"
    [ 64366.997]    compiled for 1.21.1.11, module version = 0.1.6
    [ 64366.997]    Module class: X.Org Video Driver
    [ 64366.997]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.997] (II) LoadModule: "radeon"
    [ 64366.997] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
    [ 64367.000] (II) Module radeon: vendor="X.Org Foundation"
    [ 64367.000]    compiled for 1.21.1.11, module version = 22.0.0
    [ 64367.000]    Module class: X.Org Video Driver
    [ 64367.000]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.000] (II) LoadModule: "vmware"
    [ 64367.000] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
    [ 64367.189] (II) Module vmware: vendor="X.Org Foundation"
    [ 64367.189]    compiled for 1.21.1.11, module version = 13.4.0
    [ 64367.189]    Module class: X.Org Video Driver
    [ 64367.189]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.189] (II) LoadModule: "modesetting"
    [ 64366.995]    Module class: X.Org Video Driver
    [ 64366.995]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.995] (II) LoadModule: "nouveau"
    [ 64366.995] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
    [ 64366.996] (II) Module nouveau: vendor="X.Org Foundation"
    [ 64366.996]    compiled for 1.21.1.3, module version = 1.0.17
    [ 64366.996]    Module class: X.Org Video Driver
    [ 64366.996]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.996] (II) LoadModule: "qxl"
    [ 64366.996] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
    [ 64366.997] (II) Module qxl: vendor="X.Org Foundation"
    [ 64366.997]    compiled for 1.21.1.11, module version = 0.1.6
    [ 64366.997]    Module class: X.Org Video Driver
    [ 64366.997]    ABI class: X.Org Video Driver, version 25.2
    [ 64366.997] (II) LoadModule: "radeon"
    [ 64366.997] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
    [ 64367.000] (II) Module radeon: vendor="X.Org Foundation"
    [ 64367.000]    compiled for 1.21.1.11, module version = 22.0.0
    [ 64367.000]    Module class: X.Org Video Driver
    [ 64367.000]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.000] (II) LoadModule: "vmware"
    [ 64367.000] (II) Loading /usr/lib/xorg/modules/drivers/vmware_drv.so
    [ 64367.189] (II) Module vmware: vendor="X.Org Foundation"
    [ 64367.189]    compiled for 1.21.1.11, module version = 13.4.0
    [ 64367.189]    Module class: X.Org Video Driver
    [ 64367.189]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.189] (II) LoadModule: "modesetting"
    [ 64367.189] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
    [ 64367.190] (II) Module modesetting: vendor="X.Org Foundation"
    [ 64367.190]    compiled for 1.21.1.11, module version = 1.21.1
    [ 64367.190]    Module class: X.Org Video Driver
    [ 64367.190]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.190] (II) LoadModule: "fbdev"
    [ 64367.190] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
    [ 64367.190] (II) Module fbdev: vendor="X.Org Foundation"
    [ 64367.190]    compiled for 1.21.1.11, module version = 0.5.0
    [ 64367.190]    Module class: X.Org Video Driver
    [ 64367.190]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.190] (II) LoadModule: "vesa"
    [ 64367.190] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
    [ 64367.190] (II) Module vesa: vendor="X.Org Foundation"
    [ 64367.190]    compiled for 1.21.1.7, module version = 2.6.0
    [ 64367.190]    Module class: X.Org Video Driver
    [ 64367.190]    ABI class: X.Org Video Driver, version 25.2
    [ 64367.190] (WW) Falling back to old probe method for modesetting
    [ 64367.190] (WW) Falling back to old probe method for fbdev
    [ 64367.190] No devices to configure.  Configuration failed.
    [ 64367.190] (EE) Server terminated with error (2). Closing log file.



```

Xorg -configure


    ```
root@srv621632:~# Xorg -configure
    
    X.Org X Server 1.21.1.11
    X Protocol Version 11, Revision 0
    Current Operating System: Linux srv621632 6.8.0-47-generic #47-Ubuntu SMP PREEMPT_DYNAMIC Fri Sep 27 21:40:26 UTC 2024 x86_64
    Kernel command line: BOOT_IMAGE=/vmlinuz-6.8.0-47-generic root=UUID=ff94d49d-0bcd-4b6f-827e-4f16266b0bf6 ro console=tty0 console=ttyS0,115200 earlyprintk=ttyS0,115200 consoleblank=0 memhp_default_state=online console=tty1 console=ttyS0
    xorg-server 2:21.1.12-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
    Current version of pixman: 0.42.2
            Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
            to make sure that you have the latest version.
    Markers: (--) probed, (**) from config file, (==) default setting,
            (++) from command line, (!!) notice, (II) informational,
            (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
    (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 17 18:36:26 2024
    List of video drivers:
            amdgpu
            ati
            intel
            nouveau
            qxl
            radeon
            vmware
            modesetting
            fbdev
            vesa
    No devices to configure.  Configuration failed.
    (EE) Server terminated with error (2). Closing log file.
    root@srv621632:~#
```

---

### Post by TheFu on 2024-10-19
I can only guess that there isn't any GPU (real of fake) connected to that VPS.  It is meant to be a server instance and Linux servers don't have any GUI.  Use ssh.  [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) is a good primer to get started.

If there is fake GPU connected, then the Gnome desktop is the worst choice. Gnome DE is bloated and really wants direct access to GPU hardware. Choose something like Mate, XFCE or LXQt for the DE instead and setup a remote desktop over a VPN to gain access securely.  Don't use remote desktops without a VPN unless you want to be hacked.

There are other options that provide network security and remote GUIs, but those are a little harder to setup.

Lastly, you need to know if your setup is using X11 or Wayland as the display server. Each has different capabilities. X11 has been around 40 yrs and it is where the startx command came from.  I don't know if Wayland uses startx or not, but I wouldn't assume it does.

X/Windows is a client/server architecture.  There's no magic. If you want to run it remotely, you'll need to setup that part of the connection to work. Usually, that would mean running a local X/Server for the remote X/client programs to send their packets.

---

