---
title: "Lubuntu installation problem"
date: 2024-08-16
forum: Installation &amp; Upgrades
---

### Post by nyamerooo on 2024-08-16
Hello, I'm new to linux. I have an old laptop that runs very slow on windows 10 so i want to change OS to a lighter one. My laptop is Aspire Es 11 with 2gb ram and Intel Celeron N335 processor. Now, I installed lubuntu based from the manual on their website. But once I finished installing and reboots the laptop, it shows a "NO BOOTABLE DEVICE". Spent 24hrs looking for answers but i couldn't find one. Here's what I differ from the yt fixing vids that I watched. My laptop runs on EFI boot. I changed it to Legacy by accessing the advanced BIOS but it still runs on EFI. Another problem is that I can't load a trusted UEFI file to execute. I don't need to go back to Windows so I don't mind having my HDD wiped clean. Please help me. Also I was redirected here from the boot-repair thing, here's the link that it gave me. [https://paste.ubuntu.com/p/yHkMxR28Nq/](https://paste.ubuntu.com/p/yHkMxR28Nq/)

---

### Post by yancek on 2024-08-16
It appears you may have tried multiple installs or at least did some modification of partitions.  If you look at the boot repair output, you will see on line 205 that the UUID in that file begins with "04b3..."  while the blkid output shows that partition UUID (sda3) actually begins with "b3d4e..."  Use the Ubuntu USB to mount sda1 and go in and modify it to replace the line:  search.fs_uuid 04be9e85-9547-4fa2-a2c6-9ed238b4cbcf root hd0,gpt3  WITH:  search.fs_uuid b3d4e424-fcfa-4fd7-8959-daab4a58cfae root hd0,gpt3

Boot repair does not show any information on your /etc/fstab file so you might mount /dev/sda3 and verify that it is there.
You also have a number of Unknown Device entries for Ubuntu in your EFI output and I'm not sure what that is about.

---

### Post by nyamerooo on 2024-08-16
Yes, I did install it multiple times because i thought i just messed up on the installation process. Can you guide me on fixing this? I'm new to this and is not familiar so I really need more information regarding on how to do things Iike mounting the dev/sda3 and how to verify if it's there, and how to modify the sda1 with the things that you said. Thank you! Also, I did manual partition with it, i got a guide from YouTube. I don't know if it is correct so if possible should i reinstall it again and do the partitions one more time or should i not? anyways helps and guide will be appreciated.

---

### Post by tea for one on 2024-08-17
As you are new to Lubuntu, it would probably be easier to start again rather than fix anything.
Boot into a "Try Lubuntu" live session in UEFI mode
Open the partition manager
Create a GPT (partition table) - this will remove all previous data and partitions
Start the installer and let it partition the disk automatically.
During the installation process, you should see that two partitions will be created

Also, you could tidy up your Unknown Devices with efibootmgr, for example:-
```
sudo efibootmgr -b 0002 -B [COLOR="#0000FF"]
# this will delete entry 002[/COLOR]
```
More info here [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

---

### Post by ne29914 on 2024-08-17
It's a Lubuntu install, so the installer is a bit different.
When you get to the grub menu, select "Start Lubuntu".
Proceed through the menus until you get to partitioning. Choose manual partitioning.
Create a 30 GB partition for / and use the rest for /home. Choose formating to ext4 file system for both.
Go from there.

---

### Post by oldfred on 2024-08-17
See line 71: 
> Boot0000* Unknown Device: 

Acer has a unique requirement that you have to set "trust" on UEFI boot entries you add.
You go into UEFI settings, turn on Secure boot (do not ever forget password) and change unknown to "ubuntu" or whatever name you like.

All seem to have similar instructions, but one may explain it slightly better.
<kbd>Ctrl</kbd><kbd>S</kbd>
Aspire V 15 Nitro Trust settings required.
[https://askubuntu.com/questions/1518065/dual-boot-windows-ubuntu-in-acer-no-grub-showing-up](https://askubuntu.com/questions/1518065/dual-boot-windows-ubuntu-in-acer-no-grub-showing-up)
Trust
[https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx](https://askubuntu.com/questions/908854/installed-ubuntu-17-04-and-now-cant-boot-at-all-failed-to-open-efi-boot-grubx)
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by nyamerooo on 2024-08-17
what to do if my BIOS doesn't have the "Select an UEFI file as trusted for executing"?

---

### Post by oldfred on 2024-08-17
Did you enable Secure Boot? That opens more settings.
It may also be missing if you do not have the latest UEFI firmware for your system. Even if now older, but newer than what you have.
Check version in UEFI and then go to Acer site for support for your model system.
And review the screens shown in the linked posts?

Some old threads talked about downgrading UEFI to an older version. But newer version works.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by nyamerooo on 2024-08-17
Yes, I've enabled secure boot and got into the advanced bios by using fn+tab+power but i still doesn't have the "Select and UEFI file as trusted for executing". I've already reviewed all the linked posts, thanks for it. I can't seem to find a tutorial on how to upgrade the BIOS, if you are only booting on a live Ubuntu. My laptop doesn't boot on the Lubuntu OS (that's my main problem) I can only boot from the USB bootable device which has the lubuntu installation, and runs on "Try Lubuntu". I don't know how to upgrade the BIOS in this set up since tutorials are running in the Windows. So I'm still stuck. I'll again ask for your assistance, if you ever know how to maneuver things with my current set up.

---

### Post by nyamerooo on 2024-08-17
my plan now is to reinstall windows 10 and have my firmware updated there since i can't seem find any way to update firmware using only the live lubuntu environment.

---

### Post by tea for one on 2024-08-18
Install rEFInd on a USB stick and select to boot the kernel directly i.e. hopefully avoid Grub and Acer trust settings.
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File

More info here [https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/getting-acer-es1-132-c2jz-to-boot-xubuntu-from-hdd-using-refind-and-not-just-from-usb-4175618070/](https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/getting-acer-es1-132-c2jz-to-boot-xubuntu-from-hdd-using-refind-and-not-just-from-usb-4175618070/)

I can't test the theory because I do not have an Acer laptop
Worth trying?

---

### Post by oldfred on 2024-08-18
Acer only has two models that it supports with Linux fwupdate for UEFI firmware updates.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
Aspire A315 and 515.

So not know if Acer supports any of these:
[https://www.reddit.com/r/linuxhardware/comments/khkva6/installing_a_bios_update_on_an_acer_laptop/](https://www.reddit.com/r/linuxhardware/comments/khkva6/installing_a_bios_update_on_an_acer_laptop/)

Many new systems update from within UEFI reading the update file from a FAT32 partition, either ESP if large enough or flash drive.
You often download a Windows .exe or .bin file & have to extract update.
Some update from a bootable image you can download.
Some may work with  a WinPE bootable image.

HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

---

### Post by nyamerooo on 2024-08-24
update: 

I've already updated the firmware but there's still no "Select an UEFI file for trusted executing", So updating BIOS/firmware wasn't the fix. I've fixed it by following this article: [http://www.slabbe.org/blogue/2018/05/installing-ubuntu-18.04-on-aspire-es-11-es1-132-c6lg/](http://www.slabbe.org/blogue/2018/05/installing-ubuntu-18.04-on-aspire-es-11-es1-132-c6lg/).

---

