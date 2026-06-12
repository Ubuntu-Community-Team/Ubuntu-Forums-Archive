---
title: "Ubuntu installation on Sony Vaio"
date: 2015-10-10
forum: Installation &amp; Upgrades
---

### Post by Clavicus_Vile on 2015-10-10
I boot the laptop using USB with Ubuntu, load it from the USB, install Ubuntu. It was clean installation, so all the files were erased. The installation went smoothly. After restart I received the message that "VAIO failed to start Windows" with no other options. 

I installed Ubuntu in UEFI mode. I tried to run "boot-repair" using the "recommended repair", but it did not help. The summary recorded by the boot-repair can be found following the link: [http://paste.ubuntu.com/12743741/](http://paste.ubuntu.com/12743741/)

Please give me a hint what I can try to run the Ubuntu.

---

### Post by oldfred on 2015-10-11
Sony modifies UEFI to include description and only valid description is "Windows". That is not per UEFI standard.
Back up entire efi partition. It is not large and should fit on any other device you have.

Since you only have Ubuntu, you can rename ubuntu entry to be Windows but really boot shimx64.efi.

       Check entry is there.
sudo efibootmgr -v 

   Delete entry change XXXX to current Windows which was before 0005 in pastebin.
sudo efibootmgr -b XXXX -B
OR:

            # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

You may need to delete the /EFI/Microsoft folder also:

This assumes your ESP is sda1, which yours is:
       sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Other work arounds:
       [URL="http://ubuntuforums.org/showthread.php?t=2234019"]http://ubuntuforums.org/showthread.php?t=2234019
[/URL]
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Rename bootx64.efi
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair)[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by Clavicus_Vile on 2015-10-11
**oldfriend**, Thank you for the response. I did everything according to your instructions, but still cannot run Ubuntu.
 
1. I loaded ubuntu from the USB in the 'try ubuntu without installation mode"
2. I installed the boot repair and ran the "recommended repair"
3. I look at the entries by running "sudo efibootmgr -v" and indeed 0005 entry is:
Boot0005* Windows Boot Manager HD(1,800,100000,e732f686-97f8-4443-8185-214b6d98228a)File(EFIMicrosoftBootbootmgfw.efi)

So, I deleted it as you recommended by running "efibootmgr -b 0005 -B". The entry disappears from the list of entries. There are two entries left:
Boot0000* ubuntu HD(1,800,100000,e732f686-97f8-4443-8185-214b6d98228a)File(EFIubuntushimx64.efi)
Boot0006* UEFI: JetFlashTranscend 16GB 8.07 ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(2,0)HD(1,2000,1dea000,00000000)..BO
(see the report [http://paste.ubuntu.com/12751384/](http://paste.ubuntu.com/12751384/))

However, when I restart the laptop it shows me the same message again: "VAIO failed to start Windows". When I again run the ubuntu from the USB and install the boot-repair, all the entries are again there including:
Boot0005* Windows Boot Manager HD(1,800,100000,321f0502-1640-49e2-900c-0c703226377e)File(EFIBootbootx64.efi)

When I delete the entry 0005 again and run "sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" (not sure what does it do exactly), the "Windows Boot Manager" entry returns as Boot0001.

So, I am not sure how can I delete the /EFI/Microsoft folder. I found the folder /media/ubuntu/1eb5c944-29af-493e-b338-9c89a4ce2649/boot/efi/ but it is empty.

I also tried to rename grub64.efi to bootx64.efi
sudo mount /dev/sda1 /mnt
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi
(see the report [http://paste.ubuntu.com/12751940/](http://paste.ubuntu.com/12751940/))
When I restart the computer it still does not see Ubuntu and shows the same message "VAIO failed to start Windows". 

Please let me know what else I can do to run Ubuntu on my Sony Vaio.

---

### Post by oldfred on 2015-10-11
You want to use this to create a "Windows boot entry". Then Sony will think it is booting Windows description, but actually boots shim or grub's secure boot version.

sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi

Then boot Windows entry in UEFI boot menu or one time boot key.

---

