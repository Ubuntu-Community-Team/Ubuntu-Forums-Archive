---
title: "how to install ubuntu 14.04 on acer laptop with win8.1"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by stephenbbb on 2014-06-14
I have read the other posts and answers on the topic and the links. there is no answeer and walkthru on the most common case:
windows 8 with an efi partition already exists. what to do next?

[https://flic.kr/p/nYuH98](https://flic.kr/p/nYuH98)

[https://flic.kr/p/nG1n3U](https://flic.kr/p/nG1n3U)

[https://flic.kr/p/nYoSWW](https://flic.kr/p/nYoSWW)

[https://flic.kr/p/nG1mRb](https://flic.kr/p/nG1mRb)

I want to install ubuntu in the free space. pls tell whether I need to erase the partitions after the free space. they are sdb5 and sdb6.
most importantly how do I tell the installer where to install Ubuntu? it boots in efi mode.

[https://flic.kr/p/nWsLAf](https://flic.kr/p/nWsLAf)

---

### Post by Toby_Hubbard on 2014-06-15
Please state the laptop model number. Although usually at startup you would need to go into the bios settings and set the first startup device to the disk drive (or usb if you are using one).

---

### Post by stephenbbb on 2014-06-16
I hope smb knows how to install Ubuntu on a Windows 8.1 laptop. 
If you do not know, there is no need to post and fake answers when there is no answer.

---

### Post by oldfred on 2014-06-16
You want to keep the push button reset if at all possible. But better if you can make a full back up of Windows and the efi partition. Not sure what other partition is, but for now I would keep both. Your unallocated is plenty for Ubuntu.

You should be able to just install into the unallocated space.
But the latest Windows 8 has created issues. Best to use Something Else and manually create partitions yourself.

Make sure fastboot or the always on hibernation are off.
Have you rebooted Windows so it has run chkdsk after its resize. I assume so, but need to check.

Lots of details with more links to instructions with screenshots in the link in my signature.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Best to install Ubuntu in UEFI mode, but you have to boot installer in UEFI mode as how you boot installer is how it installs. Flash drive should show 2 boot options, one UEFI and one with just the name of the flash drive or BIOS boot mode. A few systems will not let you boot in UEFI mode, often a setting buried away somewhere in UEFI. But you can install in BIOS mode and use Boot-Repair to convert to UEFI boot.

With the something else install in UEFI mode you still specify to install grub2's boot loader to the drive that is sda. But it will use the existing efi partition and add another folder with the name ubuntu with grub's efi boot files.

Some more Something else examples, install steps are the same whether UEFI or BIOS once booted in correct mode.

These are mostly BIOS and may be to a second drive, but Something Else is the same.

 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

Some other Acer, do not think they are the new 14.04, but shows installs.
 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

      
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

