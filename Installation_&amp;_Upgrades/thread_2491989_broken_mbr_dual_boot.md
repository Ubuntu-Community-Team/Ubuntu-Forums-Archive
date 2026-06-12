---
title: "broken mbr dual boot"
date: 2023-10-27
forum: Installation &amp; Upgrades
---

### Post by richlyn9 on 2023-10-27
Hi All,
i have a dual boot with Ubauntu and Windows over diferrent HDD's where the mbr is broken.
below is my -ls output
```
abc@xyz:~$ sudo parted -ls
Model: ATA WDC WD2500AAKX-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ntfs


Model: ATA ST3500418AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA Samsung SSD 750 (scsi)
Disk /dev/sdc: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  117GB  117GB   primary   ext4            boot
 2      117GB   120GB  3477MB  extended
 5      117GB   120GB  3477MB  logical   linux-swap(v1)


Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  473MB   472MB   ntfs         Basic data partition          hidden, diag
 2      473MB   578MB   105MB   fat32        EFI system partition          boot, esp
 3      578MB   595MB   16.8MB               Microsoft reserved partition  msftres
 4      595MB   105GB   104GB   ntfs         Basic data partition          msftdata
 5      105GB   1000GB  895GB   ntfs         Basic data partition          msftdata

```
i can boot in to ubuntu by pressng F12 and then choosing the OS.

i am referring to the below link to fix this issue
[https://support.system76.com/articles/bootloader/]("https://support.system76.com/articles/bootloader/")

based on my system i mounted dexv/sda1 as /mnt and sdd2 as /mnt/boot/efi
but it gave me an error while running  ```
for i in dev dev/pts proc sys run; do sudo mount -B /$i /mnt/$i;
```

was my dev mounted incorrect?

---

### Post by ajgreeny on 2023-10-27
You have a mix of msdos/MBR and gpt/UEFI  partitioned disks which will never allow all of them to boot from grub. Your Windows disk, sdd, has gpt partitions so Windows will be using UEFI. I suspect the two other disks may be using legacy BIOS.

See Boot-Repair in my signature below and follow the instructions to run the Boot-Info script.
**Do not run any repairs yet** simply post back here the Ubuntu pastebin link the report will show you.

---

### Post by richlyn9 on 2023-10-28
[https://paste.ubuntu.com/p/6555YnXhmG/](https://paste.ubuntu.com/p/6555YnXhmG/)

---

### Post by tea for one on 2023-10-28
[COLOR="#0000FF"]Line 15[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/sdd
[COLOR="#0000FF"]Line 79[/COLOR] - /efi/Microsoft/Boot/bootmgfw.efi 

Line 15 implies Windows in Legacy mode
Line 79 implies Windows in UEFI mode

Can you confirm that Windows is installed in UEFI mode on disk sdd?
(System Information > System Summary > BIOS mode > UEFI)

---

### Post by richlyn9 on 2023-10-28
Yes The windows 10 is installed in UEFI Mode

---

### Post by tea for one on 2023-10-28
Windows 10 installed in UEFI mode - good news

Now, I suspect that Ubuntu 16.04 on sdc is installed in Legacy mode?
Can you boot into Ubuntu via F12, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Please post the command and output in code tags

---

### Post by richlyn9 on 2023-10-28
```

abc@xyz:~$ [ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
UEFI
abc@xyz:~$ 

```

---

### Post by tea for one on 2023-10-29
Ubuntu in UEFI mode - again good news.

I wonder if a Windows update took precedence over Grub.
Anyway, let's try and get Grub to do its work.

Make sure that Windows is not hibernating or encrypted.
Boot into Ubuntu via F12
Check that the Ubuntu disk is still [COLOR="#0000FF"]sdc[/COLOR]
Open a terminal
```
sudo grub-install /dev/sdc
```
Hopefully, Windows Boot Manager will be added because you have [COLOR="#0000FF"]GRUB_DISABLE_OS_PROBER=false[/COLOR] in your grub file.

If that works, there is more to do.
You are using 16.04, which is now unsupported.

Backup all your data.
Download your preferred flavour of Ubuntu 22.04 and install in UEFI mode with GPT.

---

### Post by yancek on 2023-10-29
In situations like this, it is always best to indicate which version/release of windows and/or Ubuntu you are using in your initial post.  In your initial post, you indicated that when you tried to use the mount command, you got an error but failed to post what that error was.

What exactly is the problem?  You indicate that you can boot Ubuntu by using the F12 key in the BIOS.  Do you not get a Grub menu to with boot options?  Can you boot windows in the same manner as it is on a different drive?

Ubuntu and windows are both UEFI installs and thir EFI files are both on drive sdd.  Is that drive currently set to first boot priority and you get your current problem?
What do you have on sda and sdb?  Are those simply data drives?

You ran boot repair in Legacy mode rather than UEFI mode so it would not make the correct repairs.  I'm not really sure what the problem is as the only thing I see you posted is that you need to use the F12 key to access Ubuntu.  To change that, you need to go into the BIOS firmware and set Ubuntu to the first boot option if you want the Ubuntu Grub menu to show.

FYI, with regard to mixing Legacy and EFI installs, I have found that a Legacy install of Linux will boot an EFI install of windows, IF windows is on a different drive.  Your installs of Ubuntu and windows are on different drives but are both EFI so that should not be a consideration.

---

### Post by richlyn9 on 2023-10-29
while mounting the error i got is as below

```
abc@xyz:~$ sudo mount /dev/sda1 /mnt
[sudo] password for xyz: 
abc@xyz:~$ sudo mount /dev/sdd2 /mnt/boot/efi
mount: mount point /mnt/boot/efi does not exist
abc@xyz:~$ 
```


I do get the grub menu which takes me to the rescue command, this is tried to fix a long time ago and dont remember what precise errors it gave me however, i tried a different method now describer in the first post.

the error at the grub rescue is as below:

```
error file: /boot/grub/i386-pc/normal.mod not found
entering rescue mode
grub rescue>
```

---

### Post by richlyn9 on 2023-10-29
Will try this and post back
I did try to upgrade apparently i need to install all updates before upgrading which itself ia giving an error.

---

### Post by yancek on 2023-10-29
If you are trying to mount partitions on a drive while booting from the 'live' install usb of Ubuntu, you need to first create the /boot/efi directory under /mnt.  The standard place for it is of course, /boot/efi which you would use if you were trying to reinstall from a booted and installed system.  Add the line below to the commands:

```
mkdir /mnt/boot && mkdir /mnt/boot/efi
 
```

Then run the other commands to mount and install and make sure you are booted in UEFI mode as the error you report indicates not.

```
 error file: /boot/grub/i386-pc/normal.mod not found
```

---

### Post by richlyn9 on 2023-10-30
Thanks  tea for one, ajgreeny & yancek  for your guidance.
your guidance resolved my issue.

Now for the upgrade. :)

---

