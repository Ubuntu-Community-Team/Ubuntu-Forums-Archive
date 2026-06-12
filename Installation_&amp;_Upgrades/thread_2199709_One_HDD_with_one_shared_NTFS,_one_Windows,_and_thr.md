---
title: "One HDD with one shared NTFS, one Windows, and three linux partions?"
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2014-01-15
Hi

I have read to tri install Ubuntu, Kali, and Windows the order is install Windows, then Kali, then Ubuntu, and that the linux installers will take care of everything and allow the resizing of space if necessary.

Would it also be possible to install Windows, Kali, Debian, and Ubuntu in that respective order? If so please advise which partitions are primary, extended, and logical. Further, on my old desktop I have a shared NTFS partion accessible by linux and Windows, could I also configure this for this proposed quad boot setup on my UEFI laptop?

---

### Post by Mark Phelps on 2014-01-15
> the linux installers will take care of everything and allow the resizing of space if necessary.

You should NOT allow the Linux installers to modify the space used by Windows.  Doing so risks corrupting the Windows filesystem and rendering it unbootable.

The safer way is to boot into the Disk Management tool from inside Windows and do partition resizing there.

---

### Post by tfrue on 2014-01-15
Yes, to everything. I would install Windows first, then it doesn't matter what order you choose. I would just have different partitions for each installation as they will have at least 2 partitions in each partition(Root(/) and Swap...Understand? 

Now, you need to determine if you want to use UEFI/GPT, which I suggest you do, or use MBR/BIOS, which is older but very stable. Make sure that your motherboard supports UEFI before trying to set it up to use it. 

You can use *parted* or *gdisk* since *fdisk* doesn't support GPT partitions. The reason I say use GPT, is because you're not limited to only 4 primary partitions. In theory, you have 128 available partitions in Window's. 

I'm away from my machine, but use *parted* *gdisk*, and create a new GPT disk, I know you type 'o' in gdisk, then create a new primary partition. You may be able to skip this step and use the Window's disk to format and partition the disk, then manaully partition is "Disk Manager" in Window's to partition the drive, then live boot each distro and install to each manually created partition.

I'll be able to elaborate later if you need help, but in class at the moment.

Good luck,
Chris

---

### Post by Dáire Fagan on 2014-01-15
> **Mark Phelps said:**
> You should NOT allow the Linux installers to  modify the space used by Windows.  Doing so risks corrupting the  Windows filesystem and rendering it unbootable.

The safer way is to boot into the Disk Management tool from inside Windows and do partition resizing there.

On  advice I used to do that at some point but I think more recently I have  either been configuring partitions with GParted before installing any  OS or just using GParted afterwards - thanks for the reminder. This  install is only so far as the Windows 8 OS updating itself. I want to  update it fully and install software I will use, seeing how much space  it all uses up, and then deciding on the capacity of the other  partitions. Once I have resized the Windows partion with Disk  Management, am I safe to configuring the other partitions with GParted  or should I let the Linux install handle that each time? 

> **tfrue said:**
> Yes, to everything. I would install Windows first, then it doesn't matter what order you choose. I would just have different partitions for each installation as they will have at least 2 partitions in each partition(Root(/) and Swap...Understand?

Thanks for the reply. In terms of the order the Linux OS are installed after Windows, or more accuratey in terms of where the partitions fall on the disk, I was thinking:

|WIN|Shared NTFS Media|Debian root|Debian home|Ubuntu root|Ubuntu home|Kali root and home|4GB (Same as RAM) swap|

I have read in several articles today that said one individual swap partition can be used across mutliple versions of linux installed on one HDD?

The reason I am thinking about the order on the disk above is that in the future I have not left enough space on the Windows or Media partition I can resize either - these are to be the largest partitions. Also, if for any reason I do not like Debian I can remove the partition and take the space into Media. Splitting up the 500GB (465GB using 1024) HDD, I was thinking 25GB ext4 each for Ubuntu / and ~, 25Gb ext4 each for Debian / and ~, 10-20GB ext4 for kali, 4GB swap. With the remaining 341GB I could either go something like 141GB for Windows and 200GB NTFS for media shared across all OS - OR - once Windows has finished updating and I have installed programs I know I will use to the same partition, I could allocate and extra 50GB or so for updates, use all of the remaining space for the shared partiton, and then not only use that shared partition for media but also for installing future Windows programs - what do you think?

