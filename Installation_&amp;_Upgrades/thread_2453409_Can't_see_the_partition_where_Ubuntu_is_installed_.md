---
title: "Can't see the partition where Ubuntu is installed on Windows and data loss"
date: 2020-11-09
forum: Installation &amp; Upgrades
---

### Post by patrickyip on 2020-11-09
I installed dual systems on my computer with Windows 10 first and then Ubuntu 20.04 LTS.

I used create USB bootable tool to install Ubuntu and before that I freed up 300G disk space on Windows. 

But during the installation I chose to "Install Ubuntu Alongside with Windows" and also chose to assign 300G to Ubuntu and Ubuntu did its automatic installation.

Everything went smooth during the installation. But when I logged into Windows and I found the were 300G lost on disk space when I checked in the Disk Management and I did not find the partition where Ubuntu is installed! There are only 2 partitions (D & E where my personal data located in) and there is a red cross on the lower left of the sign of each partition (I cannot suppress or expand each of them) and the 300G I freed up has gone.

And I also found that the more I logged in Ubuntu the more data loss on Windows.

I don't really care about my data on my disk(coz I've backed them up), I just don't want two systems conflict each other. 

So I want to reinstall the Ubuntu on the right partition and also Windows, just can anyone tell me what is the simplest way to solve this problem?

Many many thanks!!!!

---

### Post by tea for one on 2020-11-10
Windows 10 cannot natively [COLOR="#0000FF"]see[/COLOR] Linux partitions. You will have to install a Windows utility to read Linux partitions.

However, if you boot into Ubuntu, you will see your Windows partitions.

Your 300GB Ubuntu partition must be on the disk otherwise you would not be able to boot into Ubuntu.

Can you elaborate about [COLOR="#FF0000"]more data loss on Windows[/COLOR]?

Have you actually noticed Windows files or folders missing?

---

### Post by Impavidus on 2020-11-10
Some data may help. Can you run this command in Ubuntu and paste the output to the forum?```
sudo fdisk -l
```That should tell us how your hard drive is partitioned. A screenshot from the Windows partitioning tool may help too.

Windows should see the Ubuntu partition, but it will be called an unknown partition, won't get a "drive letter" and won't be accessible.

---

### Post by Frogs Hair on 2020-11-10
I create the unallocated space for Ubuntu from the windows disk management and use the something else option and select that space to install Ubuntu. I have a 50 GB partition for Ubuntu and Win 10 sees it as healthy partition.

---

### Post by patrickyip on 2020-11-10
Here is the output of the code:

