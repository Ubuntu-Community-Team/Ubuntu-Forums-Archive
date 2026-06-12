---
title: "Finding it impossible to dual boot"
date: 2016-12-30
forum: Installation &amp; Upgrades
---

### Post by Malacath on 2016-12-30
Please help.

I have installed Ubuntu mate on my HP Windows 10 laptop.

Problem is no matter what I do I cannot get it to load Grub by default.

Every time the laptop boots it goes straight into Windows

The only way I can get Grub to load as well as linux is to keep pressing esc when switching on. Only then can I choose to load Ubuntu.

There seems to be no way to get the latop to load grub instead of windows boot manager.

I have tried running boot-repair. Doesn't work
I have tried changing the load order using the efibootmgr but as soon as the computer is restarted it forgets and Windows goes back to the top of the load order.
I have tried disabling secure boot. Makes no difference.
I have tried enabling legacy mode again makes no difference and If I try to reinstall Ubuntu using legacy mode instead of efi it doesn't recognise that windows is installed.

I have done dual boots with various laptops in the past and this is the first time I have had trouble.

---

### Post by Bucky Ball on 2016-12-30
Have you got Windows installed in UEFI mode and you installed Ubuntu in legacy mode? You don't say directly, but looks like you may have both in UEFI. A tip: don't try switching either of them to legacy if both are installed in UEFI. That is going to cause further issues. Whatever the first OS was installed in (Win/UEFI) the second should be installed in also.

---

### Post by oldfred on 2016-12-30
If Ubuntu also UEFI, then HP does not make it particularly easy. But several work arounds are available.

Many will discuss manually copying shimx64.efi, but now Boot-Repair will do that for you. 
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
 	'Use the standard EFI file' in advanced options. And then you boot the Hard drive or fallback entry in UEFI, not the ubuntu entry.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
[/URL]
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

      
 Copy to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114](http://askubuntu.com/questions/582073/dual-boot-but-only-windows-boots/582114#582114)
Rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019) 
    [URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

### Post by Malacath on 2016-12-31
> **Bucky Ball said:**
> Have you got Windows installed in UEFI mode and you installed Ubuntu in legacy mode? You don't say directly, but looks like you may have both in UEFI. A tip: don't try switching either of them to legacy if both are installed in UEFI. That is going to cause further issues. Whatever the first OS was installed in (Win/UEFI) the second should be installed in also.

Yes they are both in UEFI mode.

---

### Post by Malacath on 2016-12-31
I may just wipe the hard drive and install windows again then try installing Ubuntu Mate again.

Noticed that widows has a bug that whenever you use the reset function in recovery it will create extra recovery partitions and leave the old ones behind. I have a few of the partitions. Could it be getting confused when I run the boot repair tool?

---

### Post by Malacath on 2016-12-31
This is a total nightmare.

Done everything I can find on the internet and it's impossible for my laptop to dual boot.

The only thing left to do is switch on legacy BIOS mode and install windows and Ubuntu again in BIOS mode.

I'm hoping this will allow me to dual boot but i'm not holding my breath.

If this doesn't work i'm just going to have to give up on the idea of having Linux on this laptop until I buy a new Windows laptop

---

### Post by Malacath on 2016-12-31
Finally got it to dual boot.

Had to turn off secure boot then switch on legacy mode.

Had to wipe everything then install Windows 10 in legacy mode.
I then installed Ubuntu in Legacy mode and now am able to dual boot.

---

### Post by Bucky Ball on 2016-12-31
Excellent. Please see the last blue link in my signature at bottom of this post to mark this thread as solved and post a new one with a descriptive title for any further issues. It will greatly improve your chances of support with them. Good luck and enjoy. ;)

---

