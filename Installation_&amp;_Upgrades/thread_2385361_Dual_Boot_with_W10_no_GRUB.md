---
title: "Dual Boot with W10 no GRUB"
date: 2018-02-19
forum: Installation &amp; Upgrades
---

### Post by ianlh on 2018-02-19
Hi All,

I have just installed ubuntu-16.04.3-desktop-amd64 onto my HP laptop, installation went OK, but I have no GRUB on the reboot. I can access ubuntu if I go to F9 (boot option) there is an entry for ubuntu UEFI boot manager which when selected allows to boot into ubuntu.

I have tried to do a boot repair, both with a live USB and directly from ubuntu, still no GRUB, just boots directly into W10.

I have the output from boot repair:[URL="http://paste.ubuntu.com/p/4yZxj4wS6w/"]

http://paste.ubuntu.com/p/4yZxj4wS6w[/URL]/

Any help will be greatly appreciated.

---

### Post by oldfred on 2018-02-19
You have an HP.

HP violates UEFI standard that says NOT to use description as part of boot.
So you cannot make Ubuntu entry the default.
Various work arounds.
One you are using with the f8 manually selecting each time you reboot.
Others that seem to work are the fallback or hard drive entry, or rEFInd which may also use fallback entry by default. Some add the ubuntu entry into Windows BCD, which then you boot Windows and choose ubuntu in Windows menu & it reboots using UEFI one time reboot (like your f8 manual selection). Boot-Repair details the BCD entry at end of report.

More details in link in my signature.

Some others, issues are common across many models.
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 
Boot-repair now automatically does copy of shimx64.efi to bootx64.efi as you now have the bkpbootx64.efi which probably is just a copy of Windows .efi file.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 


 Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

---

### Post by ianlh on 2018-02-19
Thank you for the help, i will work through these and see which works

---

### Post by browser18 on 2018-02-19
@ianlh I have the exact same problem. Thanks to you I used F9 to access Ubuntu but I don't have a grub menu either.

@OldFred 
Can you elaborate on HP violates UEFI standard

---

### Post by oldfred on 2018-02-19
Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor. 

And HP ( and others) only boot this entry by description "Windows Boot Manager".
Some users with just an Ubuntu install, add a new entry to UEFI that uses the Windows description but actually boots /EFI/ubuntu/shimx64.efi (same as standard Ubuntu description entry). That that also works. But if dual booting you cannot use that work around. 
So UEFI does not actually check boot file, but uses description in UEFI entry.

To see details in UEFI entries:
sudo efibootmgr -v

---

### Post by ianlh on 2018-02-20
So if I was to completely remove W10 and just run Ubuntu, then I would still need to do some workaround?

---

### Post by oldfred on 2018-02-20
You can then delete current Windows entry and add a new Windows entry that boots Ubuntu/grub2's shim.

 If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

If ESP is not sda1 or NVMe drive the entry needs additional boot parameters.
See link in my signature & this for more details:
man efibootmgr

---

