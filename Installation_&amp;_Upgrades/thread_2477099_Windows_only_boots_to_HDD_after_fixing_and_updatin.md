---
title: "Windows only boots to HDD after fixing and updating to 22.04 on SSD"
date: 2022-07-14
forum: Installation &amp; Upgrades
---

### Post by eguy6 on 2022-07-14
Hello! I decided to upgrade to Ubuntu 22.04 (really Lubuntu base w/Ubuntu DE) after not using the Ubuntu partition on my SSD in a while (months), probably since I upgraded the Win10 on my SSD to Win 11. Along with a couple BIOS tweaks, I used Method 3 of [this tutorial]("https://itsfoss.com/no-grub-windows-linux/") to force GRUB to show up since I couldn't get Ubuntu to boot from Windows bootloader. It worked to get into Ubuntu, but now I'm finding I can't get back into my SSD Windows 11. When I choose the NVMe Windows install, it boots Win10 from the HDD instead of Win11 on the SSD. Not sure what exactly I messed up or if it's just one thing, so I have this pastebin from boot-repair to share and would really appreciate any advice or go-ahead to try the suggested repairs. 

Thank you!

Pastebin: [https://paste.ubuntu.com/p/5GPtYGGfKh/](https://paste.ubuntu.com/p/5GPtYGGfKh/)

---

### Post by grahammechanical on 2022-07-14
May I suggest that you load into Ubuntu and run

```
sudo update-grub
```

Watch the printout and see if it detects the Window 11 installation.

Regards

---

### Post by oldfred on 2022-07-14
You have same UUID, but different GUIDs for your ESP on NVMe & sda drives.
3C34-225D 

Duplicate UUIDs not allowed.

Also how did you create nvme0n1p1?
All partition tools (Windows & Linux) for years have started partitions on 2048 as is your sda.
The start at 63 or maybe 64 goes way back & may interfere with gpt? My old XP with BIOS used 63.

New drives have to have alignment and that is maybe why the posted issue on start at 63 in one place and 64 in the other.

---

### Post by eguy6 on 2022-07-15
[FONT=arial][COLOR=#202124]As far as I remember/know, nvme0n1p1 was originally a clone of the HDD Windows install that I have made my main Windows space. I'm not sure if the shift was from the cloning process, Win11 upgrade, or the recent fix I tried. Does it seem like a good idea to try boot-repair then or should I try something else?

And in reply to [/COLOR]grahammechanical, here is the output of update-grub. It looks like it sees Windows, but has a problem with it, not sure if related to the pastebin output.
[/FONT]```
Sourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'
Sourcing file `/etc/default/grub.d/lubuntu-grub-theme.cfg'
Generating grub configuration file ...
Found theme: /usr/share/grub/themes/lubuntu-grub-theme/theme.txt
Found linux image: /boot/vmlinuz-5.15.0-41-generic
Found initrd image: /boot/initrd.img-5.15.0-41-generic
Found linux image: /boot/vmlinuz-5.13.0-52-generic
Found initrd image: /boot/initrd.img-5.13.0-52-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/efi/Microsoft/Boot/bootmgfw.efi
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done

```

---

### Post by oldfred on 2022-07-15
Grub only boots working Windows with UEFI Secure boot off.
If Windows update turns fast start up back on that sets hibernation flag and prevents grub from booting Windows.
You should be able to directly boot Windows from UEFI boot menu & turn off fast start up or make other repairs.

---

### Post by eguy6 on 2022-07-21
Thank you all for the insight! By changing the bootmgr path from Ubuntu/GRUB back to Windows, I am again able to get into the Win11 session and divert the BIOS from the splash screen if I want to go to Ubuntu, which is less frequent. Still not sure exactly why I couldn't reach Ubuntu before I changed it, but it works now and I'll be back if it stops working down the road.

---

