---
title: "boot-repair advanced options"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by Luis_Arjona on 2015-07-17
I had a triple boot: windows7, ubuntu12.04 (in sda5) and an additional ubuntu 12.04 that I only used initially for testing (this one is in sda7).
I removed windows7 and installed windows10 preview. As usual, the installation removed grub2.
I used the recommended repair of "boot repair" to recover grub2 boot loader, but it only gives me access to my test system (the one in sda7). I lost accesst to  my ubuntu 12.04 working version (the one in sda5), that does not appear in the grub menu anymore. I also lost access to windows 10 (the grub menu gives me two windows7 entries but none of them works, when I click on them I only get a brown/purple screen).
Could any one tell me if it si possible to fix this choosing the appropiate options in boot-repair advanced options?
The boot infor url of my system is: [http://paste.ubuntu.com/11892839/](http://paste.ubuntu.com/11892839/)

---

### Post by oldfred on 2015-07-17
You have labelled sda5 as a /home, you show two labelled as /home.
And sda5 does not show any boot files?

Grub only boots working Windows. So when you installed new Windows did you turn off the always on hibernation or fast boot? Grub does not boot hibernated Windows.

       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

You may have to use Windows repair console or Boot-Repair to restore a Windows boot loader to MBR to boot Windows & turn off fast startup. Then restore grub to MBR.

 [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

I would expect Windows 10 to be the same:

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