> **tfrue said:**
>  Now, you need to determine if you want to use UEFI/GPT, which I suggest you do, or use MBR/BIOS, which is older but very stable. Make sure that your motherboard supports UEFI before trying to set it up to use it.

My laptop has UEFI and I am happy to use GPT, although I am not sure if I have in the past or not!

> **tfrue said:**
> You can use *parted* or *gdisk* since *fdisk* doesn't support GPT partitions. The reason I say use GPT, is because you're not limited to only 4 primary partitions. In theory, you have 128 available partitions in Window's. 

I'm away from my machine, but use *parted* *gdisk*, and create a new GPT disk, I know you type 'o' in gdisk, then create a new primary partition. You may be able to skip this step and use the Window's disk to format and partition the disk, then manaully partition is "Disk Manager" in Window's to partition the drive, then live boot each distro and install to each manually created partition.

To be clear, once Windows, which is now installed, has finished updating and I have installed all the Windows programs I know I will use and decided on the size of that partiton and the nonboot Media partition is it correct I do the following:


[LIST=1]
[*]Resize the Windows partition using Disk Management. 
[*]Create the shared Media (possibly programs too?) NTFS partiton using GParted - does it matter if this is primary, logical, extended or not - last time I used it it did ask me to specify! 
[*]Create a new GPT disk with all of the remaining space and then create one big primary partition on it before installing each distro which will manually allow me to specify swap, / and ~, or / and ~ combined from the primary GPT partition - Maybe swap should be created a the beginning with Gparted when creating the shared NTFS? 
[*]After installing Ubuntu last run boot-repair if necessary. 
[/LIST]

---

### Post by tfrue on 2014-01-15
> To be clear, once Windows, which is now installed, has finished updating  and I have installed all the Windows programs I know I will use and  decided on the size of that partiton and the nonboot Media partition is  it correct I do the following:



[LIST=1]
[*]Resize the Windows partition using Disk Management.
[*]Create  the shared Media (possibly programs too?) NTFS partiton using GParted -  does it matter if this is primary, logical, extended or not - last time  I used it it did ask me to specify!
[*]Create a new GPT  disk with all of the remaining space and then create one big primary  partition on it before installing each distro which will manually allow  me to specify swap, / and ~, or / and ~ combined from the primary GPT  partition - Maybe swap should be created a the beginning with Gparted  when creating the shared NTFS?
[*]After installing Ubuntu last run boot-repair if necessary.
[/LIST]


Not quite.

