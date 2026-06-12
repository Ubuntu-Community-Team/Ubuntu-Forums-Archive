---
title: "Best way to multi-boot Linux with Windows 10"
date: 2020-09-10
forum: Installation &amp; Upgrades
---

### Post by dryphi on 2020-09-10
What's the "best" way to install Linux (Ubuntu or another distro) alongside Windows 10 Pro with security features enabled? What I mean is, best or optimal in terms of preserving the security features? Which should be disabled and which can be kept? What's the order to follow (in disabling them)?

I'm currently multi-booting Windows 10 along with Mint and Zorin and plan to install the latest Ubuntu release as well. In order to get my system running smoothly I ended up disabling Fast Startup (don't care about this one), Secure Boot, and finally BitLocker. BitLocker gave me the most grief; despite disabling it before installing the other OS, it still required an annoying key every time it booted no matter what I did. I ended up just decrypting the drive.
Now my system runs smoothly; it boots into Grub2 and I can select whichever OS I want and I'm not prompted with any annoying security screen. But... those security features exist for a reason.

So....: which security features can I use with a multi-boot setup? Which ones can I leave enabled when installing?
I understand Ubuntu is verified and therefore will install with secure boot, so I'm assuming I can leave that enabled. But if I do, will it fail or BitLocker complain every time Grub updates?
What about BitLocker, can I / should I re-encrypt my drive at this point? Which partitions, just Windows? Does BitLocker need to be disabled before installing another (or any) Linux distro?

I've been scrounging the 'net about this for months and I still have not found an answer to my question. There's lots of posts and videos but most of them do not touch on the UEFI / Secure Boot / BitLocker stuff that's relatively new to Windows.
In brief, **what's the "correct" way to install Linux on a system with UEFI and Secure Boot and BitLocker?** Like step by step.

Given the dearth of information on the web about this topic I'm sure I'm not the only one with this question. Multi-booting with Win 10 Pro is a PITA. I may make a YouTube video or post once I figure out the best way to accomplish this.
All input appreciated. Thanks

---

### Post by oldfred on 2020-09-10
I do not have Windows nor currently use UEFI Secure Boot. But some info I have accumulated:

Dual boot with Bitlocker works
[https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10](https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10)

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

In the future I may need to turn Secure Boot on, but for now, it is off.
Torvalds clarifies Linux's Windows 8 Secure Boot position
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security



[https://www.phoronix.com/scan.php?page=news_item&px=systemd-246-Released](https://www.phoronix.com/scan.php?page=news_item&px=systemd-246-Released)
SystemD 246 July 2020 
Systemd-cryptsetup can now activate Microsoft BitLocker volumes during boot.

---

### Post by ActionParsnip on 2020-09-10
Don't assign all space to Windows. Plan your partition sizes and leave space for Ubuntu / other OSes. Have a separate data partition (Probably NTFS to accommodate Windows' shortfall) so that both system can easily access your casual data. This will most likely be the biggest file system. You'll want about 30Gb for Ubuntu to be comfortable and most of your images / music will live on the data partition.

Just how I'd do it. Assuming 1Tb drive:
500Gb Windows primary partition with a few megabytes partition for the UEFI nonsense that comes with it
50Gb Ubuntu primary partition
450Gb extended partition
450Gb data logical partition (mounted as /data in Ubuntu and D: or whatever you want in Windows)

Windows applications are far from trim. It depends what you are using Windows for. Games will need a lot more space so again, plan your sizes.

---

### Post by dryphi on 2020-09-10
> **oldfred said:**
> I do not have Windows nor currently use UEFI Secure Boot. But some info I have accumulated:

Dual boot with Bitlocker works
[https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10](https://askubuntu.com/questions/1135654/how-to-install-ubuntu-alongside-bitlocker-encrypted-windows10)

Thanks for the response and the links.

Yeah I saw that post before I started down this journey. I followed that sequence actually. Unfortunately it didn't "just work" for me as the top answer states. BitLocker still requested an annoyingly long key EVERY time it started, no matter how many times I tried disabling and rebooting, etc and inputting the key. It never seemed to accept the current state of my system. Maybe now if I re-encrypt it would work? Haven't tried it yet.

1) So I guess that's my primary question: What's the "correct" way to install another OS with BitLocker? Like step by step. Because apparently either I did something wrong or the multitude of Windows updates that have occurred since that post have affected it somehow. Maybe those steps are correct and I just did too many things at the same time though.

2) The second question is, since Grub2 updates fairly regularly, when it does, will this trigger Secure Boot and/or BitLocker?

---

### Post by oldfred on 2020-09-10
I do not yet think they have yet updated or maybe they never can update it to boot Windows in UEFI Secure boot mode. Its chain of trust issues.

Grub2 only occasionally updates UEFI files in ESP. Most of the updates are the files in /  (or /boot if separate).

If you just boot from UEFI directly, not from grub, is that still an issue?

---

