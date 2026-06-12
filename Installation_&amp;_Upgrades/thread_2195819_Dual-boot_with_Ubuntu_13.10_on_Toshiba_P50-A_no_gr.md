---
title: "Dual-boot with Ubuntu 13.10 on Toshiba P50-A no grub menu"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by timshel862 on 2013-12-26
Hi!

I have a Toshiba P50-A with Windows 8.1 self installed, and later with Ubuntu 13.10 overcoming all installation problems, **both in UEFI mode**. I have **Secure Boot on**, otherwise it wasn't able to enter the USB live session (buggy that it only boots that way), and have run boot-repair a couple of times without a satisfactory result.

If I just follow the recommended repair in boot-repair, I get a system that directly boots to Windows, after which by pressing reboot option & shift key and entering the Windows recovery menu, I can select boot from a different source and select Ubuntu system. After doing that, Windows shuts off, a Toshiba screen appears and it continues to grub, and later to Ubuntu, which works quite well. Here is the output URL from boot-repair with the recommended option:
[http://paste.ubuntu.com/6641023/](http://paste.ubuntu.com/6641023/)

If on boot-repair I select the option to backup & rename windows EFI files, I get a system that gives the following error when booting:
> Checking Media Presence......
No media present.......
and after 5/10 seconds it decides to show grub menu, and both systems boot fine. The boot-repair URL entry after selecting this option is the following:
[http://paste.ubuntu.com/6640942/](http://paste.ubuntu.com/6640942/)


So in the first option I have to run through windows every time I want to boot Ubuntu, and in the second option, the system takes like 20s just to show the grub menu after showing a bunch of errors. I was hopping I can manage better boot options than this...

Any ideas, similar cases you know of??

What bothers me also, is the boot-repair summary message in the previous links:
>  Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector      616448 of the same hard drive for core.img, but core.img can not be found      at this location.
> Boot sector info:  According to the info in the boot sector, sda2 starts                         at sector 0. But according to the info from fdisk,                         sda2 starts at sector 616448.

Thank you for the help.

PD: I guess it is not important, but I have selected No Raid present when asked by boot-repair, and also the linux partitioning is based on LVM.

---

### Post by grahammechanical on 2013-12-26
Yes, we all would like a trouble free installation process when installing Linux on a machine with Windows already installed. It is not a buggy installer that is the problem but the complications that Microsoft and the OEMs create.

If you installed Windows 8 with secure boot on then you would need to run the live session with secure boot on and install Ubuntu with secure boot on.  This is my thinking. That is the complication that secure boot creates. We are not supposed to turn secure boot off and then install unverified (by Microsoft) code. But Ubuntu for more than a year has a Linux kernel that will be accepted by a motherboard with secure boot enabled. In fact Ubuntu was the first Linux distribution to be able to do this.

I have never selected the LVM option when installing Ubuntu. And I do many installs. But I have no need. I was wondering if the delay in booting is caused by the need for the boot loader to do certain checks because you have an LVM. I have no experience of this so I cannot say.

Try installing Windows 8 after installing Ubuntu. I did this the other month with a developer preview edition of Windows 8 and Windows does not even notice a Ubuntu install. Now how is that for buggy? No. It is just Microsoft seeing its own little software island as the universe where no other OS exists. Mind you I am thankful that the Microsoft installer did behave and install Windows 8 in the partition I indicated and not take over the whole disk. Thankful for small mercies.

Regards.

---

### Post by ubfan1 on 2013-12-26
I don't know about a LVM setup, but you have grub installed both to the efi boot partition and to the Master Boot Block (incomplete).  Some machines with both might default to the (incomplete) MBR boot.  Not sure about Toshiba.   A Satellite S855 5378 has bug #1091464, which prevents it from chainloading Windows (even when the grub commands have been fixed), so you might wind up still having to use the efi boot selection for Windows.

---

### Post by timshel862 on 2013-12-26
@[[COLOR=#000000]grahammechanical[/COLOR]]("http://ubuntuforums.org/member.php?u=1087323"): I have the impression the buggy software is the Toshiba Bios, which disregards any configuration boot-repair sets, and just keeps looking after the windows EFI files, no mattering the grub ones. But what surprises me is why after renaming the files, it says no media present, and then carries on to grub (and both Ubuntu and Windows run normally from there).
Regarding LVM partition I doubt it is related, because before that I tried with logical partitions (ext4) and got the same results as I am getting now (same wait when renaming windows efi file). Also, the Ubuntu installation is done with secure boot on always, because the bios would not let me start Ubuntu through live USB with it deactivated (neither from the HDD after installation). Finally, I would rather not reinstall the OS's again, as I'm already working with them. Let's just say, one of the things I tried before was to install Ubuntu all alone, and I wasn't able to boot (although I was more inexpierienced at the time with all these EFI and secure boot things).

@ubfan1: In my case the problem is the grub menu only shows after restarting from windows, not that the grub menu does not chainload Windows. So I don't think the problem is related with a bug from grub, other than it may install incorrectly as you said. Do you know how could I fix it being badly installed on the Master Boot Block? Or about the other summary error messages from boot-repair?

Finally, I have started a Toshiba support thread too, in case they can help: [http://forums.toshiba.com/t5/Computer-Troubleshooting/Installing-Ubuntu-together-with-Windows-in-a-Toshiba-P50-A/td-p/514931](http://forums.toshiba.com/t5/Computer-Troubleshooting/Installing-Ubuntu-together-with-Windows-in-a-Toshiba-P50-A/td-p/514931)

Thank you for your help.

---

### Post by oldfred on 2013-12-26
Grub has add in modules for special devices. It shows all those mod files in /boot/grub. But since directly booting into LVM you may need that mod file added.

Someone else with issues was able to manually boot, and then found they could create a grub.cfg in the efi partition to call the grub.cfg in the install. You may need to do something similar.

His was gpt8 where grub & kernels were. If added mod files need you need them but have not seen anyone copy those into efi and see if it works. If you want to experiment you can try that.

       configfile (hd0,gpt8)/boot/grub/grub.cfg


 found that putting grub.cfg into /EFI/ubuntu works, even when grubx64.efi is in /EFI/Boot

---

