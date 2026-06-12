---
title: "Problem with installing NVidia drivers"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by prdatur on 2007-11-12
Hello everybody, have some little problems

I installed ubuntu yesterday ( have some linux knowledge from debian and ubuntu before but not very much :) )

so after i tested the nvidia-glx-new driver but they didnt worked well.
i decided to uninstall this drivers, so that what i did before
uninstalling:

nvidia-glx-new


installed:

linux-image-2.6.20-15-generic , now i use 2.6.20-"16" couse of an update
linux-image-2.6.20-16-generic
linux-image-generic

linux-headers-2.6.20-15-generic , now i use 2.6.20-"16" couse of an update
linux-headers-2.6.20-16-generic
linux-headers-generic

libc
gcc
gcc-3.3-base
gcc-3.4
gcc-3.4-base
gcc-4.1
gcc-4.1-base

make 
make install 

nvidia drivers from nvidia homepage ( latest drivers )
didnt worked because of some trouble with symbolic links which was not found ( agp thinks  but i have pciExpress card so i think this was the error why it was not found )

tried some thinks from compiz help:
checking modprobe agpgart was loaded,
i comment out this lines and i had it then that modprobe --show-depends nvidia showed

insmod .... i2c.core.ko
insmod .... nvidia.ko

but then always telled me that agp was not found
i think that nvidia found the restricted drivers and dont did something with the driver self so agp was still enabled,

if i now want to install nvidia driver again it says 

-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s).
       
       Please see the log entries 'Kernel module load error' and 'Kernel
       messages' at the end of the file '/var/log/nvidia-installer.log' for
       more information.
-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 Unknown symbol in module
-> Kernel messages:
   [   46.969328] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3700+
   processors (version 2.00.00)
   [   46.977458] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
   [   53.671150] ppdev: user-space parallel port driver
   [   54.190728] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
   [   54.190732] apm: overridden by ACPI.
   [   54.331520] Bluetooth: Core ver 2.11
   [   54.331561] NET: Registered protocol family 31
   [   54.331562] Bluetooth: HCI device and connection manager initialized
   [   54.331565] Bluetooth: HCI socket layer initialized
   [   54.361031] Bluetooth: L2CAP ver 2.8
   [   54.361034] Bluetooth: L2CAP socket layer initialized
   [   54.456669] Bluetooth: RFCOMM socket layer initialized
   [   54.456679] Bluetooth: RFCOMM TTY layer initialized
   [   54.456680] Bluetooth: RFCOMM ver 1.8
   [   67.636043] eth0: no IPv6 routers present
   [  113.135638] nvidia: module license 'NVIDIA' taints kernel.
   [  113.135912] nvidia: Unknown symbol agp_bind_memory
   [  113.135973] nvidia: Unknown symbol agp_enable
   [  113.136069] nvidia: Unknown symbol agp_backend_acquire
   [  113.136108] nvidia: Unknown symbol agp_bridges
   [  113.136207] nvidia: Unknown symbol agp_free_memory
   [  113.136272] nvidia: Unknown symbol agp_allocate_memory
   [  113.136306] nvidia: Unknown symbol agp_unbind_memory
   [  113.136430] nvidia: Unknown symbol agp_copy_info
   [  113.136491] nvidia: Unknown symbol agp_backend_release
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

dont know what u need to know also 

hope someone can help me

---

### Post by Triptol on 2007-11-13
If I understand it correctly the system still sees your self compiled nvidia.ko file. 

What you could try is to go to that source directory and do an ```
make uninstall
```

The other option you would have is:```
aptitude purge nvidia-glx-new
aptitude install nvidia-glx
```

This would install the older nvidia-glx, you could also install the nvidia-glx-new one again. This would normally remove old nvidia stuff and put back the stuff from the Ubuntu repositories.

---