```
Disk /dev/loop0: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 55.37 MiB, 58052608 bytes, 113384 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 255.58 MiB, 267980800 bytes, 523400 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop3: 217.92 MiB, 228478976 bytes, 446248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop6: 50.69 MiB, 53133312 bytes, 103776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop7: 29.9 MiB, 31334400 bytes, 61200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/nvme0n1: 238.49 GiB, 256060514304 bytes, 500118192 sectors
Disk model: Pioneer APS-SE20-256                    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 99F31ABE-F4D4-40B2-8501-7D2E4E0D48BA


Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048   1085439   1083392   529M Windows recovery environment
/dev/nvme0n1p2   1085440   1288191    202752    99M EFI System
/dev/nvme0n1p3   1288192   1320959     32768    16M Microsoft reserved
/dev/nvme0n1p4   1320960 294132647 292811688 139.6G Microsoft basic data
/dev/nvme0n1p5 294133760 295313407   1179648   576M Windows recovery environment
/dev/nvme0n1p6 295315456 500115455 204800000  97.7G Microsoft basic data


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: TOSHIBA DT01ACA1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B073FE17-4406-49BB-BC14-AA9B28F4615F


Device          Start        End    Sectors   Size Type
/dev/sda1          34       2081       2048     1M Microsoft LDM metadata
/dev/sda2        2082      32767      30686    15M Microsoft reserved
/dev/sda3       32768 1465152043 1465119276 698.6G Microsoft LDM data
/dev/sda4  1465153536 1466202111    1048576   512M EFI System
/dev/sda5  1466202112 1953523711  487321600 232.4G Linux filesystem


Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.

Disk /dev/loop8: 30.96 MiB, 32440320 bytes, 63360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

Thanks!

> **tea for one said:**
> Windows 10 cannot natively [COLOR=#0000FF]see[/COLOR] Linux partitions. You will have to install a Windows utility to read Linux partitions.

However, if you boot into Ubuntu, you will see your Windows partitions.

Your 300GB Ubuntu partition must be on the disk otherwise you would not be able to boot into Ubuntu.

Can you elaborate about [COLOR=#FF0000]more data loss on Windows[/COLOR]?

Have you actually noticed Windows files or folders missing?



Here is my screenshot on Windows disk management and as you can see disk1 works fine however disk0 isn't even shown!

For more data loss, as some of my apps continuously go wrong with some sorts of errors of "missing file", I realize the data is losing.

And I also submit the code suggested and posted the output on this discussion

Thanks!

[ATTACH=CONFIG]287331[/ATTACH]


> **Impavidus said:**
> Some data may help. Can you run this command in Ubuntu and paste the output to the forum?```
sudo fdisk -l
```That should tell us how your hard drive is partitioned. A screenshot from the Windows partitioning tool may help too.

Windows should see the Ubuntu partition, but it will be called an unknown partition, won't get a "drive letter" and won't be accessible.


I have already run the code and posted the output, please take a look at it thx!

> **Frogs Hair said:**
> I create the unallocated space for Ubuntu from the windows disk management and use the something else option and select that space to install Ubuntu. I have a 50 GB partition for Ubuntu and Win 10 sees it as healthy partition.


Yeah as the screenshot I posted you can see the total disk was missing on Windows LOL

---

### Post by tea for one on 2020-11-10
In your original post, you did not mention two disks.

Have you considered using one disk for Windows 10 and the second for Ubuntu?

This would be a simple solution and, simultaneously, prevent conflict.

Make sure that both systems use GPT and are installed in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Impavidus on 2020-11-10
Windows says the disk is there. It says it's dynamic. I don't really know about Windows dynamic disks, but I'm sure that Linux doesn't support it, which causes the confusion. Fortunately you've got backups. I suggest you format that drive to use primary partitions, not dynamic partitions. Then Ubuntu and Windows can share the drive.

---

### Post by patrickyip on 2020-11-10
> **tea for one said:**
> In your original post, you did not mention two disks.

Have you considered using one disk for Windows 10 and the second for Ubuntu?

This would be a simple solution and, simultaneously, prevent conflict.

Make sure that both systems use GPT and are installed in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Sorry I forgot to mention that, but I actually installed Windows on SSD and Ubuntu on HDD however some of my Windows data is located in the HDD.
I am not sure if I delete the Volume would it influence the Ubuntu?

---

### Post by tea for one on 2020-11-10
I notice that both disks are GPT - splendid.

Can you confirm that you have installed both Operating Systems in UEFI mode?

Use this terminal code for Ubuntu:-

```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

For Windows, navigate to System Information > System Summary > BIOS mode (value is either Legacy or UEFI)

---

### Post by oldfred on 2020-11-10
How did you get dynamic partitions on sda?
Dynamic is Microsoft proprietary but was another work around for the old MBR(msdos) 4 primary partition limit.
There really is no reason for dynamic on gpt(GUID) partitioning.

Older info on dynamic partitions. Some third party Windows tools may let you undo them, but Microsoft makes it easy to create but has no way to undo dynamic partitions.
[https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)

---

### Post by patrickyip on 2020-11-11
> **oldfred said:**
> How did you get dynamic partitions on sda?
Dynamic is Microsoft proprietary but was another work around for the old MBR(msdos) 4 primary partition limit.
There really is no reason for dynamic on gpt(GUID) partitioning.

