---
title: "No booting after installation"
date: 2017-03-29
forum: Installation &amp; Upgrades
---

### Post by vicentefong on 2017-03-29
Hi, I new on Ubuntu. After a nice and easy installation of 16.04 using a USB stick, the machine won't boot. I check some post and  I put again the USB and choose the "try without installation" option and follow the instructions for boot repair, but didn't work either. Now when i restarted the error is "Insert system disk in drive. Press any key when ready...."
[INDENT] 
 [/INDENT]
Here the log [http://paste2.org/sZL4fJHb](http://paste2.org/sZL4fJHb)

My machine is a Toshiba Ultrabook U925T-S2120

Regards,
Vicente

---

### Post by oldfred on 2017-03-30
Some Toshibas have the same issue as most HP & all Sony.
They have modified UEFI boot to use description. And only valid description for some odd reason is "Windows Boot Manager". 
That is specifically not allowed per UEFI standard. And Ubuntu has a policy statement that description should not be used.

The work around has been to create /EFI/Boot/bootx64.efi that really is grub or shim boot file and boot that, not ubuntu entry.
The bootx64.efi is a hard drive or fallback entry that UEFI uses & UEFI uses that for all external drives. But bootx64.efi can be anything.

It looks like Boot-Repair already copied shimx64.efi to bootx64.efi as you now have a backup of bootx64.efi as bkpbootx64.efi.
But it does not look like you have an UEFI entry to use that.

       You can add your hard drive entry to boot fallback file:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition 
Your ESP is sda2:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2


   Mine was sda, and ESP is sda1, so I used -p 1 to get this:
sudo efibootmgr -v
Boot0001* UEFI hard drive    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\Boot\bootx64.efi) 
    
Then see if you can boot that entry.

Other rename threads:
 Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba Satellite P55-A (UEFI) [SOLVED] Trouble installing Xubuntu 14.04 - file rename
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186) 

        Toshiba Satellite - turned Secure boot off in Boot-Repair update & UEFI
[https://ubuntuforums.org/showthread.php?t=2346022](https://ubuntuforums.org/showthread.php?t=2346022)
[http://ubuntuforums.org/showthread.php?t=2317643](http://ubuntuforums.org/showthread.php?t=2317643)
Toshiba satellite z930 copy shimx64.efi to /EFI/Boot/bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)
Toshiba Satellite C55-C5241  Windows vs. Ubuntu
[http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=broadwell-lap-winlin&num=1)

---

