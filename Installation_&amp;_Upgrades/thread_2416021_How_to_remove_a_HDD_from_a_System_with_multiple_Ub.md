---
title: "How to remove a HDD from a System with multiple Ubuntu distributions and Grub2"
date: 2019-04-04
forum: Installation &amp; Upgrades
---

### Post by sunbear-c22 on 2019-04-04
I am working on a System that has two internal disks, a) a nvme SSD with Ubuntu 16.04 and b) a HDD with Ubuntu 18.04. I am anticipating the HDD will soon fail; disk failure notice was issued during system boot-up and while using gpart to examine the disks. GRUB2 presentlly shows the options of booting up via Ubuntu 16.04 and Ubuntu 18.04. When I unplugged the HDD from the system, Grub2 does appear but after I have selected to boot up via Ubuntu 16.04, I then get a black screen. 

May I know what is the correct way to remove the HDD and correctly reconfigure Grub2? I suspect the black screen may be due to issue with Grub2 configuration not finding the HDD. Thank you.

---

### Post by sunbear-c22 on 2019-04-04
Error msg during BIOS bootup:

> SATA6G_6 : TOSHIBA DTO1ACA200
WARNING: Please back-up your data and replaced your hard disk drive.
A failure may be imminent and cause unpredictable fail.
Press F1 to Run Setup

---

### Post by yancek on 2019-04-04
> When I unplugged the HDD from the system, Grub2 does appear but after I have selected to boot up via Ubuntu 16.04, I then get a black screen. 


Make sure Grub of 16.04 is installed to the MBR of the SSD on which it resides, that is if you are using a Legacy non-EFI system?

---

### Post by sunbear-c22 on 2019-04-04
@yancek, Ubuntu 16.04 is using efi boot. How do I check whether grub2 on NVME (Ubuntu 16.04) or HHD (Ubuntu 18.04) is being used?

---

### Post by oldfred on 2019-04-04
Probably NVMe.