### Post by dryphi on 2020-09-10
> **oldfred said:**
> I do not yet think they have yet updated or maybe they never can update it to boot Windows in UEFI Secure boot mode. Its chain of trust issues.
I believe they have. Canonical obtained a UEFI certificate signed by Microsoft. Apparently you can boot from a Ubuntu flash (for example) even with secure boot enabled. Although I didn't know that either when I first installed the other OS (I actually had Ubuntu installed before Mint).
[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

> **oldfred said:**
> Grub2 only occasionally updates UEFI files in ESP. Most of the updates are the files in /  (or /boot if separate).
That's good to know. Are you saying most of the Grub updates don't affect the boot sector? Maybe it would work then.

> **oldfred said:**
> If you just boot from UEFI directly, not from grub, is that still an issue?
What do you mean by this?
EDIT: Yes I believe it would be since the bootloader comes up after you exit the UEFI no matter what. Unless I'm misunderstanding something.
For example, I had BitLocker enabled and was booting from Grub2 but every time I selected the Windows OS it would still request the encryption key.
But I haven't tried it with SecureBoot enabled yet, because I disabled that before I installed Ubuntu.

---

### Post by dryphi on 2020-09-10
Maybe the best way to answer this is just to try it :)
Any advice on this?
Should I enable SecureBoot first, then encrypt? Does BitLocker encrypt the bootsector as well?

I'm traveling this weekend which is why I'm asking about all this but don't want to break my system either.

---

### Post by oldfred on 2020-09-10
The Key that Ubuntu uses is to allow grub/shim to boot. But the chain/configfile or boot into Windows from grub then is not secure. So Windows does not recognize it, even though grub boot was secure.
There were some recent updates to grub related to Secure Boot, but do not know if that changed if grub can chain back to Windows or not.

Your UEFI boot, same as you use to boot flash drive (f12 in many systems), has Windows & Ubuntu entries. That is a direct boot.
Grub also only boots working Windows. And Windows likes to update the fast start up setting turning it back on. Then hibernation flag is set & grub will not boot Windows. 
You then boot Windows directly from UEFI menu, to turn fast start up back off or fix any other Windows issues if fixable from its repair console. Always good idea to have Windows repair flash drive as well as Ubuntu live installer to be able to make repairs.
And of course good backups.

---

### Post by dryphi on 2020-09-10
> **oldfred said:**
> The Key that Ubuntu uses is to allow grub/shim to boot. But the chain/configfile or boot into Windows from grub then is not secure. So Windows does not recognize it, even though grub boot was secure.
There were some recent updates to grub related to Secure Boot, but do not know if that changed if grub can chain back to Windows or not.
Gotcha. Well, it only seems logical that, if Microsoft provided Canonical with a certificate, they would allow Grub to (securely) load Windows because otherwise installing any Linux distro would make Windows unbootable altogether (since the Windows bootloader can't boot Linux, forcing you to install Grub). But then again, this is Microsoft we're talking about here...
Put another way, Microsoft has essentially authorized the use of another organization's bootloader.

> **oldfred said:**
> Your UEFI boot, same as you use to boot flash drive (f12 in many systems), has Windows & Ubuntu entries. That is a direct boot.
Grub also only boots working Windows. And Windows likes to update the fast start up setting turning it back on. Then hibernation flag is set & grub will not boot Windows. 
You then boot Windows directly from UEFI menu, to turn fast start up back off or fix any other Windows issues if fixable from its repair console. Always good idea to have Windows repair flash drive as well as Ubuntu live installer to be able to make repairs.
And of course good backups.
Makes sense. I did not try that before. But if I boot Windows from UEFI, won't it then still go to the active bootloader, which would still be Grub? Or are the separate bootloaders actually stored INSIDE the UEFI now?

---

### Post by CelticWarrior on 2020-09-10
> **dryphi said:**
> Makes sense. I did not try that before. But if I boot Windows from UEFI, won't it then still go to the active bootloader, which would still be Grub? Or are the separate bootloaders actually stored INSIDE the UEFI now?

They're independent and stored in the ESP (EFI System Partition). That's the main difference in the UEFI's boot process vs BIOS, actually.

---

### Post by oldfred on 2020-09-10
If you run this, you see all the UEFI boot info with details. Entry in f12 UEFI boot menu is just description.
It shows partition number, GUID/partUUID of ESP, and file in ESP to use to boot. Then that file in ESP continues boot process.

```
fred@z97-focal-kubuntu:~$ sudo efibootmgr -v
[sudo] password for fred: 
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0002,0000,001C,0021,0025,0027,0029,002A,002B
Boot0000* bionic1804    HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\BIONIC1804\SHIMX64.EFI)
Boot0001* ubuntu        HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0002* focal HD(1,GPT,3195d314-ce88-42ac-beac-d9f80289ac11,0x800,0xf9dcd)/File(\EFI\FOCAL\SHIMX64.EFI)


```

Some systems have a lot of default entries. Some have another FAT32, not flagged as ESP, but they can boot system files from that partition. A few like HP, do not seem to remember setting changes with efibootmgr like boot order.  Some like Acer need "trust" or rename from within UEFI.

Many end up with duplicate or old entries in UEFI as it remembers those. Often good idea to check & houseclean if deleting systems. See also
man efibootmgr

---

### Post by dryphi on 2020-09-10
This is great. Thanks for the info.
So if I use efibootmgr I can remove old entries? But how do I recognize Ubuntu vs Mint vs whatever, because they all use the same boot stuff.?

---

### Post by oldfred on 2020-09-10
If only Ubuntu then, you only have one UEFI boot entry.
I have tried to change the GRUB_DISTRIBUTOR= in /etc/default/grub. It does create a new UEFI entry, but something is hard coded as /EFI/ubuntu/grub.cfg is always used.

Last installed version will be grub in control unless you edit /EFI/ubuntu/grub.cfg or reinstall grub from version you want in charge. You have to manage which grub you want, if more than one. And grub will let you boot any other install. 

I have multiple installs, some obsolete. So I turn off os-prober and add to 40_custom only those I still want in my grub menu.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

