---
title: "[Boot-Repair] Re-installation of GRUB is not possible"
date: 2015-05-28
forum: MINT
---

### Post by juansb on 2015-05-28
Using the Boot-Repair, I was trying to fix a problem with my Boot loader and this is what I got:

This is my BootInfo summary: [http://paste2.org/V1waaMg9](http://paste2.org/V1waaMg9)

When re-installing, after the deletion of Grub, I was not able to re-install Grub, because I got this message:

```
The following packages have unmet dependencies:
   linux-signed-generic : depends: linux-headers-generic (=3.13.0.53.60) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

I tried to install via Synaptic those packages but I was not possible.

And without GRUB I cant start my computer :( please help! If there is already another similar problem in the forum, sorry I have not searched 

Screenshot: [URL="https://app.box.com/s/36mkttn5srdr93rg0ms9cmqj2puey79r"]
[/URL][ATTACH=CONFIG]262253[/ATTACH]
[https://app.box.com/s/36mkttn5srdr93rg0ms9cmqj2puey79r](https://app.box.com/s/36mkttn5srdr93rg0ms9cmqj2puey79r)

Thanks for any help! :D

---

### Post by oldfred on 2015-05-28
Moved to Mint.

You have grub in MBR(BIOS) and in efi(UEFI) partition. You must be consistent in how you boot and since Windows is UEFI boot, you need to always boot in UEFI mode. Make sure UEFI is on, often better to have secure boot off, and CSM must be off. 

Are you not able to go into UEFI and its boot tab and choose which system to boot. Or most systems have a one time boot key that shows those same boot choices, often f10 or f12 but varies by vendor.

It looks like it is trying to use DVD as source. You should turn that off and make sure Ethernet is working and update from on-line repository. In Ubuntu you can change in settings in update manager, not sure with Mint.
> Failed to fetch cdrom://Linux Mint 17.1 _Rebecca_

If you have Internet working, then run Boot-Repair's advanced mode when booted in UEFI mode and do a full uninstall/reinstall of grub.

---

### Post by juansb on 2015-05-28
Ok I fixed the problem, and now I present the summary of the causes and the solution.

**[SIZE=5]Causes:[/SIZE]**

I was intending to migrate from Ubuntu 14.04 to Mint 17.1, and when partitioning I made a mistake in not formatting the root partition of Mint [***sda5***] (I thought if I don't format maybe Applications would be intact). Indeed, Linux Mint has not started, and Boot has only loaded the linux system, Windows was erased from GRUB.
In the second re-install I didn't know / or remeber what was ***sda3*** for, so I used it as BIOS Boot unaware what it means. So that screwed up my Boot Loader.

Then I tried from Ubuntu and Mint LIVE to make a rescue, but always something stopped the process, and with Boot-Repair I got to erase completely the GRUB with a non totally reparation of the boot.

[SIZE=4]Actual Partition Table:[/SIZE]
[SIZE=4][SIZE=1]
[/SIZE][/SIZE][TABLE="width: 764"]
[TR]
[TH="width: 46"]Device[/TH]
[TH="width: 60"]                 Size[/TH]
[TH="width: 96"]                 Content[/TH]
[TH="width: 336"]                 Type of Partition[/TH]
[TH="width: 184"]                 Description[/TH]
[/TR]
[TR]
[TD="width: 46"]                 sda1[/TD]
[TD="width: 60"]                 315 Mb[/TD]
[TD="width: 96"]                 NTFS[/TD]
[TD="width: 336"]                 Recovery Environment Microsoft Windows (System)[/TD]
[TD="width: 184"]                 Microsoft[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda2[/TD]
[TD="width: 60"]                 105 Mb[/TD]
[TD="width: 96"]                 FAT32[/TD]
[TD="width: 336"]                 EFI System[/TD]
[TD="width: 184"]                 Microsoft[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda3[/TD]
[TD="width: 60"]                 134 Mb[/TD]
[TD="width: 96"]                 unknown[/TD]
[TD="width: 336"]                 BIOS Boot[/TD]
[TD="width: 184"]                 unknown[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda4[/TD]
[TD="width: 60"]                 83 Gb[/TD]
[TD="width: 96"]                 NTFS[/TD]
[TD="width: 336"]                 Data Basics[/TD]
[TD="width: 184"]                 Win10 InsidePreview[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda5[/TD]
[TD="width: 60"]                 20 Gb[/TD]
[TD="width: 96"]                 Ext4 v1.0[/TD]
[TD="width: 336"]                 Linux Filesystem[/TD]
[TD="width: 184"]                 LinuxMint 17.1[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda6[/TD]
[TD="width: 60"]                 3 Gb[/TD]
[TD="width: 96"]                 SWAP[/TD]
[TD="width: 336"]                 Linux Swap Partition[/TD]
[TD="width: 184"]                 SWAP[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda7[/TD]
[TD="width: 60"]                 393 Gb[/TD]
[TD="width: 96"]                 Ext4 v1.0[/TD]
[TD="width: 336"]                 Linux Filesystem[/TD]
[TD="width: 184"]                 Personal Files Partition[/TD]
[/TR]
[TR]
[TD="width: 46"]                 sda[/TD]
[TD="width: 60"]                 1,1 Mb[/TD]
[TD="width: 96"]                 not assigned[/TD]
[TD="width: 336"]                 unknown[/TD]
[TD="width: 184"]                 Error[/TD]
[/TR]
[/TABLE]

[SIZE=5]**Solution:**[/SIZE]
As **oldfred** said, a full uninstall / reinstall would fix the problem, and I think it was a casuality, that after erasing the Grub, the installation of LinuxMint worked and it fixed all my problems hahah now I can start to Mint and to Win10. \\:D/

Thanks olfred for taking the time to help me :)

---

