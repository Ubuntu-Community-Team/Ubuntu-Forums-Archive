---
title: "Linux-Installation on Samsung HE753LJ (HDD)"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by Arny006 on 2013-04-18
Dear Mates,

Untill Ubuntu 10.04 and 10.11 I was able to install the OS on my Samsung HE753LJ just simple without tricks. 

Afterwars I have to uninstall the "dmraid" & "libdmraid" packages from USB-Stick in order to achieve the goal/let Ubuntu recognize the HDD.

But now with 13.04: if I uninstall the dmraid, the installation stuck by reading the HDD's (even by hours of waiting). if I dont uninstall the dmraid the instaaltion-routine go ahead but I cannot see the /dev/sde6.

I recognize that "gparted"-usb and other older Linux-Versions still recognize my HDD.

Do anyone know what/how can I do to change that?
What can I do that every Linux (new & old) reconize my drive?

Thanks in advance and best regards, Arny

---

### Post by darkod on 2013-04-18
As the name says, dmraid handles raid in linux. It usually handles so called fakeraid, while software raid is handled by mdadm.

So, since you needed to remove dmraid to get ubuntu to recognize your disk(s), it means you have (or had earlier) a raid setup. Do you have a raid setup?

Another possibility is if the have a combination of hdd + small ssd with Intel RST active, so thwt the small ssd is like a cache disk. People have been able to install a dual boot in this setup too, but basically you first need to disable the Intel RST, remove the meta data from the disks, install ubuntu, and then activate Intel RST but tell it only to use the part of the ssd which is not used for ubuntu.

If dmraid only finds leftovers of meta data, and you are not using raid or Intel RST at the moment, you can remove the meta data and it will not give you more issues. You will not have to remove the dmraid package for any version, current or future.

Also note that 13.04 is officially not released yet.

---

### Post by Arny006 on 2013-04-18
I never understood the difference between dmraid and mdadm, maybe because I'm not a systemadministrator and Linux-newbe

To better explain the situation: 
On Intel Raid-controller (so called fake-Raid) are four (4) HE753LJ HDD in Raid-10 with Vista OS on it and the two (2) DVD-drives
On the second controller ([JMB36x]("http://www.jmicron.com/Support_FAQ.html")) are one HE753LJ and another 1TB also Samsung (this 1TB drive is recognized by the installation)
Don't want list all other drives again and don't pretend to install Linux on the Fake-Raid even so much place is wasted.

Also using```
sudo *dmraid* -f -S -M /dev/sde
``` don't help. The opposit is happen, by improper use of the command, I delete also the Raid information of my Intel-Raid-10 and have to install Vista again. That already done, vorget it.

The topic are: 
1. How can I install Linux on the 750GB-HDD without tricks?
2. Now are passt more than two years since I could not install Linux wihtout pains, everytime I tough someone correct this error that in former Linux-Distri was not present. How solve the situation?

The HE753LJ consist of two physical internal-connected hard-disks and designed/dedicated for continuos operation and forall Raid-systems. The question, at this point is: what/how do other people to install Linux on such HDD if dmraid cannot read them?

I would help you with investigations, if I can, but... do you mean that's time to solve the issue one forall? 
Or should I hope that final release of Kubuntu 13.04 let me install the system with the adoptions of tricks?

It's not a confortable situation, older ubuntu-distri don't recognize my new LCD-display or graphic-card having 2 inchies dark-space around the immage, newer distri don't recognize my HDD.
Older distries can also write the mbr of fake-raid10 and install the grub, new don't.

Help me please, maybe you help also more users.

Arny

---

### Post by darkod on 2013-04-18
Since the disks are on a different controller, and the 750GB where you want to install is not part of the raid, you should be able to do it. As you noticed yourself the 1TB disk is available to the installer.

But I think the 750GB disk might have old meta data on it and that's why it's not shown in the installer.

Since you have 5 disks of the same model, you need to be careful on which disk you remove the meta data since it can break the existing array as you noticed already.

I think it should be easy to find the disk not belonging to the raid since the other four disks will have identical partitions, and the fifth will not. So, first try this: Boot the computer with the ubuntu cd in live mode, open terminal and post the output of:
```
sudo parted -l
```

