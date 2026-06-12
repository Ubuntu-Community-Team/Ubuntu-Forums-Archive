---
title: "Boot repair: can't boot from windows after installing ubuntu"
date: 2023-12-22
forum: Installation &amp; Upgrades
---

### Post by 0-ben on 2023-12-22
Hello,

I'm having trouble booting into Windows after reinstalling Ubuntu on my machine.
A couple things:
[LIST]
[*]I was able to boot into Windows after creating the partition that now holds Ubuntu, so I don't think there's an issue with that.
[*]I am not able to load Windows directly from the bios boot menu
[*]I have tried the "Recommended repair" option in boot repair but with no success
[/LIST]
Here is my report from boot repair: [https://pastebin.ubuntu.com/p/hcXXhfCRGF/](https://pastebin.ubuntu.com/p/hcXXhfCRGF/)

Thank you for your help!

Ben

---

### Post by oldfred on 2023-12-22
Boot-Repair is for Linux system repair, it does not fix Windows boot issues.
Your ESP nvme0n1p1 shows no /EFI/Microsoft folder which should have Windows boot files?

During install did you reformat the ESP, erasing the Windows boot files?
You do show a Windows UEFI boot entry in UEFI boot menu for same GUID/partUUID, so that would indicate it was not reformatted. 
But then where are Windows files, or is report not showing them?

You also have two Elementary entries, lines 86 & 87, but neither have folders in ESP so those were also erased.
And one 0003 line 86 refers to a GUID for an ESP that does not exist, or an old install with a different or reformatted ESP.

You will need to boot your Windows repair/recovery flash drive to see if that will repair your Windows boot.

You can delete the Elementary UEFI boot entries with efibootmgr & its -b XXXX -B option.
man efibootmgr
[https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

