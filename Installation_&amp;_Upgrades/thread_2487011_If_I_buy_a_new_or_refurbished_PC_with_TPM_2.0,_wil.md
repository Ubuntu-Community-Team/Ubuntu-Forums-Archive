---
title: "If I buy a new or refurbished PC with TPM 2.0, will I be able to dual boot Ubuntu?"
date: 2023-05-19
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2023-05-19
If I buy a new or refurbished PC with TPM 2.0, will I be able to dual boot Ubuntu on it? 

I am worried that I will not be able to use Ubuntu if I buy a new PC with TPM 2.0. 

Threads on the forum like this one Thread: [TPM 2.0 / Secure Boot - Locked]("https://ubuntuforums.org/showthread.php?t=2476355") have me worried that I will no longer be able to use Ubuntu (or other form of Linux) on a purchased PC. Whether the PC is refurbished or new.

QUESTION: Does anybody have any comments or suggestions as to what I should do if I want to dual boot Windows 11 and Ubuntu (or other version of Linux)? 

Thank you,

A.

---

### Post by #&amp;thj^% on 2023-05-19
I'm not a fan of dual booting windows at all so no help from me there. (sorry)
But not all TPM devices are the same IE:
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cat /sys/class/tpm/tpm*/tpm_version_major
2
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> [ -c /dev/tpm0 ] && echo "TPM 1.2 or 2.0"
TPM 1.2 or 2.0
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>

```
ADDED:
```
sudo dmesg | grep -i tpm
[sudo] password for me: 
[    0.000000] efi: ACPI=0xcdffe000 ACPI 2.0=0xcdffe014 TPMFinalLog=0xcdefc000 SMBIOS=0xcb70d000 SMBIOS 3.0=0xcb70b000 ESRT=0xb6640a18 MEMATTR=0xb5214018 
[    0.005718] ACPI: TPM2 0x00000000CDFF0000 000034 (v04 LENOVO CB-01    00000001      01000013)
[    0.005777] ACPI: Reserving TPM2 table memory at [mem 0xcdff0000-0xcdff0033]
[    1.891774] tpm tpm0: AMD fTPM version 0x3002f00000005 causes system stutter; hwrng disabled
[    2.557156] systemd[1]: systemd 253.4-1-arch running in system mode (+PAM +AUDIT -SELINUX -APPARMOR -IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY +P11KIT -QRENCODE +TPM2 +BZIP2 +LZ4 +XZ +ZLIB +ZSTD +BPF_FRAMEWORK +XKBCOMMON +UTMP -SYSVINIT default-hierarchy=unified)
[    2.878154] systemd[1]: TPM2 PCR Machine ID Measurement was skipped because of an unmet condition check (ConditionPathExists=/sys/firmware/efi/efivars/StubPcrKernelImage-4a67b082-0a4c-41cf-b6c7-440b29bb8c4f).

