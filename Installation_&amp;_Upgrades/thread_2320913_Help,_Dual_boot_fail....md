---
title: "Help, Dual boot fail..."
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by maxfield on 2016-04-18
Hi,

So I have known about Ubuntu for a while and thought I would try it out. So I download Ubuntu and installed (version: 14.04 LTS). Before installing it I made a 20GB partition on my HDD through windows. (Windows is installed on a separate drive, I have 2 HDD, 1 SSD. (windows is on the SSD ofcourse))
Now that it was installed and I loaded it up everything worked just fine, I quite liked it too :). Then **** hit the fan, I restarted my PC and wanted to get into my Windows 10 I couldn't find a way to get into it so I tried doing things I knew that I could such as forcing it to boot from the main drive (which is separate from the Ubuntu installation) and it booted to Ubuntu.... ****. So when in Ubuntu I clicked on the separate drive (with windows on it) and this error came up:
```

Error mounting /dev/sda2 at /media/max/1C3C0C853C0C5C60: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/max/1C3C0C853C0C5C60"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```
I googled... extensively and found that I probably installed the root? and or prefix? to my main drive and something about Windows 10 being greedy to only letting one OS to a drive (Meaning my installation is still there? I hope).
After getting relatively pissed, I unplugged my drives (Not the windows 10 one) and booted up... Some recovery GRUB thing popped up... I had no clue, of to google.. I found that you could get to a grub menu to change to my windows 10 install... yay! progress. So I hard shut down my PC (As I don't know any commands to get out of this GRUB thingy) held the shift-key to get into the grub menu. It loaded. There and behold... No windows 10 boot ._.
After some **** talking to my PC I decided to come to the Ubuntu forum (where better? I'm sure someone else has had this problem) to resolve my issue.

Hope someone can help soon. 

PS: I am writing from Ubuntu, it actually quite nice. 8^) (At least there&#8217;s a positive some where in all this mayhem)

Thanks,
Max

---

### Post by westie457 on 2016-04-18
Welcome to the Forum.

While you have Ubuntu running go here. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Use the 2nd option to install Boot Repair. When it is running do not attempt any repairs,  just click on 'Create a Boot Info summary' and post the generated link here so we can peruse the situation and make informed suggestions to help you fix this.

---

### Post by slickymaster on 2016-04-18
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by maxfield on 2016-04-18
Here you go: [http://paste.ubuntu.com/15921899/](http://paste.ubuntu.com/15921899/)

---

### Post by maxfield on 2016-04-18
Errrrrr.... I just clicked on my SSD again and I can see the contents (The only thing I did during this gap was plug in another USB to see what was on it). Should I restart and try to use the GRUB menu?

---

### Post by grahammechanical on 2016-04-18
From Windows 8 onwards Microsoft has used hibernation instead of a full shut down to achieve fast start up times. This means that when we try to access a Windows partition from Ubuntu we get that message. In fact if we are installing Ubuntu on a system with Windows 10 we should;

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too.
> 
To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode. 
[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 
[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 
[/LIST]


It is the Windows Fast Startup that is actually hibernation, as far as I know.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

EDIT: There is something that you failed to mention. You have installed Ubuntu by installing wubi.exe in windows. But wubi.exe is not compatible with Windows 8 onwards and there is no further development on it and because there are too few of us on the forum who have any experience of wubi we do not support wubi installs.

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

Regards.

---

### Post by oldfred on 2016-04-18
Several issues.
It looks like you tried to install wubi in sda2. That is not supported since 12.04. Best to uninstall that to avoid confusion. 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Generally use Windows tools for Windows & Linux tools for Linux. Or do not create partitions for Linux with Windows. It can lead to major issues, but your partitions look ok, other than a missing one.

Not sure what install option you used. But you have Windows on sda with MBR partitions for BIOS boot. But sdb & sdc are the newer gpt partitioned. Grub always defaults to sda, but with multiple drives you want to install the grub2 boot loader into the same drive as Ubuntu and only the Something Else install option gives you that choice.

For grub to install correctly to gpt partitioned drives you must have either an ESP - efi system partition for UEFI boot or a tiny 1 or 2MB unformatted partition with the bios_grub boot flag. Since Windows is BIOS boot you should just add a 1MB unformatted partition anywhere on sdc and add the bios_grub partition. You can use gparted for that from live installer.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

You want to keep a Windows boot loader in sda, so when Windows breaks you can try to directly boot it and see if f8 gets you into repair console. But better to always have a Windows repair flash drive.
And you want grub installed to sdc so you directly boot from BIOS to sdc and grub will let you boot either Ubuntu or Windows. But grub only boots working Windows.
DO NOT use auto fix in Boot-Repair. That will try to install grub into the MBR of all drives. And it will not install correctly to the gpt drives without the bios_grub partition.
DO use Boot-Repair's advanced mode, choose Ubuntu install and sdc as grub bootloader install location. You can also install a Windows like boot loader the same way to sda. Choose Windows & sda. Or use your Windows repair flash drive and the fixMBR command on sda.

And Windows cannot be hibernated nor need chkdsk. Windows 8 or later is always hibernated as that is all its fast start up is. So if dual booting you need to turn fast start up off. Or you can possibly directly always boot from BIOS or one time boot key like f10 or f12, check manual.

---

### Post by maxfield on 2016-04-18
Is there a way to just uninstall Ubuntu without affecting the windows install? Then I can try a proper install with a disk. I just did a quick google would this work? [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by oldfred on 2016-04-18
You need to first fix the Windows drive's MBR with a Window boot loader.
The part of a boot loader in the MBR is tiny and just jumps to the install partition to find more boot code. If you uninstall Ubuntu before fixing Windows then you get a non-working grub.

If just reinstalling Ubuntu, you do not have to uninstall it. You can use Something Else and choose same partition or change partitions around if desired. I generally prefer to use gparted & partition in advance. It seems a bit easier, but may not be.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by maxfield on 2016-04-19
So I tried doing everything that everyone suggest no luck :| (Probably Human Error *cough* me). So I decided an easy way out. I firstly backed-up everything from the main drive to a different internal drive. Then fortunately I had a Window 7 ISO on it as well, I used winUSB to make a pen drive bootable. I tried using the system recovery once loaded with the pen drive, no luck. So I formatted my main drive and installed Windows 7. Simple.
Now happily (kinda) typing away from a Windows 7 install.
However, I am not one to give up so easily. I have a spare hard drive. If I disconnect all others and installed Ubuntu to that one (through usb) would things all be good once I reconnect the other HDD's? Would I be able to boot separately via BIOS?

---

### Post by yancek on 2016-04-19
> If I disconnect all others and installed Ubuntu to that one (through  usb) would things all be good once I reconnect the other HDD's?

Obviously you won't be able to boot windows from the Grub menu of Ubuntu if you do not have the windows drive attached so after attaching it again, run:  sudo update-grub from Ubuntu and that should solve that issue by creating an entry in the boot menu.  Or you should be able to boot separately from the BIOS by selecting the correct drive there.

Did you install windows 7 in MBR mode?  That's usually the default.  Read through the post above by oldfred regarding GPT partitioning and UEFI with windows.  You can't mix UEFI and MBR installs.  Also, as pointed out above, make sure when you install Ubuntu you install the bootloader to the MBR of the same drive.  Shouldn't be a probelm if it's the only drive attached.  You might take a look at the tutorial below on installing Ubuntu 14.04, very detailed but only deals with an MBR install.

   [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2016-04-19
If willing to disconnect drives, and only have the one drive installed then that will insure grub is installed only to that drive.
Be sure to reinstall drives so Windows is still sda, it probably is  in SATA0 port. And best to have SATA ports used in order with DVD/CD last. I have skipped ports & had DVD between drives and had drive order issues. Ubuntu uses UUID so it would always find correct drive, but device order can change and some manual commands I use device and that could be dangerous with device has changed from sdb to sdc.

---

### Post by maxfield on 2016-04-20
Ok, I installed Ubuntu on the drive. And I can pick via boot menu (Which is fine). Woo! :D

Thanks for everyone's help. :)

PS: Hope you don't see me here again soon. :P

---

### Post by oldfred on 2016-04-20
Glad it is working, come back anytime. :)

---

