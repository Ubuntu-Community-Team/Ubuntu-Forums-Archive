---
title: "Windows 8/Ubuntu Dual boot issues"
date: 2013-03-07
forum: Installation &amp; Upgrades
---

### Post by chunkypeanutlove on 2013-03-07
So after my 5yr old laptop met an untimely death via the hands of a cup of water i decided to buy a new one. I got a lenovo ideapad. It came with windows 8 installed so I decided to try to dual boot. I am having so many issues. after finding out about uefi, last windows system I owned was xp, I knew there was going to be trouble. Lenovo has a lot of tiny partitions pre-installed that make no sense to me but i havent messed to me. 

I tried to fix the boot issue with boot-repair and its still now working. I have been thinkering around for 4 days on it so now i am in need of help. 

[http://paste.ubuntu.com/5592322/](http://paste.ubuntu.com/5592322/)

thanks in advance.

---

### Post by chunkypeanutlove on 2013-03-07
sorry, the issue is that i cant load windows 8 from grub. If i want to load windows 8 i need to get into bios and move the boot order around. To boot ubuntu i have to do the same but boot ubuntu first

---

### Post by oldfred on 2013-03-07
You should use UEFI to change boot order not Windows. 

Does this entry not boot Windows? Not sure why it says recovery.
 menuentry "Windows UEFI recovery bkpbootmgfw.efi" 
This one should boot to recovery as it uses the UUID of recovery efi files:
menuentry "Windows Boot UEFI recovery bkpbootx64.efi" 

Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

And boot entries from os-prober will not work.
      grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

