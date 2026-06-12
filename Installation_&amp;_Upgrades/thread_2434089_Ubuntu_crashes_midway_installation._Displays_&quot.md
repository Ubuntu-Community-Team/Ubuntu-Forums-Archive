---
title: "Ubuntu crashes midway installation. Displays &quot;Couldn't get size: 0x800000000000000e&quot;"
date: 2019-12-30
forum: Installation &amp; Upgrades
---

### Post by pranjalgupta29 on 2019-12-30
So I am new to Linux. This is my first time installing ubuntu on my MSI GL63 9RC, i5 9th gen, with 512gb ssd and 1TB hdd. i created the free space of 100gb on my hdd, disabled the UEFI secure boot and also set the "what power button does" to unchecked. After booting from my USB, the installation process started but was stopped mid-way after the language selection window and an error of "[8.444824] Couldn't get size: 0x800000000000000e" was displayed. I am attaching the picture of the error.[ATTACH=CONFIG]284717[/ATTACH]
What should i do ?

---

### Post by webaake on 2019-12-30
You could try 2 things; try again and chose English - if it wasn't what you chose already. The other thing is that your USB stick or the Image you downloaded are faulty. So, re-downloading and reformating the stick might solve it. Redo the bootable stick from scratch.

Good luck and a Happy New Year!

PS Do not chose to update at the time of installing. If install succeeds you can then update the system (and change language and fonts)

---

### Post by oldfred on 2019-12-30
Have you updated UEFI?
If SSD updated firmware?

Are drives set for AHCI?

Message usually is related to UEFI Secure Boot and needing you to add key for a proprietary driver where Ubuntu cannot automatically sign the driver.
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

       MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)

---

### Post by webaake on 2019-12-30
He did say that "disabled the UEFI secure boot".

---

### Post by pranjalgupta29 on 2020-01-01
I tried it multiple times but no luck :(

---

### Post by P-I H on 2020-01-01
There are three methods to install
- Install alongside windows
- Erase and use the whole disk
- Something else
Install alongside windows will install on the ssd and you wrote that you have created space on the hdd. I suppose this will give the error message Couldn't get size: 0x80000000000000
I suppose you don't want to erase all data on the hdd and that leaves the third method Something else.

---

### Post by pranjalgupta29 on 2020-01-01
> **oldfred said:**
> Have you updated UEFI?
If SSD updated firmware?

Are drives set for AHCI?

Message usually is related to UEFI Secure Boot and needing you to add key for a proprietary driver where Ubuntu cannot automatically sign the driver.
[https://ubuntuforums.org/showthread.php?t=2380700](https://ubuntuforums.org/showthread.php?t=2380700)

       MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)

My BIOS is updated to the latest version, also I had set the UEFI secure boot to disabled. Still no luck.
Is it necessary that the volume I had shrunk must be from the drive I've my windows installed on? Because till now, I've been shrinking space from my (E) Drive (HDD) whereas the windows is installed on the (C) Drive (SSD).

---

### Post by pranjalgupta29 on 2020-01-01
> **P-I H said:**
> There are three methods to install
- Install alongside windows
- Erase and use the whole disk
- Something else
Install alongside windows will install on the ssd and you wrote that you have created space on the hdd. I suppose this will give the error message Couldn't get size: 0x80000000000000
I suppose you don't want to erase all data on the hdd and that leaves the third method Something else.

I didn't get this option anywhere. Pardon me if I sound naive, but this is the first time I am dealing with anything as such this.

---

### Post by oldfred on 2020-01-01
Should not matter which NTFS partition you shrink, unless you have Windows 10 installed over an old Windows 7 and drive is BIOS/MBR, not newer UEFI/gpt.

MBR has a 4 primary partition limit. Also Windows whether MBR or gpt may convert drive to dynamic partitions which is proprietary and not usable with Linux.

This shows screens you should be seeing. The install options screen may vary a bit depending on version you have.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

