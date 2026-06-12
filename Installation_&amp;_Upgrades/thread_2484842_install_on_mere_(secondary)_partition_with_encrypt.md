---
title: "install on mere (secondary) partition with encryption via installation wizard"
date: 2023-03-12
forum: Installation &amp; Upgrades
---

### Post by rawgr on 2023-03-12
Hi there,

I have a system with an 230gig ssd and a 1TB sata drive.


I want to dual-boot windows10 and ubuntu 22.4.2 on it:


Specifically, I installed windows10 on the ssd and also gave about half the old hdd's space an ntfs formatting to install games to.


Ideally I want the other half for the complete ubuntu install.


+I did install it, manually partitioning the hdd via the graphical installer, but completely forgot about proper encryption...


So now I have the running windows system as desired...


I still have the ubuntu 22.4.2 usb medium and I know how to start the ubuntu installation but I don't know how to configure the partition table to get proper encryption for the ubuntu partition only.


Is this even possible for partitions only?


(and if so, how do I make use of my free space in the partition table without touching my windows system and its' storage partition?)

---

### Post by MAFoElffen on 2023-03-12
When you installed Ubuntu, did you install with LVM2? ZFS?
```

ls /dev/mapper/
sudo zfs list

```
And for encryption, I feel that the decision for, is that someone worries about the physical security of data if a device of drive is stolen. What kind of data do you have plans for? (Like, for example, the home folder?)

---

### Post by rawgr on 2023-03-12
hi,


I had to mount a /boot partition for encryption to work - apart from said /boot ...  which had to stay readable...

---

### Post by MAFoElffen on 2023-03-12
I am confused. It had sounded like you installed Ubuntu already... and was trying to add encryption to an existing install.

If you are doing a fresh install with Ubuntu 22.04.2 Desktop, then before it gets to the installer, follow the instructions from either of these links:
[https://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot](https://askubuntu.com/questions/293028/how-can-i-install-ubuntu-encrypted-with-luks-with-dual-boot)
[https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html](https://www.mikekasberg.com/blog/2020/04/08/dual-boot-ubuntu-and-windows-with-encryption.html)

---

### Post by rawgr on 2023-03-13
it's alright


It's what I tried first but there has to be an unencrypted  /boot  partition in either of those cases...

I ultimately decided to rather do a fresh install as opposed to try and resize and get space from elsewhere...



I don't know how to close this thread
but I no longer need help with this...

Thank you both and sorry for not framing the question with a broader understanding either way!

---

### Post by MAFoElffen on 2023-03-13
> **rawgr said:**
> I don't know how to close this thread
but I no longer need help with this...
No problem. If you have any questions, feel free to ask them here. We are Users helping Users.

To close the thread (mark it as "Solved"), go to the "Thread Tools" Link at the upper right of this page, then select "Solved".

---

### Post by rawgr on 2023-03-17
Hello again,

I am very confused and would like to keep asking:



I found that my board uses the legacy+UEFI mode,

and  I have a win10 system (fast start disabled there) running on the SSD  and I am already using one partition on the other harddrive of **further** interest there for windows data only.


-I only found out about the legacy+UEFI mode now.


-Ideally I'd like both systems to boot quick. ....



as per the askubuntu article: I am not sure what the difference between UEFI and EFI is, by that I mean I am not 100% certain I DO have an EFI mainboard


I also think I installed windows so it boots from that sata drive instead of the SSD which I wanted exklusively for windows and I don't have a backup available.



Depending on the very helpful answers I am not sure If I should put off installing a properly configured linux install until this changes, first?



I am confused here because when I tried to install with a lone /boot partition earlier, having created the encrypted root / ,the installation wizard informed me I am missing an EFI partition...




Does now requiring an EFI partition mean I am making proper use of UEFI with the way I have booted the installer?



I am then unable to allocate space for an EFI partition     and the install wizard confuses me here:    Is it possible that I am running into the limit of possibly only having 3 primary partition choices and would therefor need to create a LVM group via the live mode of the usb-installer first?



I am not sure I misunderstand the involved OS knowledge.


Can someone confirm how I mean to understand UEFI there, and why I am not able to create all partitions during the installation process?


Is it actually the "MBR to GPT" thing to single out? 

(and what about the "primary partition limit" either way)



I really do not want to touch the windows drive for now as I don't have a backup option available...




I should probably get a backup solution working, reinstall windows, repeat,....


Or am I missing something simple and safe, on the off chance?


I really do not want to risk losing my music data.

---

### Post by oldfred on 2023-03-17
If you think you music or other data has any value, you must have good backups to another device preferably more than one.

UEFI is efi. Years ago it was just efi, but standardized as UEFI. 

Windows requires gpt partitioning for UEFI boot. 
Ubuntu will let you use the old (now very old) MBR partitioning with UEFI, but really should not.
Microsoft requried vendors to install in UEFI boot mode to gpt partitioned drives starting in 2012 and release of Windows 8.
So you should install in UEFI mode, since hardware is UEFI. BIOS mode was only for those with older BIOS only systems (pre 2012) and wanted compatibility of new Windows.

With gpt you do not have primary, extended, and logical partitions, nor 4 primary partition limit. All partitions are in effect primary.

Ubuntu installer defaults to using the ESP - efi system partition on first drive. So it must have an ESP, better if gpt, unless you do a work around.
Various work arounds for two drive or external drive installs:
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
You can disconnect all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

Note that converting drive from gpt to MBR or MBR to gpt, totally erases drive. It that is your music data in another partition that will also be erased. Or why you must have good backups.

Post these in code tags from Forum's advanced editor & using # icon:
sudo parted -l
lsblk -e7  -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT

---

### Post by rawgr on 2023-03-17
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD10EZEX-75W (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  53.5MB  52.4MB  primary  ntfs         boot
 2      53.5MB  581GB   581GB   primary  ntfs
 3      581GB   585GB   4200MB  primary  ext4
 4      585GB   1000GB  415GB   primary


Model: ATA SanDisk SDSSDA24 (scsi)
Disk /dev/sdb: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  239GB  239GB  primary  ntfs
 2      239GB   240GB  573MB  primary  ntfs         msftres


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdc: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      32.8kB  4922MB  4922MB               ISO9660    hidden, msftdata
 2      4922MB  4927MB  5155kB               Appended2  boot, esp
 3      4927MB  4928MB  307kB                Gap1       hidden, msftdata
 4      4928MB  8019MB  3091MB  ext4


```


```
ubuntu@ubuntu:~$ lsblk -e7 -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT 
FSTYPE      NAME   LABEL                    PARTLABEL   SIZE FSUSED MOUNTPOINT
            sda                                       931.5G        
ntfs        &#9500;&#9472;sda1 System-reserviert                     50M        
ntfs        &#9500;&#9472;sda2                                    540.8G        
ext4        &#9500;&#9472;sda3                                      3.9G        
crypto_LUKS &#9492;&#9472;sda4                                    386.7G        
            sdb                                       223.6G        
ntfs        &#9500;&#9472;sdb1                                      223G        
ntfs        &#9492;&#9472;sdb2                                      546M        
iso9660     sdc    Ubuntu 22.04.2 LTS amd64             7.5G        
iso9660     &#9500;&#9472;sdc1 Ubuntu 22.04.2 LTS amd64 ISO9660     4.6G   4.6G /cdrom
vfat        &#9500;&#9472;sdc2 ESP                      Appended2   4.9M        
            &#9500;&#9472;sdc3                          Gap1        300K        
ext4        &#9492;&#9472;sdc4 writable                             2.9G   7.4M /var/crash

```

---

### Post by oldfred on 2023-03-17
You have BIOS installs on MBR drives.
Only boot in BIOS mode, not UEFI.
How you boot install media UEFI or BIOS, is both how it will install or make repairs. For both Windows & Ubuntu.

But if UEFI hardware, you should plan on total new installs in UEFI mode & gpt partitioning.

Since it did not show used, do you have Windows fast start up or hibernation on? That also gets turned back on with some Windows updates, so often have to redo it.

You can use a gpt partitioned drive with Windows in BIOS/MBR mode on another drive.
And you can boot Ubuntu in either BIOS or UEFI mode from gpt partitioned drives. I started converting to gpt back when my XP was BIOS but Ubuntu 10.04 was on a gpt drive with a bios_grub partition so grub could install correctly in BIOS mode. UEFI requires the ESP - efi system partition.

---

### Post by rawgr on 2023-03-18
ok, I'll first of all try and get a basic backup solution then...


I'll mark the thread as solved and may open it back up once I have one ready.


Thank you.


Phil

---

