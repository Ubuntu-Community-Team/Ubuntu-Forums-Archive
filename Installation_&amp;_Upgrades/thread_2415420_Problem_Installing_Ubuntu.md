---
title: "Problem Installing Ubuntu"
date: 2019-03-25
forum: Installation &amp; Upgrades
---

### Post by pyrogarcia on 2019-03-25
I'm trying to install Ubuntu in am Acer ES 15 ES1-533-C3VD. I erease the whole HD and try to make a fresh installation of Ubuntu 18.04.2 LTS. I got that EFI incompatibility problem that won't let me boot the OS. I've already try all the guides I found, and just manage to boot into Grub Minimal Bash. 
Ubuntu was installed via ubiquity without the bootloader so I could finish the installation. Did use the boot-repair tool but it also freezes in a point. Hard freeze, so gotta restart. Any help?

---

### Post by oldfred on 2019-03-25
If you want UEFI, you need gpt partitioning, but default install will depend on how you boot installer. If you did not boot installer in UEFI mode then partitioning may not be correct.
Have you updated UEFI from Acer. Many needed newer UEFI to work correctly.
       Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [       ]("https://help.ubuntu.com/community/Boot-Repair")
 One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335) 
    [       ]("https://help.ubuntu.com/community/Boot-Repair")
 Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator) 
    [URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

