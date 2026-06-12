---
title: "Boot Repair Failure"
date: 2015-08-16
forum: Installation &amp; Upgrades
---

### Post by sieve70 on 2015-08-16
[COLOR=#111111][FONT=Ubuntu]Long story I'll try to keep short:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Win7 / Ubuntu dual boot setup on Asus G75 with Aptio 2.14.1219 bios[/FONT][/COLOR]

[LIST=1]
[*]Had 12.04 on sda5 - became corrupt / wouldn't boot, so reformatted partition.

[*]Couldn't get 14.04 to install on sda5, so I bought new 1TB drive (now sdb) and installed 14.04 there - GRUB install failure at end.

[*]Put boot-repair-disk-64bit on USB and ran. Recommended fix was perfect - boot 14.04 from sdb as default - but fix failed with bios setting UEFI both "Enabled" and "Disabled" with following message:
[/LIST]
[COLOR=#111111][FONT=Ubuntu]"The boot of your PC is in Legacy mode. Please change it to EFI mode. Please us Boot-Repair-Disk-64bit..." (you know the message! LOL)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]System info is here: [http://paste.ubuntu.com/12091973/](http://paste.ubuntu.com/12091973/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I want Ubuntu back... thanks in advance for the help!!

[/FONT][/COLOR]

---

### Post by oldfred on 2015-08-16
Your hardware is UEFI.
You have Windows booting in UEFI mode.
But you have Ubuntu booting in BIOS mode on sdb. It looks like if you select Legacy/BIOS/CSM mode and choose sdb as boot drive it should boot. 
But UEFI & BIOS are not compatible, so if you start to boot to grub in BIOS mode, you cannot switch to UEFI mode for Windows unless you reboot. Or you can only choose boot mode from UEFI/

If installing 14.04.3, it should work better as it has many updates over older UEFI install.
What video card/chip?

       Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[URL="http://ubuntuforums.org/showthread.php?t=2251167"]http://ubuntuforums.org/showthread.php?t=2251167
[/URL]
 UEFI may have setting that is Windows 8 or Windows 7, which probably is to turn off secure boot
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)

[URL="http://ubuntuforums.org/showthread.php?t=2251167"]
[/URL]

---

### Post by sieve70 on 2015-08-16
Thanks for the info / links!!!  I'll report back ASAP!

Video "card" is GeForce GTX 660M / 2G

---

### Post by oldfred on 2015-08-16
Nvidia needs the nomodeset until you install the proprietary driver from System settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If chip is not the new Maxwell series, you can just install the newest in the repository in System Settings, Software & Drivers tab.

If grub has only found Ubuntu, you may have to also press escape right after or just before UEFI ends to get menu to appear.

---

### Post by sieve70 on 2015-08-16
Thanks!!!

I had to go to hockey after reading half of previous suggestions!  I'll get back on this tomorrow ASAP with questions!

I'm used to ubuntu and working my regular gig in the environment, but this area is one that is foreign to me - I dual booted this machine on 12.04 previously, then it crashed... Leading me to the current situation...

After reading through part of previous suggestions, I know I'm going to be asking some stupid questions - hope you guys are patient with me! :)

---

### Post by mailtomendoza on 2015-08-17
I have same problem. freshly installed 8.1 then newest ubuntu, Boot repair writes same error...


> **oldfred said:**
> Your hardware is UEFI.
You have Windows booting in UEFI mode.
But you have Ubuntu booting in BIOS mode on sdb. It looks like if you select Legacy/BIOS/CSM mode and choose sdb as boot drive it should boot. 
But UEFI & BIOS are not compatible, so if you start to boot to grub in BIOS mode, you cannot switch to UEFI mode for Windows unless you reboot. Or you can only choose boot mode from UEFI/[URL="http://ubuntuforums.org/showthread.php?t=2251167"]
[/URL]

But if UEFI and BIOS modes are incompatible, how then super grub disk ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)) can boot any of the OS'es with no problems and grub it self can not?

---

### Post by oldfred on 2015-08-18
Not sure how Supergrub works. It is a good boot loader, if one has issues.

With UEFI you can set a one time boot and it reboots to use that. 
Not sure then if booted in BIOS mode you can set a UEFI boot on reboot or not.

---

### Post by mailtomendoza on 2015-08-18
Anyway, i have a problem with installing (repairing) grub... just don't know what more i can do...   i have set two options in bios CSM -> Enable, Secure Boot -> Disable. then installed W8.1, after that Ubuntu. And i can boot Ubuntu only using bootable USB stick with supergrub disk...

---

### Post by oldfred on 2015-08-18
@mailtomendoza
If you installed in BIOS mode your issues are not related to this thread. 
Please start your own thread and post link to Summary report from Boot-Repair.

---

### Post by mailtomendoza on 2015-08-19
Ok,

---

