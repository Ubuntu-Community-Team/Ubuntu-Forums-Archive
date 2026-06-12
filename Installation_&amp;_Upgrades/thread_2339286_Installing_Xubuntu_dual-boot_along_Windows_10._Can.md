---
title: "Installing Xubuntu dual-boot along Windows 10. Cannot boot linux post-install"
date: 2016-10-07
forum: Installation &amp; Upgrades
---

### Post by kurt-wheeler91 on 2016-10-07
I bought a new Acer Aspire E 15 laptop and I want to dual boot Xubuntu 16.04.1 LTS alongside the Windows 10 installation that it came with. I've been able to succesfully run the Linux installation  vis a USB drive at least a dozen times, but once I restart the computer I cannot boot into it. I've installed Ubuntu on many computers before but they always used BIOS and this new UEFI madness that Windows 10 introduced seems to be the cause of the issue.

I've done a lot of research already and tried a lot of things so I'll cover what I have tried first:
[LIST]
[*]Disabled Fast Startup
[*]Turned off Secure Boot
[*]Used efibootmgr to change the boot order so Ubuntu boots before Windows Boot Manager
[*]Installed and ran boot-repair. It said an error occurred during repair and gave me this pastebin link: [http://paste2.org/eONDG45A](http://paste2.org/eONDG45A)
[*]Changed my boot mode to Legacy from UEFI. This made it so nothing booted and I had to go into the bios and change the setting back to even get Windows to boot again. From what I've read it looks like the only way to make my computer work in legacy mode is to reinstall Windows, which I'd like to avoid at all costs.
[/LIST]

If anyone can provide any help it would be super appreciated. I've already spent a half dozen hours just trying to get Ubuntu installed and I'm really frustrated at this point.

---

### Post by kurt-wheeler91 on 2016-10-07
Wow I just got it to work literally 5 minutes after posting this!

The instructions on this page fixed it for me: [https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)

boot-repair had suggested that I run that command but the issue was that I didn't run cmd as administrator. Stupid Windows just fails commands rather than prompting you to become an administrator to run them.

---

### Post by Geoffrey_Arndt on 2016-10-07
Kurt . . it always helps to close out this thread as "Solved" (see Thread Tools at top of page).

---

### Post by Bucky Ball on 2016-10-07
> **Geoffrey_Arndt said:**
> Kurt . . it always helps to close out this thread as "Solved" (see Thread Tools at top of page).

+1. Thanks. It will not close the thread for further discussion, just helps others. 

'Thread Tools', as advised, or there is a link for how to mark as solved in my signature at the bottom of this post.

PS: Good news and well done. Climb that learning curve! :)

---

### Post by oldfred on 2016-10-07
If an Acer you can also set UEFI password and enable "trust" on grub/ubuntu .efi files. This is unique to Acer UEFI. 
Some Acer links may say to downgrade UEFI, but newer ones say newest UEFI from Acer works. So make sure you have newest UEFI from Acer.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

