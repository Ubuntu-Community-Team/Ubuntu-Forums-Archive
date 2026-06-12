---
title: "Dual boot windows with Ubuntu Using UEFI, and NOT modifying the MBR"
date: 2020-03-31
forum: Installation &amp; Upgrades
---

### Post by robertsaron on 2020-03-31
I have an MSI motherboard, that has UEFI, and I have windows 10 installed. I would like to install Ubuntu, or some flavor of linux, with out modding the MBR. I have done it before, though I do not remember how. 

What I used to do before, was have it boot to the linux drive, and then I could select Windows, there was a timer, and it would automatically boot to linux. The motherboard has 4-5 sata ports. Does the linux drive need to be on the first sata port? Or does that matter with UEFI?

---

### Post by oldfred on 2020-03-31
Only Ubuntu's Ubiquity installer requires the installation of grub into the first drives ESP - efi system partition. That usually is the Windows drive and it does normally work.
Only if you want a totally separate drive and separate ESP on that drive, do you have to do a work around. 

Either during install change mount of ESP, (none of normal settings work), or after install move boot files from first drive's ESP to second drive's ESP and edit fstab with new UUID for mount of ESP. You can manually do a total reinstall of grub as it will install to drive you specify or use Boot-Repair & its advanced mode to reinstall grub. You also in UEFI can disable temporarily the Windows drive, or physically disconnect it, so installer only sees the Ubuntu drive.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Otherwise,  you should just do a standard UEFI install, but use Something Else to be sure it installs to second drive.
Just be sure to boot installer in UEFI boot mode.

More details in link in my signature.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With second drive, I prefer to partition in advance, so I can include an ESP on that drive, otherwise installer will not add it.
Be sure to use gpt partitioning.

---

### Post by robertsaron on 2020-03-31
I never had to do any of that when I had it working the first time.

---

### Post by CelticWarrior on 2020-03-31
> **robertsaron said:**
> I never had to do any of that when I had it working the first time.

Perhaps now it's time for you to try to understand UEFI, its requirements (particularly important for Windows) and how it boots. Namely, any Windows installed in UEFI mode is in a GPT drive which means **there's no MBR**. 

What matter for booting in any UEFI system is the ESP (EFI System Partition), not "drives". It doesn't matter where the OSes are installed, the first boot stage is always in the ESP and its location can be anywhere, even in a totally different drive. There's one setting in the UEFI (firmware that replaced BIOS a long time ago but still incorrectly named as "BIOS" by many people, including vendors) that determines the order it will read the drives looking for the ESP - the physical drive containing the ESP should obviously be set as the first in that order - and another setting that depends on the actual boot stanzas read from the ESP and in this one, considering a dual-boot scenario with Windows and Ubuntu, you want to choose "Ubuntu" in order to boot to the Grub menu from which you can select either "Ubuntu" or "Windows bootloader Manager". Also you can change this in UEFI to Windows in order to boot Windows directly and ignore Ubuntu entirely.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://askubuntu.com/q/221835](https://askubuntu.com/q/221835)

---

### Post by robertsaron on 2020-03-31
@CelticWarrior If Linux supports UEFI mode, and is installed correctly, I can just choose which OS to boot? With this in mind, with UEFI, I can have the OS drives connected to any sata port on the motherboard, and they should still be seen properly? I just ask cause with BIOS windows OS boot and Linux boot drives had to be installed on the first 2 sata ports on the motherboard. 

The odd thing about this is, I have a brand new 500gig Samsung Evo Drive I am trying to install linux on. My windows install is on a 250gig drive. The setup I used to have is as follows.

Windows installed on 1Tb drive, and linux on a 120gig drive. And everything worked. I have since moved windows to the 250 gig drive, pulled out the 120, and have all my games on the 1tb. The motherboard sees the 500 gig drive, but will not boot to it. What I am going to try next is unplugging all the drives, and then connect the drive I want Liunx on, install linux, make sure it boots, and then re-connect all the other drives, and make sure everything works.

---

### Post by oldfred on 2020-03-31
With UEFI, it can forget the UEFI boot entry when a drive is disconnected. 
Many seem to auto find Windows entries, but do not find Linux entries.

You may need to houseclean old entries and perhaps add new Windows entry.
Best to keep drives in same SATA port, starting at SATA0. I have had issues of flash drive becoming sda as it seems to first do SATA ports, but on reboot put a flash drive in the missing SATA port order. My sdf flash drive on reboot becomes sda. So I do have to keep track.

See this for info on adding & housecleaning UEFI entries:
man efibootmgr

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)


More example efibootmgr entries on adding new entries in link in my signature.

---

