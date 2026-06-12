---
title: "raid0 with win and ubuntu BUT ubuntu fail to enter system"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by KingOfFright on 2010-05-30
Hi, all. Here is my case:
I using nvidia motherboard raid0, and I install a win system, then install ubuntu 10.04. The ubuntu is install in logical partition(I have 3 parition in win, all of them already in main parition). I use EasyBCD to lead ubuntu, in fact, I had tried to install ubuntu's grub, but after installation, I still get a windows bootloader(I had tried to leave the grub position to /dev/sda or the / partition, but nothing change). Using EasyBCD 2.0 beta can use the grub2 function to lead ubuntu to the select menu, but after I press enter ubuntu, it stuck at the screen, and not moving. Here is the pics I cut when I enter ubuntu using text mode, could someone can give me a hand?
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105265&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]


[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105266&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]


[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105264&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]


[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105267&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]


*
*
this one is when it stuck there, I press the power button, then it shut down the pc.
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105268&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]

---

### Post by KingOfFright on 2010-05-30
wow... fall to the bottom...:mad:

---

### Post by cj.surrusco on 2010-05-30
I've been trying to setup raid for a while too, without success. Grub has trouble setting up on RAID 0. You have to install grub to a non-raid partition for boot, I believe.

---

### Post by KingOfFright on 2010-05-30
Thx for your reply. You mean the grub2 can't work with raid0? I can enter the grub2 menu after the ubuntu's installation, could it be a prove of success with grub2 installing in raid0? In fact, I already see some one post a  installation of 10.04 at a raid0. :)  The post said you need to manually install the grub2 when installation is finish using the livecd.
> **cj.surrusco said:**
> I've been trying to setup raid for a while too, without success. Grub has trouble setting up on RAID 0. You have to install grub to a non-raid partition for boot, I believe.

---

### Post by ronparent on 2010-05-30
The grub2 can work with raid 0. The problem is that without intervention the installer tries to install the mbr on sda and fails. The mbr for grub2 has to be installed on the root symbolic link for the array to work. That is named in /dev/mapper/. The root represents the entire array and is the named one without a number at the end (the numbered ones are the individual partitions one of which is the one the ubuntu is installed to). The grub setup is to write the grub mbr to that location (ie /dev/mapper/<yourRaidArray>0.

---

### Post by KingOfFright on 2010-05-31
I had try to change the grub path when I press then install button in advanced(I know there is no /dev/sda). I am not quite understand what you say the grub2 path in raid0 should be, for my case, after I ls -l /dev/mapper, it shows and my / install at 09
[IMG]http://forum.ubuntu.com.cn/download/file.php?id=104177&t=1&sid=c9580e07d1d6057bde3449752c514a05[/IMG]

---

### Post by KingOfFright on 2010-05-31
up~

---

### Post by ronparent on 2010-05-31
isw_hfbfdhhad_0

---

### Post by KingOfFright on 2010-05-31
Hi, thx for you reply. It doesn't work, neither. Still stuck on the screen, but I can enter the system by recovery mode, then I think it should be the drivers problem. Maybe I will wait next version.> **ronparent said:**
> isw_hfbfdhhad_0

---

### Post by ronparent on 2010-06-01
Also consider a manual update from a terminal, or running dpkg in the recovery mode. For some reason that last option has consistently upgraded me to the .22 kernel. There is an off chance that an update will correct bugs. 

One of the problems I see with raid implementation is that it has been inconsistent between releases. also as we see from your results what works with one chipset doesn't work with another?

---

### Post by BoneKracker on 2010-06-01
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)


[COLOR="White"].[/COLOR]

---

### Post by KingOfFright on 2010-06-03
Hi, me again, today I research 'ubuntu 10.04 raid0' again and back to this post, and I found something I miss to mention:
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=105267&t=1&sid=f825afe3f38723905f1e7b59812eb255[/IMG]
In this pic I can see that the root is set to (hd2,6), what did it means? In fact, the floor 6 devices result was refer to others, I didn't  capture mine, but I could write down:
control
nvidia_bcidecde -> 320GB
nvidia_bcidecde1 ->NTFS, system win7
nvidia_bcidecde2 ->NTFS
nvidia_bcidecde3 ->NTFS
nvidia_bcidecde5 ->Swap
nvidia_bcidecde6 ->Ext4, /
 
you could tell that parition 5 and 6 are in locigal partitions(there should be a nvidia_bcidecde4 contains them, I use the disk utility to create these linux partitions, because the installer could not do the formation when installing, I need to pre-format them.), I had try to install the grub to nvidia_bcidecde, nvidia_bcidecde6, but nothing change. today I see the root(hd2,6), is that correct? I only have two hard disks, how could it be hd2?:confused:
> **ronparent said:**
> Also consider a manual update from a terminal, or running dpkg in the recovery mode. For some reason that last option has consistently upgraded me to the .22 kernel. There is an off chance that an update will correct bugs. 
 
One of the problems I see with raid implementation is that it has been inconsistent between releases. also as we see from your results what works with one chipset doesn't work with another?

---

### Post by KingOfFright on 2010-06-04
up~!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by KingOfFright on 2010-06-04
up and up~!

---

### Post by ronparent on 2010-06-07
Sorry I didn't get back to you - have been away for a few days.

The success you may have in installing grub depends on how your bios is setup, among other things. Mine was setup to boot from grub installed in the mbr of a non-raid sata drive. I experimented with installing to the mbr of my raid and in my case it worked like a charm.

I worked from the booted system and used the terminal command **sudo grub-instal /dev/mapper/nvidia_aehbdfib**. This installed the grub2 to the raid array mbr. I then found and selected the option in bios to boot to that raid array as a boot choice. The next time I rebooted, that is the grub mbr where I booted from with no problems.

You may look at Hermanns site to learn everything you want to know about installing and using grub2 and then some: [http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html](http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html)

Good luck.

---

