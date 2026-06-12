---
title: "I cannot boot from USB"
date: 2019-06-25
forum: Installation &amp; Upgrades
---

### Post by danlez85 on 2019-06-25
Hi guy's

First of all, I am not new here but I have bee out of the forum for a long and I can not get back to the old account.

So, I have been working with Windows but I want to get back to Ubuntu. Before to start to install Ubuntu, I booted with the live USB but I decided to go back to Windows to be sure that I have a back up updated. When I checked it I decided to start the installation but I had a mistake that you can see bellow:

 \EFI\BOOT\mmx64.efi - Not Found
Failed to load image \EFI\BOOT\mmx64.efi: Not Found
Failed to start MokManager: Not Fond
Something has gone seriously wrong: import_mok_state() failed

Yes, I know that this problem is solved in last Post but I am kind of desperate because I tried to solve it as I saw but I was not possible and I don't know what more I can do. Also I have attached some pictures of my BIOS configuration but I think that everything is fine. Also I tried to change the name but the problem is still there.

I hope someone of you guys can help me to solve this problem. I will be grateful.

---

### Post by oldfred on 2019-06-25
Do you have UEFI Secure Boot on? I might try it with it off.
Your backup of Windows needs to be another drive. Many make incorrectly selection in install options where it says full drive install & it totally erases Windows.

What Brand/model system?
What video card/chip.

Most copy shimx64.efi or any other Ubuntu boot file & re-name to mmx64.efi.
It normally is not in /EFI/Boot, but once installed mmx64.efi will be in /EFI/ubuntu folder.

See more general info on UEFI install in link in my signature. Do not skip the backup suggestion.

---

### Post by danlez85 on 2019-06-25
> **oldfred said:**
> Do you have UEFI Secure Boot on? I might try it with it off.
Your backup of Windows needs to be another drive. Many make incorrectly selection in install options where it says full drive install & it totally erases Windows.

What Brand/model system?
What video card/chip.

Most copy shimx64.efi or any other Ubuntu boot file & re-name to mmx64.efi.
It normally is not in /EFI/Boot, but once installed mmx64.efi will be in /EFI/ubuntu folder.

See more general info on UEFI install in link in my signature. Do not skip the backup suggestion.

Exactly! Finally I change it to legacy mode and now it is working. What a stupid thing...

Thanks Man!!

---

### Post by oldfred on 2019-06-25
You still want to boot in UEFI boot mode, not the very old BIOS/CSM/Legacy boot mode, unless you also have Windows in the old boot mode.

---

### Post by danlez85 on 2019-06-26
> **oldfred said:**
> You still want to boot in UEFI boot mode, not the very old BIOS/CSM/Legacy boot mode, unless you also have Windows in the old boot mode.
Hi there.

Finally I booted in legacy mode and I have installed Ubuntu. My surprise was that when I rebooted the computer, Ubuntu doesn't run, I have just a black screen. When I have tried to change de Mode and to force run Ubuntu from the hard drive, it was not possible. I have checked that Ubuntu have been installed with the live USB mode and everything looks fine.

What do you think about this problem? I have installed Ubuntu and I have delated the old Windows completely.

Thanks!

---

### Post by oldfred on 2019-06-26
Lets see where you are at.
Black screen is often a video issue. Post info requested in post #2 so we can make correct assumptions on your system.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by danlez85 on 2019-06-26
Forget it. Finally I solved the problem. This hot is getting me crazy....

---

