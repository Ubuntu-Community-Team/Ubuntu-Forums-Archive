---
title: "Grub Loading... Error 2"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ACTPOHABT on 2008-04-28
Have tried installing Hardy, it kept giving me "Grub Loading... Error 2". Googled it and found this:

"The Way To Solve This Grub Error I Found Was To Set My Bios To Auto I Cant Remember Much Of What I Did Because Im Now Back On Windows Xp But This Problem Is Nothing To Do With Going Through Grub And Ruining Ur Loader It Is Simply Ooo I Remember Go To Standard Cmos Settings In Bios Set Your Hard Drive To Auto (thats If It Has An Auto Feature) And Go To Master Which Would Be Ur Hard Drive And Instead Of Having Some Numbers There Try And Set It To Auto Using +/- Keys Save And Reset And It Should Load Right Up!"

The thing is when I press F2, I can't find those setting anywhere. Is there a
different F(..) button I need to press to access those settings? Or am I doing something wrong?

BTW, I'm trying to install it on Sony VGC RC210G desktop. ([http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=48473&DL=',600,5](http://www.iq.sony.com/srvs/DocsConnect/docget.asp?manualid=48473&DL=',600,5))

I've reinstalled Windows back on my PC. The first installation of Ubuntu was on Raid0.

Running LiveCD shows this:

+ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04
Release:        8.04
Codename:       hardy
+ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90fabbf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312574976    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d2d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   fd  Linux raid
autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x807d8dd7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS
+ sudo blkid
/dev/sdb1: UUID="155a817e-de9b-d12a-f09f-dd5ebb9ed077" TYPE="mdraid"
/dev/sdc1: UUID="BCAEE3FEAEE3AF58" LABEL="Big Boy" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"

I have two 160GB drives in a Raid0 array (currently with Vista), and I guess it's a fake Raid. 500GB drive is just for the backup. I've tried installing single boot Ubuntu 8.04 64bit in a Raid0 array using two 160GB drives.

Any ideas?

---

### Post by ACTPOHABT on 2008-04-28
Anybody?

---

### Post by dstew on 2008-04-28
> I've tried installing single boot Ubuntu 8.04 64bit in a Raid0 array using two 160GB drives.How did you do this? Were you using dmraid and the method of the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto")?

---

### Post by ACTPOHABT on 2008-04-28
> **dstew said:**
> How did you do this? Were you using dmraid and the method of the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto")?

I was using Alternate CD.

---

### Post by candtalan on 2008-04-28
I found this- 

Grub errors:
2 : "Selected disk doesn't exist"
This error is returned if the device part of a device- or full filename refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

hth

---

### Post by dstew on 2008-04-28
If you want to install onto a hardware-assisted RAID like you have, you need to do it as shown on the How-To. If you do a regular install, the installer will treat your disks as individual disks, or make a software RAID out of them. I do not think the Alternate Install CD can install to a fakeraid.

If your RAID is active, when grub boots, the BIOS will only report to grub the RAID devices, but if Ubuntu was intalled as if you had individual disks, grub will not be able to find the disk.

About accessing your BIOS, you would use F2, but I think the thread you referred to earlier was not about a fakeraid setup. The BIOS settings in your system would be different, especially if the RAID is activated.

---

### Post by ACTPOHABT on 2008-04-28
> **dstew said:**
> If you want to install onto a hardware-assisted RAID like you have, you need to do it as shown on the How-To. If you do a regular install, the installer will treat your disks as individual disks, or make a software RAID out of them. I do not think the Alternate Install CD can install to a fakeraid.

If your RAID is active, when grub boots, the BIOS will only report to grub the RAID devices, but if Ubuntu was intalled as if you had individual disks, grub will not be able to find the disk.

About accessing your BIOS, you would use F2, but I think the thread you referred to earlier was not about a fakeraid setup. The BIOS settings in your system would be different, especially if the RAID is activated.

So you are saying Raid that Alternate CD offers is different from the one described in FakeRaidHowTo?
I'm a linux newbie, I don't think I quite understand the FakeRaidHowTo guide. :)

---

### Post by Jester. on 2008-04-28
Hi there,

for me it's the same problem. But first we should talk about Fakeraid and Software Raid.
Fakeraid isn't supported by Ubuntu. A "Fakeraid" means the onboard or onchip controller on your mainboard. It is NOT a hardware controller but a software controller. To use this controller you first have to install a driver for linux.

With the Ubuntu alternate CD you can setup a Sofware Raid. The onboard/onchip controller is not used if you setup a Software Raid, but it's exacly the same like a Fakeraid. The only difference is that Ubuntu controls the devices.

As I mentioned before I've got the same problem with "Error 2". With 8.04 Alpha 2 there was no problem with this error.
I really don't know what to do now. I tried to mount my boot partition with the Live CD, to execute a grub-install again, but the raid tools are not installed. I can't use /dev/md0 because it's not there. I tried to install "mdadm" but it didn't help. I tried to mount /dev/hda1 (the first partition of raid1) but it fails with the error that this device is a raid device.

Does anybody know how I can mount a raid device with Live CD or has a solution for the "Error 2" problem?

Jester

---

