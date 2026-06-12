---
title: "kernel update disk space error"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by aaronp on 2013-03-30
Hi guys,

I've recently been getting an error when kernel updates happen saying I'm out of disk space. 
I had less than 1GB last time this happened, purged nearly all the old kernels and that seemed to fix the problem. Now, with more than 1GB of disk space I am receiving the same error. This time, I decided to fix it properly and moved /var to another partition which now gives me 2.5GB of free space. This should be plenty!
But, when running sudo apt-get -f install I am still receiving the same error. I can't help but think the error message is wrong and something else is at play here but I can't find any answers that point to anything other than a disk space issue. Any ideas?

```


aaron@apbh:/$sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libunity6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-headers-3.2.0-39-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-39 linux-headers-3.2.0-39-generic linux-headers-3.2.0-39-generic-pae
0 upgraded, 3 newly installed, 0 to remove and 50 not upgraded.
3 not fully installed or removed.
Need to get 0 B/13.7 MB of archives.
After this operation, 78.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 589226 files and directories currently installed.)
Unpacking linux-headers-3.2.0-39 (from .../linux-headers-3.2.0-39_3.2.0-39.62_all.deb) ...
Unpacking linux-headers-3.2.0-39-generic (from .../linux-headers-3.2.0-39-generic_3.2.0-39.62_i386.deb) ...
Unpacking linux-headers-3.2.0-39-generic-pae (from .../linux-headers-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-39-generic-pae/include/config/usb/storage/isd200.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-39-generic-pae/include/config/usb/storage/isd200.h'): No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-39-generic-pae_3.2.0-39.62_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by plucky on 2013-03-30
Check your /boot partition as that is where new kernel installs are placed.

You can try removing old kernel/headers to free up space in the /boot partition.

Post output for ```
df -h
```

Good Luck

---

### Post by aaronp on 2013-03-30
Thanks plucky. 
My /boot is not in a separate partition.
Here is the output of df -h:
```

aaron@apbh:/$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        12G  8.8G  2.3G  80% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  1.5M  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  2.5M 1005M   1% /run/shm
/dev/sdb1        74G   67G  4.2G  95% /media/store
/dev/sda3        78G   72G  2.3G  97% /home
/dev/sda4        56G   13G   41G  25% /media/data
/dev/sdc1       459G  218G  218G  50% /media/backups

```

---

### Post by matt_symes on 2013-03-30
Hi

Plenty of space for a kernel there. Are you out of inodes ?

Please post the output of

```
df -i
```

Kind regards

---

### Post by aaronp on 2013-03-30
Thanks mkatt_symes. It looks like you're correct. Here's the output:

```

aaron@apbh:/boot$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        768544 765860     2684  100% /
udev             214837    558   214279    1% /dev
tmpfs            218472    530   217942    1% /run
none             218472      5   218467    1% /run/lock
none             218472     13   218459    1% /run/shm
/dev/sdb1       4890624  56896  4833728    2% /media/store
/dev/sda3       5140000 302225  4837775    6% /home
/dev/sda4       3686400  19332  3667068    1% /media/data
/dev/sdc1      30531584  48363 30483221    1% /media/backups


```

---

### Post by matt_symes on 2013-03-30
Hi

> /dev/sda1        **768544** **765860**     2684  100% /

That's pretty full. All inodes used up, almost.

Can we take a look at the old kernels and kernel headers you have installed please.

Please post the output of..

```
dpkg -l | egrep "linux-image|linux-headers"
```

Kind regards

---

### Post by aaronp on 2013-03-30
Yep, thank you. Here's the output:

```

aaron@apbh:/$ sudo dpkg -l | egrep "linux-image|linux-headers"
ii  linux-headers-3.2.0-30                 3.2.0-30.48                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic         3.2.0-30.48                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-30-generic-pae     3.2.0-30.48                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31                 3.2.0-31.50                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic         3.2.0-31.50                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-31-generic-pae     3.2.0-31.50                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32                 3.2.0-32.51                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic         3.2.0-32.51                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-32-generic-pae     3.2.0-32.51                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33                 3.2.0-33.52                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic         3.2.0-33.52                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-33-generic-pae     3.2.0-33.52                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34                 3.2.0-34.53                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic         3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-34-generic-pae     3.2.0-34.53                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35                 3.2.0-35.55                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic         3.2.0-35.55                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-35-generic-pae     3.2.0-35.55                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                 3.2.0-36.57                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic         3.2.0-36.57                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36-generic-pae     3.2.0-36.57                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                 3.2.0-37.58                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic         3.2.0-37.58                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37-generic-pae     3.2.0-37.58                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                 3.2.0-38.61                                         Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic         3.2.0-38.61                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38-generic-pae     3.2.0-38.61                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-3.2.0-39                 3.2.0-39.62                                         Header files related to Linux kernel version 3.2.0
iU  linux-headers-3.2.0-39-generic         3.2.0-39.62                                         Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic                  3.2.0.39.47                                         Generic Linux kernel headers
iU  linux-headers-generic-pae              3.2.0.39.47                                         Generic Linux kernel headers
ii  linux-image-3.2.0-36-generic           3.2.0-36.57                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-37-generic           3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-38-generic           3.2.0-38.61                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-39-generic           3.2.0-39.62                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic                    3.2.0.39.47                                         Generic Linux kernel image


```

---

### Post by matt_symes on 2013-03-30
Hi

Let's get rid of some of those old kernels and kernel header files. 

That will free up plenty of inodes.

From the terminal (copy and paste into it)

```
sudo dpkg -P linux-headers-3.2.0-{30,31,32,33,34,35,36,37}-generic{,-pae}
```

```
sudo dpkg -P linux-image-3.2.0-{36,37}-generic
```

```
sudo apt-get -f install
```

Then post back the output of

```
df -i
```

Kind regards

---

### Post by aaronp on 2013-03-30
Thanks so much, that solved the problem. (apt-get -f install ran to completion) 

Here's the output of df -i:
```

aaron@apbh:/$ sudo df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1        768544 630735   137809   83% /
udev             214837    559   214278    1% /dev
tmpfs            218472    531   217941    1% /run
none             218472      5   218467    1% /run/lock
none             218472     13   218459    1% /run/shm
/dev/sdb1       4890624  56896  4833728    2% /media/store
/dev/sda3       5140000 302227  4837773    6% /home
/dev/sda4       3686400  19307  3667093    1% /media/data
/dev/sdc1      30531584  48363 30483221    1% /media/backups

```

I'm still really worried about that inode usage. It seems extremely high given my understanding is it will usually be much lower. 
I'm sure it will last me a while now but is there anything preventative I can do (short of re-installing the root partition) to help it?

---

### Post by matt_symes on 2013-03-30
Hi
> 
I'm still really worried about that inode usage. It seems extremely high  given my understanding is it will usually be much lower. 
I'm sure it will last me a while now but is there anything preventative I  can do (short of re-installing the root partition) to help it?

That did free up ~ 13000 inodes so that is good.

Unfortunately, with an extX filing system you cannot change the number of inodes after formatting unlike some other filing systems.

Your best to is to keep an eye on the root partition and uninstall things like the kernel headers and kernels when no longer needed.

The kernel headers packages install many small files into your PC and can really bite into the number of inodes on your filing system.

Do you have any applications that are creating many small files on your system ?

Another option is to move any files you can from your root partition to a different partition.

Incidentally, you have a problem with your kernel headers for .39. 

They have not installed correctly hence the iU next to the name from the output of dpkg.

Kind regards

---