---

### Post by Arny006 on 2013-04-20
> **darkod said:**
> Since the disks are on a different controller, and the 750GB where you want to install is not part of the raid, you should be able to do it. As you noticed yourself the 1TB disk is available to the installer.
That's the point
> But I think the 750GB disk might have old meta data on it and that's why it's not shown in the installer.
My opinion: The controller host two place, one for intern connection and one for extern connection. I put a data cable from extern connection inside the case. Even if I switch the data-cable, the result is the same. Maybe the problem is the E-Sata-Win-Driver of manufacturer
> Since you have 5 disks of the same model, you need to be careful on which disk you remove the meta data since it can break the existing array as you noticed already.
I know now (after my error) but as sayd Kubuntu cannot read RAID-10 at all.
> I think it should be easy to find the disk not belonging to the raid since the other four disks will have identical partitions, and the fifth will not. So, first try this: Boot the computer with the ubuntu cd in live mode, open terminal and post the output of:
```
sudo parted -l
```
```
Fehler: Partitionen ausserhalb der Festplatte sind nicht möglich!         

Fehler: Partitionen ausserhalb der Festplatte sind nicht möglich!         

Fehler: /dev/sdc: unbekannte Partitionstabelle                            

Fehler: /dev/sdd: unbekannte Partitionstabelle  #Here Kubuntu cannot detect detect /dev/sda & /dev/sdb                          

Modell: ATA SAMSUNG HE753LJ (scsi)
Festplatte  /dev/sde:  750GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende   Größe   Typ       Dateisystem     Flags
 1      1049kB  161GB  161GB   primary   ntfs                              # Data = Linux-Downloads
 2      161GB   163GB  2147MB  primary   fat32           boot, LBA   # Grub-2-Partition
 3      163GB   750GB  587GB   extended
 5      163GB   180GB  17,2GB  logical   linux-swap(v1)
 6      180GB   294GB  114GB   logical   ext4
 7      294GB   408GB  114GB   logical   ext4
 8      408GB   522GB  114GB   logical   ext4
 9      522GB   636GB  114GB   logical   ext4
10      636GB   750GB  114GB   logical   ext4


Modell: ATA SAMSUNG HD103UJ (scsi)
Festplatte  /dev/sdf:  1000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs                        # Win-Backups


Modell: Initio MK2035GSS (scsi)
Festplatte  /dev/sdg:  200GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende   Größe  Typ      Dateisystem  Flags
 1      1049kB  200GB  200GB  primary  ntfs                            # External USB-Drive = Win-Downloads  


Modell: Generic STORAGE DEVICE (scsi)
Festplatte  /dev/sdj:  3965MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      4194kB  3965MB  3961MB  primary  fat32        boot     # SD-Card with copy of Grub-2-partition since Easy-BCD don't detect anymore  the internal one

 
```
```
/dev/sda: Kein GRUB 9f83
/dev/sda1: Kein GRUB 3b76
/dev/sdb: Kein GRUB 9f83
/dev/sdb1: Kein GRUB 3b76
/dev/sdc: Kein GRUB 00
/dev/sdd: Kein GRUB 00
/dev/sde: Kein GRUB 00
/dev/sde1: Kein GRUB 55aa
/dev/sde2: GRUB 2 v1.99
/dev/sde3: Kein GRUB 00
/dev/sde5: Kein GRUB 00
/dev/sde6: GRUB 2 v1.99
/dev/sde7: GRUB 2 v1.99
/dev/sde8: Kein GRUB 00
/dev/sde9: Kein GRUB 00
/dev/sde10: Kein GRUB 00
/dev/sdf: Kein GRUB 00
/dev/sdf1: Kein GRUB 55aa
/dev/sdg: Kein GRUB 9f83
/dev/sdg1: Kein GRUB 55aa
/dev/sdj: Kein GRUB 00
/dev/sdj1: GRUB 2 v1.99 
```

---

