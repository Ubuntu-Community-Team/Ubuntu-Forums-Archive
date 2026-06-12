---
title: "Windows 8 / Ubuntu Dual-Boot issues..."
date: 2014-11-02
forum: Installation &amp; Upgrades
---

### Post by magus169999 on 2014-11-02
I have tried a bunch of different things trying to get this to work today but haven't had any success. After I install Ubuntu, I am getting no grub menu.. just straight to windows 8. I have used boot-repair many times in an effort to figure this out. I have literraly spent the last 12 hours trying to set this up, using different methods found throughout this forum. Any help is appreciated. This thing seriously has me stumped! My computer is a Vaio E Series model | SVE14A35CXH pre-installed with windows 8. Here is the boot-repair log. 

[http://paste.ubuntu.com/8786345/](http://paste.ubuntu.com/8786345/)

Thanks everyone!

---

### Post by oldfred on 2014-11-02
Sony's only boot Windows.
UEFI stardard is that UEFI should offer to boot anything, but Sony, HP and others internally modify UEFI to only boot a entry with Windows in the description. But they still allow booting hard drive with bootx64.efi file, so there are work arounds.

Several alternatives, some better for different systems :
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019

[/URL]
 One Sony user
> The trick was to manually copy the ubuntu Boot directory in place of the \EFI\Boot Directory, and rename shimx64.efi to \EFI\Boot\bootx64.efi (not \EFI\Microsoft\Boot\bootmgfw.efi )


 Sony Vaio Pro  hard coded to only boot "Windows Boot Manager"
[http://ubuntuforums.org/showthread.php?t=2196415](http://ubuntuforums.org/showthread.php?t=2196415)
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"
[http://ubuntuforums.org/showthread.php?t=2200818](http://ubuntuforums.org/showthread.php?t=2200818)
Sony Vaio Pro SVP-1x21 - Arch but similar settings needed for any Linux Haswell
[https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21](https://wiki.archlinux.org/index.php/Sony_Vaio_Pro_SVP-1x21)

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by tehtotalpwnage on 2014-11-02
Another thing that might also be an issue: did you install Ubuntu in UEFI mode?

---

### Post by oldfred on 2014-11-02
@ tehtotalpwnage

While installing in BIOS mode is often an issue, OP posted the summary report from Boot-Repair. It shows no grub installed in MBR and both Ubuntu & Windows efi boot files in sda3 the efi partition. 
So both installs are in UEFI boot mode.

Users often do not know how they install so we like all the detail in Boot-Repair's summary report, although sometimes just asking for some info can resolve simile issues. All the Boot-Repair summary report is many commands like fdisk, parted, cat /etc/default/grub in one large report.

---

### Post by tehtotalpwnage on 2014-11-02
Ah alright, got confused since I saw boot files besides .efi

---

