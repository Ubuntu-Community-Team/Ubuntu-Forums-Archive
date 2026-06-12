---
title: "Neither Ubuntu 13.10 nor Windows 7 are able to boot"
date: 2014-01-17
forum: Installation &amp; Upgrades
---

### Post by jaege172 on 2014-01-17
Hello all,

I am new to linux/ubuntu and generally don't know a whole lot of terminology regarding boot loaders, etc, so hopefully someone here can explain it in a way I can understand.

I tried to install a dual boot ubuntu 13.10 alongside my pre-existing windows 7. I finally got it installed last night, but this morning I realized that windows was no longer in the boot selection menu. I had a buddy of mine take a look and he did some messing around but didn't really get anywhere. I did some further messing around using the boot repair, but still no luck. I went to my BIOS and I changed UEFI mode to disabled, and then enabled it again (for no reason, really). Now, I can no longer load Ubuntu or Windows 7. No matter which boot device I select I end up at the grub rescue command prompt. I've been using the "Try Ubuntu" option from my bootable USB and been trying to run the boot repair tool but have not had any success.

I have a Lenovo Ideapad Y-580, Intel core i7. I believe I have windows installed on my 700GB HDD and Ubuntu installed on my 32GB SSD (not 100% about this... how can I make sure?). My recent boot repair run gave me this link: paste.ubuntu.com/6766165. Note that I do NOT have the installation/recovery disk for Windows 7 (never got one with my laptop).

Please help, and thanks in advance!!

---

### Post by Bucky Ball on 2014-01-17
Open Gparted and take a look. You should see your Windows partition(s) there marked as NTFS filesystem (or not).

Did you install in UEFI both Win7 and Ubuntu. That can be tricky if you don't do it right (you need to switch off secureboot and faststart in the BIOS and make sure you are booting and installing in EFI). If Win is installed in EFI, Ubuntu MUST be installed EFI. 

I suggest you ascertain whether Win is there or not and get back to us. This makes a lot of difference. If you didn't install Ubuntu in EFI mode then there is a good chance it ignored Windows, considered the disk blank and used the lot. When installing in EFI you MUST use the 'Something Else' option at the partitioning section of the Ubuntu install and manually partition.

Post back a screenshot from Gparted if you like ('Go Advanced'>Paperclip Icon> Attach pic rather than inserting in the body of your post).

---

### Post by tfrue on 2014-01-17
Will you tell me what you did when you installed Ubuntu? Did you choose "Something Else" or did you choose to wipe disk, or did you choose to install alongside Win 7? Did you install using a USB? 

It seems like you installed Ubuntu with EFI/GPT, while the 720GB drive uses BIOS/MBR. When you have a GPT, especially newer model laptops pre-installed with Win 8, they use UEFI to boot Win 8 (There is more to it than that, but we will stay simple). What some people do, is disable EFI/Secure boot, and enable Legacy boot so they can boot into different OS's like Linux. What that does is disable EFI/GPT and uses BIOS/MBR, so when you live boot into Linux with a disabled EFI, you are practically seeing a whole new world. The drive will look empty and people will continue to install, and over write all the data on the drive.


> Model: ATA SAMSUNG MZMPC032 (scsi)
Disk /dev/sda: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  512MB   511MB   fat32                 boot
2      512MB   29.1GB  28.5GB  ext4
3      29.1GB  32.0GB  2960MB  linux-swap(v1)


Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
1      1013kB  703GB  703GB   primary  ntfs         diag
3      729GB   750GB  21.0GB  primary  ntfs         diag


