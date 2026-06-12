---
title: "Boot Device Not Found message while installing Ubuntu 16.04 via USB"
date: 2017-08-30
forum: Installation &amp; Upgrades
---

### Post by smittiduss on 2017-08-30
I am a complete noob and have spent the last 6 hours searching a way to fix what I have done! 

- I installed 16.04 using USB using this tutorial [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#5](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#5)
- I did everything exactly how it explains it here; including step 6 "Allocate drive space", where I clicked on the "Erase disk and install Ubuntu".
- Everything seemed to install correctly until after I restarted the computer; step 12.  I was never given a prompt to remove the USB so when it restarted the computer booted from the USB prompting me to try ubuntu, install, etc.  So I restarted the computer again but this time removed the USB and now I'm getting a blue rectangular box that says:

                                                    Boot Device Not Found
                          Please install and operating system on your hard disk. 
                          Hard Disk - (3FO)
                          F2 - System Diagnostics
                          For more information, please visit:
                          [http://www.hp.com./go/techcenter/startup](http://www.hp.com./go/techcenter/startup)

The computer a HP 19 if this helps at all.  This is pushing my patience to the point of using this piece of junk computer for target practice and just go buy my mom a new one! 

TIA for any help

---

### Post by vasa1 on 2017-08-30
OP, I've tried to provide a more descriptive thread title. If you need any changes, you can do so by clicking the "Go Advanced" icon and modifying the title. If you want forum staff to do so, please post your desired thread title.

---

### Post by oldfred on 2017-08-31
Did you install in UEFI boot mode?
Or is UEFI still have UEFI Secure Boot on?

How you boot install media is then how it installs, UEFI or BIOS.

HP is not UEFI dual boot friendly and requires a work around.
It violates UEFI spec that says NOT to use description as part of boot. And for some strange reason the only valid description is "Windows Boot Manager".

If dual booting, we often can set the "fallback" or hard drive entry that still seems to work. That is using /EFI/Boot/bootx6.efi which we create but use a copy of shim. If file exists it probably is a copy of Windows .efi boot file.

If only booting Ubuntu we often change the UEFI entry to read "Windows Boot Manger" but actually boot shimx64.efi. It seems to only check description, not actual file used to boot.

Details in link in my signature and:

Some HP have a way buried pretty deep in UEFI settings:
 HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216) 

Boot-Repair will not copy shimx64.efi to /EFI/Boot/bootx64.efi, so you do not have to do the manual copy. In advanced options check the 'use the standard efi file'. But you boot hard drive or fallback, not ubuntu entry in UEFI.

 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

check current entries:
sudo efibootmgr -v
You can create a new "Windows" entry in UEFI.
IF ESP is not sda1 additional parameters are required. See also
man efibootmgr

 **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1. 
 	sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
Check that entry was added:
sudo efibootmgr -v

---

