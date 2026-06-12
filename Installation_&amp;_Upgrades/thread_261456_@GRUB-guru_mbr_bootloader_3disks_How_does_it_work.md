---
title: "@GRUB-guru mbr bootloader 3disks How does it work?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by frafu on 2006-09-20
Hello, 



First of all, my box is running, so I don't need any troubleshooting help. But there are different aspects of the boot cycle that are not yet clear to me. 



Here is part of the setup of my celerenbox: 

/dev/hda
/dev/hdb
/dev/sda

sda1: primary partition with ubuntu desktop i386
sda2: extend partition containing sda5
sda3: primary partition with a second installation of ubuntu desktop i386
sda4: primary partition without system 
sda5: swap
hda1: primary partition without system 
hdb1: primary partition without system 




When I put the sda-device in the first position in the bios it always uses menu.lst from sda1, regardless of me using ubuntu on sda1 or sda3.

When I put the hda-device in the first position in the bios it always uses menu.lst from sda3, regardless of me using ubuntu on sda1 or sda3. I suppose it is because its mbr contains a bootloader calling grub in sda3. Can you confirm? 

When I put the hdb-device in the first position in the bios I get a black screen with a blinking curser. I suppose it is because it does not have any bootloader on it. Can you confirm? 

If there is no bootloader on the first partition, should the boot cycle not continue the search on the next partitions of the disk and if unsuccessful carry on searching on the next disks? 




When I look in device.map in sda1, the sda device is mapped to hd0; when I look in device.map in sda3 the sda device is mapped to hd2. I suppose this has to do with the order of the disks in the bios. Could you confirm? 

I tried to change device.map and menu.lst from sda1 in order to make the hd0, hd1 and hd2 entries match those on sda3; but it did not work, so I put them back to their previous state. Is the device.map file not used? Is there a way to make the device.maps match? Moreover, does it make any sense of wanting to make them match? 




Most important: 

How can I check whether a mbr contains a bootloader and especially where that bootloader points to? 

Where are the mbrs? 
- Is there a mbr (even if it does not contain a bootloader) on every partition or only on partitions that are primary? 
- Is there a mbr on each harddisk beside those in the partitions? (I have seen grub commands with hd(x) instead of hd(x,y))


Many thanks for any help and explanation or link about how it works? 


frafu

---

