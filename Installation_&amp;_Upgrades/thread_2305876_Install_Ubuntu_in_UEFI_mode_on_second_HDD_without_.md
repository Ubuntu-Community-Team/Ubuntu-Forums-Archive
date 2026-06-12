---
title: "Install Ubuntu in UEFI mode on second HDD without affecting first HDD"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by gamelife on 2015-12-10
My system before installing Ubuntu:
HDD1: GPT, Windows 10 installed, with one EFI system partition
HDD2: GPT, two data partitions

What I wanted to do:
Install Ubuntu Desktop and Ubuntu Server on HDD2, without affecting anything on HDD1.
In UEFI BIOS, I select what to boot myself.
If I select HDD1, Windows is booted straight away. I don't want any bootloader asking me what to boot.
If I select HDD2, I can select Ubuntu Desktop or Server under GRUB. I don't care whether there is Windows option.

What I did:
I tried to install Ubuntu Desktop (specifically Kubuntu, 15.10) on HDD2 in UEFI mode.
In the installer, I selected HDD2 (/dev/sdb), added one EFI system partition, one swap partition, one root / partition.
Under "Device for boot loader installation", I made sure I chose /dev/sdb.

What happens now:
Ubuntu installed GRUB to HDD1 (/dev/sda).
In UEFI BIOS,
if I select HDD1, GRUB asks me what to boot (Ubuntu Desktop - default, Windows next);
if I select HDD2, nothing boots - no bootloader is installed in /dev/sdb.

Now, how can I revert back (remove GRUB on HDD1), and achieve what I wanted originally?

---

### Post by sudodus on 2015-12-10
Welcome to the Ubuntu Forums :-)

If I could read your description correctly, you did what you should do, and yet the bootloader was installed in the wrong drive. Either you made a mistake about the bootloader (not likely) or there is a bug in the installer, ubiquity, (also not likely), but we are warned now and should look out for problems in such cases with two drives.

There is a safer way to do the installation: ***Remove the other drive during the installation.*** Then it is not possible to write anything to it. You can install grub into your Ubuntu drive according to the following link

[Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

-o-

I think you need Windows tools to re-install the Windows bootloader, and I don't know the details, but there are other people who know better. So I hope you will soon get advice how to do it :-)

---

### Post by gamelife on 2015-12-10
I successfully reverted back HDD1 (by using DISKPART.exe to remove EFI\ubuntu and a freeware to remove the Ubuntu boot option from firmware).
Now I am finding workarounds to reinstall Ubuntu on HDD2 without physically removing HDD1.

---

### Post by Dennis N on 2015-12-10
If UEFI install mode, Ubuntu's installer (ubiquity) currently uses the first EFI system partition it detects starting with sda. It ignores any user input on this. Since Windows already has an EFI system partition on sda, Ubuntu sees this one first and uses it.

Yes, there is a little dialog where you choose where to install the EFI system partition grub files, but in UEFI mode, is is not functional (it is functional in BIOS mode installs).

Other Linux distributions may have installers that allow you to select the EFI system partition to use (you can have more than one present). One example would be Fedora with its anaconda installer. Hopefully, ubiquity will get this option at some point.

If you find a way around this, please post your method so others can benefit.

---

### Post by Dennis N on 2015-12-10
I haven't experimented with this, but I have thought that you may be able to copy the entire ubuntu folder from an EFI system partition on sda to another one on sdb. Then, use the efibootmgr command to write a new entry into the efibootmgr menu pointing to the new EFI system partition? It seems like is should be possible. 

If you try this out, I would be interested to hear if it works or not.

Also see post #8 below.

---

### Post by sudodus on 2015-12-10
In most modern computers, the easy solution is to remove the other internal drive during the installation of Ubuntu.

---

### Post by ubfan1 on 2015-12-10
Looks like bug 1173457 (...64 bit install uses wrong ESP for secure boot laptop), from April 2013 is still a problem.  Do add yourself to the list, and maybe someday it will be fixed.  
  Both suggestions from Dennis N and Sudodus should work.  The other thing I do on my ESPs is to set up the default bootloader in /EFI/Boot, which is what removable media uses, and what some firmware falls back to upon a failure.  Put a copy of shimx64.efi into /EFI/Boot and rename it bootx64.efi, and also put a copy of grubx64.efi there.  This assumes the normal install's /EFI/ubuntu/grub.cfg file is present.  Using shimx64.efi for the bootx64.efi (instead of grubx64.efi directly) allows both secure and non-secure boot to work.

---

### Post by Dennis N on 2015-12-10
One additional thing I realized after post #5 is that if you should try that idea, you would need to edit the /etc/fstab file so that the new EFI system partition is mounted at /boot/efi instead of the original. Otherwise, it's not going to work. Obviously, do this before booting with the new EFI system partition. 

Again, there may be other pitfalls to be discovered, as I haven't tried this to confirm that it works. Test at your own risk.

---

### Post by gamelife on 2015-12-11
I tried Dennis' idea, it works.

Some other posts suggested to specify the EFI system partition (ESP) for the option "Device for boot loader installation" (e.g. /dev/sdb3 instead of /dev/sdb), I tried but to no avail. I confirmed this option is simply ignored during installation in UEFI mode.

I booted to Ubuntu, manually moved the /EFI/ubuntu folder from HDD1 ESP to HDD2 ESP (I also copied the /EFI/boot folder, maybe not necessary) and rebooted. The UEFI boot menu listed three options: "Windows - HDD1", "Ubuntu - HDD1", "Ubuntu - HDD2". I removed the "Ubuntu - HDD1" option by a freeware (I believe efibootmgr also could do). Then I booted to "Ubuntu - HDD2", updated the device UUID of /boot/efi mount point inside /etc/fstab to HDD2 ESP. Now it basically works, I have "Windows - HDD1" and "Ubuntu - HDD2" in my boot menu.

---

### Post by Dennis N on 2015-12-11
> **gamelife said:**
> I tried Dennis' idea, it works.

Some other posts suggested to specify the EFI system partition (ESP) for the option "Device for boot loader installation" (e.g. /dev/sdb3 instead of /dev/sdb), I tried but to no avail. I confirmed this option is simply ignored during installation in UEFI mode.

I booted to Ubuntu, manually moved the /EFI/ubuntu folder from HDD1 ESP to HDD2 ESP (I also copied the /EFI/boot folder, maybe not necessary) and rebooted. The UEFI boot menu listed three options: "Windows - HDD1", "Ubuntu - HDD1", "Ubuntu - HDD2". I removed the "Ubuntu - HDD1" option by a freeware (I believe efibootmgr also could do). Then I booted to "Ubuntu - HDD2", updated the device UUID of /boot/efi mount point inside /etc/fstab to HDD2 ESP. Now it basically works, I have "Windows - HDD1" and "Ubuntu - HDD2" in my boot menu.

Fantastic! Thanks to testing this idea, confirming that it works and posting your findings. From what you report, the UEFI firmware detected the new EFI system partition files on HDD2 automatically, and created its own new menu entry for HDD2. I thought it might, but wasn't sure. That makes it even easier than I thought. Now we all can use this method when the need arises.

In particular, it would be a way to create separate Ubuntu entries in the UEFI menu for two or more Ubuntu installs, so each can be directly booted.

---

### Post by oldfred on 2015-12-11
I have also tried this for my xenial install on sdb :

#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="xenial_b"

And I do get a unique entry in UEFI. 
But grub is somewhere hard coded to only use the grub.cfg in /EFI/ubuntu not the Grub in the new entry. There has to be a setting somewhere as other distributions use grub2 and use their own name.

And I saw that if you do not have a GRUB_DISTRIBUTOR= entry in grub, UEFI install just silently fails.

---

### Post by Dennis N on 2015-12-11
> **oldfred said:**
> I have also tried this for my xenial install on sdb :

#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_DISTRIBUTOR="xenial_b"

And I do get a unique entry in UEFI. 
But grub is somewhere hard coded to only use the grub.cfg in /EFI/ubuntu not the Grub in the new entry. There has to be a setting somewhere as other distributions use grub2 and use their own name.

And I saw that if you do not have a GRUB_DISTRIBUTOR= entry in grub, UEFI install just silently fails.

Yes, J.A. Watson reported the same in his ZDNet columns. I would leave all as Ubuntu entries in UEFI menu and not rename. The user would have to know which is which based on the entire entry. But, I boot all my Ubuntu (and other OS installs) on the computer through grub on one of the installed OSes - that way they are easy identify using custom menu entries. 

But now, gamelife's result suggests to me they could all be in the UEFI menu (and not some indirectly booted) even if you don't want to boot them that way.

---

