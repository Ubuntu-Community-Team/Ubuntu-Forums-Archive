---
title: "device-mapper: resume ioctl on (252:0) failed: Invalid argument"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by jryburn on 2017-11-05
I am in the process of moving a Ubuntu 16.04 VM from one provider to another. With the old provider, I did not have access to the host OS but they made a raw disk image for me that I moved to the new provider. At the new provider, I have a host OS of Ubuntu 16.04 with KVM running on top. I am attempting to boot the disk image as a VM but it dies when trying to load the root filesystem.

```
Begin: Running /scripts/local-block ... mdadm: CREATE group disk not found                                 
mdadm: No arrays found in config file or automatically                                                     
  lvmetad is not active yet, using direct activation during sysinit                                        
[   55.221230] device-mapper: table: 252:0: vda5 too small for target: start=2048, len=594567168, dev_size=354789424                                                                                                  
  device-mapper: resume ioctl on (252:0) failed: Invalid argument                                          
  Unable to resume dev--jryburn--vg-root (252:0)     
done.                                                
done.                                                
Gave up waiting for root device.  Common problems:   
 - Boot args (cat /proc/cmdline)                     
   - Check rootdelay= (did the system wait long enough?)                                                   
   - Check root= (did the system wait for the right device?)                                               
 - Missing modules (cat /proc/modules; ls /dev)      
ALERT!  /dev/mapper/dev--jryburn--vg-root does not exist.  Dropping to a shell!                            
[   55.249256] hidraw: raw HID events driver (C) Jiri Kosina                                               
[   55.256077] usbcore: registered new interface driver usbhid                                             
[   55.257181] usbhid: USB HID core driver           


BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)                                           
Enter 'help' for a list of built-in commands.        

(initramfs)                                          
```

The root filesystem is a using LVM. Some outputs from the existing (running) VM on the old provider:

 ```
jryburn@dev-jryburn:/var/log$ sudo fdisk -lu                                                                                                                                                                         
[sudo] password for jryburn:                         
Disk /dev/vda: 300 GiB, 322122547200 bytes, 629145600 sectors                                             
Units: sectors of 1 * 512 = 512 bytes                
Sector size (logical/physical): 512 bytes / 512 bytes                                                     
I/O size (minimum/optimal): 512 bytes / 512 bytes    
Disklabel type: dos                                  
Disk identifier: 0xdf201a4e                          

Device     Boot   Start       End   Sectors   Size Id Type                                                
/dev/vda1  *       2048    999423    997376   487M 83 Linux                                               
/dev/vda2       1001470 629143551 628142082 299.5G  5 Extended                                            
/dev/vda5       1001472 629143551 628142080 299.5G 8e Linux LVM                                           




Disk /dev/mapper/dev--jryburn--vg-root: 283.5 GiB, 304418390016 bytes, 594567168 sectors                  
Units: sectors of 1 * 512 = 512 bytes                
Sector size (logical/physical): 512 bytes / 512 bytes                                                     
I/O size (minimum/optimal): 512 bytes / 512 bytes    


Disk /dev/mapper/dev--jryburn--vg-swap_1: 16 GiB, 17175674880 bytes, 33546240 sectors                     
Units: sectors of 1 * 512 = 512 bytes                
Sector size (logical/physical): 512 bytes / 512 bytes                                                     
I/O size (minimum/optimal): 512 bytes / 512 bytes    

```

```

jryburn@dev-jryburn:/var/log$ sudo pvscan
  PV /dev/vda5   VG dev-jryburn-vg   lvm2 [299.52 GiB / 12.00 MiB free]
  Total: 1 [299.52 GiB] / in use: 1 [299.52 GiB] / in no VG: 0 [0   ]

```
```

jryburn@dev-jryburn:/var/log$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "dev-jryburn-vg" using metadata type lvm2

```
```

jryburn@dev-jryburn:/var/log$ sudo lvscan
  ACTIVE            '/dev/dev-jryburn-vg/root' [283.51 GiB] inherit
  ACTIVE            '/dev/dev-jryburn-vg/swap_1' [16.00 GiB] inherit

```

It would appear the VM is not trying to load the root filesystem with LVM defined first. However, I am not sure how to change that. I can mount the /boot filesystem in the underlying host OS on the new provider and make changes to grub.cfg if needed. I have not been able to figure out how to mount the LVM filesystem of this VM in the underlying host OS but not sure how helpful that would be anyway.

Any pointers would be greatly appreciated.

---

