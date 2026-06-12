---
title: "Ubuntu on HP8640p - bootdevice not found"
date: 2022-06-24
forum: Installation &amp; Upgrades
---

### Post by synedhr on 2022-06-24
Hi everyone

I installed Ubuntu on HP8640p and when I try to boot I get the following error:
Boot Device Not Found
Please install an operating system on your hard disk.
Hard Disk - (3F0)

I can boot from the USB > Try Ubuntu, where I installed and ran boot-repair and got the following report: [https://paste.ubuntu.com/p/ZtyQZr8mVT/](https://paste.ubuntu.com/p/ZtyQZr8mVT/)
Is it safe to just click "Recommended repair"? Or is there another way to fix this?

I should also mention that I am unable to access BIOS settings because some keys (including some of the F keys) on the keyboard don't work. Tried connecting an external USB keyboard but it didn't help - I guess because it's not initialised soon enough. Just mentioning this in case someone suggests changing something in BIOS :)

---

### Post by tea for one on 2022-06-24
You have both a BIOS boot partition and an EFI partion.
Did you try to install more than once?

> **synedhr said:**
>  Or is there another way to fix this?
In order to be more future-proof, I suggest that you re-install (which will tidy up the partitions)
Boot the live session in UEFI mode
Double check with this terminal command
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open gparted and create a GPT (partition table)
Allow the installer to create the necessary partitions.

---

### Post by yancek on 2022-06-24
> I should also mention that I am unable to access BIOS settings because  some keys (including some of the F keys) on the keyboard don't work 

The recommended repair is for you to reboot in UEFI mode after disabling Legacy/CM in the BIOS.  If you can't access the BIOS that won't work.  That's a little confusing since as mentioned in post 2, you have a bios_boot partition as well as an EFI partition so you must have booted Legacy and EFI?  Which release of Ubuntu are you using?  If you could access the BIOS firmware, you might be able to change the boot order to Ubuntu in either UEFI or Legacy.  If you can't do that, it's a pretty serious problem.

---

### Post by sudodus on 2022-06-24
I have my son's old HP Elitebook 8560p, which is very similar to your computer. The internal screen is dead, but I can use it to test that new versions of Ubuntu and community flavours work also in such an old computer.

I can connect an external screen via a 'VGA' cable, and I can connect a keyboard via USB and they work at the grub menu and when running the graphical desktop. I can boot into a USB drive cloned from a current iso file. Right now it is running with Xubuntu Core 22.04 LTS (which is small, so quick and easy to boot). Lubuntu and 'full' Xubuntu work well too in that old computer.

**I tap F9 in order to provide a temporary boot menu** where I can select the drive I want to boot from (and current Ubuntu and Ubuntu family systems can boot both in UEFI mode and BIOS mode (alias CSM alias legacy mode)). Are your F9 and F10 keys working? I must also tap an *internal key* to get to this menu (or to the UEFI/BIOS menus via F10). So the external keyboard does not help us get into those menus. On the other hand, I don't think that it has changed from when you installed Ubuntu. The live system worked and did its work to install, and the installed system should work in the same boot mode whatever it is.

If boot fails you need to wait a while after shutdown until you boot again in order to have everything reset properly.

[hr][/hr]
If this does not work, you can move your internal drive to another computer and install/repair the system there. It is easier, if you remove the other (internal) drives, so that there are only the USB drive, that you work from, and the target drive. Modern Ubuntu desktop and Ubuntu flavour systems are quite portable between PC computers with Intel and AMD CPUs (amd64 architecture). But avoid proprietary drives at this stage, it might reduce the portability.

---

### Post by oldfred on 2022-06-24
You show mount of ESP - efi system partition in fstab, so install based on report is UEFI.

But you have to know whether UEFI settings are for UEFI boot or BIOS/Legacy/CSM boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

you really need function keys, especially with HP.
HP seems to be the only vendor who does not let you update boot order with efibootmgr. Efibootmgr is also used by grub to install the Ubuntu boot entry (which does work) and set Ubuntu as first in UEFI boot order (which does not work).
man efibootmgr

Almost all threads with HP say they have to go into UEFI settings (not UEFI boot menu) and change boot order.
Many with HP have to also update UEFI firmware and if SSD update SSD firmware.

HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios setup

Many other models also:
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)

Do either of these work?
Reboot into UEFI:
sudo systemctl reboot --firmware or
sudo systemctl reboot --firmware-setup

Grub menu also has a boot into firmware entry.
But with install, you normally do not get grub menu and have to press escape between vendor screen & when grub menu normally shows. Often have to try several times as timing is short. And if UEFI fast boot on which is default you may not have any time. Then a full shutdown & drain all power, and "cold" boot may give just enough time as it should then do a normal boot.

Grub menu entry to get into UEFI, this is now a default entry. You also could try just pressing down arrow when starting to boot. I have found it remembers the arrow keys entries right after vendor logo, but I have grub menu always showing.
```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'UEFI Firmware Settings' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}


```

---

### Post by synedhr on 2022-06-25
Thank you all for your replies. After posting here I played with it for a while (before anyone replied), didn't manage to resolve the boot issue so I thought I'd try installing another version of Ubuntu. First I installed version 16 ( just for testing purposes) and it worked fine. Then I installed Ubuntu 20 (clean install again, not just an upgrade) and it also worked. So I decided to just leave Ubuntu 20 there, it was pretty urgent to make it work so I didn't have time to try Ubuntu 22 again.

Not sure what went wrong with that original Ubuntu 22 installation. Prior to that, it was running Windows 10, I just inserted Ubuntu 22 USB and ran the installation using the "Erase disk and install Ubuntu" option.

Thankfully, the F9 key was still working, which came in handy a couple of times, but all the other F's useful for HP were dead (F2, F8, F10..).

---

