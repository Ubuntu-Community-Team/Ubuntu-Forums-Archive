---
title: "Dual install Win 10 + ubuntu 18.04, boots directly into windows"
date: 2019-01-02
forum: Installation &amp; Upgrades
---

### Post by andreberg on 2019-01-02
Hi there,

I have been using ubuntu since the early versions (over ten years) on an in and out basis and mostly to learn about it, as due to work constraints I need to use Excel. However I usually installed it as a single standing OS on an older machine or had no issues installing alongside windows.

I recently installed ubuntu 18.04 in a brand new HP Pavillion (bc-003la) which came in with Win 10 Home. After three tries, the machine still boots directly into windows.

Every time I finish the install and reboot, the machine says an error happened, enters into repair mode (sponsored by Microsoft), then reboots and boots windows directly.

If I hit the "esc" key and then "F9" and enter into the boot menu I can see windows and ubuntu standing there. Windows is the first in the line. Bios does not allow to change boot order. Upgraded Bios to the latest available with no luck.

Have read extensively about dual boot in UEFI machines in Ubuntu forums, askubuntu and other linux distros, and about some brands not allowing dual boot on purpose, followed install instructions without success. Bios has the option to allow for a UEFI boot or a legacy boot. I disabled legacy boot and disabled Secure Boot before installing ubuntu. Also disabled Fast Boot on windows. No success.

I can boot Ubuntu without any issues if I access the boot menu in the Bios. The OS works flaulessly. I even updated the OS completely, installed NVIDIA drivers and connected to my wifi network.

Haven't tried tinkering with the EFI boot files as I have not figured out how to access them yet (not an advanced user).

The machine comes with an EFI boot partition and a rescue partition for windows.

If you ask for information about the laptop i can provide as long as you tell me how to.

Thanks for your help.

---

### Post by oldfred on 2019-01-02
HP has not been the most friendly to dual boot.
Some with newer UEFI have said from within UEFI and boot tab, you could change boot order.
But our normal commands using efibootmgr (which grub uses when installing), will not change or change permanently the boot order.

Others use the work around of booting the fallback or hard drive entry. It uses /EFI/Boot/bootx64.efi with original will be a copy of Windows boot file. We used to have to manually copy shimx64.efi (and maybe some additional files, if errors), but now Boot-Repair will do that copy, if you run it and its suggested fix.

       Just to confirm install is otherwise normal.
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

    
       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309) 
            HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook) 
    
Older manually copy of files, but Boot-Repair should do this for you.
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

---

### Post by yancek on 2019-01-02
Instead of the F9 key for Boot Options, after hitting the Esc key on boot, select the F10 key and go to the System Configuration tab and on that BIOS page, you scroll down to boot options and you should be able to change by using the F5/F6 keys.

---

### Post by andreberg on 2019-01-02
Thanks for that! Must have skipped the option after the Bios udpdate. Now the system boots into Grub.

Oldfred, thanks for your input. It seems the issue was sitting between the chair and the keyboard...

¿Is there a way to edit the boot loader so as for Windows to be the default option? Currently it is Ubuntu. I remember having done that in the past, but with non-UEFI systems.

Thanks once more!

---

### Post by andreberg on 2019-01-02
Solved it. Found the grub.cfg file and followed instructions on the info grub menu about it's configuration.

Thanks once more!

André

---

### Post by yancek on 2019-01-02
>  Found the grub.cfg file and followed instructions on the info grub menu about it's configuration.

Not sure what you did here but if you did modify grub.cfg it will be changed every time you update Grub.  If you edited the /etc/default/grub file to make the change and then ran update-grub, it should be good.

---

### Post by andreberg on 2019-01-03
Hi yancek, what I did is edit the /etc/default/grub file. The grub.cfg file got me started on the info grub menu about its configuration.

Thanks for your reply.

---

