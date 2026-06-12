---
title: "EFI grub entries fail to boot Win8"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by rossman47 on 2012-12-17
I recently bought new XPS 13 with Win8 UEFI. Deleted all partitions (there were many), performed a clean install of Win8 and created a NTFS partition with the Win8 installer. Win8 installer also created a "SYSTEM RESERVED" NTFS partition of 350 MB (that appeared to have the boot flag set).

Followed the instructions [here]("https://help.ubuntu.com/community/UEFI") to install Ubuntu alongside of Win8 in an ext4 partition using the Ubuntu 12.10 Secure Remix. After install of Ubuntu, reboot went directly into Win8 and no grub menu appeared.

So I booted with USB stick again, created a 250 MB FAT32 EFI boot parition, ran Boot-Repair, and selected to have grub install into the new boot partition.  For Boot-Repair results, please see: [http://paste.ubuntu.com/1444728/](http://paste.ubuntu.com/1444728/)

With the above changed I get a grub menu, and I can boot into Ubuntu, but any attempts to load Win8 result in "Invalid EFI file" and something about "drivemap".

So after reading through a multitude of forum posts, I ran the following command:

```

sudo grub-probe --target=fs_uuid /boot/efi/efi/Microsoft/Boot/bootmgfw.efi
6B17-40A0

```Then added the following to /etc/grub.d/40_custom:

```
menuentry "Windows x86_64 UEFI-GPT" {
    search --fs-uuid --no-floppy --set=root 6B17-40A0
    chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi.grb
}
```When I boot with this option, I get a blank screen for a moment, then back to the grub screen.

For some reason, when I attempt to use the UEFI boot menu (F12 on the XPS), I can't load either Ubuntu or Windows. But if I choose "Local HDD" from the menu, I can load grub then Ubuntu.

SecureBoot is not enabled.

Please let me know if you have any suggestions. I've tried just about everything I can think of. Thanks!

---

### Post by oldfred on 2012-12-17
Why did you reinstall Windows?

When you reinstalled Windows you converted back to BIOS/MBR, but then tried to install Ubuntu in UEFI. Both have to be installed in the same mode. Not sure if it is even possible to have UEFI boot with MBR partitions as efi partition is not really directly loaded in BIOS/MBR like UEFI does.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
    
        Windows will only boot from gpt partitioned drives with UEFI.
Windows x64 Installer determines which firmware has been used for booting the ISO/DVD/USB. If BIOS is used, only MBR is supported. If UEFI is used then only GPT is supported. Not vice-versa.

 Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Unless you want to totally reinstall Windows again in UEFI mode it may just be easier to reinstall Ubuntu in BIOS mode. You have to boot Ubuntu installer in same mode as you want to install. Or boot in BIOS mode to install in BIOS.

---

### Post by rossman47 on 2012-12-17
> **oldfred said:**
> Why did you reinstall Windows?
I reinstalled via a Win8 DVD because there were too many partitions (I didn't know which ones I could safely delete), and because neither the Ubuntu 12.10 installer nor GParted recognized the factory Win8 install. I assumed it would be easier to just do a clean install of Win8 then install Ubuntu. Win8 did work after the clean install. It stopped working after I installed Ubuntu and got grub working in EFI mode.

> **oldfred said:**
> Unless you want to totally reinstall Windows again in UEFI mode it may just be easier to reinstall Ubuntu in BIOS mode. You have to boot Ubuntu installer in same mode as you want to install. Or boot in BIOS mode to install in BIOS.
I really don't care if I'm using UEFI or not. Is there a way I can convert my existing Ubuntu install to BIOS mode? Previously, grub would not work until I created the /boot/EFI FAT32 partition and told Boot-Repair to put grub there. My computer doesn't boot when I remove /boot/EFI and tell Boot-Repair to put grub on /dev/sda.

Thanks for your help!

---

### Post by YannBuntu on 2012-12-17
If Windows has been reinstalled in Legacy mode as Oldfred guessed, then there is no need to reinstall Ubuntu, you can just convert Ubuntu into Legacy mode as described here: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode)

This is what i would try first.

---

### Post by rossman47 on 2012-12-17
> **YannBuntu said:**
> If Windows has been reinstalled in Legacy mode as Oldfred guessed, then there is no need to reinstall Ubuntu, you can just convert Ubuntu into Legacy mode as described here: [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode)

So I followed the instructions to convert to legacy mode, but GParted didn't list the "bios_grub" flag as an option, so I figured I would try gdisk, which reported the following:

```

***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************


```I proceeded with fixing the partitions to GPT format and rebooted into Ubuntu Secure Remix via USB. I ran GParted, set the flag on the unformatted 1 MB partition to "bios_grub", then ran Boot-Repair and rebooted. No grub. Just a black screen with a flashing cursor in the upper-left corner. Output from Boot-Repair is here: [http://paste.ubuntu.com/1446707/](http://paste.ubuntu.com/1446707/)

I then rebooted via USB and deleted the unformatted partition and created a 250 MB FAT 32 partition with boot flag set, and re-ran Boot-Repair, but the option to put grub into the EFI boot partition no longer exists. I'm not sure what to do now. I can't boot into any operating system now.

---

### Post by oldfred on 2012-12-17
Windows only boots from gpt with UEFI. So when you installed in BIOS mode it converted drive to MBR. But Windows does not recognize the backup gpt partition table. Linux tools see the backup gpt and primary MBR and get confused. You were converting to BIOS/MBR for both systems, so I do not know why you let it convert buck to gpt. Windows in MBR will not work with gpt. Not even sure you can convert to UEFI, although I think I saw something somewhere, but it looked easier to reinstall.

Now I think you have to start over. I would erase all partitions. The decide if you want MBR or gpt and then install both systems in BIOS/MBR or UEFI/gpt.

Related to gdisk is fixparts (same author) which is used to remove the backup gpt partition table if found and you want MBR.

I always partition in advance but use gparted. But you do have to have some idea of partitions & sizes you need. You only need a bios_grub partition with gpt and Ubuntu in BIOS mode. That is what I have, but you then cannot install Windows on the same drive as it only boots from gpt in UEFI.

---

### Post by rossman47 on 2012-12-18
> ou were converting to BIOS/MBR for both systems, so I do not know why you let it convert buck to gpt.
I did it because (1) there was no bios_grub flag available in GParted, and (2) because it's what gdisk told me to do, and now I have a bios_grub flag in GParted, so apparently something was off with my GPT/MBR.

I ran Boot-Repair again with the purge option, and it told me to setup the unformatted partition with the bios_grub flag. So I did that and now I get a grub menu, and I can boot into Ubuntu again. Yay.

When I try to boot Win8, it complains and tells me to run the windows startup repair from the install disk (this is progress at least). I tried that, but it didn't work. I then tried re-installing Win8, but it now complains that it won't install to a GPT disk. I did some searching, and apparently it's possible to boot the Win8 install media into UEFI mode to install on a GPT disk, but I couldn't make it work. No matter what I tried, the Win8 install media wouldn't show up as a UEFI boot option.

So Ubuntu is working in BIOS mode supposedly, even though I have a GPT disk? Does anyone know how I would go about converting back to MBR from GPT?

---

### Post by YannBuntu on 2012-12-18
> **rossman47 said:**
> Output from Boot-Repair is here: [http://paste.ubuntu.com/1446707/](http://paste.ubuntu.com/1446707/)

Your BIOS-Boot partition is incorrect: it is now FAT32, but it should be 'unformatted'.

That's why GRUB didn't install correctly.

---

### Post by rossman47 on 2012-12-18
I used gdisk to convert the GPT to MBR, reinstalled Win8, and re-ran Boot-Repair (did not re-install Ubuntu), and now I can boot into both Win8 and Ubuntu. Thanks guys for helping me through this!

---

### Post by YannBuntu on 2012-12-18
Good job :)
For our information, please could you indicate the last URL provided by Boot-Repair?
(if you don't remember, please click the "Create BootInfo" button and tell the new URL.)

---

### Post by rossman47 on 2012-12-18
> **YannBuntu said:**
> Good job :)
For our information, please could you indicate the last URL provided by Boot-Repair?
(if you don't remember, please click the "Create BootInfo" button and tell the new URL.)
No problem, the link is below. Let me know if you see anything that I should change. I got the error "could not connect to plymouth" when attempting to boot into Ubuntu today, but I cycled power and then it booted OK, so I'm not sure what's going on, but I'll do some research and open another thread if it continues to be a problem. Thanks again for your help!

[http://paste.ubuntu.com/1449247/](http://paste.ubuntu.com/1449247/)

---

