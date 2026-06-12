---
title: "Input/output error reading sda during installation"
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by jander2 on 2015-01-09
Hello everyone, 


Please, I need help with this issue. I think I checked all posts about similar problems and I still couldn’t solve it.
 
[B]Background:
[/B]I rescued an unused old CPU tower from 2007 with a core 2 quad, 4 gb ddr2 ram and a more modern (around 2011) discrete graphic card.  I recently cancelled the TV subscription and want to use this PC as media center connected to the TV + network storage.
The CPU was still working with dual boot Windows 7 64bit/Ubuntu 11 installed in a noisy and slowly 320gb hdd.
 
[B]Problem:
[/B]To make the PC a bit faster and smoother I bought a SSD drive (Kingston SSDnowv300 120gb) to use as boot device for Ubuntu. However, I am unable to install Ubuntu on it. The Ubuntu 14.04.1 desktop 64bit DVD boots and loads the installer (very slowly, I have to say) but when the real installation starts, it gives me the error: input/output error reading dev/sda. If a press ignore several times I get also fsync error on sda and return me to the the window where you choose where to install Ubuntu.
 
**Things I tried:** 
[LIST]
[*]Erase disk and install option on Ubuntu installer gives the error. 
[*]If I choose manual partition it shows me the drive but without any partition table. I create a partition table from that window and manually create the partitions, but when it starts the installation I get the same error. 
[*]Windows Diskpart clean and convert to MBR also do not work. I assume this old motherboard has no EFI support. In fact the Ubuntu DVD boots in BIOS mode ([No EFI screen asking what to do]("https://www.google.nl/search?q=efi+ubuntu&espv=2&biw=1680&bih=928&source=lnms&tbm=isch&sa=X&ei=AiewVNqBOMG-UuOLgqgH&sqi=2&ved=0CAYQ_AUoAQ&dpr=1#imgdii=_&imgrc=ZnEyqeb_QGvzTM%253A%3Bu7spT0v1LRj1GM%3Bhttp%253A%252F%252Fpix.toile-libre.org%252Fupload%252Foriginal%252F1347445084.png%3Bhttp%253A%252F%252Faskubuntu.com%252Fquestions%252F91484%252Fhow-to-boot-ubuntu-from-efi-uefi%3B300%3B224") ). Anyway, I also tried covert to GPT and got the same result. 
[*]Gparted, Disks and other many disk utilities using the live CD session also gives the same error and/or similar ones. 
[*]Burn another DVD at low speed also didn’t help. MD5sum was verified for the iso. Linux Mint 17 DVD also gives the same error. 
[*]_Windows 7 64 can be installed smoothly_ and works very nice (so the drive and the SATA cable seem OK) 
[*]_Connect the SSD to my laptop_ and install Ubuntu _worked_ perfectly (drive is OK and can run linux) (in this case it was installed in EFI mode with GPT partition tables because it is a modern laptop) 
[*]In one post I saw that changing the SSD to AHCI mode in the BIOS solved a similar issue. But I don’t have that option in the BIOS, so I guess is in IDE mode. Also I don’t see many options to play around in the BIOS. 
[*]I ordered a new SATA cable just to discard that maybe it produces an error only in linux installation. I don’t have any hope, but I will try as soon as it arrives. 
[/LIST]
 
[B]Request:
[/B]What else can I try? Right now I don’t know what else to do. There must be a way to install Ubuntu in this CPU if Windows can make it. 


I hope I am not forgetting any important detail. Thanks for your time and sorry for the long post.

---

### Post by Bashing-om on 2015-01-09
jander2; Hi ! Welcome to the forum .

I will start this ball rolling, We will all want to know that the SSD is seen by the operating system.
Boot up the liveDVD in "try ubuntu" mode to a terminal:
post back the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Which will show what you are working with and give us an indication of where to go from there to get ya to a point of installing ubuntu.
Is it your goal to install ubuntu alone on that SSD drive - or dual boot on that drive with Windows 7 ?
Will Windows continue to be a factor, such that we arrange the system to dual boot ?

[INDENT][INDENT]we find the way
[INDENT][INDENT][INDENT][INDENT]make it happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jander2 on 2015-01-09
Thanks for replying Bashing-om, 

