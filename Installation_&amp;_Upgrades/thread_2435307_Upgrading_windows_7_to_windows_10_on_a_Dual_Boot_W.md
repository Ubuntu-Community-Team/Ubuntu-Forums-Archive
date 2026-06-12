---
title: "Upgrading windows 7 to windows 10 on a Dual Boot Windows/Ubuntu system"
date: 2020-01-19
forum: Installation &amp; Upgrades
---

### Post by oisin000 on 2020-01-19
Hi, 

I set up my laptop to be dual boot Ubuntu/Windows a number of years ago. I use Ubuntu by default but once a year I have to boot up Windows to access a government website. With the demise of Windows 7 support I intend to upgrade to windows 10 (via the tool provided by Microsoft [https://go.microsoft.com/fwlink/?LinkId=691209](https://go.microsoft.com/fwlink/?LinkId=691209)) 
So I'm just wondering if I should expect any problems here given that it is a dual boot system or should the upgrade tool just affect the windows partitions and the Linux partitions and my dual boot setup should remain unaffected ? 
Or are there some steps I have to take in advance to ensure that there are no problems ? 

Thanks, 

Usjes.

---

### Post by CatKiller on 2020-01-19
> **oisin000 said:**
> So I'm just wondering if I should expect any problems here given that it is a dual boot system or should the upgrade tool just affect the windows partitions and the Linux partitions and my dual boot setup should remain unaffected ?  

Windows in general likes to pretend that no other OS exists. Malicious or careless breaking of your Linux part is a possibility. 

> Or are there some steps I have to take in advance to ensure that there are no problems ? 

Make backups. Prepare your install media. Accept the possibility that you'll need to reinstall both OSes.

---

### Post by oldfred on 2020-01-19
All BIOS/MBR versions of Windows in recent history have ignored Linux logical partitions when it rewrites the partition table. 
Data is still there all that is needed is to restore the Linux partition to partition table.

You can backup partition table info to a small text files and then if necessary restore that if you do not otherwise change partitions during Windows install.
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX >parts_ parts.txt
sudo sfdisk -d /dev/sdb > parts_sdb.txt
Be sure to use same version of sfdisk. Older versions only supported MBR, newer verisons of sfdisk now support gpt and include a lot more info in the text file.

Is install BIOS/MBR or newer UEFI/gpt? Most but not all Windows 7 installs were BIOS/MBR.
Is hardware after 2012, so really UEFI hardware? If so may be better to just backup all data and do total new installs in UEFI boot mode to gpt partitioned drive.
Microsoft required vendors to install in UEFI/gpt mode starting with Windows 8. But users could install in BIOS mode and some vendors still sold Windows 7 on newer hardware.

---

### Post by oisin000 on 2020-01-19
> **oldfred said:**
> All BIOS/MBR versions of Windows in recent history have ignored Linux logical partitions when it rewrites the partition table. 

Is install BIOS/MBR or newer UEFI/gpt? Most but not all Windows 7 installs were BIOS/MBR.
Is hardware after 2012, so really UEFI hardware? If so may be better to just backup all data and do total new installs in UEFI boot mode to gpt partitioned drive.
Microsoft required vendors to install in UEFI/gpt mode starting with Windows 8. But users could install in BIOS mode and some vendors still sold Windows 7 on newer hardware.

Well its a Dell Latitude E6410 and it looks like it shipped in about 2011/2012. The system info shows a BIOS version from 2013 and Dell's website tells me there is a BIOS update from 2017 which I will install before the upgrade. 
Currently gparted shows the partitions as:

/dev/sda1: Boot
/dev/sda2: Windows install
/dev/sda3: Linux root (/)
/dev/sda4: Linux 'home'
                 |- sda5
                 |- sda6

So the sd4 partition is divided into two logical 'sub-partitions' if that is the correct term. 

Do I need to back each of these up individually ? eg.

sudo sfdisk -d /dev/sda1 > parts_parts.txt
sudo sfdisk -d /dev/sda2 > parts_sda2.txt
 .
 .
sudo sfdisk -d /dev/sda6 > parts_sda6.txt

Assuming that the windows upgrade does then remove all references to the Linux partitions in the partition table what syntax do I use to restore these from the parts_<xyz>.txt backups ?

Thanks, 

Usjes.

---

### Post by oldfred on 2020-01-19
You back up just a drive like sda.
If you look at text file it should show all your partitions.

-d is the dump command
see example uses full --dump rather than -d as short name
man sfdisk
>       Use the --dump option to save a description of the device layout  to  a
       text  file.   The  dump format is suitable for later sfdisk input.  For
       example:

              sfdisk --dump /dev/sda > sda.dump

       This can later be restored by:

              sfdisk /dev/sda < sda.dump


---

### Post by oisin000 on 2020-01-19
> **oldfred said:**
> You back up just a drive like sda.
If you look at text file it should show all your partitions.

-d is the dump command
see example uses full --dump rather than -d as short name
man sfdisk

I executed the backup command and it created the text file however it did also issue a warning (emphasis mine):

oisin@oisin-Latitude-E6410:~$ sudo sfdisk --dump /dev/sda > sda.txt 
[sudo] password for oisin:  
[B]Warning: extended partition does not start at a cylinder boundary. 
DOS and Linux will interpret the contents differently.[/B]

Should I be concerned about this? Also, it has occurred to me, if the update to windows 10 does remove the Linux partitions from the partition table and I want to restore them using my sda.txt backup then I will need to be able to run the sfdisk command without my current linux installation. I guess this means I also have to have a Linux live on a thumbdrive ? Or is there some other way of running the sfdisk command if my Linux installation is unbootable ?

Thanks, 

Usjes.

---

### Post by oldfred on 2020-01-19
Do not worry about the start issue on an extended partition. You do not write into the extended partition, only the logical partitions inside the extended.
That warning is standard on old MBR configurations, and warnings based on newer 4K drives. If drive is older 256k then warning would never apply.

You always need a repair disk for the current version of every operating system you have installed.
So always have a Windows repair/recovery drive and an Ubuntu live installer.

---

