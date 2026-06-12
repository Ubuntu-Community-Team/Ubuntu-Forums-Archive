---
title: "In quest for the GRUB2 trouble."
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by bijaydeyp on 2020-05-07
Hello members
Hope all is well.
 
My HP notebook was running well with   ***windows 10***   &  ***Ubuntu 19.10*  **on UEFI mode. 
Today I made a multiboot-USB with  ***Ubuntu***  & ***Kubuntu 20.04*** & installed them onto new partitions. Grub2 also installed into their respective partitions.
 None of the Linux systems are booting now. They drops into grub2 console. 
 1st after Kubuntu it started, then installing Ubuntu 20.04 shows same. Reinstalling the new OSes several times was not also helpful.
 
 My questions, Why it happened & what's the solution ?
 
 Best regards

---

### Post by oldfred on 2020-05-07
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Are all installs UEFI?

Grub in UEFI mode, boots from a small 3 line grub.cfg in the ESP - efi system partition that loads the full grub.cfg in your install. Last install will be the only one as all flavors are "ubuntu". But the last install should run os-prober and find all the other installs and offer to boot them.

---

### Post by bijaydeyp on 2020-05-08
Many thanks for your reply @[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711")

Here, is the boot log from ***live ubuntu 20.04*** session as you suggested  [https://paste.ubuntu.com/p/fqXcp2x3nw/](https://paste.ubuntu.com/p/fqXcp2x3nw/)
 I am not a pro user so plz let me khow what the problems are.

With regards

---

### Post by oldfred on 2020-05-08
You have an UEFI system and UEFI install of Windows.
But it looks like you originally installed Ubuntu in UEFI mode as you have an Ubuntu folder in the ESP.
But the grub.cfg in the ESP is tying to boot an unknown UUID. So you must have reinstalled and used BIOS boot mode as you have grub installed to gpt's protective MBR for BIOS boot. You also installed grub to PBR of sda8. You almost never install grub to a partition and if UEFI do not install grub to MBR.

You need to be sure to boot installer in UEFI mode, and then add Boot-Repair so it can reinstall grub in UEFI boot mode.

I also do not now see Windows UEFI boot entry. Not sure if just not shown or it got erased?
We can add one if Windows is otherwise ok. If anything else wrong with Windows, you then need your Windows repair/recovery flash drive.

---

### Post by bijaydeyp on 2020-05-08
Thanks again @[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") 

> I also do not now see Windows UEFI boot entry. Not sure if just not shown or it got erased?
I have two Windows 10 installed on the HDD both in working state.

> You need to be sure to boot installer in UEFI mode, and then add Boot-Repair so it can reinstall grub in UEFI boot mode.
 I suspect the utility I used for. I will use a different utility & let you know the results.
Regards

---

### Post by bijaydeyp on 2020-05-09
@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") Good news!
The systems are up again.
Last time I used the tool *WinSetupFromUSB* [https://www.winsetupfromusb.com/](https://www.winsetupfromusb.com/) Later I discovered that somehow my old grub2 menu shifted (the one before the trouble) on the bootable thumb drive. All the linux systems were accessible from there. This was unexpected. I suspect the tool for this mishap.
 As per your suggestions, this time I used *YUMI-UEFI* tool [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)  & it worked!
Problem solved.

Thank you so much for your helps.

---

