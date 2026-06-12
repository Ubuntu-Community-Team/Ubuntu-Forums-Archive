---
title: "Boot loader for UEFI?"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by renato3 on 2013-08-21
Hi, I've succesfully installed Ubuntu 13.04 in dual boot with Windows 8 while preserving my UEFI partition. The problem is that I have no boot loader. Ubuntu is my first option, so it's booted when my notebook is turned on, but I can't choose otherwise. Whenever I must go to Windows, I have to press F12 and manually select Windows to boot. Is there a way to install a boot loader without harming or erasing my UEFI partition? I have some important Dell tools in this partition that I can't afford to lose.

---

### Post by grahammechanical on 2013-08-21
I do not think that UEFI is a partition. It is a boot system in the same way that BIOS is a boot system. If Windows 8 is installed with the boot system in UEFI mode then Ubuntu must also install in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you get a boot menu? Or does the machine load into Ubuntu without any menu options? We always have a boot loader. We do not always see it. This is the case if Ubuntu is the only OS on the machine. Are Windows and Ubuntu on separate hard disks? Was the Windows hard disk connected when Ubuntu was installed? If not then the Ubuntu boot loader (Grub) does not know about the existence of Windows 8.

You could try loading into Ubuntu and opening a terminal and running.

```
sudo update-grub
```

That will search for all operating systems and the output from the command should indentify Windows 8 as one of the OS and with a bit of luck the next time you boot you might see Windows as a boot option.

Regards.

---

### Post by oldfred on 2013-08-21
Did you install Ubuntu in UEFI mode?
And grub2's os-prober has a bug and only creates BIOS entries to boot Windows but Windows will only boot in UEFI mode. Use Boot-Repair to fix, and just be sure to boot Boot-Repair in UEFI mode.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Some info in Post #3 on cleaning up menus, if desired.
[http://ubuntuforums.org/showthread.php?t=2085530](http://ubuntuforums.org/showthread.php?t=2085530)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by renato3 on 2013-09-02
Well, since everything is so bugged yet, I'll wait a little longer...

---

