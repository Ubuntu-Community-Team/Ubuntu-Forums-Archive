---
title: "Sudden Boot Issues"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by jim139 on 2016-05-22
Hi all,

I've been dual booting 16.04 (originally 15.10) and Windows 10 for a while. The windows instance has barely been used but yesterday I loaded it up and performed some updates e.t.c.

Now it seems like either Windows or the Dell Software has altered the boot since it now always boots directly into windows.

I've tried altering the boot settings and sequence with no luck.

Boot repair seemed to make no difference - it still boots straight to windows. The boot info it provided is here: [http://pastebin.com/pMLY4E8e](http://pastebin.com/pMLY4E8e). Following the instructions at the bottom also didn't seem to make  difference.

It's a Dell Inspiron 15 5000 series laptop.

Any advice/pointers would be appreciated.

---

### Post by grahammechanical on 2016-05-22
I can give you one piece of information from the BootInfo summary report. The update to Windows has switched hibernation (fast boot) back on. I have no idea if this is the cause of the problem. It certainly is preventing Boot Repair from doing what it wants.

> Windows is hibernated, refused to mount.Failed to mount '/dev/sda3': Operation not permittedThe NTFS partition is in an unsafe state. Please resume and shutdownWindows fully (no hibernation or fast restarting), or mount the volumeread-only with the 'ro' mount option.



At least the Windows update did not re-write the partition table without including Linux partitions. I have heard of that happening.

Regards.

---

### Post by ubfan1 on 2016-05-22
Windows 8-10 does seem to occasionally turn the fast-boot option back on, but Windows 10 has now buried the switch down in the advanced options for power.  Dig around a bit and you will find it.  The large number of FSCK... files in your EFI partition is something I haven't seen either, maybe a disk problem?

---

### Post by jim139 on 2016-05-22
I've disabled the fast boot option, this does seem to remove some of the  error messages in the boot repair log but unfortunately it seems to  have had no other effect.

Latest paste is [http://pastebin.com/E32ySy3r](http://pastebin.com/E32ySy3r)

> **ubfan1 said:**
> maybe a disk problem?

It's possible though the laptop is fairly new.

Thanks for the help.

Edit: One thing to add, if these kinds of issues usually take a while or are a  hassle to troubleshoot am I just better biting the bullet and doing a  reinstall of Ubuntu?

---

### Post by oldfred on 2016-05-22
You show boot order as 0002, 0000, 0001

0002 is bootx64.efi or hard drive boot entry or fallback.

That file is normally a copy of Windows /efi/Microsoft/Boot/bootmgfw.efi, but Boot-Repair usually backs up bootx64.efi and makes it shimx64.efi so hard drive entry will boot Ubuntu/grub. You probably have to check sizes to know which it is, or when booting that entry with f12, what boots.

And your UEFI entry for Windows already boots shim. That was an old fix for systems that would only boot Windows, but Windows updates overwrites it. Dell's usually do not need that fix. I might add a correct Windows efi boot entry.
      >  Boot0000* [COLOR=#ff0000]Windows Boot Manager[/COLOR]    HD(1,GPT,62cd36d6-cc32-4adf-b610-6329bdd93864,0x800,0xfa000)/File([COLOR=#ff0000]EFIubuntushimx64.efi[/COLOR]) 

    
     

It still is running fsck on the ESP. I might also try chkdsk from Windows. 
Or as last resort, fully backup all of ESP, it is not huge.
Delete  partition, recreate FAT32 partition with boot flag and copy backup back in. 
ESP only need .efi files to boot, no install like with BIOS to MBR required, so copy of files works.

---

### Post by jim139 on 2016-05-22
Thanks for the help everyone. dosfsck on the EFI partition claimed it had a dirty bit set. Clearing this and some manual cleanup of the ubuntu folder and rerunning boot repair solved my problem.

---

