---
title: "Dual ubuntu, broken EFI, does not detect bootable usb"
date: 2022-11-22
forum: Installation &amp; Upgrades
---

### Post by touffaya on 2022-11-22
Hello there,

tl;dr : Bootable usb not detected by EFI, here's Boot Repair info -> [https://paste.ubuntu.com/p/WXSVSX4VPx/](https://paste.ubuntu.com/p/WXSVSX4VPx/)
**Update : solution was to update BIOS with new version from vendor**

I wanted a while ago to install two different versions of Ubuntu alongside each other.
I found some pointers to bypass the different problems with this setup (mainly because of the conflicting entries in GRUB) and I managed to make it work. Sadly, I can't find the sources anymore.

Now, I want to remove one of the instance of Ubuntu and replace it with Windows 10 (how to install Windows after Ubuntu is another problem).
However, neither GRUB nor UEFI are detecting the bootable usb key I prepared (I tried with a bootable w10 or a bootable Ubuntu, which are detected just fine on another computer with w7).

I suspect that it might be because of the setup I had to do to be able to have 2 instances of Ubuntu coexisting.

Here's what I already tried, among other tinkering with EFI and GRUB :
```

sudo mkdir /boot/efi/EFI/usb-key
sudo cp /media/me/usb-key/EFI/boot/* /boot/efi/EFI/usb-key
sudo efibootmgr -c -d /dev/sda -p 1 -L usb-key -l \EFI\usb-key

```

Any idea ?

Thanks !

---

### Post by ubfan1 on 2022-11-22
Ensure grub is installed from the Ubuntu you want to keep, not the one you're deleting.  Check your USBI settings, there may be some USB options.  Vendors + secure boot = weird things, so maybe turn off secure boot.  That really should not be necessary to install Ubuntu, but if the machine refuses to EFI boot a USB in secure boot mode without another settings -- maybe try a supervisor password, or enabling legacy boot, etc.   google for your machine and see what others have done.

---

### Post by oldfred on 2022-11-22
You should be booting USB flash drive directly from UEFI boot menu.
Some UEFI are particular is flash drive is gpt or MBR. It should not matter, but better to use gpt. You are showing MBR(msdos) for flash drive.

External drives boot from /EFI/Boot/bootx64.efi.
That type of entry may also be a fallback hard drive entry for internal drive, but normal UEFI entry refers to /EFI/ubuntu/shimx64.efi.
You have some unusual UEFI entries. Whenever I have tried to rename ubuntu to for example, jammy. It creates a jammy entry, but uses /EFI/ubuntu/grub.cfg to boot in all cases. Something hard coded in Ubuntu's UEFI boot files.

---

### Post by C.S.Cameron on 2022-11-23
You do not need a program to create a USB that is bootable in UEFI.

- Format the 8GB or larger USB as NTFS using GParted, (or Windows Disk Management). Making an internal NTFS partition also works.
- Extract the OS ISO to the NTFS partition using Archive Manager, (or 7-Zip).
- When booting use the applicable F key to open the UEFI menu and then select the USB, or internal, NTFS partition to boot.

UEFI may refer to the partition as other than the ISO name ie USB not Ubuntu.

---

### Post by touffaya on 2022-11-23
Wow, thanks for the quick answers :o

> **ubfan1 said:**
> Ensure grub is installed from the Ubuntu you want to keep
I already formatted the partition where the Ubuntu I want to trash was, my main Ubuntu is booting just fine. Trashed-ubuntu is still suggested by grub but I guess it's due to the files being still present in /boot/efi

> **ubfan1 said:**
> Vendors + secure boot = weird things, so maybe turn off secure boot
I already had to set legacy mode ON + secure boot OFF to make the 2 Ubuntus cohabit.

> **oldfred said:**
> You should be booting USB flash drive directly from UEFI boot menu
I tried booting directly from UEFI boot menu but neither grub (which boots first) nor UEFI (which I access by furiously mashing the escape key) are detecting the key.
The USB entries in efibootmgr are empty and deactivated.

