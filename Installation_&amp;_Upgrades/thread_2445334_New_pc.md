---
title: "New pc"
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by thomas_j_marshall2 on 2020-06-12
Currently runninmg Windows 10 and Ubuntu 20.04 on two separate SSDs. Just bought a new PC with W10 on an NMVe and just wondering if I put the SSD with my Ubuntu install on it, will it run?  I am thinking if I boot it from the bios it would then pick up windows?  Would that be correct?

---

### Post by tea for one on 2020-06-12
Does your new PC allow you to install multiple internal drives?

New PCs have UEFI set up pages rather than BIOS and one of the major advantages is that you can de-activate drives to prevent errors.

I would suggest that you first explore the UEFI set up to gain familiarity with your new PC.

You can select OS systems from the UEFI boot menu.

My gut feeling is that your ssd installation of Ubuntu will run (subject to graphics).

It's difficult to be more precise until you offer more details about your PC and your intentions? e.g. dual boot one one drive or separate drives.

---

### Post by thomas_j_marshall2 on 2020-06-12
Thanks for that.  My old pc is uefi and the new one has 6 sata ports so I can addd drives OK.  In my old pc I did the two OS installs and the only one that would run was W10 so I went into the bios and set ubuntu as the boot drive and it ran and picked up windows so I had both on the menu.  This is what I'm hoping to do again but not sure if Ubuntu will work but I suppose I can jusrt try it and see!

---

### Post by tea for one on 2020-06-12
In your position, I would do the following with your new PC:-

Jump into the UEFI and de-activate the Windows nvme drive.
Power off the PC
Insert your Ubuntu ssd - make sure the drive is active
Reboot the PC

Fingers crossed............Will it boot?

---

### Post by CelticWarrior on 2020-06-12
As above but you also need to change accordingly two settings in UEFI.
One is regarding the drive priority. This is similar to old BIOS systems but the purpose is different, the purpose is to read its EFI partition. Then you may need to reboot and again open UEFI settings, now in the Boot menu or similar and select the OS to boot. This should be read from the EFI partition present in the drive selected in the previous step.

Will it work? Well, unlike previous commenters here, IMO it won't. I'm saying this assuming you had Windows installed first (or preinstalled) in the old computer, in the 1st drive. This drive likely contains the EFI partitions and the Windows partitions. When you installed Ubuntu in the 2nd driver it used and kept booting from the 1st drive's EFI partition. So, very likely your "Ubuntu drive" does NOT contain an EFI partition.

---

### Post by oldfred on 2020-06-12
From old computer run Boot-Repair, and then we can see exact configuration.
Part of reason why I like to have an ESP on every drive, even if grub is actually installed into a Windows drive's ESP.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If Ubuntu drive has ESP, then all you may need to do is a reinstall of grub will will put grub's efi boot files into ESP and add UEFI boot entry.

---

### Post by tea for one on 2020-06-12
> **CelticWarrior said:**
> So, very likely your "Ubuntu drive" does NOT contain an EFI partition.

Yes, good point.

When I replied earlier, unconsciously I imagined that all the user's drives contained an EFI partition because that is what I have on my own system.

Let's see the results from the OP and try and supply further support.

---

