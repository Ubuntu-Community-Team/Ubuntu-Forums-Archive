---
title: "Howto Cleanup EFI after boot-repair"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by franknfurter2 on 2018-10-16
Hallo,

a few days ago I did a normal update of my 18.04 LTS Desktop System, which I some weeks ago upgraded from 16 (Flavour Ubuntu Studio). It is a dual boot System with Windows 10 on the same SSD.

When I have restarted it after update, GRUB menu hasn't shown up any more and the only way to start has been via BIOS Menu and the only system starting was Windows. So I had build a Live USB Stick, started from there and run boot-repair tool as mentioned here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The default repair button results in message telling me, to switch off SecureBoot. But i did not. I did' a repair anyway which did not work. And after a while i had the idea, that it might have to do with unsigned kernal files. So I moved the newest kernal files in a subfolder under /boot/ and suddenly, I was able to start Ubuntu from SSD again (I do not know anymore, if it was from the BIOS menu or if the GRUB Menu was showing).
Within that system, I installed boot-repair again and started a repair without switching SecureBoot off.

A reboot than shows a new GRUB Menu with a lot of entries. I then copied the newest kernal files (4.15.0-36) back into the /boot folder (4.15.0-36) and run boot-repair again.

Next reboot has show up the GRUB Menu and it was able to start lowlatency kernal 4.15.0-36.

Now, I see three problems:


    Why was Boot Loader corrupted and why does it now work with the newest kernal
    Why are there so many (mainly Windows) entries in the GRUB menu
    How to clean up the menu and the files and subfolders of /boot 

You can find the boot-repair system report [here]("http://paste.ubuntu.com/p/pgmvbFjG6d/")

Which of the files (bkpbootx64.efi, bootx64.efi, fbx64.efi, fwupx64.efi, grubx64.efi, mmx64.efi, shimx64.efi, bootmgfw.efi, bootmgr.efi and memtest.efi) is really needed? Who has installed them?

If someone knows a good How-To which explains all this. Let me know.

So, can someone help me with this?

---

### Post by oldfred on 2018-10-16
You now show UEFI Secure Boot off.
To boot with it on you need shimx64.efi and kernels that are signed. Do not know if there are low latency signed kernels or not, but you are not showing any signed kernels, just low latency & generic.

Yes you need those files. but may need to use them, regularly.
But you do not necessarily need them all in grub menu.
Boot-Repair sees additional .efi boot files and creates another grub boot file 25_custom and adds all those entries. You can either edit, delete or turn off execute bit so not added to grub menu on updates.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
Or remove completely from menu by turning off execute bit:
sudo chmod a-x /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by franknfurter2 on 2018-10-17
Dear Oldfred,

you are absolutely right. My System is now not in SecureBoot Mode. I must have changed this while I was messing around with my boot problem. Your solution thow cleaned up my boot menu. Thanks for helping me.

But my main problem is still, that I could not boot anymore with secure boot on. I found my first boot-repair report when I started analysing the problem, and there I can see, that my system was in secure boot mode.
I have got an ASUS Z170-A Motherboard and the only entry, effecting secure boot, is under boot, secure boot. Here is an extract from the handbook:  
----------------------------------------
Secure Boot
[INDENT]This item allows you to configure the Windows ® Secure Boot settings and manage its keys to
protect the system from unauthorized access and malwares during POST.
OS Type [Windows UEFI mode]
[/INDENT]

[LIST]
[*=2][Windows UEFI Mode] 
This item allows you to select your installed operating system.
Execute the Microsoft ® Secure Boot check. Only select
this option when booting on Windows ® UEFI mode or other
Microsoft ® Secure Boot compliant OS.
[*=2][Other OS]
Get the optimized function when booting on Windows ® non-
UEFI mode. Microsoft ® Secure Boot only supports Windows ®
UEFI mode.
[/LIST]

----------------------------------------

I am sure, that I never changed this, only when I was messing around with my problem.

[Other OS] is showing Grub Menu, [Windows UEFI Mode] does not. Any idea about that?

---

### Post by oldfred on 2018-10-17
I have an Asus Z97 and I think almost all the screens are the same.
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)

I do not have Windows, only use "Other" setting. But for now, do not want UEFI Secure Boot.
I do have multiple other settings, see post #6 in above thread.

I also check regularly and update UEFI to most current version. But that resets some of the UEFI settings, so I had to keep a list.

---

### Post by franknfurter2 on 2018-10-19
Dear oldfred,

thanks for this. The topic (Cleanup Grub entries) of this thread is solved, so I marked it "solved".

The other problems of SecureBoot are not solved but are not subject of this thread. Maybe I'll open a new thread for that after I went deeper into documentation.

---

