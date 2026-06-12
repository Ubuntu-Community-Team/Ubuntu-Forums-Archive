---
title: "apt-get upgrade error,"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2013-05-29
I'm having an issue upgrading


Here are some of reports


```

    sudo apt-get upgrade
    
    Errors were encountered while processing:
     /var/cache/apt/archives/linux-image-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb
    
    
    server@philo:/$ sudo apt-get upgrade -f
    The following NEW packages will be installed:
      linux-image-3.2.0-44-generic-pae
    E: Internal Error, No file name for libssl1.0.0


```

So I tried this...

    server@philo:/mnt/halftb/media/Videos$ sudo dpkg --configure -a
    
    Errors were encountered while processing:
     linux-image-generic-pae


Also 

sudo apt-get install libssl1.0.0

nothing




Heres a ton of output...

```


    (Reading database ... 80098 files and directories currently installed.)
    Unpacking linux-image-3.2.0-44-generic-pae (from .../linux-image-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb) ...
    Done.
    dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb (--unpack):
     failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-44-generic-pae': No space left on device
    No apport report written because MaxReports is reached already
                                                                  dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
    Examining /etc/kernel/postrm.d .
    run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
    run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-44-generic-pae /boot/vmlinuz-3.2.0-44-generic-pae
    Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.8 (using .../libssl1.0.0_1.0.1-4ubuntu5.9_i386.deb) ...
    Unpacking replacement libssl1.0.0 ...
    Errors were encountered while processing:
     /var/cache/apt/archives/linux-image-3.2.0-44-generic-pae_3.2.0-44.69_i386.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)
    server@philo:/mnt/halftb/media/Videos$ sudo apt-get upgrade -f
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Correcting dependencies... Done
    The following NEW packages will be installed:
      linux-image-3.2.0-44-generic-pae
    The following packages will be upgraded:
      aptitude bash-completion cifs-utils cups cups-bsd cups-client cups-common cups-ppdc libasound2 libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1
      libdrm-intel1 libdrm-nouveau1a libdrm-radeon1 libdrm2 libgnutls26 libtiff4 linux-image-generic-pae linux-libc-dev openssl python-apt python-apt-common rsyslog smbfs
    28 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
    3 not fully installed or removed.
    Need to get 0 B/46.8 MB of archives.
    After this operation, 113 MB of additional disk space will be used.
    Do you want to continue [Y/n]? Y
    E: Internal Error, No file name for libssl1.0.0
    server@philo:/mnt/halftb/media/Videos$ sudo dpkg --configure -a
    Setting up libssl1.0.0 (1.0.1-4ubuntu5.9) ...
    dpkg: dependency problems prevent configuration of linux-image-generic-pae:
     linux-image-generic-pae depends on linux-image-3.2.0-43-generic-pae; however:
      Package linux-image-3.2.0-43-generic-pae is not installed.
    dpkg: error processing linux-image-generic-pae (--configure):
     dependency problems - leaving unconfigured
    Setting up linux-libc-dev (3.2.0-43.68) ...
    Processing triggers for libc-bin ...
    ldconfig deferred processing now taking place
    Errors were encountered while processing:
     linux-image-generic-pae
    server@philo:/mnt/halftb/media/Videos$




edits-
additional:

    server@philo:~$ sudo apt-get install libssl1.0.0
    [sudo] password for server:
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    libssl1.0.0 is already the newest version.
    You might want to run 'apt-get -f install' to correct these:
    The following packages have unmet dependencies:
     linux-image-generic-pae : Depends: linux-image-3.2.0-43-generic-pae but it is not going to be installed
    E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by ajgreeny on 2013-05-29
Are you really still on 10.04 as your profile says?

If so, you need to update to a newer ubuntu version as 10.04 has lost support.  If you are on 12.04 libssl1.0.0 is in the repos, so should be installable.

---

### Post by wlraider70 on 2013-05-30
It is out dated. This is a 12.04 machine.
However 1004 is an LTS wouldn't it still be supported?

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]wlraider70; Hi !

Try this first ( I really do not expect a good result)
```
 sudo apt-get dist-upgrade
``` just to see if the package manager's smart mode will reolve that issue.
Then if no effect do:
[/COLOR]```
sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae
```
//
 > Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.


You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic and apt-cache show linux-headers-generic.


The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.
[INDENT=2]
all good now ??

[/INDENT]

---

### Post by wlraider70 on 2013-05-31
no luck...

I did however get a differnt message about /boot being full. 
I'm going to clean that now.

```

