---
title: "Ubuntu is making EFI changes during updates"
date: 2021-04-06
forum: Installation &amp; Upgrades
---

### Post by orodoni_le on 2021-04-06
I have a multiple boot setup. My main drive uses GRUB from another distro and this menu has an Ubuntu entry, which lies in a different drive. Ubuntu is NOT my main distro. So far, so good.

When I boot into Ubuntu and do some upgrades, sometimes it modifies the EFI boot order, making Ubuntu the first device, using the EFI of the other drive, and executing the GRUB from Ubuntu. The Ubuntu drive had an EFI partition because it also has Windows 10.

So when I update Ubuntu, sometimes my system boot order is screwed up.

I believe Ubuntu calls ```
efibootmgr
``` as part of the update process, and makes these changes. Is there any way to change this behavior, and keep the boot order as it is? Other than uninstalling [FONT=system]efibootmgr[/FONT]... which probably won't work.

Thanks

---

### Post by tea for one on 2021-04-06
> **orodoni_le said:**
> I have a multiple boot setup. My main drive uses GRUB from another distro and this menu has an Ubuntu entry, which lies in a different drive. Ubuntu is NOT my main distro.

Have you tried to set your [COLOR="#0000FF"]main drive[/COLOR] as first boot priority in your UEFI set up?

What is your main distro?

---

### Post by orodoni_le on 2021-04-06
> **tea for one said:**
>  What is your main distro? 
Arch Linux

> **tea for one said:**
> Have you tried to set your [COLOR="#0000FF"]main drive[/COLOR] as first boot priority in your UEFI set up?


Yes, it is like that. Selected on the firmware. But the boot order can be changed with efibootmgr, which I believe is what Ubuntu update is doing

My laptop has a SATA SSD and an NVME. Windows is installed on the SATA, alongside Ubuntu. Arch is installed on the NVME. The SATA had an EFI partition from Windows install. I created an EFI partition on the NVME to boot Arch and Windows. I then Installed Ubuntu on the SATA, and it created its own Grub and put it on the EFI of the SATA drive (which I did not liked), and set the firmware to boot this before the NVME (which I hated). I fixed the firmware order, and Ubuntu changed it again after the last update. I can either make it stop running efibootmgr, or make a script to reverse the boot order and execute it after every update. Or make an alias for efibootmgr that does nothing.

---

### Post by oldfred on 2021-04-06
All systems, Ubuntu, Windows & I assume any system with grub on a major update re-install boot loader.
And part of the reinstall of boot loader is an update to UEFI boot order.
We see a lot of questions where Windows updates make Windows first.
Or those with multiple installs having issue.

I create another ESP on sdb, now sda as I installed NVMe drive.
That prevents my other Ubuntu installs from overwriting my main working install's /EFI/ubuntu folder. But boot order still is an issue.

So I have to run efibootmgr's -o command to reset order.

You would first type sudo efibootmgr -v to get a list of boot options. Note the number associated with the Ubuntu entry -- for instance, it might be Boot0005. You'd then type sudo efibootmgr -o 5 to make "Ubuntu" (actually GRUB) the default boot loader. (You can specify a set of boot loaders to be tried in order, as in sudo efibootmgr -o 5,1,2 to use 5, then 1 if that fails, then 2 if both 5 and 1 fail.)

Check current order & hex number of each entry:
sudo efibootmgr -v
Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
 sudo efibootmgr -o 0,1,2
see also 
man efibootmgr

---

### Post by orodoni_le on 2021-04-07
> **oldfred said:**
> All systems, Ubuntu, Windows & I assume any system with grub on a major update re-install boot loader.
And part of the reinstall of boot loader is an update to UEFI boot order.

I agree with the first part. New kernel, headers, etc, requires a new linux image. And consequently a re-install of grub (a regeneration of the grub.cfg file)

I don't see why changing the boot order is necessary. The first GRUB install yes, but not the subsequents "re-installs".

I'm used to old linux, partition tables, and setting the boot order on the BIOS. The fact than an OS can make changes on the BIOS boot options is still surprising too me, but that's part of the features of UEFI.

Is there any way to make Ubuntu NOT do this? Or is there an standard way to make the update process (GUI or apt-get) automatically run a script that calls again efibootmgr and resets the boot order to the way I like it?

Thanks

---

### Post by tea for one on 2021-04-07
> **orodoni_le said:**
> Is there any way to make Ubuntu NOT do this? Or is there an standard way to make the update process (GUI or apt-get) automatically run a script that calls again efibootmgr and resets the boot order to the way I like it?

I doubt if there is a **standard way**, but there is probably a way (like most things in the Linux world).

Anyway, as grub is a boot loader rather than a boot manager, you may wish to explore [https://rodsbooks.com/refind/](https://rodsbooks.com/refind/)

I have no need to use this utility myself but it seems to be a versatile application and [COLOR="#0000FF"]may[/COLOR] help you find a solution.

---

### Post by Dennis N on 2021-04-07
> Is there any way to make Ubuntu NOT do this?
Sure. Since in Ubuntu the UEFI boot order is only changed when a grub package is installed or upgraded, hold any grub packages from updating. 

In Ubuntu's terminal:
```
sudo apt-mark hold grub*
```

---

### Post by grahammechanical on 2021-04-09
Could this problem be caused by the Ubuntu Grub being installed on the Arch drive? 

If we have two Linux distributions on two different drives, then the Grub bootloader from each must be install on its own drive. Ubuntu Grub on the Ubuntu drive. Arch Grub on the Arch drive. Then if the boot priority is given to the Arch drive an update to the Ubuntu Grub, such as happens when the Linux kernel is upgraded or Grub itself is reinstalled, should not change the boot priority.

You would need to run

[sudo update-grub[/code]

from Arch for the upgraded Ubuntu kernel to be loaded. 

Regards

---

