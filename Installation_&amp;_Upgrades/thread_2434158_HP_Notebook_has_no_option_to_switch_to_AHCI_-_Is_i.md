---
title: "HP Notebook has no option to switch to AHCI - Is installation possible?"
date: 2019-12-31
forum: Installation &amp; Upgrades
---

### Post by Tony_Bennett on 2019-12-31
Notebook:  HP 15-da0073wm
OS:          Windows 10 - 1909
Memory:   4GB
Storage:      1TB HDD + 16 GB Optane "memory" (a 16GB SSD stick)
BIOS:            InsydeH20 - version F.22 (most current version)

All instructions I have read about how to install Ubuntu 18.04LTS in a dual boot configuration
with Windows 10, include a step to set SATA controller to AHCI mode (instead of RAID or RST).

The BIOS on this system does not have an option to change the SATA controllers MODE.

I posted a question in the HP forum asking how to do it, and the response was:
[INDENT][@ToneBen]("https://h30434.www3.hp.com/t5/user/viewprofilepage/user-id/3564220")  It looks like the advanced options in BIOS on your device is locked by  HP, to prevent changes that may render the device unstable,
  that said, you can't change the SATA controller to AHCI due to the reason mentioned above.

   
  You may try updating the BIOS and then, check for changes, if nothing helps, its because the options are locked by design.

[/INDENT]

So, my question is "does this mean I will be unable to install Ubuntu on this notebook?"

Thanks,
-tony

---

### Post by CelticWarrior on 2020-01-02
Try a live session and check if the drive where you intend to install is seen. If it is then no change is needed.

---

### Post by Tony_Bennett on 2020-01-03
Thank you for your response.

I did previously try a live usb, and started to do an installation, only to discover it didn’t detect the windows installation on the hard disk, so I exited before it wrote anything.

I have discovered a website where they help you modify the bios (to unlock options).  But considering this notebook is not mine, and belongs to a neophyte user, and every option I know of are risky, and require deeper understanding than the user possesses, I have returned it to them as a Windows only system.

I must say I am more than annoyed at HP for doing this, and will not consider purchasing an hp in the future because of it.

I do hope Linux kernel developers will take note of this new manufacturing direction (locking out config changes to the bios) and perhaps enable installing Linux on non-AHCI PCs.

---

### Post by oldfred on 2020-01-03
Maybe they do not call it AHCI anymore?

This HP user just disabled optane.
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)

While Dell, some explaination of Optane.
[https://www.dell.com/support/article/us/en/19/sln306745/optane-memory-module-frequently-asked-questions?lang=en](https://www.dell.com/support/article/us/en/19/sln306745/optane-memory-module-frequently-asked-questions?lang=en)

---

### Post by Tony_Bennett on 2020-01-07
The “HP user” who just “disabled optane”, according to their post did so in the BIOS, which is not available in this HP Notebook.

As to the Dell explanation, I have successfully enabled a Linux/windows-10 dual boot on a dell notebook equipped with optane (disable in intel RST app, setup window it install AHCI driver, disable RST/RAID in BIOS).

My question is “Is it possible to install Ubuntu on a system that CANNOT be put into AHCI mode?”

---

### Post by saraswat40 on 2020-09-25
> **Tony_Bennett said:**
> The “HP user” who just “disabled optane”, according to their post did so in the BIOS, which is not available in this HP Notebook.

As to the Dell explanation, I have successfully enabled a Linux/windows-10 dual boot on a dell notebook equipped with optane (disable in intel RST app, setup window it install AHCI driver, disable RST/RAID in BIOS).

My question is “Is it possible to install Ubuntu on a system that CANNOT be put into AHCI mode?”

Hey,

I am in the same boat. Were you able to find an answer to your question?

Thanks
ps

---

### Post by Tony_Bennett on 2020-09-25
Considering the owner of the HP is not a "power user" (to say the least), 
and she was happy with Windows (sigh...), I gave her back the computer
unmodified.

I since found a pretty detailed write up about installing Ubuntu on a system
which has Intel RST (Rapid Storage Technology) HERE: [https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

But, if HP doesn't provide an option in the UEFI (BIOS) to convert SATA from Raid (or RST) to AHCI, 
I still don't see how we can install Ubuntu.  If you figure it out, please post an update.

---

### Post by more023 on 2021-04-24
> **Tony_Bennett said:**
> Notebook:  HP 15-da0073wm
OS:          Windows 10 - 1909
Memory:   4GB
Storage:      1TB HDD + 16 GB Optane "memory" (a 16GB SSD stick)
BIOS:            InsydeH20 - version F.22 (most current version)

All instructions I have read about how to install Ubuntu 18.04LTS in a dual boot configuration
with Windows 10, include a step to set SATA controller to AHCI mode (instead of RAID or RST).

The BIOS on this system does not have an option to change the SATA controllers MODE.

I posted a question in the HP forum asking how to do it, and the response was:
[INDENT][@ToneBen]("https://h30434.www3.hp.com/t5/user/viewprofilepage/user-id/3564220")  It looks like the advanced options in BIOS on your device is locked by  HP, to prevent changes that may render the device unstable,
  that said, you can't change the SATA controller to AHCI due to the reason mentioned above.

   
  You may try updating the BIOS and then, check for changes, if nothing helps, its because the options are locked by design.

[/INDENT]

So, my question is "does this mean I will be unable to install Ubuntu on this notebook?"

Thanks,
-tony

Hi, i try this and work for my. Try to install previus version of ubuntu, like 10.08, in your usb drive and then in to hard drive. This version haven't problem with de rst system. Finally install de last version from ubuntu.

I hope this work for you

Saludos

---

### Post by alvincarter717 on 2022-04-04
Have you found a way to do it yet? I tried many distros (Arch, Fedora, etc) none of them shows Intel RST restriction while installing. Why Ubuntu?

The only way I'm able to use Ubuntu 21.10 is first to install 18.04, then upgrade it to 20,04 and then upgrade it to 21.10. Why can't Ubuntu just let users install directly just like in 18.04?

---