server@philo:/boot$ sudo dpkg --remove linux-generic-pae
[sudo] password for server:
dpkg: warning: there's no installed package matching linux-generic-pae
server@philo:/boot$ sudo dpkg --remove linux-generic-pae*
dpkg: warning: there's no installed package matching linux-generic-pae*
server@philo:/boot$ sudo apt-get install linux-generic-pae*
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'linux-generic-pae' for regex 'linux-generic-pae*'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.45.54) but 3.2.0.                                                                        
43.51 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.45.54) but it i                                                                        
s not going to be installed
 linux-image-generic-pae : Depends: linux-image-3.2.0-43-generic-pae but it is n                                                                        
ot going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s                                                                        
olution).

```

---

### Post by wlraider70 on 2013-05-31
Ok I seem to have gotten it. I had cleared out old files, but I guess it was enough to not give me a "low /boot folder space" but not enough to install the next kernel.


SO the question can I delete all this stuff? Do I have to use a special method of can i `rm` them?


THANKS



```

server@philo:~$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version                          Description
+++-================================-================================-================================================================================
un  linux-image                      <none>                           (no description available)
un  linux-image-3.0                  <none>                           (no description available)
un  linux-image-3.0.0-12-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-16-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-17-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-19-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-20-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-21-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-22-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-24-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-25-generic-pae <none>                           (no description available)
un  linux-image-3.0.0-26-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-32-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-33-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-34-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-35-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-36-generic-pae <none>                           (no description available)
un  linux-image-3.2.0-37-generic-pae <none>                           (no description available)
ii  linux-image-3.2.0-38-generic-pae 3.2.0-38.61                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic-pae 3.2.0-39.62                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae 3.2.0-40.64                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-41-generic-pae 3.2.0-41.66                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae 3.2.0-43.68                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-44-generic-pae 3.2.0-44.69                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-45-generic-pae 3.2.0-45.70                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae          3.2.0.45.54                      Generic Linux kernel image



server@philo:~$ cd /boot
server@philo:/boot$ ls
abi-3.2.0-38-generic-pae     config-3.2.0-41-generic-pae      initrd.img-3.2.0-44-generic-pae  System.map-3.2.0-44-generic-pae
abi-3.2.0-39-generic-pae     config-3.2.0-43-generic-pae      initrd.img-3.2.0-45-generic-pae  System.map-3.2.0-45-generic-pae
abi-3.2.0-40-generic-pae     config-3.2.0-44-generic-pae      lost+found                       vmlinuz-3.2.0-38-generic-pae
abi-3.2.0-41-generic-pae     config-3.2.0-45-generic-pae      memtest86+.bin                   vmlinuz-3.2.0-39-generic-pae
abi-3.2.0-43-generic-pae     grub                             memtest86+_multiboot.bin         vmlinuz-3.2.0-40-generic-pae
abi-3.2.0-44-generic-pae     initrd.img-3.2.0-38-generic-pae  System.map-3.2.0-38-generic-pae  vmlinuz-3.2.0-41-generic-pae
abi-3.2.0-45-generic-pae     initrd.img-3.2.0-39-generic-pae  System.map-3.2.0-39-generic-pae  vmlinuz-3.2.0-43-generic-pae
config-3.2.0-38-generic-pae  initrd.img-3.2.0-40-generic-pae  System.map-3.2.0-40-generic-pae  vmlinuz-3.2.0-44-generic-pae
config-3.2.0-39-generic-pae  initrd.img-3.2.0-41-generic-pae  System.map-3.2.0-41-generic-pae  vmlinuz-3.2.0-45-generic-pae
config-3.2.0-40-generic-pae  initrd.img-3.2.0-43-generic-pae  System.map-3.2.0-43-generic-pae
server@philo:/boot$

```

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]wlraider70;
 Yes, old kernels can and should be removed and that will go a long way toward resolution of your present crisis; house clean first.
[/COLOR]```

sudo apt-get autoclean 
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get purge linux-image-3.2.0-{38,39,40,41,43}-generic-pae
sudo apt-get purge linux-headers-3.2.0-{38,39,40,41,43}-generic-pae
sudo apt-get --purge autoremove ##The 'autoremove' based command simply removes the old kernel modules.

```
Keeping 2 "working" kernels - newest installed and 1 latter (45 and 44) and to be dealt with is the xxxx.45 version. 
Now lets look at where you stand:
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT=2]
we be look'n

[/INDENT]

---

