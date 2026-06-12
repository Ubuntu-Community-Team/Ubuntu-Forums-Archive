---
title: "Problem with boot after installing"
date: 2017-07-09
forum: Installation &amp; Upgrades
---

### Post by martin362 on 2017-07-09
Hi all,

I just tried a lot of things to resolve this problem myself but ultimately I create this post.
I tried to install Ubuntu 16.04.2 LTS on my samsung laptop from DVD media.
Now when I try to boot I get blinking cursor in the top left corner and nothing else happens.

My laptop **Samsung R580-JS02PL **configuration:

[Intel Core i3-330M]("https://www.notebookcheck.pl/Intel-Core-i3-330M.46249.0.html")[COLOR=#171717][FONT=arial] 2.13 GHz
[/FONT][/COLOR][NVIDIA GeForce 310M]("https://www.notebookcheck.pl/NVIDIA-GeForce-310M.45928.0.html")[COLOR=#171717][FONT=arial] - 512 MB, core: 625 MHz, memory: 790 MHz, DDR3, ForceWare 187.87[/FONT][/COLOR][COLOR=#171717][FONT=arial]
Chipset [/FONT][/COLOR][COLOR=#171717][FONT=arial]Intel HM55

[/FONT][/COLOR]Boot-Repair report:
[http://paste.ubuntu.com/25055556/](http://paste.ubuntu.com/25055556/)

Where the problem is?

---

### Post by Futant on 2017-07-10
Hello, welcome to the forum! What steps did you follow in your installation? For example in the BIOS did you disable secure boot? What things have you tried to fix the problem? Can you type when you get the cursor?

---

### Post by slickymaster on 2017-07-10
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by martin362 on 2017-07-16
Hi,

Thanks for your quick answer.

- at first I tried to install from USB stick, and I thought that grub is installed in the wrong place (of corse [COLOR=#000000]when I try to boot I got blinking cursor in the top left corner and nothing else happens),
- next I tried to install from DVD media and effect was the same like from USB stick,
- next I tried to boot from Boot-Repair and selected Recommended repair (repairs most frequent problems) option,
- next I tried to do things describes here [/COLOR]http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd and here [https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)
- next I tried to change options in BIOS (first option "Legacy OS Boot", second option "Large Disk Access Mode"),
- I dont have option "Secure Boot",
- I get blinking cursor exactly after BIOS Summary screen.

I think that maybe it is a problem with graphic card but what are you thinking about it? Are you need my logs from booting process?

---

### Post by oldfred on 2017-07-16
You have an UEFI install.
If you can get to grub menu, you need to add nomodeset until you add the correct nVidia driver from repository.
With one install and UEFI, you have to press escape key after UEFI/BIOS screen, perhaps more than once. If UEFI fast boot is on, you probably do not have time to press a key, and may need to do a full cold boot/power down including removing battery or full reset/restart of UEFI.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by martin362 on 2017-07-30
Hi,

Thanks for your answer but I still have the problem ([COLOR=#000000] I got blinking cursor in the top left corner and nothing else happens[/COLOR]).

I set **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" **like describes in links that you gave (permanently option becouse I cant get into grub menu after BIOS screen. I try Escape and Shift keys).

When I tried to run command sudo update-grub directly then I got an error: /usr/sbin/grub-probe error failed to get canonical path of aufs'.

So next I tried to chroot like describes here: [https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows) (from 1 to 7 point) 
and now sudo update-grub was succeeded.

But when reboot I got the same. Do you need my logs from booting process?

---

### Post by oldfred on 2017-07-30
You have an UEFI install, but those chroot look like the old BIOS version. If you have UEFI, you have to also mount the ESP/efi system partition as part of chroot.
Often just easier to use Boot-Repair as it normally mounts the correct partitions. It does not work for some (older) advanced configurations that assign partitions to many system folders like some server installs still do.

Have you turned off fast boot in UEFI. That often prevents pressing any boot keys as boot is too quick for key to be recognized, system is already starting to boot.

These were some older threads with Samsung, not sure if any still apply but issues are often common by brand.
 Phoenix SecureCore Tiano bios setup and secure boot is greyed out. You need to set a Supervisor Password in the Security tab
Samsung w/ Phoenix Tiano SecureCore
[http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267](http://askubuntu.com/questions/760102/ubuntu-16-04-error-installing-grub/762267#762267)
Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

---

### Post by martin362 on 2017-11-09
Hi again,

Finally I have succeed in install Ubuntu, below what I did:
- in the BIOS: Advanced tab -> Legacy OS Boot I disabled it.
- I have installed new Ubuntu version 17.10
and now it works!

---

