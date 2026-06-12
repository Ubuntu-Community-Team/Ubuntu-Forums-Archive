---
title: "About GRUB"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by satimis on 2010-02-28
Hi folks,

On this PC there are 2 HDs

HD-1, IDE connection - Windows Vista 32bit
HD-2, SATA connection - Fedora 12 64bit (previously)

They were controlled by BIOS for start-up without problem.  Just wiped out Fedora and installed Ubuntu 9.10 64bit.  During installing GRUB I saved it on Master, IIRC.  Now Ubuntu and Vista startup are controlled by boot loader.  I have to start Ubuntu first and on kernel selection select (loader)(on/dev/sdb1).  Then Vista starts.  It works.

How can I restore to its original setup?  Their booting is controlled by BIOS.  TIA


B.R.
satimis

---

### Post by darkod on 2010-02-28
And what happens when you try to boot from the other disk? Which bootloader is shown?

Although, I have no idea why you prefer selecting a boot device in BIOS. It works fine as it is. If you go into BIOS, make changes and save them, that's as if you're restarting the computer, it restarts again.
So any change in boot disc is restarting it. Just selecting from grub menu is much more efficient, both for you and your computer.

---

### Post by satimis on 2010-02-28
> **darkod said:**
> And what happens when you try to boot from the other disk? Which bootloader is shown?

If on GRUB boot loader selecting Window Vista (loader)(on /dev/sdb1) it starts Vista

> 
Although, I have no idea why you prefer selecting a boot device in BIOS. It works fine as it is. If you go into BIOS, make changes and save them, that's as if you're restarting the computer, it restarts again.
So any change in boot disc is restarting it. Just selecting from grub menu is much more efficient, both for you and your computer.

That is a good question.  If I wipe out Ubuntu then Vista can't boot.  I made following test.  Pulling out the power cable of HD-2 (SATA) Ubuntu 9.10 and selecting on BIOS boot sequence, HD-1 (Vista), Vista can't boot, only GRUB> displayed on a black screen.


$ sudo fdisk -l```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003a4bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      118706   953505913+  83  Linux
/dev/sda2          118707      121601    23254087+   5  Extended
/dev/sda5          118707      121601    23254056   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0883bef2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4867    39086080    7  HPFS/NTFS

```


B.R.
satimis

---

### Post by darkod on 2010-02-28
After you wipe ubuntu you can easily restore vista bootloader. But I understand your point. You want grub2 on /dev/sda and windows bootloader on /dev/sdb.

Boot into ubuntu. Once it's booted up, execute:

sudo grub-install /dev/sda

That will make sure grub2 is installed on /dev/sda. Then to install generic mbr on /dev/sdb from ubuntu:

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

Ignore the warnings it will show. That will install generic mbr on /dev/sdb.

After all this, if you boot from the 1TB disk you should see the grub menu with ubuntu and vista choices. If you boot from the 40GB disk, it should load vista directly.

---

### Post by satimis on 2010-02-28
> **darkod said:**
> After you wipe ubuntu you can easily restore vista bootloader. But I understand your point. You want grub2 on /dev/sda and windows bootloader on /dev/sdb.

Boot into ubuntu. Once it's booted up, execute:

sudo grub-install /dev/sda

That will make sure grub2 is installed on /dev/sda. Then to install generic mbr on /dev/sdb from ubuntu:

sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr

Ignore the warnings it will show. That will install generic mbr on /dev/sdb.

After all this, if you boot from the 1TB disk you should see the grub menu with ubuntu and vista choices. If you boot from the 40GB disk, it should load vista directly.

Hi darkod,


Performed following steps;


$ sudo grub-install /dev/sda```

Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

```


$ sudo apt-get install lilo```

......
LILO configuration                                                              
It seems to be your first LILO installation. It is absolutely necessary to run liloconfig(8) when you complete this process and execute /sbin/lilo after this. 

LILO won't work if you don't do this.  
<OK>  

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

```


$ sudo /usr/sbin/liloconfig ```

WARNING!       
                                                                   
Your /etc/fstab configuration file gives device UUID=4ff364c6-c510-4f46-93df-902590749a76 as the root filesystem device. This   doesn't look to me like an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple configuration program does not handle.

<Ok>    

```

