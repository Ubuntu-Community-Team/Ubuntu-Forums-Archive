---
title: "Karmic Issues, part 2"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by g63marty on 2009-10-23
System: HP s3220n AMD 5000+, 4GB RAM, Nvidia 8400gs 512mb, 640GB internal drive, multiple external drives (eSata,Firewire 400,USB)

O/S is 64 bit Kubuntu Karmic Koala 9.10 RC with most updates. 

I have a 1500 GB (1.5 TB) Seagate SATA hard drive (single drive, no RAID) attached to a firewire 400 port. It is formated with NTFS. It does not show up at all with the lshw (output is below) command. I cannot find a driver for this.

I also have an external Western Digital 2TB drive, eSata II, RAID 0 (striped) over 2 1TB disks. It also is not listed. I suspect this uses a soft RAID configuration. 

Since the only drives Kubuntu cannot see are both over 1TB, I am wondering if ubuntu even supports these larger sizes?

Any help with the drivers required to support these drives and I would be eternally grateful.

- MG 

sudo lshw -C disk                                              
  *-disk                                                                              
       description: ATA Disk                                                          
       product: WDC WD10EACS-00Z                                                      
       vendor: Western Digital                                                        
       physical id: 0.0.0                                                             
       bus info: scsi@3:0.0.0                                                         
       logical name: /dev/sda                                                         
       version: 01.0                                                                  
       serial: WD-WCASJ1048739                                                        
       size: 931GiB (1TB)                                                             
       capabilities: partitioned partitioned:dos                                      
       configuration: ansiversion=5 signature=724c68bb                                
  *-cdrom                                                                             
       description: DVD-RAM writer                                                    
       product: CD/DVDW TS-H653L                                                      
       vendor: TSSTcorp                                                               
       physical id: 0                                                                 
       bus info: scsi@4:0.0.0                                                         
       logical name: /dev/cdrom                                                       
       logical name: /dev/cdrw                                                        
       logical name: /dev/dvd                                                         
       logical name: /dev/dvdrw                                                       
       logical name: /dev/scd0                                                        
       logical name: /dev/sr0                                                         
       version: 0714                                                                  
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram                     
       configuration: ansiversion=5 status=nodisc                                     
  *-disk                                                                              
       description: ATA Disk                                                          
       product: Hitachi HDT72504                                                      
       vendor: Hitachi                                                                
       physical id: 1                                                                 
       bus info: scsi@5:0.0.0                                                         
       logical name: /dev/sdb                                                         
       version: V5CO                                                                  
       serial: VFK301R31G56EK                                                         
       size: 372GiB (400GB)                                                           
       capabilities: partitioned partitioned:dos                                      
       configuration: ansiversion=5 signature=1549f232                                
  *-disk:0                                                                            
       description: SCSI Disk                                                         
       physical id: 0.0.0                                                             
       bus info: scsi@9:0.0.0                                                         
       logical name: /dev/sdc                                                         
       size: 3887MiB (4076MB)                                                         
       capabilities: partitioned partitioned:dos                                      
       configuration: signature=001c2022                                              
  *-disk:1                                                                            
       description: SCSI Disk                                                         
       physical id: 0.0.1                                                             
       bus info: scsi@9:0.0.1                                                         
       logical name: /dev/sdd                                                         
  *-disk:2                                                                            
       description: SCSI Disk                                                         
       physical id: 0.0.2                                                             
       bus info: scsi@9:0.0.2                                                         
       logical name: /dev/sde                                                         
  *-disk:3                                                                            
       description: SCSI Disk                                                         
       physical id: 0.0.3                                                             
       bus info: scsi@9:0.0.3                                                         
       logical name: /dev/sdf                                                         
  *-disk                                                                              
       description: SCSI Disk                                                         
       product: 7500AAK External                                                      
       vendor: WD                                                                     
       physical id: 0.0.0                                                             
       bus info: scsi@8:0.0.0                                                         
       logical name: /dev/sdg
       version: 1.06
       serial: E
       size: 698GiB (750GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=a238f957
  *-disk
       description: SCSI Disk
       product: My Book ES
       vendor: WD
       physical id: 0.0.0
       bus info: scsi@10:0.0.0
       logical name: /dev/sdh
       version: 012
       serial: 3
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=4 signature=8d399bc0

---

### Post by jbrown96 on 2009-10-23
There's no problem with the disk sizes. I'm not sure I understand the 2TB drive system. Is it one unit that happens to use RAID0 internally, or did you configure some sort of system with RAID? Is it just a normal esata hard drive that uses two drives because the capacity is so large?

It looks like all your devices are being seen by the system; it must be that the device notifier is ignoring them for some reason. This isn't that unusual for the eSATA drive because Kbuntu can't tell the difference between a regular hard drive and an external esata drive. It is stranger, but not unheard of, for a firewire drive to be ignored as well. Post the output of ```
sudo fdisk -l
``` and I will help you manually mount them. That way we can be sure that there are no problems with the drives, then we'll work on getting KDE to recognize them and automatically prompt you to mount them.

Edit:
If all the drives are NTFS, you may not have the drivers installed. Do ```
sudo apt-get install ntfs-3g ntfsprogs
``` Logout and back, then re-connect the drives once you are logged in.

---

### Post by RichardCL on 2009-10-24
I'm currently having a very similar problem.

2x1TB drives on an NVIDA motherboard with RAID. Ubuntu 9.04 Jaunty and before didn't recognise any RAID and just treated the system as 2x1TB drives. On install I could only select and install to one of the drives (guided) or partition manually and use a whole drive for /home/

Now with a fresh install of Karmic, the installation program recognises both the 2x1TB drives and also a 2TB drive, which is the RAID array.

Unfortunately, GRUB fails on install (although it seems that install managed to format and begin the installation).

---