UEFI uses GUID.
This will show a GUID as part of boot:
sudo efibootmgr -v
And this will show GUIDs (also called partUUID:
       lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop" 
or by device You have /dev/nvme0n1?
      
 lsblk -f -o +PARTUUID /dev/sda

---

### Post by sunbear-c22 on 2019-04-05
@oldfred, below are the output. I have removed the UDID & PARTUUID data. 

```
sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* ubuntu	HD(1,GPT,fe1c10df-6af1-4ddf-829f-a9af111561aa,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive	BBS(HD,,0x0)..GO..NOs.......Y.B.P.X....................A..........................................Gd-.;.A..MQ..L.B.P.X........BO

$ lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop" 
NAME        MOUNTPOINT                   LABEL   SIZE FSTYPE   UUID                                 PARTUUID
nvme0n1                                        447.1G                                               
&#9500;&#9472;nvme0n1p3 /                                   19.5G ext4     
&#9500;&#9472;nvme0n1p1 /boot/efi                            512M vfat     
&#9500;&#9472;nvme0n1p4 /home                              395.9G ext4     
&#9492;&#9472;nvme0n1p2 [SWAP]                              31.3G swap

```


I had to unplugged the failed HHD finally. On reboot, although I get the black screen, I had to wait for quite some time before login screen reappears (or maybe pressing some keys onto the keyboard during the black screen helped start the login scrren?). In any case, after login I ran a sudo update-grub command and noticed the following:

```
$ sudo update-grub2
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-42-generic
Found initrd image: /boot/initrd.img-4.10.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-141-generic
Found initrd image: /boot/initrd.img-4.4.0-141-generic
Invalid output format export. Choose from value,
	device, list, or full
Invalid output format export. Choose from value,
	device, list, or full
Invalid output format export. Choose from value,
	device, list, or full
Invalid output format export. Choose from value,
	device, list, or full
Adding boot menu entry for EFI firmware configuration
done

```
I suspect that > Invalid output format export. Choose from value, device, list, or full
 has something to do with grub2 trying to find the linux images associated to Ubuntu 18.04 that was found in my failed HDD that i had removed. How do I tell remove this dated references so that Grub2 will not look for them? Is this the way to solve my issue?

---

### Post by oldfred on 2019-04-05
The idea was to see if the GUID shown in UEFI entry, shown now as fe1c10df-6af1-4ddf-829f-a9af111561aa matches the partUUID of any of your partitions. They would only be FAT32 and should be only ESP - efi system partitions which are FAT32 with boot flag and/or esp flag.
You may have one ESP per drive.

I would normally suggest running Boot-Repair as it shows a lot of info.  But it has not been updated to show details on NVMe drives, so we cannot see details.
You could run Boot-Repair and see if it will reinstall grub. I might use advanced mode and choose NVMe drive and your install for a full reinstall of grub, not just update grub which refreshes settings.

---

### Post by sunbear-c22 on 2019-04-05
@oldfred, fe1c10df-6af1-4ddf-829f-a9af111561aa is the PARTUUID of nvme0n1p1 /boot/efi, which is a fat32 filesystem and has both boot and esp flags ( I double check these using gparted).

Given that I have only 1 nvme storage plugged in my system (failed HDD was unplugged), is it normal for [COLOR=#000000][FONT=&amp]sudo efibootmgr -v[/FONT][/COLOR] to show this  
```
BootOrder: 0000,0001
Boot0000* ubuntu    HD(1,GPT,fe1c10df-6af1-4ddf-829f-a9af111561aa,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NOs.......Y.B.P.X....................A..........................................Gd-.;.A..MQ..L.B.P.X........BO
```

Should it not just show (I have only 1 storage disk and one efi partition to boot from) :confused::
```
BootOrder: 0000
Boot0000* ubuntu    HD(1,GPT,fe1c10df-6af1-4ddf-829f-a9af111561aa,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
```

What does this line mean? ```
Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NOs.......Y.B.P.X....................A..........................................Gd-.;.A..MQ..L.B.P.X........BO
```

---

### Post by oldfred on 2019-04-05
I do not fully understand all the other UEFI entries.
If you unplug a drive, it seems to change to some sort of default.

Some have a Hard Drive boot entry that uses the fallback entry. External drives only boot from /EFI/Boot/bootx64.efi, but UEFI was updated to allow fallback boot from internal drives also which is /EFI/Boot/bootx64.efi. Many systems have that, but it is a copy of Windows .efi boot file. Using that has been a work around for  some systems that only wanted to boot Windows by description, so we made bootx64.efi on internal drive be a copy of grub's shimx64.efi instead of Windows's file to boot Ubuntu.

What is the device full message.
You do not have a lot of UEFI entries, so it should not be that. That had been a problem a couple of years ago.
So is one of your partition full.
Mount all your partitions from live installer, so they show and run this.
df -h

---

### Post by sunbear-c22 on 2019-04-06
In my system, I found that by going into **ASUS UEFI** --> **Boot Menu** --> and by **disabling Compatibility Support Module (CSM)**, this line will be eliminated:
```
 Boot0001* Hard Drive    BBS(HD,,0x0)..GO..NOs.......Y.B.P.X....................A..........................................Gd-.;.A..MQ..L.B.P.X........BO
```

So this is what I get now: 
```
$ sudo efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000
Boot0000* ubuntu    HD(1,GPT,fe1c10df-6af1-4ddf-829f-a9af111561aa,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
```

**Another benefit** of disabling CSM is that my **Grub2 splash screen now fills the entire monitor screen instead of appearing at a lower resolution. **:p

The partitions are not full. Checked, 80% max in one partition.

---

### Post by oldfred on 2019-04-06
When UEFI only, it must not show BIOS boot options, so your hard drive entry was a BIOS boot option.
Many also have the fallback entry shown as a hard drive entry, but it will be more similar to the Ubuntu entry but instead of shimx64.efi, will be bootx64.efi in /EFI/Boot folder.

UEFI entry looks correct.
And if only one install, you will not normally get a grub menu as you only have one system to boot.
To get to other entries like recovery entry, you have to press Escape key between UEFI screen & grub menu. If UEFI fast boot is on, you may not have time to press a key.

Black screen issue, is often a video issue. What video card/chip?

---

### Post by sunbear-c22 on 2019-04-06
> [COLOR=#000000]When UEFI only, it must not show BIOS boot options, so your hard drive entry was a BIOS boot option.[/COLOR]
Thank you for reminding me on why I enabled CSM previously; the HHD used a BIOS boot while the NVME SSD with a GPT partition table used an EFI Boot option.

I noticed Boot-Repair has some privacy issue. To resolve the > [COLOR=#000000]*Invalid output format export. Choose from value, device, list, or full*[/COLOR] error from the [COLOR=#000000][FONT=&quot]$ sudo update-grub2[/FONT][/COLOR] command, I am thinking that grub2 needs to be reinstalled and to use the approach mentioned in [https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd). However, I think the EFI Boot partition also needs to be mounted. Can you advice me on any other amendments needed?

---

### Post by oldfred on 2019-04-06
If you boot live installer in UEFI mode and the use Boot-Repair to repair an UEFI install it should work.
But it also has advanced mode.
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