### Post by darkod on 2013-04-20
Well, it seems clear the disk you want to use for ubuntu is /dev/sde. You can try removing meta data from it (if there is meta data) with:
```
sudo dmraid -Er /dev/sde
```

That should not touch the meta data on other disks. If that asks you to confirm removal of meta data on sde, then you had meta data on it and that's why the installer is not seeing it.

On another note, you say sde2 is grub2 partition, but it's fat32. Usually you would have linux filesystem on the partitions of your linux installation.

---

### Post by Arny006 on 2013-04-20
> **darkod said:**
> Well, it seems clear the disk you want to use for ubuntu is /dev/sde. You can try removing meta data from it (if there is meta data) with:
```
sudo dmraid -Er /dev/sde
```
Installed dmraid again to give you feedback
```
sudo dmraid -Er /dev/sde
no raid disks and with names: "/dev/sde"
```
> 
That should not touch the meta data on other disks. If that asks you to confirm removal of meta data on sde, then you had meta data on it and that's why the installer is not seeing it.
The issue is, when the dmraid is installed, Kubuntu become big slowness, hence uninstall it again. Somethink is strange to me.
> 
On another note, you say sde2 is grub2 partition, but it's fat32. Usually you would have linux filesystem on the partitions of your linux installation.
Read many instruction sayd no matter for Grub2. I come to this partition trhough Easy-BCD, the copy of this partition is also on SD-card sdj1 and work perfectly till now.
The advantage is, I can manage start-option also over Vista on RAID-10. But that's other story.

---

### Post by darkod on 2013-04-20
So, there is no meta data on sde. That is not the reason why the installer is not showing it. At this point, it might be issue with the controller. Do you have any other SATA ports to try? Maybe swapping it with one of the DVD drives?

Even if you conect it to the controller running the raid, it should not matter when you are not actually configuring this disk as part of an array. That's what I think, I might be wrong.

---

### Post by Arny006 on 2013-04-22
The Intel-Raid-Controller hosts 6 data-connections, but only four are  designated to work in raid. Two are designated and connected to the two  DVD or not raid as it is.
I assume, if a connect a raid-hdd to one non-raid slot I brack the raid, if remember well already try it.

Welll/bad,  before I can start linux with an extra Grub-SD-card but now not more.  Vista is not a choice anymore (for many reasons) but yes for two  reasons: Cano-Scan-software and sound-driver.

MY consideration at  moment: I bought 6 best HDD-Drive at time for running 24x365 to host  Vista, the other hardware is 8 GB RAM, 2,66 GHz quadcore Intel proc., 1  GB newest Nvidia graph-card. Learn a little to use linux want to use it  but now can I nighter install them nor srat the existing one. What's up?  I'm discouraged!

Well, all my data are on the Samsung HD103UJ,  It's half full and i can host on them also the Initio-USB-drive (no nedd  but) and the linux-Downloads at moment on the Samsung HE753LJ. So I can  start from scratch and make a fresh install of everythink. If so...

