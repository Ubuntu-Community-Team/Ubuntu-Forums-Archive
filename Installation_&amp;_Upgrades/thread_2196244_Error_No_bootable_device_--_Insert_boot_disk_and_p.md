---
title: "Error: No bootable device -- Insert boot disk and press any key"
date: 2013-12-28
forum: Installation &amp; Upgrades
---

### Post by croatianlover on 2013-12-28
Hello everyone, I hope you had great holidays :-)

Here is the link of Boot-Repair: [http://paste.ubuntu.com/6652971/](http://paste.ubuntu.com/6652971/)

The story:

I had a working Dualboot of Windows 8 and Mac 10.8 (Hackintosh) on my HP Pavilion DV6.
Then I installed Ubuntu 13.10 and everything worked, but Windows 8 did not. It said it needed to be repaired with the recovery disk.
So I booted in my Windows 8 DVD and then typed some commands (recommended for the problem on the internet) in the CMD.
As I rebooted I get the message: No bootable device, insert boot disk and press any key.
So now I cannot boot in any of the 3 operating systems :(
I also tried to put the Bios to default settings and changed the boot order but nothing helped.
Now I tried to fix it with Boot-Repair, but it did not fix the problem. Still get "No bootable device...".
But it also said: "The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode."
But there is no option in the Bios to change it and I never changed something there, so it should be by default on legacy, and it never was in Efi mode?

I hope you can help me :(

---

### Post by grahammechanical on 2013-12-28
Did you see this?

> chroot /mnt/boot-sav/sda5 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-14-generic
Found initrd image: /boot/initrd.img-3.11.0-14-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found Mac OS X on /dev/sda3
mount: warning: /mnt/boot-sav/sda3 seems to be mounted [COLOR=#AA22FF]read[/COLOR]-only.
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg

Where is Windows 8. It is not being detected by os-proper so you are not getting an option to boot into Windows 8. Please load into Ubuntu and run

```
sudo update-grub
```

and see what is printed on the screen and if there is a reference to Windows 8 loader. Also if you look through that boot repair printout at the point that says this

> [COLOR=#BB4444]### BEGIN /etc/grub.d/30_os-prober ### [/COLOR]

and carry on reading you will see references to the Mac OS but no reference to the Windows OS. This is the section of Grub's configuration file that should show other OSes found. Windows 8 ain't there.

Regards.

---

### Post by croatianlover on 2013-12-28
Hello grahammechanical, and thank you so much, that you help me :)

Right now I cannot boot in any OS. If I power up my laptop I get "No bootable device -- Insert book disk and press any key".
So right now I put my Ubuntu Install DVD in and went to "Try Ubuntu".
I run "sudo update-grub " and get:
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

What now? :(

---

### Post by oldfred on 2013-12-29
You cannot run sudo update-grub on live installer as it cannot write a new grub to the new installer. You have to chroot into system which is what Boot-Repair did.

We cannot help on Hackintosh systems as that is against Code of conduct. We are not allowed to violate other vendors terms of use.

Boot-Repair says you booted in BIOS mode? You have UEFI installs and need to boot in UEFI mode. And Ubuntu is not installed in secure boot mode, so that must be off also. If secure boot is on, then only secure boot systems will boot. 
Boot-Repair has done its rename for buggy UEFI that only boot Windows efi file. If you can boot ubuntu entry from UEFI then you shoud undo rename, so you can boot Windows directly from UEFI menu. Now both ubuntu & Windows entry should take you to grub menu. And you only can boot the renamed/backed up Windows entry from grub menu.

       With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

