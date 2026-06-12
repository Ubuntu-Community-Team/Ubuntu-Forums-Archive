---
title: "no GRUB menu after upgrading 24.04"
date: 2024-09-15
forum: Installation &amp; Upgrades
---

### Post by parsek772 on 2024-09-15
Hi,

I have a dual boot system with Win11. I lost GRUB menu. Mini PC directly goes into Linux. I installed and ran Boot Repair, but it didn't change anything. Here is the report from boor repair: [https://bpa.st/6YPUG](https://bpa.st/6YPUG) . The other thing is I can not enter BIOS. During startup I get a blank screen and no GRUB menu to choose.

Thanks for suggestions

---

### Post by grahammechanical on 2024-09-15
Just to be clear about some things. Can you load into Ubuntu 24.04? If so, run this command in a terminal:

[/code]sudo update-grub[/code]

Watch the printout. Do you see an entry for Windows 11?

When you boot the machine the splash screen should tell you a key to press to enter the UEFI/BIOS utility. Press it, may be repeatedly while the splash screen is showing. On some machines it is ESC. On others it might be F1: F2 or another function key.

Updating Grub may add Windows 11 to the Grub boot menu and that will be sufficient to make Grub appear at every boot.

Regards

---

### Post by tea for one on 2024-09-15
> **parsek772 said:**
> The other thing is I can not enter BIOS.
As you can boot into Ubuntu, you should be able to reach your UEFI settings via a terminal command 
```
sudo systemctl reboot --firmware-setup
```

---

