---
title: "Dual boot win8.1 crashing"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2016-03-13
Hi, I have followed a couple of different tutorials on dual boot Ubuntu with win8.1. Each time they trashed windows.

The first one did not show Grub at the start so it went straight to windows. I then used the 
bcdedit {bootmgr} path /EFI/Ubuntu/grubx64.efi

That trashed windows so I started again by restoring windows, then installing Ubuntu again and again, no grub at start, so this time tried

bcdedit {bootmgr} path /EFI/Ubuntu/shimx64.efi

Both times it showed Grub but then trashed windows again. It takes about an hour to restore windows and install Ubuntu each time, so now I am looking for instructions that are NOT going to trash it all again.

Anyone have this working? How?

Thanks

---

### Post by fantab on 2016-03-13
We need more info... Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") utility to create BootInfo Summary, and post the link here. Do Not run any repairs, just create the bootinfo..

---

### Post by FerryGnu on 2016-03-14
Thanks fantab, but I had to reinstall win image and that then trashed the Ubuntu installation. I am downloading boot-repair  as I type and will install Ubuntu again, will that provide the information you need? It will automatically boot to windows. I can then  boot the disk-repair and get the information, but you don't state of what you want and when. After the trashing of windows or after the install and no grub?

Update.

I reinstalled Ubuntu then booted to Disk-Repair USB. It then said I needed to disable secure boot to proceed. I did that then it would not boot again.

I have an option in the UEFI/BIOS for booting ubuntu which also shows up in the windows F12 boot menu. But, if I select that I then get grub to make a selection. Not quite as fluid (user-friendly) as I expected, but it does work - except, if I decide from grub that I want to boot windows it again crashes and trashes with a very long error message about not finding a windows .efi file.

Might just give up and wait another year to see if Ubuntu installs get better. It is better than last time I tried, but still not there yet. 

I am quite techy with windows (programmer 30+ years) and for me this is not an easy situation. If Canonical wants people to choose Ubuntu over windows it has got to be smoother than this. With the horrific privacy intrusions win10 is making and getting worse with, this is a prime time for Canonical to leap ahead with Ubuntu. BUT -- a neophyte would drop back to the disgustingly pervasive win10 in a heartbeat.

---

### Post by oldfred on 2016-03-14
If you do not want to boot Windows, the Ubuntu install works easily.

But a few manufacturers violated UEFI spec and only boot by description. And that description has to be "Windows Boot Manager".
We have work arounds for all the issues on various brands, but it is Microsoft & the vendors that make it difficult. And there is not much that any Linux can do other than create work arounds.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor. 
   UEFI 2.3 -it is permitted for the firmware to treat the EFI system partition in the same way as removable media or use bootx64.efi 
[http://mjg59.dreamwidth.org/4125.html](http://mjg59.dreamwidth.org/4125.html)

---

### Post by FerryGnu on 2016-03-14
Thanks, but I want to be able to choose as I need to boot both several times a day.

I went to the page 2147295 and interestingly - or not, there is a file causing a fault when trying to save it. I need to see the page but I also need to shut own this laptop. So, I was going to display the page in a browser on another PC on drive N: that does not have Internet access. But, I get this error, just wondering if it might have been a code-injection!! {gasp} Not again!! LOL
...
"N:\_Transfer\UEFI Installing - Tips_files\kajtek58 could not be saved, because the source file could not be read. Try again later, or contact the server administrator."

---

### Post by oldfred on 2016-03-14
Do not know about Windows but an underscore as first character is unusual.
And in Linux best not to use spaces in files or folder names. Once I started using Linux I quickly converted to onename, under_score, or CamelCase.

But we know more about Linux issues, not Windows issues.

---

