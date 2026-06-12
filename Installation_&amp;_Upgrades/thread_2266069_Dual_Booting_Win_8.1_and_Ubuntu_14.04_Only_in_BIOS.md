---
title: "Dual Booting Win 8.1 and Ubuntu 14.04 Only in BIOS"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by Mark_Stiverson on 2015-02-19
I have read other threads here but perhaps those responses were beyond my current understanding, so I'll ask if there is a reasonable fix for my dual booting situation.  I have a Samsung pc that was running on windows 8.1 64bit.  I decided to try Ubuntu 14.04.  I downloaded the iso and ran the installation program.  It asked to segregate a portion of the partition and I did that, but reduced it some.  I rebooted the pc and ubuntu was working great...except I can't seem to get the wireless connection set yet.

However when I rebooted the pc and get the option to boot in both, only the Ubuntu boots.  I get an error message when trying to boot windows.

I didn't change anything on the pc bios before install.  After the install, when I go into the bios, I can choose to boot either windows or ubuntu.  Is there a way to get the choice during the "normal" booting process?  Please be detailed as possible if you need futher info or have a solution.

Thanks

---

### Post by oldfred on 2015-02-19
Do both boot ok when booting from UEFI boot menu?

You may have installed Ubuntu in BIOS mode and have Windows in UEFI boot mode?

May be best to see details, you can run this from your working Ubuntu or a live installer:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Mark_Stiverson on 2015-02-19
> **oldfred said:**
> Do both boot ok when booting from UEFI boot menu? 

[U][B]Pressing f10 at start up, in the boot Menu, I can select 1. Windows Boot Manager 2. ubuntu 3. HDD 4. CD 5.ubuntu  And yes, windows will boot if selected as well as ubuntu will boot if selected.

Pressing f2 at start up, in the bios boot, the PXE OPROM was apparently disabled when I installed ubuntu (or at least that is the way it was after install)
[/B][/U]


You may have installed Ubuntu in BIOS mode and have Windows in UEFI boot mode?

_**Not sure what this means, but it doesn't sound compatible.  Is there a work around, or how would I uninstall ubuntu and start all over?**_

May be best to see details, you can run this from your working Ubuntu or a live installer:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

_**uh, I'll have to read up on this.**_

**Thanks for the quick response.**

---

### Post by oldfred on 2015-02-19
Do not reinstall Ubuntu unless you use Something Else. It may erase entire drive even if it says replacing Ubuntu.
See link in my signature.

If installed in BIOS mode, Boot-Repairs advanced mode can walk you thru the uninstall of grub-pc (BIOS) and install of grub-efi-amd64 (UEFI). But you can also do that without Boot-Repair.

Be sure to always boot in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark_Stiverson on 2015-02-19
> **oldfred said:**
> Do not reinstall Ubuntu unless you use Something Else. It may erase entire drive even if it says replacing Ubuntu.
See link in my signature.

If installed in BIOS mode, Boot-Repairs advanced mode can walk you thru the uninstall of grub-pc (BIOS) and install of grub-efi-amd64 (UEFI). But you can also do that without Boot-Repair.

Be sure to always boot in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


Much of it was greek to except when I got to this area of the post.  Was this what you were referring to?

**REPAIRING THE BOOT**
  After finishing the installation, if you happen to have Windows 8  disabled from booting and it only boots to Ubuntu, do not worry. In  Ubuntu after it boots, [install Boot-Repair in Ubuntu]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") by opening a Terminal and typing the following:
  sudo add-apt-repository ppa:yannubuntu/boot-repair  
sudo apt-get update
sudo apt-get install boot-repair
boot-repair 
  [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")  will mention that we have some GRUB error, that we have an EFI system  and that Ubuntu rocks. Since Ubuntu rocks (It does not work if Ubuntu  does not rock! ^^), just click on **Apply** so boot repair fixes everything. Now reboot and you should see Windows 8 and Ubuntu side by side.

---