```
You will need to study the refurbed machine to see if it is locked for windows only.
If you really need windows, consider running one OS in a VM....save yourself from a lot of frustrations that way. ;)

---

### Post by ian-weisser on 2023-05-19
> **AbleTassie said:**
> Threads on the forum like this one Thread: [TPM 2.0 / Secure Boot - Locked]("https://ubuntuforums.org/showthread.php?t=2476355") ...

...are an example of the perils of dual-booting with Windows.

If you read that thread carefully, Ubuntu didn't lock the fellow out of Ubuntu. The OEM didn't lock the fellow out of Ubuntu. A Windows update caused the problem...as Windows updates have been doing, on and off, for the entire history of Ubuntu.

So sure, you will be able to install Ubuntu. And you will be able to dual boot...until you cannot. Nothing new there.

I honestly have no idea why dual-booting remains a popular question among new folks. It's so much harder, more fraught, and more limited than simply using a VM.

---

### Post by ajohnl on 2023-05-20
One solution may be to ensure the machine comes with OS installation kit including drivers. The latest version of openbox will support win11 so that could be installed under Linux and win added that way. Best look for comments on openbox's site incase there are TPM variations.

On bios and things greyed out. I have bought a new win11 HP machine. The bios can be a bit confusing as one section can change another. First thing I noticed was boot order.  A use once boot order change can be made. A permanent change has to be made elsewhere. It seems when dual booting win's fast boot must be turned off and bitlocking undone if the drive is set up that way. On win11 I turned off fast boot but following an update I can't find the section to do it any more. Fast boot can also be turned off in the bios but that may be another fast boot. Win will do some sort of sleep type turn off if it can. Selecting turn off should prevent that.

There may be another change as well but based on updating a win 8.1 laptop that hadn't been used for several years. The machine had been set up to use our wifi so win used it when auto updates were turned off and before I logged in. Turn off options changed to update and then turn off etc. Updates took a while and then reported a fail following a reboot and reverted most of the changes. As one of the updates wrecked Dell's recovery stuff I ran the update 3 times. The last one has destroyed win. Black screen of death rather than the blue one. The change to turning the machine off may be to make all users update. This may relate to all versions that they still support.

MS do not officially support running under a vm. On the face it they do support dual booting. This page mentions some of the complications and options.
[https://wiki.archlinux.org/title/Dual_boot_with_Windows](https://wiki.archlinux.org/title/Dual_boot_with_Windows)

---

### Post by TheFu on 2023-05-20
Add me to the "use a virtual machine" group.  I stopped dual booting around 2008 when any mid-range CPU became capable of running Windows inside a VM nicely.  VMs remove all sorts of issues.  Just pick the host OS carefully.

---

### Post by MAFoElffen on 2023-05-20
+1 on the VM side for Windows. (This may be a surprise to people here, that know me.) Though with the title of this thread, TPM 2.0 is not an issue for being dual-boot or not.

I have been on the other side of this... But now am on the fence. I have been doing multi-boots for 13 years now. Even on them, I have only had a VM of Windows on Linux... And of Linux on Windows.

*** I have a PC with TPM 2.0, and pass-through the TPM for KVM Virtual Machine Hosting for use with hosting Windows VM's. So, "NO".... I do not have a problem with a computer having a TPM and running Ubuntu Linux. Also... TPM 2.0 can also be emulated via package 'swtpm' to use with KVM VM's to install Windows 11. ***

I do not have a problem installing Ubuntu with SecureBoot enabled... Since around LTS 20.04. 22.04 is even better at that.

On my daily runners, I do only run LTS versions. I test Development versions, but I do not use them as daily runners. My testing process is brutal, to see where I can break things, and to see just how far I can push things, so I run them in sandboxes.

I am not an average "User". I do Ubuntu +1 DEV testing, so am used to dealing with problems of some type almost daily. I am used to dealing with boot problems as they arise. My config's are not "vanilla." But I do not want to deal with problems in my daily runner. They need to be stable, and reliable.

The computers that have problems with being dual-boot, and have BIOS issues tied to the TPM, seem to be mostly of one brand... HP: Hewlett Packard, and their UEFI BIOS settings, that they want to lock a machine to using Windows. I (personally) hate to say that, because I have used HPC Server hardware for years, and my son-in-law is closely related to the Packard Family... But it is true, and the problem is there.

Why am I on the fence now with Dual-booting? As TheFu said, and as I have recommended to others, maintaining a dual-boot is work. Windows runs great in a VM! I very rarely use Windows these days, any more. The most I use it them now, is to keep their Updates current. Or to do Insider Testing. I have a few games I still play on Windows... But my time is not as free as it has been in the past. That is about it.

My hardware is "open." My configurations are very complex. I have a maintenance program that I stick to for security and recovery. Why? Because I know, with what I do, things do break.

---

### Post by ajohnl on 2023-05-21
I've dual booted for a long time. Must be over 25years now but initially installed linux in a VM under windows. An enterprise version of Linux. Suse bought from PCWorld. Boxed DVD's and docs. It came with a support phone number that wouldn't cover an Intel motherboard and a machine with more than one drive but the guy gave me  some set up tips. PCworld probably started selling it as the number of people using it in the USA was increasing steadily.  ;) Linux people often saw it as a boring distro as it always worked. That meant that latest releases always took a while to appear,

Why dual boot. I suppose in my case there are 2 reasons. In case I need it and the fact that I have paid for it. The machine I am on now has been dual booting for just over 3 years and win has never been used. It's a win10 HP machine. Going on a laptop that hadn't been used for a long time, win8.1 it does seem to be a good idea to use win from time to time to update. The updates have trashed windows and also dell's recovery software. HP do that via the bios. Win seem to have made changes to make people use update. Also taken steps to prevent people changing passwords via back doors. No problem if their accounts system worked properly and it was possible to talk to some one. A legal reinstall can mess this area up.

My next dual boot will be on a newer far far more recent HP model. It looks like the bios will just warn about boot changes as the win10 machine did. The previous post suggests I may have other problems. My main beef is no win installation media as the machine uses digitally signed. Also HP do not support 2 OS's on the same machine.

---

### Post by ian-weisser on 2023-05-21
Well said. Thank you for explaining some good reasons to dual-boot.

---

### Post by ajohnl on 2023-05-21
Dual boot problems? I am using a laptop to try out 2 versions of Ubuntu, straight and Studio. So I have straight installed UEFI and used a UEFI boot option to install Studio from USB. I selected mount to / in free space as there is an EFI partition. It said no can do, a boot efi partition is needed. So selected an auto install and pointed it at free space. It showed before and after correctly so went ahead. I now find I've lost the option to boot straight ubuntu, It just goes to studio, I can't copy past the output from this command on that machine. This is from the one I am using

```

