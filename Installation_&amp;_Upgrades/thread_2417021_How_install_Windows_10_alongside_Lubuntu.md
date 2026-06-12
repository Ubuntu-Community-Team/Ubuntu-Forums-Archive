---
title: "How install Windows 10 alongside Lubuntu?"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by tackskull on 2019-04-19
Hi there,

I have my laptop with 1tb hdd. Here I have installed Lubuntu but I have decided to reinstall windows 10 keeping Lubuntu. 
Now, with an usb live of Ubuntu I used Gparted to resize the partition, giving 250gb to Lubuntu and 750gb of free partition where I would like to install windows 10. 
So there is some kind of process I shouod follow to install windows alongside Lubuntu or I have just simply install windows on the 750gb partition? I readed around the internet that installing windows the grub will have problems and Lubuntu would not be working anymore

---

### Post by oldfred on 2019-04-19
UEFI or BIOS or more correctly is drive gpt partitioned or MBR partitioned?

Windows only installs in UEFI boot mode to gpt partitioned drives.
And Windows only installs to a primary NTFS partition with boot flag if MBR(msdos) partitioned.
And you need to install all systems in same boot mode.
How you boot install media UEFI or BIOS is then how it installs.

Windows will set itself as default boot. So you will have to reinstall grub to MBR or reconfigure to make grub as default boot.
If system is BIOS/MBR, Windows updates partition table and "forgets" to write back into partition table any Linux logical partitions as it does not  correctly see them  (Backup partition table). 
But if you have UEFI hardware better to have both systems in UEFI boot mode as Windows 10 will keep turning on fast start up & then grub will not boot it. So then you temporarily have to restore Windows boot loader to MBR, fix Windows & then restore grub to MBR.

Either way make sure you have good backups and keep both Lubuntu & Windows install/repair flash drives handy.

---

### Post by tackskull on 2019-04-19
I suppose to have uefi. So in fact I've installed windows already and grub doesn't start. So I don't know much about pc and stuff, what I have to do now to make grub work again?

---

### Post by yancek on 2019-04-19
Windows 10 can be installed on a Legacy system with msdos partitioning but will usually install UEFI if the partitioning is GPT.  There is a Custom install option in windows 10 which is the best option to use in your case.  You need to post some information, as it is necessary to KNOW if you use UEFI not guess.  With your Lubuntu install media, boot and open a terminal and run the command:  sudo parted -l (Lower Case Letter L in the command)   If you are using UEFI, there will be an EFI partition showing.  

Might be best to get boot repair from the link below, using the 2nd option to download the ppa version.  Run it by selecting the option to Create BootInfo Summary and do not try any repairs as it may make things even worse.  Post the link you get after running it here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by kurt18947 on 2019-04-20
I hope this isn't out of line with forum rules. If so, please delete the entry. I used a proprietary boot loader when everything was MBR. The current boot loader is Bootit Collection supports both MBR and UEFI. The MBR version also work on UEFI is compatibility mode in BIOS is enabled which was a pleasant surprise. I have no interest in the company or product beyond being a user.

[https://www.terabyteunlimited.com/bootit-collection.htm](https://www.terabyteunlimited.com/bootit-collection.htm)

I haven't tried the current version yet but the MBR/non-UEFI version was quite reliable once a quirk or two was mastered. It doesn't care in which order the OSs are loaded, just that the instructions are followed. I could also choose which partitions are visible to which operating systems.

---

