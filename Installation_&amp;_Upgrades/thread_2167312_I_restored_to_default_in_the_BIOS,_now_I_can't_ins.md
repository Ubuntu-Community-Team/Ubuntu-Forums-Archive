---
title: "I restored to default in the BIOS, now I can't install Ubuntu"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by evillan on 2013-08-13
I wiped my entire system through the BIOS by restoring to default and now I want to install ubuntu on my laptop (64-bit Asus Zenbook). There's nothing on it, when I turn it on it automatically goes to the BIOS.

I have a bootable USB with 12.04 and the laptop correctly shows the start menu where I can choose between trying ubuntu, installing ubuntu or checking the desk. No matter what option I pick, the screen just goes to black and nothing happens (I've waited more than 10 minutes).

Any ideas? Do I need to install something before I can install ubuntu?

Thank you.

---

### Post by fantab on 2013-08-13
What Graphics do you have there?
Try [**NOMODESET**]("http://ubuntuforums.org/showthread.php?t=1613132") option.

Do you have BIOS or UEFI?

Since you have reset Bios to default check what mode is SATA set to. It should be ACHI.

---

### Post by evillan on 2013-08-13
It has "Intel HD Graphics 4000". In the BIOS, I can pick "DVMT Pre-Allocated" and it's set to 64M (other options are 128M, 256M and 512M). There are no other graphics related options in the BIOS. I'm restarting after I've posted this to try the nomodeset option, thank you.

I think I have BIOS, it says "BIOS Information" in the main tab and the BIOS vendor is American Megatrends. The headline is "Aptio Setup Utility" though. Sorry, I'm not that well versed in these sorts of things, so if I've omitted any info, please tell me what to look for. 

The SATA mode is AHCI, so that should be correct.

This is a completely new laptop and I actually installed ubuntu 12.04 on it before the reformatting, with the same bootable usb I'm using now. The laptop has a 24 GB SDD and a 500 GB HDD, it came with Win8 on the SDD and I didn't want Win on it, that's why I reformatted it. When I installed 12.04 the first time, I placed it on the HDD. I'd like to put 12.04 on the SDD, but yeah, first I need to get it to work.

---

### Post by evillan on 2013-08-13
Hi again,

I tried the nomodeset option and it didn't work, unfortunately. Still just a blank screen.

---

### Post by oldfred on 2013-08-13
If it was a new computer with Windows 8, you have UEFI with secure boot. UEFI also has a CSM mode which is for compatibility or emulates the old BIOS.

If you have the small SSD, then it was probably an Ultrabook which had Intel SRT and that uses RAID. So you need to remove the RAID meta-data from the drive to get grub to correctly install. And it has dual video.
        
Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

Do you want BIOS or UEFI? Either way drives are gpt partitioned unless you totally erased and reformatted. If you use Windows to convert to MBR(msdos), it does not do it correctly and drive is MBR with gpt backup or confused.

If installing in BIOS mode with gpt partitioning you need a bios_grub partition. Or if UEFI install, you need an efi partition as the first partition on the drive. Best to have one on both drives as some do not directly boot from SSD.

What computer is this?

---

### Post by Geezanansa on 2013-08-14
Wow oldfred you never cease to amaze me; it is amazing how you can decipher so much from as little info, which is a testament to your vast knowledge..  There is a question on Ask Ubuntu that is very similar to which i tried to give advice. On reading this thread you (oldfred) have given much more extra advice that is important for the use of Ubuntu on this machine so thought it would be helpful to try and bring the posters attention to this thread and vice versa.  It is an assumption to assume both posters are the same so maybe both could benefit as this has not been marked as solved.  The Ask Ubuntu question is found [http://askubuntu.com/questions/332011/i-restored-to-default-in-the-bios-now-i-cant-install-ubuntu/332030#332030](http://askubuntu.com/questions/332011/i-restored-to-default-in-the-bios-now-i-cant-install-ubuntu/332030#332030)  I used my answer there to edit another answer found at [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

The asker of the first linked question found that disabling Secure Boot allowed installation of Ubuntu.

---

### Post by grahammechanical on 2013-08-14
> The asker of the first linked question found that disabling Secure Boot allowed installation of Ubuntu.

That would be the case if installing Ubuntu 12.04 as Ubuntu 12.10 was the first Linux distribution to be able to install with secure boot enabled. If we download the latest Ubuntu 12.04 we will find it is 12.04.2 and that it will install with secure boot enabled because the signed kernel feature of 12.10 was backported to 12.04.1 and 12.04.2 and is present on every version of ubuntu since 12.10.

That does not mean that installing Ubuntu alongside Windows 8 will be without problems. Many threads on this forum testify to this.

Regards.

---

### Post by oldfred on 2013-08-14
In another thread a user with HP had black screen issues. 

I asked the OP to confirm, but it seemed system would not work with UEFI but did work with CSM. But was still booted with UEFI. Or it maybe one of the systems that auto boots either UEFI if boot files in efi partition or BIOS if MBR found after checking efi partition. And then does UEFI mean secure boot on for that system?

---

### Post by Geezanansa on 2013-08-14
> **grahammechanical said:**
> That would be the case if installing Ubuntu 12.04 as Ubuntu 12.10 was the first Linux distribution to be able to install with secure boot enabled. If we download the latest Ubuntu 12.04 we will find it is 12.04.2 and that it will install with secure boot enabled because the signed kernel feature of 12.10 was backported to 12.04.1 and 12.04.2 and is present on every version of ubuntu since 12.10.

That does not mean that installing Ubuntu alongside Windows 8 will be without problems. Many threads on this forum testify to this.

Regards.

This is the intention of and supposed advantage of using a signed.efi image.  It simply does not happen for the majority as researching this will confirm and as you indicate grahammechanical.  The work around is to switch off secure boot and install Ubuntu using UEFI mode. Then switch Secure Boot back on and use boot-repair to install grub signed.efi.  But again the success of this depends on the hardware being used due to the complexities of different manufacturers implementing UEFI specification in different ways. If Ubuntu installer still does not run with UEFI switch it off or CSM on which will allow installer to run in legacy  mode then using boot repair to install grub-efi and or signed.efi appropriate to firmware settings.  

The point being the Ubuntu installer does not work for the majority using UEFI.

---

