---
title: "VAIO - UEFI - Dualboot fail with 14.04"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by f.sardis on 2014-06-12
So the laptop is an SVZ1311C5E with UEFI turned on. It has two SSD set to GPT from Windows 8.1
Windows is installed on the first SSD and I want to install 14.04 x64 on the second SSD with the boot manager on the Windows SSD so I can select what to boot from GRUB.

I am using an external USB DVD drive because the laptop doesn't have one. Ubuntu displays the message Could not open "\EFI\BOOT\fallback.efi": 14
and then proceeds to the usual menu for running a demo or installing. I choose to install and when it comes to partitioning, it tells me that no other OS was detected and that it plans to wipe the disk and install.
Problem 1) which disk of the two is it planning to wipe? I am assuming it wants to wipe the first SSD which has Windows so no thanks I will partition manually. Which takes us to the second problem.
Problem 2) if i partition manually and since it is completely oblivious to the existence of Windows on the first SSD, I am afraid that if I put GRUB on the first SSD, it will wipe Windows boot record and I will lose Windows anyway.

So what is the recommended solution in this case? I get the impression that ubuntu detects the system is running UEFI but fails to find the UEFI boot on the DVD so it falls back to Legacy which is what makes it blind to the Windows installation. It sees the UEFI partitions on the first disk but it doesn't see the OS installed. I checked the DVD and the .img file for problems and they are both clean. Secure boot is disabled as reported by Windows and there is no option in the BIOS to change it anyway.

Thanks in advance for any ideas.

---

### Post by oldfred on 2014-06-12
Sony's are not particularly friendly to dual booting.

Better to plan to install grub to sdb or same drive as Ubuntu. You can have an efi partition on every drive, UEFI will include all drives, and grub can easily chain load to the Windows in the other drive. The issue is that Sony will not let that work like it should and work arounds are required.

Even if a second drive be sure to have Window's fast boot or always on hibernation off. 
Do you also have Intel SRT? Or are SSD's configured as RAID

Lots of links in the link in my signature. Those links all have screen shots showing install.
You will need to use Something Else as that is only option that lets you choose where to install grub boot loader and you want the efi partition on sdb or Ubuntu drive.

 Could not open "\EFI\BOOT\fallback.efi"
[https://bugs.launchpad.net/ubuntu/+bug/1241824](https://bugs.launchpad.net/ubuntu/+bug/1241824)
Some just add another copy of grub or shim.

Some other threads on Sony, your UEFI may be similar.
      
  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)

 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )
Dual booting with Windows 8 on a Sony Vaio 
[http://ubuntuforums.org/showthread.php?t=2153589](http://ubuntuforums.org/showthread.php?t=2153589)
Sony Vaio & Ubuntu 13.10
 [http://www.slideshare.net/slideshow/embed_code/27418512](http://www.slideshare.net/slideshow/embed_code/27418512)
Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)
Sony Vaio Pro 13 initrd issues - turn off UUID and libata.force=noncq splash parameter needed
[http://ubuntuforums.org/showthread.php?t=2189052](http://ubuntuforums.org/showthread.php?t=2189052)

---

