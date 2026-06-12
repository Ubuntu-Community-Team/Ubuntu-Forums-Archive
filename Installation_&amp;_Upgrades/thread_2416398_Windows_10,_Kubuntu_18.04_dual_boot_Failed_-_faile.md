---
title: "Windows 10, Kubuntu 18.04 dual boot Failed - failed to open grubx64.efi"
date: 2019-04-09
forum: Installation &amp; Upgrades
---

### Post by sikander3786 on 2019-04-09
Hello everyone, after a short break... :)

Hope all my friends are still around and doing finer than ever.

Need some help as my main laptop is refusing to boot after I installed Kubuntu 18.04 for dual-boot.

Info log here:

[http://paste.ubuntu.com/p/3R94DW7Hbf/](http://paste.ubuntu.com/p/3R94DW7Hbf/)

I've tried multiple things and feel like I've broken it further.

Thanks for your time and efforts,
Sikander

---

### Post by oldfred on 2019-04-09
Windows only boots in UEFI mode from gpt.
Windows only boots in BIOS boot mode from MBR.

You now show two drives using MBR(msdos), but sdb has two ESP partitions on MBR drive. You only can have one (active) per drive. You may be able to switch boot flag to make other active, but not really recommended. And Windows needs gpt, Ubuntu should have gpt partitioning as that is recommended by UEFI.
One ESP shows Windows UEFI boot files and other ESP shows Ubuntu UEFI boot files.

Did you run something to convert drive from gpt to MBR?
And then install the generic BIOS boot loader syslinux into MBR which is only for BIOS/MBR boots.

Only if you have good backups, I would suggest converting drive back to gpt.
You may need to use Windows repair flash drive to reinstall/update boot loaders and will have to reinstall grub boot loader to move Ubuntu/grub boot files from second FAT32 to first one. And before re-installing grub, backup & then remove sdb5, so grub only sees sdb1 as ESP - efi system partition. You may need to move boot flag or esp setting in gparted to sdb1, so seen as ESP.

So if you have good backups, a Windows repair flash drive & Ubuntu live installer to use to reinstall grub.
       Converting to or from GPT
[URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]http://www.rodsbooks.com/gdisk/mbr2gpt.html
      [/URL]
 Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252) 
    [URL="http://www.rodsbooks.com/gdisk/mbr2gpt.html"]
[/URL]

---

### Post by sikander3786 on 2019-04-09
Thanks for the quick reply. I guess a re-install would be the best option then as I don't have any important data and I was just testing around.

But why didn't Grub2 detect Windows 10 in the first place? After installation of Kubuntu, it started booting into Kubuntu but was unable to list Windows 10. I tried "update-grub" command and it didn't list Windows 10. Then I repaired Windows 10 bootup from repair media and then tried repairing Grub2 from boot-repair live usb. That's when all this messed up.

How should I proceed for a dual-boot now, clean installs of both OS, UEFI or Legacy? A few hints would be appreciated.

Thanks again.

---

### Post by oldfred on 2019-04-09
New Windows systems have Product key in UEFI. So if system came with Windows installed in UEFI mode, you have a product key.

Microsoft has required vendors to install in UEFI mode, since Windows 8 in 2012, but users still can install in BIOS boot mode. 
For both Windows & Ubuntu how you boot install media, UEFI or BIOS, is then how it installs. So be sure to boot both installers in same boot mode.

Ubuntu's grub really only wants to install to ESP on first drive, usually sda.  Often easier to disconnect sda, if installing to sdb. Or move sdb drive to lower SATA port so it becomes sda. Windows & Ubuntu will share one ESP.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  & 
[https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi)

More info on UEFI install in link in my signature below.

---

### Post by sikander3786 on 2019-04-10
Eventually I ended up repairing the setup:

1. Disconnect sda
2. Convert to GPT as you linked here:
    [https://ubuntuforums.org/showthread.php?t=1454252&p=9123670#post9123670](https://ubuntuforums.org/showthread.php?t=1454252&p=9123670#post9123670)
3. Repair Windows 10 boot:
    [https://www.partitionwizard.com/clone-disk/bootrec-fixboot-access-is-denied.html](https://www.partitionwizard.com/clone-disk/bootrec-fixboot-access-is-denied.html)
4. Set sda1 as EFI/active/boot partition and delete the other EFI partition
5. Run [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

Thanks to this amazing community and specially [oldfred]("https://ubuntuforums.org/member.php?u=852711").

Sikander.

---

