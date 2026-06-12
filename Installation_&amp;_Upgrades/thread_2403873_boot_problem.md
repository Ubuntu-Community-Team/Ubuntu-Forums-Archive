---
title: "boot problem"
date: 2018-10-17
forum: Installation &amp; Upgrades
---

### Post by yonasm on 2018-10-17
i successful installed Ubuntu 16.04 on my Lenove Thinkpad laptop, i cant able to boot in on Ubuntu after installation. i tried to reinstall but still the same problem exist. I have already tried boot repair tool but it can't fix the problem. Here i upload the boot information summary for reference purpose. [http://paste.ubuntu.com/p/j6hgS6m9wF/](http://paste.ubuntu.com/p/j6hgS6m9wF/). if some one can help me

---

### Post by yancek on 2018-10-17
What does can't boot mean?  What actually happens?  Do you see a boot menu?  black screen?  data scrolling and then a freeze?

You have a mix of EFI and Legacy, Grub files in your EFI partition as well as in the MBR.  When you boot, do you see a key to use to access boot options (F9, F12?).  WHat options do you see?  Do you have an optoin to boot from EFI file?  Can you find the option suggested in boot repair to select the option to boot from:  /EFI/ubuntu/grubx64.efi

---

### Post by oldfred on 2018-10-17
It looks like you have done multiple installs and multiple entries into UEFI, some using old GUID for ESP and some newer GUID.
Script shows this:
sudo efibootmgr -v
sudo blkid
lsblk -o +PARTUUID /dev/sda
PartUUID is that entry UEFI uses to find ESP's GUID.

Your current ESP:
       /dev/sda1: UUID="09EB-BAE6" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="[COLOR=#ff0000]255bc25f-3d4d-479c-a17b-b1476fae9db1[/COLOR]" 

   Boot0000* ubuntu	HD(1,GPT,[COLOR=#ff0000]849a0ed2-6fa5-4f22-bf4a-d38278ce54e6[/COLOR],0x800,0x100000)/File(EFIubuntushimx64.efi) 

            Boot0006* ubuntu	HD(1,GPT,[COLOR=#ff0000]255bc25f-3d4d-479c-a17b-b1476fae9db1[/COLOR],0x800,0x100000)/File(EFIubuntushimx64.efi) 

    You should delete all the UEFI boot entries with 849.... as old GUID so you only have the newer entries with 255.... to avoid confusion on which ubuntu entry in UEFI boot menu is valid one.

sudo efibootmgr -v        Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

---

