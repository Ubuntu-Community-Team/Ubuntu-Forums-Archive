---
title: "Grub installation failed on HP Laptop"
date: 2018-02-23
forum: Installation &amp; Upgrades
---

### Post by uzumakifahim on 2018-02-23
I'm trying to install Ubuntu 17.10 on a HP laptop (Model:HP14bs547TU) as  dual boot with Windows 10. Every time installation fails at the grub  installation stage. It is giving me the following message

"The 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot."

I've never faced this kind of issue previously. How can I overcome it? Please help.
  Thanks in advance.

---

### Post by rouvenster on 2018-02-24
Oh, I thing this is the secure boot thing. You have to disable secure boot on your BIOS and probably put a file in /EFI/BOOT
You have to check if the EFI should be 32 or 64 bit (most probably 64).

---

### Post by panditax on 2018-02-24
Same problem here, HP laptop as well: [https://ubuntuforums.org/showthread.php?t=2385686](https://ubuntuforums.org/showthread.php?t=2385686)
I can't find solution :/
Yesterday I installed grub by hand after Ubuntu installator failed. It was successful, but after reboot I see "No bootable devices"....

---

### Post by oldfred on 2018-02-24
HP is not particularly friendly to dual boot or Linux installs. It  violates UEFI standard that says not to use description as part of UEFI  boot. And only valid description is "Windows Boot Manger". But various  work arounds depending on configuration.

May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 

    
Copy shimx64.efi to /EFI/Boot/bootx64.efi
 [http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others workarounds:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)

Other HP, issues often common across models of same brand.
       
 Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[URL="https://ubuntuforums.org/showthread.php?t=2376227"]https://ubuntuforums.org/showthread.php?t=2376227
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="https://ubuntuforums.org/showthread.php?t=2376227"]
[/URL]

---

### Post by panditax on 2018-02-25
Thanks for your answer Oldred. I'll test it asap and let know if it was useful. My laptop is HP G3 840.

Additionally I have just tried to install Ubuntu without encrypting (UEFI + manual LVM) and it was successful.

---

### Post by oldfred on 2018-02-25
Were you able to directly boot the Ubuntu UEFI entry?
Or did you install in the old BIOS boot mode.
Or has HP modified UEFI to allow others to boot?

---

### Post by panditax on 2018-02-25
Yes, I was able to directly boot the Ubuntu UEFI entry. I don't understand your last question. In BIOS settings I can set **Legacy Boot Enabled/Disabled** and **Secure Boot Enabled/Disabled**. In my case I set it to **disabled/disabled**. Then in boot menu I can choose "UEFI-UbuntuUSB "/ "boot from file". After installation _without_ encryption I had "UEFI - Ubuntu" boot option and it worked well. 

With encryption, when I tried to repair GRUB by hand, it was successful, but after reboot in boot menu I had just my "UEFI-SATA Disk" option (and boot from file but I think its irrelevant). After having it chosen, it ended up with black screen with "No bootable devices found".

Tomorrow I'll provide report from boot repair utility and some screenshots from efibootmgr after repairing grub.

---

### Post by oldfred on 2018-02-25
With encryption, and Boot-Repair or manually installing grub you have to mount ESP - efi system partition, /boot & unencrypted / before grub will correctly update. Boot-Repair will do most of that but not sure about mounting unencrypted /. Somewhere you have to give passphase.

How you boot install media UEFI or BIOS is then how it installs.
Most systems with Legacy/BIOS/CSM on, only boot in that mode. But booting flash drive installer usually still has both options.
But some systems mix up UEFI and UEFI Secure Boot.

My desktop has Secure boot as "Windows" or "Other" and fine print says use "Other" if installing Windows 7 UEFI as it does not support Secure Boot. So that is really Secure Boot on/off setting.

---

### Post by panditax on 2018-02-26
I boot install media in UEFI. I do everyting in UEFI, no doubts.

Boot-Repair failed. I mean it says boot is successfully repaired, but after reboot I see "No bootable devices found".

Manually repairing grub:
> 
cryptsetup luksOpen /dev/sda2 sda2_crypt
vgchange -ay system
mount /dev/mapper/system-root /mnt
mount /dev/sda1 /mnt/boot #sda1 is unencrypted EFI System partition
mount -t proc proc /mnt/proc
mount -t sysfs sys /mnt/dev
mount -o bind /dev /mnt /dev
mount -t devpts pts /mnt/dev/pts
modprobe efivarfs
chroot /mnt
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck
update-grub


It results with:
> 
For grub-install:
Installing for x86_64-efi platform.
Installation finished. No error reported.

For update-grub:
Generating grub configuration file ...
Adding boot menu entry for EFI firmware configuration.
done


Then, when I run efibootmgr, I can see entry "Boot000A* ubuntu", but after exiting from /mnt and running efibootmgr I cant see it anymore. After reboot - black screen with "No bootable devices found".

---

### Post by oldfred on 2018-02-26
Back to post #4.
HP not dual boot friendly. It uses description and only valid description is "Windows Boot Manager". That is a violation of UEFI standard that says not to use description.
So with HP we have to do work arounds.

If only booting Ubuntu one work around is to use the required description but ubuntu/grub's shim file.

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Other work arounds in link in my signature and links in post #4.

---

### Post by panditax on 2018-03-02
Forget about Windows and dual boot for a moment, please. For now I have just two partitions: EFI+encrypted LVM.
My point is that **I can't boot Ubuntu**, and I didn't find sufficient satisfactory answer in post #4.

I'll describe the problem once again here.
CLEAN DISK SSD. Trying to install Ubuntu in UEFI mode, with LUKS encrypted LVM partiton (luks and lvm made by hand, installer doesn't provide such option) - it failes with error like in post #1.
Partitions:
- /dev/sda1 - 1G ESP (unencrypted)
- /dev/sda2 - 400G, Linux LVM, LUKS encrypted, LVM: root,home,swap
Installation without LUKS in this scenario is successful. But I want encryption as well..

I'm searching the Internet, docs, trying everything and nothing works. That's why I post my problem here.

---

### Post by oldfred on 2018-03-02
I do not know LVM, but  the ones I have seen with encryption all have a separate /boot partition.
There may be ways to have kernel in ESP which is not encrypted or load a grub mod file to unencrypt as booting so it can see into (and have you give passphase).
But normally it seems that /boot is unencrypted.

And then if not dual booting, this is one work around on HPs.
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by panditax on 2018-03-02
I solved this by myself a few minutes ago, with boot encrypted. Will provide solution here soon, because now I have to install Windows.. :D

---

### Post by panditax on 2018-03-05
Meanwhile, seeking for a solution to double pass check, I found a script, which is doing everything I made by hand previously: [https://github.com/rdkr/lvm-on-luks](https://github.com/rdkr/lvm-on-luks)
Look at this: > "I found using this method that the bootloader installation failed  every time (select continue without bootloader) and sometimes crashed,  but this doesn't matter as the script must re-install GRUB with modified  config anyway."

Why I didn't find it earlier... ehh. I think it's useful enough to pin it somewhere on forum. It would have saved me a lot of time.

---