### Post by parsek772 on 2024-09-16
When I did grub-update this is the list and I don't get Win11:
```
[FONT=monospace][COLOR=#000000]Sourcing file `/etc/default/grub' [/COLOR]
Generating grub configuration file ... 
Found linux image: /boot/vmlinuz-6.8.0-44-generic 
Found initrd image: /boot/initrd.img-6.8.0-44-generic 
Found linux image: /boot/vmlinuz-6.2.0-34-generic 
Found initrd image: /boot/initrd.img-6.2.0-34-generic 
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi 
Warning: os-prober will be executed to detect other bootable partitions. 
Its output will be used to detect bootable binaries on them and create new boot entries. 
Adding boot menu entry for UEFI Firmware Settings ... 
done [/FONT]
```[FONT=monospace]

My miniPC enters into BIOS with DEL key, however I press it, it does not go into BIOS. I got black screen and it waits. I have to CTRL+ALT+DEL or hit power button.
[/FONT]

---

### Post by parsek772 on 2024-09-16
It doesn't do anything. It waits on black screen.

---

### Post by parsek772 on 2024-09-16
sudo systemctl reboot --firmware-setup

It doesn't do anything. It waits on black screen.

---

### Post by yancek on 2024-09-16
> I lost GRUB menu 

What does that mean?  How exactly did you lost the Grub menu?    Were you previously able to boot both Ubuntu and windows from the Grub menu?  What changes did you make to software or hardware, if any?  You have the proper EFI files for both Ubuntu and windows so it should boot.  The windows EFI files may be corrupted somehow and that can't be fixed from Linux.  A suggestion, take a look at the /boot/grub/grub.cfg file in Ubuntu and check to see if you have an entry there.  You should have it but if you don't, as root (using sudo with a text editor, put the entry below there and save the change and reboot to test.  If it fails, post back with the results.  If it boots, post back and someone will tell you how to make it permanent.

```
menuentry 'Windows Boot Manager' {
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root 58AC-E2FC
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

---

### Post by parsek772 on 2024-09-16
> What does that mean?  
There is no GRUB menu showing during startup. I have blank screenand there is no PC logo what so ever. Then it boots into Ubuntu automatically.
> How exactly did you lost the Grub menu?
I did an upgrade from LTS22.04.03.
    > Were you previously able to boot both Ubuntu and windows from the Grub menu?
Yes
  > What changes did you make to software or hardware, if any?  
I did an LTS update.
> You have the proper EFI files for both Ubuntu and windows so it should boot.  The windows EFI files may be corrupted somehow and that can't be fixed from Linux.  A suggestion, take a look at the /boot/grub/grub.cfg file in Ubuntu and check to see if you have an entry there.  
Below is the section about windows:
```
[FONT=monospace][COLOR=#000000]### BEGIN /etc/grub.d/30_os-prober ### [/COLOR]
menuentry 'Windows Boot Manager (on /dev/nvme0n1p1)' --class windows --class os $menuentry_id_option 'osprober-efi-58AC-E2FC' { 
        insmod part_gpt 
        insmod fat 
        search --no-floppy --fs-uuid --set=root 58AC-E2FC 
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi 
} 
set timeout_style=menu 
if [ "${timeout}" = 0 ]; then 
  set timeout=10 
fi 
### END /etc/grub.d/30_os-prober ###
[/FONT]
```

> You should have it but if you don't, as root (using sudo with a text editor, put the entry below there and save the change and reboot to test.  If it fails, post back with the results.  If it boots, post back and someone will tell you how to make it permanent.

```
menuentry 'Windows Boot Manager' {
    insmod part_gpt
    insmod fat
    search --no-floppy --fs-uuid --set=root 58AC-E2FC
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
```

Any idea?

---

### Post by nariub on 2024-09-16
Boot ubuntu
use 'lsblk'  to look at the HDs and Partitions
make sure your old "[COLOR=#000000][FONT=monospace]/dev/nvme0n1p1"[/FONT][/COLOR] partition is still there
the new ubuntu doesnt seem to detect existing installations like it used to..   Make sure it didnt overwrite it and then manually add the grub entry back in if you can and try to boot from it.
if its gone, unless you have a backup (clonezilla image or something), it's kinda gone gone..

---

### Post by oldfred on 2024-09-18
Grub only boots working Windows. And if only one system found automatically boots that system.
That also means Windows fast startup which sets hibernation flag must be off. And Windows must not need chkdsk.

Can you boot Windows directly from UEFI boot menu?
If you cannot get to UEFI boot menu that may be because UEFI fast boot is on. That assumes no system changes and immediately boots system as previously configured. Usually full "cold" boot or power down (not "warm reboot")  has system do an update and give just enough time to press correct key to get into UEFI or one time boot.
If you cannot boot Windows then a Windows issues.

If Windows works then Windows updates probably turned fast startup back on. Turn it off or make other Windows repairs & then run another update of grub to add Windows back into grub menu.

---

### Post by parsek772 on 2024-09-18
I understand. I tried multiple times with fully shutdown and restart but no luck getting into boot menu or BIOS. Should I try changing boot order to get into windows using **efibootmgr**? My fear is can not back to ubuntu and stuck in win11.

```
[FONT=monospace][COLOR=#000000]BootCurrent: 0001 [/COLOR]
Timeout: 5 seconds 
BootOrder: 0001,0000,0006,0007 
Boot0000* Windows Boot Manager  HD(1,GPT,03143c98-bbb3-4078-b3e0-4ad4b4adeeb6,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)57494
e444f5753000100000088000000780000004200430044004f0042004a004500430054003d007b00390064006500610038003600320063002d0035006300640064002d003
4006500370030002d0061006300630031002d006600330032006200330034003400640034003700390035007d00000039000100000010000000040000007fff0400 
Boot0001* Ubuntu        HD(1,GPT,03143c98-bbb3-4078-b3e0-4ad4b4adeeb6,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI) 
Boot0006* UEFI: PXE IPv4 Realtek PCIe 2.5GBE Family Controller  PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(8447091f337f,0)/IPv4(0.0.0.00
.0.0.0,0,0)0000424f 
Boot0007* UEFI: PXE IPv6 Realtek PCIe 2.5GBE Family Controller  PciRoot(0x0)/Pci(0x1,0x3)/Pci(0x0,0x0)/MAC(8447091f337f,0)/IPv6([::]:<->
[::]:,0,0)0000424f
[/FONT]
```

---

### Post by oldfred on 2024-09-18
A few, primarily HP, do not support changes with efibootmgr.
You can use live installer, but then have to at least get to UEFI one time boot key to boot it.

Did you do full power down?
And pressing key during initial vendor screen should give you access to UEFI/BIOS.
With laptop than can be difficult as you always have power.
Some have to open system and jumper pins or remove the coin battery on motherboard to reset UEFI/BIOS.
Or some tablets have pin hole reset button.

---

