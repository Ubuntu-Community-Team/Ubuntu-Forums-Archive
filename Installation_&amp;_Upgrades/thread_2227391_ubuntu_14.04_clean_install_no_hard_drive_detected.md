---
title: "ubuntu 14.04 clean install/ no hard drive detected"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by paul146 on 2014-06-01
Good afternoon,

I recently completed my new PC build and wanted to use Ubuntu. I have created a disk image on my usb using ubootin

. I can use Ubuntu live, go on internet and everything works.

 When I try to "install Ubuntu" it says I have no hard drive space available. I have a new unsued 128gb SSD and two 1tb hard drives. My Bios recognizes all hard drives... help:(

I have never used windows or any other OS on this computer. Do I need to Format the SSD ad HDD before I use them?

thanks,

Paul

specs:

MSI z97-gd65 motherboard
MSI  geforce gtx 760 4gb video card
16BG corsair ram
intel i5 4670k (not overclocked yet)
corsair 860i power unit
corsair h110i cooler
corsair 128gb ssd
2 western digital 1tb hdd  (i have unhooked these to no avail)

---

### Post by oldfred on 2014-06-02
I do normally partition in advance as I do not want just / (root) & swap especially on larger drives. And I now partition all new drives with gpt, but since I only have BIOS I have to have a bios_grub partition.
Your system will be UEFI so you can install in either UEFI or BIOS, but only if also installing Windows in BIOS mode would I keep the Windows boot drive as MBR(msdos).

What does gparted show?

And if just a data drive you must partition before formatting and copying data.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Food for thought:
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by paul146 on 2014-06-02
> **oldfred said:**
> I do normally partition in advance as I do not want just / (root) & swap especially on larger drives. And I now partition all new drives with gpt, but since I only have BIOS I have to have a bios_grub partition.
Your system will be UEFI so you can install in either UEFI or BIOS, but only if also installing Windows in BIOS mode would I keep the Windows boot drive as MBR(msdos).

What does gparted show?

And if just a data drive you must partition before formatting and copying data.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Food for thought:
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.



i am obviously over my head. I have no Idea what any of that means. All I know is that i can log onto Ubuntu with a "cd image' on my flash drive, but i cannot install it onto my new computer that has never been used before. I think it it is a software issue that i cannot fix. My bios shows the 128 SSD, but i cannot save to it while in the "live mode" with ubuntu.

If you know how to add hard drives to the live version, show me which section of the forum I need to read. OR if i should just buy windows...

thanks for the reply,


Paul

---

### Post by paul146 on 2014-06-02
i am reading the tutorial stuff now... I will update if i come across something that helps me without buying windows right away.

thanks,

Paul

---

### Post by oldfred on 2014-06-02
From the live installer, load gparted and see if it sees drives.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by paul146 on 2014-06-02
it only shows the USB stick that i am currently using right this moment on the internet with.... does not show any other drives ( but motherboard bios does...)

in gparted ; /dev/sda (1.91Gib) is what it says. and under devices, it only shows the USB. I have (while the computer was off and unplugged) disconnect all other drives power and sata cables except for the SSD, I have tried the HDD as well instead of the SSD, still no luck. i tried to refresh in gparted and it does not load anyting but the usb.

---

### Post by oldfred on 2014-06-02
Some UEFI/BIOS have settings to turn on drives?

What setting in BIOS is hard drives. It should be AHCI, or at least LBA which may be called large for large block allocation. But not IDE nor RAID. Some new systems may have Intel SRT type settings also which should be off.
Fast boot should be off.

You say motherboard is z99, is it really a new z97?
Different brand, but same Intel chipset, so it should work.
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

---

### Post by paul146 on 2014-06-02
i will check

---

### Post by paul146 on 2014-06-02
[COLOR=#000000]
It did check and the SSD is not disabled. I did not see the AHCI.  It did say UEFI or LEGACY+UEFI (or something like that). is that what you are talking about? I clicked the non Legacy option and my usb, dvd, and hard drive dissapeared from the boot menu. so i put it back to the way it was. when i boot without the usb it just says" no boot drive found" insert boot key or device and hit any key and it still does not boot. keep usb in and "reset" with button and ta-da Ubuntu loads. try to install, not enought hard drive space. 

Maybe it is my motherboard is so new that it is not 100% compatible. which is frustrating because i am using it right now......:mad:[/COLOR]

---

### Post by fantab on 2014-06-02
> **paul146 said:**
> Good afternoon,

I recently completed my new PC build and wanted to use Ubuntu. I have created a disk image on my usb using ubootin

. I can use Ubuntu live, go on internet and everything works.

 When I try to "install Ubuntu" it says I have no hard drive space available. I have a new unsued 128gb SSD and two 1tb hard drives. My Bios recognizes all hard drives... 

Boot in Live Ubuntu, open Terminal [ctrl+alt+T], run the following commands and post its output here:

```
sudo parted -l
sudo fdisk -l
```

The output will tell us how your SSD and HDDs are being read and seen as by Ubuntu...

AHCI is an option for SATA MODE in UEFI or BIOS. Usually the options include, IDE, AHCI and RAID...

---

### Post by oldfred on 2014-06-03
For security reasons many new systems also have a UEFI setting to turn on or turn off USB ports in UEFI mode. Old BIOS/CSM allows it since that was normal with BIOS.

These new UEFI systems have many settings and some that may not seem relevant make a difference.

This shows AHCI as a setting, but he goes thru things very quickly. First 4 min show main settings.
[http://www.youtube.com/watch?v=VTD_fBj12tA](http://www.youtube.com/watch?v=VTD_fBj12tA)

You have a lot of settings that I think you may have to change, but do not know what defaults are.

---

### Post by paul146 on 2014-06-03
I will try that when I get home. 

thank you,

Paul

---

### Post by paul146 on 2014-06-03
> **oldfred said:**
> Some UEFI/BIOS have settings to turn on drives?

What setting in BIOS is hard drives. It should be AHCI, or at least LBA which may be called large for large block allocation. But not IDE nor RAID. Some new systems may have Intel SRT type settings also which should be off.
Fast boot should be off.

You say motherboard is z99, is it really a new z97?
Different brand, but same Intel chipset, so it should work.
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

THANK YOU!!!!

I found the AHCI mode you were talking about, totally missed it. It is changed and i am using the computer now. It is updating in the background. This is my first PC build and first time using a Linux based program. I dove in head first.. lol


With support like this it is no supprise how popular this is becoming.

I will read the beginner threads whenever i get a chance so I can use it to the fullest.

problem solved

---

