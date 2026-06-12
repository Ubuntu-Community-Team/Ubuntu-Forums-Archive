---
title: "new nvme and sata will not boot"
date: 2021-05-17
forum: Installation &amp; Upgrades
---

### Post by vidtek on 2021-05-17
I purchased a new Pioneer 250gb NVME drive, cloned my original Samsung sata SSD EVO 250gb to it and it worked perfectly first time.

This drive has neon 20.04 and Windows 10.   It worked all the time I do not have the original sata drive installed.

I also bought a new NVME Sabrent 2tb Rocket drive so both M2 slots on my Asus Strix 270E are populated.

As soon as I insert the sata drive into the quick dock it no longer boots to either drive, all I get is the default grub black screen of nothingness.  The same happens if I 

use my sata docking station via USB, black screen with that super-helpful black grub screen. 

If I remove the SSD drive all works ok.

I spent the morning playing around with bios options, changing sata cables over and the configuration is 

now with sata 1,5 and 6 disabled, as sata 1 is required by the NVME drive, and 5&6 are required for x4 speed instead of x2 when they are enabled in the bios.

Also the PCI16 is enabled not the USB3 in the bios.

I have changed the UUID of the SSD so that is not the reason for the clash.

I want to be able to boot from either device particularly for cloning and backup, but it does not look as if that is possible with my motherboard.

Anyone any ideas?[ATTACH]288488[/ATTACH]

Cheers Tony

---

### Post by VMC on 2021-05-17
show out of:
```
sudo fdisk -l and efibootmgr
```
with all the drives plugged in

edit:try with live cd if you can't get a terminal prompt. Use VT if possible

---

### Post by rbmorse on 2021-05-17
If the two SSD devices are really "clones" of each other, the partition UUIDs and other metadata will be the same on both devices. Not allowed. During the boot process when the O/S scans for storage devices the dupes are detected and since it doesn't know which to choose, it goes catatonic.   

reformat the old SSD.   If you need to have a copy of the files on the new SSD, use rsync to make the copy.  That will solve the duplicate UUID problem and using rsync will preserve all the filesystem metadata like ownerships and permissions.

---

### Post by vidtek on 2021-05-17
> **VMC said:**
> show out of:
```
sudo fdisk -l and efibootmgr
```
with all the drives plugged in

edit:try with live cd if you can't get a terminal prompt. Use VT if possible

Can't do it, no boot with the sata drive in either direct sata cable to mobo or via USB.

I'll give a live usb stick a go but I doubt it will work either.

Get back to you soon, thanks for reply.

Tony.

EDIT*****************

OK attached results.[ATTACH]288492[/ATTACH]

---

### Post by vidtek on 2021-05-17
[ATTACH=CONFIG]288494[/ATTACH]

Here is the dreaded black screen of grub I get.  Sorry about the reflections, been pissing with rain all day then when I take a 'photo out comes the sun.....

Tony

---

### Post by VMC on 2021-05-17
If you type "set" from the grub prompt, look for the grub partition that controls your boot. I suspect its your neon.

---

### Post by vidtek on 2021-05-17
> **rbmorse said:**
> If the two SSD devices are really "clones" of each other, the partition UUIDs and other metadata will be the same on both devices. Not allowed. During the boot process when the O/S scans for storage devices the dupes are detected and since it doesn't know which to choose, it goes catatonic.   

reformat the old SSD.   If you need to have a copy of the files on the new SSD, use rsync to make the copy.  That will solve the duplicate UUID problem and using rsync will preserve all the filesystem metadata like ownerships and permissions.

Thank you for your reply.

I did wonder about the UUID's so I changed the UUID on the SSD sata drive.   I have a dual quick release dock for [https://www.amazon.com/Mobile-Internal-Enclosure-Floppy-Location/dp/B07WK2M9GR]("https://www.amazon.com/Mobile-Internal-Enclosure-Floppy-Location/dp/B07WK2M9GR")

When I changed the UUID I did wonder if it would affect windows10 activation status.....    

Anyway it made no difference, still get the black screen of grub as per picture above.

Tony.

---

