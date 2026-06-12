---
title: "cant boot internal or external hdd"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by johnalexrob on 2011-01-03
I just installed maverick netbook edition on an external hard drive, creating my own partition table. When I tried to boot the drive, grub rescue mode told me file not found. I installed again and used the default partition table and got the same error. I gave up and tried to boot my fedora 13 internal hdd but was told that there was no such device. I looked through these forums and ran a bootloader script and was told that my internal hdd had a bootloader but my external didn't. I tried to load the kernel through grub rescue, but the file system was unknown to grub. The files are still on my internal drive and I don't want to reinstall just to boot it. could the maverick install have incorrectly reconfigured my sda bootloader and it cant boot my sda drive?

---

### Post by johnalexrob on 2011-01-05
Is there anybody out there that can help me at all? I really need to use that computer and Booting from the live cd isn't really that convenient. I feel like a total idiot for not knowing what is wrong and I don't want to reinstall and wipe my main hd if I don't have to.

---

### Post by oldfred on 2011-01-05
Anytime you install to a second, third or external drive that looks like a second drive, you have to use manual install. Then you can get the option to choose where to install grub. You want grub installed to the same drive you install Ubuntu to, especially with external drives.

Grub automatically installs to sda as it assumes that is the drive you want to boot and it will overwrite the boot loader there. Usually this is an issue with windows but grub will add windows and should have added your Fedora to its menu. You need to reinstall Fedora's grub to sda, which I think is still old grub legacy (0.97). With Fedora you also may have a separate /boot partition which you also have to mount to reinstall grub legacy to sda.

You then should install grub2 to the external drive which may be sdb, but sometimes is mounted as other drive letters depending on what else you have installed. Use fdisk to confirm drive letter before installing grub2.

Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

You may have to check on the exact procedure to reinstall grub with Fedora. It should be similar to reinstalling grub legacy with Ubuntu but include the /boot mount also which is not common with Ubuntu and many instructions in Ubuntu leave that off.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by johnalexrob on 2011-01-05
OK. I'll try that. 
Could that be why when my external drive was unplugged grub would tell me no such device? It was installed on sda but looked for sdb?

---

### Post by johnalexrob on 2011-01-05
Reinstalling grub didn't work. I found a site that had instructions on manually installing ubuntu. I did a complete reinstall, and I have now booted off my external hard drive. Now I just have to fix my bootloader on my sda drive. 
I don't know what the problem was. In my last install, I had installed the bootloader on the sdb drive, so I don't know why it wouldn't boot. Now I just have to fix my sda drive bootloader. \Thanks for the help.

---

### Post by oldfred on 2011-01-06
If Ubuntu's osprober found the Fedora, you should be able to boot into Fedora from that. Then it is easy to reinstall Fedora's grub to sda (or does Fedora still use hda?).

For Fedora you would have to get into admin mode, since it does not use sudo. then:

grub-install /dev/sda

---