1. Should I renounce to RAID? Last Vista install take only 20 GB!
2. Is a good idea to install Kubuntu on RAID-10? Gparted can see them, linux-installer not!
3. Vista-disk-management see at moment:
3.1 [JMB36x]("http://www.jmicron.com/Support_FAQ.html") external connection as Disk 0
3.2 [JMB36x]("http://www.jmicron.com/Support_FAQ.html") internal connection as Disk 1
3.3 Intel-RAID-10- connection as Disk 2 (the other are not relevant)
4. Gparted/fdisk see the Disk on other way:
4.1 RAID-10 (4 HDD's) sda-sdb-sdc-sdd
4.2 [JMB36x]("http://www.jmicron.com/Support_FAQ.html") external as sde
4.3 [JMB36x]("http://www.jmicron.com/Support_FAQ.html") internal as sdf
5. Diskpart> list disk see the disks like Vista-disk-management, that's OK

What the hell is going on? Even if i dissolve the raid remain the issue: **linux-installer don't recognize the Samsung HE753LJ**

I can understand if linux consider the HE753LJ (due the physical construction) as LVA (2 disk each 375 GB cascaded = serial connection of two disk) but not as raid. This is a big misstake, cause of a raid is always a parallel connection of disks. I'm wrong? 

I can also understand that a raid-0+1 composed from 4-LVA's is unreadable for linux, but not as single LVA through LVM. It's a standard LVM in linux newest kernels?

I cannot understand [http://en.wikipedia.org/wiki/Logical_volume_management](http://en.wikipedia.org/wiki/Logical_volume_management) coming from Linux-world, linux-kernel 2.6 don't support (apparently) raid-5 but was able to manage raid-5 & raid-0+1 writing also mbr and put grub-2 on it. The newer kernels don't support anythings.

What's your reccommendation?

---

### Post by darkod on 2013-04-23
Wow man, the decision is not easy.

I am rereading the thread again, and I notice you said you have a copy of grub2 on a SD card because EasyBCD can't see it on the internal too. I wonder if it's possible that there is some error with one of the partitions in the table, in which case linux can ignore the disk not knowing which partitions to display. If EasyBCD can't see the grub2 files on /dev/sde, then that means it's not only linux that can't read the disk correctly. Right?

If you want ubuntu/kubuntu on the fakeraid it should work. The only thing is that usually it's installed slightly different from the standard non-raid install. For ubuntu, there was something called Alternate Install CD (separate ISO file, not the standard live cd), which is best to be used for raid or lvm installs. The live cd was able to install on fakeraid too, so many people were using it too. But the live cd fails at the final step, the grub2 installation on a fakeraid, so you would need to add grub2 later manually.
Also, sometimes a fakeraid array needs to be activated to be seen by ubuntu. For example in live mode in terminal you can do:
```
sudo dmraid -ay
```

That will scan and activate all fakeraid arrays. Of course, if you removed the dmraid package that will not work. The first thing to be able to install to a fakeraid (or simply to read it), is that it has to activate it and it has to have the dmraid package present, not removed.

I am starting to think this has something to do with a partition issue, as I mentioned above. Especially if you are mixing the partitioning programs you use. Windows is very stupid when linux partitions are concerned, so once you start using a disk for linux, I wouldn't touch it with windows tools. Windows sometimes can't handle even ntfs, it has happened to me. :)

---

### Post by Arny006 on 2013-04-24
I found somethink in the i-net. What do you think about?

```
# in order to let Ubuntu & Kubuntu read all kind of Disks, install following Packages-->

# Kubuntu:

sudo apt-get install dmraid libdmraid lvm2 kvpm gparted ntfs-3g
sudo dmraid -ay


# Ubuntu:

sudo apt-get install dmraid libdmraid lvm2 system-config-lvm gparted ntfs-3g
sudo dmraid -ay
```

---

### Post by darkod on 2013-04-24
Well, dmraid should already be included, but you said yourself you removed it. As I said, for reading fakeraid arrays, ubuntu needs it.

As for the other packages, lvm2 is for LVM which you don't have. gparted is the GUI frontend of parted, and ntfs-3g is the ntfs driver. They help for GUI disk management tools and managinf ntfs partitions, but in your case it doesn't even see the disk so I don't think it will help. You can try anyway.

However, since dmraid was removed by you, installing dmraid can help see the fakeraid.

---

### Post by Arny006 on 2013-04-25
My hope ist LVM can/allow to see the HE753LJ which compsed from zwo hard disks.

My intent is to install first LVM & test, than dmraid & test, than the other packages and after each to test if my HDD can be seen.

---

### Post by darkod on 2013-04-25
Hold on, what do you mean by two disks? I thought that was only a single SATA disk. Is it like a hybrid disk with ssd cache on it?

LVM can allow you sometimes to see disks but not always, it depends how the disk is configured. If you want to try, simply add the lvm2 package and try activating any Volume Groups:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

---

### Post by Arny006 on 2013-04-25
Right, that's a unique disk (seeing the hardware from outside) but internally are two physical disks each 375 GB.

I think, that cause all the trouble under Linux.

Anyway, thanks for the additional command that I will try

[COLOR=#ff0000]**Addendum:**[/COLOR]

installing "gparted" on Kubuntu-USB-Stick (here no dmraid installed) I can read all drives including the Soft-RAID-0+1.

All the magic will be to convince Kubuntu-installer to use "gparted" or whose libraries during the installation-process.

---

### Post by Arny006 on 2013-05-02
> **darkod said:**
> So, there is no meta data on sde. That is not the reason why the installer is not showing it. At this point, it might be issue with the controller. Do you have any other SATA ports to try? Maybe swapping it with one of the DVD drives?
You are right and I was wrong, in fact is a controller problem, the responsible is the "Intel ICH8"-RAID-Controller.
I connect an other HDD to the ([JMB36x]("http://www.jmicron.com/Support_FAQ.html")) and produce the same results/problem/error.
> 
Even if you conect it to the controller running the raid, it should not matter when you are not actually configuring this disk as part of an array. That's what I think, I might be wrong.
But after many try and error, the solution is founded and maybe can be adopted from other users.

**Challenge: The Linux-Installation-Routine stuck by preparing the Drive**

[B]Solution (step by step):
1.[/B] The installation can be done only with a Live-USB/medium because we need to uninstall some software and install some other on the Installation-Medium
**2.** Make the Live-Installation-Drive (USB-Stick, SD-Card, etc.) with "Unetbootin" for Windows or Linux and assign 2,5-3 GB "Space used to preserve files across reboots"
**3.** Boot the PC from the Live-Installation-Medium press "Enter" to "Default" an choice "Try Ubuntu/Kubuntu". Than in a terminal type:
```
sudo apt-get purge dmraid libdmraid && sudo apt-get install gparted
```
**4.** Once done reboot the PC as explained in point 3. (Try Ubuntu/Kubuntu) and after the boot is finished click "Install Ubuntu/Kubuntu"

**Now** the "Installation-Routine" ignore the existing RAID's and use the additional libraries (installed with "gparted") to detect quick all other Drives where you want to install Linux.

**Note:** With this method the "dmraid" will not be installed on the OS-destination-Drive, hence no boot-problems at all.

Enjoy

---

### Post by darkod on 2013-05-02
Glad you found a way.
Just to go back to your step 1, this can be done with a cd too, not only usb. But since the cd can not keep the changes, you will have to do it every time you reboot. You can remove and add packages when using a cd in live mode too, not that you can't. Only these changes go away on reboot.

And not to lose the changes (which go away when you reboot), start the installation using the Install icon while still in the same live session, without rebooting. It should work.

---

### Post by Arny006 on 2013-05-03
That's the point, you/we need the libraries installed with "gparted" & we need to reboot, hence an install-medium with persistence space is needed.
Maybe I'm wrong again cause of I don't use DVDs to install Linux and don't know if the DVD can use the libraries immediately or need a reboot like a USB-Stick.

---

### Post by darkod on 2013-05-03
I think they should be able to be used right away. But in any case a medium with persistance is useful.

---

### Post by Arny006 on 2013-05-25
[COLOR=#ff0000]**Edit:**[/COLOR]
Finally, new Kubuntu take place on the separate HE753LJ. In total the HDD host a 150GB NTFS partition for "Linux-Downloads", a 2GB FAT32 "Dedicated GRUB2 partition", and on the remain extended place (ca. 500GB) a 16GB "swap" and five Linuxs.

Additionally I install a Kubuntu 12.10 on Intel RAID 0+1.

All the basic/magic for Ubuntu & Kubuntu is "dmraid" + "gparted". With these apps are many additional libraries installed that permit to read and write RAID & non-RAID disks.

**Considerations:**
On mentioned HDD are Kubuntu 12.10+13.04, Mint KDE 14+15 & Linux Ultimate Edition 3.5 (five in total)
The Kubuntus presents the most difficulties (Ubuntu tests give same results as brother Kub...). As newer the distri as difficult the install.
No need additional packages or apps for Mints and UE 3.5 in order to make the installation.
Mint but has problems with the "sources" and not only the KDE but also "cinnamon" & "MATE" 

**Conclusions:**
I wish Ubuntu & Kubuntu take more care about the hardware compatibility also because the times of distris on CD are past and now users need anyway DVD/SD/USB-sticks.

---

