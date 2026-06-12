---
title: "Grub incorrectly installed after reinstall and Boot Repair not repairing."
date: 2015-09-28
forum: Installation &amp; Upgrades
---

### Post by Flyer on 2015-09-28
Hi,
I have been running a dual boot Ubuntu 14.04.10 and Windows 8. I. I have done a reinstall to upgrade to 14.04.03 using the reinstall option on the installer.
Grub has not correctly reinstalled and Boot Repair has not fixed the problem. It has produced the following info:
[http://paste.Ubuntu.com/12572295](http://paste.Ubuntu.com/12572295).

Would be very grateful for any assistance.

Thanks

---

### Post by ajgreeny on 2015-09-28
Firstly, you did not need to reinstall to get from 14.04.1 to 14.04.3; you could have made that change much more simply by running normal updates and also installing the appropriate packages for the hardware-enablement-stack upgrade.

However, having now reinstalled Ubuntu it seems you used legacy BIOS settings rather than UEFI, which it was previously, and must be now in order to allow both OSs to boot.

I am no expert in dual booting but it looks as if the default boot-repair, mentioned at the bottom of your report, can put this right and remove grub-pc and replace with grub-efi.
> The default repair of the Boot-Repair utility would purge (in order to fix packages sign-grub fix executable) and reinstall the grub-efi-amd64-signed of sda9, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file
Perhaps wait for more expert responses before taking the plunge with this, and do not do anything in a rush until you know what is needed.

---

### Post by oldfred on 2015-09-28
I do see grub-pc (BIOS) in gpt drive's protective MBR. So at some point you did install in BIOS boot mode.
But fstab shows a mount of /boot/efi, so it looks like current install is set for UEFI boot. And you also have the ubuntu entries in the efibootmgr list from your UEFI.

If you go into UEFI and boot in UEFI mode you should get both Windows & two ubuntu options. One is grub for UEFI and the other shim for UEFI with secure boot on. You do have to make sure UEFI is on, and if you want to dual boot from grub menu have secure boot off, but UEFI on and CSM/BIOS  off.

---

### Post by Flyer on 2015-09-28
Hi,
Thanks for your responses.
I did actually try updating to the newer version but it failed so I tried the reinstall option.

In the Bios under  boot configuration I only have:
Fast Boot  (disabled)
Launch CSM (disabled)

Where do I make UEFI on?

On starting up and pressing ESC (and in Bios) I get a boot order listing of Windows and 2 Ubuntu options which look the same. I have tried both but still no luck.

Thanks again

---

### Post by Bucky Ball on 2015-09-28
> **Flyer said:**
> ... 2 Ubuntu options which look the same. I have tried both but still no luck.



So what does happen when you try the first of these entries (the second would probably be the recovery mode)?

---

### Post by oldfred on 2015-09-28
```
 Boot0000* ubuntu	HD(1,800,96000,ed04135b-bd79-4c7c-b3b5-b0f9c2fe6826)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0004* ubuntu	HD(1,800,96000,ed04135b-bd79-4c7c-b3b5-b0f9c2fe6826)File(EFIUbuntu[COLOR=#ff0000]grubx64.efi[/COLOR])


```

Your two entries are grub & shim. Shim is the secure boot version of grub and should work whether secure boot is on or not.

If you have CSM off, then you should have UEFI on. And then with UEFI, you have secure boot on or off.

What brand/model system? What video card.
Did you have to run any of the work arounds to get ubuntu to boot. Many vendors modify UEFI (not  per UEFI spec) to use description as part of boot and only valid description is "Windows". Then we have to do a work around.

---

### Post by Flyer on 2015-09-28
Hi,
Ubuntu 14.04.10 was working fine as a dual boot with Windows. Grub gave me the choice of which system to boot.

When I choose either of the 2 Ubuntu options now I get:

' Minimal Bash-like  line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>'

I have no idea what all that means!

---

### Post by oldfred on 2015-09-28
Run Boot-Repair and reinstall grub in UEFI boot mode.

You may still be booting the MBR copy of grub or the copy in UEFI is from the old install and then will not work.

Then be sure to boot in UEFI boot mode.

---

### Post by Flyer on 2015-09-29
Hi,
I ran boot repair in UEFI mode. It purges grub and blocks at the reinstall of grub after I have copied and pasted the reinstall command.
I noted that Boot Repair was trying to reinstall to sd9 but using Gparted I see that there is a partition sd6 which shows 'bios-grub'.
Is that significant?

---

### Post by oldfred on 2015-09-29
The bios_grub is for the BIOS boot version of grub when installed to the MBR and using gpt partitioning. You do not need or use it with UEFI boot. I actually have both ESP & bios_grub on all gpt drives(including full install flash drives), but only use ESP on new system. I used gpt & bios_grub with my older BIOS system.

With BIOS on MBR partitions, there is space after the MBR where core.img is stored. With gpt that space does not exist so grub needs the bios_grub partition. Windows system reserved partition with gpt is for the same reason as it also will use the space after the MBR with BIOS/MBR systems.

When you say it blocks on the reinstall of grub, what is blocked. 
Is Internet working? Or is ESP, the FAT32 partition not being seen correctly?

---

### Post by Flyer on 2015-09-29
When I copy and paste the reinstall instruction it starts the process and then just stops. It does this every time I have tried. It is not a problem of internet connection.

---

### Post by oldfred on 2015-09-29
Can you post what you have done & where it stops?

---

### Post by Flyer on 2015-10-03
I am devoted to my Ubuntu which I wanted up and running asap so I did another install using the "something else" option with new partitions etc. It all works now perfectly. 
Many thanks oldfred and others for your time and help.

---

