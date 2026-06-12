---
title: "Boot-repair didn't help on Lenovo Z580 &quot;error: unknown filesystem&quot;"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by PaulMc75 on 2013-03-08
Hi all,

[http://paste2.org/p/3081940](http://paste2.org/p/3081940)

Hope you can help.

I have windows 8 on one partition, and had an ubuntu installation that I managed to break by upgrading the nvidia drivers on another.  I decided I'd give linux mint a try and when this installed grub borked out with "error: unknown filesystem" . I've tried boot repair (twice now) and I still get the same problem when I boot.

Any help much appreciated.

Thanks,

Paul.

---

### Post by PaulMc75 on 2013-03-08
I may be OK now, I followed the instructions here [http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue](http://askubuntu.com/questions/142300/how-to-fix-error-unknown-filesystem-grub-rescue), this got me my grub menu back.  Mint would only boot every now and again (if I entered the BIOS and out again, then it would boot).  I then ran boot-repair again, and it (fingers-crossed!) seems to boot OK now into windows and mint.

I'll come back if I continue to have problems with the intermittent boot.

---

### Post by oldfred on 2013-03-08
You have Windows 8 installed in UEFI mode with gpt partitioning.

But you show a grub installed to the gpt drive's protective MBR. You can boot gpt drives in BIOS mode with Ubuntu, but it makes dual booting Windows in UEFI mode very difficult as you have to go back into UEFI and turn it on or off to boot Linux in BIOS mode.

Best to have Linux in UEFI mode. And Ubuntu is one of the few that will work with secure boot versions of Windows. With secure boot off then other Linux may also work.

Boot-Repair will convert a BIOS install of Ubuntu to UEFI by uninstalling grub-pc (BIOS) and installing grub-efi (UEFI) if drive is gpt.
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

---

