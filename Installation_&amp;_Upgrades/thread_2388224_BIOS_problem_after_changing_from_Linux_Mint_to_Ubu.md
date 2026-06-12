---
title: "BIOS problem after changing from Linux Mint to Ubuntu."
date: 2018-03-30
forum: Installation &amp; Upgrades
---

### Post by orca100 on 2018-03-30
I have a fairly new Acer Aspire ES 11 with an embedded SSD (eMMC) on which I removed Windows and installed Linux Mint.
I then replaced Linux with Ubuntu and overwrote and removed Linux.

Ubuntu installed on my C drive but now it will not boot from it and I cannot change the boot priority order. Also due to the above installation I had to set a supervisor password to change the grey wording to blue for access to the "Secure Boot Mode": Select an UEFI file as trusted for executing: 
The only access in BIOS - Security - I have is "Set User Password". Please help.

---

### Post by oldfred on 2018-03-30
Have you updated UEFI from Acer for your system?
Many need that to have the set trust option.

Post this:
sudo efibootmgr -v
That shows current settings.

If not running Windows you may be able to set a new UEFI entry that says "Windows Boot Manager" but really boots using grub or shim to boot Ubuntu.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="https://ubuntuforums.org/showthread.php?t=2358003"]https://ubuntuforums.org/showthread.php?t=2358003
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 
      
 One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335) 
    
To see details on all UEFI boot entries:

 sudo efibootmgr -v  
      
  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
    If drive not sda and partition sda1 you have to add that.

       
 if nvme  where drive is /dev/nvme0n1 and partition -p is 1 may be p1
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1 
Probably similar for mmc devices. Use drive device setting (-d) and partition number (-p).
see
man efibootmgr

---

### Post by orca100 on 2018-03-30
Thanks Fred. It will take me some time as a nooby to digest your post and read the links.

I have no Windows so I cannot do anything more than look at grey stuff in BIOS. Have patience with me as I am a noob pensioner trying my best to save money by fixing this laptop.

Today I stripped it and removed the battery and all ribbon connectors to the main board and left it for an hour then re assembled it. Booted to BIOS and no difference. All still greyed out. Sniff.

---

### Post by gidden2 on 2018-04-02
I have Acer Aspire ES 11 too. (ES1-132-C92R)
It had Win 10 but after update it stop working.

I try few linux and i figure out that this notebook has bugged firmware. It can boot only through UEFI and only from hardcoded specific paths (it ignore paths in efibootmgr -v).
[https://www.linux.org.ru/forum/linux-install/13154949](https://www.linux.org.ru/forum/linux-install/13154949)

When i copied files from folders "BOOT" and "ubuntu" in EFI partition to folder "Linux" it can boot now.
You can do it with these commands if your EFI partition has name *mmcblk0p1* too.
[HTML]sudo mount /dev/mmcblk0p1 /mnt
sudo mkdir /mnt/EFI/Linux
sudo cp /mnt/EFI/BOOT/* /mnt/EFI/Linux
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Linux
sudo umount /mnt[/HTML]

This is only temporary workaround. I think it not start new kernel or grub after update.
Can somebody help me how can I configure folder "/boot/efi/EFI/Linux" as default instead of "/boot/efi/EFI/ubuntu" for bootloader (or what is it)?

---

### Post by oldfred on 2018-04-02
Most UEFI will use a fallback or hard drive entry at /EFI/Boot/bootx64.efi.
So we copy shimx64.efi from /EFI/ubuntu to /EFI/Boot and rename shimx64.efi to bootx64.efi. Some have also had to copy grubx64.efi.

If you cannot set "trust" on /EFI/ubuntu .efi boot file, I do not think you can set "trust" on files on /EFI/Linux. Some other distributions may use that path, but not Ubuntu's version of grub.

Just noticed with a new install of 18.04 that it created /EFI/Boot/bootx64.efi. Have not tried booting with that to confirm it works.
This has been a standard complaint in the Ubuntu grub bug reports.

---

### Post by gidden2 on 2018-04-02
This notebook boot from /EFI/Linux/BOOTX64.efi and some few other hardcoded paths.
It does not use /EFI/Boot/bootx64.efi. 
Now with commands mentioned in #4 it works. I did not asked if i can configure UEFI trust paths. I ask if I can configure Ubuntu (I now use Xubuntu 17.10) to install and actualize bootloader to folder */boot/efi/EFI/Linux*.

---

### Post by oldfred on 2018-04-02
Grub is hard coded to install to /EFI/ubuntu with Ubuntu's grub.
You may be able to manually tell grub to install to another path as grub does have commands to specify just about anything, but that then is a manual install of grub.

see:
man grub-install

---

### Post by orca100 on 2018-04-03
> **gidden2 said:**
> I have Acer Aspire ES 11 too. (ES1-132-C92R)
It had Win 10 but after update it stop working.

I try few linux and i figure out that this notebook has bugged firmware. It can boot only through UEFI and only from hardcoded specific paths

I now have 2 of those laptops. One updated to the latest Windows 10 and I still had over 10 GB free for apps. Thanks to the new file shrink thing. The other one was not used and missed the large update in the middle of last year so it is now full despite deleting all apps. It also stopped working hence the need for Ubuntu.

I ran Linux Mint on it and changed to Ubuntu 16. something and it also worked but then decided that the 17.10.1 looked better. Installed it and that is when my BIOS corrupted. Not by the Ubuntu 17 but perhaps by the 16 version. I cannot enter the "trust" for the UEFI as it is greyed out.

---

### Post by oldfred on 2018-04-03
If "trust" is greyed out, you may not have set UEFI Secure Boot password. 
Do not lose password or remove password after you are done.
Or you need to update UEFI from Acer. Many have had to do that to make it work, but may vary by model.

---

### Post by orca100 on 2018-04-05
I know my password but don't know where to place it as it does not ask for it. I needed to reset it to blank so removed my BIOS battery for 10 mins to do so but now it will not boot at all. Dead and no lights nix nada.

Found that the BIOS bat was only 2.7 v instead of 3.4 v but don't know why it was so low and never gave me any warnings. Some may say that a dead bat will only boot to the BIOS on every start up. Not so. Some laptops such as Acer and HP will not boot up at all with a dead bat.

---