$ sudo /sbin/lilo ```

Fatal: Cannot open: /etc/lilo.conf

```


$ sudo lilo -M /etc/sdb mbr```

Fatal: Cannot open /etc/sdb: No such file or directory

```


What shall I do?  I'll reboot.  If fails to start I'll reply on another PC.


Edit: (Continue)

Reboot:-
BIOS Boot sequency
HD-2 (SATA) Ubuntu
HD-1 (IDE) Vista

I can boot either Ubuntu or Vista

BIOS Boot sequency
HD-1 (IDE) Vista
HD-2 (SATA) Ubuntu

Fail to boot Vista
```

GRUB loading .....
ERROR 15
```


B.R.
satimis

---

### Post by darkod on 2010-02-28
> **satimis said:**
> 
$ sudo lilo -M /etc/sdb mbr```

Fatal: Cannot open /etc/sdb: No such file or directory

```


sudo lilo -M /dev/sdb mbr (not /etc/sdb, that's why it reported the error and it didn't work booting from the vista disk first).

---

### Post by satimis on 2010-02-28
> **darkod said:**
> sudo lilo -M /dev/sdb mbr (not /etc/sdb, that's why it reported the error and it didn't work booting from the vista disk first).

Hi darkod,

Ah, sorry I see.

$ sudo lilo -M /dev/sdb```

Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.

```

Reboot.

It works now.  Vista boots on its own disk.  Thanks

Further questions;

1)
Why there are so many warnings?  If without your advice.  I won't proceed further.

2)
This is NOT the first time for me having a second HD on the PC with running Windows.  Previously on installing Linux OS on another HD I would disconnect the power cable to Windows HD.  This time I forgot to do this step.  Where should I save the grub, the boot loader, if having the power cable to Windows HD connected?  Thanks

B.R.
satimis

---

### Post by darkod on 2010-02-28
> **satimis said:**
> Hi darkod,

Ah, sorry I see.

$ sudo lilo -M /dev/sdb```

Backup copy of /dev/sdb in /boot/boot.0810
The Master Boot Record of  /dev/sdb  has been updated.

```Reboot.

It works now.  Vista boots on its own disk.  Thanks

Further questions;

1)
Why there are so many warnings?  If without your advice.  I won't proceed further.

2)
This is NOT the first time for me having a second HD on the PC with running Windows.  Previously on installing Linux OS on another HD I would disconnect the power cable to Windows HD.  This time I forgot to do this step.  Where should I save the grub, the boot loader, if having the power cable to Windows HD connected?  Thanks

B.R.
satimis

The warnings are because you are not using fully the lilo bootloader, and the system can see that. You want to keep using grub, but just to use one command from lilo to write generic mbr on the hdd.

The system would have worked just fine even without these operations, as you saw yourself. You were able to use both ubuntu and vista.
However, if you want to keep the windows bootloader on the windows disk, and install the grub bootloader on the ubuntu disk, in the last screen of the ubuntu installer before clicking Install click on Advanced and tell it to install the bootloader to the ubuntu disk. For example, if the ubuntu hdd was called /dev/sdb in step 4 when selecting where to install, then in advanced options tell the bootloader to install on /dev/sdb (without a number, just /dev/sdb). That's how you control where grub goes.

---

### Post by satimis on 2010-02-28
> **darkod said:**
> The warnings are because you are not using fully the lilo bootloader, and the system can see that. You want to keep using grub, but just to use one command from lilo to write generic mbr on the hdd.

The system would have worked just fine even without these operations, as you saw yourself. You were able to use both ubuntu and vista.
However, if you want to keep the windows bootloader on the windows disk, and install the grub bootloader on the ubuntu disk, in the last screen of the ubuntu installer before clicking Install click on Advanced and tell it to install the bootloader to the ubuntu disk. For example, if the ubuntu hdd was called /dev/sdb in step 4 when selecting where to install, then in advanced options tell the bootloader to install on /dev/sdb (without a number, just /dev/sdb). That's how you control where grub goes.

Your advice noted.  Thanks

B.R.
satimis

---

