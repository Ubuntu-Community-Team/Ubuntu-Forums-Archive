---
title: "Installing Ubuntu to external SSD"
date: 2023-05-09
forum: Installation &amp; Upgrades
---

### Post by noobtechninja on 2023-05-09
Hi there guys.

I was having a bit of a brain fart, I've overthought this to the point of
sillyness, and  was hopinng that you could help me out with a couple of
quick questions about an Ubuntu installation, please.


**History / situation:**

I now have x2 desktop PCs (PC-1 and PC-2)
PC-1 is my main desktop PC and running well.
PC-2 is new (to me).


PC-2 does not have any GFX capeabilitys at all (ATM).
It doesnt even have on-board GFX (I'm currently awaitng receipt of a GFX
card - a 1070) 


I thought I'd get adead of the game and install Ubuntu on the new SSD
whilst I await the delivery of my GFX card.


I have an external HDD reader, that supports many different HDD connection types.


The internal HD for PC-2 is a SSD (250 GB)


**Questions:**

1. Can I connect my external HDD reader to PC-1, install Ubuntu to the SSD drive
using the GFX and monitor from my main PC, without affecting the current
install of Ubuntu on PC-1, and trashing the bootloader for PC-1 ?


2. Do I need to be careful where I chose to put the bootloader on the SSD ?
(As I don't want to prevent PC-1 from booting properly, once I'm done)

3. Is ther anything else that I need to be aware of ?

TIA for any help or advice.

---

### Post by tea for one on 2023-05-09
Why not install directly to PC-2 via a bootable disk?
Then add the relevant drivers when your GPU arrives?

---

### Post by oldfred on 2023-05-09
1. May depend on installer. Ubiquity only installs grub to first drive, usually your internal drive.
2. Ubiquity may show choices but never uses them.

Old bug but only applies to external or internal drives where you do not want UEFI boot loader on first drive.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Multiple work arounds in bug report. 

Oldfred uses his work around of creating ESP on gpt drive first & unmounting incorrect ESP in middle of install (when installer mounts it) Details in post #55.

But removing esp,boot flag is probably easier for most users.
Remove esp flag from Windows or first drive,  before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator)

Be sure to partition in advance & use gpt partitioning.

---

### Post by ubfan1 on 2023-05-09
Note that Ubuntu 23.04 changed installer from Ubiquity to Subiquity, and the bootloaders go where you tell the installer to put them.  But 23.04 is a 9 month support release, so you'd have more work on the back end keeping up with upgrades.

---

### Post by mIk3_08 on 2023-05-10
> **noobtechninja said:**
> 
2. Do I need to be careful where I chose to put the bootloader on the SSD ?
(As I don't want to prevent PC-1 from booting properly, once I'm done)
TIA for any help or advice. If you are worried about the boot  loader, you can use rEFInd, Grub2, Clover EFI Bootloader and etc. This  are the boot loader that are very simple to configure. Regards and  cheers.

---

### Post by MAFoElffen on 2023-05-10
If I am installing something where it is going to be on another computer, or I want it to be independent of other OS'es...

I just disable all the other drives. Either by disabling them in BIOS, or by physically disconnecting them. (I have hot-swap drive bays on two of my computers, so easily done without cracking the cases.) That way I am 100% sure that it will not affect anything else.

When I am installing a second OS on a machine of the same type, if using a subiquity installer, it has a startup option (subiquity -b) to tell it to install without installing the bootloader... That way the original bootloader is not affected. The second OS can be found by the original boot loader, and I never have to worry about any competing fighting with each other during updates. LOL

---

### Post by noobtechninja on 2023-05-11
[HR][/HR]I had created another thread about this issue, 
As I had made some further progress, and I didn't want this thread to be cluttered up
However it's been closed as a duplicate.
So I'll update this thread instead.


**More information / history:**


On PC-1, I have done the following -


1. Mounted the SSD


2. Used Gparted to delete **(all)** of the old, original partitions on the SSD
This included the Windows installation that the PC came with, the recovery
partition and.................


3. As I've now found out, it appears that I have also deleted any FAT
partition that may have included the EFI / boot partition.


4. Repartitioned the SSD to my preferred set-up =
4.1. A 180 GB = /(root)
4.2. A 320 GB = /home




**New Issue:**
I was running Ubuntu from a live USB stick (22.04.02)
When I got to the HD partitioning, I chose manual, then opted to use the
partitioning scheme that I had alrady configured (outlined above in points 4)


As I was doing this, the installation wizard, complained that it couldn't find
any EFI partitions, and that the install, and subsequent boots may not work
or boot properly.


I realised my mistake, and cancelled the installation of the new OS
on the SSD




**Questions:**


1. Do I actually need a EFI partition to allow me to boot Ubuntu on my new
PC-2 ?


2. (If so) can I recover the old EFI partition and code ?
(unlikeley I know)


3. Can I create a new EFI boot partition ?
3.1. If so how ?


4. Do I need a EFI / "registration code" that is tied to the physical ID of the  SSD ?
4.1. If so, how can I generate it / a new version ?




**Useful information for PC-2:**


Motherboard = Sabertooth 990FX
SSD = Samsung SSD 850 EVO 500G

TIA for any further help or advice

---

### Post by yancek on 2023-05-11
> 1. Do I actually need a EFI partition to allow me to boot Ubuntu on my newPC-2 ?

Some newer computers only allow UEFI installs but most will allow you to install in Legacy mode.  UEFI is much better than the older Legacy/CSM particularly if you have a GPT drive.  You can determine this by booting your Ubuntu USB and from a terminal, running the command below and looking if disklabel shows msdo or gpt.  If gpt, much better to use UEFI.

Highly unlikely you will be able to recover the old EFI partition but you could try testdisk.  Easier to just reinstall.  You can create an EFI partition with GParted on the Ubuntu USB and also create your / and /home partitions. Use the Something Else (manual) install option.  EFI partition 100-500MB with FAT filesystem (usuall FAT32/vfat), your choice depending on the size of your drive, 20-30GB for / and the rest for /home or data.  Make sure when you boot the Ubuntu USB you select the UEFI option to boot.

---

### Post by oldfred on 2023-05-11
I used to also suggest 20 or 30GB for /. But now am using 16GB in my Kubuntu install with no snaps. And have seen some users post with snaps using 20GB!. So now if Ubuntu 40 to 50GB for / if you also are going to use snaps.

Besure to change to gpt as that is recommended for UEFI installs. 
I think gparted still defaults to old MBR(msdos). 

Changing from MBR to gpt totally erases a drive.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.
sudo parted /dev/sda mklabel gpt
man fdisk # disk labels section:
"GPT is always a better choice than MBR, especially on modern hardware with a UEFI boot loader."
You can create a GPT partition table with g with fdisk

Converting to or from GPT - must have good backups, but may not erase disk.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by ubfan1 on 2023-05-11
Another note, the installer on Ubuntu 23.04 for "something else" makes it difficult to make an EFI of a size you want -- initial creation of a new partition does not allow FAT filesystem type (you can go back and change), and furthermore, does not allow you to allocate an EFI partition.  It will however, use a preexisting EFI partition, so you either make one before the install, or let the installer make the EFI partition it wants (1GB in size!).

---

### Post by monkeybrain20122 on 2023-05-11
I haven't tried Ubuntu23.04 but I have been installing interim releases since Ubuntu 11.xx (with ubiquity) in external hd for testing with no issue and it makes a portable, fully functional system (not like live usb) that can boot from different machines. Just make sure you install the bootloader in the external drive instead of the internal one.

---

