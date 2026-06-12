---
title: "Windows 10 - Ubuntu Dual boot problems"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by garethdunley on 2015-10-21
I know this issue has been discussed at depth but I cannot find simple instructions. I have installed Ubuntu 15.04 as a dual boot on a friend's Compaq CQ58 alongside Windows 10. I cannot get to the grub 2 screen - the machine boots straight to windows. I can access it via the boot menu (esc - F9) but cannot find step by step instructions to solve the problem. Please help! I have tried some of the solutions here including Boot-Repair-Disk but nothing works.

---

### Post by oldfred on 2015-10-21
Did you install Ubuntu in UEFI mode and is Windows in UEFI mode?
Or are both systems installed in BIOS boot mode?

Best to post details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by garethdunley on 2015-10-21
Thanks.
As far as I know it's all UEFI. Legacy is turned off and always was. Will post to boot-repair and see.

[http://paste.ubuntu.com/12885849](http://paste.ubuntu.com/12885849)

---

### Post by oldfred on 2015-10-21
You need to have Windows fast start up off.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

And HP UEFI does not boot anything but "Windows". They  modify UEFI to also use description which is not per UEFI standard that specifically says not to use descriptions.

Work arounds, also in link in my signature:

 [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[URL="http://ubuntuforums.org/showthread.php?t=2227889"]http://ubuntuforums.org/showthread.php?t=2227889
      [/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

    [URL="http://ubuntuforums.org/showthread.php?t=2227889"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

