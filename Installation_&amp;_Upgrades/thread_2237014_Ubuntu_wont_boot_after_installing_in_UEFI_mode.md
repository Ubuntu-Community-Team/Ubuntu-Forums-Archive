---
title: "Ubuntu wont boot after installing in UEFI mode"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by tagy011 on 2014-07-30
Ok , heres what i did : This is blank HDD never had win. I converted the drive to gpt , created partions : FAT32 mount /boot/efi size 512mb , Swap 16gb , rest is home ext4 . installation goes trough smooth with no error messages , Restart and it says no OS found . Bios is in EUFI only mode . 
is there something im missing and / or doing wrong ? Ubuntu wont boot in legacy mode either . Installing it with drive converted back to masdos and installing it under legacy , it boots fine . 
I have bootable  usb flash drive with ISO ubuntu 64 amd image . Could it be that grub on that image is not compatible with EFI ?

---

### Post by oldfred on 2014-07-30
You also can and I recommend if not installing Windows to use gpt anyway as Ubuntu boots from gpt with either BIOS or UEFI.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

[/URL]
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[URL="http://ubuntuforums.org/showthread.php?t=2021534"]http://ubuntuforums.org/showthread.php?t=2021534


[/URL]

[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by tagy011 on 2014-08-01
I did all that , installation goes smooth with no error messages . After restarting , Ubuntu wont boot with error message no OS found . I checked bios and it is set to UEFI only . I tried converting the drive back to msdos and installing in legacy and it boots fine . For some reason and i cant figure out why , it wont boot with drive in gpt , installation goes smooth tho ..This is a fairly new Lenovo desktop about 5 months old , bios should be able to recognize gpt format .

---

### Post by oldfred on 2014-08-01
What model Lenovo?
I thought Lenovo would boot Ubuntu, but HP & Sony modify UEFI to only boot the UEFI entry that is Windows. So work arounds are required.

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Another lenovo solution copy grubx64.efi to bootx64.efi & boot hard drive not anyother entry
[http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470](http://ubuntuforums.org/showthread.php?t=2185869&p=12884470#post12884470)

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

      Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)
Installing GNU/Linux on a 2014 Lenovo Thinkpad X1 Carbon UEFI/BIOS suspend to RAM issue
[http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon](http://mako.cc/copyrighteous/installing-gnulinux-on-an-2014-lenovo-thinkpad-x1-carbon)
Lenovo IDEAPAD Y410P -  In My BIOS I set Boot Legacy Support But i set Boot UEFI First. 
[http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503](http://askubuntu.com/questions/455503/dual-boot-windows-8-and-ubuntu-problem-uefi?noredirect=1#comment599330_455503)

---

### Post by tagy011 on 2014-08-07
Its Lenovo H355 desktop (lenovo idea product) . Ubuntu boots just fine under legacy and drive formatted in MSDOS , however Ubuntu wont boot if its installed with drive converted to gpt in legacy or UEFI . I tried installing WIN 8.1 under UEFI and  everything went OK . I came to conclusion that my Lenovo firmware (BIOS/UEFI) doesnt recognize gpt drive format and thats why im getting "no OS found" error when is Ubuntu installed in legacy or Uefi with gpt format .

---

### Post by oldfred on 2014-08-07
gpt is not the issue.
Perhaps Microsoft now has Lenovo converted to only boot Windows.
No OS means the UEFI is looking for Windows and cannot find it.

Usually one of these works, although based on reports certain systems seem to work with one alternative that others do not. Often using the rename of bootx64.efi and boot hard drive is allowed or using rEFInd works. Some use efibootmgr to reorder or rename entries directly and that works, but with others Windows still reorders the UEFI entries.

 [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi (manual version of B: below) and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

