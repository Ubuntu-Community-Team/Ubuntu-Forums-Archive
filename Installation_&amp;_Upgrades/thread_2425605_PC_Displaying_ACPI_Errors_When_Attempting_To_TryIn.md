---
title: "PC Displaying ACPI Errors When Attempting To Try/Install Ubuntu 18.04 LTS"
date: 2019-08-27
forum: Installation &amp; Upgrades
---

### Post by shadshd on 2019-08-27
[Solved]
Pressing E on the boot menu allowed me to type acpi=off into the boot options, which let me boot into the USB. But now I get a &#8220;grub cannot be installed to /target/&#8220;error. Progress, though.


I've been trying to dualboot Windows 10 1903 and Ubuntu 18.04 LTS on my laptop, but I can't even get past the "*Try Ubuntu" menu. The screen goes black for about 30 seconds then begins rapidly displaying the errors in the included image. I've tried installing LinuxLite, Manjaro, CentOS, and ArchLinux, and I receive the same screen and errors. I have also tried booting with UEFI, UEFI with CSM, and Legacy, as well as creating the install disk as both DD image and ISO image (Using Rufus 3.5 for making the boot drive.).

PC Info:
MSI GS63 Stealth 8RE-010US
i7-8750h
16GB DDR4
GTX 1060
Intel 660p 512GB boot drive w/Windows 10 1903
Samsung 860 EVO 1TB storage drive

Any help would be appreciated, as I'm trying to migrate to Linux semi-permanently and dualbooting my PC would be a huge help. 

[ATTACH=CONFIG]283881[/ATTACH]

---

### Post by ubfan1 on 2019-08-27
Stick with UEFI, forget legacy/csm.  You can edit the grub menu item "try ubuntu" (type E, edit, then boot with f10 or ctrl-X, instructions at bottom of screen). With Nvidia hardware, you need the nomodeset keyword added at the end of the line starting with "linux" -- add it at the "quiet splash" words.  Do this until you have added the proprietary Nvidia drivers.  Another keyword to try is acpi=off.  If that allows you to boot, look at  [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) under the "Common Kernel Options" near the bottom and see more acpi options of a finer granularity which may work instead of acpi=off.

---

### Post by oldfred on 2019-08-28
Issues are often common by brand, bigger difference if AMD or Intel.
Have you updated UEFI from MSI?

       MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)

---

### Post by electro-mag on 2019-08-29
I had the same problem and it took me multiple attempts to have it installed. 
1- make sure from from 'system information' what type of BIOS you have. I'm pretty sure it's UEFI, but check anyways. boot type must match. You might be able to install Legacy on UEFI BIOS and vise versa, but you won't be able to boot your installation unless you do it via power shell in windows. It's pain in the butt.
2- when the grub screen appear, click 'e' to edit (I'm just throwing it out there in case you didn't know) and type right between 'ro' and 'quiet splash'  either:
    a- acpi=off. this will disable the power saving function, or:
    b- noapic, this will disable the main interrupt controller, or:
    c- all of the above.

[IMG]https://wiki.ubuntu.com/Kernel/KernelBootParameters?action=AttachFile&do=get&target=grub2_menu_editing.png[/IMG]

Option 'b' and 'c' worked for me. even with option b, it still kept freezing up, but I have a dell so that's might be the problem!! they are notorious heat generators.

---

### Post by Autodave on 2019-08-29
Have you disabled *fast boot* in the BIOS?

---

### Post by shadshd on 2019-08-29
Edit: By &#8220;this one&#8221;, I mean typing acpi=off in the grub menu.

This one worked for me. I was finally able to boot into the USB using your tip. However now when I try installing Ubuntu, I get the error:

&#8221;The 'grub-efi-amd64-signed' package failed to install into /target/. Without the grub boot loader, the installed system will not boot&#8221;.

I&#8217;ve searched for a solution to this, but nothing has worked so far. Tried manual partitioning, automatic installation, but nothing yet. I have no clue what&#8217;s the problem at this point. Windows is definitely GPT and the boot manager is UEFI with the &#8220;boot&#8221; flag.

---

### Post by oldfred on 2019-08-29
If installing in UEFI mode /target will be the first EFI partition on the system. Usually sda or first NVMe drive.

Ubiquity will not let you choose where to install grub in UEFI boot mode. The choice does work with BIOS mode & Something Else.

If you have an ESP, Boot-Repair will let you install grub to your existing ESP. The issue is not grub install but Ubiquity's mount of ESP.

       Posted work around to manually unmount & mount correct ESP during install
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

