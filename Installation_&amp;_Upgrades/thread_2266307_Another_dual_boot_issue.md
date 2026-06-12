---
title: "Another dual boot issue"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by Durgol on 2015-02-21
Hello 
I'm kind of embarrassed to post this.
But this issue is now getting out of hand (After 4 days of trial and error).
I've been trying to get this dualboot working with windows 7 on one ssd and ubuntu on the other ssd.
I've installed this kind of dualboot multiple times on just one ssd and also once on this exact setup (Windows on one ssd ubuntu on the other).
And now I seem to not be able to do it after >7 attempts.
I think the frustration doesnt let me think straight anymore. So that's why I came here to beg for help.
Please there has to be a saviour out there that can stop my descend into insanity.
As an attachment there are the results from the bootinfo script..
Any input is greatly appreciated!
Edit: it might be important to know that i can boot into ubuntu through the grub loader but windows just doesn't show up..
Cheers
Durgolias

---

### Post by oldfred on 2015-02-21
You are into the major differences between UEFI & BIOS.
When you install both Windows and Ubuntu how you boot install media, is how it will install. And you then must be consistent in booting installer. Either both UEFI or both BIOS.

And Windows at least in BIOS mode, installs its boot loader to the drive set as boot in BIOS. That may not be same drive as you install. So then if you install Ubuntu to the boot drive, you overwriteh the 100MB boot partition.

There are advantages to gpt and UEFI.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

Some find it easier to disconnect one drive and totally install one system to that drive. Then do same with other drive. But you still need to be consistent how you install. And usually better to keep Windows as first drive in UEFI/BIOS or sda.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)


 Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

Even if you elect to install both systems in BIOS mode, often best to still use gpt partitioning with Ubuntu. But you need the 1 or 2MB unformatted partition with the bios_grub flag. 
Windows (and Ubuntu) only boot in BIOS mode from MBR (msdos) partitioned drives.
Windows only boots with UEFI mode from gpt(GUID) partitioned drives.
Ubuntu can boot in UEFI or BIOS mode from gpt drives if correct supporting partitions are on drive.

More info on UEFI if desire in link below in my signature.

---

### Post by Durgol on 2015-02-21
Thank you so much for your informative answer!
I will try again tomorrow and will post the results.
I'm sure this will help! :)

---

### Post by Durgol on 2015-02-22
If finally works.
Installing both OS' with GPT partitioning (while other HD's were disconnected) and UEFI boot mode in bios did the trick.
Installed windows first on the primary ssd with usb stick (GPT) and ubuntu after on other ssd with GPT also.
After that launched boot-repair from usb live distro and did the recommended repair.
Now both ubuntu and windows show up in the grub loader.
Thank you so much! 
:D
Cheers 
Durgolias

---

### Post by oldfred on 2015-02-22
Glad you go it working. :)

---