### Post by zxee on 2006-09-20
I've done a lot with grub including multibooting over a dozen distros-but don't think of myself as an expert. There's always more to learn and not enough time.
The mbr is a designated section (like a 1st tiny partition that hold the bootloader) [http://www.webopedia.com/TERM/M/MBR.html](http://www.webopedia.com/TERM/M/MBR.html)
Slave drives don't generally have a mbr because the master does. 
Most importantly you can install grub to the root partition and then use grub to chainload from that partition-which may be what you want to do? 
However you can't easily just change bios setting and have that work the way you want  without also changing your /etc/fstab settings too. All that seems like a lot of work to me if what you want is more flexibility-I think you may need to decide how and what you want to boot before you install/create partitions.
The questions about the device map: Yes that is set up when grub installs and it "reads" the hard drive order in the state it is then-which is why altering the bios doesn't work. 
There is a newer version of grub i.e grub2 planned but not yet released. Also there are other bootloaders [http://linux.softpedia.com/get/System/Boot/Gujin-3210.shtml](http://linux.softpedia.com/get/System/Boot/Gujin-3210.shtml) IMO isn't as hampered by some of the restrictions of grub or lilo.

---

### Post by frafu on 2006-09-20
Thanks for your reply. 

```
 
Most importantly you can install grub to the root partition and then use grub to chainload from that partition-which may be what you want to do?

``` 

What do you mean by root partition? sda1? sda3? 
Isn't chainloading used to boot an operating system that is not supported by grub? I don't have Windows on my computer; I have 2 ubuntus on it. 



In fact, what I am trying to do is to understand how it works, so that I can change things if I want/need to. 


When booting, the menu.lst from sda1 is used. The entries in this menu.lst are hd(0,0) and hd(0,2).

However, when I enter the command find /boot/grub/stage1, it outputs hd(2,0) and hd(2,2).

The sda disk being the first boot device in the bios, should it not be hd(0,n)? Why does find return hd(2,n)? 

The entries of the menu.lst on sda3 are hd(2,0) and hd(2,2). Could it be that the find command uses the device.map from sda3?


Is there a way to make the computer use the menu.lst from sda3?
Is there a way to make it use the names hd(0,n) instead of hd(2,n)? 


frafu

---

### Post by frafu on 2006-09-21
I changed groot=hd(2,2) to groot=hd(0,2) in menu.lst from sda3. Now, when using 'sudo update-grub' it uses hd(0,n) instead of hd(2,n) to update menu.lst.

However, when I give grub the command 'find /boot/grub/stage1' it still outputs hd(2,n). How can I make it output hd(0,n)?

frafu

---

### Post by zxee on 2006-09-21
> **frafu said:**
> I changed groot=hd(2,2) to groot=hd(0,2) in menu.lst from sda3. Now, when using 'sudo update-grub' it uses hd(0,n) instead of hd(2,n) to update menu.lst.

However, when I give grub the command 'find /boot/grub/stage1' it still outputs hd(2,n). How can I make it output hd(0,n)?

frafu

As I understand it sata drives, in ubuntu & maybe other debian based distros are always listed after ide/ata. Someone else care to comment/correct that?

As far as chainloading. I've used it with many linux distros so I know it works. And yes the root partition is the partition you have your system installed on. 
You can, using the alternate cd, install to a partition instead of the mbr, but you would still have to have a bootloader in the mbr to hand off i.e chainload to the grub installed on the partition.

---

### Post by frafu on 2006-09-21
Thanks again for your reply. 

```
 
And yes the root partition is the partition you have your system installed on. 

``` 

I have 2 systems: the first ubuntu on sda1; the second ubuntu on sda3. Does this mean that I have 2 root partitions on sda? Or is only sda1 a root partition because grub using menu.lst from sda1? 

```
 
As far as chainloading. I've used it with many linux distros so I know it works.

``` 

Why use chainloading to load a linux system? I have ubuntu from sda1 and ubuntu from sda2 in the menu.lst the is saved on sda1. As far as I can tell, there is no problem booting both systems (of course not at the same time. 

```
 
As I understand it sata drives, in ubuntu & maybe other debian based distros are always listed after ide/ata.

``` 

In fact I thought that if sda was mapped to hd0,there would be no problems if I later add another harddisk. If it is not possible to map sda to hd0, will I not get problems when I later add an ide drive? Because if I understand it correctly, adding another ide drive will change the mapping from sda from hd2 to hd3? 

Thanks in advance for any clarification. 

frafr

---

### Post by zxee on 2006-09-21
2 different systems=2 different root partitions. I'm not sure what you mean about "grub using menu.lst from sda1" Was the ubuntu installed to sda3 installed first and then your 2nd install saw the sda3 install and just added it? I don't know and that's why I use chainloader it's easy/lazy I have a grub that runs from my mbr-I've had the installer(s) of my others distros install to the partition and then I just add the title and chainloader commands to my  "master" grub-no problems.
Adding an ide drive now, to your system, will require some more editing of menu.lst-I've never had to change mapping though, and I have moved drives. I mostly found that I needed to edit my fstab, but your system and experiance may differ.

---

### Post by frafu on 2006-09-22
```

I'm not sure what you mean about "grub using menu.lst from sda1"

```
each of my 2 systems have a /boot/grub directory with a menu.lst file and at boot it always uses the menu.lst on sda1.

```
 
Was the ubuntu installed to sda3 installed first and then your 2nd install saw the sda3 install and just added it?

``` 
I first installed the system on sda1,then on sda3. But at some point I completely erased an ide disk (by changing its disk label from mac to msdos) and afterwards the system did not boot anymore. Then I fiddled a bit around with grub and the disk order in the bios, which solved the problem. Unfortunately I don't remember exactly what I did. 

```
 
I have a grub that runs from my mbr

``` 
Do you mean stage 1 of your grub is in the mbr? 
Where is your "master grub"? 

```
 
I've had the installer(s) of my others distros install to the partition and then I just add the title and chainloader commands to my "master" grub-no problems.

``` 
Did you tell to the installer of the other systems not to install grub? 
I also have to edit menu.lst manually because an update-grub does not see the kernels on the other partition. 

frafu

---

### Post by zxee on 2006-09-24
Grub and other bootloaders including windows bootloader install data to the mbr-otherwise they wouldn't boot. My master grub is from slackware on my 1st ide drive-so all the other distros (7) run through that grub using the chainloader command. I did have the installers of the other distros install grub-as I said previously-to the partition(s) or root partition that those distros were installed to-rather than the mbr. Hope that helps.

---

