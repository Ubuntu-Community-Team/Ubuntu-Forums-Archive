---
title: "RAID 5 access - partition creation problem"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by nate8 on 2014-03-29
Hello All,

Im not new to Linux but Im not advanced either.

I've installed a fairly vanuilla Ubuntu server 13.04 with SSHD and ubuntu-desktop added in only.

The hardware Im running is:

Asus KGPE-D16 MB
Dual AMD 12-core CPU's
64 GB RAM (4 sticks - 16GB each - matches the HCL tested and runs clean)
4 Seagate 1.5 TB 7200 RPM HDD's
1 Samsung 500GB SSD

Ive installed Ubuntu server 13.04 to the SSD and I want to use the SSD for server OS and critical applications. The ASUS MB has an onboard Promise RAID array chip set but the OS apparently has detected the other disks separately from the RAID array, meaning it doesnt see the RAID array as one drive rather it sees each disk thats part of the array.

I executed the following command
 
```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

to see what Ubuntu thinks it has mounted and this it what it returns:

```
NAME                            FSTYPE                     SIZE MOUNTPOINT LABEL
sda                             promise_fasttrack_raid_m   1.4T            
sdb                             promise_fasttrack_raid_m   1.4T            
â”œâ”€sdb1                                                     522G            
â”œâ”€sdb2                                                     522G            
â”œâ”€sdb3                                                     522G            
â””â”€sdb4                                                     522G            
sdc                             promise_fasttrack_raid_m   1.4T            
sdd                             promise_fasttrack_raid_m   1.4T            
â”œâ”€sdd1                                                     522G            
â”œâ”€sdd2                                                     522G            
â”œâ”€sdd3                                                     522G            
â””â”€sdd4                                                     522G            
sde                                                      465.8G            
â”œâ”€sde1                          ext2                       243M /boot      
â”œâ”€sde2                                                       1K            
â””â”€sde5                          LVM2_member              465.5G            
  â”œâ”€andromeda--vg-root (dm-0)   ext4                     369.6G /          
  â””â”€andromeda--vg-swap_1 (dm-1) swap                      95.9G [SWAP]     
sr0                                                       1024M
```

So...I would like to continue to use the ASUS promise RAID array chipset and make Ubuntu see the 4 x 1.5 TB HDD's as one logical disk and create one partition for it to use (as per RAID 5 specs I should see something close to one logical disk with ~4.5 TB of disk space to use).

Any ideas would be greatly appreciated!

Thanks!

---

### Post by TheFu on 2014-03-29
First - for critical and important applications, you shouldn't use an OS that is NOT supported.
12.04, 13.10 are the OS versions that should be used today. In a month, 14.04 LTS should be used. It will be supported for 5 yrs, like 12.04 is (until 2017). 13.10 support ends in a few months, so if you choose to install that release, be prepared to either reinstall 14.04 or update to it shortly.

Sorry - didn't read the rest of the post carefully.

I do have an old Promise RAID card - it is not useful as RAID, just as JBOD controller. The only Linux drivers they ever released for it were out of date binary blobs for a 2.6 kernel that was 2 yrs old when I bought it. Anyway I wasn't thrilled with their claimed "linux support."

These days I'd only use RAID hardware that has support built into the Linux kernel or comes with source code that I can build drivers with.

---

### Post by nate8 on 2014-04-03
I appreciate the response TheFU! Since this is a new server I will upgrade it to 14.04 as per your suggestion. With regards to the promise RAID chip set. Is there anyway to make it work or do you suggest I do a soft RAID from linux (any suggestions would be appreciated!)?

I would have responded sooner but I havent navigated Ubuntu forums much combined with business from work has made my attention delayed. This is very important to me and again I appreciate anything you would suggest.

Thanks!

---

### Post by TheFu on 2014-04-03
> **nate8 said:**
> I appreciate the response TheFU! Since this is a new server I will upgrade it to 14.04 as per your suggestion. With regards to the promise RAID chip set. Is there anyway to make it work or do you suggest I do a soft RAID from linux (any suggestions would be appreciated!)?

I would have responded sooner but I havent navigated Ubuntu forums much combined with business from work has made my attention delayed. This is very important to me and again I appreciate anything you would suggest.

Thanks!

I didn't do **any** research on your MB or RAID. Sorry.
MB RAID usually sucks.  Get an LSI SAS controller with kernel support if you want HW-RAID performance. Those are about $300-$400.

I use software RAID. It is much more flexible and provides *_good enough performance_* for the current needs. Not being tied to specific hardware is nice. I've migrated that external array across 3 different motherboards, NO ISSUES. If you use MB-RAID, that won't be possible.

You can set options here to send an email when a response happens. Filter it for later, if you like. I do.

---

### Post by nate8 on 2014-04-04
> **TheFu said:**
> I didn't do **any** research on your MB or RAID. Sorry.
MB RAID usually sucks.  Get an LSI SAS controller with kernel support if you want HW-RAID performance. Those are about $300-$400.

I use software RAID. It is much more flexible and provides *_good enough performance_* for the current needs. Not being tied to specific hardware is nice. I've migrated that external array across 3 different motherboards, NO ISSUES. If you use MB-RAID, that won't be possible.

You can set options here to send an email when a response happens. Filter it for later, if you like. I do.

Well, that is something I can do as well. Would an HP/LSI SMART Array with an HP part number of 405831-001 do the trick? Let me know when you can and Thanks!

---

### Post by TheFu on 2014-04-04
Don't know. Haven't purchased anything from HP in about 7 yrs.   Disk array stuff came off an approved list from the storage group - mostly we bought 4Gb fibre HBAs to connect to a SAN - cisco and brocade switches to EMC storage.

Even in a small business - a SAN is nice.  A 1G ethernet SAN opens up all sorts of capabilities for smaller networks. I've deployed a $4K SAN box (not made anymore).  I've read about folks building their own SAN server (iSCSI, AoE) for cheap on the FreeNAS forums. Perhaps looking there for specific hardware would be helpful? It all depends on the level of performance you need.

---

### Post by nate8 on 2014-04-04
> **TheFu said:**
> Don't know. Haven't purchased anything from HP in about 7 yrs.   Disk array stuff came off an approved list from the storage group - mostly we bought 4Gb fibre HBAs to connect to a SAN - cisco and brocade switches to EMC storage.

Even in a small business - a SAN is nice.  A 1G ethernet SAN opens up all sorts of capabilities for smaller networks. I've deployed a $4K SAN box (not made anymore).  I've read about folks building their own SAN server (iSCSI, AoE) for cheap on the FreeNAS forums. Perhaps looking there for specific hardware would be helpful? It all depends on the level of performance you need.

Ok. Well once its installed will 14.04 auto detect the controller or will I have to manually install drivers and the such?

---

### Post by nate8 on 2014-04-05
So I went to ASUS' website and found their driver for Promise chipset. Im not sure how to install it. Any suggestions would be appreciated as Ive googled how to install linux drivers and nothing really explained how to do so.

The driver is in a compressed file called "UBUNSERVER-10.4.1-X86_32.tgz" which when extracted contains "UBUNSERVER-10.4.1-X86_64.tar" and when that is extracted it contains the following files:
ahci.ko
ahci_generic.ko
install
readme
ubuntu.pre
update.post
update.pre

Thanks!

---

### Post by nate8 on 2014-04-05
This is what the install file says:

```
#!/bin/sh#
# Installation script for Ubuntu Linux
# Promise Technology, Inc (C) 2010