### Post by VMC on 2021-05-17
Here's a link on how to fix the minimal-bash prompt:
[https://www.geeksforgeeks.org/how-to-fix-minimal-bash-like-line-editing-is-supported-grub-error-in-linux/](https://www.geeksforgeeks.org/how-to-fix-minimal-bash-like-line-editing-is-supported-grub-error-in-linux/)

---

### Post by oldfred on 2021-05-17
To get around boot issue, boot live installer. Then post this in code tags, do not copy to another site.

lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by vidtek on 2021-05-17
VMC    I can't see what the set command says it scrolls to bottom too quickly :cry:

---

### Post by vidtek on 2021-05-17
> **oldfred said:**
> To get around boot issue, boot live installer. Then post this in code tags, do not copy to another site.

lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Oldfred-thanks for your reply, take me a while to get the info you want-now dinner's ready, the lovely Jane is not impressed.....

---

### Post by vidtek on 2021-05-17
> **oldfred said:**
> To get around boot issue, boot live installer. Then post this in code tags, do not copy to another site.

lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Oldfred-thanks for your help.   sdg is the SDD, the sabrent nvme 2tb is not there for some reason??? 

```
kubuntu@kubuntu:~$ lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"
NAME        MOUNTPOINT LABEL                 SIZE FSTYPE   UUID                                 PARTUUID
sda                                          3.6T                                               
&#9492;&#9472;sda1                 data                  3.6T ext4     b0171cc5-2137-4789-9359-ee7315ade770 26d3afe3-d442-4c36-867b-7e48cb5671fe
sdb                                          4.5T                                               
&#9492;&#9472;sdb1                 tv                    4.5T ntfs     6E66CE4866CE112F                     d9118715-a532-4b4f-8ba0-01fe09c65398
sdg                                        238.5G                                               
&#9500;&#9472;sdg1                 SYSTEM                716M vfat     0FE6-9C83                            aee32a46-0ba7-44bf-9015-1c8a0ab01ee5
&#9500;&#9472;sdg2                                      80.9M vfat     D224-4637                            911ec5cd-151e-45b3-8668-49227963ae95
&#9500;&#9472;sdg3                 Windows              92.9G ntfs     94EA89EAEA89C946                     a1207cf5-2cb3-42cc-8d07-c29839f753d9
&#9500;&#9472;sdg4                                       540M ntfs     AE3A159F3A15659D                     1ce72b0e-9da1-4bf7-966e-ef36f3419eb4
&#9500;&#9472;sdg5                                      48.8G ext4     213fb185-2dc7-4eb2-ab58-fc2c36924d6f ebbbae4e-77b2-474d-9f2e-28f2869dfe2c
&#9500;&#9472;sdg6                                        84G ext4     7fff3192-2e26-4add-81d2-0ba7a8ee7601 606c2405-5ba0-42fa-bc4a-6b8cb77e8805
&#9492;&#9472;sdg7                 Windows RE tools      5.9G ntfs     14448A2C448A10A2                     a15361d7-819e-4485-8f09-d9b978980046
sdh                                         14.3G                                               
&#9500;&#9472;sdh1                 usbdata               1.1G ntfs     03479FBC56EAF4C5                     4b74152a-d56f-4c74-83a6-5615a32ae027
&#9500;&#9472;sdh2                                       977K                                               749d89df-8529-4d8b-89a0-0dfe16aeaf78
&#9500;&#9472;sdh3                 usbboot             244.1M vfat     4C2B-A37F                            273e49c9-e85a-43f4-a86e-47af010d77fb
&#9500;&#9472;sdh4      /cdrom     Kubuntu 21.04 amd64   2.8G iso9660  2021-04-20-11-02-45-00               0205fe1c-69b4-4964-8817-9743d5498080
&#9492;&#9472;sdh5                 casper-rw            10.2G ext4     8f72e95b-5f21-447e-8565-7f867cac7ca8 65897d1f-8af5-4914-911f-93d1cae4dea4
nvme0n1                                    238.5G                                               
&#9500;&#9472;nvme0n1p1            SYSTEM                716M vfat     CFCD-57FD                            aee32a46-0ba7-44bf-9015-1c8a0ab01ee5
&#9500;&#9472;nvme0n1p2                                 80.9M vfat     D224-4637                            911ec5cd-151e-45b3-8668-49227963ae95
&#9500;&#9472;nvme0n1p3            Windows              92.9G ntfs     94EA89EAEA89C946                     a1207cf5-2cb3-42cc-8d07-c29839f753d9
&#9500;&#9472;nvme0n1p4                                  540M ntfs     AE3A159F3A15659D                     1ce72b0e-9da1-4bf7-966e-ef36f3419eb4
&#9500;&#9472;nvme0n1p5                                 48.8G ext4     213fb185-2dc7-4eb2-ab58-fc2c36924d6f ebbbae4e-77b2-474d-9f2e-28f2869dfe2c
&#9500;&#9472;nvme0n1p6                                   84G ext4     7fff3192-2e26-4add-81d2-0ba7a8ee7601 606c2405-5ba0-42fa-bc4a-6b8cb77e8805
&#9492;&#9472;nvme0n1p7            Windows RE tools      5.9G ntfs     14448A2C448A10A2                     a15361d7-819e-4485-8f09-d9b978980046
kubuntu@kubuntu:~$ 

```

---

### Post by VMC on 2021-05-17
> **vidtek said:**
> VMC    I can't see what the set command says it scrolls to bottom too quickly :cry:

type "pager=1", then you will get a page at a time.

---

### Post by oldfred on 2021-05-17
You show all partUUID or guid as duplicate between sdg & nvme0n1.
And most of the UUIDs are the same.

You cannot have any duplicates.
UEFI used guid/partuuid to know which ESP to boot from. You see it in efibootmgr -v.
And other partitions are mounted normally by UUID.
Do not know how Windows works, but  Windows will not boot from an external drive anyway, so does not matter to change its UUID, in case you want to mount it. You do have to make sure fast start up is off and Windows will keep turning it on with updates.

I normally suggest a full install rather than a clone & then restore from your normal backup. That way, you know you have a good backup procedure since you still have older install to find any missing info. 

New install can take less time than trying to resolve these kinds of issues.
I have new install down to about 10 minutes from previously downloaded ISO, booted into RAM using grub2's loopmount. About 90% of configuration is by my install scripts which do take a bit. Or in about an hour I have a fully working an mostly configured system.

---

### Post by vidtek on 2021-05-18
> **oldfred said:**
> You show all partUUID or guid as duplicate between sdg & nvme0n1.
And most of the UUIDs are the same.

You cannot have any duplicates.
UEFI used guid/partuuid to know which ESP to boot from. You see it in efibootmgr -v.
And other partitions are mounted normally by UUID.
Do not know how Windows works, but  Windows will not boot from an external drive anyway, so does not matter to change its UUID, in case you want to mount it. You do have to make sure fast start up is off and Windows will keep turning it on with updates.

I normally suggest a full install rather than a clone & then restore from your normal backup. That way, you know you have a good backup procedure since you still have older install to find any missing info. 

New install can take less time than trying to resolve these kinds of issues.
I have new install down to about 10 minutes from previously downloaded ISO, booted into RAM using grub2's loopmount. About 90% of configuration is by my install scripts which do take a bit. Or in about an hour I have a fully working an mostly configured system.

Oldfred- Thanks for your time and effort.   I think I have not been clear in my intended use, I don't want to run both systems simultaneously.  What I do want is to be able to choose whether to boot from the NVME or SDD drives at boot time.  I can easily remove the SSD as it's in a quick caddy to boot from the NVME, but there seems no way to disable the NVME drive when I need to boot from the SSD.

The reason all the UUID's of the partitions are identical is because I cloned the NVME drive from the SSD originally with clonezilla (only changing the main UUID later).

If there is no way to readily disable the NVME drive at boot time I will just have to work round it.   I suspect newer motherboards will have better options for handling the way M2 drives work and will have the capability I seek.   

The other alternative would be a PCI caddy for the NVME drive I suppose......running out of PCI lanes.

I have my installs down to about 15mins too, but then there is mythtv install-the rest of the day for that!

Cheers Tony.

---

### Post by vidtek on 2021-05-18
> **VMC said:**
> type "pager=1", then you will get a page at a time.

VMC--Here are the results:  [ATTACH=CONFIG]288495[/ATTACH][ATTACH=CONFIG]288496[/ATTACH]

Cheers Tony

---

### Post by vidtek on 2021-05-18
Oldfred- Incidentally I have managed to get windows 10 to boot from my turbo leopard dual cloning external USB3 dock from my SSD drive.   That surely can be classed as an external drive?[ATTACH=CONFIG]288497[/ATTACH]

Cheers Tony.

---

### Post by oldfred on 2021-05-18
I know if directly to USB port, Windows knows.
Perhaps your dock is not then seen as a USB port?

Some UEFI have settings for drives. Its the same place as AHCI, RAID/Intel RST. It may have a "disabled" setting.
Also if drive is removed, it may forget UEFI boot entry or change entry to some sort of default. Often then have to use efibootmgr to recreate entry or reinstall grub (which uses efibootmgr) to add/update entry. UEFI often auto finds Windows, but not other operating systems.
Not sure with your ESP & duplicate UUIDs & GUIDs if it will work or you  still need some changes.

UEFI boots using GUID/partUUID to know which ESP. In ESP is a three line grub.cfg which has UUID of the install with the full grub.cfg for booting. It uses configfile to load another grub.cfg.

---

### Post by vidtek on 2021-05-18
> **oldfred said:**
> I know if directly to USB port, Windows knows.
Perhaps your dock is not then seen as a USB port?

Some UEFI have settings for drives. Its the same place as AHCI, RAID/Intel RST. It may have a "disabled" setting.
Also if drive is removed, it may forget UEFI boot entry or change entry to some sort of default. Often then have to use efibootmgr to recreate entry or reinstall grub (which uses efibootmgr) to add/update entry. UEFI often auto finds Windows, but not other operating systems.
Not sure with your ESP & duplicate UUIDs & GUIDs if it will work or you  still need some changes.

UEFI boots using GUID/partUUID to know which ESP. In ESP is a three line grub.cfg which has UUID of the install with the full grub.cfg for booting. It uses configfile to load another grub.cfg.

Sounds probable that is the main cause of not booting and going straight to the default  (really helpful) grub command prompt.

I do not have to re-install grub after this though-just removing the sata SDD lets mt boot normally from the nvme drive.

OK so let me see if I follow you properly.

You imply that if I could make changes to the grub.cfg file to point the EFI system to the correct system it may work?  

all I get now from the (really helpful) grub command prompt is you need to load a kernel first  (paraphrasing).

Right I'll give that a go and let you know how I get on.

By the way, I'm not an orphan, there are many many posts on the various forums bemoaning the fact that people cannot disable their M2 nvme drives easily.

Thanks again for your trouble oldfred!

---

### Post by vidtek on 2021-05-20
I tried editing the grub.cfg file. (In the SSD drive only) I changed the*** partition*** UUID for a new random one using the tune2fs command thus:```
tune2fs -U random /dev/sdg5
```

The blkid command now shows a different UUID :
```
root@linuxmint:/home/tony# blkid
/dev/nvme0n1p1: LABEL="SYSTEM" UUID="CFCD-57FD" TYPE="vfat" PARTUUID="aee32a46-0ba7-44bf-9015-1c8a0ab01ee5"
/dev/nvme0n1p2: SEC_TYPE="msdos" UUID="D224-4637" TYPE="vfat" PARTUUID="911ec5cd-151e-45b3-8668-49227963ae95"
/dev/nvme0n1p3: LABEL="Windows" UUID="94EA89EAEA89C946" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a1207cf5-2cb3-42cc-8d07-c29839f753d9"
/dev/nvme0n1p4: UUID="AE3A159F3A15659D" TYPE="ntfs" PARTUUID="1ce72b0e-9da1-4bf7-966e-ef36f3419eb4"
/dev/nvme0n1p5: UUID="213fb185-2dc7-4eb2-ab58-fc2c36924d6f" TYPE="ext4" PARTLABEL="kubuntu20" PARTUUID="ebbbae4e-77b2-474d-9f2e-28f2869dfe2c"
/dev/nvme0n1p6: UUID="7fff3192-2e26-4add-81d2-0ba7a8ee7601" TYPE="ext4" PARTUUID="606c2405-5ba0-42fa-bc4a-6b8cb77e8805"
/dev/nvme0n1p7: LABEL="Windows RE tools" UUID="14448A2C448A10A2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a15361d7-819e-4485-8f09-d9b978980046"
/dev/sdb1: LABEL="tv" UUID="6E66CE4866CE112F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="d9118715-a532-4b4f-8ba0-01fe09c65398"
/dev/sda1: LABEL="data" UUID="b0171cc5-2137-4789-9359-ee7315ade770" TYPE="ext4" PARTUUID="26d3afe3-d442-4c36-867b-7e48cb5671fe"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/sdg1: LABEL="SYSTEM" UUID="0FE6-9C83" TYPE="vfat" PARTUUID="aee32a46-0ba7-44bf-9015-1c8a0ab01ee5"
/dev/sdg2: SEC_TYPE="msdos" UUID="D224-4637" TYPE="vfat" PARTUUID="911ec5cd-151e-45b3-8668-49227963ae95"
/dev/sdg3: LABEL="Windows" UUID="94EA89EAEA89C946" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a1207cf5-2cb3-42cc-8d07-c29839f753d9"
/dev/sdg4: UUID="AE3A159F3A15659D" TYPE="ntfs" PARTUUID="1ce72b0e-9da1-4bf7-966e-ef36f3419eb4"
/dev/sdg5: UUID="70afb10c-38bf-4edd-a070-24b1b3ddb1b5" TYPE="ext4" PARTLABEL="kubuntu20" PARTUUID="ebbbae4e-77b2-474d-9f2e-28f2869dfe2c"
/dev/sdg6: UUID="7fff3192-2e26-4add-81d2-0ba7a8ee7601" TYPE="ext4" PARTUUID="606c2405-5ba0-42fa-bc4a-6b8cb77e8805"
/dev/sdg7: LABEL="Windows RE tools" UUID="14448A2C448A10A2" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a15361d7-819e-4485-8f09-d9b978980046"
```

Then I edited the grub.cfg to reflect the changes, (with 67 results for the search and replace of the partition UUID).

In the bios I selected to boot from the ssd drive

No change, the really helpful grub screen appears as usual.

Can you tell me why there seems to be 2 UUID's for the partition?  as thus:  ```
/dev/sdg5: UUID="70afb10c-38bf-4edd-a070-24b1b3ddb1b5" TYPE="ext4" PARTLABEL="kubuntu20" PARTUUID="ebbbae4e-77b2-474d-9f2e-28f2869dfe2c"
```

The tune2fs command only changed the first bit........

why are there two for each one?   Why on earth do they have to make things so bloody complicated?   GRRRRRRR!!!

---

### Post by oldfred on 2021-05-20
If removing SATA drive then allows NVMe drive to work, check your motherboard manual.
Many disable a SATA port to enable NVMe.

---

### Post by VMC on 2021-05-20
> **vidtek said:**
> ...

Can you tell me why there seems to be 2 UUID's for the partition?  as thus:  ```
/dev/sdg5: UUID="70afb10c-38bf-4edd-a070-24b1b3ddb1b5" TYPE="ext4" PARTLABEL="kubuntu20" PARTUUID="ebbbae4e-77b2-474d-9f2e-28f2869dfe2c"
```

The tune2fs command only changed the first bit........

why are there two for each one?   Why on earth do they have to make things so bloody complicated?   GRRRRRRR!!!

Are you referring to the PARTLABEL? If so read this:
[https://unix.stackexchange.com/questions/375548/what-is-uuid-partuuid-and-ptuuid](https://unix.stackexchange.com/questions/375548/what-is-uuid-partuuid-and-ptuuid)

The partition number is inside the PARTLABEL (see sudo blkid -p)

You just need to change UUID.

---

### Post by vidtek on 2021-05-20
> **oldfred said:**
> If removing SATA drive then allows NVMe drive to work, check your motherboard manual.
Many disable a SATA port to enable NVMe.

Been there done that oldfred....along with countless others  I spent a whole day trying all the various options....and gave up on that route along with everyone else!

---

### Post by vidtek on 2021-05-20
> **VMC said:**
> Are you referring to the PARTLABEL? If so read this:
[https://unix.stackexchange.com/questions/375548/what-is-uuid-partuuid-and-ptuuid](https://unix.stackexchange.com/questions/375548/what-is-uuid-partuuid-and-ptuuid)

The partition number is inside the PARTLABEL (see sudo blkid -p)

You just need to change UUID.

It still seems inordinately complicated for simply identifying a partition.   I suppose it's all because of different file systems and encryption methods.

I'll bet all the same info could be put in a simple 8-bit string.

Why do they make stuff so unnecessarily complicated...seems to me it is just designed to baffle the uninitiated.   The modern equivalent of religious "educated" men in the middle ages keeping everything in latin so their parishioners are in awe of them.

---

### Post by vidtek on 2021-05-23
OK guys, I finally have an answer.
I was playing around with gdisk  (as you do) and came across this little gem in the expert menu (highlighted in red).```
root@linuxmint:/home/tony# gdisk
GPT fdisk (gdisk) version 1.0.5

Type device filename, or press <Enter> to exit: /dev/sdg1
Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************


Command (? for help): ?
b       back up GPT data to a file
c       change a partition's name
d       delete a partition
i       show detailed information on a partition
l       list known partition types
n       add a new partition
o       create a new empty GUID partition table (GPT)
p       print the partition table
q       quit without saving changes
r       recovery and transformation options (experts only)
s       sort partitions
t       change a partition's type code
v       verify disk
w       write table to disk and exit
x       extra functionality (experts only)
?       print this menu

Command (? for help): x

Expert command (? for help): ?
a       set attributes
c       change partition GUID
d       display the sector alignment value
e       relocate backup data structures to the end of the disk
[COLOR="#FF0000"]**f       randomize disk and partition unique GUIDs**[/COLOR]
g       change disk GUID
h       recompute CHS values in protective/hybrid MBR
i       show detailed information on a partition
j       move the main partition table
l       set the sector alignment value
m       return to main menu
n       create a new protective MBR
o       print protective MBR data
p       print the partition table
q       quit without saving changes
r       recovery and transformation options (experts only)
s       resize partition table
t       transpose two partition table entries
u       replicate partition table on new device
v       verify disk
w       write table to disk and exit
z       zap (destroy) GPT data structures and exit
?       print this menu

Expert command
```

With this one change I was able to boot from the nvme or sata drive.

Steps to get it going:

[LIST=1]
[*]boot as normal from nvme drive
[*]after linux boots connect sata drive (I just connect via USB3 from my docking station)
[*]open command prompt and sudo or su for root prompt
[*]list disks  I use blkid
[*]once you know the disk device designation, open gdisk
[*]enter device name into gdisk prompt eg. /dev/sdg (as in my case)
[*]press x for expert menu
[*]then just enter the letter  f
[*]w for write your changes then q for quit out of gdisk
[*]I installed Grub Cutomizer as it make life so simple otherwise make your manual grub changes to add the sata drive to the boot menu
[*]reboot
[*]
[/LIST]

That's it, I was even able to once again boot my windows 10 installation from the sata drive via usb3 connection from my turbo lepoard docking station.  So much for Microsoft's much vaunted "you can't boot windows form an external drive mantra".  I will take a video of the booting process and upload it to my mega cloud storage if anyone is that interested, I'll edit this and post the link [here]("https://mega.nz/file/psgCBDzZ#NA_X68_rLmoZW8KiqeVqV8mTXVNuxXmoW5juCVrtM9A") when I've done it.

I want to thank all for their help with this, particularly VMC & OldFred for pointing out the issue was probably the partition UUID's. Spot on guys!:KS

---

