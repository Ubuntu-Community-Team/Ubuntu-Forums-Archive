---
title: "[Mint]  How to set up a dual boot to go to linux, without stopping, by default"
date: 2018-09-25
forum: MINT
---

### Post by tinker123 on 2018-09-25
I have Mint Linux 18.* on my PC at home.

I would like to partition my hard drive and set up a dual boot with Windows 10  ( I have a licensed installation DVD ).

I currently have my Mint installation set up to go straight through to the desk top once I turn my computer on.   No stopping for passwords prompts or any other kind of stopping.

I would like to keep that as I will only be using Windows 10 occasionally.

I would like to be able to turn my PC on and have it go straight to the Mint desktop, without any intervention,  BUT with a menu that would appear temporarily  to pull out of that on the rare occasion I want to go to Windows.  That menu would appear temporarily, then disappear, then return to the default Mint booting unless I intervene.

Is this possible.

Can you point me to any docs on how to do it?

I haven't found what I wanted through Google.

---

### Post by deadflowr on 2018-09-25
*Thread moved to **MINT***

---

### Post by oldfred on 2018-09-25
If only occasionally, many here will suggest using a VM.
I have not yet installed anything into a VM, so do not know details.

If wanting dual boot, it is important to know if Mint is installed in UEFI or BIOS boot mode.
Windows only installs in UEFI boot mode to gpt partitioned drives.
And Windows only installs in BIOS boot mode to MBR partitioned drives.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Both UEFI & grub are boot managers or menus. And then you choose which to boot. You set one system as default and others as available if boot interrupted. But Windows must be in same boot mode as Mint for grub to be able to boot it at all.

But grub only boots working Windows. And Windows needs chkdsk sometimes and has its fast start up/hibernation, both of which prevent grub from booting Windows. If UEFI, you usually can directly boot Windows, but if BIOS, you have to temporarily reinstall Windows boot loader to MBR, fix Windows, and then restore grub to MBR.
Windows 10 will also turn its fast start up on with updates, which you may not always see.

---

### Post by tinker123 on 2018-09-26
I tried the VM route, it will not work for my needs.

Can what I want be done?   Have a dual boot that automatically boots up linux unless I intervene?

---

### Post by oldfred on 2018-09-26
You just set defaults in grub and/or UEFI to have Ubuntu as first.
I do have ability in my UEFI to set delay to 3 sec, so I have just enough time to press a key. If UEFI fast boot is on, you may not have time to press a key.
Grub's default is 10 sec, but I also change it to 3 as I am normally booting my working install. But have enough time to change to another install.

---