## Determine Ubuntu 10.04 kernel version


DRVNAME=ahci
RELEASE=$(ls /lib/modules)


tmp1=`uname -r |grep pae`
tmp2=`uname -r |grep server`


if [ -n "$tmp1" ] || [ -n "$tmp2" ]; then
    ## update modules.dep
    mv /lib/modules/$RELEASE/kernel/drivers/ata/ahci.ko /lib/modules/$RELEASE/kernel/drivers/ata/ahci.ko.bak
    cp -ap $DRVNAME.ko /lib/modules/$RELEASE/kernel/drivers/scsi/
    depmod -a $RELEASE


    ## make new initrd.img
    cp -ap /boot/initrd.img-$RELEASE /boot/initrd.img-$RELEASE.bak
    mkinitramfs -o /boot/initrd.img-$RELEASE $RELEASE
else  
    ## update modules.dep
        mv /lib/modules/$RELEASE/kernel/drivers/ata/ahci.ko /lib/modules/$RELEASE/kernel/drivers/ata/ahci.ko.bak
        cp -ap ahci_generic.ko /lib/modules/$RELEASE/kernel/drivers/scsi/$DRVNAME.ko
        depmod -a $RELEASE


        ## make new initrd.img
        cp -ap /boot/initrd.img-$RELEASE /boot/initrd.img-$RELEASE.bak
        mkinitramfs -o /boot/initrd.img-$RELEASE $RELEASE
fi


echo ""
echo "setup is complete"
echo "-------------------------------"
echo "Promise Technology, Inc (C)2010"
echo ""


exit
```

I execute it with sudo sh install. Here's what I get:

```
mv: target â€˜3.8.0-31-generic/kernel/drivers/ata/ahci.ko.bakâ€™ is not a directory
cp: target â€˜3.8.0-31-generic/kernel/drivers/scsi/ahci.koâ€™ is not a directory
cp: target â€˜3.8.0-31-generic.bakâ€™ is not a directory


setup is complete
-------------------------------
Promise Technology, Inc (C)2010
```

but when I do "sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL"
It still returns the same thing as above...

Any suggestions on how to make the drivre work?

Thanks!

---

