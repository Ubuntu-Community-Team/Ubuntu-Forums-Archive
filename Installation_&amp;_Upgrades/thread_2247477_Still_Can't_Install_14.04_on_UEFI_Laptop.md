---
title: "Still Can't Install 14.04 on UEFI Laptop"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by Travin_Keith on 2014-10-08
Greetings,

So, this has been something going on-and-off for the past year now with my UEFI laptop. Over the past few days, I've finally decided to sit down and actually get Ubuntu 14.04 installed on my laptop properly. Last time, I somehow installed it (13.10 probably) and had it appear on the OS selection on the Windows boot loader (not GRUB). However, when clicking it, it leads to nowhere and says that nothing is found. 

Now, I've been reading a bunch of tutorials and I've turned off Secure Boot (it was off already, probably from the previous time I gave it a go) and rearranged the boot load sequence on UEFI. However, I still can't seem to boot from my CD. I'm not sure how I got it to boot from a CD before, though it was probably when I switched it to BIOS, but I can't seem to do it now. It won't boot from CD through the Windows menu on the OS selection via the Windows Boot Loader, nor when I click F12 or when I have the order made so it boots from the CD first. 

Any ideas on what's going on?

---

### Post by kc1di on 2014-10-08
I Have no Ideas off the top of my head, but it may be useful to post some details about your laptop. brand, model , ram graphic card, ETC. 
That way someone who has successfully installed on your type of machine may come to your aid. 
By the way welcome to the Ubuntu Forums.
:)

---

### Post by Travin_Keith on 2014-10-08
Thanks for the welcome! I was on this forum multiple years ago, but life got in the way and I'm on a new account. Quite different now from back then, so it's really like it's all new! 

Here's some information regarding my laptop:

Acer Aspire V5
NVIDIA GEFORCE 710M
Intel i7
64 Bit
8 GB of RAM
Current System: Windows 8.1 Pro (Upgraded from 8)

---

### Post by oldfred on 2014-10-08
Best to review these first, even more links to additional info in link in my signature:
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Others with Acer, may be similar issues and how they resolved them. Most find 14.04 works better or has fewer issues than the older verions. 

 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Added new msata drive post #3
[http://ubuntuforums.org/showthread.php?t=2174844](http://ubuntuforums.org/showthread.php?t=2174844)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by Travin_Keith on 2014-10-19
Thanks for your help oldfred! I looked into them and did what I found appropriate for my situation and it still didn't work. Lo and behold, the ISO didn't download properly and thus the CD was a few hundred MB short of what it should have been. I'm now happily back on Ubuntu!

---

