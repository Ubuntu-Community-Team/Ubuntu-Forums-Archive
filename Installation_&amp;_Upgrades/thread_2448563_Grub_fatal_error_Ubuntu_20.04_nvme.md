---
title: "Grub fatal error Ubuntu 20.04 nvme"
date: 2020-08-10
forum: Installation &amp; Upgrades
---

### Post by aeternus.ignis on 2020-08-10
Good morning,
I'm new here and I registered and I'm new writing about a big installation problem.

I bought a new laptop, an HP OMEN 15-dh0 with a NVMe SSD and a Sata HDD.
I want to install Ubuntu alongside Windows and this isn't the first time I do something like this.

I disabled the secure boot; I created a partition in the ssd for Ubuntu and a partition in the HDD for the /home but when I actually installed Ubuntu, the grub installation failed with a fatal error:
Cannot install in /dev/nvme0n1.

I read something about this, and I tried to install it into /dev/nvme0n1p1, the windows loader, without success. I tried several times boot-repair, every time with not clear error, and to install it manually, with similar error of the installer.

Any ideas?

Thank you

! SOLUTION !

I was booting Ubuntu with acpi=off flag, because of some issues at first boots.
Trying to solve the grub installation issue I update the BIOS to F.32.
Searching for refind errors I found out something about an ACPI issue so I tried to re-enable ACPI at boot time.
Now not only the ACPI issues are gone but also grub installation finishes without troubles.

---

### Post by CelticWarrior on 2020-08-10
Welcome.

You'd be installing in UEFI mode so you also need a small FAT32 partition (~300MB should be enough for a lot of OSes) at the beginning of the drive that is defined as first priority in the boot order (can be changed in UEFI settings). Then you can use "something else" to install by selecting the ESP (EFI System Partition) previously created or create in the moment in that dialog), the root partition and a separated /home partition if you want.

---

### Post by aeternus.ignis on 2020-08-10
Thank you!
I already have a ESP partition used to boot by Windows and there I tried to install Grub. I have also tried to make another ESP and install it, but the results were the same...

---

### Post by CelticWarrior on 2020-08-10
Only ONE ESP per drive! Actually only one per system is recommended but no problem in having it duplicated in a different drive (it has some advantages but it takes more work and, again, not really needed).

If you want a dual-boot with Windows then you must disable Windows "Fast Startup" feature, otherwise the Ubuntu installer won't be able to mount the NTFS partitions properly and sometimes not even the ESP which will cause the error you reported. Also Fast Boot in UEFI should be disabled.

Last but not least you need to assure you're booting the installer in UEFI mode because how it boots is how it installs.

---

### Post by oldfred on 2020-08-10
In addition a few systems have some sort of way to lock ESP in UEFI settings. Check your UEFI.
May be related to UEFI Secure Boot. Is Secure Boot on?

HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

HP also only wants to boot Windows.
Some have posted that UEFI update and only changing boot order in UEFI works. Using efibootmgr which grub uses to set grub/ubuntu as first in boot order does not work.
HP change boot order in UEFI boot
[https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881](https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881)

---

### Post by aeternus.ignis on 2020-08-11
> **CelticWarrior said:**
> Only ONE ESP per drive! Actually only one  per system is recommended but no problem in having it duplicated in a  different drive (it has some advantages but it takes more work and,  again, not really needed).

Ok! Pretty clear, just one! Was a try and I will not do this anymore :)

> **CelticWarrior said:**
>  Last but not least you need to assure you're booting the installer in UEFI mode because how it boots is how it installs.

Yes, I'm sure of it.

> **CelticWarrior said:**
> If you want a dual-boot with Windows then  you must disable Windows "Fast Startup" feature, otherwise the Ubuntu  installer won't be able to mount the NTFS partitions properly and  sometimes not even the ESP which will cause the error you reported. Also  Fast Boot in UEFI should be disabled.