Model:  Patriot Memory (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  4010MB  4006MB  primary  fat32        boot, lba

What this tells us is that /dev/sda is your 32GB SSD that uses GPT, while /dev/sdb is your 750GB HDD that uses msdos (MBR), and /dev/sdc which I have no idea what it is, it says it's about 4GB uses MBR and has a single primary partition that is marked with a boot flag but should be mounted on /cdrom. I don't know.

What you need to do is disable UEFI, since the main drive that has Window's on it is using MBR and see if you can boot into Window's that way.

We may need to disable the boot flags on your SSD, and the Patriot Memory. Did you boot from USB or a CD? But, the *diag* you see under /dev/sdb, means that that partition can be used as a recovery partition, we may need to re enable /dev/sdb1 as bootable.

Can you live boot into Ubuntu? If you can, would you post the output of:
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

This will determine if you live booted as EFI or bios, and then we can turn determine to enable Legacy boot or disable EFI boot. If you do get BIOS see if you can see Window's from the installer.

Just food for thought, you may have installed grub to /dev/sdb while you were trying to install Ubuntu in UEFI, which would cause problems since you have two different boot loaders on two different devices. This may be as simple as installing grub on your 720GB HDD while BIOS booting, so you can see all of your options. I doubt it though.

Good luck,
Chris

---

### Post by Bucky Ball on 2014-01-17
@jaege172: How about making us all privvy to the information that tfrue is in possession of??? Post all info on the forum if you want help from the community or discuss this in private. Thanks.

---

### Post by tfrue on 2014-01-17
He didn't install Win in EFI. /dev/sdb (The 720GB HDD) is used as an msdos partition with two primary partitions that both have a flag of diag, not boot, and the /dev/sda (The SSD) has a GPT disk signature with three partitions the first being the EFI, and the other two as / and swap. If he can get into Window's I will feel like there is more hope for him saving Win 7, but there may not be anything wrong with the data on the drive, maybe just incorrectly marked flags, while trying to use different partition styles.

He will never be able to boot into Window's unless he disables EFI, since the /dev/sdb uses msdos, so this will be tricky.

---

### Post by tfrue on 2014-01-17
He did, he pasted the boot-info url in the post. I had to copy and paste it into the browser lol. Here is the link:
[http://paste.ubuntu.com/6766165/](http://paste.ubuntu.com/6766165/)

---

### Post by Bucky Ball on 2014-01-17
He will never be able to boot into Windows if it's not there. Let's just deal with the first request. 

To the OP: Open Gparted from the Live boot desktop and see if your Win partition still exists, please.

---

### Post by Bucky Ball on 2014-01-17
He will never be able to boot into Windows if it's not there. Let's just deal with the first request. 

To the OP: Open Gparted from the Live boot desktop and see if your Win partition still exists, please.

PS: > **tfrue said:**
> He did, he pasted the boot-info url in the post. I had to copy and paste it into the browser lol. Here is the link:
[http://paste.ubuntu.com/6766165/](http://paste.ubuntu.com/6766165/)

? Where?

In any case, looks like Win is there, but things are a mess. :-k

---

### Post by tfrue on 2014-01-17
I was thinking that he could wipe, and possibly remove, the SSD and run MBR fix or boot fix or  turn on a boot flag for /dev/sdb1, and see if he could boot back into Win. Whatcha think?

---

### Post by oldfred on 2014-01-17
I think the OP may need to look at his 750GB drive with testdisk. While it may be MBR now, it may not have been as he shows Windows efi files in sdb's efi partition?

And it only shows two partitions sdb1 & sdb3, both as Compaq diagnostics which may just be from garbage data in partition table.

 [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by jaege172 on 2014-01-17
Hey guys, sorry for the late reply. I have the screenshots of both my HDD and SSD partitions attached. My 4GB patriot memory is the USB stick I am using right now to boot Ubuntu (as I cannot boot the installed version on my SSD).

---

### Post by jaege172 on 2014-01-17
> **tfrue said:**
> Will you tell me what you did when you installed Ubuntu? Did you choose "Something Else" or did you choose to wipe disk, or did you choose to install alongside Win 7? Did you install using a USB? 

It seems like you installed Ubuntu with EFI/GPT, while the 720GB drive uses BIOS/MBR. When you have a GPT, especially newer model laptops pre-installed with Win 8, they use UEFI to boot Win 8 (There is more to it than that, but we will stay simple). What some people do, is disable EFI/Secure boot, and enable Legacy boot so they can boot into different OS's like Linux. What that does is disable EFI/GPT and uses BIOS/MBR, so when you live boot into Linux with a disabled EFI, you are practically seeing a whole new world. The drive will look empty and people will continue to install, and over write all the data on the drive.




What this tells us is that /dev/sda is your 32GB SSD that uses GPT, while /dev/sdb is your 750GB HDD that uses msdos (MBR), and /dev/sdc which I have no idea what it is, it says it's about 4GB uses MBR and has a single primary partition that is marked with a boot flag but should be mounted on /cdrom. I don't know.

What you need to do is disable UEFI, since the main drive that has Window's on it is using MBR and see if you can boot into Window's that way.

We may need to disable the boot flags on your SSD, and the Patriot Memory. Did you boot from USB or a CD? But, the *diag* you see under /dev/sdb, means that that partition can be used as a recovery partition, we may need to re enable /dev/sdb1 as bootable.

Can you live boot into Ubuntu? If you can, would you post the output of:
```
[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS
```

This will determine if you live booted as EFI or bios, and then we can turn determine to enable Legacy boot or disable EFI boot. If you do get BIOS see if you can see Window's from the installer.

Just food for thought, you may have installed grub to /dev/sdb while you were trying to install Ubuntu in UEFI, which would cause problems since you have two different boot loaders on two different devices. This may be as simple as installing grub on your 720GB HDD while BIOS booting, so you can see all of your options. I doubt it though.

Good luck,
Chris

I entered the code and the output is BIOS. I don't really know what you mean by "see Windows from the installer". 

Thanks for your help!

---

### Post by jaege172 on 2014-01-17
> **tfrue said:**
> He didn't install Win in EFI. /dev/sdb (The 720GB HDD) is used as an msdos partition with two primary partitions that both have a flag of diag, not boot, and the /dev/sda (The SSD) has a GPT disk signature with three partitions the first being the EFI, and the other two as / and swap. If he can get into Window's I will feel like there is more hope for him saving Win 7, but there may not be anything wrong with the data on the drive, maybe just incorrectly marked flags, while trying to use different partition styles.

He will never be able to boot into Window's unless he disables EFI, since the /dev/sdb uses msdos, so this will be tricky.

How do I disable EFI? After I do this, will I need to enable some other boot type?

---

### Post by jaege172 on 2014-01-17
Now I must go but I will return tonight. Above are the screenshots of gparted, the url to the Boot Repair summary is in the OP. Thanks for your help guys, its such a relief that this forum exists and there are actually people who can help.

Best,
Ian

---

### Post by oldfred on 2014-01-17
UEFI have several settings. Different vendors implement it differently. You have UEFI with secure boot, UEFI and CSM/legacy/BIOS as three boot options. With secure boot on you can only boot secure boot systems.
Some have multiple switches to see just UEFI or just CSM, others have a CSM/UEFI boot mode where it looks for UEFI and if not found tries BIOS boot mode.
       UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Both Windows & Ubuntu will install in the same mode as you boot install media. UEFI & BIOS are not really compatible, so once you start booting in one mode you cannot change. Best to have both system installed in same boot mode either both UEFI or both BIOS. But some boot only using UEFI or one time boot key and have systems installed in different modes.

This does show the Ubuntu boot screens:
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by jaege172 on 2014-01-17
It seems as though I am using BIOS as my boot mode. It gives me only one option regarding UEFI mode and that is either enabled or disabled. Does this mean I should delete my ubuntu partition and then maybe Win7 will be bootable?

---

### Post by oldfred on 2014-01-18
The only Windows boot loader shown was in the efi partition.  Or UEFI boot.

But the partitions still do not look right on hard drive. May just be partition table issue.

---

