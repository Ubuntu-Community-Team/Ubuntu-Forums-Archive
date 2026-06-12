---
title: "Is this too simple: Two disks - install WIndows 7 after Ubuntu on a separate disk"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by gefalu2008 on 2009-12-04
I have two Sata disks in my computer. I have Ubuntu 9.10 on my /dev/sda disk and I want to install Windows 7 on the other (empty) disk (/dev/sdb).

Please tell me, if the the following method will be successful:

1. First I intend to disconnect physically the Ubuntu (/dev/sda) by removing its Sata cable from the computer.
2. Then I am planning to install Windows 7 normally on the remaining disk.
3. When the Windows installation has been completed and the machine has been rebooted, I shall reconnect the sata cable of the Ubuntu disk.
4. When booting after that, I shall use BIOS settings to force the machine to boot from the Ubuntu disk
5. Will Ubuntu start up and run normally? If it does, can I use terminal command update-grub in order to make the GRUB 2 realize that there is now a Windows operating system on the other disk?
6. Or do I have to edit GRUB 2 (or MBR settings manually)

I want to have a system in which Ubuntu boots by default and I can select Windows on those occasions I need it.

Thank you very much for advice already in advance. I am a beginner and somewhat confused by this GRUB-MBR business.

- Gef

---

### Post by darkod on 2009-12-04
Yes, it will work exactly as you said. update-grub should do the trick.
I usually don't like disconnecting any hardware when installing an OS, but in this case it is simpler if you do it that way.

---

### Post by gefalu2008 on 2009-12-29
Dear Darko,

thank you very much for your help. I finally got Windows 7 as a Christmas present and as you assured, installation succeeded very smoothly by using this method. The 'update-grub' command is excellent improvement!

- Gef

---

