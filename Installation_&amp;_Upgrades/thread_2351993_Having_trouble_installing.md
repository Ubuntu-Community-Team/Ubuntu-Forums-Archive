---
title: "Having trouble installing"
date: 2017-02-08
forum: Installation &amp; Upgrades
---

### Post by fluffymcmuffins on 2017-02-08
I'm trying to install Ubuntu on a brand new SSD. I just bought it and it has nothing on it yet.

I have tried to do the installation through both a USB drive and a CD as directed by the installation instructions page, but my computer refuses to boot from either. After some searching around forums, it seems that the issue is "Secure boot" which I have found instructions on how to disable. Unfortunately, when I get to the point where I am supposed to be able to disable secure boot, the option is greyed out and I cannot select it. One site I stumbled upon stated that Microsoft gives the manufacturers the option to restrict users from disabling secure boot. 

So my questions are:

1. Is there any way I can disable secure boot so that I can boot from the USB drive or CD given that the option is greyed out?

2. Is there any other way I can install Ubuntu on the SSD without having my computer boot from one of them? 

If there is any information that will help resolve this issue please don't hesitate to ask. ^_^

---

### Post by oldfred on 2017-02-08
What system brand & model?
A few lightweight tablet type systems were UEFI 32 bit and no BIOS boot. 
But all standard systems Microsoft requires vendors to give users a way to turn off UEFI Secure boot. You probably still should boot in UEFI mode.
A few require Legacy/CSM/BIOS mode on, but still have you boot in UEFI mode. Most with CSM on, only boot in BIOS mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Some require you to set a UEFI password to open more settings. Never forget that or reset to no password after configuration if possible.

But Ubuntu installs to systems with Secure boot on. You may have to specifically allow USB boot in UEFI mode as booting any other device is often considered not secure. And if dual booting can then only boot from UEFI boot menu, not grub menu.

More details in link in my signature below.

---

### Post by fluffymcmuffins on 2017-02-08
Thanks so much for your response. =)

My system is an ASUS M51AD running Windows 10. 

I did enable CSM (which if I recall correctly had a Legacy option which I chose) and enabled USB boot. I didn't try setting a UEFI password so I'll see if that gets it to work. 

I'll read through the thread in your signature as well and see if I can figure it out from there if the password doesn't do it. I am very new to this so I'm not sure I'll understand/know how to do things right off but I'll give it a shot. =P

---

### Post by oldfred on 2017-02-09
Some Asus needed boot parameter pci=nomsi.
Often UEFI is similar across models, so even if not same model, users may  have posted helpful info.
Newer version of Ubuntu should be better that threads discussing older versions.

 Asus/Samsung problem with every NVME SSD and G752! 
[https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551](https://ubuntuforums.org/showthread.php?t=2307273&p=13584551#post13584551)
[http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04](http://askubuntu.com/questions/861854/nvme-disk-configured-in-raid0-unable-to-install-ubuntu-16-04)
Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi

---

### Post by fluffymcmuffins on 2017-02-09
I made a password for UEFI and also disabled "Fast boot" and it worked so I assume one of those was the issue, so thank you for that!!

Thanks to that I was able to get Ubuntu installed on my hard drive. The issue I am having now is that I don't know how to install it on my SSD. I selected "something else" for the installation process since it defaulted to my hard drive, but when I select the SSD and try to install it says "No root file system is defined. Please correct this from the partitioning menu." I am not sure what to do from that point. I looked up the error and people have said you need to partition the SSD first but I have already done that. Any idea what to do there?

---

### Post by RobGoss on 2017-02-09
This means you need to set the Root for your installation you normally do this with gparted or partition management

I believe you can click on the **+** or** -** and it should bring up a drop down menu choose / as the Root and continue with the installation

I've attached a screen shot that might help

---

### Post by oldfred on 2017-02-09
When you want control over partitioning or better partition in advance, you have to use the Something Else install option.
But that option does not know which partition is / (root) and which is /home or other partitions. You may have multiple ext4 partitions. It is smart enough to auto use ESP and find swap.

You need to choose(change button) and select ext4 & / in pop up.

example, many install blogs show using + key as they are partitioning during install:
       [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) 

But if your are installing to SSD & it is sdb, you must have an ESP on sda. Make sure you also have created on on SSD.
Grub only installs to drive seen as sda. And drive order is mostly controlled by SATA port order.

 I found I must have sda in SATA0 and use ports in port order. If you skip ports, when you plug in a flash drive it may be sdc, but on reboot goes into the skipped port changing all your other drives. Ubuntu still works as it uses UUID, but any command using device like /dev/sdb may or may not be drive you expect.

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by fluffymcmuffins on 2017-02-09
Ok so I set the mount point as / and it let me go through with the installation. However, during the installation a window popped up saying that it could not install the boot loader on the SSD. I wasn't sure what to do at that point so I just told it to continue without the boot loader and it informed me I would need to manually install one in order to use Ubuntu. So it appears to have gone through with the installation successfully and is just missing the boot loader now. If I try to boot from the SSD it takes me to the login screen but does nothing after I enter my password. It just shows the same screen with nothing except the Ubuntu version number in the bottom left. 

So I assume at this point I just need to manually install the boot loader onto the SSD, is that right?

Edit: I also do not know how to do that by the by.

---

### Post by RobGoss on 2017-02-09
SSD maybe a little different compared to a normal hard drive but I think you should still be able to use Boot repair to get your boot loader installed

You will Need to boot into the live desktop in order to run boot repair, follow the on screen instructions when you have installed boot repair 

Boot repair
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

After you done reboot your machine and see if you're able to see your desktop

---

### Post by oldfred on 2017-02-09
Is SSD seen as drive sda?

If not you must have an ESP - efi system partition on drive seen as sda.
And what is drive sda?

Post this:
sudo parted -l

---

### Post by fluffymcmuffins on 2017-02-09
Alright I got it to install successfully by detaching my HDD from the motherboard. Then I just followed the same installation procedure by booting from the USB drive.

Thanks so much for your help guys I really appreciate it. ^_^

---

### Post by oldfred on 2017-02-09
You can change to [Solved].

I have had issues if I do not plug drives in SATA ports in port order. The sda drive is SATA0 and then each drive in next numbered SATA port. Issue often is when I plug in flash drive as sdc, but then reboot, flash drive becomes sdb and sdb becomes sdc.  So a command to erase flash drive as sdc potentially erases wrong drive if not paying attentions to drive order.

---

### Post by RobGoss on 2017-02-09
Glad to hear you got it all sorted out great job

---