This is what I got:

```

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

```


Hope it is useful

---

### Post by Bashing-om on 2015-01-09
jander2; Nope;

Not too helpful ... humm ...
Is there but the single SSD drive connected at this time ?
Is that last the complete output of the commands ?

Presently all we have is an idication that the partition table is messed up .. 
> 
Error: Can't have a partition outside the disk!


Confirm please that you are booting a DVD and not from a USB drive in this live-environment . Yes, I do see "  Unable to open /dev/sr0 " which certainly indicates the liveDVD .

Let's get some additional confirmation of what is. What return is there from terminal command:
```

sudo lshw -C disk

```
Then perhaps we can 'sic' fdisk on the SSD , IF you want to partition in legacy mode
OR
'sic' gdisk on it IF you want to partition in GPT .

[INDENT][INDENT]get that SSD recognized and identified .. then we can do something
[/INDENT][/INDENT]

---

### Post by jander2 on 2015-01-09
Yes, it was the whole output from those commands.

Connected to the motherboard are only: SSD, cdrom, the PCI discrete graphics card and a multi-card reader . 

I don't have any usb drive plugged in, so it can only boot from the cdrom. By the way, I tried to boot from a usb drive and never made it work after trying three different programs to make bootable USB drives (also tried several different pendrives). But the usb is detected when the PC boot and listed after pressing F8.



Didn't know this command. Very useful. Output bellow:

```

ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/sr0
       logical name: /cdrom
       version: 1.02
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          capabilities: partitioned partitioned:dos
          configuration: mount.fstype=iso9660 mount.options=ro,noatime signature=1b45097d state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@5:0.0.0
       logical name: /dev/sda
       size: 111GiB (120GB)
       configuration: sectorsize=512
  *-disk:0
       description: SCSI Disk
       product: Flash HS-CF
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdb
       version: 5.14
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: Flash HS-MS/SD
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@6:0.0.1
       logical name: /dev/sdc
       version: 5.14
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: Flash HS-SM
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@6:0.0.2
       logical name: /dev/sdd
       version: 5.14
       capabilities: removable
       configuration: sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdd

```

Indeed the SSD is listed there.

Thanks

---

### Post by Bashing-om on 2015-01-09
jander2; Well ...

The SSD is recognized, and is identified - for now - as 'sda'.

In GParted - from the liveDVD .. make sure that there are no key icons in the display pane (swap may be in use, -> swap off ).

What results if you (RE-)format the SSD -> file system type ext4  ?

As it is in my mind a possibility that AHCI may be required for bios to properly recognize the Solid State Device , We can just poke at it and see what results we can obtain.

[INDENT][INDENT]sometimes, not so yes
[/INDENT][/INDENT]

---

### Post by jander2 on 2015-01-09
I don't see any key icons or swap option. Where should I see them? In the gparted window?

When I launch gparted it already gives me error "Libparted bug found: Input/output error during read on /dev/sda". 
I press ignore and it shows me just 111GiB of unallocated space with a warning. Double click in the warning gives:
```

/dev/sda: unrecognised disk label

Input/output error during read on /dev/sda

Input/output error during read on /dev/sda

Input/output error during write on /dev/sda

Error fsyncing/closing /dev/sda: Input/output error

Input/output error during read on /dev/sda

Input/output error during read on /dev/sda

/dev/sda: unrecognised disk label

```

I cannot create partitions or format becuase it says that there is no partition table. 
So I go device/create partition table, choose msdos, and get same error again (gpt table either)

Bed time in Europe. Let's see tomorrow

Many thanks

---

### Post by Bashing-om on 2015-01-09
jander2; OK,

We continue tomorrow.
Maybe with both GPT and MBR tables in place it is confusing the issue ..
Maybe, we should just zero out that SSD with 'dd' and see then if it will take a new partitioning ?

What say others ?

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by jander2 on 2015-01-10
I tried *dd* to erase MBR and partition table, but if fails:

```

ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=1
dd: error writing &#8216;/dev/sda&#8217;: Input/output error
1+0 records in
0+0 records out
0 bytes (0 B) copied, 0.000602042 s, 0.0 kB/s

```

