---
title: "Ubuntu not booting - Boot-Repair unsuccessful"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by Insomniac18 on 2013-01-17
Hi,

I have always had issues with Ubuntu on this laptop, because I think I have a UEFI setup, but I am not sure. I followed the steps on [this page]("https://help.ubuntu.com/community/UEFI").

Basically, I:
 - downloaded Ubuntu Secure Remix 64bit
 - Used Universal USB Installer to put it on a flash drive
 - Booted from flash drive
 - hit "try Ubuntu without installing"
 - installed Ubuntu alongside Windows 7
 - rebooted and computer automatically boot into Windows 7 without showing GRUB
 - rebooted into the flash drive, ran Boot-Repair
 - rebooted, same as before it booted into Windows 7
 - rebooted into the flash drive, ran Boot-Repair, and noted this pastebin URL: [http://paste.ubuntu.com/1540321/](http://paste.ubuntu.com/1540321/)
 - rebooted, same as before it booted into Windows 7
 - and here we are. :(

Any help would be appreciated. I have an ASUS N56VZ, if this is helpful. If any other information is needed, I can provide it.

Thank you all!

---

### Post by oldfred on 2013-01-17
You may an UEFI system, but Windows is in BIOS/MBR mode.

Boot-Repair says it installed grub to the MBR, but you still have a Windows boot loader in the MBR.

Do you have a BIOS that has security or a locked MBR to prevent writing to the MBR? A few systems do have that.

       BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker

    
I do not think I have seen Boot-Repair not work, but you can try the manual ways also.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2
Grub2 info & full chroot version - also METHOD 3 - CHROOT:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Insomniac18 on 2013-01-18
Thanks for the reply.

I don't think my BIOS has security. It has Intel Anti-Theft, but as far as I know that's unrelated. I went ahead and disabled it anyways. I looked through the BIOS settings and as far as I know, nothing there said anything about security. I also went ahead and googled around for information about the ASUS N56VZ BIOS, but didn't find anything too helpful.

Out of all the links you gave, which would you suggest as the best way to do this? I'm a bit of a noob at messing with Ubuntu/GRUB settings.

Thanks again.

EDIT:
Solved!!!
I went to the first link you posted, and ran the following commands in a Terminal window from the Live Disk. (My Ubuntu install was on /dev/sda5)
```

sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```

Rebooted, and there was GRUB! Thanks for all your help!

---

### Post by oldfred on 2013-01-19
Glad you resolved it.

I think it was the Intel Anti-theft. That totally locks up system if stolen, you cannot boot nor update BIOS unless authorized. And to do that it has to control BIOS or UEFI. It seems that is being offered with all Ultrabooks as part of the Intel specification for an Ultrabook.

---

### Post by Insomniac18 on 2013-01-19
Not really sure. After I disabled Anti-theft I tried Boot-Repair again and it didn't work. Only manually reinstalling GRUB did it.

Also, from what I read, Intel Anti-theft needs to be activated through additional software.

Shrug, works now, thanks again!

---

