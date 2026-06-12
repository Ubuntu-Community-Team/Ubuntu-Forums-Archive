---
title: "move Raid1 from MBR to UEFI without reinstall"
date: 2022-02-05
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2022-02-05
I have a fairly basic Ubuntu Desktop with two partitions "/" & "/home" together with another disk running Windows 10. 

So strictly speaking I'm not dual booting, although I can boot either system from grub or BIOS.

Both Ubuntu and Windows are booted with the legacy setting in the bios, but I need to change this to UEFI due to Windows 11 requirements.

While there is lots of info on how to do this, I couldn't find much info on the best approach (other than a reinstall) for systems that use raid; in my case raid1.

Thanks

---

### Post by oldfred on 2022-02-05
Windows requires gpt partitioning for UEFI boot. And normal reinstall with conversion erases drive.
There are tools to convert, but multiple posts of user that tried the Windows tools to convert a BIOS/MBR install to UEFI/gpt ended up reinstalling.

Ubuntu will let you install in UEFI boot mode to MBR partitioned drives, but really should not.
Is drive gpt, I started to use gpt in 2010, back then with BIOS.

For UEFI boot you will have to add an ESP - efi system partition which is FAT32 formatted with boot,esp flags (when using gparted).

Post these inb code tags:
sudo parted -l
lsblk -e7  -o FSTYPE,NAME,LABEL,PARTLABEL,SIZE,FSUSED,MOUNTPOINT

---

### Post by linux-sysop on 2022-02-06
Gparted has the ability to shuffle partitions and even copy paste from one HD to another.  I recently used Gparted (from Live USB) and removed all the partitions from a drive to a temporary HD.   Then I reformatted the drive from MBR to GPT, copied the partitions back without issue.  I will state, it is a good thing there was no power loss, or I would be starting all over.  The total operation took several hours, however I was dealing with over 800 GB in files.

@oldfred Windows 10 doesn't require UEFI to boot, it can be setup to use MBR. I have set Windows 10 to run in MBR.
Factory settings are UEFI, I am sure Microsoft love us all using their boot manager. I wouldn't be a bit surprise Windows 11 demands it.

---

### Post by oldfred on 2022-02-06
Microsoft wanted to make Windows 8 UEFI only. But large customers with 100's or 1000's of systems some newer Windows 7 systems that would not support UEFI wanted to be able to update to Windows 8 on old systems. So BIOS installs were allowed, but only to MBR partitioned drives.

Now vendors are making new systems UEFI only. One of the announcements.
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by MAFoElffen on 2022-02-06
Just my thoughts if it was me, and mine. I think a safer plan would be for a migration plan: backup, reinstall fresh on disks with new GPT partition tables, migrate applications, data and settings to the fresh system.

I know you said "without reinstall", but that. to me, is not a safe option. Migration, if you do it right, can be painless.

I know people say you can convert MBR to GPT, but you risk losing everything on that disk in the process... And end up spending much more time and effort trying to make that work. All the while, under the premise of saving you effort and time. Lessons learned from my own experiences on that.

---

### Post by linux-sysop on 2022-02-10
Depending on your hardware, dual booting Windows/Linux might be considered "old school" as [this Linux YouTuber]("https://youtu.be/w473rRf9aYA") has shown using Qemu VM and booting Windows from within the Linux OS.

As long as you are using your Windows OS license (OEM number on your case) this is perfectly a legit way to access Windows.  I am not a gamer, but the only issues I have read, are about games running EAC (easy anti-cheat), where it detects the VM, and stops you from starting the game. 

I imagine the majority of people who run both Linux and Windows, need Windows for game related issues.  If this gets much better, it could be the standard setup for using both OS on the same PC.

---

### Post by ActionParsnip on 2022-02-10
Make sure you have a full backup of your important data before starting

---

