---
title: "Why did Ubuntu just try to switch me to UEFI Secure Boot?"
date: 2020-01-16
forum: Installation &amp; Upgrades
---

### Post by Vulcanasm on 2020-01-16
Hi, 

I've been running some flavor of Ubuntu (lately, Xubuntu) as my primary Linux OS for more than a decade, and something very strange happened a few minutes ago with Software Updates. For reasons unknown, Ubuntu 18.04.3 LTS attempted to switch me to UEFI Secure Boot, which I neither need nor want nor have installed AFAIK. Software Update stole focus with a popup to set a Secure Boot password as I was closing tabs in my browser with CTRL + W. Then the predictable happened. I couldn't cancel the update despite the now-closed window, and I don't want this "feature" in the first place, so I closed the updater. Now sudo apt update gives "E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)" and I see some dead processes:

root      8064  1.1  0.1 115028 23752 pts/3    SN+  14:24   0:05 /usr/bin/perl -w /usr/share/debconf/frontend /usr/sbin/update-secureboot-policy --enroll-key
root      8074  0.3  0.0   4624  1736 pts/3    SN+  14:24   0:01 /bin/sh /usr/sbin/update-secureboot-policy --enroll-key

I assume it's safe to kill these processes, but what other precautions do I need to remove (or, perhaps, undo) this now-half-installed "feature"?

I can only assume that this is a bug, as I saw no announcement about Ubuntu surprise-requiring Secure Boot in the middle of an LTS cycle. I can think of no reason why this would be done as Ubuntu seems very keen about NOT breaking UX with self-incompatible changes.

So, finally, what ... exactly ... caused this?

---

