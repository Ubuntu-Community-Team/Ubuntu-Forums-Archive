---
title: "Grub Won't load after Ubuntu Installed Win 7 Boots Automatically"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by AryaYawe1 on 2012-03-25
Hi

I just installed ubuntu and grub won't load.

It loads windows 7 automatically just like before ubuntu installed.

Am using an acer aspire 5560g.

Thanks

---

### Post by Ryan Csh on 2012-03-25
what exactly do you mean? ubuntu installed win7?

---

### Post by darkod on 2012-03-25
You need to explain more.
Do you have more than one hdd? In that case you might have windows bootloader on the disk you are booting from, and grub2 might be on the other disk. Try changing the boot order in bios.

Are you running raid maybe? If you installed on raid using the standard desktop live cd very often grub2 can't get installed. That is why raid installs should be done with the alternate install cd.

---

### Post by garvinrick4 on 2012-03-25
Run boot_info_script from site below in Live CD and post results (Will give users a good look at your machine)
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

---

### Post by AryaYawe1 on 2012-03-27
Hi

sorry to not be more specific

no i don't have multiple hard drives, or a raid setup.

I used the standard installer, and used the slider to specify how much space to give ubuntu in the partition.

Needless to say, when i restarted...... no grub and windows seven started as normal.

Thanks

---

### Post by darkod on 2012-03-27
Please post the results of the boot info script as asked above. It will show us more details.

---

### Post by Spewed on 2012-03-27
> **AryaYawe1 said:**
> Hi

I just installed ubuntu and grub won't load.

It loads windows 7 automatically just like before ubuntu installed.

Am using an acer aspire 5560g.

Thanks


Hey, I had the same issue. I have a dual boot of Windows 7 and Ubuntu 11.10. There is a very simple solution to this problem. You can at least try it before doing anything else. 

I'm assuming you have a Ubuntu CD or USB that you used to install Ubuntu with. Go ahead and put that in and boot into the live version of Ubuntu. The version that says "Try Ubuntu", where you can use without installing anything. Once you do that open up the terminal and do a boot repair. The entire reason you'll be doing a boot repair is to repair GRUB, and have it boot up when you boot your computer back up. 

So press CTRL ALT T and enter your terminal, and enter the following one by one.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```

Let me know if that fixes your problem. :D

---

### Post by confussionaut on 2012-05-06
Hello al, I just make registration to post about it!

Well, I have an Acer Spire 5560G as well, A8 processor and 64 bits Win7. I install ubuntu 12.04 as well and had the same issue, when system reboot,  run Windows 7 without Ubuntu Grub. Im already reading about the boot repair option, and when finish show this.
The boot of your PC is in EFI mode, but no EFI partition detected. You may want to retry after creating a EFI partition |Fat32 >200Mo, start of the disk, boot flag, want to continue?

But nothing really happend after that, I going to try reinstalling ubuntu using Fat32, replacing EXT4.

Sorry for any language mistake, Im spanish speaker!

---

### Post by oldfred on 2012-05-06
No, do not attempt to use FAT and if Windows is not in UEFI mode, you will break Windows.

I think Boot_repair is seeing your system as UEFI enabled, but it also can boot in BIOS mode. If you have MBR partitioning you are booting in BIOS mode. Windows will only boot in UEFI mode with gpt partitioning and Windows would have created the efi partition.

Post this to confirm:
```

sudo fdisk -l
```

---

### Post by immerohnegott on 2012-05-13
From personal experience, I would recommend against using UEFI on this machine (I also have a 5560). For whatever reason, running in UEFI mode causes the system to hang at boot every other attempt. Also, there is no way in setup to force a BIOS mode boot. 

The simplest way to get a dual boot working is to do as follows:

Either create an Ubuntu live USB stick (using startup disk creator), and remove or rename the 'efi' directory at the root of the drive; or use an ISO editor (like ISO Master) to modify the Ubuntu Live CD image in the same way. This will make sure that Ubuntu runs in BIOS mode instead of UEFI - you can tell because UEFI mode just gives you a black and white Grub menu, while BIOS brings up the purple screen with Accessibility icons at the bottom. 

Boot that up and install like normal - keep the default MBR partition table and Windows installation, shrink the Windows partition if necessary and install Ubuntu. Grub will install to the MBR like normal and the system will boot it in BIOS mode.

---

### Post by YannBuntu on 2012-05-14
> **Spewed said:**
> ```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair-ubuntu
```

Since 12.04, there is no boot-repair-ubuntu package any more, the package to install is now simply boot-repair for all Ubuntu versions. See [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

