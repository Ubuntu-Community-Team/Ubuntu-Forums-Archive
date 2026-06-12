---
title: "Windows boot still fails after following Intel RST instructions"
date: 2021-11-29
forum: Installation &amp; Upgrades
---

### Post by macguges on 2021-11-29
I encountered the message about disabling Intel RST while installing Ubuntu onto a new Dell Inspiron 15 3000 laptop, and followed the instructions at [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/).  I changed the keys in the Windows registry and switched from RST to SATA AHCI in the bios.  When I first got "inaccessible boot device", I opened the Command Prompt from the Repair mode, and ran the diskpart and bcdedit commands as written.  All three of the bcdedit commands failed with the error "Element not found", so I searched for the BCD file.  I found it not in {drive letter}:\boot but in {drive letter}:\EFI\Microsoft\boot.  I renamed it to BCD.bak and ran bcdboot, as written, and that command returned success.  But when I rebooted, Windows again failed to boot, with "inaccessible boot device".

I've documented my steps with screenshots and photographs.  I've been able to recover access to Windows, but my goal is to set up dual booting on this machine before I present it as a gift.  Please let me know which details you need to see.

It seems there are some differences between this machine and the assumptions of these instructions, but I don't know which differences matter.  For instance, I was instructed in the Windows Registry to change the value of two Start keys to 0, but I found these keys with the value 0 already.  Later, all three bcdedit commands failed, and I don't know how I should interpret "Element not found".  And the top-level boot directory on the EFI drive was empty.  So I'm at a loss for my next steps.

---

### Post by oldfred on 2021-11-30
Have you tried the saft boot method?

Windows AHCI instructions - some have found safeboot method better
[https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571](https://www.dell.com/community/Laptops-General-Read-Only/Dell-M-2-FAQ-regarding-AHCI-vs-RAID-ON-Storage-Drivers-M-2-Lanes/td-p/5072571) & 
[https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) & 
But if you do a safe boot first to update Windows, then boot to UEFI/BIOS and change to AHCI and finally boot normally, it works
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)

---

### Post by macguges on 2021-11-30
OK, this is great.  No, I was unaware of this method.  I expect I should be able to backtrack to booting Windows again with RST, and then follow this.  Thank you, I'll let you know how it goes.

---

### Post by macguges on 2021-12-01
Yes, that second method worked great.  It's a much simpler method than has been described in [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/), which required multiple registry changes and use of the Recovery mode command prompt.

I have since discovered I need to disable BitLocker as well, which I imagine the installer couldn't detect before the disk controller was changed.  With any luck there won't be any complications to following our official instructions for that.

---

### Post by macguges on 2021-12-03
OK, since my last post I've successfully installed Ubuntu 21.10 on this Dell Inspirion 15 laptop. Thank you for your help, oldfred! I'd like to summarize now the steps I took with this machine, particularly because the process was much simpler than the method I'd tried first which is published at [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/). It makes me wonder how the community inform the folks responsible (employees of Canonical?) to recommend a revision.

1. Of course, it almost goes without saying that I backed up the original filesystem first, but I remember being a younger engineer who may have rushed past creating a full backup.  If I could admonish them then from now I'd warn them that experience may be the best teacher, but it is also cruel.  Following Murphy's Law means that we take practical precautions against failure.  For the most part I followed the following article to create the backup, except that I discovered I need to perform a clean boot first, due to third-party services that came pre-installed by Dell.

[https://answers.microsoft.com/en-us/windows/forum/all/how-to-create-a-system-image-in-windows-11-and/036110b8-66bb-4cc7-b9e2-2d66df27d236](https://answers.microsoft.com/en-us/windows/forum/all/how-to-create-a-system-image-in-windows-11-and/036110b8-66bb-4cc7-b9e2-2d66df27d236)
[https://support.microsoft.com/en-us/topic/how-to-perform-a-clean-boot-in-windows-da2f9573-6eec-00ad-2f8a-a97a1807f3dd](https://support.microsoft.com/en-us/topic/how-to-perform-a-clean-boot-in-windows-da2f9573-6eec-00ad-2f8a-a97a1807f3dd)

Before I performed the clean boot, I encountered the error "Windows Backup Failed to Get an Exclusive Lock on the EFI System Partition" when I attempted to backup the laptop.

2. I converted the Windows installation from Intel RST to AHCI following the 2nd set of instructions in [https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems](https://askubuntu.com/questions/1233623/workaround-to-install-ubuntu-20-04-with-intel-rst-systems) :
a. I opened a Command Prompt (cmd.exe) with Administrator privileges.
b. I ran "bcdedit /set {current} safeboot minimal"
c. I restarted the computer, pressing F12 (as required with Dell laptops) to enter BIOS setup.
d. I changed the storage controller from using Intel RST to AHCI, then saved and exited BIOS.
e. Windows booted automatically into Safe Mode.
f. Again, I opened a Command Prompt (cmd.exe).
g. I ran "bcdedit /deletevalue {current} safeboot".
h. I rebooted, confirming that I could boot Windows in AHCI mode.
(YMMV, check the AskUbuntu page for more detail.)

I then ran the Ubuntu installer again, which did not fail at the same point as it had before, but with the benefit of foresight I would perform this last step in Windows:

3. Turn BitLocker off in Windows, decrypting the hard drive.
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-running-windows-and-bitlocker-turned-on/15338)

These instructions served me fine.  My goal was to prepare the new laptop for dual-booting to both Linux and Windows, so I could only proceed by disabling BitLocker.  As I'd already backed up the Windows filesystem once, all that was left was to find Drive Encryption in Windows Settings and turn it off.  Once Windows finished decrypting the drive I rebooted into my Ubuntu Live Drive and began installation, which completed successfully from that point.

---

### Post by MAFoElffen on 2021-12-04
In support of oldfred, he is dealing with more than 100's for brands and models... He is amazing in the information he retains and saves on models and issues...

 I am a Dell Certified Warranty RTU Tech, and I can tell you that that setting is not consistant as it is sold/delivered. On system boards, when I replaced a Dell system board on warranty, I changed that setting from SATA mode RAID, to AHCI, because of over a decade of experience here... When ity came in from Dell, it was always setfrom Dell as RAID. Logically, that never made sense to me.

Only rarely was that setting on the original system board, after I reset it to AHCI, where it had to be set to RAID to boot Windows, but there was a few. When Windows was installed in this mode, it lo0oked for that mode to boot as. it needed help to boot as AHCI from that different AHCI setting, if it was originally installed as RAID mode.

---

### Post by oldfred on 2021-12-04
Glad you got system working. :)

Oldfred has searchable notes(Zim text files). He started with seeing same questions over & over, so saved answers.
Old answers still work for older systems, but newer systems keep changing things.

It seems all brands install Windows with RAID. Must be something in Windows RAID driver that they prefer that over AHCI. And then you have to install AHCI driver in Windows.
Or it could be like the old Microsoft, make it difficult for others to install.

New systems are now NVMe. Just saw where they developed a hard drive using NVMe driver. HDD still not mechanically faster but using one driver.
In a few years we may just be installing a NVMe driver for new systems. But old systems will still have AHCI.

---

