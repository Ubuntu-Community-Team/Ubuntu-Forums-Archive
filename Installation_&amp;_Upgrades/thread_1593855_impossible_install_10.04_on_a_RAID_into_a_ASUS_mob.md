---
title: "impossible install 10.04 on a RAID into a ASUS mobo P7H57-D EVO"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by PinguinZeneize on 2010-10-11
hello everyone!
I'm new to the forum and I hope I have done the right steps.
I would like to report the following problems to see if anyone could help me out, I am really in need.
I assembled a computer with an Asus motherboard P7H57D-EVO-V which I connected 2 Hard Disk Western Digital 1 TB each, after you install a microprocessor i7-860.
(Meanwhile they have already stumbled across the sad surprise of not seeing the onboard video work for reasons required by the video card GPU and managed by i7! And I have seen so compelled to take up an expansion slot with an additional video card - avoid Comments about this because I believe that for a brand like ASUS that this is just a bad picture! and then we are a different matter.)
Now I tried to write to ASUS to get explanations from them and understand even if I have to give up the use of integrated RAID, since I'm not able to install linux version Ubuntu 4.10 discs mounted in RAID1 configuration.
I state that I have already updated the BIOS to the latest version possible and that you followed the procedures described in the manual regarding the qualification of the operator and the RAID nelBIOS configuration of RAID 1 - Mirroring - through the proper configuration utility.
In fact, the Ubuntu installer correctly recognize 10.04 one logical disk, given by the raids of the two discs, with a name and a whole lot of the value of 1 terabyte, only in the configuration partition and installing the software indicates several configuration errors, often different, such as to suggest some incompatible drivers or, worse, a hardware failure, unfortunately, we would be more inclined to believe this is a second chance.
Only once has apparently completed the partition, formatting, and install grub but was then mounted on sda1 instead of logical drive raid, and then restart did not work.
Before resorting to warranty replacement card I would understand if indeed there are some incompatibilities reported with regard to what or if I made mistakes along the way.
Maybe you would have some evidence or to suggest alternative or the feeling that there is already about half-way somewhere on the net and have not yet been able to find it?


Thank you all.
I am looking forward!

:-)

---

### Post by ronparent on 2010-10-12
You had perhaps verify that gparted sees raid drives in your release of Ubuntu. Booting to a live cd start gparted. It should show the raid drive. If it doesn't quit and install kpartx (that install will persist only for that live cd session). That is needed in 10.04 (as opposed to the later release 10.04.1) to be able to see a raid drive. Once you are able to see the raid with gparted, hit the install icon on the desktop and run the install. You should now install to the raid 1.

---

### Post by PinguinZeneize on 2010-10-14
thanks for the answer!
In fact I was amazed that with Disk Utility saw the only RAID drive while with gparted saw the raid as two separate drives.
I tried to download the version 10.04.1 and - perhaps because it is the 64bit version? - Continues to be the same situation. However, installing "blessed kpartx" something has changed!
gparted  continues to show me the two separate drives "sda" and "sdb" but I also  see the raid unit. editing and formatting partitions I do not have  more errors.
Unfortunately, however,  have not yet reached its destination: launching the installation program  icon does everything perfectly, but when the pc restarts  not find the operative system on boot disk.
I  specify that during installation I set in the advanced options to  install grub raid unit information, (but not in its own partition like when  you want to install grub on the boot sector of a fisical drive).
Thanks again!
I'm waiting for your new help
:)

---

### Post by ronparent on 2010-10-14
I didn't mention it because the grub install often works (but then again sometimes it doesn't). You merely have to do the grub 2 reinstall to fix it as described here: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Just remember that the grub install command has to refer to the raid array root (the first item listed after /dev/mapper/control) to install the boot loader to. Glad to hear it is working for you. Post again on any problem.

---

### Post by PinguinZeneize on 2010-10-15
So, if I understand correctly, I should 
not install it in **/"raiddisk"/boot 
but I have to install it in **/"raiddisk"/

I'm looking for the GRub's link

;)

Thanks of all

---

### Post by ronparent on 2010-10-15
If you examine the reference I gave you, The reinstall of grub (so you can boot with it) is done in three steps using some terminal language. In the 1st method described you are instructed to do:
> sudo fdisk -l
This is simply to identify where the name of the partition where you installed Ubuntu. You can additionally verify the name of the raid partition by doing:
> ls /dev/mapper
This will list all of your raid partitions (ignore /dev/mapper/control) begining with the raid array name and followed by the individual raid partitions. When you have identified your raid partition you mount it:
> sudo mount /dev/mapper/<TheNameofTheRaidPartitionYouInstalledTo>
It will be a long name. Next you reinstall grub to boot from your raid array by:
> sudo grub-install --root-directory=/mnt/ /dev/mapper/<RaidArrayName>
With everything done as I outlined you should now have a bootable system. Good luck.

---

### Post by P4man on 2010-10-15
You dont have a real hardware raid; you have a so called fake raid (aka bios raid). What you need to understand is that the only purpose of a bios raid is to allow windows to boot from a raid.

Believe it or not,  Windows cannot boot from a software raid without the help of the bios. Thats only ONLY reason for a bios raid. Windows can create raid arrays without the help of the bios (so called dynamic disks) and those work fine, but it can not boot from it.

Bios RAID is basically a windows RAID driver in firmware. Its an ugly crutch, because a fake raid ties your raid completely to your motherboard and even to your bios (version). If your motherboard dies, you may not be able to rebuild the fakeraid on a different motherboard. Think about that before using it. It has all the drawbacks of a hardware raid (except price that is), but none of the performance boost since none of the workload is offloaded from the CPU. 

Now Linux has no such problems. It can install on 2 (or more) regular sata disks configured as software raid and achieve the same result. Only better, without all the drawbacks, not tied to the bios and without the performance hit. Thats right, performance hit. A bios raid doesnt speed things up compared to a pure software raid, it slows it down if its an external "controller" chip and you are not using the sata controller integrated in the southbridge.

Now Ubuntu *can* install on such a fakeraid. Actually, not really, but it can read the settings you configured in the bios and then create a dmraid with those same settings. Its rather pointless, but serves people who do not know better and think their "onboard raid controller" actually gives a speedboost.

I would advice you to just forget the fakeraid for ubuntu. You dont need it. If you have dedicated RAID sata ports, dont use them. The other, regular sata ports are faster! Then do a pure software raid, easiest is probably installing form the alternate CD.

---

### Post by PinguinZeneize on 2010-10-15
Thanks to you both
Thanks to Ronparent surely find the solution to my original question, that I want to try to pride;
Thanks to P4Man I'll have to re-evaluate if my initial question really is the best solution for me .
Perhaps  the most just and practice will be to mount a single disk for the  operating system and two others to set up RAID in Linux through  software. So all three are configured as SATA drives in AHCI without RAID in the BIOS.
Thank you again!
Truly a great experience this interview on ubuntuforum! very constructive!
;)

excuse me for my english but I'm italian

---

### Post by P4man on 2010-10-16
> **PinguinZeneize said:**
> 
Perhaps  the most just and practice will be to mount a single disk for the  operating system and two others to set up RAID in Linux through  software. So all three are configured as SATA drives in AHCI without RAID in the BIOS.


You might as well mirror the OS drives too. Or rather, install the OS on the RIAD.  Its only a few gigabytes, and its rather convenient if one drive dies that you can still boot. Just know that the easiest way to install ubuntu on a raid is the alternate CD:
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

That installer doesnt have the flashy GUI of the normal livecd, but it certainly gets the job done.

---