> **oldfred said:**
> You have some unusual UEFI entries
If you're talking about the ubuntu/ubuntu-perso/ubuntu-pro it's due to the tweaking necessary to allow grub to handle two Ubuntu alongside each other. ubuntu is the default pointing to ubuntu-pro, and ubuntu-perso is the 2nd one I trashed (just didn't remove the entry yet).
In the grub list I can see :
- ubuntu (which boots ubuntu-pro)
- advanced settings for ubuntu
- uefi settings
- ubuntu-perso

> **C.S.Cameron said:**
> You do not need a program to create a USB that is bootable in UEFI
I used the Startup Disk Creator of Ubuntu 22, which had worked just fine for me before, up to after manually tweaking UEFI/grub to be able to boot 2 different Ubuntu.

I will try to recreate the bootable key manually and with GPT and I'll post the results, probably tomorrow.
Is there anything that I can try that comes to mind ?

---

### Post by touffaya on 2022-11-24
Here's what I tried :
```

- Created a GPT partition table on the USB drive using GParted
- Formatted the drive as NTFS
- Extracted the Ubuntu ISO (tried with w10 too) to the NTFS partition

```

Both Ubuntu and Windows were bootable on a colleague's computer (from BIOS) but on mine the USB drive doesn't appear at all in the BIOS boot options.
Here's the Repair Boot report with the [manually created bootable USB]("https://paste.ubuntu.com/p/4Nv9m6dsJM/").
Any further idea ?

If nothing else comes to mind I am ready to wipe my computer and reinstall both OSes from scratch but I am not sured how to do that without booting some formatting tool on USB drive...

ps: sorry if I misuse UEFI/BIOS/grub

---

### Post by tea for one on 2022-11-24
> **touffaya said:**
> Both Ubuntu and Windows were bootable on a colleague's computer (from BIOS) but on mine the USB drive doesn't appear at all in the BIOS boot options.
If your bootable USB does not appear in your device boot menu, then I would double-check all the UEFI/BIOS settings i.e. Security, Boot Order etc

I notice from the boot-repair report that you have already booted into Ubuntu 22.04, therefore you can try this:-

Plug in your bootable USB while using Ubuntu 22.04
Open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup
```
This should take you directly to UEFI settings.
Is your bootable USB visible under Devices or UEFI Boot Order (or similar phrase)?

---

### Post by touffaya on 2022-11-24
> **tea for one said:**
> I would double-check all the UEFI/BIOS settings i.e. Security, Boot Order etc

- Secure boot is disabled
- Legacy boot is enabled
- USB is the first entry in UEFI boot and legacy boot
- both UEFI and legacy USB entries do not show the bootable drive
- the bootable drive does not appear in "Boot from file" menu

---

### Post by oldfred on 2022-11-24
UEFI systems use FAT32 for booting.

You can create an Ubuntu live installer by formatting a gpt partition on Flash drive to FAT32 and giving it boot,esp flags. Then extract ISO into the FAT32 partition.

---

### Post by ajgreeny on 2022-11-24
> **touffaya said:**
> - Secure boot is disabled
[COLOR="#FF0000"]- Legacy boot is enabled[/COLOR]
- USB is the first entry in UEFI boot and legacy boot
- both UEFI and legacy USB entries do not show the bootable drive
- the bootable drive does not appear in "Boot from file" menu

That is why the USB does not boot in your system UEFI boot menu.
Disable legacy mode and enable EFI or UEFI; I suspect different systems call it differently, but it's a .long time since I used legacy mode for anything.

---

### Post by touffaya on 2022-11-26
Hello again :)

> **oldfred said:**
> Flash drive to FAT32 and giving it boot,esp flags

Tried that. On the control computer, it doesn't boot directly but is detected in UEFI and can boot from there.
On my problematic computer, the key drive is still not detected in UEFI.

> **ajgreeny said:**
> Disable legacy mode and enable EFI or UEFI

Tried that too. When disabling legacy nothing mode nothing changes : the flash drive does not appear in the boot menu.
And I think that UEFI is always enabled since the first items in the boot menu are UEFI entries.

I am ready to swipe the whole computer from the BIOS in order to start from fresh.
But I am afraid that if I do that, the flash drive will still not be recognized and I'l have no way to reinstall an OS.

---

### Post by tea for one on 2022-11-26
> **touffaya said:**
> I am ready to swipe the whole computer from the BIOS in order to start from fresh.
But I am afraid that if I do that, the flash drive will still not be recognized and I'l have no way to reinstall an OS.
Agreed, that would be a difficult situation.
Did you try my second suggestion from post 7?
> I notice from the boot-repair report that you have already booted into Ubuntu 22.04, therefore you can try this:-
Plug in your bootable USB while using Ubuntu 22.04
Open a terminal and enter:-
```
sudo systemctl reboot --firmware-setup
```
This should take you directly to UEFI settings.
Is your bootable USB visible under Devices or UEFI Boot Order (or similar phrase)? 

---

### Post by touffaya on 2022-11-26
> **tea for one said:**
> Did you try my second suggestion from post 7?

Yes I did, it took me to UEFI settings after reboot. But from there nothing was different than when I accessed UEFI settings either by pressing escape key during boot or by selecting "uefi settings" from grub menu.
Still no detected flash drive.

---

### Post by oldfred on 2022-11-26
Did you ever say what brand/model system this is?Or what motherboard?Some have additions UEFI security setting to prevent USB boot.A few older ones required Legacy on, but you still could boot USB in UEFI mode.Normally the legacy/UEFI or both setting is for the installed system. But some seem to also use it for USB flash drive.

Some older Dell seemed to need Legacy enabled, but set boot to UEFI. Newer systems need legacy turned off.

My old Haswell based Dell. has these settings.Under Advanced: USB enable, On board device, AHCI.Under boot: Secure Boot off, Load legacy, USB boot enabled, Boot mode UEFI.

---

### Post by tea for one on 2022-11-26
This difficulty seems to point towards a UEFI firmware setting.
As you have installed Ubuntu 22.04, can you remember if you updated the UEFI firmware since the successful installation?

---

### Post by touffaya on 2022-11-26
> **tea for one said:**
> This difficulty seems to point towards a UEFI firmware setting.
As you have installed Ubuntu 22.04, can you remember if you updated the UEFI firmware since the successful installation?

WELL !!! I just updated the firmware by downloading the BIN from HP and installing it from a flash drive and lo and behold ! It works.
The version I had was from 2016...
I just don't get why it worked just fine until now.

Thanks a lot everybody for the help !

---

