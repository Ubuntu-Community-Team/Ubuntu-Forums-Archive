---
title: "Upgrading to Windows 10 with Dual Boot Ubuntu and Grub"
date: 2016-07-16
forum: Installation &amp; Upgrades
---

### Post by Geek10 on 2016-07-16
This is a post about how my Windows 10 upgrade was hindered by my  misunderstanding of the dual-boot nature of Windows and Ubuntu with  Grub. I don't normally take the time to share how my problems were  solved, but with the free upgrade to Windows 10 coming to an end on 29  July 2016, I thought this may help fellow dual-booters with the optional  upgrade. 

First, I will mention that Microsoft has an extensive list of troubleshooting advice for upgrading to Windows 10 [here]("https://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-troubleshoot-common-setup-and-stop-errors/324d5a5f-d658-456c-bb82-b1201f735683").

I followed this advice, but each time after running the Windows 10 setup  from a DVD created from the Windows 10 Installation Media, the computer  rebooted, and once logged in to Windows 7, produces the error message:  "0xC1900101 - 0x20017 The installation failed in the SAFE_OS phase with  an error during BOOT operation".

After much consternation and investigation, I finally found the solution in an obscure [thread]("http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/solved-windows-8-upgrade-on-dual-boot-machine-with/33fc8c23-5645-4cd9-a30c-a6c5c4e224ed?auth=1") by a user called Qshunt who had similar problems upgrading to Windows 8 with a dual boot setup. Qshunt said:
>                                                          I realised that on my GRUB loader screen there were *two* Win7 boot   options.  One on /dev/sda1 and on on /dev/sda2.  I'd always booted into   /dev/sda2, because the 1st time I'd tried sda1 it had gone through  some  sort of windows check-disk  process and I'd assumed it was a  safe-boot or similar.   

 In any event, booting via /dev/sda1 and then starting the upgrade   process and using sda1 on all the interim reboots during the upgrade did   the trick.

So if you have two GRUB Windows 7 boot options that work and you get upgrade failures on one, then maybe try the other.                      

Moderators, if you feel this post is irrelevant/should be  moved/should be kicked to Microsoft's forums, please let me know/do so.  I'm only trying to help the wonderful dual-boot community that helped me  enjoy the benefits of dual-booting. Thanks! :razz:

---

