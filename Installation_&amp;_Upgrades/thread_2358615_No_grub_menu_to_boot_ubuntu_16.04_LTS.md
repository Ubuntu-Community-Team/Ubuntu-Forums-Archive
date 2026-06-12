---
title: "No grub menu to boot ubuntu 16.04 LTS"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by etu-iseahz on 2017-04-15
I have installed ubuntu 16.04 lts on my computer. This one came with a pre-installed windows 8 upgraded to windows 10.
It has UEFI and I have followed exactly the steps in the installation tutorial.
Secure boot , quick qnd rapid boot are all disabled.

However, the grub loader does not show at boot and windows opens automatically.

I tried boot repair with recommended repair to no avail.

Here is the pastebin I got from it.
[URL="http://paste2.org/XhhnBat8"]http://paste2.org/XhhnBat8
[/URL]I am noticing that in it there is  *No boot loader is installed in the MBR of /dev/sda.* despite the fact I left it to be installed there and even run the repair once.


The PC is lenovo Ideacentre K410 64bits with Intel core processor I7

---

### Post by oldfred on 2017-04-15
The MBR is used for the 35 year old BIOS/CSM/Legacy boot. If UEFI boot (which you want) your MBR should not have a boot loader.

These are your boot files in sda2, your ESP - efi system partition:
>                        /EFI/ubuntu/fbx64.efi /EFI/ubuntu/fwupx64.efi 

                            /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                            /EFI/ubuntu/shimx64.efi

What model Lenovo?
It looks like you ran Boot-Repair and it copied shimx64.efi to bootx64.efi as it created the bkp backup version which only Boot-Repair creates.
> /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi

The bootx64.efi is a backup/fallback or direct hard drive boot entry.  With most systems it is just a copy of Windows .efi boot file. If we make it a copy of grub2's shimx64.efi then you can often boot the hard drive entry. Many UEFI already have an UEFI hard drive boot entry, some need one added.

       You can add your hard drive entry to boot fallback file:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition, example for sda2 
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sda -p 2 

Mine was sda, and ESP is sda1, so I used -p 1 to get this:
sudo efibootmgr -v
Boot0001* UEFI hard drive    HD(1,GPT,c371fe4e-a6db-4c46-b056-a4eea609f81d,0x800,0x639c000)/File(\EFI\Boot\bootx64.efi) 

Then see is your UEFI will let you boot the UEFI hard drive entry.

---

### Post by etu-iseahz on 2017-04-15
The model is lenovo K410

The instructions for the efibootmanager, I do them from a terminal in the live CD, right?
Because I have no access to the installed ubuntu.

---

### Post by oldfred on 2017-04-15
You can update UEFI with efibootmgr from live installer.

See also:
man efibootmgr

---

### Post by etu-iseahz on 2017-04-15
I did as instructed but there was no change at boot.

---

### Post by etu-iseahz on 2017-04-15
I found a solution which worked in another forum.
It was to open a terminal from windows as administrator and write 

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

--> operation done

---

### Post by oldfred on 2017-04-15
That also works for many. It also is one alternative posted at bottom of Boot-Repair's Summary Report.
You are just booting into Windows & Windows reboots using UEFI one time reboot option.

---