Older info on dynamic partitions. Some third party Windows tools may let you undo them, but Microsoft makes it easy to create but has no way to undo dynamic partitions.
[https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](https://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)


Well I also want to know how I did that.

Now I deleted those volumes and it is expected that those volumes would become unallocated but it turns out that they disappear in the disk Management and I have no way to find them on Windows...

---

### Post by Impavidus on 2020-11-11
I think that you now deleted the dynamic partitions on that drive, but the primary partitions underneath (where Windows stores how the primary partitions were configured) are still there. The Windows tool only shows you the dynamic partitions, so it shows you nothing now, and Ubuntu only shows the primary partitions.

This may work: Use the Ubuntu live disk to wipe the first megabyte of that drive, so that Windows forgets it uses dynamic partitions. Then create a new GTP partition table and create all partitions you want. At least one Linux partition (ext4, unless you're sure you want something else), maybe a swap partition, maybe an EFI partition (Ubuntu can use the EFI partition on the other drive, but you may want both drives to be bootable) and one or two ntfs partitions for your Windows files. Then install Ubuntu. Windows should detect the new ntfs partitions and allow you to use them. Restore your files from your backup.

---

### Post by patrickyip on 2020-11-11
> **tea for one said:**
> I notice that both disks are GPT - splendid.

Can you confirm that you have installed both Operating Systems in UEFI mode?

Use this terminal code for Ubuntu:-

```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

For Windows, navigate to System Information > System Summary > BIOS mode (value is either Legacy or UEFI)



Yes, I can confirm that both are in UEFI mode

---

### Post by patrickyip on 2020-11-11
> **Impavidus said:**
> I think that you now deleted the dynamic partitions on that drive, but the primary partitions underneath (where Windows stores how the primary partitions were configured) are still there. The Windows tool only shows you the dynamic partitions, so it shows you nothing now, and Ubuntu only shows the primary partitions.

This may work: Use the Ubuntu live disk to wipe the first megabyte of that drive, so that Windows forgets it uses dynamic partitions. Then create a new GTP partition table and create all partitions you want. At least one Linux partition (ext4, unless you're sure you want something else), maybe a swap partition, maybe an EFI partition (Ubuntu can use the EFI partition on the other drive, but you may want both drives to be bootable) and one or two ntfs partitions for your Windows files. Then install Ubuntu. Windows should detect the new ntfs partitions and allow you to use them. Restore your files from your backup.


Do you mean formatting or deleting the first partition? Could you elaborate more about the whole process? Here I post the screenshot of Ubuntu's disk management.[ATTACH=CONFIG]287339[/ATTACH]

---

### Post by tea for one on 2020-11-11
> **patrickyip said:**
> Yes, I can confirm that both are in UEFI mode

Assuming that you still wish to achieve the objective in your original post as follows:-
> So I want to reinstall the Ubuntu on the right partition and also Windows, just can anyone tell me what is the simplest way to solve this problem?

Widows 10 on one disk - Ubuntu on the other disk.

You already have GPT organised, therefore install both systems in UEFI mode.

Unless, you now have a different objective.................?

---

### Post by The Cog on 2020-11-11
The screenshot in post #5 has a scrollbar next to the disk list. Are you sure there isn't a Disk 2 as well?

---

### Post by Impavidus on 2020-11-11
> **patrickyip said:**
> Do you mean formatting or deleting the first partition? Could you elaborate more about the whole process? Here I post the screenshot of Ubuntu's disk management.
With "wipe the first megabyte" I mean exactly that: wipe the first megabyte of the drive by overwriting it with zeros. That destroys the partition table, making the drive appear as if it comes fresh from the factory. That should eliminate any confusion coming from using two partitioning methods (primary partitions and Windows dynamic partitions), one on top of the other. A tool like dd can do it, of for a bit more safety you can use mkusb. It must be done from a live disk. Then you can use gparted (included on the live disk) to make new partitions. Then install Ubuntu.

Maybe you first want to see some suggestions from others. What I propose is sure to work, but it is the nuclear option.

---

### Post by patrickyip on 2020-11-12
I wiped the whole disk with a third-party App and now the disk is available on Windows, then I think this should be solved (hopefully)

Thanks everyone for helping me with such a stupid question!

Appreciated!

---

