---
title: "Trouble with getting live CD to boot"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by jgmillr1 on 2012-12-23
Hi All,

I have a newly purchased Lenovo G580 laptop with Win8 preinstalled that I'm attempting to install 12.04 or 12.10 alongside. I shrunk the Win8 volume to leave 200Gb for the Ubuntu system. 

I have successfully installed Ubuntu (and Mandriva) on dozens of systems for over the last 10+ years. All that means is that I'm not a total noob and have tried the obvious things, except when it now comes to problems that I suspect I'm having with this new-fangled UEFI and secure boot.

Let me first go over the things I have already tried and failed...
Attemped to do CD install:
1) I burned the ISO using the "write to disc" option in another working Ubuntu 12.10 system.
2) I have already tested that this DVD actually will boot on a desktop machine.
3) I have already reset the boot order on the laptop to boot the CDROM before the HDD. 

RESULT: The disc won't boot and does not even show up as a boot option when the boot menu is presented. In the Windows boot manager, when I direct it to boot from the CD the system just reboots.

Attempted to do USB install:
1) I made a bootable USB flash drive with the 12.04 iso image under a working 12.10 system using the "startup disc creator". 
2) I reset the boot order to USB HDD first and enabled the usb booting in the BIOS.

RESULT: Again no luck. The flash drive would not boot or show up as a boot option under the boot menu.

Attempted to use Ubuntu's CD boot helper.
1) Ran wubi.exe on the LiveCD, clicked Demo and Full install and then clicked help me boot cd.
2) After it downloaded the boot helper a new menu item appeared on the boot manager screen which I selected.

RESULT: Error message saying there is a problem with a file it installed. (I would give the exact message but it isn't on the screen long enough for me to type it out here.)

So, I'm am completely stumped. I suspect I'm running into some trouble with a BIOS setting and/or some security setting. Note that I am unable to alter the "Secure Boot" mode in the BIOS. It is grayed out for some reason. Hope I'm not screwed here. Should be able to change that, but how?

I have seen notes that I need to use the 64bit version of Ubuntu. There used to be separate Desktop versions for 32bit and 64bit but now there is only one "PC (Intel x86) desktop image". Is this 64bit or 32bit?

Any help is appreciated. Thanks in advance.
-John

---

### Post by grahammechanical on 2012-12-23
First thing, do not try to install Ubuntu 12.04. You must use Ubuntu 12.10 because that comes complete with a kernel that has been signed with a Microsoft key so that it is recognised by the secure boot system.

Second, there is no guarantee that the maker of this laptop is complying with the Microsoft protocol regarding secure boot. All they might care about is that Windows 8 is on the machine and working. Microsoft only recommends it does not demand that the maker put the Microsoft secure boot key in the UEFI/BIOS of the machine.

Third, the purpose behind secure boot is to stop the installation of another OS that does not have the Microsoft signed kernel. So, it will not recognise the 12.04 live CD as a valid OS to load.

Fourth, there are still options for downloading 32bit or 64bit versions of Ubuntu. Where are you downloading from?

[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

The choose your flavour menu offers 64bit. May I suggest that you take a step back. Re-think and start again with only 12.10? We can get confused with too many things going wrong.

> The Ubuntu first-stage EFI bootloader is signed by Microsoft, but the key that is used for signing is one that's _recommended_ by Microsoft, not one that's _required_ by the Windows 8 certification requirements. Will all hardware include this key in practice? The Windows 8 requirements also say that every machine must allow the user to disable Secure Boot. Will manufacturers get this right, and will users be able to make use of it in the event the manufacture didn't include the Microsoft-recommended key? Only time will tell.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Regards.

---

### Post by jgmillr1 on 2012-12-23
Thanks for the quick reply. I mistook the "AMD64" naming of the 64bit ISO to mean that I could/should not run it on a system with an Intel processor. This was the link I had used:
[http://releases.ubuntu.com/quantal/](http://releases.ubuntu.com/quantal/)

I'm downloading that now and will post on any success or failure.

---

### Post by jgmillr1 on 2012-12-23
I downloaded and burned a copy of 12.10 64-bit but still no luck. It will neither boot off the CD nor boot with the "wubi" boot helper.

At this point I can't do anything but hope 13.04 works or that Lenovo can somehow help. Anyone have any other thoughts?

---

### Post by jgmillr1 on 2012-12-27
I have a successful update to this saga... I'll post the info here in case some other poor soul has the same issue and can cut days of impending head-banging.

First, I eventually was able to disable Secure Boot. To do this with the Lenovo laptop, you first have to set an administrator password. This is in the same BIOS menu as the Secure Boot option. After you do this, the Secure Boot option is no longer greyed out and you can change it. 

(Note that once you have ALREADY set up the admin password and can move down to the Secure Boot setting, then it kindly gives you the hint that you need to set up an admin password before this can be changed. Good job Lenovo, next time I'll seek the guidance of my crystal ball to figure out what I need to do ahead of time.)

Second, I changed the UEFI boot to Legacy mode.

I believe all this finally allowed the laptop to boot the Ubuntu live ISO.

Third, I couldn't get the laptop to boot from the CDROM regardless of the boot order setting or F12 taps. The laptop simply did not recognize there was a bootable CD in the drive. I had to boot from a USB flash drive. (Be sure to set the boot order in the BIOS to USB first and check the enable USB booting option). Important, in order for the USB drive to actually boot, I had to format it as FAT32. Then I used the USB-creator software from a different working Ubuntu distribution to write the ISO to the drive.

With all this, the laptop is finally beginning to install 12.10 64-bit! Yeah! 

I'm hoping the last part of the install process will be easier than the first part.

---

### Post by oldfred on 2012-12-28
You really want to install in UEFI mode not legacy. As both Windows & Ubuntu have to be installed in the same mode.

And be sure to turn off any fast boot or quick boot options in UEFI menu. Otherwise you may not be able to get back into the UEFI menu. When fast boot is on, you only get to UEFI menu with Windows.

But if you install in legacy mode you can convert it to UEFI mode easily. Boot-Repair automates the process of uninstalling grub-pc (BIOS/legacy) and installing grub-efi (UEFI).

Grub also has a bug in that it still creates only BIOS chain load entry in the grub menu. For UEFI you need an efi chain type entry. But Boot-Repair also fixes that.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

