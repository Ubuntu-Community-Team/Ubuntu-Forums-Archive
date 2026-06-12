---
title: "dual boot ubuntu 14.04 and pre installed windows 8 not working"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by psychok7 on 2014-04-29
so i installed Ubuntu 14.04 on a windows 8 pre-installed hp laptop.

the problem is when i boot the computer it takes me straight to windows and NO grub is shown.

i tried following this: [http://askubuntu.com/a/358524/59618](http://askubuntu.com/a/358524/59618) and used boot-repair which threw this error [http://paste.ubuntu.com/7295325/](http://paste.ubuntu.com/7295325/)

i also tried [http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot) with no luck

i am completely lost with this eufi stuff, can someone help me with an easy solution to have grub working on this laptop where i can choose Ubuntu or windows 8?

PS: i cant seem to get this working on my hp. i disabled fast startup and secure boot and ran bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi and still no Grub :(

---

### Post by oldfred on 2014-04-29
I have seen several work arounds. HP & Sony seem to be one's with modified UEFI to only boot Windows.

**Systems that only boot Windows from UEFI. Often Sony & HP**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Some install rEFInd which seems to be another workaround.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

