---
title: "Ubuntu Update hosed my GRUB"
date: 2022-10-30
forum: Installation &amp; Upgrades
---

### Post by kotoff on 2022-10-30
I have a triple boot system Ubuntu, Manjaro and Fedora. Manjaro is in the number one boot spot but Ubuntu keeps trying to replace it with GRUB updates. I have to keep fixing it with EFIbootmanager. In the last update the boot order was so wacked the standard efibootmanager fix did not work. is it possible to stop changing the grub data on an update or to update with a specification to ignore any grub changes?

---

### Post by grahammechanical on 2022-10-30
In Ubuntu we have a simple means to update Grub and even to re-install it if the bootloader on another OS takes over the boot menu. How is this handled on Manjaro and Fedora? What Linux bootloader do each of these distributions use?

Oh, Manjaro uses Grub. But the method for putting the Manjaro Grub back in change of the bootloader menu is not so simple.

[https://wiki.manjaro.org/index.php/GRUB/Restore_the_GRUB_Bootloader](https://wiki.manjaro.org/index.php/GRUB/Restore_the_GRUB_Bootloader)

Oh, Oh, Fedora uses Grub. Again the method for putting the Fedora Grub back into control of the bootloader menu is not so simple.

When I have more than one install of Linux that uses Grub and an update takes control away from Ubuntu I can load into Ubuntu and run these two commands.

```
sudo update-grub
```

That will run a Grub utility that will detect all OS and compose a boot menu. Then I run a command to re-install the Ubuntu Grub onto the drive.

For BIOS motherboards it would be

```
sudo grub-install /dev/sda
```

If there is only one hard drive. It becomes a bit more complicated if we have a UEFI motherboard and a nvme solid state drive. We need the partition designation of the EFI system partition. On my machine it is

```
sudo grub-install /dev/nvme0np1n1
```

Ubuntu developers have provided these two scripts that make it easy to reconfigure and re-install Grub in Ubuntu.

Another way to do this is to update Ubuntu first. Then Fedora and update Manjaro last. Then if the other two update Grub the Mangaro update of Grub that must surely happen will put the Mangaro Grub back in charge of the boot menu.

Regards

---

### Post by ian-weisser on 2022-10-30
There's a lot more useful information in your AskUbuntu question, and it's a shame you didn't share it here (you still should) while asking folks for their time and effort.

The key element I saw was your statement:  "in most cases taking me out of GPT and putting me in MBR on the Ubuntu root partition." That's the really important information. That's the part that should be up front, in bold. Again, total shame that your question here didn't include that (you can still fix it!).

Simply "stopping" GRUB updates won't work. That would disconnect GRUB from newly-installed kernels, eventually making your Ubuntu system unbootable.

---

