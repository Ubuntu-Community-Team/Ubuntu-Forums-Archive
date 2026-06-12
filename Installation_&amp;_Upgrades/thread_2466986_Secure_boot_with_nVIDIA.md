---
title: "Secure boot with nVIDIA?"
date: 2021-09-12
forum: Installation &amp; Upgrades
---

### Post by bert.ram.aerts on 2021-09-12
I have a dual boot laptop with Ubuntu 21.04 and Windows 10.
Secure boot is disabled in the BIOS.
I use the nVIDIA proprietary drivers and Intel graphics are disabled in the BIOS (discrete graphics).
But when Windows 11 comes, secure boot should be enabled.
What should I do to prepare for this moment?
Is there somewhere a clear howto for enabling secure boot on an already installed Ubuntu before this is done in the BIOS?

---

### Post by CatKiller on 2021-09-13
> **bert.ram.aerts said:**
> Is there somewhere a clear howto for enabling secure boot on an already installed Ubuntu before this is done in the BIOS?
Probably. The term to look for is "enrolling a Machine-Owners' Key" or MOK.

The principle is that Secure Boot will only allow things to run if they've been signed by someone the UEFI trusts. Your UEFI trusts Microsoft. Since Ubuntu's stuff is signed using Microsoft's key, your UEFI also trusts Ubuntu. It doesn't trust Nvidia, since their stuff isn't signed. So you sign it yourself, as the owner of the machine, and tell the UEFI to trust your key.

---

### Post by oldfred on 2021-09-13
I currently do not use Secure Boot, nor plan to in near future unless major issues.
I also will not be dual booting Windows 11.

More info on Secure boot.
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)
[FONT=monospace][COLOR=#000000]man mokutil[/COLOR]


[/FONT]

---

### Post by MAFoElffen on 2021-09-14
NVidia "is not" a factor, in any way related to SecureBoot. Nvidia is "Graphics", not an Operating System. There is a difference in digitally signed "packages", which would relate to APT trusting if a package is trusted, before installing it... Or a BIOS trusting a non-digitally signed OS Kernel.

As for Windows 11... when the first preview came out, everyone freaked out over an ealry indication that it would only install if UEFI, that SecureBoot had to be enabled, AND that it had to be TPM 2.0 or newer capable... That was quickly found to be false and there are many work-arounds to install it on old legacy systems.

SecureBoot is always going to be a subject. Even with Windows. Many early Vendor implementations in UEFI firmware need their firmware updated to be compliant to what is current to today.

A number of years ago, Debian abandoned supporting booting with SecureBoot enabled, but promised to support it again in the future. Ubuntu, being right under Debian in the branch, took the lead in trying to support it again, to make Debian's promise good. They started supporting it again with LTS Version 20.04.

So Ubuntu today (20.04 and newer), if UEFI, will run with either SecureBoot enabled or disabled... But it running with SecureBoot enabled depends on other factors being in place for that to happen. One that the UEFI firmware is updated and current. Two, that grub-efi-<arch>-signed is installed, so that the current UEFI firmware see's the efi files as being signed and trusted. 

There are other ways, but not for the faint of heart (or unskilled). You could manually say it is trusted, using an UEFI utility, but then would be locked into doing that for each update of those files.

Are there ways? Yes, many ways, and many avenues. It's too early to tell which is the easiest and best.

What *is important* for all at this point, is to ensure that you keep up to date on your motherboard's BIOS firmware updates.

---

### Post by bert.ram.aerts on 2021-09-16
Thanks for the helpful replies!
My experience with enabling secure boot:

[LIST]
[*][COLOR=#000000][FONT=Arial]Secure boot enabled in BIOS (otherwise command in next step complains that secure boot is disabled)
Ubuntu booted fine but without nVIDIA proprietary drivers (but with nouveau driver) and without wifi (my own compiled driver)[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]sudo update-secureboot-policy --enroll-key[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]gave following error:
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo fuser -v /var/cache/debconf/config.dat[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]To find out PID of process locking the file and then [/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]kill -9 PID
This command brought up a user interface in terminal to set password for Machine Owners Key (MOK)[/FONT][/COLOR] 
[/LIST]

[LIST]
[*][COLOR=#000000][FONT=Arial]After reboot special MOK user interface was shown, selected enroll MOK, entered password from previous step, but take care keyboard is Querty at moment of entry[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]After further booting nVIDIA was loaded correctly[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]Undo iwlwifi own compiled driver and after reboot wifi was OK.[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]Remaining issue: VMware modules are not trusted[/FONT][/COLOR][COLOR=#000000][FONT=Arial], solution described in:
[/FONT][/COLOR][COLOR=#1155cc]_[https://kb.vmware.com/s/article/2146460](https://kb.vmware.com/s/article/2146460)_[/COLOR] 
[*][COLOR=#000000][FONT=Arial]sudo mokutil --import MOK.der (word sudo is missing in kb)[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Same password used as before[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]After reboot special MOK user interface was shown, selected enroll MOK, view MOK clearly showed word vmware, entered password of previous step, but take care keyboard is Querty at moment of entry[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]After further booting vmmon and vmnet are loaded but vmware reported that Windows 10 virtual machine was copied or moved, I selected moved. Windows 10 VM is running just fine.[/FONT][/COLOR] 
[*][COLOR=#000000][FONT=Arial]mokutil --list-enrolled[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]Gives overview of 3 keys on my system.[/FONT][/COLOR] 
[/LIST]

---

### Post by MAFoElffen on 2021-09-16
Good job. Yes, mokutil works... And yet, it is a pain.

So this is solved now? If so, please us the Thread Tools located at the upper Right of the page so others can find your solution to help solve their similar problems.

---

