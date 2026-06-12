---
title: "Ubuntu 12.10 Secure Remix (UEFI and Windows 8) path to 13.04?"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by bigfootnmd on 2013-04-30
I have an Lenovo IdeaCentre Q190.  This little PC came with Window 8 preloaded.  So, since I spend 95% of my time in Ubuntu I of course wanted to make my new computer Dual Boot with Ubuntu.
Reasearch lead me to the UEFI community guide ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) which has not been updated to cover 13.04) and other articles told me that Ubuntu 12.04 and 12.10 in 64 bit mode suppoted UEFI.  So, in early March I loaded Ubuntu 12.10 Secure remix (64 bit).  I did have to use the boot repair to get the Boot loader to present the options of Ubuntu or Windows 8.  So, time passes and here we are with 13.04.  However, although Update tells me I can upgrade I am not so trusting. As I previously mentioned Ubuntu 12.10 Secure remix is working fine.

So, what might be the safest path for the journey from 12.10 Secure remix 64 bit to 13.04?  Is there a 13.04 Secure remix yet?
Thank you in advance.

---

### Post by oldfred on 2013-05-01
I believe the secure remix is just Ubuntu with Boot-Repair, Boot uninstaller and maybe a couple of other repair tools included.
Not sure when a 13.04 Secure remix may be out. 

Do you have another 10 or 20GB on hard drive? If so you could just to another install and see how it works. I might backup efi partition as I am not sure how two Ubuntu installs will work in one efi partition and you only can have one efi partition per drive.

---

### Post by Hellrevisted on 2013-05-01
I have sony vaio sve14ae11w model........and its os is Win8 uefi mode.......i installed ubuntu 12.10 but it encountered problem while booting saying wubil.mbr file missing......i want both os win 8 and ubuntu.......what should i do now?

---

### Post by oldfred on 2013-05-01
@Hellrevisted
Please do not hijack another thread. But wubi does not work with gpt partitioning which is used for all UEFI systems like Windows 8 pre-installed. Please start another thread with your issues.

---

### Post by grahammechanical on 2013-05-01
@ bigfootnmd

I am posting this from Ubuntu 12.10 Secure Remix that I just (2 hours ago) upgraded to 13.04. Everything went fine. The upgrade needs some user input (twice) so do not leave it unattended. It does not remove Boot Repair or OS-Uninstaller. Both load. How well they work I cannot say. Except that OS-Uninstaller detected and listed a Ubuntu install on a second hard disk that I had recently converted to 13.10 and it labelled it as Saucy Salamander. So, that part is looking good.

The one thing it does do is change the distribution label. You are asked if you agree to the change. Say no and Grub will list it as Ubuntu Secure Remix 12.10. Accept the change and it gets listed as Ubuntu 13.04.

The script that gets changed is found at /etc/lsb-release. This is what it says

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

I think that with administrator privileges it should be possible to edit that file and add Secure Remix.

Edit: It can be changed to DISTRIB_DESCRIPTION="Ubuntu Secure Remix 13.04" But remember to run ```
sudo update-grub
``` to get the Grub configuration files updated.

Regards.

---

### Post by megamaced on 2013-05-20
Hi


Sorry to hijack but I was thinking about buying the Lenovo Q190 (with core i3 proc) to run Mythbuntu 12.04.2 but I've read that some people couldn't get an X server running using the Celeron 877 version and that the WiFi doesn't work. How does Ubuntu run for you?

ta

---

