---
title: "apt-get install vmware player fails, compile from tar.gz fails"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by timothyp on 2007-04-23
Any machine I install feisty on , I cannot apt-get install vmware-player.
it downloads the packages but something goes wrong every time.

```

Reading package lists... Done                                                   
Building dependency tree                                                        
Reading state information... Done                                               
The following packages were automatically installed and are no longer required: 
  libgtkhtml3.8-19 libxcb1 libxcb-xlib0                                         
Use 'apt-get autoremove' to remove them.                                        
The following NEW packages will be installed:                                   
  vmware-player                                                                 
0 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.                 
2 not fully installed or removed.                                               
Need to get 11.9MB of archives.                                                 
After unpacking 32.1MB of additional disk space will be used.                   
Get:1 http://be.archive.ubuntu.com feisty/multiverse vmware-player 1.0.2-2 [11.9
MB]                                                                             
..........

Setting up vmware-player-kernel-modules-2.6.20-15 (2.6.20.5-15.20) ...          
Setting up vmware-player-kernel-modules (2.6.20.15.14) ...
Setting up vmware-player (1.0.2-2) ...
Now configuring VMware Player.  (This may take some time...) 
Configuring a bridged network for vmnet0.

Configuring a NAT network for vmnet8.

Probing for an unused private subnet (this can take some time)...

......

Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an

```


I tried downloaden the tar.gz for 1.0.3, but I get weird compilation errors:
```

None of the pre-built vmmon modules for VMware Player is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.20-15-generic/build/include
...
D/. modules                                                                     
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'          
  CC [M]  /tmp/vmware-config4/vmmon-only/linux/driver.o                         
In file included from /tmp/vmware-config4/vmmon-only/linux/driver.c:80:         
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected dec
laration specifiers or ‘...’ before ‘compat_exit’                               
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: error: expected dec
laration specifiers or ‘...’ before ‘exit_code’                                 
/tmp/vmware-config4/vmmon-only/./include/compat_kernel.h:21: warning: type defau
lts to ‘int’ in declaration of ‘_syscall1’                                      
make[2]: *** [/tmp/vmware-config4/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config4/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config4/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

I have got the linux headers installed, and gcc, and ccp and build-essential

What's going on ?

---

### Post by mannheim on 2007-04-23
I don't really know what's going on, but one thing that did work for me was downloading the beta of the next version from vmware's site, as a tar.gz.

In my case, I'm using VMWare Workstation (and the beta version is 6.0). There's a corresponding beta version of the Player, version 2, which probably shares the underlying "difficult bits".

---

### Post by timothyp on 2007-04-23
Thank you :)

---