### Post by CelticWarrior on 2020-01-17
Ubuntu does not require Secure Boot but if Secure Boot is enabled (it's a UEFI feature, independent of any OS) and unsigned drivers are to be installed/loaded then it stands to reason that the updater will need you to set a password for Secure Boot through mokutil.

If you don't want this to happen just disable Secure Boot in UEFI.

---

### Post by ubfan1 on 2020-01-17
At some point in the past, (but before the 4.15 kernel series used in 18.04.1), the kernel package naming convention changed.  Formerly, the signed packages had a "signed" in their name, now the signed packages have nothing, but the unsigned packages have "unsigned" in their names.

---

### Post by Vulcanasm on 2020-01-17
> **CelticWarrior said:**
> Ubuntu does not require Secure Boot but if Secure Boot is enabled (it's a UEFI feature, independent of any OS) and unsigned drivers are to be installed/loaded then it stands to reason that the updater will need you to set a password for Secure Boot through mokutil.

If you don't want this to happen just disable Secure Boot in UEFI.

Right. Secure Boot is disabled in UEFI, so the password screen is especially baffling...

---

### Post by CelticWarrior on 2020-01-17
Is it really? Please double-check. Some Windows updates may heve re-enabled it even if you had it disabled.

---

### Post by Vulcanasm on 2020-01-17
> **CelticWarrior said:**
> Is it really? Please double-check. Some Windows updates may heve re-enabled it even if you had it disabled.

I want to be certain that rebooting won't break my Ubuntu install before I double-check. I disabled Secure Boot when I got the laptop (mid-December) and haven't booted Windows since. I also disabled Windows update.

Can Ubuntu change UEFI settings? AFAIK there's been no opportunity for UEFI settings to be changed by anything else. My last Ubuntu reboot was last week, so even that seems unlikely.

---

### Post by rbmorse on 2020-01-18
If controlled rebooting breaks your Ubuntu, your Ubuntu is already broken.

---

### Post by CelticWarrior on 2020-01-19
> **rbmorse said:**
> If controlled rebooting breaks your Ubuntu, your Ubuntu is already broken.

Exactly ):P

---

### Post by Impavidus on 2020-01-19
Ubuntu can be broken in such a way that it no longer boots, but can be fixed as long as it's running. You'd also be able to fix it using a live disk. Or you may be able to boot Ubuntu using an older kernel from the grub menu.

Maybe related to a kernel upgrade? Ubuntu 18.04 recently went from 5.0 to 5.3 (except for those who use 4.15).

---

### Post by Vulcanasm on 2020-01-20
> **Impavidus said:**
> Ubuntu can be broken in such a way that it no longer boots, but can be fixed as long as it's running. You'd also be able to fix it using a live disk. Or you may be able to boot Ubuntu using an older kernel from the grub menu.

Maybe related to a kernel upgrade? Ubuntu 18.04 recently went from 5.0 to 5.3 (except for those who use 4.15).

Exactly. That's why I'm being paranoid about rebooting. I've had that happen with other distributions.

I agree that this could be related to the kernel upgrade, but if we're being forced to use Secure Boot in 5.3, was the change announced? I do note that I haven't rebooted since that kernel was installed: [FONT=courier new]uname -r[/FONT] gives me 5.0.0-37-generic.

Found a few more issues that make me worry about rebooting. I tried to [FONT=courier new]sudo grub-install[/FONT] and got
> Installing for x86_64-efi platform.
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
Installation finished. No error reported.

[FONT=courier new]efibootmgr -v[/FONT] looked OK. But then [FONT=courier new]sudo gdisk /dev/sda[/FONT] threw the same warning as reported by  [https://ubuntuforums.org/showthread.php?t=2411598](https://ubuntuforums.org/showthread.php?t=2411598):
> ***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************

Okay, whatever, backed up the partition table to USB drive with [FONT=courier new]sudo sfdisk[/FONT], ran [FONT=courier new]sudo gdisk /dev/sda[/FONT], [FONT=courier new]v[/FONT] --> looks ok, [FONT=courier new]w[/FONT] --> 
> [FONT=&amp]About to write GPT data. THIS WILL OVERWRITE EXISTING PARTITIONS!! O NOES[/FONT][FONT=&amp]
[/FONT]worked, [FONT=courier new]sudo grub-install[/FONT] stopped warning about the GUID Partition Table Header signature, [FONT=courier new]sudo partprobe[/FONT] caused no issue AFAIK. One...tiny...concern, though. 

Why did the old MBR format suddenly become problematic?

---

### Post by oldfred on 2020-01-20
Did you have a MBR(msdos) partitioned drive, but UEFI install?
Ubuntu lets you do that and probably should not.

Windows only installs to gpt partitioned drives with UEFI.
Windows only installs to MBR partitioned drives with BIOS.
You cannot dual boot on same drive Windows in BIOS/MBR and Ubuntu in UEFI/MBR.
So about the only way to boot Ubuntu in UEFI mode from MBR is if drive only has Ubuntu. And then there is no real reason not to use gpt.
I have used gpt for Ubuntu in BIOS mode with bios_grub partition, since 2010 and not had any issues with gpt (that I know of). And then in 2012 started to add an ESP to every new or repartitioned drive so when I converted to UEFI, drive would be compatible.

You can use gdisk to convert from MBR to gpt, but have to reinstall grub. And if Windows MBR drive,then you break Windows.

---

### Post by Vulcanasm on 2020-01-20
> **oldfred said:**
> Did you have a MBR(msdos) partitioned drive, but UEFI install?
Ubuntu lets you do that and probably should not.

Windows only installs to gpt partitioned drives with UEFI.
Windows only installs to MBR partitioned drives with BIOS.
You cannot dual boot on same drive Windows in BIOS/MBR and Ubuntu in UEFI/MBR.
So about the only way to boot Ubuntu in UEFI mode from MBR is if drive only has Ubuntu. And then there is no real reason not to use gpt.
I have used gpt for Ubuntu in BIOS mode with bios_grub partition, since 2010 and not had any issues with gpt (that I know of). And then in 2012 started to add an ESP to every new or repartitioned drive so when I converted to UEFI, drive would be compatible.

You can use gdisk to convert from MBR to gpt, but have to reinstall grub. And if Windows MBR drive,then you break Windows.

Oh, yes, the drive (2 TB SATA) only has Ubuntu installed. I did gpt conversion and grub reinstall already. Windows 10 is on a different physical disk. I moved the SATA drive into a new laptop in December and didn't need to reinstall; both laptops had UEFI and not BIOS. Presumably the use of MBR was a bad decision on my part when I installed Ubuntu.

There is a shared NTFS partition on the SATA drive for documents, data, etc, but Microsoft's "Windows and GPT FAQ" suggests mounting it in Windows 10 won't be a problem... (famous last words)

---

### Post by oldfred on 2020-01-20
The only real issue on NTFS for data (only) is Windows fast start up. And Windows will keep turning it on with updates which then locks up NTFS partitions. It sets hibernation flag and when that is set the Linux NTFS driver will not mount read/write. When Windows remounts it, it uses the hibernation and any changes are lost. 

Best to also use parameters on mounting like windows_names to prevent characters Windows does not support and big_writes to speed up NTFS a bit.

NTFS mount parameters - Windows_names, big_writes
[https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)
[https://linux.die.net/man/8/mount.ntfs-3g](https://linux.die.net/man/8/mount.ntfs-3g)

While Windows allows spaces, Linux has to have spaces escaped. Better to use CamelCase or under_score for any names or labels.

---

### Post by Vulcanasm on 2020-01-20
> **oldfred said:**
> The only real issue on NTFS for data (only) is Windows fast start up. And Windows will keep turning it on with updates which then locks up NTFS partitions. It sets hibernation flag and when that is set the Linux NTFS driver will not mount read/write. When Windows remounts it, it uses the hibernation and any changes are lost. 

Best to also use parameters on mounting like windows_names to prevent characters Windows does not support and big_writes to speed up NTFS a bit.

NTFS mount parameters - Windows_names, big_writes
[https://wiki.archlinux.org/index.php/NTFS-3G](https://wiki.archlinux.org/index.php/NTFS-3G)
[https://linux.die.net/man/8/mount.ntfs-3g](https://linux.die.net/man/8/mount.ntfs-3g)

While Windows allows spaces, Linux has to have spaces escaped. Better to use CamelCase or under_score for any names or labels.

Ubuntu rebooted with no difficulty, of course. Not even a warning thrown. A+

...and Windows 10 broke. Because of course it did. BSOD with "Inaccessible Boot Device :-(" and a QR code. (Should I also check out Microsoft's Friendster...?). Windows 10 really is on a different physical disk, though. :(

As it turns out, you were correct that something reactivated UEFI Secure Boot, presumably triggering the original issue. I don't understand how. You said that nothing in Ubuntu can do that, right...? Does Dell have a means of automatically changing system settings without a user's knowledge? Can Dell reset UEFI settings if one runs the battery down to 0%? I realize that's bordering on magical thinking but that's the only unusual thing I've done on this machine in weeks.

Looks like the Ubuntu issue is solved for now. Windows 10, on the other hand...sigh. (edit) Maybe fixed...booted to Windows 10 Safe Mode, then rebooted to Windows 10 normally, and the error cleared up. 

Thanks for the suggestions!

---

### Post by oldfred on 2020-01-21
Back with BIOS, you could not change any settings from the operating system.

But with UEFI, many or most settings can be changed with software.
Now you also can update UEFI from Windows and some systems from Linux. And UEFI update resets to defaults which may vary by vendor.
My Asus motherboard needs multiple settings changed, my newer Gigabyte only a few.

I thought I saw one other post where a user thought Windows turned on Secure Boot, but not sure and it probably was an UEFI update.

Dell seems to be one of the first major vendors to support UEFI update from Linux and now has a long list of models that can be updated. One user thought Ubuntu did an UEFI update without asking? If you have all software updates turned on automatically, it may include UEFI update? My motherboards are not supported so do not know details.

UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