efibootmgr -v
BootCurrent: 0001
Timeout: 5 seconds
BootOrder: 0004,0001,0000,0005,0003
Boot0000* Windows Boot Manager  HD(1,GPT,60ad8d5d-3aee-4a2f-bef7-147f3cafa2f2,0x800,0xb4000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o....................ISPH
Boot0001* opensuse-secureboot   HD(1,GPT,384d9607-06e3-46dc-8a68-fcb39ea9c2af,0x800,0xc8000)/File(\EFI\opensuse\shim.efi)....ISPH
Boot0003* SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127     BBS(HD,SAMSUNG MZVLB1T0HALR-000H1-S3WSNX0M105127,0x400)/PciRoot(0x0)/Pci(0x1b,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-25-38-81-91-B6-73-D8)......ISPH
Boot0004* Generic USB Storage 000000000830      PciRoot(0x0)/Pci(0x14,0x0)/USB(24,0)/USB(2,0)/USB(2,0)N.....YM....R,Y.....ISPH
Boot0005  USB:          BBS(65535,,0x0)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH

```

The entries state where the boot managers are. LOL Trust win to have the longest entry. The laptop just shows one Ubuntu when there should be 2..

All win problems / hp. I wonder.

---

### Post by TheFu on 2023-05-21
I thought all versions of Ubuntu were basically the same, just with different DEs and default applications.  To test different DEs, install them all, but create new userids for each and prior to login, pick the DE you want running.  This will avoid personalized config file file collisions.  No need to dual boot at all.

When done, remove the DEs you don't like and delete the extra userids with their HOME directories.

I suppose, some DEs are tightly coupled to the login manager, so reinstalling the login-manager tool that is most common to the selected DE might be necessary, but that should be it.

Oh ... and run **sudo apt autoremove --purge** when all done to remote the hundreds of packages installed that you don't want.

At least, that's my expectation and how I'd attempt the goal of picking a new DE. YMMV.  I stopped desktop switching a few years ago and returned to the pure WM-only setup I'd used first in the 1990s. Different DEs just slow me down looking for the 50 things I actually use whereas my WM setup has those things all at my fingertips. Everyone needs to find their happy place.  Hope you find yours.

---

### Post by ajohnl on 2023-05-21
I have done the different desktop and select by user name in the past.  :) I got really annoyed. It resulted in a mix of applications from  different desktops on each one. Annoyed because of how the desktop icon  files were arranged by the distro i used. All in one directory and not  separated according to  desktop, ;) Maybe things have changed. I did  look at xdg aspects to correct it but too much work. If apps were off  the ~xdg home directory it could have worked or if they were split  according to desktop type. There were comments around concerning the myth that a linux install can offer different desktops.

Straight Ubuntu and Studio though. Studio has shifted to KDE so totally different on the desktop area. I'm not sure it's possible to add what it offers to Ubuntu any more. Must admit for my use I am not keen on Ubuntu's start button ;) or as I sometimes wear varifocals having things right at the top of the screen. Needs a rubber neck. I have added things to change that but.............

UEFI though. I have read a reasonable overview about but comments I see add to confusion. Those efi entries are pointers to boot loaders. It would seem that all an install needs to do is extend the list, change the boot order and collect the pointers to other OS's boot loaders which could be located anywhere. The Dell includes 2 net ones. IPV4 and 6 and network. Suppose for support. Also a change boot setting - that may be Dell's F12 key to set a none standard boot such as UEFI usb or even legacy. Some of these can not be changed from the bios only  via a utility.

The opensuse output I posted fitted in with my view of how it should work by offering an option during it's boot to jump to the win boot manager. Sadly they seem to be falling behind on maintaining popular apps in their long term releases. Also a video by an Arch user who tries various distro's. All appear in his menu and items can be removed with efibootmgr.

I think I will try renaming the Ubuntu entry to Studio if I can after making sure it is booting UEFI mode as it did install legacy when win was on the machine as win was installed that way. This can even happen when 10 is on a machine.  Then reinstall Ubuntu over it's current partition to see if it gets it right. I'll just assume it will automatically use the  existing efi. On studio I could only do that with an auto install pointing at a particular partition. Manual partitioning insisted I needed to create one even though there was one there. The auto way didn't appear to create a new efi and doesn't seem to have overwritten the lot as it still contains bios entries.

---

### Post by ian-weisser on 2023-05-21
> **ajohnl said:**
> Sadly they seem to be falling behind on maintaining popular apps in their long term releases.

That's not a bug. That's been the main **feature** of LTS since 2006. That's what makes LTS possible.

---

### Post by oldfred on 2023-05-21
You just have to be consistent.
If UEFI hardware better to always use UEFI, not BIOS/Legacy/CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

And if using UEFI always use gpt partitioning. From 
man fdisk
> 
[FONT=monospace][COLOR=#000000]**GPT**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**(GUID**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Partition**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**Table)**[/COLOR][COLOR=#000000] [/COLOR]
           GPT is modern standard for the layout of the partition table. GPT uses 64-bit logical block addresses, 
           checksums, UUIDs and names for partitions and an unlimited number of partitions (although the number of 
           partitions is usually restricted to 128 in many partitioning tools). 

           Note that the first sector is still reserved for a [COLOR=#000000]**protective**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]**MBR**[/COLOR][COLOR=#000000] in the GPT specification. It prevents MBR-only [/COLOR]
           partitioning tools from mis-recognizing and overwriting GPT disks. 

           GPT is always a better choice than MBR, especially on modern hardware with a UEFI boot loader.


[/FONT]

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

---

### Post by MAFoElffen on 2023-05-21
+1 on GPT and using UEFI.

---

### Post by ajohnl on 2023-05-21
:) That post was a bit confused in terms of what went wrong. My fault. The output shown by efibootmgr is in none volatile memory. The install should have added an entry to that and collected any other OS's. The machine shows one ubuntu entry. That points to a 32bit  FAT partition on a particular disk+sector that contains grub and what ever. Ubuntu is the highest priority in the list so if Studio is using UEFI that is how it's booting. As there is only one ubuntu entry it can't have added another entry, It could still boot legacy and add efi boot manager entries to it's menu. I haven't checked that it is using UEFI yet, I need to follow instructions in another post I made,

Collecting OS's isn't nice as for instance windows is still shown but no longer exists on the machine. It's 32bit fat partition has gone. It could have been anywhere. Grub could pick up all nv stored boot entries and jump to them even USB etc if that was there.

The OP's post. This is one of the few that mentions using win's boot manager for other OS's including Linux. Sadly it doesn't use Linux  as an example, just mentions it. Grub would be in it's efi partition and not offer boot options Just load etc. This gets mentioned but I have yet to see an example of how it could be done. Things can be reordered within win's boot manager. There are also other boot managers around. Not something I have looked into.

---

### Post by tea for one on 2023-05-21
> **AbleTassie said:**
> If I buy a new or refurbished PC with TPM 2.0, will I be able to dual boot Ubuntu on it? 
Yes, I would certainly hope so, because you should be able to disable TPM in the UEFI settings.

How about re-phrasing the the question:-
If I were to buy a PC with Ubuntu pre-installed, can I dual boot with Windows 11?

---

### Post by AbleTassie on 2023-05-22
Hello,

Thanks to everybody for their posts. **I think you all have more or less persuaded me to switch back to Lubuntu and just to run the Windows 10 I already have in a Virtual Machine. **I also did some reading comparing the security of Linux vs Windows 10, as well as the speed of Linux vs Windows 10 and that was persuasive too.

I used to use Lubuntu all the time and in fact ran Windows XP as a Virtual Machine in Lubuntu. But I had some problems connecting the Virtual Machine to the internet and also to the CD Disc reader. As I recall I eventually got the Virtual Machine with Windows XP to connect (at least to some extent) to the internet and the CD Disc reader. But, I also ended up creating a "Shared Folder" that allowed me to transfer files back and forth between the regular real Lubuntu Machine and the VM with Windows XP. And that worked pretty well.

**But, if it is appropriate to ask the questions here on this Forum, I have a couple of questions about using a VM with Windows 10 with my present PC after I install the latest Lubuntu LTS.** 

My  present machine is an ACER E5-575-33BM with Windows 10 Home Edition; **Processor** Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz   2.40 GHz, **RAM** 4.00 GB (3.87 GB usable), **System Type**: 64-bit operating system, x64-based processor.
I believe the Windows 10  Operating System Product Key that came with my present machine has code that is somehow  burned into the UEFI or motherboard so that the Windows 10 operating system can be  reinstalled via an internet connection. I think this link ([https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html](https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html)) contains instructions on how to do this.

QUESTIONS: Do you think I will have trouble Virtualizing the Windows 10 that I presently have on my PC after I install the latest Lubuntu LTS given that the Windows 10 Product Key is apparently on the UEFI or motherboard?

Do you think I will have trouble connecting the VM with Windows 10 on it to the internet or my CD/DVD reader?

If I do have such a problem with connecting the VM with Windows 10 to the internet and/or my CD/DVD reader, would there be some limited work around, like a "shared folder" that would allow me to transfer files back and forth between the real machine with Lubuntu and the VM with Windows 10?

Thanks again,

A.

---

### Post by MAFoElffen on 2023-05-22
News on your Microsoft Pluton TPU concerns...
RE: [https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3](https://www.phoronix.com/news/Pluton-TPM-CRB-Merged-Linux-6.3)

On retrieving your motherboard injected digital product key, from Windows Powershell, started with Admin rights, do:
```

(Get-WmiObject -query 'select * from SoftwareLicensingService'). OA3xOriginalProductKey

```
You can use that key to re-activate your Windows...

Shared storage folders, yes. Many ways, differing based on the VM Host system you are using. Be specific and someone who knows about that Virtual Host system can answer you about the how-to's. I mostly use KVM, which varies depending on the viewer you are using. Passing through the CD/DVD drive is possible, but how to do that also varies on what you are using.

Networking, yes. Same conditions as above. Most use NAT and dhcp as a default.

---

### Post by ajohnl on 2023-05-22
> **ian-weisser said:**
> That's not a bug. That's been the main **feature** of LTS since 2006. That's what makes LTS possible.

I was referring to a different distro not Ubuntu  flavours. I haven't seen the same problem on Ubuntu. I expect LTS packages to lag behind the latest releases. What I don't expect is to find only experimental packages to be available or via another install method to offer a selection with no mention of which one is best to use. So I  installed an experimental version of gimp and had dependency problems within 2 days on updates.

Another change as well. I had a problem with wine asked winehq what to do. Go away and install the latest version pointing out that I was lucky as the repo of the distro I was using always contained the latest version that would be compatible with my release.. This wasn't maintained by the parent distro company but by some individual. A couple of photo apps I use were maintained in much the same way so were always updated and never caused problems. There is some risk when these are used so some removal may be needed at times but that never happened with the ones i regularly used.

Ubuntu. The desktop app  search has failed to provide some packages I need. Use of the official LTS repo to install has thrown up dependency problems - of the can't install type. Apt search and apt install has so far installed. Risky? have to wait and see.

Another example. I'm not sure I want a snap version of Firefox. Youtube of all places informs me that 2 installable versions are maintained by some one that is seen as reliable. One version is kept fairly up to date. The other lags for business and school use. What I have done is installed Chromium the OS version of Chrome. ;)Initial feeling what the hell have they done to it - toolbar gone. I sometimes print to pdf. Maybe I need to poke around in it's settings more. Anyway these things are available under Ubuntu. Finding them may be a bit more tricky than my previous disto but the facility I used has gone.

---

### Post by TheFu on 2023-05-22
> **AbleTassie said:**
> 
My  present machine is an ACER E5-575-33BM with Windows 10 Home Edition; **Processor** Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz   2.40 GHz, **RAM** 4.00 GB (3.87 GB usable), **System Type**: 64-bit operating system, x64-based processor.
I believe the Windows 10  Operating System Product Key that came with my present machine has code that is somehow  burned into the UEFI or motherboard so that the Windows 10 operating system can be  reinstalled via an internet connection. I think this link ([https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html](https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html)) contains instructions on how to do this.

So, you will want more RAM.  4GB isn't sufficient to run a VM, well, not really. RAM is cheap.  16GB should be about $40.

I know nothing about Win10 or licenses of it. Sorry.
> **AbleTassie said:**
> 
Do you think I will have trouble connecting the VM with Windows 10 on it to the internet or my CD/DVD reader?

In virtualbox, choose either NAT or bridged for the networking type and it sorta "just works".  Also, use virtio as the type of NIC, if virtualbox allow it. Otherwise, choose one of the Intel PRO/1000 virtual-NICs as the presented hardware to the VM.

If it were me, I'd completely forget about accessing the CD/DVD drive from inside any VM. It just isn't worth the hassle and terrible performance.

> **AbleTassie said:**
> If I do have such a problem with connecting the VM with Windows 10 to the internet and/or my CD/DVD reader, would there be some limited work around, like a "shared folder" that would allow me to transfer files back and forth between the real machine with Lubuntu and the VM with Windows 10?

Lubuntu used to be based on GTK+/Gnome2.  In 2020, they switched to be based on Qt which what KDE is based on, so there will be many differences and the default applications will all be Qt-based, not Gnome-based. With only 4GB of RAM, this will matter a bunch.  If you put in 8-16GB of RAM, then it becomes less important and you can run almost anything you like.  4GB of RAM is the bare minimum for any computer these days, much more so if you use virtualization.

---

### Post by ajohnl on 2023-05-22
[I]You can use that key to re-activate your Windows...


[/I]Thanks I may find that useful as HP sent me win10 and 11 usb's and dvd's. However there may still be a problem - win complained about the lack of signed drivers for the machine it was being installed on. They sent me driver dvd's but getting them in - pass no way could I do it. I had wiped the disk completely and set the bios to factory defaults. Having given up with the usb's and disks I simply rebooted. Bios said no OS would you like to install. Yes - not perfect as chuntered for a while and then stopped. Another reboot finished it off. This install when I ran it went through the usual stuff other than activation. It wanted a MS account - I simply used the outlook route it offered.

The OP's original post. If dual booting to another OS with windows TPM should not matter providing all parties even the machine makers sticks to the UEFI spec. Win is the only thing that needs it.UEFI is aimed at multi booting. ;)Mind you that may not strictly mean multiple OS's. Years ago a judge in the USA took steps to break up the ties between MS and HP. One factor mentioned was difficulties running multiple OS's - pass on that. Not sure I was when this happened.

HP and MS - both have done helpful work on Linux.

---

### Post by ajohnl on 2023-05-22
> My  present machine is an ACER E5-575-33BM with Windows 10 Home Edition; **Processor** Intel(R) Core(TM) i3-7100U CPU @ 2.40GHz   2.40 GHz, **RAM** 4.00 GB (3.87 GB usable), **System Type**: 64-bit operating system, x64-based processor.
I believe the Windows 10  Operating System Product Key that came with my  present machine has code that is somehow  burned into the UEFI or  motherboard so that the Windows 10 operating system can be  reinstalled  via an internet connection. I think this link ([https://www.tenforums.com/tutorials/...dows-10-a.html]("https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html")) contains instructions on how to do this.

QUESTIONS: Do you think I will have trouble Virtualizing the Windows 10  that I presently have on my PC after I install the latest Lubuntu LTS  given that the Windows 10 Product Key is apparently on the UEFI or  motherboard?

The tutorial is a bit mixed as it mentions product keys and later says digitally signed will correct itself. Also use of your Microsoft account. Machines may be supplied with win digitally signed or via a normal install and no installation media. Those should have the activation key some where on them. A label. It may not be on the outside of say a laptop. I think some have been stuck in the battery compartment etc. MS log the activation keys as win is installed. They may complain if hardware is changed even on the original machine it's installed on. That may be a past problem. People had to log into their account. That made adding a disk etc ok. They may have stopped doing this. This area is all down to their licensing terms - on one machine. Some might move a disk from one to another or clone etc.

I thought that there was only a few companies that used digitally signed. 2 for instance HP and Lenovo but there could be others. If a machine comes with the activation key stuck on it reinstall is simple. Download the correct media from MS, install and use the activation key. You may need your account email address but as mine was blacked on win11 I just took out another, It was blacked because I wrecked win II and tried to reinstall with media downloaded from MS on a machine that was digitally signed. Suspicious use noticed.

On my win10 machine I plugged in a 2nd ssd. No problems. Does win log other hardware aspects - I don't know. Digitally signed is likely to have problems used on a different machine. There are utilities around to extract win activation keys. Digitally signed too ??? Win 10 may be able to do that itself under security but if digitally signed it might just state that. The tutorial mentions generating installation media, I'd assume via win itself but with MS iso's available that's not really needed. The iso must match the legit version of win also it may complain about registering as both personal use and business use at some point so best keep even that the same.

Maybe you best option is to play with what you have. Look at ways of getting win installation media and keys. Load a VM into linux and see what happens. Update the machine - perhaps find out how win was installed but that doesn't mean all will be ok. TPM worries may be a red herring. EEEEkkk I'll find out, my win11 machine is bound to have it and is digitally signed. Use a VM. When I have used those in the past they have been transparent from a use point of view, No resource allocation and mouse position sets what's running*. I'd ideally want that again but have no idea if it is available. A heavy resource using win app isn't going to be spectacular using one core and a bit of ram. Dual booting takes care of that. I've mostly got away with using wine under linux but I only run odd win apps. Updating firmware has needed windows also certain apps provided with cameras where it's best to use these. Spreadsheets? Fulling compatible. Yes and no. I have come across some full of macro's and they wont run correctly under linux.

*Not exactly true but resource usage looked after itself.

:) TBH I should be asking myself if I really need win but having paid for it I'd like to keep it. I have seen signs on win installs I still have that it is best to update them from time to time as not doing that may mess up recovery methods, Updates have trashed a win 8.1 install I have. My win10 hasn't been updated for several years. Dual booted and not used. I've forgotten the password and recovery on that aspect is no longer working. It has used the net connection and will make use of it even before I have logged on. ;) Makes me feel a bit paranoid.

---

### Post by MAFoElffen on 2023-05-22
> **ajohnl said:**
> The tutorial is a bit mixed as it mentions product keys and later says digitally signed will correct itself. Also use of your Microsoft account. 
Your comments about there being a Label somewhere inside the case, or in the battery compartment... are incorrect. Labels for those product keys haven't been used by Name Brand computer manufacturers for a very long time.

I was a certified HP, Dell and Lenovo Onsite Warranty Service Tech. (...up until about a year ago.) The digital key, "them" saying the key is injected into the motherboard, is sort of correct, but a bit misleading. I don't know why they make it sound so "magical". What that really means is that it is flashed into the permanent storage area of the BIOS. It is in an protected area of the BIOS that not overwritten by reflashing the BIOS. 

Use the PowerShell command I posted previously to retrieve the key from the BIOS. 

When  I was called in to replace motherboards, I had use the specific vendor's tools to manually enter the product key from the old motherboards, into the replacement motherboards, so that Windows would stay activated. With some vendors, you only had one-chance to get it right. If incorrectly done, we had to return the motherboard (for the depot to unlock again) and have another new board shipped out via overnight shipping. If I was called onsite to reload Windows onto a machine, Windows would use that same key to activate. It is a good idea to create at least one User with your Microsoft account, because that account would also store that key, and your 64 digit encryption key from bit-locker.

I loved it when I was called onsite for a pre-loaded Ubuntu machine, that their own vendor support had nothing in their support scripts, to be able to support. With me getting on the phone, to a different tier, I still had to give them the serial or tag number, to prove that they sold something with Ubuntu pre-loaded from the factory, and that they had to support it. Ugh. LOL.

Tier 1 support also had no idea that they have their own repo's with specific Linux drivers or their own products...

IMHO... For the main name brands, stay with Dell: Dell Optiplex 3000 Thin Client, Precision 3460 Small Form Factor Workstation, Dell XPS 13 Developer Edition... All were factory builds that could be ordered with Ubuntu pre-installed. As well as any Dell EMC PowerEdge product. Dell has great support and repositories for Ubuntu. Then Lenovo, then HP. In that order... For those 3.

---

### Post by TheFu on 2023-05-24
> **MAFoElffen said:**
>  It is a good idea to create at least one User with your Microsoft account, because that account would also store that key, and your 64 digit encryption key from bit-locker.

This was the main reason I stopped using MS-Windows.  I've never had any MSFT account. Don't want any and certainly don't want them to have access to any of my encryption keys.

When MSFT tried to update their EULA under Win7, Win8 and Win10 to add this and allow them the contractual wording that said they could load software without my permission, I started blocking all MSFT IPs.  I have 2 Win7 systems (not currently booted) still. One runs inside a VM and is used for tax and financial software. Works great.  It still tries to phone home, constantly.  The financial software is from 2013 and still works fine though that company has switched to an annual subscription for $35 model. Doesn't impact me.  I started using their software in 1991.  I'm looking for a native Linux replacement.

I'm fortunate that 
a) I don't need MS-Windows
b) the software I need still works

---

### Post by AbleTassie on 2023-05-25
Thanks for all the posts. **You guys have pretty much persuaded me to install Lubuntu and use Windows on a VM machine.** Right now I am thinking that I only really need Windows for tax software. 

I personally agree with the Fu and others: I don't like Microsoft snooping all over the place. And I remember visiting some Linux forums many years ago and posters encouraging me to *"give Microsoft the old heave ho,"* which I was more than ready to do and did. The only reason I am using Windows 10 now is because I was given a cheap brand new PC as a Christmas gift about 5.5 years ago. And I never really took the time to figure out how to dual boot Lubuntu. It's not that straightforward anymore, with UEFIs, fast and secure boots, etc. It was easier at one time with the old BIOS.

In any case, my once brand new gift PC (5.5 year-old Acer Aspire E5-575) has two keys that don't work anymore, has a hairline crack in the lid and missing rubber "feet" on the bottom of the PC. I just need to see if I can get some free RAM from a relative to increase my RAM and see if I can buy a cheap keyboard (without the touchpad, etc) in order to keep the cost of rehabilitating my present PC down before I install Lubuntu and then Windows 10 on a VM. If I can't keep the cost of rehab down, I will spend the money on a cheap refurbished, but newer PC with more RAM and I will install the latest Lubuntu LTS with Windows 10 on a VM -- I really don't want to spend more money for Windows 11 for the VM unless somebody explains why I should.

Thank you again and any more comments or advice will be appreciated.

A.

---

### Post by TheFu on 2023-05-25
Acer Aspire E5-575 ... I don't know specific models, but we used to have Linux InstallFests at the local University and I definitely remember cheap Acer machines with CPUs that could support VT-x or AMD-v (those are the hardware virtual machine instructions) also having no way to enable those features in the BIOS.  That means you should check the BIOS for your computer and verify that "Virtualization" can be enabled.

I double-checked that the i3-7100U CPU does support VT-x.  [https://ark.intel.com/content/www/us/en/ark/products/95442/intel-core-i37100u-processor-3m-cache-2-40-ghz.html](https://ark.intel.com/content/www/us/en/ark/products/95442/intel-core-i37100u-processor-3m-cache-2-40-ghz.html)  

You need to check the BIOS yourself.  [https://community.acer.com/en/discussion/498060/acer-aspire-e-15-e5-575-33bm-virtualization](https://community.acer.com/en/discussion/498060/acer-aspire-e-15-e5-575-33bm-virtualization) is encouraging. It says that recent Acer BIOSes have VT-x enabled, even if there's no way to enable it in the BIOS.  YMMV.

---

### Post by AbleTassie on 2023-06-15
Thanks to everybody for their replies, including TheFu MAFoElffen, oldfred, tea for one and others. I am marking this thread as SOLVED.

Thanks again,

A.[COLOR=#DD4814]****[/COLOR]

---

