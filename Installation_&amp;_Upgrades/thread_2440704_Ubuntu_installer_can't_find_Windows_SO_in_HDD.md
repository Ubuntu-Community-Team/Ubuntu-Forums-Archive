---
title: "Ubuntu installer can't find Windows SO in HDD"
date: 2020-04-14
forum: Installation &amp; Upgrades
---

### Post by jordibcn1974 on 2020-04-14
Hi, I'm pretty noob in linux, so sorry in advance ;)

I'm trying to install Ubuntu on a laptop with Windows 10, in dual boot mode, but the ubuntu installer keeps telling me that there is no OS installed, so I can't install Ubuntu properly.

I've googled my problem, and the "usual suspects" are ruled out:
-My HDD is fine, "chkdsk /v" is already done
-HDD in BIOS is set on "legacy" not in "UEFI" mode (Windows 10 instalation had to be done in legacy mode because pen drive wasn't detected in UEFI mode)
-"Secure boot" is not active

I've also tried to follow a tutorial where even Windows was not detected, you can install Ubuntu with the "something else" option and making 3 manual partitions in the free space of the HDD, but after creating "/" and "swap" partitions without problem, the unused space suddenly changed to "useless", and I had no option to create the "/home" partition.

This is how Windows' partitions look in Ubuntu installer (Spanish Windows):
[IMG]https://images2.imagebam.com/a9/41/33/1801f31340326146.png[/IMG]

And this is the info of Windows partitions:
[IMG]https://images2.imagebam.com/9c/c5/74/c962b61340326156.png[/IMG]


At this point, I have no idea what to do, and I'm asking if someone can give me a hand [-o<
Thanks a lot for your help :)

---

### Post by CelticWarrior on 2020-04-14
Windows in BIOS/Legacy mode requires MBR drives and MBR drives are limited to 4 primary partition (that's one of the advantages of UEFI for which Windows requires GTP drives and those have no such limitation).

You don't need a swap partition because since a few releases ago Ubuntu uses swapfile. A separated /home is also optional.

**No, you should not install Ubuntu if the installer doesn't detect Windows.** Because you forced Windows in Legacy, if you install Ubuntu now, **Windows will not boot.**

First of all boot Windows and disable Fast Startup. Then and only then try to install Ubuntu. Windows should now be detected. If not, again, do NOT attempt the installation.

---

### Post by Impavidus on 2020-04-14
You missed the most obvious usual suspect: disable Fast Startup. Keep in mind that Windows may automatically switch it back on, which will make Windows unbootable on a legacy system. I think you may need a repair disk to fix it if that happens. One reason to use UEFI when dual booting with Windows 8 or higher.

You can have more than 4 partitions on an mbr drive. With less than 4 primary partitions, you can still make as many logical partitions as you want, as long as your logical partitions are adjacent.

---

### Post by jordibcn1974 on 2020-04-14
Thanks for the info @CelticWarrior and @impavidus.

I have no idea why I couldn't install Windows 10 using EFI, but it seems everything will be easier if UEFI is on, so I'm gonna google it and start from scratch with Windows installation in UEFI mode. And after that I'll try again to install ubuntu.

Thanks =d>

edit: Ok, Now I know I need how to create the bootable usb iso in order to use UEFI. ;)

---

### Post by jordibcn1974 on 2020-04-15
I'm stuck again :(

I've installed Windows 10 from scratch, in UEFI mode, disabled secure boot in BIOS and fast boot on Windows. I've made bootable ubuntu pen drive, using Rufus and slecting UEFI mode, and when I boot from usb I get "minimal bash-like line editing is supported..." error.
I've googled it and it seems it's a problem you can get when ubuntu is installed, but I haven't been able to install it.

Any ideas? And just in case, BIOS should remain in UEFI mode not legacy, right? And Rufus must create the bootable iso in UEFI mode already, right?

Thanks :D

Edit: Solved. I had to use the DD option in Rufus when creating the bootable usb

---

### Post by Impavidus on 2020-04-15
Everything should be UEFI mode.

The error you get comes from grub, the boot loader. Something must have gone wrong when you created the live disk. There are several live usb creators, maybe you'll have more success with a different tool. I've never made a live usb on Windows.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yancek on 2020-04-15
You might also verify the download of the Ubuntu iso as it is possible for it to be corrupted in the process of downloading.  md5sum and sha256 sums and the process are explained on the download site.

---

### Post by jordibcn1974 on 2020-04-15
> **Impavidus said:**
> Everything should be UEFI mode.

The error you get comes from grub, the boot loader. Something must have gone wrong when you created the live disk. There are several live usb creators, maybe you'll have more success with a different tool. I've never made a live usb on Windows.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
I've been able to properly create the bootusb, and I'm installing ubuntu atm.

Thanks a lot for the help &#55357;&#56842;

edit: Thanks to your tips, finally I have boot SO installed and everything is working fine.

---

