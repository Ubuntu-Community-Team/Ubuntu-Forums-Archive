---
title: "GRUB doesn't show after boot-repair recommended repair"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by Roken on 2015-01-14
Hey all,

I Installed Windows 8.1 after I installed Linux Mint 17. Used the USB to run boot-repair and clicked on recommended repair. Restarted and GRUB didn't show, just went straight into Windows. Changed the default boot entry of the Windows bootloader to: bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi like it suggested and nothing happened. Looking for some advice!

Here's my url: [http://paste2.org/hwd7Ftyb](http://paste2.org/hwd7Ftyb)

Thanks!

---

### Post by fkch7y4 on 2015-01-15
It seems that your linux boot files are not installed in the same disk with windows.
Perhaps you should try to install the files in dev/sda as well.

---

### Post by oldfred on 2015-01-15
The second drive shown is just the live installer.

HP's only boot Windows from UEFI menu. Some are able to one time boot with the one time boot key or from Windows boot menu, it that is updated.

Most have to backup the hard drive boot entry /EFI/Boot/bootx64.efi and copy grub or shim into that folder and rename grubx64.efi to be bootx64.efi. Then the hard drive boot entry should work.

Other HP that used rename.
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

Detailed terminal instructions, if needed, from another system, but otherwise the same.
[http://ubuntuforums.org/showthread.php?t=2259521&p=13204087#post13204087](http://ubuntuforums.org/showthread.php?t=2259521&p=13204087#post13204087)

---

### Post by Roken on 2015-01-16
Alright, thanks. Can I do the rename with boot-repair or should I do that via the terminal? It seems like some of those threads suggest that it can be done either way. Also, should I have SecureBoot enabled or disabled? And if it is disabled, should I enable legacy support or keep it disabled as well? My BIOS says that if I keep legacy support disabled it will still use SecureBoot even if the SecureBoot option is set to disabled.

---

### Post by oldfred on 2015-01-17
You can use terminal to run the rename commands. Either from Ubuntu live installer or any other Linux repair liveCD you can boot.

Generally better to have secure boot off. Only shimx64.efi works not grubx64.efi if you have secure boot on.

There are three boot modes, UEFI with secure boot, UEFI and CSM or BIOS/legacy. But not all systems make it clear which mode or how you set each mode. And some have simplified systems that seem to auto switch.

Someone posted this:
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

---