> **oldfred said:**
> In addition a few systems have some sort of way to lock ESP in UEFI settings. Check your UEFI.
May be related to UEFI Secure Boot. Is Secure Boot on?

HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

HP also only wants to boot Windows.
Some have posted that UEFI update and only changing boot order in UEFI works. Using efibootmgr which grub uses to set grub/ubuntu as first in boot order does not work.
HP change boot order in UEFI boot
[https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881](https://ubuntuforums.org/showthread.php?t=2441981&p=13952881#post13952881)

I disabled fast reboot in Windows, without better results; and I've lost the last day searching for a way to enter in the UEFI settings. I think I only see the basic settings and I've tried everything to enter the UEFI ones without success, I think I going to call the HP assistance.

EDIT: I called them, HP seems to allow the edit only of a subset of settings and the UEFI fast boot isn't included... What can I do?

---

### Post by oldfred on 2020-08-11
Some systems only open the additional settings if you set a UEFI password.
But never lose that password or reset to blank when done, or else you may brick system.

---

### Post by aeternus.ignis on 2020-08-12
> **oldfred said:**
> Some systems only open the additional settings if you set a UEFI password.
But never lose that password or reset to blank when done, or else you may brick system.

Just tried without results...

---

### Post by CelticWarrior on 2020-08-12
You probably have found out this by now but for the sake of completeness: In most HP UEFI systems users press ESC at the boot time. In the next menu users choose F10 to access UEFI settings.

---

### Post by aeternus.ignis on 2020-08-13
> **CelticWarrior said:**
> You probably have found out this by now but for the sake of completeness: In most HP UEFI systems users press ESC at the boot time. In the next menu users choose F10 to access UEFI settings.

Yes, this is the way I tried; in general I think that the ESC menu is just a summary of the Fn options, in fact, pressing F9 instead of ESC or after ESC menu has the same effect. I upload in order ESC menu, F9 menu and boot tab in F9 menu:
[ATTACH=CONFIG]286692[/ATTACH][ATTACH=CONFIG]286693[/ATTACH][ATTACH=CONFIG]286694[/ATTACH]


I tried to get more info from grub-install verbose output, but after a lot of [info], it ends this way:

```

grub-install: info: Registering with EFI: distributor = `ubuntu', path = `\EFI\ubuntu\shimx64.efi', ESP at hostdisk//dev/nvme0n1,gpt1.
grub-install: warning: Internal error.
grub-install: error: failed to register the EFI boot entry: Operation not permitted.

```

---

### Post by oldfred on 2020-08-13
Have you updated UEFI from HP for your system.
Many report that is required.

Some with HP have used rEFInd as boot manager.

Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by aeternus.ignis on 2020-08-16
> **oldfred said:**
> Have you updated UEFI from HP for your system.
Many report that is required.

Some with HP have used rEFInd as boot manager.

Alternative efi boot manager for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

Thank you very much.
I've studied something about rEFInd for the last days, I've tried to install it but Ubuntu started with a lot of errors that made the system unstable and unusable...

So I tried to learn more about EFI and efibootmgr, used during the install; now I'm trying to clean up the messed-up NVRAM, but I cannot work on it. Searching more on this lock I have a new question:
could start with "acp=off" create problems with EFI managment?

---

### Post by oldfred on 2020-08-16
"acpi=off" not acp ?
And that should not interfere with UEFI boot, but may cause some other issues. 
Some do not have everything working and need, for example, nVidia driver installed for video but also for things you might not associate with a video driver.

---

### Post by aeternus.ignis on 2020-08-17
> **oldfred said:**
> "acpi=off" not acp ?
And that should not interfere with UEFI boot, but may cause some other issues. 
Some do not have everything working and need, for example, nVidia driver installed for video but also for things you might not associate with a video driver.

Yes, during first boots of Ubuntu and clonezilla I had some ACPI errors, so I had to disable it.

Now, with the new F.32 BIOS, the ACPI issues are gone and the installation works just fine. I think I solved my problem! Thank you for your help :)

---

