---
title: "Unable to set up dual-boot configuration after installing Windows 10, build 10586"
date: 2016-01-04
forum: Installation &amp; Upgrades
---

### Post by Tomas_Balderas on 2016-01-04
Hello dear experts. I hope you can help me ;)

In the past, I was able to set up my HP laptop to boot either Ubuntu 14.04.1 LTS or Windows 8.1 or, later, Windows 10. Yesterday, I performed a fresh installation of 64-bit Windows 10 Home from the DVD source, which during the phase of installing updates, installed the [COLOR=#252525][FONT=sans-serif]build 10586 [/FONT][/COLOR][COLOR=#252525][FONT=sans-serif]("November Update" or "Version 1511" or "Threshold 2" (TH2)).

As previously, in order for dual-boot I turned off fast setup and ran "[/FONT][/COLOR]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi" in Windows 10, but I failed this time.[COLOR=#252525][FONT=sans-serif]
[/FONT][/COLOR]
In the past, I received the following text after running boot-repair:

```

Boot successfully repaired.
Please write on a paper the following URL:
http://paste.ubuntu.com/9403740/
In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/shimx64.efi file!
If your computer boots directly into Windows, try to change the boot order in
your BIOS.
If your BIOS does not allow to change the boot order, change the default boot
entry of the Windows boot loader.
For example you can boot into Windows, then type the following command in an
admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

```

This time, I got the following message:

```

Boot successfully repaired.
Please write on a paper the following URL:
http://paste.ubuntu.com/14406044/
In case you still experience boot problem, indicate this URL to:
boot.repair@gmail.com or to your favorite support forum.
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (1000GB) disk!
The boot files of [The OS now in use - Ubuntu 14.04.3 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

```

As you can see the messages are different and I don't really understand what the new one indicates. As a result, no GRUB gets executed when turning the computer on or restarting it, and the boot goes straight to Windows 10. My Ubuntu 14.04.1 LTS remains intact and I'm able to boot into it by shift-restarting from Windows 10.

What am I doing wrong?

Thank you very much. Kindest regards.

Tomás

---

### Post by yancek on 2016-01-04
Do you have both windows and Ubuntu installed using UEFI?  You didn't post the link to the output of the boot repair script which would be helpful.

---

### Post by oldfred on 2016-01-05
Hidden in you code was this, is this you most current Summary Report?
[http://paste.ubuntu.com/14406044/](http://paste.ubuntu.com/14406044/)

HP has not been dual boot friendly, did the Windows BCD entry work before?

Most with HP, copy shimx64.efi into /EFI/Boot and rename to bootx64.efi. Your current bootx64.efi was backed up by Boot-Repair and probably is just another copy of the Windows efi boot loader.
Then you can boot a hard drive or fallback default entry in UEFI. Some may need to add that entry with efibootmgr, but you show several hard drive entries(not sure if UEFI or BIOS or both?)
Details in link in my signature.

Other HP users:
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

        HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)

---

