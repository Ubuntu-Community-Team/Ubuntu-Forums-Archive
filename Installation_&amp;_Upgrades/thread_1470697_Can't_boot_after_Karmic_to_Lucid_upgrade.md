---
title: "Can't boot after Karmic to Lucid upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by enigmajr on 2010-05-03
Hey everyone, quasi-n00b here so try and be patient with me. 

I made the mistake of trying to upgrade my Karmic (server) installation to Lucid earlier today, after which I've been unable to boot into my server. The server is on OVH, so I can't watch it boot, but I am able to access all of the data from the filesystems via rescue mode. I ran fsck and that came back clean. I also ran the boot info script, the results of which are below. 

I know my best bet is to backup what I can and do a fresh install, but I won't be able to back everything up so trying to get this working would certainly be more convenient. I'm sure I'm leaving out useful information, so let me know and I'll post it. Thanks everyone, and please help if you can! 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /etc/lilo.conf /boot/map

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda2 already mounted or sda2 busy

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1    20,480,000    20,480,000  83 Linux
/dev/sda2          20,480,001   975,718,400   955,238,400  83 Linux
/dev/sda3         975,718,401   976,768,064     1,049,664  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c26791b5-6c82-483b-8a66-d6dd6a61550b   ext3       /                             
/dev/sda2        efe5a1fc-e7b2-4b18-ba10-3622c4cb2b29   ext3       /home                         
/dev/sda3        7c0f4f74-c449-46f4-b939-b293ca901f14   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/hda: No such device or address
error: /dev/hdc: No such device or address
error: /dev/sdb: No such device or address
error: /dev/sdc: No such device or address
error: /dev/sdd: No such device or address

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)


=============================== sda1/etc/fstab: ===============================

# <sys.fichiers><pt de montage><type> <options>  <dump> <pass>
/dev/sda1	/	ext3	errors=remount-ro	0	1
/dev/sda2  	/home  	ext3  	defaults,usrquota,grpquota	0	1
/dev/sda3	swap	swap	defaults	0	0
proc		/proc	proc	defaults		0	0
sysfs		/sys	sysfs	defaults		0	0

============================= sda1/etc/lilo.conf: =============================

lba32
boot=/dev/sda
prompt
timeout=50
default=linux

# Enable large memory mode.
large-memory

image=/boot/bzImage-2.6.31.5-xxxx-grs-ipv4-64
        label="linux"
        root=/dev/sda1
        read-only
=======Devices which don't seem to have a corresponding hard drive==============

hda hdc sdb sdc sdd 
=============================== StdErr Messages: ===============================

  /proc/mounts: _get_sysfs_dir: fopen %s failed: No such file or directory
  /proc/devices: fopen failed: No such file or directory
  Failed to create lvm type filter
  Internal error: _vginfos list should be empty
  You have a memory leak (not released memory pool):
   [0x6b1450]
  You have a memory leak (not released memory pool):
   [0x6b1450]
mdadm: cannot open /proc/partitions
mdadm: No devices listed in conf file were found.

```

---

### Post by enigmajr on 2010-05-04
bump?

---

### Post by Tolaris on 2010-05-07
Is it really ext3, or is it ext4?  Can Lilo even boot ext4?  I'm afraid I can't help much with Lilo.  Haven't used it in 10 years.

---

### Post by Ammee on 2011-05-08
Hello!
Right now I'm facing identical problem. What makes it worse, I'm not "quasi-n00b", I'm just-n00b :-(
Also, it is Sunday, so I don't know if OVH will help me anyhow...

I've decided to upgrade 'cos my desktop upgrades were rather OK (I'm using Ubuntu on desktop since 6.10). But now my websites are offline and it's a real tragedy for me ;-(
I've googled it a lot, but could not find anything helpful. I'm willing to Paypal some USD for help (if needed) but I'm not really rich.

I would be very, very, very thankful for any help!

---

### Post by Rubi1200 on 2011-05-08
> **Ammee said:**
> Hello!
Right now I'm facing identical problem. What makes it worse, I'm not "quasi-n00b", I'm just-n00b :-(
Also, it is Sunday, so I don't know if OVH will help me anyhow...

I've decided to upgrade 'cos my desktop upgrades were rather OK (I'm using Ubuntu on desktop since 6.10). But now my websites are offline and it's a real tragedy for me ;-(
I've googled it a lot, but could not find anything helpful. I'm willing to Paypal some USD for help (if needed) but I'm not really rich.

I would be very, very, very thankful for any help!

Hi and welcome to the forums :-)

I think it would be better if you started your own thread and post relevant information such as the boot info script.

As you can see, this is a rather old thread and I suspect the original poster is not coming back.

You can click on the Report Abuse function next to your post and ask the staff to move it to it's own thread.

---

### Post by Ammee on 2011-05-08
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

I think it would be better if you started your own thread and post relevant information such as the boot info script.

As you can see, this is a rather old thread and I suspect the original poster is not coming back.

You can click on the Report Abuse function next to your post and ask the staff to move it to it's own thread.
Thanks for the answer and the advice... Fortunately, in the meantime I have found:
[http://travaux.ovh.net/?do=details&id=4154](http://travaux.ovh.net/?do=details&id=4154)
1. In the rescue mode:
```
echo -e "dev\t\t/dev\tdevtmpfs\trw\t0\t0" >> /etc/fstab
```
2. In the manager:
- Pick the new kernel via Netboot
- Reboot

---

