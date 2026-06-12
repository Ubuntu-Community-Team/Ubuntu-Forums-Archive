---
title: "Install Ubuntu  on a Windows 8 pre-installed hybrid graphics laptop"
date: 2014-06-11
forum: Installation &amp; Upgrades
---

### Post by tetelee on 2014-06-11
It has been almost 3 years since last time I was using Linux. Yesterday I decided to try it again with my newly-bought Acer Aspire E1 laptop with Windows 8.1 installed. The hardware specs is Intel I5 4200U CPU, 8G RAM, 1T HDD and ATI Raedon 8760 Graphics. It is hybrid graphics too. I have encountered three main problems so I can't have Ubuntu boot.

Firstly, many post already pointed out that the GRUB might not be working with Windows 8 right after the installation. So a boot-repair tool needs to be run. This is a graphics tool so I assume it means I should use "Try Ubuntu without installing" to have a desktop session after the reboot (during the installation I didn't use the try Ubuntu option. I selected directly install Ubuntu from a black screen selection. 

But then after I select the try Ubuntu, I got this error "the system is running in low-graphics mode". So then I googled the solution to that. Some say I need to install the correct drivers for ATI graphics card. Run ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install fglrx[/FONT][/COLOR]
```. And here comes another problem: since I am not really running Ubuntu from my computer, even though the apt-get installed it correctly, after the reboot I still see this problem and I suspect it is because the live desktop session doesn't get any change.

Somebody also suggested to disable ATI graphics and only use the INTEL integrated one to get into session. In order to do that, I need to configure in BIOS. But when I hit F2 during the reboot and in the BIOS, I only have a very limited number of configurations in my BIOS. It seems that laptop manufacture has made the BIOS less configurable so that users can't mess up with the system. My BIOS looks like this one
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

But I can't do like in the video since my BIOS version is 2.13 and it sounds too risky to me. I don't want to lose my warranty the second day I bough it because I flashed the BIOS.

So now I really don't know what to do next. To make a summary of all the problems: I installed Ubuntu on a Windows 8, hybrid graphics laptop. I need to run boot repair tool but I can't have a live desktop session because I have a "the system is running in low-graphics mode" error. I can't install the ATI drivers because the live desktop session doesn't save any changes. I can't disable ATI graphics card since my BIOS is a locked one. This sounds like more horrible story than 3 years ago when I was using it, and that was when I finally gave it up because I also had the problem with graphics card with version 11.XX

---

### Post by oldfred on 2014-06-11
If you have one of the BIOS that requires a supervisory password, you must set that to be able to make changes. But never lose that password.

If you install video drivers in live session you cannot reboot as live session does not save anything. You may be able to log out and log back in?

Other models, but UEFI may be similar since same vendor:
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

---

### Post by tetelee on 2014-06-11
Thanks again for your reply this post of mine. You provide much information so I need to learn them (as I mentioned in my other post that you answered I already solved my problem though). Basically my current BIOS seems quite limited (and I don't know why I don't have the normal UEFI). I don't know if it requires a supervisory password to activate some additional settings. I'll search for that.

---

