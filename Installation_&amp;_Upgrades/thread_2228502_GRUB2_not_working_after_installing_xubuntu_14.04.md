---
title: "GRUB2 not working after installing xubuntu 14.04"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by hector8 on 2014-06-07
Hi everbody,

          I have a vaio laptop and it used to have installed windows 8 and Xubuntu 13.04 in dual boot, everything was working fine.
  I decided to update my version of xubuntu 14.04 LTS mainly because  the support for 13.04 is finished and LTS version have 3 years of  support. What I did was to format the partition where xubuntu 13.04 was  installed and install 14.04 in that formated partition. When I restarted  my computer willing to start using my new system I got the following  message:

[INDENT]   error: symbol 'grub_term_highlight_color' not found


 [/INDENT]
and I was not able to enter any OS. 
  I tried boot-repair from live USB  more than two times and it did not fix the problem. 
  I tried to enter to my computer using super GRUB2 disk, however it  does not apperar to work with UEFI active (besides super grub2 disk says  it can) I only get the message "no operating system found". 
  If I boot super grub2  disk with UEFI disabled, super grub2 disk can  not detect any OS,I also tried Rescatux distro, however, as of super  grub2 disk, rescatux cannot enter when UEFI is active.
  I tried boot-repair with the option of "restore EFI backups", after  that I was able to boot on windows, but no grub menu appeared. I ran  boot-repair again with no improving results
  Here is the last Bootinfo report I got:

[INDENT][http://paste2.org/y5EEHgAV](http://paste2.org/y5EEHgAV)
[/INDENT]

 Do you have any idea of what is happening?
  I really appreciate your help,
  Best regards,

---

### Post by oldfred on 2014-06-08
Did you remove Windows boot entry from UEFI, it is not shown even though your efi partiiton has the Microsoft efi folder.

>  BootOrder: 0001,2001
Boot0000* EFI USB Device (USB Flash Disk)
Boot0004* EFI USB Device (USB Flash Disk)
Boot0001* ubuntu.


It may be this and Boot-Repair's total uninstall and reinstall of grub from a chroot may work. Or while chroot run the dpkg commands. But Sony's typically do not directly boot Ubuntu anyway.
 Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.


Sony's all seem to have issues. They only want to boot Windows.
Most users seem to use one of the rename functions. I now do not prefer the rename of bootmgfw.efi that Boot-Repair does as Windows updates will overwrite that.

       **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
**A:** Manually rename files either bootmfg.efi and/or bootx64.efi : 
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair rename Windows bootmfg.efi. But cannot boot Windows from UEFI only grub 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

      
  Sony Vaio Pro 13 - To get into  UEFI press this "Assist" button BEFORE starting
[http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio](http://askubuntu.com/questions/458413/how-to-fix-dual-booting-windows-8-and-ubuntu-14-04-on-a-sony-vaio)
Issues on rename
[https://bugs.launchpad.net/boot-repair/+bug/1315490](https://bugs.launchpad.net/boot-repair/+bug/1315490)
With encryption but you do not have to
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)
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

