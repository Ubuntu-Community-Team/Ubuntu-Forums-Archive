---
title: "Problem installing Ubuntu after Windows"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by john_connor2 on 2016-02-14
Hello, I am posting this from a Live CD.

Since I installed Ubuntu, I lost the dual-boot I used to have. I used to be able to choose between several operating systems. Now I dont even get a prompt from grub (but I know that the Windows partition is there..).
I managed to make grub prompt and made a entry for the windows8.1 partition, and when I try to boot from it I get ***invalid EFI path***.

Now from a Live CD I managed to run boot repair, but I get :

```
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.
```

I did not wanted to mess with the system, so I didn't do anything yet.. I don't know if the Windows installation was done under BIOS or UEFI (how can I know?) . What if one was under BIOS and the other from EFI? Am I screwed?

I want to be able to dual boot to both systems.

output from parted -l : 
```

Model: ATA WDC WD3200AAJS-2 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs         boot


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name  Flags
 1      1049kB  538MB  537MB   fat32              boot
 2      538MB   492GB  491GB   ext4
 3      492GB   500GB  8485MB

```

---

### Post by oldfred on 2016-02-14
UEFI & BIOS boot modes are not compatible.
Or from grub menu, you can only boot systems installed in the same boot mode as grub.
It looks like Ubuntu/grub is in UEFI boot mode.
And it looks like Windows is in BIOS/MBR boot mode. Windows only boots from MBR(msdos) partitioned drives with BIOS.

You can add the tiny 1 or 2MB unformatted partition with the bios_grub partition with gparted on sdc, and install a BIOS boot version of grub to sdc drive with Boot-Repair. Only use adanced mode to install grub. Keep Windows BIOS boot loader on Windows drive.

Or you can use UEFI as boot manager. You should be able to use f10 or f12 or similar one time boot key to choose system. Some do still require you to turn on/off UEFI or CSM/BIOS/Legacy boot mode. But mode recognize the way system wants to boot.

---

### Post by ajgreeny on 2016-02-14
We really need the full output report from Boot-repair please, but you appear to have two hard disks with msdos partition tables:-
sda, 320GB, with a single 320GB NTFS partition on disk,
sdb, 500GB, with no partition yet made,

and one hard disk with gpt partition table:-
sdc, 500GB, with two partitions, 537MB fat32, 491GB ext4, and 8485MB of presumably unallocated space.

It's difficult to say more at this stage, other than it would seem likely that your Windows OS is installed in BIOS mode not UEFI, as it is on an msdos partition table.

Run Boot-repair again and show us the pastebin link it will give you when you choose the boot-info script.

EDIT:
Beaten to the reply by oldfred who knows a great deal more about this than I, so listen carefully to what he says and you should do well.

---

### Post by john_connor2 on 2016-02-14
> **oldfred said:**
> UEFI & BIOS boot modes are not compatible.
Or from grub menu, you can only boot systems installed in the same boot mode as grub.
It looks like Ubuntu/grub is in UEFI boot mode.
And it looks like Windows is in BIOS/MBR boot mode. Windows only boots from MBR(msdos) partitioned drives with BIOS.

You can add the tiny 1 or 2MB unformatted partition with the bios_grub partition with gparted on sdc, and install a BIOS boot version of grub to sdc drive with Boot-Repair. Only use adanced mode to install grub. Keep Windows BIOS boot loader on Windows drive.

Or you can use UEFI as boot manager. You should be able to use f10 or f12 or similar one time boot key to choose system. Some do still require you to turn on/off UEFI or CSM/BIOS/Legacy boot mode. But mode recognize the way system wants to boot.

Hello fred, thank you for answering. Grub was installed before on the 320gb partition (the other 500gb msdos part. Is just trash i just formatted) and if I try to boot it in BIOS it gives me no such device and goes to grub rescue. What should I do?

---

### Post by oldfred on 2016-02-14
What brand/model computer.

Best to see details on where you now are at. You can install into live installer and run report.
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by john_connor2 on 2016-02-15
Here it goes [http://paste.ubuntu.com/15077905/](http://paste.ubuntu.com/15077905/)   The computer is a desktop computer. The motherboard is an ASUS M5A97 R2.

---

### Post by yancek on 2016-02-15
As indicated in the earlier post by oldfred, you have mixed an MBR install (windows) with a UEFI install (Ubuntu) and seen the result.  Complicating matters further, for some reason you have Grub code in the MBR of the windows only drive, sda.  To repair that, you will probably need the windows installation medium and select the repair option.  Not sure what the exact steps are as I don't use windows.

Not sure what your situation is but it might be simpler to reinsall Ubuntu in MBR as that is what you have for windows.  If that is not a good option in your case, wait for someone to come along with other suggestions

---

### Post by john_connor2 on 2016-02-15
There is grub code in the windows partition because i had a previous dual boot installed there. What if I reinstall grub in that partition? Is there a tool to install grub/mbr from a live cd?

---

### Post by yancek on 2016-02-15
> There is grub code in the windows partition because i had a previous dual boot installed there

It's not on a windows partition, it's in the MBR of that drive.  That alone won't prevent booting.  You are getting invalid EFI path when you try to boot windows because it is not installed using UEFI, it is using MBR.  The suggestion you got from the output was to create the small BIOS boot partition on sdc which was also suggested by oldfred in his post.  I don't know what you would do with the EFI partition on the sdc drive if anything.  If you do that an can boot Ubuntu, you should be able to run sudo update-grub and get an entry for windows. I don't use EFI myself so can't give you any more ideas other than to check the links posted above.

---

### Post by john_connor2 on 2016-02-16
If i reinstall windows on another drive, will I be able to dual boot?

---

### Post by ajgreeny on 2016-02-16
I am not certain about this, but I believe it is possible to change the boot mode of Ubuntu from BIOS to UEFI (and vice-versa) using Boot-repair, but it may be easier to wait for oldfred to confirm that, if he comes along and tries to help again here.

A quick search shows that I am correct;  have a look at [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_UEFI_or_Legacy_mode)

---

### Post by Geoffrey_Arndt on 2016-02-16
Also, see post #3 from OldFred in this current thread, most of this applies to your install as well  . . . 

[http://ubuntuforums.org/showthread.php?t=2313728](http://ubuntuforums.org/showthread.php?t=2313728)

---

### Post by oldfred on 2016-02-16
You can only dual boot if both systems are installed in same boot mode.

I would suggest reinstalling a Windows boot loader to sda for Windows BIOS boot directly from UEFI/BIOS.

And add a 1 or 2MB unformatted partition with the bios_grub flag using gparted on sdc.

Then use Boot-Repair to uninstall the UEFI version of grub and install grub-pc for BIOS boot. Use Boot-Repairs advanced mode. Boot Ubuntu installer in BIOS mode, not UEFI. And from Boot-Repair's advanced options choose the full uninstall/reinstall of grub. Also see link by ajgreeny above as it shows Boot-Repair and also has similar instructions.
Set BIOS to boot from sdc, and if issues with Ubuntu drive at any time you then can directly boot Windows from sda with BIOS or one time boot key, often f10 or f12.

Then you should be able to dual boot both systems in BIOS boot mode.

---

### Post by john_connor2 on 2016-02-16
Thank you fred, really appreciated. I will do that and come back.

---

