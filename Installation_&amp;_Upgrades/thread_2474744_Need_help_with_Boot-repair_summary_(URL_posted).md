---
title: "Need help with Boot-repair summary (URL posted)"
date: 2022-05-06
forum: Installation &amp; Upgrades
---

### Post by furrati on 2022-05-06
Hello, I installed Ubuntu alongside Windows 10 using the option provided in the installation process (moved the slider to make the space for Ubuntu). Then, once the installation finished it restarted my computer and the following error keeps popping up:

[B]&#8220;Reboot and select proper Boot Device&#8221;

[/B]Neither Ubuntu nor Windows 10 starts up or is available. I tried looking at the "Install Ubuntu" option again to see if Windows 10 is detected and it is, along with Ubuntu.

I looked at my boot order and my main HDD is listed as the first option, I never changed it from that position. Now I'm on the Live Ubuntu session ("Try Ubuntu") to see if someone can help me and check the boot-repair summary that I ran, below is the URL.

[https://pastebin.ubuntu.com/p/zK82SXvKPk/](https://pastebin.ubuntu.com/p/zK82SXvKPk/)

I would like to know if I can go ahead and run the recommended repairs. Thank you.

---

### Post by tea for one on 2022-05-06
You have Windows 10 installed in old-style BIOS mode with msdos partition table.
Windows 10 usually requires UEFI mode with GPT.

According to the boot-repair report:-
[COLOR="#0000FF"]Line 93[/COLOR] - The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).

Your priority is to ensure that you have a backup of your personal files.

Then, I would suggest that you re-install Windows 10 in UEFI mode with GPT.
Then install Ubuntu in the same mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2022-05-06
You have a newer UEFI system, but Windows installed in old BIOS/MBR (msdos) mode.
Microsoft has required vendors to install Windows in UEFI/gpt mode since 2012.
Users were allowed to install in old BIOS/MBR mode more to allow newer Windows on old hardware.

You cannot mix UEFI & BIOS on same drive. And it can be difficult to mix UEFI & BIOS boot modes on same system.
Windows in BIOS mode must have boot flag on its boot partition which must be a primary NTFS partition.
Install systems in UEFI mode use boot flag to signify the ESP - efi system partition. Most systems only allow one boot flag per drive. 
You first need to move boot flag back to sda1 with gparted, command line or other tools.

Then do not use autofix in Boot-Repair, but use its advanced mode to choose install & drive to install grub2 bootloader into.
Grub only boots working Windows. And having both installs on same drive normally only allows one boot loader in MBR. Windows will not boot grub/Ubuntu, but grub will boot working Windows. This worked reasonably well with Windows 7 but Windows 8 and later use fast start up which sets hibernation flag. That prevents grub from booting Windows.
Since you have two drives, better then to install grub to sda & keep Windows boot loader on sdb. Then you will normally boot grub/Ubuntu & can choose Windows. But then when Windows breaks or fast start up turned back on with an update which it often does, then you can directly boot Windows, fix issues & then boot grub.
If you have grub in same drive as Windows you must always have Windows repair flash drive & Ubuntu live installer to temporarily switch boot loaders in MBR. Best to have those repair tools, anyway.

Long term think about reinstalling Windows in UEFI boot mode. And maybe Windows on one drive & Ubuntu on the other.  Or both on SSD in UEFI mode.
And much better to have systems installed on SSD. Your Windows install on sda, boots thru boot partition on sdb.

---