### Post by dstew on 2008-04-28
> So you are saying Raid that Alternate CD offers is different from the one described in FakeRaidHowTo?Yes. The Alternate CD RAID is software RAID that uses the program **mdadm**. The FakeRaidHowTo describes a hybrid hardware-software RAID that uses a special disk controller, and needs the program **dmraid**. The two are completely different. The software RAID does not need a special disk controller.

I have experience with software RAID, having installed Ubuntu onto a NAS device with 4 hard drives, with a RAID-1 /boot partition, and a RAID-5 root partition. I have been looking for a free computer with a fakeraid controller to play with, but haven't found one yet. You can tell if you have a fakeraid controller by looking in your BIOS. If the BIOS has RAID settings, it's a fakeraid controller. The fakeraid controller can assemble the disks into a RAID, but it cannot do the calculations, hence "fake" RAID. It needs the OS to create the parity data for a RAID-5, for example. But, a true hardware RAID controller (rarely seen in PCs) can do the calculations too.

A fakeraid BIOS will report the RAID device to grub as a single disk, and grub can boot it. However, with a software RAID, the BIOS reports the RAID to grub as separate disks, so you can only boot a RAID-1 (mirrored) software RAID with grub. Grub cannot boot a software RAID-0 or RAID-5, but can boot a fakeraid RAID-0 or RAID-5. And then, only if you set it up correctly. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). In that HowTo, you are creating an Ubuntu system by hand, and not using the convenient installation disk method that we all know and love. But, it is the only way to dual-boot a fakeraid that has Windows on it.

---

### Post by ACTPOHABT on 2008-04-28
> **dstew said:**
> Yes. The Alternate CD RAID is software RAID that uses the program **mdadm**. The FakeRaidHowTo describes a hybrid hardware-software RAID that uses a special disk controller, and needs the program **dmraid**. The two are completely different. The software RAID does not need a special disk controller.

I have experience with software RAID, having installed Ubuntu onto a NAS device with 4 hard drives, with a RAID-1 /boot partition, and a RAID-5 root partition. I have been looking for a free computer with a fakeraid controller to play with, but haven't found one yet. You can tell if you have a fakeraid controller by looking in your BIOS. If the BIOS has RAID settings, it's a fakeraid controller. The fakeraid controller can assemble the disks into a RAID, but it cannot do the calculations, hence "fake" RAID. It needs the OS to create the parity data for a RAID-5, for example. But, a true hardware RAID controller (rarely seen in PCs) can do the calculations too.

A fakeraid BIOS will report the RAID device to grub as a single disk, and grub can boot it. However, with a software RAID, the BIOS reports the RAID to grub as separate disks, so you can only boot a RAID-1 (mirrored) software RAID with grub. Grub cannot boot a software RAID-0 or RAID-5, but can boot a fakeraid RAID-0 or RAID-5. And then, only if you set it up correctly. See the [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto"). In that HowTo, you are creating an Ubuntu system by hand, and not using the convenient installation disk method that we all know and love. But, it is the only way to dual-boot a fakeraid that has Windows on it.

The thing is that I don't need a dual boot. I just want Ubuntu on it. Plus, for some reason there's no Raid settings in my BIOS.
Supposedly I should be able to press Ctrl+I to edit Raid Settings, but the Vaio logo just freezes and nothing happens.

---

### Post by dstew on 2008-04-29
Looking at the [User Guide]("http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGCRC210G") for that system, it seems that it does indeed have a RAID controller (fakeraid) but the BIOS setup screens do not allow you to set it up there, at least in what I could see. It seems you need to use their proprietary software to do it.

If you really don't want the Vista that is on it, or the RAID setup, maybe you can make it go back to treating the disks as individual by resetting the BIOS to its factory defaults. The method is in the Users Manual.

---

### Post by awperk on 2008-04-29
i am also getting this "error 2" but i know why it's happening. i have hardy installed on my external hdd and can boot to it perfectly fine. my problem is that when i'm not attached to my external (i.e. traveling since my main box is a laptop right now) i get the error and cannot boot into windows. is it possible to override this error or not use grub at all? i know that i used to be able to boot directly to my linux partition on my old external drive if it was simply on during my boot sequence and it didn't even give me the grub menu.

-thanks

---

### Post by candtalan on 2008-04-30
> **awperk said:**
> i am also getting this "error 2" but i know why it's happening. i have hardy installed on my external hdd and can boot to it perfectly fine. my problem is that when i'm not attached to my external (i.e. traveling since my main box is a laptop right now) i get the error and cannot boot into windows. is it possible to override this error or not use grub at all? i know that i used to be able to boot directly to my linux partition on my old external drive if it was simply on during my boot sequence and it didn't even give me the grub menu.

-thanks

When you install (hardy) the grub files are put into the /boot directory of your installed ubuntu system. On the external drive. It is possible to install (or maybe modify the existing install? not sure) so that the boot files reside on their own (small) partition on the fixed  drive. It needs only to be tens of MB or so. Grub would need to be reinstalled or modified so that the MBR on the fixed drive  then points to the grub boot files (new partition) on the fixed drive.
This will allow windows to boot via grrub, when the external drive is not connected. 

This can all be done during an install of ubuntu by using a manual install after creating the necessary partition/s
hth

---

