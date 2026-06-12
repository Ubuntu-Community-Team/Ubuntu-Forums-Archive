---
title: "Cannot boot Windows 8 using GRUB after reinstalling Windows 8"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by charch on 2012-10-06
Hello everyone. I have been dual booting Windows 8(The official release of it given to me by my university) and Ubuntu 12.04.1 LTS for about a month without any problems, but recently my Windows 8 install has been having some issues so I decided to reinstall it from scratch. The installation went well, but after reinstalling grub using the chroot method from the liveUSB I have not been able to load up windows 8. Windows 8 has a menu option but when I click it, the blue windows icon shows up, but the spinning circle isn't there and Windows 8 does not boot up... The only way I can get Windows 8 to boot is to use "bootrec.exe /fixboot" and "bootrec.exe /fixmbr" from the Windows 8 cd, but this removes grub... Please help!

---

### Post by darkod on 2012-10-06
First of all, chroot is not necessary when ubuntu is running fine and you only want to reinstall the MBR part of grub2. You only need to mount the root partition and use that as parameter.

You might need to run update-grub since the win8 partition was formatted.

So, from live mode you can reinstall grub with (assuming the ubuntu root partition is /dev/sdaX):
sudo mount /dev/sdaX /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/code]

Note that in the second command you use only /dev/sda without any partition number.

After you boot ubuntu once, run:
sudo update-grub

See if that helps.

---

### Post by oldfred on 2012-10-06
Did you turn off the hybrid hibernation feature? Even if dual booting two copies of Windows, you should not use it.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by charch on 2012-10-06
I have tried this, yet I have come to the same issue. I even tried boot-repair... I really don't know what's going on. It worked before reinstalling Windows :S Looks like I may have to reinstall Ubuntu aswell...

---

