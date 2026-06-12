---
title: "Dual boot installation completely broken"
date: 2017-10-16
forum: Installation &amp; Upgrades
---

### Post by aroaro on 2017-10-16
I am returning to Ubuntu after a few years and I'm having a problem I never had in the past.

My PC has Win 7 on one drive that is not partitioned. I have an external USB drive with two partitions. On one of them I installed Ubuntu (using the 'Something else' option when installing).

After that, nothing worked anymore. When I reboot, I get in the terminal something like 'Gmeo error" and "grub rescue >" and that's it. No Ubuntu and no Windows.

I rebooted from the USB flash drive and ran boot-repair, but it didn't help. This is the output from that: [http://paste.ubuntu.com/25750701/](http://paste.ubuntu.com/25750701/)

Any ideas as to how to get my computer back?

---

### Post by oldfred on 2017-10-16
After running Boot-Repair and the reinstall of grub to sdb, it still does not boot Ubuntu?

Have not seen many (any?) 6TB drives.
You do have to have the bios_grub and grub says that can be anywhere on drive. But I typically make it the second partition. And my first partition is an ESP - efi system partition in case I want to install Ubuntu in UEFI boot mode.

Report says grub in gpt's protective MBR is looking at wrong sector for rest of grub. That sector should be first sector of bios_grub partition. Reinstall of grub should have fixed that and it did not show an error on reinstall.

You used Windows to partition drive as it always adds the system reserved partition. That is required before the first NTFS bootable partition on gpt drives. But since external and Windows will not install/boot from external drives, you do not need the system reserved. If concerned you think you need it, you can just shrink it by a couple MB and put bios_grub after it (remove other bios_grub). Then reinstall grub to sdb with Boot-Repair or manually. 
If then it works we know that was the issue.

---

### Post by aroaro on 2017-10-16
Thank you for your reply. Yes, the 5TB drive was a good one day deal on Amazon, so I jumped on it. So far it's been good.

I reinstalled Ubuntu many times, and I ran Boot-repair even more times. Last time I figured that Windows won't be able to start from the external USB, so I had Boot-repair install grub on sda (Windows). This is the output: [http://paste.ubuntu.com/25753021/](http://paste.ubuntu.com/25753021/)

It doesn't give me options when I restart. It starts Windows in safe mode, it says there are problems and runs check disk, and then it says it's done and it can't do anything...

---

### Post by oldfred on 2017-10-16
With gpt grub has to boot thru or using the bios_grub partition.
So we need to test if having that at end is the issue.

You have a Windows boot loader, syslinux in the MBR of sda. You could reinstall the Windows boot loader, but have to use your Windows repair flash drive.
Do not know if your use of EasyBCD is confusing things. With two drives you do not need EasyBCD for booting.
You can either boot from drive using BIOS or use grub as default and it will boot Windows or Ubuntu.

What brand/model system?

---

### Post by aroaro on 2017-10-16
Now I am really worried. 

I booted from a Windows DVD, it found problems with the booting process, it fixed them and... nothing changed. When I restart, I get the same blue screen of death. At this point I don't know what to do anymore. This is very weird. In the past I used Debian for years, then used Ubuntu for a while and I never had anything like this.

I might have to reinstall Windows, which would be a huge pain. At least my data is all on the external drive, but my applications data and settings would be gone. This is very sad.

The computer is a Dell Optiplex 780.

---

### Post by oldfred on 2017-10-17
Did you just let Windows run its fixes, or did you go to repair console's command prompt and run the normal set of repair commands.
And if chkdsk, you have to run until there are no errors as it does not fix everything on one pass.

       oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by aroaro on 2017-10-17
Thanks for your help. At this point I just reinstalled Windows. I created a partition on the hard drive and installed Ubuntu on it. It all runs fine now without any effort. That Ubuntu installation on the external USB must have messed up everything for some reason.

Grub boots the computer now, but I want to have Windows do it, just in case I ever want to install another Linux on that partition. I'll have to figure out how to do that. Maybe with EasyBCD....?

As far as the previous efforts, I let Windows Setup repair to run the fixes. It said it fixed the booting, checked the disk and it tried to restore to an earlier date. Nothing was successful.

---

### Post by oldfred on 2017-10-17
Some users have posted they use EasyBCD, but  it requires a configuration that grub2 does not recommend.

EasyBCD adds a BCD entry to use the now very old grub4dos to chain load to grub2 in a partition boot sector (PBR or BS).
But grub2 is larger than grub legacy and does not really fit in a PBR and has to convert to blocklists which are unreliable.

If you have another MBR, external drive, flash drive or whatever better to use that for grub.
You still could use EasyBCD to chain load to that MBR rather than a PBR.

---

### Post by aroaro on 2017-10-17
So there is no way to make Windows handle the boot process?

---

### Post by oldfred on 2017-10-17
The only one I know of is EasyBCD.
Most of us use grub to boot Windows.

As long as Windows is not hibernated nor needs chkdsk, grub will boot Windows.
But grub only boots working Windows, so best to have Windows repair disk to fix it when it breaks. But you should have that anyway to fix Windows issues.
And you should always have good backups.

---

### Post by aroaro on 2017-10-17
Ok, I'll let grub do the job. Now I can finally start chasing the packages that I need and set them up.

---

