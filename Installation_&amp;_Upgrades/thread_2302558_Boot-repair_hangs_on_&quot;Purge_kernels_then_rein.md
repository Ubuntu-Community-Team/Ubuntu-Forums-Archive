---
title: "Boot-repair hangs on &quot;Purge kernels then reinstall last kernel sda1 (ins).&quot;"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by zwarte_piet on 2015-11-11
Hello Ubuntu community!

Our tech department in our company have just installed Windows on a separate drive while there was a Ubuntu 14.04 drive present. This caused Grub to stop working so I made a live USB and started a boot-repair.

But now the boot-repair has been running on "Purge kernels then reinstall last kernel sda1 (ins). This may require several minutes..." for 1,5 hours. 

Is this normal? Or should I restart the process or would that cause irreversible damage to the boot loader?

Help would be appreciated and thanks in advance!

Casper

---

### Post by oldfred on 2015-11-11
Can you just run the Boot-Repair summary report?

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

But if a corporate firewall is preventing you from getting to repository to download kernels, it may prevent you from uploading the report. 

You may be able to boot with Supergrub and install grub to the Ubuntu drive, if older BIOS install. If newer UEFI you may still have ubuntu in ESP unless Windows install totally erase that. 
Best with multiple drives to have each install on separate drives and have its boot loader on that system's drive. But with newer systems and UEFI, every install is usually in the one ESP - efi system partition on drive seen as sda.

---

### Post by zwarte_piet on 2015-11-11
Hey Oldfred,

I have created an Boot-Repair summary report: [http://paste.ubuntu.com/13228032/](http://paste.ubuntu.com/13228032/) .

Is this enough for you to diagnose the problem? 

The firewall shouldn't be an issue here. So I guess that's not the problem.

I was hoping the boot-repair would just fix Grub :(. This is taking me to much time which I should spent on work...

---

### Post by oldfred on 2015-11-11
You have a configuration that I used to think was not possible.
You have Ubuntu on sda as a MBR(msdos) drive.
And Windows on sdb as gpt partitioned booting in UEFI mode. But a Windows BIOS boot in gpt's protective MBR. 

But you have a grub in the MBR of sda for BIOS boot, but also show the mount of the ESP - efi system partition in fstab which indicates it currently is also booting in UEFI mode.

Windows only boots from gpt with UEFI.
Windows only boots with BIOS from a MBR partitioned drive. So BIOS boot loader in sdb for Windows will not work.
But Ubuntu can boot from gpt with either BIOS or UEFI. And some (like your current configuration) have Ubuntu on a MBR partitioned drive, but booting from an ESP on another gpt partitioned drive.

Better to have all drives as gpt if booting Windows as UEFI. And have Ubuntu boot in UEFI mode.
Script did not show efi boot files in sdb2 the ESP. Do you have /EFI/Microsoft and /EFI/ubuntu in that partition? 

Your reinstall of grub may be hanging as grub seems to be hard coded to install to the ESP on sda. But your ESP is on sdb. When I try to install a second copy of Ubuntu on sdb and use the ESP I have created on sdb, the installer says it is installing grub to sdb, but over writes my /EFI/ubuntu on sda. It seems to be hard coded to install to sda drive.

Your UEFI seems to correctly recognize that ESP is on sdb and boots from that.
Have you turned off secure boot, script says it may be on?
And are you booting system with UEFI? BIOS boot entries should not work at all.

If you do not have a lot of data in sda's Ubuntu I would fully backup and convert drive to gpt partitioning and standard UEFI install.

Windows often is happier on sda also, but since UEFI is seeing it on sdb, moving drive to sda would probably require reinstalling boot entires in UEFI with efibootmgr. You can only change drive order by plugging into different ports in motherboard.

---