1. Install Window's, which you've done.)
2. Use Disk Manager to partition the drive. When you are partitioning in Windows you have to *shrink* the drive to the size that you want Ubuntu, and Kali to be.
3. Live boot into Ubuntu, or Kali ( Which either first doesn't matter).
4. Run the installer and choose *Something Else* and install to the proper partition. Make sure that you can see the Windows partition from Something Else.
5. Then boot into the different distro and do the same thing.

You can try and do the shared swap, but I've never tried it so I don't know. What I was explaining was
|Window's| |Debian root, and Swap| |Ubuntu /, and Swap| |Kali /, and Swap|

---

### Post by oldfred on 2014-01-16
With gpt there is only one partition type essentially all primary.

I might not add the /home partitions as separate partition if using a shared NTFS for data anyway. That data can be mounted in every install. I prefer smaller system partitions and separate data partitions that can be mounted in multiple installs. I have both a Linux data and still have my old (from XP boot) NTFS shared data partitions.

You can share swap as long as you do not hibernate nor use encryption.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by Dáire Fagan on 2014-01-21
After much time installing Windows 8, updates, upgrading to 8.1, setting up SSD expresscache and then configuring it with my most essential programs I discovered that even after defragmenting the disk the 30GB of Windows was installed on, Disk Management would only allow me shrink the partition to ~236GB, which is about 136GB over the mark. Using GParted Live I then deleted all partitions on the 436GB disk and from the Windows 8 install I created a partition just over 100GB, the just over allows for the 350MB second primary system partition the Windows install creates automatically. After configuring Windows 8.1 again, from Ubuntu Live I looked in GParted which warned me:
> 
/dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you detected the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?

Here on the forums gdisk was initially being recommended to fix this but then fixparts. According to the fixparts tutorial I answered N when the following warning appeared:

> NOTICE: GPT signatures detected on the disk, but no 0xEE protective partition!The GPT signatures are probably left over from a previous partition table.Do you want to delete them (if you answer 'Y', this will happenimmediately)? (Y/N):

fixparts then gave me the following warning which is not covered in the tutorial and initial Google results are ambiguous about:

> Warning: 0xEE partition doesn't start on sector 1. This can cause problems in some OSes.

Is this something that should concern me and I need to do something about? I'm holding off on further installation until advised.

It was mentioned earlier on this thread that with GPT there are unlimited numbers of primary partitions. A few minutes ago in the Ubuntu install I looked at (which I soon after ended without making any changes) and in GParted I saw the option to create a GPT partition table but both warned they would erase all data on the disk and I do not want to lose my Windows install. Do I just install each linux OS as normal selecting all partitions as primary? I looked at creating a 4GB swap at the end of the drive and it gave me the option for logical or primary with swap selected.

I am confused about how the drive is using MBR for Windows 8.1 but will also end up using GPT, maybe the latter replaces the former completely?

I would like to install from left to right on the disk 465GB something like:

[Win 8.1 100GB][Shared NTFS Media and Win Program files 234GB][Possible Clonezilla image of Win 8.1 install 30GB or less][Ubuntu / 25GB][Ubuntu ~ 10GB][Ubuntu swap 4GB][Debian / 25GB][Debian ~ 10GB][Debian swap 4GB][Kali / + ~ 10 or 15GB][Kali swap 4GB][Possible bootable Clonezilla 2GB]

I think think this order would allow the greatest flexibility in the future if resizing the first three partitions after backing up where necessary. Please advise if you would recommend a different order, or partitions sizes, maybe 10GB is too big for home on Debian and Ubuntu with a shared NTFS partition for media etc?

---

### Post by oldfred on 2014-01-22
Did you then reinstall Windows 8 in BIOS/MBR boot mode? 
How you boot install media UEFI or BIOS for both Windows & Ubuntu is how it installs, but pre-installed Windows 8 systems only have UEFI/gpt systems and recovery of them would be the same UEFI/gpt.
       Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Dáire Fagan on 2014-01-22
> **oldfred said:**
> Did you then reinstall Windows 8 in BIOS/MBR boot mode?

I just removed all partitions with GParted, booted from Windows 8 USB and installed. Sometimes when I boot from USB the bootmenu prefixes some of the options with 'UEFI:'. If it did then I would have selected that option but I am not sure if it did. If the boot-repair info will not answer this please advise how I can check.

> **oldfred said:**
> How you boot install media UEFI or BIOS for both Windows & Ubuntu is how it installs, but pre-installed Windows 8 systems only have UEFI/gpt systems and recovery of them would be the same UEFI/gpt.
       Product key now in UEFI/BIOS

Sorry, but I do not understand what you are telling me.

      > **oldfred said:**
> Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

[http://paste.ubuntu.com/6798145/](http://paste.ubuntu.com/6798145/)

sdb is an SSD for Intel Rapid Storage Technology, Intel Rapid Start Technology, and Expresscache.

[TABLE="class: ajC"]
[TR="class: ajv"]
[TD="class: gG, colspan: 2"][/TD]
[TD="class: gL, colspan: 2"][/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2014-01-22
You reinstalled Windows in BIOS/MBR mode.
Windows does not correctly convert a gpt partitioned drive to MBR. It leaves the gpt backup partition table, so Linux tools see both MBR primary and gpt backup and get confused on what you really want.
If you do not want to reinstall in UEFI/gpt mode, you have to remove backup gpt data.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Dáire Fagan on 2014-01-22
> **oldfred said:**
> You reinstalled Windows in BIOS/MBR mode.
Windows does not correctly convert a gpt partitioned drive to MBR. It leaves the gpt backup partition table, so Linux tools see both MBR primary and gpt backup and get confused on what you really want.
If you do not want to reinstall in UEFI/gpt mode, you have to remove backup gpt data.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Hi, I have already completed that tutorial, please see where I mentioned it above. After the tutorial GParted did recognise the Windows partitions but it gave the warning about 00xE - also, see above.

I did not know I was supposed to install in UEFI mode. I have read it is faster booting which appeals. If I am better off with Windows installed in UEFI for the system I have described, multiple linux installs etc, do you know a good way to convert the Windows MBR install to UEFI or can you tell me what you think of this guide?

[https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

OR if you recommend a completely new Windows install can you please confirm I just delete all partitions with GParted then install UEFI following this guide:

[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

---

### Post by oldfred on 2014-01-22
With fixparts the entire purpose is to erase gpt data, so you have to say yes.

I have never installed Windows 8, so do not know. Since partitioning is so different I would think a new install would be better. Only if you had lots of data or configurations may conversion be a consideration.

---

