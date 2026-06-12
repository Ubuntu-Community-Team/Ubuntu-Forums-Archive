---
title: "reboot and select proper boot device after clean installation of ubuntu"
date: 2014-12-09
forum: Installation &amp; Upgrades
---

### Post by aka.mdsg on 2014-12-09
Hello.

I installed ubuntu, which replaced my whole hard drive, which means it replaced my windows, I only want to have ubuntu but it is quite messing up my installation..

I have done this before but never had this error, its the first time doing it on this computer tho..

After the installation, I couldn-t boot the computer getting the error that is on the title, then I booted into live cd and ran boot repair, that didn-t help so I got the log file from it and I am hoping you guys can understand it and help me out.

[http://paste.ubuntu.com/9449558/](http://paste.ubuntu.com/9449558/)

I have my boot order correct, I don-t really know what should I do.

Any help would be appreciated.

Cheers

---

### Post by grahammechanical on 2014-12-09
This is the original problem

> No boot loader is installed in the MBR of /dev/sda.

This is the Boor Repair recommended repair.

> [COLOR=#666666]===================[/COLOR] Suggested repair
The default repair of the Boot-Repair utility would purge [COLOR=#666666]([/COLOR]in order to sign-grub[COLOR=#666666])[/COLOR] and reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s

But then there is this:

> [COLOR=#666666]===================[/COLOR] User settings
The settings chosen by the user will not act on the boot.

Did you not accept the recommended repair?

Regards.

---

### Post by aka.mdsg on 2014-12-09
I did, I have done it once before and now again, il reboot and see if it made any good, this is the log..

[http://paste.ubuntu.com/9449834/](http://paste.ubuntu.com/9449834/)

brb

---

### Post by aka.mdsg on 2014-12-09
Well, I am back and I still cannot boot into Ubuntu normally.

I done again the recommended repair of the boot-repair... no success tho.. :c

edit:

done another log, [http://paste.ubuntu.com/9449969/](http://paste.ubuntu.com/9449969/)

any ideas?

edit2:
while it boots up, before the error in the american megatrends first screen, it says 'couldn't open EFi - boot - fallback ..

Something like that, I didn-t catch every detail...

---

### Post by oldfred on 2014-12-09
What brand and model computer. 
Many vendors modify UEFI to only boot Windows.
Some vendors require you to set a password in UEFI to allow to reset or make Ubuntu default.

If you have a system that only boots Windows see the D: option as you only have Ubuntu installed.

 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by aka.mdsg on 2014-12-10
Thanks very much, my computer is acer m3970 and that may actually be the problem.

Il look into it and then I'l say something here.

---

### Post by oldfred on 2014-12-10
You may not need the rename with efibootmgr but probably need a password to let you change things. Acers seem to need passwords.

 Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

 Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by aka.mdsg on 2014-12-10
I am sorry but I am not understanding exacly what I have to do in the BIOS, and the command @sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"@ doesn' work, it says sudo: @efibootmgr: command not found@..

Well, il see what my bios enables me to do if I put in a password.

Thanks for the information, cheers :)

edit:

It added no options in the BIOS, and I don't appear to have anything in the folder boot/efi, at least not visible with the file explorer..

I had windows 8, I replaced it completly with Ubuntu for work but I seem to have to go back to Windows, this time the W7 and keep emulating ubuntu with virtualbox like I did so far till now...

I have some projects on the raspberry pi and it would help me to have linux actually installed instead of emulating it but I seem to have no luck in my computer...

Il start download and burn Windows 7 in a usb, I don't see myself getting through this boot error, I ran the bootrepair so many times and tried many solutions I found on the internet and the solution D you sent me, it still doesn't boot.. seems like I have to give up on ubuntu with sadness :/

---

### Post by oldfred on 2014-12-10
The efibootmgr is only available if you boot in UEFI mode not BIOS mode. You should have the option to boot live installer in either boot mode from UEFI boot menu.

this should show your efi boot settings in your UEFI:
 sudo efibootmgr -v


With Windows 7 you have to install in UEFI mode or have to run fixparts as Windows 7 in BIOS mode converts the gpt partitioned drive from gpt to MBR, but does it incorrectly. Fixparts is a tool you can download to correct the mistake that Windows does.


You have to change settings in UEFI with Acer you have to enable a UEFI password to be able to change some of those settings. Never ever lose that password or you may just have a brick.

---

### Post by oldfred on 2014-12-10
post this:
this should show your efi boot settings in your UEFI:
 sudo efibootmgr -v

I did find a typo in my command, an extra space where one should not be. There was a space after the " and before the \EFI, should have no space after " like these:
       
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"

---

