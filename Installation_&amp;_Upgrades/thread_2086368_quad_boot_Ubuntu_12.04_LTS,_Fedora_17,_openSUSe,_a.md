---
title: "quad boot Ubuntu 12.04 LTS, Fedora 17, openSUSe, and Slackware"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by disturbed13 on 2012-11-20
okay so i was in the middle of trying to make a quad boot rig
with Ubuntu 12.04, Fedora 17, openSUSE, and Slackware
i installed Ubuntu like normal, and had it only use 1/4 of the hard drive.
it said that i didnt have any swap space but that i would still run
and it did, so i restarted and let it boot from the drive
installed 400 somethin updates then shut it down and installed Fedora 17
thats when $h!t hit the fan
i told it to use the free space on the HDD and partion off 40010 MB just like Ubuntu did
it complained about the same thing
and now when it boots it only sees Fedora in the GRUB menu

any words of wisdom would be greatly appreciated
and how can i fix this?
also when i go to install the other 2 what do i have to do differently?
thanks

---

### Post by Mr_JMM on 2012-11-20
Personally I would have installed Ubuntu last but that's because my main distro is Ubuntu.

Have I done this before? One laptop currently has (on a single hard drive):
Ubuntu 64 bit
Ubuntu 32 bit
Fedora 17
OpenSuse 12.2 (KDE)
Lubuntu
Linux Mint14 64bit
Linux Mint Debian


I would also advise partitioning the hard drive FIRST, it makes it a lot easier.

You now need to check how many partitions the Ubuntu and Fedora installs have created.

Please supply content of ```
sudo fdisk -l
```

You need to update grub on what ever distro you want to be in control of boot and grub. To that point you may as well install themn all now then worry about it if the partitioning is ok.

---

### Post by oldfred on 2012-11-20
I have not installed Fedora, but it normally defaults to a separate /boot and LVM for the main install. If multi-booting the LVM adds complexity and gives none of the advantages of LVM in the way of moving partitions around.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
    
Some have posted just to install Fedora to a preformatted partition.

You can install Ubuntu's grub2 with Boot-Repair or the Ubuntu liveCD. If Fedora is in the LVM you have to add the lvm2 driver & mount the Fedora partition before running a sudo update-grub to get os-prober to find the Fedora partition.

       [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajgreeny on 2012-11-20
I think oldfred has hit the nail on the head.  I installed fedora some time ago as a dual boot, or that was my intention, with ubuntu, and found that it completely messed up the two hard disks' partitions with the LVM that it uses by default.  Luckily I made it put grub on the second of the two disks, keeping ubuntu's grub on the first disk, so I could still use both OSs by booting to the appropriate disk.

Ubuntu's grub did not see fedora, and I could not mount the fedora partition at all in ubuntu until I asked on this forum and was informed about LVM and the problems it added.  I have since tried fedora a few more times, most recently fedora 17, but then I manually partitioned, just as I do when I install ubuntu, so did not have the LVM problem.  However, it did not stay on the machine for long; I just could not get to grips with the fedora way of doing things, particularly its package management, which I found unwieldy and not as good as apt-get etc etc

---

### Post by disturbed13 on 2012-11-20
so why does the Swap partion have to be a primary partion?
it wont let me make the last little 4 GB part of my HDD a swap partion

---

### Post by Mr_JMM on 2012-11-20
Swap doesn't have to be a primary. I have a system where swap is logical (within an Extended) partition and seems to work fine.

I can't answer you much more since you, for what ever reason, have decided not to share the layout of your hard drive.

---

### Post by disturbed13 on 2012-11-20
i was busy installing the other OS to the HDD and posted it from my Vista machine
i have my linux machine on the VGA input of my primary monitor
and running FF on my second 22" on my Vista machine

as requested

```

[sudo] password for allen: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7b7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    78145535    39071744   83  Linux
/dev/sda2        78145536   160086015    40970240   83  Linux
/dev/sda3   *   160086016   243978239    41946112   83  Linux
/dev/sda4       243980288   304771303    30395508   83  Linux
[allen@linux ~]$ ^C
[allen@linux ~]$ 

```

---

### Post by disturbed13 on 2012-11-20
and this is what i face now
its attached

---

### Post by Mr_JMM on 2012-11-20
Sorry for delay... Dinner beckoned.

You can't have more than four primary partitions.

Your choices are:
1. Up to four primary
2. Up to three primary + an Extended.

Within an extended partition you can have over 100 "logical" partitions. I'll admit I'm not knowledgable with LVM partitions as someone mentioned but doesn't look like that's an issue.

If I were you I'd do this:
Start again.
You can though keep whatever is in sda1 (guessing ubuntu). 
Delete the others.
Create a swap as sda2 (you don't have too, it can go anywhere within the extended partition...).
Create an extended partition with the remaining space.
Add as many partitions within that as you need.

Will attach example in a minute.

---

### Post by disturbed13 on 2012-11-20
sda1 is Ubuntu
oddly enough openSUSE can see Fedora 17 and Ubuntu and makes them available in a grub menu
sadly i dont see my Slackware install
but im not going to cry over spilled milk
im thinking ill just delete the slackware partiton
and make an extended partition for storage.... or something

---

### Post by Mr_JMM on 2012-11-20
Sometimes, before a distro can be seen (for me it's always Fedora) the partition has to be mounted (from which ever distro is running grub mbr) before updating grub. It might be worth a try with Slackware.

Splitting the drive in four without swap is Ok, it should work OK (I'm not aware of any distro that will refuse to run without it), maybe, I just prefer to have it there.

Extended partitions really will allow you set things up great and you can still, as you say, have a separate partition for /home etc.

---

### Post by oldfred on 2012-11-20
Does Slackware still use Lilo? You may be able to add a chain load entry somewhat like a Windows chain load entry to boot Slackware.

The lilo menu entries may just be enough different that os-prober is not able to translate, but chain load does not care.

       # Chainload another bootloader
menuentry "Chainload partition 3" {
set root=(hd0,3)
chainloader +1
}

    
You may need insmod or some other settings, but above boot stanza just may work.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

---