Any suggestions?

---

### Post by jander2 on 2015-01-10
Great news! It is working now!!! :smile:

It turns out that the motherboard has 3 sata ports, one supported by Marvell 88SE6111 and two supported by ICH9R/ICH9DO/ICH9DH. 

I was using the Marvel one, so I decided to check one of the other kind. This time gparted recognized the Windows 7 existing partitions and the installer allowed me to erase and install ubuntu.
First attempt didn't boot, but I had the old HDD connected during the installation and maybe the boot was created there. So I repeated the installation, this time with Linux Mint, and it boots and work nicely and fast.

So I will tag this as solved and update the keywords with more relevant ones. 

Thanks for you help, Bashing-om

---

### Post by Bashing-om on 2015-01-10
jander2; Well !

A bus controller !.. I will mark that down for future reference .

It is great you got it figured out .
To mark as solved:
1st post -> thread tools .
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by jander2 on 2015-01-11
I made some progress with the Marvell SATA/PATA port. 

With the SSD running Ubuntu nicely on the ACH9 SATA port, I tried to use the old HDD in the Marvell port. Again I got the same error (input/output error reading...). 
So I connected it to the remaining ACH9 SATA port and it is recognized and I can make partitions. I erase everything and make a fat32 partition. 
When I connected back to the Marvell port it fails again.

lspci shows this:
```

   03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO])  
 	Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller  
 	Flags: bus master, fast devsel, latency 0, IRQ 16  
 	I/O ports at df00 [size=8]  
 	I/O ports at de00 [size=4]  
 	I/O ports at dd00 [size=8]  
 	I/O ports at dc00 [size=4]  
 	I/O ports at db00 [size=16]  
 	Memory at fd9ff000 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: [48] Power Management version 2  
 	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-  
 	Capabilities: [e0] Express Legacy Endpoint, MSI 00  
 	Capabilities: [100] Advanced Error Reporting  
 	Kernel driver in use: pata_marvell

```
   
So I made some research about the pata_marvell on Marvell SATA/PATA ports and found this [wiki]("https://wiki.debian.org/pata_marvell"). I follow the steps and now it is recognized and I can access the partitions.

Now lspci shows:
```


03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller (rev b2) (prog-if 8f [Master SecP SecO PriP PriO]) 

 	Subsystem: Marvell Technology Group Ltd. 88SE6121 SATA II / PATA Controller 

 	Flags: bus master, fast devsel, latency 0, IRQ 16 
 	I/O ports at df00 [size=8] 
 	I/O ports at de00 [size=4] 
 	I/O ports at dd00 [size=8] 
 	I/O ports at dc00 [size=4] 
 	I/O ports at db00 [size=16] 
 	Memory at fd9ff000 (32-bit, non-prefetchable) [size=1K] 
 	Capabilities: [48] Power Management version 2 
 	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit- 
 	Capabilities: [e0] Express Legacy Endpoint, MSI 00 
 	Capabilities: [100] Advanced Error Reporting 
 	Kernel driver in use: ahci

```

So I decided to try to connect the SSD on the Marvell port and see if it works and loads Ubuntu. 
However, the PC restarts after POST and it doesn't boot Ubuntu. 

The point is that the motherboard does not have any AHCI option. In fact all the ICH9 ports are in IDE mode:

```

00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA Controller [IDE mode] (rev 02) (prog-if 85 [Master SecO PriO])
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device 7358
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at f500 [size=8]
    I/O ports at f400 [size=4]
    I/O ports at f300 [size=8]
    I/O ports at f200 [size=4]
    I/O ports at f100 [size=16]
    I/O ports at f000 [size=16]
    Capabilities: [70] Power Management version 3
    Capabilities: [b0] Vendor Specific Information: Len=06 <?>
    Kernel driver in use: ata_piix

```

Any suggestion of why it is failing with the SSD?  How can I use IDE mode on that Marvell port?

(Should I make a new thread for this?)


Thanks

---

### Post by Bashing-om on 2015-01-11
jander2; Uummmm ,,,

This has now progressed beyond my confidence level to advise. Hold onto this thread and let's see those who do have this experience advise.

( I can see a bios upgrade in the future )

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

