---
title: "Trouble restoring grub menu after Windows update"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by EricMWalton on 2015-06-14
I built a dual-boot Linux + Windows 7 machine, with a grub boot menu.  This worked fine for about a year, then after a Windows update it only boots into windows. I've tried using boot-repair but I get this message, no matter what settings I tried:

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

I already have a BIOS partition...I believe it's sda1,

Here is the result of the boot-repair disk analysis:

[http://paste.ubuntu.com/11717221/](http://paste.ubuntu.com/11717221/)

Any help would be greatly appreciated!

(P.S. f*** windows.)

---

### Post by oldfred on 2015-06-14
Can you boot Windows?

It looks like you have an UEFI install, but also seem to somehow chosen the ESP - efi system partition as the Ubuntu /boot partition. Now that supposed can work, but I have not seen it, nor know details of how that is supposed to work.

Generally better not to even have a /boot partition with standard desktop. But if you have an encrypted partition (sdb1?) then you have to have a separate /boot.

I do not see a Windows boot in the efi partition. 
And it looks like you may have booted Boot-Repair in BIOS/CSM mode not UEFI mode.

If Windows was BIOS installed it will not work with gpt partitioning which all your drives now are. Your 3TB drive has to be gpt, the others are optional, depending more on how you boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Also you are showing signed copies of kernel. But Windows 7 will  not boot with secure boot on. So better to have secure boot off, CSM/BIOS off or UEFI on as the way you always boot.

---

### Post by EricMWalton on 2015-06-15
Thanks.  

Indeed, /sdb1 is encrypted.  

I can boot windows just fine (it doesn't offer the menu, just boots automatically to Windows).  I guess that means windows was installed via UEFI (apologies, it's been a while)?  I guess then I should convert ubuntu into UEFI mode too?

---

### Post by oldfred on 2015-06-15
You have no boot loaders in the gpt protective MBR for BIOS boot and all the files in the efi partition look like  those that are in a separate /boot partition.
You cannot mount a partition twice, so you cannot have the efi partition and /boot both mounted as the same partition?
 So grub then did not install correctly for UEFI boot. 
In the efi partition is normally a tiny 3 line grub.cfg that is a configfile to link to the full grub.cfg in the /boot folder or partition.
Your grub.cfg then does not show the loading of the kernels from a /boot partition, but from the encrypted  partition which it then cannot load as it is encrypted. Only after grub has loaded then you are asked for the passphase as kernel is loaded.
set root='hd2,gpt1'

Best to create a new /boot partition and move boot files. But you have to not move efi files.
Maybe best to create new /boot partition, and do a full uninstall/reinstall of grub from boot-Repair.
Tell it you have a new /boot partition (you may have to manually add to fstab yourself)
and grub reinstall should then also install the newest kernel.

Be sure to boot Boot-Repair in UEFI boot mode.

---

### Post by EricMWalton on 2015-07-01
I followed the instructions at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), under "Converting Ubuntu into UEFI mode".  This seemed to work fine, as the next time computer booted it showed the boot menu, including working options for Ubuntu and Windows.  However, if I boot into Windows, the next time the computer reboots, the menu's gone again and I have to do it all over again.

Should I consider switching my Ubuntu into BIOS mode?  Or is there some way to change the Windows boot so it doesn't mess with the boot menu?

Thanks again.

---

### Post by oldfred on 2015-07-01
Windows likes to reset itself as default.

There are several things you can try.
Boot-Repair suggests this one, which others have posted works.
But I do not know if you really are booting into Windows and then Windows forces a reboot. UEFI does have a one time boot option that can be used and that may be what Windows does. If you are able to directly boot Ubuntu that would be preferred and there are other workarounds. ( see link in my signature).

 Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

Entry can be shimx64.efi instead of grubx64.efi. Shim is the secure boot version of grub, but works for standard UEFI boot also.

---

### Post by EricMWalton on 2015-07-15
Thanks, oldfred!  I registered grub inside Windows, and now it works fine.  I ran the command you suggested:

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

Thanks, everyone for the help!

---

