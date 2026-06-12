---
title: "Installing Ubuntu"
date: 2014-03-29
forum: Installation &amp; Upgrades
---

### Post by Sebastian_Ulloa on 2014-03-29
Hi everyone,
I'm going to install ubuntu via LiveCD, and the wizard doesn't show me that Windows7 was installed. I get this form boot-repair:

[http://paste.ubuntu.com/7176626/](http://paste.ubuntu.com/7176626/)

Someone knows something about this?

Thanks!

---

### Post by fantab on 2014-03-29
> **Sebastian_Ulloa said:**
> Hi everyone,
I'm going to install ubuntu via LiveCD, and the wizard doesn't show me that Windows7 was installed. 

```
parted -l:

Model: ATA ST640LM001 HN-M6 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/4096B
**Partition Table: gpt**

Number  Start   End     Size    File system  Name                          Flags
1      1049kB  274MB   273MB   fat32        EFI system partition          hidden
2      274MB   20.4GB  20.1GB  ntfs         Basic data partition          hidden, diag
**3      20.4GB  20.7GB  273MB   fat32        EFI system partition          boot**
4      20.7GB  20.8GB  134MB                Microsoft reserved partition  msftres
5      20.8GB  346GB   326GB   ntfs         Basic data partition          msftdata
6      346GB   640GB   294GB   ntfs         Basic data partition          msftdata


```

The Ubuntu installer needs to a see either 'unallocated space' or a 'linux filesystem' to be able to install. You have made neither.

***Note: Windows Partitions MUST be managed with Windows Disk Management tools only.
*** Make good BACKUPS of your DATA.
*** Make a [Windows REPAIR DISC]("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html").

You will need to make space for Ubuntu.
--**[Shrink]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html")** one of the NTFS data partition, say the 6th partition of 294GB and make space for Ubuntu. 30GB of for Ubuntu is a recommended minimum. 
After Shrinking you will leave the space as 'unallocated space'. But before you Shrink the NTFS partition run '**defragmentation**' a couple of times on the paritition. 
--Then run '[**chkdsk**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html")' on the Windows Partitions... this will take care of the filesystem errors, if any.
--Reboot a couple of times to make sure there are no errors.

--Boot with Ubuntu DVD/USB and 'Try Ubuntu (Without Installing). Test Ubuntu on your machine. Check internet, wifi and check all the hardware you plug in to the machine and see if they all work with Ubuntu.
**Some Graphic Cards can cause 'black Screen'. As a temporary workaround you need to append '[**NOMODESET**]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' option to the kernel line to boot Ubuntu in a 'failsafe graphics mode'.
--Install Ubuntu from desktop.
--Follow the Install Wizard. When you reach the 'Installation Type' dialog choose either:
1. *Install alongside Windows* - the installer will setup Ubuntu in the 'unallocated space' we created earlier.. and continue with installation.
OR
2. '*Something Else*' option to manually create partitions from the 'unallocated space'.
Select the 'unallocated space' and make two partitions from it (asuming you have 30Gb space):
28Gb for Ubuntu '/'  and set it up with
Use As= Ext4 Journaling system
Mountpoint=/
format=yes
2GB SWAP
Use As= Linux SWAP
format=yes

continue with installaiton.

More Info: 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[gpated tutorial]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by Sebastian_Ulloa on 2014-03-30
Thanks, I'm going to try it!:D

---

### Post by Sebastian_Ulloa on 2014-04-06
Hi!
I did everthing you told me, the only thing I'm missing is how to boot. I tried to put Ubuntu as an option in the Windows Boot Loader, but I did not know the path so I put
[B]/ubuntu.bin
[/B]And it didn't work!
Any idea?

---

