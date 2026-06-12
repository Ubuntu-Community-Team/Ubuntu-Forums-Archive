---
title: "Minimal Grub"
date: 2017-01-31
forum: Installation &amp; Upgrades
---

### Post by yasgur99 on 2017-01-31
Hi so I booted into a live usb drive and when i went to reboot i got the minimal grub command line. I cant boot into ubuntu. I looked at this thread: [https://ubuntuforums.org/showthread.php?t=1762106](https://ubuntuforums.org/showthread.php?t=1762106) but it looked like the solution was very specifc for the partitions he had.

Here is my pastebin: [http://paste2.org/kKeFPf2m](http://paste2.org/kKeFPf2m)

Would anyone please help me with this. Boot repair said it was successful but when I reboot I still get the same menu. I can still go into my EFI and boot to windows. I think i need to reinstall grub. Currently I am on a Live Ubuntu drive.

---

### Post by oldfred on 2017-01-31
You are showing two ESP - efi system partition. 
That is set with boot flag if you are using gparted. Removed boot flag on sda5.

Your Windows configuration is not normal. 
Windows requires certain partitions, and expects them in certain places. You Windows may now work, but at some point it may have issues when it needs partition where it should be.

[https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)        Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by yasgur99 on 2017-01-31
So what you are saying is to remove the boot and esp flag on sda5? what should i change the flag to if so?

---

### Post by oldfred on 2017-01-31
No flag, most UEFI systems can only have one ESP active at one time. 
And sda3 is your ESP - efi system partition.

---

### Post by yasgur99 on 2017-01-31
When I take off the flag, it automatically chooses msftdata and I cant uncheck it so there are no flags. is that an issue?

---

### Post by yasgur99 on 2017-01-31
**Update: **I took off the boot flag and the ESP flag and it set the msftdata flag on it. I tried to reboot but got to the same minimal grub page

---

### Post by oldfred on 2017-01-31
From UEFI boot menu can you choose the Windows entry?
What brand/model system?

In Boot-Repair's advanced mode you can choose an operating system and drive to install into.
Choose the uninstall/reinstall of grub, to reinstall grub-efi-amd64. That should fix the configuration issue that is giving just grub entry.

---

### Post by yasgur99 on 2017-01-31
From UEFI boot menu, I can in fact boot into windows. As for the brand/model of the system, I built my machine so i'm not sure if that is much help. it is an ASUS Z170-E motherboard if that helps.

In the advanced tab, the grub location tab and the grub options tab is greyed out so I cant go in and make any of the changes regarding grub.

Any ideas? is grub installed incorrectly or something?

---

### Post by oldfred on 2017-01-31
I have an Asus Z97 and Gigabyte Z170.
But no Windows on either system.
Are you using the internal Intel video or have video card?

But with the Asus system I had to make many UEFI settings changes & keep a record of changes as every UEFI update from Asus reset to defaults and I have to redo them. Your newer system may need the same settings.

Some other Asus threads, I save those because of my Asus.
 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
[http://ubuntuforums.org/showthread.php?t=2258575](http://ubuntuforums.org/showthread.php?t=2258575)
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)
BIOS only install Asus Z97-a
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)

---

