---
title: "Windows 10 won't boot from GRUB - (Anyone want a challenge?)"
date: 2019-07-14
forum: Installation &amp; Upgrades
---

### Post by satoshilluminati on 2019-07-14
Hi,

This is an attempted, and failed, dual boot of Ubuntu and Windows 10.

**Specs**: Alienware Area-51, **OS**: Ubuntu 18.04.2,  **Inaccessible  OS**: Windows 10 

Here's some information from **Boot Repair**

> Boot successfully repaired.

Please write on a paper the following URL:

[http://paste.ubuntu.com/p/4367sGzjPG/](http://paste.ubuntu.com/p/4367sGzjPG/)

> In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb2/EFI/ubuntu/shimx64.efi file!

The boot files of [The OS now in use - Ubuntu 18.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].


I also updated **/etc/grub.d/40_custom** to contain:

```
menuentry "Windows 10" {
        insmod part_gpt
        insmod chain
        set root='(hd0,msdos2)'
        chainloader +1
}
```

However, I just copy and pasted that from a random tutorial I found in Google. So while "Windows 10" shows up in GRUB; but the code is clearly incompatible here because this appears when I click it in GRUB

> error: disk 'hd0,msdos2' not found.

Press any key to continue...


I've tried things from a lot of tutorials; but none seem to work. Does anyone care to help?

I love you,

Satoshilluminati

---

### Post by jeremy31 on 2019-07-14
You might want to try (hd1,gpt1)
Strange that boot repair shows Windows is MBR of sda and sdb as if it was installed in Legacy mode and Ubuntu appears to be installed UEFI

---

### Post by sevendogs1337 on 2019-07-14
Curious if you have tried os-prober. Os-prober will do all of the customization for you, you just have to run grub-update, or whatever Ubuntu uses, after you run os-prober. Os-prober is installed by default in 18.04.

---

### Post by satoshilluminati on 2019-07-14
> **jeremy31 said:**
> You might want to try (hd1,gpt1)
Strange that boot repair shows Windows is MBR of sda and sdb as if it  was installed in Legacy mode and Ubuntu appears to be installed  UEFI
Yeah. No clue.


> **sevendogs1337 said:**
> Curious if you have tried os-prober. Os-prober will do all of the customization for you, you just have to run grub-update, or whatever Ubuntu uses, after you run os-prober. Os-prober is installed by default in 18.04.
That used to work. Now it just outputs a null response.

I should also mention 2 other things

1. "sudo update-grub" never returned "Found Windows 10" like it appears to for most
2. I also posted this to stackexchange and there are some pretty grim comments: [https://askubuntu.com/questions/1158242/windows-10-wont-boot-from-grub-anyone-want-a-challenge](https://askubuntu.com/questions/1158242/windows-10-wont-boot-from-grub-anyone-want-a-challenge) :confused:

---

### Post by oldfred on 2019-07-14
Your Windows NTFS partition is not showing any boot files, it looks more like a data partition.

Windows only boots in UEFI mode from gpt partitioned drives and you show no UEFI entry for Windows nor any /EFI/Microsoft folder in ESP for UEFI boot. Both drives are now gpt.

You do have Windows BIOS boot loaders in gpt's protective MBR of both sda & sdb for BIOS boot, but Windows only boots in BIOS mode from MBR(msdos) partitioned drives. NTFS partition does not show any boot files at all. BIOS mode would show multiple files & even UEFI mode shows one file, with most in ESP - efi system partition in the /EFI/Microsoft folder.

Not sure if this is repairable. Normally we like to try to repair before suggesting reinstall. Either way make sure you have good backups for both Ubuntu & Windows. And install & repair media for both systems.

Know difference between UEFI & BIOS boot as how you boot install media, is then how it installs and expects the default boot in UEFI to be set.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by satoshilluminati on 2019-07-14
> **oldfred said:**
> Your Windows NTFS partition is not showing any boot files, it looks more like a data partition.

Windows only boots in UEFI mode from gpt partitioned drives and you show no UEFI entry for Windows nor any /EFI/Microsoft folder in ESP for UEFI boot. Both drives are now gpt.

You do have Windows BIOS boot loaders in gpt's protective MBR of both sda & sdb for BIOS boot, but Windows only boots in BIOS mode from MBR(msdos) partitioned drives. NTFS partition does not show any boot files at all. BIOS mode would show multiple files & even UEFI mode shows one file, with most in ESP - efi system partition in the /EFI/Microsoft folder.

Not sure if this is repairable. Normally we like to try to repair before suggesting reinstall. Either way make sure you have good backups for both Ubuntu & Windows. And install & repair media for both systems.

Know difference between UEFI & BIOS boot as how you boot install media, is then how it installs and expects the default boot in UEFI to be set.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
Yowza. Thanks.

---

