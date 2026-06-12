---
title: "Grub/EFI issues on new HP elitebook"
date: 2020-03-18
forum: Installation &amp; Upgrades
---

### Post by annadg on 2020-03-18
Hi,

Although I managed to easily install a Windows 10/Ubuntu 18.04 dual-boot on a Lenovo X1 Carbon a few weeks ago, I'm having a lot of trouble when trying to do the same with a (brand-new) HP Elitebook (Dragonfly). I have disabled fast startup in Windows, and in the "BIOS" (it's UEFI) I've disabled Legacy and Secure Boot.

The install itself seems to have gone fine, at least that is, there are no errors during the install. However, afterwards it'll boot directly into Windows, with no sign of Grub or Ubuntu to be found: an entry for Ubuntu doesn't show up when looking at efibootmgr / when looking at the boot menu when pressing Esc after booting. When I plug in a live usb however, it does say Ubuntu has been installed. I have tried different Ubuntu versions, but to no avail - I started off with 19.10, but then tried 18.04 since boot-repair threw errors in 19.10 (something to do with glade2script-python3). 

When running boot-repair for the 18.04 install, it says it has successfully repaired boot, but the problem persists and I still don't see Grub after booting nor an Ubuntu entry in the boot menu. The boot-repair output is the following: [http://paste.ubuntu.com/p/j8CpzswtrD/](http://paste.ubuntu.com/p/j8CpzswtrD/)

It says something about MBR, which I don't really understand, since the disk should be GPT.  But really, to me most of this is gibberish, so I would really appreciate some help to get Grub to boot!

---

### Post by oldfred on 2020-03-18
The report does not show all details on NVMe drives.

Do you have UEFI RAID or Intel RST on? That can confuse things as grub from a desktop installer will not install to RAID. And Intel RST just does not seem to work. Drives need to be in AHCI mode.
You also need Windows fast start up off. 

Grub uses efibootmgr to add UEFI entry, but many with HP said efibootmgr changes to boot order do not work. You typically have to use HP's UEFI to change boot order. But Ubuntu entry not yet shown in efibootmgr list.
Some also posted UEFI update solved some issues. And many SSD need firmware update.

Different model, but vendors often have similar issues across many models as same UEFI, but only options different.
HP Elitebook 840 G5 gpt issues - 
HP put a fail-safe gpt recovery into the UEFI Settings,  go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"
[https://ubuntuforums.org/showthread.php?t=2436271](https://ubuntuforums.org/showthread.php?t=2436271)

HP Dragonfly Elite G1 19.10 works, 18.04, no WiFi
[https://arstechnica.com/gadgets/2020/01/linux-on-laptops-ubuntu-19-10-on-the-hp-dragonfly-elite-g1/](https://arstechnica.com/gadgets/2020/01/linux-on-laptops-ubuntu-19-10-on-the-hp-dragonfly-elite-g1/)


If willing to live with potential issues as not yet released, you can experiment with 20.04. I am using it now and have reported a couple of bugs. Printer sometimes works. I actually unplugged it from USB port and WiFi works to print??

---

### Post by annadg on 2020-03-18
Thanks for your quick reply. I updated the UEFI but that doesn't change much, the GPT recovery option is greyed out so also not relevant here.

Your point about RAID is a good one. I was under the impression I had just one disk (512GB), but I have Intel Optane with a smaller second disk (32GB), which yes will be in RAID and therefore explains the installation issues. I've not seen this type of setup before - do you know what the consequences will be if I remove the Intel Optane? Won't my Windows distro break if I get rid of the RAID?

---

### Post by yancek on 2020-03-18
If you look at boot repair beginning at line 384, you have the efi boot menu and you have no ubuntu entry so you will need to reinstall Grub EFI files.
I'm also using an HP and have never been able to change efi setting w/efibootmgr but it is pretty simple to access the BIOS w/Esc, F10, System Configuration, UEFI Boot options and OS Boot Manager should show different options.  


Lines 300-302 show the windows system is hibernated.

---

### Post by oldfred on 2020-03-18
Have not seen many newer systems with the separate small SSD.  That was used a lot when Windows required faster boot as Windows does not boot quickly. They used small SSD only as boot cache but main drive was HDD.
Some erased or stopped the use of the boot cache & used SSD just for Ubuntu. Some with larger SSD and only 8GB of RAM found only 8GB of SSD was uses and installed / (root) into the remaining space.

NVMe drives are even faster, so not sure why you see a smaller cache drive.

Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

---

### Post by annadg on 2020-03-19
Yes, I read about issues with HP and efibootmgr, and I haven't done anything with it beyond looking at the output. With all attempts so far, in the BIOS I can only see the Windows boot manager as an option. I also looked at the "boot from file" but there's no Ubuntu EFI file there either. I'll try again to reinstall the EFI files myself - Intel Optane may be the culprit however.

---

### Post by annadg on 2020-03-19
Thanks, you're right the laptop should be more than fast enough without the Intel Optane. I'll try to get rid of the RAID and reinstall. Update: disabling Intel Optane + reinstalling Ubuntu 19.04 did the trick.

---

